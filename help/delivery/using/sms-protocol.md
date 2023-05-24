---
product: campaign
title: SMS 连接器协议和设置
description: 了解关于短信连接器的更多信息以及如何配置它
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: SMS
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '8460'
ht-degree: 1%

---

# SMS 连接器协议和设置 {#sms-connector-protocol}



>[!NOTE]
>
>通过本文档，所有对协议、字段名称和值详细信息的引用均参考 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

## 概述 {#overview}

SMS可能仅限于发送无格式的短文本消息，但其简单性使其成为有价值的通信渠道。

发送短信有两种主要方式：

* 用手机手动发送，这是人们之间直接沟通的常用方式。
* 通过Adobe Campaign发送消息的方式从互联网发送。 为此，您需要一个SMS服务提供商，将Internet连接到移动网络。
Adobe Campaign使用SMPP协议向服务提供商发送短信。

本文档将指导您逐步完成Adobe Campaign与SMPP提供商之间的连接设置。

SMPP提供商有时可能偏离官方规范，但Adobe Campaign中的SMS连接器提供了许多选项来调整其行为，以便与大多数提供商兼容。

>[!IMPORTANT]
>
>设置与新提供商的连接可能需要一些技术技能、TCP知识、二进制、十六进制表示和文本编码。 它还需要与提供者积极合作。

### 短信类型 {#sms-types}

通过短信提供商发送大量短信时，您将遇到三种不同类型的短信：

* **短信MT（移动端已终止）**：Adobe Campaign通过SMPP提供商向移动电话发出的短信。

* **SMS MO（发起移动设备）**：移动设备通过SMPP提供商发送到Adobe Campaign的短信。

* **SMS SR（状态报告）或DR或DLR（交货收货）**：移动设备通过SMPP提供商发送到Adobe Campaign的回执，指示短信已成功接收。 Adobe Campaign还可能会收到SR，指示无法传递消息，通常包含错误描述。

您需要区分确认（RESP PDU，SMPP协议的一部分）和SR： SR是一种通过网络端到端发送的SMS，而确认仅是确认一次传输已成功。

确认和SR都可以触发错误，区分两者将有助于进行故障排除。

### 短信携带的信息 {#information-sms}

短信携带的信息比文本多。 下面是您可以在短信中找到的内容列表：

