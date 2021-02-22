---
solution: Campaign Classic
product: campaign
title: SMS 连接器协议和设置
description: 了解有关SMS连接器的更多信息以及如何配置它。
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: a157082070b22e3621cb81411a5ddde387fd5fcf
workflow-type: tm+mt
source-wordcount: '8458'
ht-degree: 0%

---

# SMS 连接器协议和设置 {#sms-connector-protocol}

>[!NOTE]
>
>可在此[页面](https://experienceleague.adobe.com/docs/campaign-standard/using/administrating/configuring-sms/sms-protocol.html#administrating)中找到Adobe Campaign Standard的&#x200B;**SMS连接器协议和设置**。
>
>通过本文档，所有对协议详细信息、字段名称和值的引用都引用[SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)。

## 概述 {#overview}

SMS可能仅限于发送没有格式的短文本消息，但其简单性使其成为宝贵的通信渠道。

发送SMS主要有两种方式：

* 手动从电话发送，这是直接在人与人之间进行交流的常用方式。
* 通过Internet发送，即Adobe Campaign发送消息的方式。 为此，您需要将Internet连接到移动网络的SMS服务提供商。
Adobe Campaign使用SMPP协议将SMS发送到服务提供商。

此文档将引导您了解Adobe Campaign与SMPP提供商之间建立的连接。

SMPP提供商有时可能偏离官方规范，但Adobe Campaign中的SMS连接器提供了许多选项来调整其行为，使其与大多数提供商兼容。

>[!IMPORTANT]
>
>设置与新提供程序的连接可能需要一些技术技能、TCP知识、二进制、十六进制表示和文本编码。 它还需要与提供商积极合作。

### SMS类型{#sms-types}

当通过SMS提供商发送大量SMS时，您会遇到三种不同的SMS:

* **SMS MT（已终止移动）**:通过SMPP提供商向移动电话发送的SMS。

* **SMS MO（移动端诞生）**:由移动设备通过SMPP提供商发送给Adobe Campaign的SMS。

* **SMS SR（状态报告）或DR或DLR(投放收据)**:由移动设备通过SMPP提供商发送给Adobe Campaign的返回回执，指示SMS已成功接收。Adobe Campaign还可能收到指示无法传递消息的SR，通常包含错误的描述。

您需要区分鸣谢（RESP PDU， SMPP协议的一部分）和SR:SR是一种通过网络端对端发送的SMS，而确认只是一次传输成功的确认。

确认和SR都可能触发错误，区分二者将有助于故障排除。

### SMS {#information-sms}携带的信息

短信携带的信息比文本多。 下面是您在SMS中可以找到的列表:

* 文本（限于140字节），表示70到160个字符之间，具体取决于编码。 有关详细信息和限制，请参阅下面的[SMS文本编码](../../delivery/using/sms-protocol.md#sms-text-encoding)。

* 收件人地址，有时称为`ADC`或`MSISDN`。 这就是接收短信的手机数量。

* 发件人地址，可以称为`oADC`，有时也称为`sender id`。 这可以是日常使用中的电话号码、通过提供商发送的简短代码或姓名。 名称是可选功能，在这种情况下，您无法回复SMS。

* 一个标志，用于指示消息是否为Flash消息。 闪存消息是不存储在内存中的弹出窗口。

* 指示是否需要SR的标志。

* 有效日期，之后不允许网络设备重试。

* 一个`data_coding`字段，指示文本的编码。

## SMPP协议{#smpp-protocol}

Adobe Campaign Classic支持SMPP协议3.4版。这是一种广泛的协议，允许向提供商(SMSC)发送SMS并接收SMS和接收。 有关详细信息，请参阅[SMPP文档](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)。

SMS服务提供商端的网络设备通常称为SMSC。

### SMPP连接{#smpp-connections}

Adobe Campaign通过TCP连接到SMS服务提供商的网络设备。 SMPP协议设置从Adobe Campaign到提供程序的永久TCP连接。 TCP连接始终由Adobe Campaign启动，甚至是接收消息。
SMPP会打开1个或2个TCP连接，具体取决于其模式。 所有连接始终由Adobe Campaign启动。

SMPP协议可以在两种模式下工作：

* **发射机+接收机（或TX+RX）**:两个独立的TCP连接用于发送和接收消息。
* **收发器（或TRX）**:单个TCP连接用于发送和接收消息。

>[!NOTE]
>
> Adobe Campaign Classic仅支持TX+RX模式。 这种限制是由于其技术架构。

### SMPP PDU {#smpp-pdu}

SMPP传输单元（“数据包”）称为PDU。 **PDU**&#x200B;包含命令、状态、序列号和数据。

每个PDU必须由`SMPP RESP PDU`（同步响应）进行确认。 请求可以流水线处理：发送方可以发送许多命令而无需等待`RESP`，随时可以流水线处理的请求数称为窗口。 `RESP PDU` 可能以任何顺序到达，而与其相应的启动器PDU的顺序无关。

在分离的&#x200B;**发射器+接收器**&#x200B;模式中，所使用的连接取决于所传输的消息类型。 发射机连接用于MT，接收机连接用于MO和SR。 每种消息的请求和响应都通过同一TCP连接发送。

例如，当发送MT时，使用发射器连接，并且确认MT的`RESP`也通过发射器渠道发送。 当您收到MO（或SR）时，接收器连接用于接收MO并发送确认MO的`RESP`。

![](assets/do-not-localize/sms_protocol_1.png)

在Adobe Campaign Classic中，要将SR与其对应的MT链接，SMSC将返回一个ID，其中包含`SUBMIT_SM_RESP`和`DELIVER_SM`步骤。 标识符存储在`nms::providerMsgId`表的`providerId`字段中，并链接到`broadLogId`和`deliveryId`。 此匹配操作由SMS进程在写入数据库时完成。

成功`SUBMIT_SM_RESP PDU`会触发发送日志中的“已发送”消息状态，而成功`DELIVER_SM (SR) PDU`会触发“已接收”消息状态。

### 安全方面{#security-aspects}

协议本身不加密。 大多数提供商在时实现IP的变允许列表体，因此Adobe Campaign服务器IP地址必须向提供商声明。

Adobe Campaign支持在绑定阶段传递登录名和口令。 它还支持SMPP而不是TLS。 应当指出，需要证书才能获得适当的安全。 尽管SMPP连接器允许绕过证书检查，但它只应用于测试，因为没有证书的TLS提供的安全级别要低得多。

连接器使用系统`openssl`库提供的默认证书。 通常由Debian上的`/etc/ssl/certs`目录提供。 默认情况下，此目录由“ca-certificates”包提供，但可以自定义它。

### 每种PDU{#information-pdu}中的信息

每种PDU都有不同的字段，这些字段携带不同的信息。 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)中详细介绍了这些PDU。

以下各节介绍PDU及其同步响应(`*_RESP PDU`)。 所有PDU都必须由相应的`RESP`进行确认，这是规范的必需部分。

PDU可以有可选字段。 此处只介绍最常见的字段。 有关详细信息，请参阅[SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)。

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_RENSIVER**

此PDU用于启动到SMSC的连接。 **发送器**、 **** 接收 **** 器和收发模式只更改允许通过此连接传输的SMS类型，具体而言：

| 模式 | 允许的短信种类 |
|:-:|:-:|
| 发射机 | MT |
| 接收机 | MO + SR |
| 收发器 | MT + MO + SR |

`BIND_* PDU`中值得注意的字段：

* **system_id**:用于身份验证的登录名。在外部帐户中设置。

* **密码**:用于身份验证的密码。在外部帐户中设置。

* **system_type**:需要为某些提供者设置特定值。在外部帐户中设置，所有版本都提供。 通常区分不同类型的合同、渠道、国家等。

* **addr_** tonand  **addr_npi**:某些提供商要求。由外部帐户中的`Bind TON`和`Bind NPI`设置设置。

* **address_range**:某些提供商要求。大多数情况下，这是在此连接上允许的简短代码列表。 在外部帐户中设置。

`BIND_*_RESP` 没有特定字段，它会确认连接是否成功。

#### 取消绑定{#unbind}

在断开连接之前，必须由系统发送此PDU。 在关闭连接之前，它必须等待匹配的`UNBIND_RESP` PDU。

符合SMSC的TCP连接不能关闭，TCP连接由Adobe Campaign连接器控制。

#### SUBMIT_SM {#submit-sm}

此PDU向SMSC发送MT。 其响应PDU给出MT的ID。

`SUBMIT_SM` PDU中的显着字段：

* **service_type**:提供商。在投放属性中设置。

* **source_addr_** tonand  **source_addr_npi**:指示传输的源地址类型。这些字段的含义是标准化的，但是，由于某些提供者使用它的方式不同，您应要求提供者提供其正确的值。 在外部帐户中设置。

* **source_addr**:MT的源地址/oADC。它将显示在手机上。 在外部帐户和投放中设置，投放中的值优先于外部帐户的值。

* **dest_addr_** ton和 **dest_addr_npi**:指示传输的目标地址类型（例如本地或国际格式）。这些字段的含义是标准化的，但是，由于某些提供者使用它的方式不同，您应要求提供者提供其正确的值。 在外部帐户中设置。

* **destination_addr**:收件人地址、电话号码或MSISDN。

* **esm_class**:用于判断文本字段中是否使用了UDH。如果未使用`message_payload`模式，则连接器会自动启用拆分SMS。

* **priority_flag**:优先于其他人。这与投放本身的优先级相关。

* **validity_period**:不应尝试重试的时间戳。在投放中设置。

* **registered_投放**:指示是否请求SR。Adobe Campaign始终设置此标志，但自动回复除外。 对于多部件消息，仅为第一部分设置标志。 所有版本都具有相同的行为。

* **data_coding**:指示文本字段中使用的编码。有关详细信息，请参阅[SMS文本编码](../../delivery/using/sms-protocol.md#sms-text-encoding)部分。

* **short_message**:消息的文本。如果使用UDH，则还包含UHD头。

Adobe Campaign支持以下可选字段：

* **dest_addr_ubunit**:用于指定SMS的目标:Flash、移动或SIM卡。在投放属性中设置。

* **message_payload**:在外部帐户中启用时，长消息将在单个PDU中发送，文本将在此字段而非字段中 `short_message` 传输。

#### SUBMIT_SM_RESP {#submit-sm-resp}

此PDU将包含MT的ID。 这对于将其与传入SR匹配很有用。

>[!IMPORTANT]
>
>许多提供者以十六进制形式传输MT ID。 确保在外部帐户中正确设置MT确认&#x200B;**中的** ID格式。

在发送SR后，某些提供者发送`SUBMIT_SM_RESP`。 为了解释该行为，Adobe Campaign会等待30秒，然后将&#x200B;**无效消息ID**&#x200B;回复到SR，ID未知。

#### DELIVER_SM {#delivery-sm}

此PDU由SMSC发送给Adobe Campaign。 它包含MO或SR。

大多数字段与其`SUBMIT_SM`对应字段具有相同的含义。 以下是有用字段的列表:

* **source_addr**:MO/SR的源地址。通常这是电话号码。

* **destination_addr**:接收MO或SR的短代码。

* **esm_class**:用于判断PDU是MO还是SR。

* **short_message**:文本。对于SR，它包含SMPP协议规范附录B中描述的数据。 有关详细信息，请参阅[SR错误管理](../../delivery/using/sms-protocol.md#sr-error-management)。

Adobe Campaign能够读取`receipted_message_id`可选字段中的消息ID，并进行某些配置。

#### DELIVER_SM_RESP {#deliver-sm-resp}

此PDU由Adobe Campaign发送以确认SR和MO。

Adobe Campaign Classic在将SR和MO插入数据库后即确认它们。 即使发送了成功的`DELIVER_SM_RESP` PDU，也会发生一些处理错误。 此限制是由Adobe Campaign Classic的软件架构造成的。

#### INQUIRE_LINK {#enquire-links}

此PDU仅用于检查连接是否处于活动状态。 应根据供应商的需要设置其频率。

默认的60秒应与外部帐户中设置的大多数配置相匹配。

#### INQUIRE_LINK_RESP {#enquire-links-resp}

此PDU确认连接是活的。

### 多部SMS（长SMS）{#multipart}

多部分SMS或长SMS是多部分发送的SMS。 由于移动网络协议中的技术限制，SMS不能大于140字节或需要拆分。 请参阅[SMS文本编码](../../delivery/using/sms-protocol.md#sms-text-encoding)部分，进一步了解适合SMS的字符数。

长信息的每个部分都是单独的SMS。 这些部件在网络上独立运行，并由接收手机组装。 为了处理重试和连接问题，Adobe Campaign以反向顺序发送这些部件，并仅在消息的第一部分（即最后发送的部分）上请求SR。 由于手机在收到第一部分时只显示一条消息，因此附加部分上的重试不会在手机上产生重复。

使用&#x200B;**投放模板**&#x200B;中的&#x200B;**每条消息的最大SMS数**&#x200B;设置，可以为每条投放设置最大SMS数。 在发送时，超过此限制的消息将失败，原因是SMS过长。

发送长短信有两种方法：

* **UDH**:发送长消息的默认和推荐方式。在此模式中，连接器将消息拆分为多个`SUBMIT_SM PDU`s，其中包含UDH信息。 此协议是手机本身使用的协议。 这意味着Adobe Campaign对消息生成拥有最大的控制权，从而能够准确计算发送的部件数量和拆分方式。

* **message_payload**:一次发送长信息的方式 `SUBMIT_SM PDU`提供商必须拆分它，这意味着Adobe Campaign不可能确切知道发送了多少部件。 某些提供商需要此模式，但我们建议您仅在它们不支持UDH时使用它。

有关协议和格式的详细信息，请参阅[ SUBMIT_SM PDU](../../delivery/using/sms-protocol.md#information-pdu)的`esm_class`、`short_message`和`message_payload`字段的说明。

### 吞吐量上限和窗口{#throughput-capping}

大多数提供程序要求每个SMPP连接都有吞吐量限制。 这可以通过在外部帐户中设置多个SMS来实现。 请注意，每个连接都会发生吞吐量限制，总有效吞吐量是每个连接的限制乘以连接总数。 这在[同时连接](../../delivery/using/sms-protocol.md#connection-settings)部分中有详细说明。

要达到最大的吞吐量，您需要微调最大发送窗口。 发送窗口是可以发送的`SUBMIT_SM PDU`数，无需等待`SUBMIT_SM_RESP`。 有关详细信息，请参阅[发送窗口设置](../../delivery/using/sms-protocol.md#throughput-timeouts)部分。

### SR和错误管理（“附录B”）{#sr-error-management}

SMPP协议定义`RESP PDU`s中的标准同步错误，但不定义SR的错误代码。 每个提供者使用各自的错误代码及其含义。

在[SMPP协议规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)（第167页）的附录B部分中提出了建议，但这并不列表实际错误代码及其含义。

为了适应错误管理，Adobe Campaign的广播消息系统被用于正确设置错误及其严重性（硬、软等）。

如上所述，存在两种不同的错误：

* `SUBMIT_SM_RESP`中在消息发送到SMSC后立即发生的同步回复
* 可能会在较晚时间，当移动设备收到消息或消息超时时收到。 在这种情况下，在SR中发现错误。

收到SR后，在其`short_message`字段（例如，附录B符合实现）中可找到状态和错误。 PDU的`short_message`字段通常称为&#x200B;**文本字段**，因为它包含MT中的文本。 对于SR，它包含技术信息加上一个名为&#x200B;**Text**&#x200B;的子字段。 这2个字段不同，`short_message`实际包含&#x200B;**Text**&#x200B;字段和其他信息。

Adobe Campaign Classic连接器（扩展SMPP除外）使用硬编码行为，具体取决于选定的提供程序。 通用SMPP仅区分成功和错误，没有详细信息。 投放日志可能包含某些不保证的信息。

#### SR文本字段格式{#sr-text-field-format}

规范建议对SR文本字段使用此格式。 它是子字段的列表，以空格分隔，并带有冒号以分隔字段名称及其值。 字段名称不区分大小写。

与附录B建议匹配的SR文本字段示例：

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

id字段是在`SUBMIT_SM_RESP PDU`（MT的确认）中接收的ID。

`sub` 而 `dlvrd` 且应该计算传递的部件和传递的消息的数量，但这不是Adobe Campaign使用的，因为广播系统提供了更好、更集成的信息。

`submit date` 和字 `done date` 段是指示MT何时发送以及移动设备何时发送SR的时间戳。如果移动设备设置的日期不正确，则可能会遇到时区问题，甚至会出现错误的时间戳。

stat字段很重要，因为它会告知消息的状态。 唯一重要的状态是`DELIVRD`、`UNDELIV`和`REJECTD`。 `DELIVRD`状态表示成功，另两个表示错误。 其他值是可能的，但通常是中间通知，例如MT到达移动运营商，而不是移动电话。 这些中间通知被Adobe Campaign忽略。

错误字段包含提供程序特定的错误代码。 提供者必须提供可能的错误代码表及其含义，才能解释此值。

最后，文本字段通常包含MT文本的开头。 这被Adobe Campaign忽略，某些提供商不会通过传输来避免PII泄漏和网络带宽消耗。 它可在故障排除期间使用，通过阅读此字段更轻松地发现与测试MT匹配的SR。

### Adobe Campaign Classic Extended通用SMPP {#sr-processing}中SR处理示例

此示例显示按附录B建议实施的情况、外部帐户中的默认值和成功的SMS MT。

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

首先，应用`id extraction`正则表达式提取ID并将其与相应的MT协调。

然后，应用`status extraction`正则表达式和`error code extraction`正则表达式以提取这些字段并附加到字符串。

广播消息是使用此信息构建的，并附加原始未更改的字符串作为参考：

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

然后，该消息被标准化，删除MESSAGE部分以能够使多个消息与相同的状态和错误代码匹配。

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

如果广播消息表中尚未设置该消息，则将创建一个新条目，将整个消息用作&#x200B;**firstText**&#x200B;和标准化消息。 然后，连接器使用成功和`error`正则表达式确定成功还是失败：

* 如果它与`success`正则表达式匹配，则会将其视为成功。

* 如果与`error`正则表达式匹配，则消息被限定为错误。

* 如果这两个正则表达式都不匹配，则忽略SR。 它可能是中间通知，不由Adobe Campaign处理。

默认情况下，所有错误都设置为软错误。 这意味着必须手动设置硬错误。

### SMS文本编码{#sms-text-encoding}

如果发生编码问题，应&#x200B;**始终与SMSC提供程序联系。**&#x200B;只有SMSC提供商了解他们支持的编码以及由于其技术平台限制而可能适用的特殊规则。

SMS消息使用特殊的7位编码，通常称为GSM7编码。

在SMPP协议中，GSM7文本将扩展为每个字符8位，以便更轻松地排除故障。 SMSC将在将其发送到移动设备之前将其打包为7位/字符。 这意味着在SMPP帧中，SMS的`short_message`字段最长可达160个字节，而在移动网络上发送时，该字段最长可限制为140个字节。

在编码出现问题时，需要检查以下重要事项：

* 确保您知道哪些字符属于哪个编码。 GSM7不完全支持音符或重音。 在法语中尤其如此，在法语中，é和è是GSM7的一部分，但ê或ï不是。 西班牙语也是如此。

* 带有Cedilla(ç)的C仅在GSM7字母表中的大写中存在，但某些电话将它呈现在小写或“smart”大写中。 一般建议是完全避免这种情况，并删除代码或切换到UCS-2。

* **除非SMSC提供者明确** 请求，否则不要在SMS中使用ASCII。这种编码浪费了空间，因为它具有8位字符，并且比GSM7的覆盖范围更小。 在北美使用的CDMA网络可能需要此编码。

* 不总是支持拉丁语–1。 尝试使用拉丁语–1之前，请检查与SMSC提供商的兼容性。

* 国家语言转换表不受Adobe Campaign连接器支持。 必须改用UCS-2或其他`data_coding`。

* UCS-2和UTF-16通常由电话混合。 在使用UCS-2中不存在的表情符号和其他字符时，这是个问题。

* 大多数手机没有所有UCS-2字符的字体字形。 智能手机往往能够很容易地显示稀有人物，但功能手机通常对它们所购买的国家的母语有用功能的支持有限。 如果要使用emoji或ASCII-art，请在发送前在各种电话上测试它。 Adobe Campaign预览不模拟缺失的字形，并将显示Web浏览器上可用的符号。

`data_coding`字段会告诉您使用的编码。 一个主要问题是，值0表示规范中的默认SMSC编码，通常指GSM7。 请咨询与`data_coding` = 0关联的SMSC合作伙伴，该Adobe Campaign仅支持该项。 其他`data_coding`值往往遵循规范，但确保的唯一方法是与SMSC提供程序进行检查。

消息的最大大小取决于其编码。 下表总结了所有相关信息：

| 编码 | 通常的data_coding | 消息大小（字符） | 多部件SMS的部件大小 | 可用字符 |
|:-:|:-:|:-:|:-:|:-:|
| GSM7 | 0 | 160 | 152 | GSM7基本字符集+扩展（扩展字符为2个字符） |
| 拉丁语–1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode（因电话而异） |

## SMPP外部帐户参数{#SMPP-parameters-external}

SMPP协议的每个实现都有许多不同之处。 为了提高兼容性和适应性，可以使用许多设置来更改SMPP连接器的行为。 本节介绍每个参数及其对连接器的影响。

### 常规参数和路由{#general-parameters-routing}

**限制此帐户的MTA实例**

可以设置允许连接到SMPP提供程序的MTA实例数的限制。 选中后，您最多可以指定可以使用多少MTA。

此选项允许对连接数进行更精细的控制，请参见[同时连接](../../delivery/using/sms-protocol.md#connection-settings)。

如果设置的值高于正在运行的MTA的数量，则所有MTA都将正常运行：此选项仅为限制，无法生成其他MTA。

如果您需要精确控制连接数，例如提供者要求，则建议始终设置此选项，即使当前部署正在运行的MTA数目正确。 如果之后添加了其他MTA，则仍将遵守连接限制。

### 连接设置{#connection-settings}

#### SMSC实现名称{#smsc-implementation-name}

设置SMSC实现的名称。 它应设置为提供者的名称。 请与管理员或交付能力团队联系，了解要在此字段中添加的内容。 在[SR错误管理](../../delivery/using/sms-protocol.md#sr-error-management)部分中介绍了此字段的作用。

#### 服务器{#server}

要连接到的服务器的DNS名称或IP地址。

#### 端口{#port}

要连接到的TCP端口。

#### 帐户{#account}

连接的登录名。 在BIND PDU的`system_id`字段中传递。

#### 密码{#password}

SMPP连接的口令。 在BIND PDU的密码字段中传递。

#### 系统类型{#system-type}

在BIND PDU的`system_id`字段中传递的值。 某些提供商需要此处的特定值。

#### MTA子连接数{#number-mta-child}

在Adobe Campaign Classic中，它定义每个MTA子项的连接数。

Adobe Campaign Classic Extended SMPP连接器可以控制每个MTA子项的连接数。 要控制连接的全局限制，您必须限制MTA子进程的数量，这通常意味着有一个专用的SMS中间源平台。

对于Adobe Campaign Classic，可以有不同数量的接收器和发射器连接：

* **发送器连接= MTA子连接数x MTA子进程数x MTA子进程数x MTA数（如果设置了自动回复）+ MTA子连接数**

如上所述，如果启用了自动回复，Adobe Campaign Classic SMS进程将打开更多的发射器连接。 这些附加连接用于发送自动回复。

* **接收方连接= MTA子连接数**

如果设置自动回复，SMS进程将打开发送机/接收机对，增加发送机连接数。 如果未设置任何自动回复，它将仅打开接收方连接。

#### 在SMPP {#enable-TLS}上启用TLS

使用TLS连接到提供程序。 连接将加密。 TLS连接由OpenSSL库管理，任何适用于OpenSSL的内容对于此连接均为true。

#### 在日志文件{#enable-verbose-log-file}中启用详细的SMPP跟踪

此设置会转储日志文件中的所有SMPP流量。 通常需要在初始设置期间调整参数。 在排除连接器故障时必须启用此功能，并与提供者看到的流量进行比较。

在Adobe Campaign Classic中，日志输出位于与MT相关的通信的MTA日志中，以及与MO和SR相关的通信的SMS日志中。

### 接收器连接设置{#receiver-connection}

此部分仅在分离的&#x200B;**发射器+接收器**&#x200B;模式下可见。

#### 对接收器{#receiver-parameters}使用不同的参数

当该框未选中时，发送器和接收器也使用相同的设置。

选中该框后，**连接设置**&#x200B;部分中的设置将应用于发射机，而&#x200B;**接收机连接**&#x200B;设置中的设置将应用于接收机。

**接收服务器、端口、帐户、密码、系统类型**

这些设置在发射机+接收机模式下应用于接收机。 它们的工作方式与发射器部分类似，有关更多详细信息，请参阅上文。

### SMPP渠道设置{#smpp-channel-settings}

#### 允许字符音译{#allow-character-transliteration}

音译是寻找等效字符与缺失字符的过程。 例如，GSM编码中缺少法文“ê”（带扬抑符）字符，但可以用“e”替换，而不会损害可读性。

如果未选中此框，则文本编码将失败（如果无法按原样对字符串进行编码）。

选中此框后，文本编码将尝试将字符串转换为近似版本，而不是失败。 如果某些字符在目标编码中没有对等项，文本编码将失败。

有关编码过程的更一般说明，请参阅[定义编码设置的特定映射。](../../delivery/using/sms-protocol.md#SMSC-specifics)

#### 在数据库{#incoming-mo-storing}中存储传入的MO

启用后，传入的MO将存储在数据库的inSMS表中。 可以使用任何工作流的查询活动查询此表。

Adobe Campaign Classic始终将所有MO存储在inSMS数据库中，因此此选项不可用。

#### 在SR处理{#real-time-kpi}期间启用实时KPI更新

启用后，当收到错误SR时，KPI将在主投放页上实时更新。

缺点是性能低，因为它会生成数据库争用。 如果禁用，则统计信息将由每20分钟运行一次的&#x200B;**syncfromexec**&#x200B;工作流更新。

Adobe Campaign Classic的KPI机制完全不同，因此此选项不可用。

#### 源编号{#source-number}

定义消息的默认源地址。 此设置仅在源编号在投放中留空时适用。

默认情况下，不会传递源编号字段，因此提供程序将用它替换短代码。

这允许发送者地址/oADC覆盖功能。

#### 短代码{#short-code}

指示帐户的主短代码。 如果此帐户使用了多个短代码，或者短代码未知，请将此字段留空。

指定短代码对以下两个功能有帮助：

* 如果未提供源代码，预览将显示短代码。 它将反映手机上的真实行为。

* 自动阻止列表回复功能的隔离设置仅向用户发送特定短代码。

#### 来源吨/NPI，目标吨/NPI {#ton-npi}

[SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)（第117页）的第5.2.5节中介绍了TON（编号类型）和NPI（编号计划指标）。 这些值应设置为提供程序的需要。

在`SUBMIT_SM PDU`的`source_addr_ton`、`source_addr_npi`、`dest_addr_ton`和`dest_addr_npi`字段中按原样传输。

#### 服务类型{#service-type}

此字段按原样在`SUBMIT_SM PDU`的`service_type`字段中传输。 根据提供商的需要设置此值。

### 吞吐量和超时{#throughput-timeouts}

这些设置控制SMPP渠道的所有时间方面。 某些提供者需要非常精确地控制消息速率、窗口和重试定时。 这些设置应设置为与提供商的容量及其合同中指明的条件相匹配的值。

#### 发送窗口{#sending-window}

窗口是可以发送的`SUBMIT_SM PDU`数，无需等待匹配的`SUBMIT_SM_RESP`。

最大窗口为4的传输示例：

![](assets/do-not-localize/sms_protocol_2.png)

当网络链路具有高延迟时，该窗口有助于提高吞吐量。  窗口的值必须至少是SMS/s的数量乘以链路的等待时间
以秒为单位，因此在发送下一条消息之前，连接器从不等待`SUBMIT_SM_RESP`。
如果窗口太大，您可能会在出现连接问题时发送更多重复消息。 此外，大多数提供商对窗口有非常严格的限制，拒绝超过此限制的消息。

如何计算最佳发送窗口公式：

* 测量`SUBMIT_SM`和`SUBMIT_SM_RESP`之间的最大延迟。

* 将此值以秒为单位乘以最大MT吞吐量。 这将给出最佳发送窗口值。

示例：如果在最大MT吞吐量中设置了300个SMS/s，并且在`SUBMIT_SM`和`SUBMIT_SM_RESP`之间平均有100ms的延迟，则最佳值为`300×0.1 = 30`。

#### 最大MT吞吐量{#max-mt-throughput}

每秒和每个连接的最大MT数。 严格强制执行此设置，MTA将永远不会以超过此限制的速度推送消息。 对于需要精确调节的提供商而言，此功能非常有用。

要了解总吞吐量限制，请将此数字乘以上面公式中详述的连接总数。

0表示无限制，MTA将尽快发送MT。

通常建议将此设置保持在1000以下，因为除非在最终体系结构上进行适当基准测试并明确请求的SMPP提供商，否则无法保证高于此数的精确吞吐量。 将连接数增加到1000 MT/s以上可能更好。

#### 重新连接{#time-reconnection}之前的时间

当TCP连接丢失时，连接器将等待此秒数，然后尝试建立连接。

#### MT {#expiration-period}的过期时间

`SUBMIT_SM`与其匹配的`SUBMIT_SM_RESP`之间的超时。 如果未按时收到`RESP`，则消息将被视为失败，并且MTA的全局重试策略将适用。

#### 绑定超时{#bind-timeout}

TCP连接尝试与`BIND_*_RESP`回复之间的超时。 超时时，连接由Adobe Campaign连接器关闭，在重新连接之前，它将等待时间。

#### inquire_link期间{#enquire-link-period}

`enquire_link` 是发送的一种特殊PDU，用于保持连接生效。此时段以秒为单位。 活动连接器仅在连接空闲时发送`enquire_link`以节省带宽。 如果在此时间段后未收到RESP，则连接将被视为死机，并将触发重新连接过程。

### SMSC 详情{#SMSC-specifics}

这些设置是高级设置，可使Adobe Campaign连接器适应大多数SMPP实现特性。

**定义编码的特定映射**

有关文本编码的详细信息，请参阅[SMS文本编码](../../delivery/using/sms-protocol.md#sms-text-encoding)部分。

此设置允许您定义自定义编码映射（不同于规范）。 您将能够声明编码的列表及其`data_coding`值。

MTA将尝试使用列表中的第一个编码进行编码。 如果失败，它将尝试在列表上使用下一个编码，等等。 如果不能使用编码对消息进行编码，则会发生错误。 找到编码后，MTA将创建`SUBMIT_SM PDU`，并设置编码文本和`data_coding`字段，其值在表中指定。

表中项目的顺序很重要：编码尝试从上到下。 您应将最便宜或最推荐的编码放在列表顶部，然后是越来越昂贵的编码。

请注意，UCS-2永远不会失败，因为它可以对Adobe Campaign支持的所有字符进行编码，并且UCS-2 SMS的最大长度要小得多：仅70个字符。

您还可以使用此设置，通过在映射表中仅声明1行来强制始终使用特定编码。

未选中复选框时使用的默认映射与下表相同：

| data_coding | 编码 |
|---|---|
| 0 | GSM |
| 9 | UCS-2 |

这意味着MTA将尝试在GSM中对消息进行编码。 如果成功，它将在`data_coding`设置为0时发送。

如果消息无法在GSM中编码，则它将在UCS-2中编码，并将`data_coding`设置为8。

#### 启用message_payload {#enable-message-payload}

如果未选中，长SMS将被MTA拆分，并与UDH一起以多个`SUBMIT_SM PDU`s发送。 消息将由手机按照UDH数据重组。

选中后，长SMS将在一个SUBMIT_SM PDU中发送，并将文本放在message_payload可选字段中。 有关此的详细信息，请参见[SMPP规范](../../delivery/using/sms-protocol.md#ACS-SMPP-connector)。

如果启用此功能，Adobe Campaign将无法单独计算SMS部件：所有消息将计为一部分发送。

#### 发送完整电话号码{#send-full-phone-number}

如果未选中此复选框，则只向提供者发送电话号码的数字（`SUBMIT_SM`字段的`destination_addr`字段）。 这是默认行为，因为SMPP中的国际数字指示符（通常为+前缀）被TON和NPI字段替换。

选中此复选框后，将按原样发送电话号码，没有预处理和潜在空格，+前缀或井号/哈希/星号。

此功能还会影响自动回复功能的阻止列表行为：如果未选中此复选框，将在插入隔离表的电话号码中添加+前缀，以补偿SMPP协议本身从电话号码中删除的+前缀。

#### 跳过TLS证书检查{#skip-tls}

启用TLS后，跳过所有证书检查。

如果选中此项，则连接不再安全，不应在生产中启用。

它可用于调试或测试目的。

您可以在三种不同的证书验证值之间进行选择：

* 默认为完整认证检查（包括主机名）。
* 跳过主机名验证。
* 跳过证书验证。

#### 绑定TON/NPI {#bind-ton-npi}

[SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)（第117页）第5.2.5节中描述的TON（编号类型）和NPI（编号计划指标）。 这些值应设置为提供程序需要的任何值。

在BIND PDU的`addr_ton`和`addr_npi`字段中按原样传输它们。

#### 地址范围{#address-range}

在BIND PDU的address_range字段中按原样发送。 此值应设置为提供程序需要的任何值。

#### 无效的ID确认计数{#invalid-id}

限制可为单个SR发送的&#x200B;**消息ID无效** `DELIVER_SM_RESP`的数量。

**这应仅用于作为工作环境进行故** 障排除，并在正常情况下设置为0。

Fox示例，当设置为2时：

* 提供程序发送ID为“1234”的SR(`DELIVER_SM`)。

* 在数据库中找不到ID“1234”。

* 连接器对该ID计数1 **无效ID**&#x200B;错误，因此它使用“消息ID无效”错误代码（正常行为）发送`DELIVER_SM_RESP`。

* 提供商重试ID为“1234”的同一SR。

* 在数据库中仍然找不到ID“1234”。

* 连接器对该ID计数2 **无效ID**&#x200B;错误，因此它发送`DELIVER_SM_RESP` &quot;OK&quot;，即使未正确处理也是如此。

* 当无效的SR块合法且无法处理消息时，此功能旨在刷新提供方端的SR缓冲区。

将此字段设置为0将禁用始终返回&#x200B;**消息ID invalid**&#x200B;的机制，这是正常行为。

将此字段设置为1会使连接器始终响应“OK”（确定），即使ID无效。 应将此值设置为1（仅在监管下），以排除故障并在最短时间内（例如从提供方问题中恢复）。

#### 提取SR {#regex-extraction}中ID的正则表达式

SR格式未严格由SMPP协议规范执行。 它只是说明书[附录B](../../delivery/using/sms-protocol.md#sr-error-management)（第167页）中描述的建议。 某些SMPP实现器以不同格式设置此字段，因此Adobe Campaign需要一种方法提取正确的字段。

默认情况下，它在`id:`后最多捕获10个字母数字字符。

正则表达式必须只有一个捕获组，且括号中包含一个部分。 括号必须包围ID部分。 正则表达式格式为PCRE。

在调整此设置时，请务必尽可能多地包含上下文以避免出现虚假触发器。 如果有特定前缀，如标准中的`id:`，则在正则表达式中包括这些前缀。 还尽可能使用单词分隔符(\b)来避免捕获单词中间的文本。

正则表达式中不包含足够的上下文可能会引入一个小的安全漏洞：SR中可以包含消息的实际内容。 如果仅匹配没有上下文的特定ID格式（如UUID），则它可能正在分析实际文本内容，如嵌入在文本字段中的UUID，而不是ID。

#### 已应用正则表达式以确定成功/错误状态{#regex-applied}

当遇到具有未知stat/err字段组合的消息时，这些正则表达式将应用于stat字段，以确定SR是成功还是错误。 将忽略不匹配任何这些regex的stat值的SR。

默认情况下，以`DELIV`开头的stat值，例如[附录B](../../delivery/using/sms-protocol.md#sr-error-management)中的`DELIVRD`将被视为已成功传送，且所有与错误匹配的stat值，例如`REJECTED`、`UNDELIV`被视为错误。

#### MT确认{#id-format-mt}中的ID格式

这表示在`SUBMIT_SM_RESP PDU`的`message_id`字段中返回的ID的格式。

* **请勿修改**:该ID按原样存储在数据库中，作为ASCII编码的文本。不进行预处理或过滤。

* **小数**:ID应为ASCII格式的十进制数。使用此设置时，将删除前导和尾随空格以及前导零。

* **十六进制数字**:ID应为ASCII格式的十六进制数，不带前导0x，也不带尾随h。ID随后将转换为十进制数字，然后存储在数据库中。

* **十六进制字符串**:ID应为ASCII编码的文本，它本身是一个字节字符串，以十六进制编码。例如，在PDU中，您会找到`0x34 0x31 0x34 0x32 0x34 0x33` ，它转换为ASCII &quot;414243&quot;。 然后，该字符串被解码为字节的十六进制字符串，因此您获得“ABC”：您将在数据库中存储ID“ABC”。

#### SR {#id-format-sr}中的ID格式

这表示由SR中ID的`Extraction`正则表达式捕获的ID的格式。 值与上述MT中的格式具有相同的含义和行为。

**可选字段中的SR ID或错误代码**

>[!NOTE]
>
>仅在Adobe Campaign Classic Extended SMPP连接器中可用。

如果选中，则可选字段的内容将附加到以上区域处理的文本。 文本的格式为`0xTAG:VALUE`, `0xTAG`是大写标记的4位十六进制值，例如`0x002E`。

例如，您可能希望在`receipted_message_id`字段中捕获ID。 为此，请启用此复选框，以下文本将添加到状态：

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

在此示例中，0x001E是可选字段的标记，UUID是字段的值。

为了捕获此值，您现在可以在SR字段中ID的提取正则表达式中设置以下正则表达式：

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>只能捕获具有文本(ASCII/UTF-8)值的可选字段。 具体而言，无法使用当前正则表达式系统可靠地捕获二进制字段。

**文本字段中的SR ID或错误代码**

如果选中，则在处理SR的状态文本期间将保留&#x200B;**Text**&#x200B;字段。

如果提供程序在此字段中放置重要数据（如ID或状态），则此功能很有用。 通常，此字段可以安全地被丢弃，因为它可能包含具有非ASCII编码的文本并中断正则表达式处理。

如果SR字段中ID的`Extraction`正则表达式不够具体，启用此选项可能会引入非常小的安全漏洞。 **Text**&#x200B;字段的内容可以解析为ID，攻击者可以使用它插入伪造的ID，这可能导致部分拒绝服务情况。

**服务ID标记**

允许添加自定义TLV。 此字段设置标记部分。 可以根据&#x200B;**服务中的投放或投放高级参数中的项目ID**&#x200B;值自定义该值。

此设置只允许为每个消息添加一个TLV选项。

### 发送给 MO 的自动回复{#automatic-reply}

>[!IMPORTANT]
>
>在Adobe Campaign Classic和混合架构中，对扩展SMPP连接器应用自动回复要求在&#x200B;**外部帐户**&#x200B;文件夹上为mid运算符添加写访问。

此功能允许快速将文本回复给MO并处理发送给的每短代码阻止列表。

**关键字**&#x200B;和&#x200B;**短代码**&#x200B;列定义触发自动回复的条件。 如果两个字段都匹配，则发送MO并触发其他操作。 要指定通配符，应将字段留空。 关键字与MO文本中的第一个字母数字词匹配，忽略标点和前导空格。 这意味着&#x200B;**Keyword**&#x200B;字段不能包含空格，且必须是单个字。

**Keyword**&#x200B;设置是前缀。 例如，如果您指定“AD”，它将匹配“AD”、“ADAPT”和“ADOBE”。 如果您有多个带有公共前缀的关键字，则需要注意订单，因为关键字是自上而下处理的。

**Reply**&#x200B;列是要回复的文本。 此字段中不提供任何个性化。 如果将此字段留空，则不会回复任何消息，但仍将触发其他操作。

当&#x200B;**Additional action**&#x200B;列&#x200B;**Keyword**&#x200B;和&#x200B;**Short code**&#x200B;匹配时，空短代码与所有短代码匹配时，该列会提供额外的操作。 您可以发送到隔离或从隔离中删除文本，并且不考虑对文本的回复。 如果指定&#x200B;**其他操作**，但将&#x200B;**回复**&#x200B;字段留空，则将执行操作，但不会发送回复。 隔离仅应用于指定的短代码，如果字段留空，则应用所有短代码。

>[!IMPORTANT]
>
>发送完整电话号码设置对自动回复隔离机制的行为有影响：如果未选中“发送完整电话号码”，则输入隔离的电话号码将用加号(“+”)前缀，以使其与国际电话号码格式兼容。

表中的所有条目将按指定顺序处理，直到一个规则匹配。 如果多个规则与一个MO匹配，则只应用最顶层的规则。

## SMS投放模板参数{#sms-delivery-template-parameters}

某些参数可以按投放模板设置。

### 从字段{#from-field}

此字段为可选字段。 它允许覆盖发送者地址(oADC)。 此字段的内容放在`SUBMIT_SM PDU`的`source_addr`字段中。

SMPP规范将字段限制为21个字符，但某些提供者可能允许更长的值。 另请注意，在某些国家/地区可能会应用非常严格的限制，例如，长度、内容和允许的字符。

### 投放参数 {#delivery-parameters}

#### 每条消息{#maximum-sms}的最大SMS数

此设置仅在&#x200B;**消息有效负荷**&#x200B;设置被禁用时有效。 如果消息需要比此值更多的SMS，将触发错误。

SMS协议将SMS限制在255个部分，但一些手机很难将长消息与大约10个部分组合起来，这一限制取决于确切模型。 我们建议您不要浏览每封邮件的5部分。

由于个性化消息在Adobe Campaign中的作用，消息的大小可能有所不同。 发送大量长消息可能会增加发送成本。

#### 传输模式{#transmission-mode}

此字段指示要传输的SMS类型：正常或闪存消息，存储在手机或SIM卡上。

此设置将在`SUBMIT_SM PDU`的`dest_addr_subunit`可选字段中传输。

* **未** 指定的PDU中不发送任何可选字段。

* **** Flash将值设置为1。它发送一个闪存消息，该消息弹出到移动设备上且不存储在内存中。

* **** 标准化将值设置为0。它发出了一条普通的信息。

* **在移动** 设备上保存会将值设置为2。它让电话把短信存储在内存中。

* **在终止时** 保存会将值设置为3。它让手机把手机短信存储在SIM卡中。

#### 有效期{#validity-period}

有效期在`SUBMIT_SM PDU`的`validity_period`字段中传输。 日期始终以绝对UTC时间格式设置，日期字段将以“00+”结尾。

## 扩展的通用SMPP连接器{#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

箭头表示数据流。

发送投放部件时，MTA生成MTA子项。 MTA子进程的数量是动态的，取决于serverConf.xml中的配置。 每个MTA子级都实例化连接到SMPP提供程序的连接器`CSmppConnectorWorker`。 只要MTA子项保持活动，连接就保持活动状态，也可在serverConf.xml中进行配置。

SMS进程只处理SR，它连接到提供者并保持连接打开。 该进程每10分钟重新连接一次以重新加载新设置，这是正常操作。

### 匹配MT、SR和广播条目{#matching-mt}

中间表`nmsProviderMsgId`用于临时存储MT和SR数据，然后异步提交到广播。

`nmsProviderMsgId` 表包含3组列：

* 在发送和确认MT时更新的列：`iBroadLogId`, `iDeliveryId`

* 收到SR时更新的列：`iMsgId`, `iStatus`

* 始终更新的列：`tsCreated`, `sProviderId`

当MT和SR都完成处理后，您应该有完整的行，其中包含广播信息和状态信息。

此处，`iMsgId`链接到`nmsBroadLogMsg`表，指示完整状态/错误消息。

SMS流程每分钟检查完整行，然后异步处理：

* 将读取完整行。
* SMS进程基于投放映射计算广播表的名称。
* SMS进程使用消息ID和状态更新广播表。

**吞吐量和并行连接**

每个MTA子级创建可配置的连接数，因此限制MTA子级的数量将限制连接数。 由于MTA子进程与流量之间的相关性是相关的，因此这可以有些控制，但仍有些不可预测。

## 在上线前{#checklist}

此清单提供了上线前应检查的列表。 设置不完整可能会导致许多问题。

### 检查外部帐户冲突{#external-account-conflict}

检查您没有旧的SMS外部帐户。 如果将测试帐户保留为禁用状态，则可能会在生产系统上重新启用该帐户并生成潜在冲突。

如果您在连接到同一提供程序的同一Adobe Campaign实例上有多个帐户，请与提供程序联系，以确保它们实际区分这些帐户之间的连接。 拥有多个具有相同登录名的帐户需要额外配置。

### 在检查{#enable-verbose}期间启用详细的SMPP跟踪

您应始终在检查期间启用详细的SMPP跟踪。
即使您无法亲自检查日志，[Adobe客户服务中心](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)也会更轻松地为您提供帮助。

### 测试SMS {#test}

* **发送包含各种字符**
的SMS如果您需要发送包含非GSM或非ASCII字符的SMS，请尝试尽可能发送包含多种字符的消息。如果设置自定义字符映射表，请至少为所有可能的对象发送一个SMS 
`data_coding` values.

* **检查SR是否正**
确处理SR应在投放日志中将SMS标记为已接收。投放日志应成功，如下所示：

检查您是否更改了投放提供程序名称。 投放日志不应包含    `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
检查您是否更改了投放提供程序名称。投放日志在生产环境上不应包含**SR Generic**。

* **检查是否已处**
理MO如果需要处理MO（自动回复，将MO存储在数据库中等）试着做些测试。 发送几条短信，查看所有自动回复关键字，并检查回复是否足够快，不超过几秒。
签入Adobe Campaign成功回复的日志 
`DELIVER_SM_RESP` (command_status=0)。

### 检查PDU {#check-pdus}

即使消息看起来成功，检查PDU的格式是否正确也很重要。

连接到以前未连接到Adobe Campaign的提供程序时，此步骤是必需的。

#### BIND {#bind}

检查是否已正确发送`BIND_* PDUs`。 要检查的最重要的一点是提供程序始终返回成功的`BIND_*_RESP PDUs`(command_status = 0)。

检查`BIND_* PDU`s不太多。如果其中太多，则可能表明连接不稳定。 有关详细信息，请参阅[连接不稳定的问题](../../delivery/using/sms-protocol.md#issues-unstable-connection)部分。

#### INQUIRE_LINK {#enquire-link-pdus}

检查连接空闲时是否定期交换`ENQUIRE_LINK PDU`s。

**SUBMIT_SM / DELIVER_SM**

发送消息，然后在日志中搜索相应的`SUBMIT_SM`、`SUBMIT_SM_RESP`、`DELIVER_SM`和`DELIVER_SM_RESP PDU`。

使用`SUBMIT_SM PDU`:

* 检查`data_coding`是否正确，默认情况下为0。
* 检查`short_message`是否已正确编码。 尝试使用支持多个编码的十六进制转换器对其进行解码。

使用`SUBMIT_SM_RESP PDU`:

* 检查是否成功，command_status = 0。
* 检查其正文是否包含格式正确的ID，后跟“0”字节。

使用`DELIVER_SM PDU`:

* 解码十六进制`short_message`字段。
* 使用正则表达式检查工具检查在SR中ID的`Extraction`正则表达式中定义的正则表达式是否只返回一个捕获组，并且它捕获消息中的整个ID。
* 检查提取的ID是否与`SUBMIT_SM_RESP`中的ID匹配。
* 检查在SR中状态的`Extraction`正则表达式中定义的正则表达式是否返回stat字段的内容。
* 检查在SR中错误的`Extraction`正则表达式中定义的正则表达式是否返回err字段的内容。

使用`DELIVER_SM_RESP PDU`:

* 检查收到`DELIVER_SM PDU`后是否快速发送，通常不到1秒。
* 检查是否成功，command_status = 0。

### 请咨询提供程序{#provider}

即使您的SMS成功，也要联系提供商以查看所有内容是否都正确。

### 禁用详细SMPP跟踪{#disable-verbose}

完成所有检查后，最后一件事是&#x200B;**禁用详细SMPP跟踪**&#x200B;以不生成太多日志。 即使在生产系统上，您也可以重新启用它们以用于故障排除。