* 文本，长度限制为140字节，根据编码方式，这意味着在70到160个字符之间。 参见 [短信文本编码](sms-protocol.md#sms-text-encoding) 详细信息和限制，请参阅下文。

* 收件人地址，有时称为 `ADC` 或 `MSISDN`. 这是将接收短信的移动设备的号码。

* 可呼叫的发件人地址 `oADC` 有时候 `sender id`. 这可以是日常使用的电话号码、通过提供商发送的短代码或姓名。 名称是一个可选功能，在这种情况下，您无法回复短信。

* 指示消息是否为闪存消息的标志。 闪存消息是不存储在内存中的弹出窗口。

* 指示是否需要SR的标志。

* 有效日期，在此日期之后不允许任何网络设备重试。

* A `data_coding` 字段，指示文本的编码。

## SMPP协议 {#smpp-protocol}

Adobe Campaign Classic支持SMPP协议版本3.4。这是一种广泛使用的协议，允许向提供商(SMSC)发送SMS并接收SMS以及接收。 有关详情，请参阅 [SMPP文档](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

SMS服务提供商端的网络设备通常称为SMSC。

### SMPP连接 {#smpp-connections}

Adobe Campaign通过TCP连接到SMS服务提供商的网络设备。 SMPP协议设置从Adobe Campaign到提供程序的永久TCP连接。 TCP连接始终由Adobe Campaign启动，即使接收消息也是如此。
SMPP会打开1个或2个TCP连接，具体取决于其模式。 所有连接始终由Adobe Campaign启动。

SMPP协议可以在两种模式下工作：

* **发射器+接收器（或TX+RX）**：使用两个单独的TCP连接来发送和接收消息。
* **收发器（或TRX）**：单个TCP连接用于发送和接收消息。

>[!NOTE]
>
> Adobe Campaign Classic仅支持TX+RX模式。 此限制是由于其技术架构造成的。

### SMPP PDU {#smpp-pdu}

SMPP传输单元（“数据包”）称为PDU。 A **PDU** 包含命令、状态、序列号和数据。

每个PDU必须由 `SMPP RESP PDU` （同步响应）。 请求可以流水线：发送者可以发送许多命令而无需等待 `RESP`，可以随时管道处理的请求数称为窗口。 `RESP PDU` 可以任何顺序到达，与它们相应的启动器PDU的顺序无关。

在分隔的 **发射器+接收器** 模式，所使用的连接取决于发送的消息类型。 发射器连接用于MT，接收器连接用于MO和SR。 通过同一TCP连接发送各种消息的请求和响应。

例如，发送MT时，使用发射器连接，并且 `RESP` 确认MT也通过发送器通道发送。 当您收到MO（或SR）时，接收器连接用于接收MO并发送 `RESP` 认可备忘录的条款。

![](assets/do-not-localize/sms_protocol_1.png)

在Adobe Campaign Classic中，要将SR与其对应的MT关联，SMSC会返回一个ID，其中包含 `SUBMIT_SM_RESP` 和 `DELIVER_SM` 步骤。 标识符存储在 `providerId` 字段 `nms::providerMsgId` 表并链接到 `broadLogId` 和 `deliveryId`. 此匹配操作由SMS进程在写入数据库时完成。

成功 `SUBMIT_SM_RESP PDU` 成功时，在发送日志中触发“已发送”消息状态 `DELIVER_SM (SR) PDU` 触发“已接收”消息状态。

### 安全方面 {#security-aspects}

协议本身不加密。 允许列表大多数提供商在上实施IP的变体，因此必须向提供商声明Adobe Campaign服务器IP地址。

Adobe Campaign支持在绑定阶段传递登录名和密码。 它还支持SMPP over TLS。 需要注意的是，要获得适当的安全性，需要证书。 虽然SMPP连接器允许绕过证书检查，但只应将其用于测试，因为没有证书的TLS提供了显着较低的安全级别。

连接器使用系统提供的默认证书 `openssl` 库。 通常由 `/etc/ssl/certs` Debian目录。 默认情况下，“ca-certificates”包会提供此目录，但可以对其进行自定义。

### 各种PDU中的信息 {#information-pdu}

每种PDU都有不同的字段，这些字段包含不同的信息。 有关这些PDU的详情，请参见 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

以下各节都介绍了PDU及其同步响应(`*_RESP PDU`)。 所有PDU都必须由对应的 `RESP`，这是规范的必需部分。

PDU可以有可选字段。 此处仅介绍最常见的字段。 请参阅 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) 了解更多信息。

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

此PDU用于启动与SMSC的连接。 **发射器**， **接收方** 和 **收发器** 模式只会更改允许通过此连接传输的短信类型，具体包括：

| 模式 | 允许的短信类型 |
|:-:|:-:|
| 发射器 | MT |
| 接收方 | MO + SR |
| 收发器 | MT + MO + SR |

中的重要字段 `BIND_* PDU`：

* **system_id**：用于身份验证的登录。 在外部帐户中设置。

* **密码**：用于身份验证的密码。 在外部帐户中设置。

* **system_type**：对于某些提供程序，需要设置为特定值。 在外部帐户中设置（在所有版本中均可用）。 通常区分不同类型的合同、渠道、国家/地区等。

* **addr_ton** 和 **addr_npi**：某些提供商需要。 由 `Bind TON` 和 `Bind NPI` 外部帐户中的设置。

* **address_range**：某些提供商需要。 大多数情况下，这是此连接上允许的短代码列表。 在外部帐户中设置。

`BIND_*_RESP` 没有特定字段，用于确认连接是否成功。

#### 取消绑定 {#unbind}

此PDU必须在断开连接之前由系统发送。 它必须等待匹配 `UNBIND_RESP` PDU。

符合条件的SMSC不得关闭连接，TCP连接由Adobe Campaign连接器控制。

#### SUBMIT_SM {#submit-sm}

此PDU向SMSC发送MT。 其响应PDU提供MT的ID。

中的重要字段 `SUBMIT_SM` PDU：

* **service_type**：某些提供商需要使用此参数。 在投放属性中设置。

* **source_addr_ton** 和 **source_addr_npi**：指示传输的源地址类型。 这些字段的含义是标准化的，但由于某些提供商使用字段的方式有所不同，因此您应该要求提供商提供其正确的值。 在外部帐户中设置。

* **source_addr**：MT的源地址/ oADC。 那个显示在手机上。 在外部帐户和投放中设置，投放中的值优先于外部帐户的值。

* **dest_addr_ton** 和 **dest_addr_npi**：指示传输的目标地址类型（例如，本地或国际格式）。 这些字段的含义是标准化的，但由于某些提供商使用字段的方式有所不同，因此您应该要求提供商提供其正确的值。 在外部帐户中设置。

* **destination_addr**：收件人地址、电话号码或MSISDN。

* **esm_class**：用于判断文本字段中是否使用了UDH。 在以下情况下，连接器将自动启用拆分短信： `message_payload` 未使用模式。

* **priority_flag**：此消息的优先级。 这与投放本身的优先级紧密相关。

* **validity_period**：时间戳，此后不应尝试重试。 在投放本身中设置。

* **registered_delivery**：说明是否请求了SR。 Adobe Campaign始终设置此标记，但自动回复除外。 对于多部分消息，仅为第一部分设置标志。 所有版本都具有相同的行为。

* **数据编码**：指示文本字段中使用的编码。 请参阅 [短信文本编码](sms-protocol.md#sms-text-encoding) 部分以了解更多信息。

* **short_message**：消息的文本。 如果使用UDH，则其中还包含UHD标头。

Adobe Campaign支持以下可选字段：

* **dest_addr_subunit**：用于指定短信的目标：闪存、移动或SIM卡。 在投放属性中设置。

* **message_payload**：在外部帐户中启用时，长消息将在单个PDU中发送，文本将在此字段中传输，而不是 `short_message` 字段。

#### SUBMIT_SM_RESP {#submit-sm-resp}

此PDU将包含MT的ID。 这有助于将其与传入的SR进行匹配。

>[!IMPORTANT]
>
>许多提供商以十六进制格式传输MT ID。 确保设置 **MT确认中的ID格式** 正确设置外部帐户。

某些提供商发送 `SUBMIT_SM_RESP` 发送SR之后。 为了解释这种行为，Adobe Campaign会等待30秒再进行回复 **消息ID无效** 到具有未知ID的SR。

#### DELIVER_SM {#delivery-sm}

此PDU由SMSC发送到Adobe Campaign。 它包含MO或SR。

大多数字段与它们的含义相同 `SUBMIT_SM` 对应。 以下是有用字段的列表：

* **source_addr**：MO/SR的源地址。 通常这是一个电话号码。

* **destination_addr**：接收MO或SR的简短代码。

* **esm_class**：用于判断PDU是MO还是SR。

* **short_message**：消息的文本。 对于SR，它包含SMPP协议规范的附录B中描述的数据。 参见 [SR错误管理](sms-protocol.md#sr-error-management) 了解更多详细信息。

Adobe Campaign能够读取中的消息ID `receipted_message_id` 可选字段，带有一些配置。

#### DELIVER_SM_RESP {#deliver-sm-resp}

此PDU由Adobe Campaign发送，用于确认SR和MO。

将SR和MO插入数据库后，Adobe Campaign Classic会确认它们。 即使成功，也可能会发生一些处理错误 `DELIVER_SM_RESP` 已发送PDU。 此限制是由Adobe Campaign Classic的软件架构造成的。

#### ENQUIRE_LINK {#enquire-links}

此PDU仅用于检查连接是否处于活动状态。 其频率应根据提供商的需求进行设置。

默认的60秒应与外部帐户中设置的大多数配置匹配。

#### ENQUIRE_LINK_RESP {#enquire-links-resp}

此PDU确认连接处于活动状态。

### 多部分SMS（长SMS） {#multipart}

>[!IMPORTANT]
>
> Adobe Campaign仅支持发送多部分短信或长短信。 UDH和 `message_payload` 不支持传入短信(MO)，这意味着MO限制为160个字符。

多部分SMS或长SMS是以多个部分发送的短信。 由于移动网络协议中的技术限制，短信不能大于140字节，否则需要拆分。 请参阅 [短信文本编码](sms-protocol.md#sms-text-encoding) 部分以了解有关短信中可容纳的字符数的更多信息。

长消息的每个部分都是单独的短信。 这些部件在网络上独立运行，并由接收手机组装。 为了处理重试和连接问题，Adobe Campaign以反向顺序发送这些部分，并仅在消息的第一部分（即最后发送的那一部分）请求SR。 由于移动电话只在收到其第一部分时显示消息，因此对其他部分的重试不会在移动电话上产生重复项。

可以使用设置每次投放的每条消息的短信最大数量 **每条消息的最大短信数** 在中设置 **投放模板**. 超过此限制的消息在发送期间将会失败，并且短信失败原因太长。

有2种方法可发送长短信：

* **UDH**：发送长消息的默认和推荐方式。 在此模式下，连接器将消息拆分为多个 `SUBMIT_SM PDU`包含了UDH信息。 此协议是移动电话本身使用的协议。 这意味着Adobe Campaign对消息生成具有最大控制权，能够准确计算发送了多少个部分以及它们是如何拆分的。

* **message_payload**：在单个发件人中发送整个长消息的方式 `SUBMIT_SM PDU`. 提供商将必须拆分该部分，这意味着Adobe Campaign无法确切知道已发送了多少个部分。 某些提供商需要此模式，但我们建议您仅在它们不支持UDH时才使用它。

请参阅 `esm_class`， `short_message` 和 `message_payload` 字段 [SUBMIT_SM PDU](sms-protocol.md#information-pdu) 以了解有关协议和格式的更多详细信息。

### 吞吐量上限和窗口 {#throughput-capping}

大多数提供程序要求每个SMPP连接的吞吐量限制。 这可以通过在外部帐户中设置大量短信来实现。 请注意，吞吐量限制发生在每个连接上，总有效吞吐量是每个连接的限制乘以连接总数。 有关详情，请参见 [同时连接](sms-protocol.md#connection-settings) 部分。

要达到最大可能的吞吐量，您需要微调最大发送窗口。 发送窗口是 `SUBMIT_SM PDU`可以发送，而无需等待 `SUBMIT_SM_RESP`. 请参阅 [发送窗口设置](sms-protocol.md#throughput-timeouts) 部分以了解更多详细信息。

### 服务请求和错误管理（“附录B”） {#sr-error-management}

SMPP协议定义中的标准同步错误 `RESP PDU`s，但它没有为SR定义错误代码。 每个提供商都使用各自的错误代码及其含义。

建议见本报告附录B部分。 [SMPP协议规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) （第167页），但这并未列出实际错误代码及其含义。

为了适应错误管理，已利用Adobe Campaign的broadlog消息系统正确配置错误及其严重性（硬、软等）。

如上所述，有两种不同的错误：

* 中的同步回复 `SUBMIT_SM_RESP` 在消息发送至SMSC后立即发生
* 可能在移动设备收到消息或消息超时后很晚才收到的回执。 在这种情况下，该错误可在SR中找到。

收到SR时，可在其SR中找到状态和错误 `short_message` 字段（例如，符合实施的附录B）。 此 `short_message` PDU的字段通常称为 **文本字段** 因为它包含MT格式的文本。 对于SR，它包含技术信息以及一个名为的子字段 **文本**. 这2个字段是不同的，并且 `short_message` 实际上包含 **文本** 字段和其他信息。

Adobe Campaign Classic连接器（扩展SMPP除外）使用取决于所选提供商的硬编码行为。 通用SMPP只区分成功和错误，不提供详细信息。 投放日志可能包含一些不保证的信息。

#### SR文本字段格式 {#sr-text-field-format}

该规范建议对SR文本字段使用此格式。 它是子字段的列表，用冒号分隔以分隔字段名称及其值。 字段名称不区分大小写。

与附录B推荐匹配的SR文本字段示例：

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

ID字段是中收到的ID `SUBMIT_SM_RESP PDU`，对MT的认识。

`sub` 和 `dlvrd` 应计算已投放部件和已投放消息的数量，但Adobe Campaign不使用此项，因为broadlog系统可提供更好、更集成的信息。

`submit date` 和 `done date` 字段表示发送MT的时间以及移动设备发送SR的时间戳。 预期存在时区问题，甚至时间戳由日期集不正确的移动设备给出的错误。

stat字段非常重要，因为它可告知消息的状态。 唯一重要的状态为 `DELIVRD`， `UNDELIV` 和 `REJECTD`. 此 `DELIVRD` 状态表示成功，其他两个表示错误。 可以使用其他值，但它们通常是中间通知，例如MT到达了移动运营商，但未到达移动电话。 Adobe Campaign会忽略这些中间通知。

err字段包含特定于提供程序的错误代码。 提供程序必须给出一个可能的错误代码表及其含义，才能解释此值。

最后，文本字段通常包含MT文本的开头。 Adobe Campaign会忽略这一点，并且一些提供商不会传输此信息，以避免PII泄漏和网络带宽消耗。 在故障排除期间，可阅读此字段以更轻松地发现与测试MT匹配的SR。

### Adobe Campaign Classic Extended generic SMPP中的SR处理示例 {#sr-processing}

此示例显示了遵循附录B建议的实施案例、外部帐户中的默认值以及成功的SMS MT。

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

首先， `id extraction` 正则表达式用于提取ID并将其与相应的MT进行对帐。

然后， `status extraction` 正则表达式和 `error code extraction` 应用正则表达式来提取这些字段，并将其附加到字符串中。

broadlog消息是使用此信息构建的，原始未更改的字符串将被附加以供参考：

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

然后，对消息进行标准化，删除MESSAGE部分，以便能够将多个消息与相同的状态和错误代码进行匹配。

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

如果消息尚未在broadlog消息表中预配，则将创建一个新条目，并将整个消息用作 **第一文本** 和规范化消息。 然后，连接器使用成功和 `error` 用于确定是成功还是失败的正则表达式：

* 如果它与 `success` 正则表达式，则被视为成功。

* 如果它与 `error` 正则表达式，则消息被限定为错误。

* 如果这两个正则表达式都不匹配，则会忽略SR。 它可能是不由Adobe Campaign处理的中间通知。

默认情况下，所有错误都会设置为软错误。 这意味着必须手动配置硬错误。

### 短信文本编码 {#sms-text-encoding}

您应该 **如果出现编码问题，请始终联系SMSC提供商**. 只有SMSC提供商了解他们支持的编码以及由于其技术平台的限制而可能适用的特殊规则。

SMS消息使用特殊的7位编码，通常称为GSM7编码。

在SMPP协议中，GSM7文本将扩展为每个字符8位，以方便故障排除。 SMSC会将其打包为每个字符7位，然后再发送到移动设备。 这意味着 `short_message` 短信的字段在SMPP帧中可能长达160字节，而在移动网络上发送时限制为140字节。

如果出现编码问题，请检查以下重要事项：

* 确保您知道哪些字符属于哪种编码。 GSM7不完全支持变音标记或重音符号。 尤其是在法语中，é和ï是GSM7的一部分，但ê、â或ï不是。 西班牙语也是如此。

* 带有cedilla (c)的C在GSM7字母表中仅以大写形式出现，但有些手机以小写或“智能”大小写形式呈现。 一般建议是完全避免这种情况并删除cedilla或切换到UCS-2。

* **请勿在短信中使用ASCII** 除非SMSC提供程序明确要求。 此编码会浪费空间，因为它有8位字符且覆盖范围比GSM7小。 北美使用的CDMA网络可能需要此编码。

* 并非始终支持Latin-1。 在尝试使用Latin-1之前，请检查与您的SMSC提供商的兼容性。

* Adobe Campaign连接器不支持国家语言转换表。 您必须使用UCS-2或其他 `data_coding` 而是。

* UCS-2和UTF-16经常被手机混合使用。 当使用表情符号和UCS-2中不存在的其他字符时，会出现此问题。

* 大多数手机没有所有UCS-2字符的字体字形。 智能手机往往能够轻松显示稀有字符，但功能型手机通常只能提供有限的支持，以它们购买所在国家的母语为主题。 如果要使用emoji或ASCII-art，请在发送前在多种手机上进行测试。 Adobe Campaign预览不会模拟缺少的字形，而是会显示Web浏览器上可用的符号。

此 `data_coding` 字段告诉您使用哪种编码。 主要问题是，值0表示规范中的默认SMSC编码，通常指GSM7。 与编码相关联的SMSC合作伙伴核实 `data_coding` = 0，即Adobe Campaign仅支持的值。 其他 `data_coding` 值通常遵循规范，但唯一确定的方法是与SMSC提供程序确认。

消息的最大大小取决于其编码。 下表总结了所有相关信息：

| 编码 | 常用数据编码 | 消息大小（字符） | 多部分SMS的部分大小 | 可用字符 |
|:-:|:-:|:-:|:-:|:-:|
| GSM 7 | 0 | 160 | 152 | GSM7基本字符集+扩展（扩展字符占2个字符） |
| Latin-1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode（因手机而异） |

## SMPP外部帐户参数 {#SMPP-parameters-external}

SMPP协议的每个实施都有许多变化。 为了提高兼容性和适应性，可以使用许多设置来更改SMPP连接器的行为。 本节介绍每个参数及其对连接器的影响。

### 常规参数和路由 {#general-parameters-routing}

**限制此帐户的MTA实例**

可以设置允许连接到SMPP提供商的MTA实例数限制。 选中后，您可以指定最多可以使用多少个MTA。

此选项允许更好地控制连接数，请参见 [同时连接](sms-protocol.md#connection-settings).

如果设置的值高于正在运行的MTA的数量，则所有MTA都将正常运行：此选项只是一个限制，不能生成其他MTA。

如果您需要精确控制连接数（如提供程序要求），建议始终设置此选项，即使当前部署运行了正确数量的MTA也是如此。 如果之后添加其他MTA，则连接限制仍将得到遵守。

### 连接设置 {#connection-settings}

#### SMSC 实施名称 {#smsc-implementation-name}

设置SMSC实施的名称。 应将其设置为提供商的名称。 请联系管理员或可投放性团队，以了解要在此字段中添加的内容。 此字段的角色在中进行了描述 [SR错误管理](sms-protocol.md#sr-error-management) 部分。

#### 服务器 {#server}

要连接的服务器的DNS名称或IP地址。

#### 端口 {#port}

要连接的TCP端口。

#### 帐户 {#account}

连接的登录名。 传入 `system_id` 绑定PDU的字段。

#### 密码 {#password}

SMPP连接的密码。 在BIND PDU的密码字段中传递。

#### 系统类型 {#system-type}

传入的值 `system_id` 绑定PDU的字段。 某些提供商需要在此指定特定值。

#### MTA 子连接数 {#number-mta-child}

在Adobe Campaign Classic中，它定义每个MTA子级的连接数。

Adobe Campaign Classic Extended SMPP连接器可以控制每个MTA子级的连接数。 要控制连接的全局限制，您必须限制MTA子进程的数量，这通常意味着为SMS提供专用的中间源平台。

对于Adobe Campaign Classic，可以有其他数量的接收器和发射器连接：

* **发射器连接= MTA子连接数* MTA子进程数* MTA数 </br> （如果已设置自动回复）+ MTA子连接数**

如上所述，如果启用了自动回复，Adobe Campaign Classic短信流程会打开更多发送器连接。 这些额外的连接用于发送自动回复。

* **接收方连接= MTA子连接的数量**

如果您设置了自动回复，短信流程将打开发送器/接收器对，从而增加发送器连接的数量。 如果您未设置任何自动回复，它将只打开接收器连接。

#### 通过 SMPP 启用 TLS {#enable-TLS}

使用TLS连接到提供程序。 连接将被加密。 TLS连接由OpenSSL库管理，任何适用于OpenSSL的内容都将对此连接设置为true。

#### 在日志文件中启用详细的 SMPP 跟踪 {#enable-verbose-log-file}

此设置将所有SMPP通信量转储到日志文件中。 在初始设置过程中，通常需要调整参数。 在对连接器进行故障诊断时，必须启用此项，并将其与提供商看到的流量进行比较。

在Adobe Campaign Classic中，日志输出位于MT相关流量的MTA日志中，以及与MO和SR相关的流量的SMS日志中。

### 接收器连接设置 {#receiver-connection}

此分区仅以分隔形式显示 **发射机+接收机** 模式。

#### 为接收器使用不同的参数 {#receiver-parameters}

如果取消选中该框，则会对发射器和接收器使用相同的设置。

选中该框后， **连接设置** 部分将应用于中的发射器和设置 **接收器连接** 设置将应用于接收器。

**接收服务器、端口、帐户、密码、系统类型**

这些设置适用于处于发射器+接收器模式的接收器。 它们的工作方式与发射器部分类似，请参阅上文，了解更多详细信息。

### SMPP渠道设置 {#smpp-channel-settings}

#### 允许字符音译 {#allow-character-transliteration}

音译是寻找与缺少的字符等价的字符的过程。 例如，GSM编码中缺少法语“e”（带抑扬符）字符，但可以将其替换为“e”，而不会影响可读性。

如果未选中此框，则如果无法按原样对字符串进行编码，则文本编码将失败。

选中此框后，文本编码将尝试将字符串转换为近似版本，而不是失败。 如果某些字符在目标编码中没有等效字符，则文本编码将失败。

请参阅 [定义编码设置的特定映射](sms-protocol.md#SMSC-specifics) 以获取有关编码过程的更一般性的说明。

#### 将传入的MO存储在数据库中 {#incoming-mo-storing}

启用后，传入的MO将存储在数据库的inSMS表中。 可以使用任何工作流的查询活动来查询此表。

Adobe Campaign Classic始终将所有MO存储在inSMS数据库中，因此此选项不可用。

#### 在SR处理期间启用实时KPI更新 {#real-time-kpi}

启用后，当收到错误SR时，将在主投放页面上实时更新KPI。

其缺点可能是由于它产生的数据库争用导致性能不佳。 如果禁用，则统计信息将由 **syncfromexec** 工作流，每20分钟运行一次。

Adobe Campaign Classic具有完全不同的KPI机制，因此此选项不可用。

#### 来源编号 {#source-number}

定义消息的默认源地址。 此设置仅适用于投放中源编号留空的情况。

默认情况下，不会传递源编号字段，因此提供程序会将其替换为短代码。

这将启用发件人地址/oADC覆盖功能。

#### 短代码 {#short-code}

指示帐户的主短代码。 如果此帐户使用了多个短代码，或者如果短代码未知，则将此字段留空。

指定短代码对以下两个功能很有用：

* 如果未提供源编号，则预览将显示短代码。 它会反映手机上的真实行为。

* 自动回复功能的“阻止列表”设置仅会针对特定的短代码向用户发送隔离信息。

#### 来源TON/NPI，目标TON/NPI {#ton-npi}

TON（编号类型）和NPI（编号计划指示符）在 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) （第117页）。 这些值应设置为提供商的需求。

它们按原样传输 `source_addr_ton`， `source_addr_npi`， `dest_addr_ton` 和 `dest_addr_npi` 字段 `SUBMIT_SM PDU`.

#### 服务类型 {#service-type}

此字段将按原样在中传输 `service_type` 字段 `SUBMIT_SM PDU`. 根据提供商的需求设置此参数。

### 吞吐量和超时 {#throughput-timeouts}

这些设置控制SMPP频道的所有计时方面。 某些提供商需要非常精确地控制消息速率、窗口和重试计时。 这些设置应该设置为与提供商的容量及其合同中指示的条件匹配的值。

#### 发送窗口 {#sending-window}

窗口为 `SUBMIT_SM PDU`无需等待匹配即可发送的 `SUBMIT_SM_RESP`.

最大窗口为4的传输示例：

![](assets/do-not-localize/sms_protocol_2.png)

当网络链路具有高延迟时，该窗口有助于提高吞吐量。  该窗口的值必须至少是SMS数乘以链接的延迟时间（以秒为单位），以便连接器从不等待 `SUBMIT_SM_RESP` ，然后再发送下一条消息。
如果窗口太大，则在出现连接问题时可能会发送更多重复消息。 此外，大多数提供商对窗口都有非常严格的限制，并拒绝超出限制的报文。

如何计算最佳发送窗口公式：

* 测量以下天数之间的最大延迟： `SUBMIT_SM` 和 `SUBMIT_SM_RESP`.

* 将该值以秒为单位乘以最大MT吞吐量。 这将提供最佳发送窗口值。

示例：如果在最大MT吞吐量中设置300 SMS/s，并且这两者之间有100毫秒的延迟 `SUBMIT_SM` 和 `SUBMIT_SM_RESP` 平均而言，最佳值将为 `300×0.1 = 30`.

#### 最大 MT 吞吐量 {#max-mt-throughput}

每秒和每个连接的最大MT数。 严格强制执行此设置，MTA绝不会以快于此限制的速度推送消息。 它对于需要精确节流的提供商非常有用。

要了解总吞吐量限制，请将此数字乘以上述公式中详述的连接总数。

0表示无限制，MTA将尽快发送MT。

通常建议将此设置保持在1000以下，因为不可能保证超过此数量的精确吞吐量，除非在最终架构上正确设定了基准并专门请求了SMPP提供商。 最好将连接数增加到1000 MT/s以上。

#### 重新连接前的时间 {#time-reconnection}

当TCP连接丢失时，连接器将等待此秒数，然后再尝试建立连接。

#### MT 的有效期 {#expiration-period}

超时介于 `SUBMIT_SM` 及其匹配 `SUBMIT_SM_RESP`. 如果 `RESP` 未及时收到，该消息将被视为失败，MTA的全局重试策略将适用。

#### 绑定超时 {#bind-timeout}

TCP连接尝试与 `BIND_*_RESP` 回复。 如果超时，连接将被Adobe Campaign连接器关闭，它将等待一段时间后再重新连接，然后重试。

#### 查询链接期 {#enquire-link-period}

`enquire_link` 是为保持连接活动而发送的一种特殊类型的PDU。 此时间段以秒为单位。 Campaign连接器仅发送 `enquire_link` 连接空闲以节省带宽时。 如果在此时段后两次未收到任何RESP，则连接将被视为无效，并触发重新连接过程。

### SMSC 详情 {#SMSC-specifics}

这些设置是高级设置，可使Adobe Campaign连接器适应大多数SMPP实施特性。

**定义编码的特定映射**

请参阅 [短信文本编码](sms-protocol.md#sms-text-encoding) 部分，了解文本编码的详细信息。

此设置允许您定义与规范不同的自定义编码映射。 您将能够声明一个编码列表，以及它们的 `data_coding` 值。

MTA将尝试使用列表中的第一个编码进行编码。 如果失败，它将尝试使用列表中的下一个编码等。 如果无法使用编码对消息进行编码，则会发生错误。 找到编码后，MTA将创建 `SUBMIT_SM PDU` 包含编码文本和 `data_coding` 使用表中指定的值设置的字段。

表中的项目顺序很重要：编码是从上到下的尝试。 您应该将最便宜或最推荐的编码放在列表的顶部，然后进行更多更昂贵的编码。

请注意，UCS-2永远不会失败，因为它可以编码Adobe Campaign中支持的所有字符，并且UCS-2短信的最大长度要小得多：仅为70个字符。

也可以使用此设置通过仅声明映射表中的1行来强制始终使用特定编码。

未选中该复选框时使用的默认映射等效于下表：

| 数据编码 | 编码 |
|---|---|
| 0 | GSM |
| 9 | UCS-2 |

这意味着MTA将尝试在GSM中编码消息。 如果成功，它将发送为 `data_coding` 设置为0。

如果消息无法以GSM编码，则会以UCS-2编码，并且将 `data_coding` 到8。

#### 启用message_payload {#enable-message-payload}

取消选中后，长短信将被MTA拆分，并以多个形式发送 `SUBMIT_SM PDU`与UDH一起使用。 该消息将由手机根据UDH数据重新组合。

选中后，长短信将在一个SUBMIT_SM PDU中发送，并将文本放置在message_payload可选字段中。 请参阅 [SMPP规范](sms-protocol.md#ACS-SMPP-connector) 了解详细信息。

如果启用了此功能，Adobe Campaign将无法单独计算短信部件数：所有消息都将计为一个部件中的已发送消息。

#### 发送完整的电话号码 {#send-full-phone-number}

如果未选中此复选框，则只向提供商发送电话号码的号码(`destination_addr` 字段 `SUBMIT_SM` 字段)。 这是默认行为，因为国际数字指示符（通常为+前缀）被SMPP中的TON和NPI字段替换。

选中该复选框后，电话号码将按原样发送，无需预处理和可能的空格，+前缀或井号/井号/星号。

阻止列表此功能还对自动回复功能的行为产生影响：如果未选中该复选框，则会在插入到隔离表的电话号码中添加+前缀，以补偿SMPP协议本身从电话号码中删除的+前缀。

#### 跳过TLS证书检查 {#skip-tls}

启用TLS后，跳过所有证书检查。

选中后，连接不再安全，不应在生产环境中启用。

它可用于调试或测试。

您可以在三个不同的证书验证值之间进行选择：

* 完整的认证检查（包括主机名），默认。
* 跳过主机名验证.
* 跳过证书验证.

#### 绑定TON/NPI {#bind-ton-npi}

TON（编号类型）和NPI（编号计划指示符），详见 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) （第117页）。 这些值应设置为提供商所需的任何值。

它们按原样传输 `addr_ton` 和 `addr_npi` 绑定PDU的字段。

#### 地址范围 {#address-range}

在BIND PDU的address_range字段中按原样发送。 此值应设置为提供商所需的任何值。

#### 无效 ID 确认计数 {#invalid-id}

限制 **消息ID无效** `DELIVER_SM_RESP` 可以为单个SR发送的URL。

**此解决方案应仅用于故障排除目的，作为解决方法** 并且在正常情况下设置为0。

Fox示例，当设置为2时：

* 提供程序发送SR (`DELIVER_SM`)，ID为“1234”。

* 在数据库中找不到ID“1234”。

* 连接器数量为1 **ID无效** 该ID出错，因此它发送 `DELIVER_SM_RESP` “消息ID无效”错误代码（正常行为）。

* 提供程序将重试ID为“1234”的相同SR。

* 在数据库中仍然找不到ID“1234”。

* 连接器计数为2 **ID无效** 该ID出错，因此它发送 `DELIVER_SM_RESP` “确定”，即使未正确处理也是如此。

* 此功能旨在当无效的SR块合法表示无法处理消息时刷新提供程序端的SR缓冲区。

将此字段设置为0将禁用以下机制： **消息ID无效** 始终返回，这是正常行为。

将此字段设置为1可使连接器始终响应“确定”，即使ID无效也是如此。 只有在监控下，才应将此参数设置为1，以便进行故障排除并在最短时间内完成恢复，例如，从提供商端问题中恢复。

#### SR 中 ID 的提取正则表达式 {#regex-extraction}

SMPP协议规范未严格实施SR格式。 它只是中所述的一项建议 [附录B](sms-protocol.md#sr-error-management) （第167页）。 有些SMPP实施者对此字段的格式不同，因此Adobe Campaign需要一种方法来提取正确的字段。

默认情况下，它最多捕获10个字母数字字符之后 `id:`.

正则表达式必须正好有一个捕获组，其部分包含在括号中。 ID部分必须用括号括起来。 正则表达式格式为PCRE。

调整此设置时，请确保包含尽可能多的上下文，以避免错误触发。 如果有特定的前缀，例如 `id:` 在标准中，将它们包含在正则表达式中。 此外，请尽量使用单词分隔符(\b)，以避免在单词中间捕获文本。

在正则表达式中不包括足够的上下文可能会引入一个小的安全缺陷：消息的实际内容可以包含在SR中。 如果您只匹配没有上下文的特定ID格式（例如UUID），则它可能会解析实际文本内容（例如，嵌入文本字段中的UUID），而不是ID。

#### 应用正则表达式来确定成功/错误状态 {#regex-applied}

当遇到具有未知stat/err字段组合的消息时，这些正则表达式将应用于stat字段，以确定SR是成功还是错误。 如果其stat值与任何正则表达式都不匹配，则会忽略SR。

默认情况下，以开头的统计值 `DELIV`，例如 `DELIVRD` 在 [附录B](sms-protocol.md#sr-error-management)，将被视为已成功交付，并且所有匹配错误的stat值，例如 `REJECTED`， `UNDELIV`被视为错误。

#### MT确认中的ID格式 {#id-format-mt}

这表示ID返回到 `message_id` 字段 `SUBMIT_SM_RESP PDU`.

* **不修改**：ID将作为ASCII编码的文本按原样存储在数据库中。 不进行预处理或过滤。

* **小数**：ID应为ASCII格式的小数。 使用此设置时，将删除前导和尾随空格以及前导零。

* **十六进制数**：ID应为ASCII格式的十六进制数字，且前导为0x，后导为h。然后，该ID在存储到数据库中之前被转换为十进制数。

* **十六进制字符串**：ID应为ASCII编码的文本，它本身是编码为十六进制的字节字符串。 例如，在PDU中，您将找到 `0x34 0x31 0x34 0x32 0x34 0x33`，会转换为ASCII“414243”。 然后，此字符串被解码为字节的十六进制字符串，您因此获得“ABC”：您将在数据库中存储ID“ABC”。

#### SR中的ID格式 {#id-format-sr}

这表示捕获的ID的格式 `Extraction` SR中ID的正则表达式。 值与上述MT中的格式具有相同的含义和行为。

**可选字段中的 SR ID 或错误代码**

>[!NOTE]
>
>仅在Adobe Campaign Classic Extended SMPP连接器中可用。

如果选中，可选字段的内容将附加到由上述正则表达式处理的文本中。 文本将具有格式 `0xTAG:VALUE`， `0xTAG` 是标记的4位十六进制值（以大写表示），例如 `0x002E`.

例如，您可能希望捕获 `receipted_message_id` 字段。 为此，请启用此复选框，并将以下文本添加到状态：

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
>您只能捕获具有文本(ASCII/UTF-8)值的可选字段。 具体而言，使用当前的正则表达式系统无法可靠地捕获二进制字段。

**文本字段中的 SR ID 或错误代码**

如果选中， **文本** 字段将在处理SR的状态文本期间保留。

如果提供商将重要数据（如ID或状态）放置在此字段中，这将很有用。 通常，此字段可以安全丢弃，因为它可能包含使用非ASCII编码的文本并中断正则表达式处理。

启用此选项可能会引入非常小的安全缺陷，如果 `Extraction` SR字段中ID的正则表达式不够具体。 的内容 **文本** 字段可能会被解析为ID，攻击者可能会用它来注入伪造的ID，这可能会导致部分拒绝服务情况。

**服务ID标记**

允许添加自定义TLV。 此字段设置标记部分。 此值可在每次投放时自定义，位于 **服务或项目ID** 投放的高级参数中的值。

此设置仅允许每条消息添加一个TLV选项。

### 发送给 MO 的自动回复 {#automatic-reply}

>[!IMPORTANT]
>
>在Adobe Campaign Classic和混合架构中，对扩展SMPP连接器应用自动回复需要为mid运算符在 **外部帐户** 文件夹。

阻止列表此功能允许快速回复文本到MO，并处理向发送的每短代码发送。

此 **关键词** 和 **短代码** 列定义触发自动回复的条件。 如果两个字段匹配，则会发送MO并触发其他操作。 要指定通配符，应将字段留空。 关键字与MO文本中的第一个字母数字词匹配，忽略标点符号和前导空格。 这意味着 **关键词** 字段不能包含空格，且必须是一个单词。

此 **关键词** 设置是一个前缀。 例如，如果指定“AD”，它将匹配“AD”、“ADAPT”和“ADOBE”。 如果您有多个具有相同前缀的关键字，则需要注意顺序，因为关键字是从上到下处理的。

此 **回复** column是要回复的文本。 此字段中没有可用的个性化。 如果您将此字段留空，将不会回复任何消息，但仍将触发其他操作。

此 **其他操作** 列在以下两种情况下都提供了额外的操作 **关键词** 和 **短代码** 匹配，空短代码匹配所有短代码。 您可以发送到隔离或从隔离中删除，值none回复文本。 如果您指定 **其他操作** 但请留下 **回复** 字段为空，则将执行操作，但不发送回复。 仅对指定的短代码应用隔离，如果字段留空，则对所有短代码应用隔离。

>[!IMPORTANT]
>
>“发送完整电话号码”设置会影响自动回复隔离机制的行为：如果未选中“发送完整电话号码”，则被隔离的电话号码将带有加号(“+”)，以使它与国际电话号码格式兼容。

表格中的所有条目按指定的顺序进行处理，直到一个规则匹配为止。 如果多个规则匹配一个MO，则仅应用最顶层的规则。

## 短信投放模板参数 {#sms-delivery-template-parameters}

可以为每个投放模板设置一些参数。

### 发件人字段 {#from-field}

此字段是可选的。 它允许覆盖发件人地址(oADC)。 此字段的内容放在 `source_addr` 字段 `SUBMIT_SM PDU`.

按照SMPP规范，字段限制为21个字符，但某些提供程序可能允许较长的值。 另请注意，在某些国家/地区，可能会应用非常严格的限制，例如长度、内容、允许的字符。

### 投放参数 {#delivery-parameters}

#### 每条消息的最大短信数 {#maximum-sms}

此设置仅在 **消息有效负载** 设置已禁用。 如果消息需要的短信数量超过此值，则会触发错误。

SMS协议将SMS限制为255个部分，但某些手机无法拼合长度超过10个部分或以上的消息，此限制取决于确切模型。 我们建议你不要每条信息超过5部分。

由于个性化消息在Adobe Campaign中的工作方式，消息的大小可能有所不同。 拥有大量长报文可能会增加发送成本。

#### 传输方式 {#transmission-mode}

此字段指示要传输的SMS类型：普通消息或闪存消息，存储在移动设备或SIM卡上。

此设置将传输到 `dest_addr_subunit` 中的可选字段 `SUBMIT_SM PDU`.

* **未指定** 未在PDU中发送任何可选字段。

* **Flash** 将值设置为1。 它会发送一条闪存消息，该消息会在手机上弹出，并且不会存储在内存中。

* **普通** 将值设置为0。 它会发送一条正常消息。

* **在移动设备上保存** 将值设置为2。 它指示手机将短信存储在内存中。

* **保存在终端上** 将值设置为3。 它指示手机将短信存储在SIM卡中。

#### 有效期 {#validity-period}

有效期在 `validity_period` 字段 `SUBMIT_SM PDU`. 日期始终采用绝对UTC时间格式的格式，日期字段将以“00+”结尾。

## 扩展通用SMPP连接器 {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

箭头表示数据流。

发送投放部分时，MTA会生成MTA子项。 MTA子进程的数目是动态的，取决于serverConf.xml中的配置。 每个MTA子级实例化连接器 `CSmppConnectorWorker` ，以连接到SMPP提供程序。 只要MTA子项保持活动状态（也可以在serverConf.xml中配置），连接就会保持活动状态。

SMS进程仅处理SR，它连接到提供程序并保持连接打开。 该进程每10分钟重新连接一次，以重新加载新设置，这是正常操作。

### 匹配MT、SR和broadlog条目 {#matching-mt}

中间表 `nmsProviderMsgId` 用于在异步提交到broadlog之前临时存储MT和SR数据。

`nmsProviderMsgId` 表有3组列：

* 发送和确认MT时更新的列： `iBroadLogId`， `iDeliveryId`

* 收到SR时更新的列： `iMsgId`， `iStatus`

* 始终更新的列： `tsCreated`， `sProviderId`

当MT和SR都完成处理时，您应具有完整的行，其中包含broadlog信息和状态信息。

此处， `iMsgId` 链接到 `nmsBroadLogMsg` 表，指示完整状态/错误消息。

短信流程每分钟检查一次完整的行，然后异步处理它们：

* 读取整行。
* SMS进程根据投放映射计算broadlog表的名称。
* SMS进程使用消息ID和状态更新broadlog表。

**吞吐量和并行连接**

每个MTA子级都创建一个可配置的连接量，因此限制MTA子级的数量将限制连接数量。 由于MTA子进程与流量之间的相关性是相关的，因此这可以在一定程度上进行控制，但仍然是有点不可预测的。

## 上线之前 {#checklist}

此清单列出了您在上线前应检查的事项。 不完整的设置可能会导致许多问题。

### 检查外部帐户冲突 {#external-account-conflict}

检查您是否没有旧的短信外部帐户。 如果禁用测试帐户，则会在生产系统上重新启用该帐户并产生潜在冲突。

如果同一Adobe Campaign实例上有多个帐户连接到同一提供商，请联系提供商以确保他们实际区分这些帐户之间的连接。 使用同一登录名拥有多个帐户需要额外配置。

### 在检查期间启用详细的SMPP跟踪 {#enable-verbose}

检查期间应始终启用详细的SMPP跟踪。
即使您无法自行检查日志，也更容易于 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 帮你。

### 测试短信 {#test}

* **发送包含各种字符的短信**
如果您需要发送包含非GSM或非ASCII字符的短信，请尝试发送一些包含尽可能多不同字符的消息。 如果设置自定义字符映射表，请为所有可能情况发送至少一条短信 
`data_coding` values.

* **检查是否已正确处理SR**
在投放日志中，短信应标记为已接收。 投放日志应该成功，并且如下所示：请检查您是否更改了投放提供商名称。 投放日志不得包含    `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
检查是否更改了投放提供商名称。 投放日志不得包含 **SR通用** 在生产环境中。

* **检查是否已处理MO**
如果需要处理MO（自动回复、将MO存储在数据库中等）， 尝试做一些测试。 为所有自动回复关键字发送几条短信，并检查回复是否足够快，不超过几秒。
在日志中检查Adobe Campaign是否成功回复 
`DELIVER_SM_RESP` (command_status=0)。

### 检查PDU {#check-pdus}

即使消息看起来成功，也务必检查PDU的格式是否正确。

在连接到之前未连接到Adobe Campaign的提供程序时，必须执行此步骤。

#### 绑定 {#bind}

检查 `BIND_* PDUs` 正确发送。 要检查的最重要事项是提供商始终成功返回 `BIND_*_RESP PDUs` (command_status = 0)。

检查检查是否没有太多 `BIND_* PDU`s.如果数量过多，则可能表示连接不稳定。 请参阅 [连接不稳定问题](sms-protocol.md#issues-unstable-connection) 部分以了解更多信息。

#### ENQUIRE_LINK {#enquire-link-pdus}

检查 `ENQUIRE_LINK PDU`在连接空闲时定期交换。

**SUBMIT_SM / DELIVER_SM**

发送消息，然后在日志中搜索其对应的消息 `SUBMIT_SM`， `SUBMIT_SM_RESP`， `DELIVER_SM` 和 `DELIVER_SM_RESP PDU`s.

使用 `SUBMIT_SM PDU`：

* 检查 `data_coding` 正确，默认为0。
* 检查 `short_message` 已正确编码。 尝试使用支持多种编码的十六进制转换器对其进行解码。

使用 `SUBMIT_SM_RESP PDU`：

* 检查是否成功，command_status = 0。
* 检查其正文是否包含格式正确的ID，后跟“0”字节。

使用 `DELIVER_SM PDU`：

* 解码十六进制 `short_message` 字段。
* 使用正则表达式检查工具检查中定义的正则表达式 `Extraction` SR中ID的regex只返回一个捕获组，并且捕获消息中的整个ID。
* 检查提取的ID是否与中的匹配 `SUBMIT_SM_RESP`.
* 检查中定义的正则表达式 `Extraction` SR中状态的正则表达式返回stat字段的内容。
* 检查中定义的正则表达式 `Extraction` SR中错误的正则表达式返回err字段的内容。

使用 `DELIVER_SM_RESP PDU`：

* 检查在收到 `DELIVER_SM PDU`，通常少于1秒。
* 检查是否成功，command_status = 0。

### 与提供商核实 {#provider}

即使短信成功，请联系提供商以查看是否一切正常。

### 禁用详细的SMPP跟踪 {#disable-verbose}

完成所有检查后，最后一件事就是 **禁用详细的SMPP跟踪** 不生成太多日志。 即使是在生产系统中，您也可以出于故障排除目的重新启用它们。
