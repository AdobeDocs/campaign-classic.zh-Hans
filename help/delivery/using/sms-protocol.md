---
product: campaign
title: SMS 连接器协议和设置
description: 进一步了解SMS连接器及其配置方法。
audience: delivery
content-type: reference
topic-tags: configuring-channels
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
source-git-commit: 4d789ad0138f65134d3c1592ef5d5517d39fc0f7
workflow-type: tm+mt
source-wordcount: '8460'
ht-degree: 0%

---

# SMS 连接器协议和设置 {#sms-connector-protocol}

![](../../assets/common.svg)

>[!NOTE]
>
>通过本文档，对协议、字段名称和值的详细信息的所有引用均引用 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

## 概述 {#overview}

短信可能仅限于发送没有格式的短文本消息，但其简单性使其成为有价值的通信渠道。

发送短信的主要方式有两种：

* 手动从电话发送，这是在人与人之间直接通信的常用方式。
* 从互联网发送，就像Adobe Campaign发送邮件一样。 为此，您需要一个短信服务提供商，将Internet连接到移动网络。
Adobe Campaign使用SMPP协议向服务提供商发送短信。

本文档将指导您完成在Adobe Campaign与SMPP提供商之间设置的连接。

SMPP提供商有时可能会偏离官方规范，但Adobe Campaign的SMS连接器提供了许多选项来调整其行为，以便与大多数提供商兼容。

>[!IMPORTANT]
>
>设置与新提供商的连接可能需要一些技术技能、TCP知识、二进制、十六进制表示和文本编码。 它还需要与提供商积极合作。

### 短信类型 {#sms-types}

通过短信提供商发送批量短信时，您会遇到三种不同的短信：

* **短信MT（已终止移动设备）**:由Adobe Campaign通过SMPP提供商向移动电话发出的短信。

* **SMS MO（来自移动设备）**:由移动设备通过SMPP提供商发送到Adobe Campaign的短信。

* **短信SR（状态报告）、DR或DLR（投放接收）**:移动设备通过SMPP提供商发送到Adobe Campaign的回执，指示短信已成功接收。 Adobe Campaign可能还会收到指示无法发送消息的SR，通常包含错误描述。

您需要区分确认（RESP PDU， SMPP协议的一部分）和SR:SR是一种通过网络端对端发送的短信，而确认只是确认一次传输成功。

确认和SR都可能触发错误，区分这两种错误将有助于进行故障排除。

### 短信携带的信息 {#information-sms}

短信携带的信息多于文本。 以下是您希望在短信中找到的内容列表：

* 文本，长度限制为140字节，表示70到160个字符，具体取决于编码。 请参阅 [短信文本编码](sms-protocol.md#sms-text-encoding) 以了解详细信息和限制。

* 收件人地址，有时称为 `ADC` 或 `MSISDN`. 即接收短信的移动设备数量。

* 发件人地址，可以称为 `oADC` 有时 `sender id`. 这可以是日常使用中的电话号码，也可以是通过提供商发送的简短代码或名称。 名称是一项可选功能，在这种情况下，您无法回复短信。

* 用于指示消息是否为Flash消息的标记。 闪存消息是未存储在内存中的弹出窗口。

* 用于指示SR是否为预期的标记。

* 有效日期，之后不允许任何网络设备重试。

* A `data_coding` 字段，表示文本的编码。

## SMPP协议 {#smpp-protocol}

Adobe Campaign Classic支持SMPP协议版本3.4。这是一种广泛的协议，允许向提供商(SMSC)发送短信，以及接收短信和接收。 有关更多信息，请参阅 [SMPP文档](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

短信服务提供商端的网络设备通常称为SMSC。

### SMPP连接 {#smpp-connections}

Adobe Campaign通过TCP连接到短信服务提供商的网络设备。 SMPP协议设置从Adobe Campaign到提供程序的永久TCP连接。 TCP连接始终由Adobe Campaign发起，甚至用于接收消息。
SMPP会打开1个或2个TCP连接，具体取决于其模式。 所有连接始终由Adobe Campaign启动。

SMPP协议可以采用两种模式：

* **发射机+接收机（或TX+RX）**:两个单独的TCP连接用于发送和接收消息。
* **收发器（或TRX）**:单个TCP连接用于发送和接收消息。

>[!NOTE]
>
> Adobe Campaign Classic仅支持TX+RX模式。 这种限制是由于其技术架构所致。

### SMPP PDU {#smpp-pdu}

SMPP传输单元（“数据包”）称为PDU。 A **PDU** 包含命令、状态、序列号和数据。

每个PDU必须由 `SMPP RESP PDU` （同步响应）。 请求可以流水线处理：发送者无需等待即可发送许多命令 `RESP`，则任何时间可能流水处理的请求数称为窗口。 `RESP PDU` 可以按与相应启动器PDU的顺序无关的任何顺序到达。

在分隔 **发射机+接收机** 模式，所使用的连接取决于所传输的消息类型。 发射机连接用于MT，接收机连接用于MO和SR。 每种消息的请求和响应通过同一TCP连接发送。

例如，发送MT时，会使用发送器连接，并且 `RESP` 确认MT也通过发送器信道发送。 当您收到MO（或SR）时，接收器连接用于接收MO并发送 `RESP` 这是对军事部的认可。

![](assets/do-not-localize/sms_protocol_1.png)

在Adobe Campaign Classic中，要将SR与其相应的MT链接，则SMSC会将ID与 `SUBMIT_SM_RESP` 和 `DELIVER_SM` 步骤。 标识符存储在 `providerId` 字段 `nms::providerMsgId` 表和链接到 `broadLogId` 和 `deliveryId`. 此匹配操作由短信进程在写入数据库时完成。

成功 `SUBMIT_SM_RESP PDU` 成功时，会在发送日志中触发“已发送”消息状态 `DELIVER_SM (SR) PDU` 触发“已接收”消息状态。

### 安全方面 {#security-aspects}

协议本身未加密。 大多数提供程序在时实施IP的变允许列表体，因此必须向提供程序声明Adobe Campaign服务器IP地址。

Adobe Campaign支持在绑定阶段期间传递登录名和密码。 它还支持SMPP而不是TLS。 应当指出，需要证书才能获得适当的安全性。 虽然SMPP连接器允许绕过证书检查，但它只应用于测试，因为没有证书的TLS提供的安全级别要低得多。

连接器使用系统提供的默认证书 `openssl` 库。 通常由 `/etc/ssl/certs` 目录访问Debian。 默认情况下，此目录由“ca-certificates”包提供，但可以对其进行自定义。

### 每种PDU中的信息 {#information-pdu}

每种PDU都有不同的字段，这些字段包含不同的信息。 这些PDU详见 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

下面的每个部分都描述了PDU及其同步响应(`*_RESP PDU`)。 所有PDU必须由相应的 `RESP`，这是规范的必备部分。

PDU可以具有可选字段。 此处只介绍了最常见的字段。 请参阅 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) 以了解更多信息。

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSFIER**

此PDU用于启动与SMSC的连接。 **发射机**, **接收器** 和 **收发器** 模式只更改允许通过此连接传输的短信类型，具体如下：

| 模式 | 允许的短信类型 |
|:-:|:-:|
| 发射机 | MT |
| 接收器 | MO + SR |
| 收发器 | MT + MO + SR |

中的显着字段 `BIND_* PDU`:

* **system_id**:用于身份验证的登录。 在外部帐户中设置。

* **密码**:用于身份验证的密码。 在外部帐户中设置。

* **system_type**:需要为某些提供程序设置特定值。 在外部帐户中设置，可在所有版本中使用。 通常会区分不同类型的合同、渠道、国家/地区等。

* **addr_ton** 和 **addr_npi**:某些提供程序需要。 由 `Bind TON` 和 `Bind NPI` 设置。

* **address_range**:某些提供程序需要。 大多数情况下，此连接中允许使用的快捷方式列表。 在外部帐户中设置。

`BIND_*_RESP` 没有特定字段，则会确认连接是否成功。

#### 取消绑定 {#unbind}

此PDU必须由系统发送，然后才能断开连接。 它必须等待匹配项 `UNBIND_RESP` PDU。

符合SMSC不能关闭连接，TCP连接由Adobe Campaign连接器控制。

#### SUBMIT_SM {#submit-sm}

此PDU向SMSC发送MT。 其响应PDU提供MT的ID。

中的显着字段 `SUBMIT_SM` PDU:

* **service_type**:某些提供程序所需。 在投放属性中设置。

* **source_addr_ton** 和 **source_addr_npi**:指示传输的源地址类型。 这些字段的含义是标准化的，但由于某些提供商使用它的方式不同，因此您应该向提供商询问其正确值。 在外部帐户中设置。

* **source_addr**:MT的源地址/oADC。 它将显示在手机上。 在外部帐户和投放中设置，投放中的值优先于外部帐户的值。

* **dest_addr_ton** 和 **dest_addr_npi**:指示传输的目的地址类型（如本地或国际格式）。 这些字段的含义是标准化的，但由于某些提供商使用它的方式不同，因此您应该向提供商询问其正确值。 在外部帐户中设置。

* **destination_addr**:收件人地址、电话号码或MSISDN。

* **esm_class**:用于判断文本字段中是否使用了UDH。 如果 `message_payload` 模式。

* **priority_flag**:优先于其他邮件。 这与投放本身的优先级相关。

* **validity_period**:时间戳后，不应尝试重试。 在投放本身中设置。

* **registered_delivery**:告知是否请求SR。 Adobe Campaign始终设置此标志，但自动回复除外。 对于多部分消息，仅为第一部分设置标志。 所有版本都具有相同的行为。

* **data_coding**:指示在文本字段中使用的编码。 请参阅 [短信文本编码](sms-protocol.md#sms-text-encoding) 的子菜单。

* **short_message**:消息的文本。 如果使用UDH，则还包含UHD标头。

Adobe Campaign支持以下可选字段：

* **dest_addr_ubinut**:用于指定短信的目标：Flash、移动或SIM卡。 在投放属性中设置。

* **message_payload**:在外部帐户中启用后，长报文将在单个PDU中发送，而文本将在此字段中发送，而不是 `short_message` 字段。

#### SUBMIT_SM_RESP {#submit-sm-resp}

此PDU将包含MT的ID。 这对于将其与传入的SR匹配非常有用。

>[!IMPORTANT]
>
>许多提供商以十六进制传输MT ID。 确保您将 **MT确认中的ID格式** 正确设置。

某些提供商发送 `SUBMIT_SM_RESP` 发送SR后 要考虑这种行为，Adobe Campaign需要等待30秒才能回复 **消息ID无效** ID未知的SR。

#### DELIVER_SM {#delivery-sm}

此PDU由SMSC发送至Adobe Campaign。 它包含MO或SR。

大多数字段的含义与其 `SUBMIT_SM` 对应。 以下是有用字段的列表：

* **source_addr**:MO/SR的源地址。 通常是电话号码。

* **destination_addr**:接收MO或SR的短代码。

* **esm_class**:用于判断PDU是MO还是SR。

* **short_message**:消息的文本。 对于SR，它包含SMPP协议规范附录B中描述的数据。 请参阅 [SR错误管理](sms-protocol.md#sr-error-management) 以了解更多详细信息。

Adobe Campaign能够在 `receipted_message_id` 可选字段。

#### DELIVER_SM_RESP {#deliver-sm-resp}

此PDU由Adobe Campaign发送以确认SR和MO。

Adobe Campaign Classic在将SR和MO插入数据库后确认它们。 即使处理成功，也可能会发生一些处理错误 `DELIVER_SM_RESP` 已发送PDU。 这种限制是由Adobe Campaign Classic的软件架构造成的。

#### INQUIRE_LINK {#enquire-links}

此PDU仅用于检查连接是否处于活动状态。 频度应根据提供商的需求进行设置。

默认的60秒应与外部帐户中设置的大多数配置相匹配。

#### INQUIRE_LINK_RESP {#enquire-links-resp}

此PDU确认连接处于活动状态。

### 多部分短信（长短信） {#multipart}

>[!IMPORTANT]
>
> Adobe Campaign仅支持多部分短信或长短信进行发送。 UDH和 `message_payload` 传入短信(MO)不受支持，这意味着MO的长度限制为160个字符。

多部分短信或长短信是分多部分发送的短信。 由于移动网络协议的技术限制，短信的长度不能超过140字节，否则需要拆分。 请参阅 [短信文本编码](sms-protocol.md#sms-text-encoding) 部分以了解有关短信可容纳的字符数的更多信息。

长消息的每个部分都是单个短信。 这些部件在网络上独立运行，并由接收手机组装。 为了处理重试和连接问题，Adobe Campaign会以反向顺序发送这些部分，并仅在消息的第一部分（即上次发送的部分）请求SR。 由于移动电话仅在收到其第一部分时才显示消息，因此对其他部分的重试不会在移动电话上产生重复。

使用 **每条消息的最大短信数** 设置 **投放模板**. 在发送短信时，超过此限制的消息将失败，原因为短信过长。

有2种方法可发送长短信：

* **UDH**:发送长消息的默认和推荐方法。 在此模式下，连接器将消息拆分为多个 `SUBMIT_SM PDU`都有UDH的信息。 此协议是手机本身使用的协议。 这意味着Adobe Campaign对消息生成的控制最强，能够准确计算发送了多少个部件以及它们的拆分方式。

* **message_payload**:用一条长信息发送整条长信息 `SUBMIT_SM PDU`. 提供商必须对其进行拆分，这意味着Adobe Campaign无法确切知道已发送的部件数量。 有些提供商需要此模式，但我们建议您仅在它们不支持UDH时才使用此模式。

请参阅 `esm_class`, `short_message` 和 `message_payload` 字段 [SUBMIT_SM PDU](sms-protocol.md#information-pdu) 有关协议和格式的更多详细信息。

### 吞吐量上限和窗口 {#throughput-capping}

大多数提供程序要求对每个SMPP连接设置吞吐量限制。 可以通过在外部帐户中设置多个短信来实现这一点。 请注意，每个连接发生吞吐量限制，总有效吞吐量是每个连接的限制乘以连接总数。 详情请参阅 [同时连接](sms-protocol.md#connection-settings) 中。

要达到最大的吞吐量，您需要微调最大发送窗口。 发送窗口是 `SUBMIT_SM PDU`无需等待即可发送 `SUBMIT_SM_RESP`. 请参阅 [发送窗口设置](sms-protocol.md#throughput-timeouts) 部分以了解更多详细信息。

### SR和错误管理（“附录B”） {#sr-error-management}

SMPP协议在 `RESP PDU`s，但它不定义SR的错误代码。 每个提供商都使用各自的错误代码来表示其含义。

本公司于2014年12月31日 [SMPP协议规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) （第167页），但并未列出实际错误代码及其含义。

为了适应错误管理，Adobe Campaign的broadlog消息系统已被用于正确配置错误及其严重性（硬、软等）。

如上所述，存在两种不同的错误：

* 中的同步回复 `SUBMIT_SM_RESP` 消息发送到SMSC后立即发生的事件
* 在移动设备收到消息或消息超时时，可能会很晚收到的收据。 在这种情况下，在SR中发现错误。

收到SR后，在其中可找到状态和错误 `short_message` 字段（附录B符合实施条件的示例）。 的 `short_message` PDU的字段通常称为 **文本字段** 因为它包含MT中的文本。 如果是SR，则包含技术信息以及一个名为 **文本**. 这2个字段不同，并且 `short_message` 实际包含 **文本** 字段和其他信息。

Adobe Campaign Classic连接器（扩展SMPP除外）使用硬编码行为，具体取决于选定的提供程序。 通用SMPP仅区分成功和错误，没有详细信息。 投放日志可能包含一些无法保证的信息。

#### SR文本字段格式 {#sr-text-field-format}

规范建议对SR文本字段使用此格式。 它是子字段列表，用冒号以空格分隔，用于分隔字段名称及其值。 字段名称不区分大小写。

与附录B推荐匹配的SR文本字段示例：

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

id字段是 `SUBMIT_SM_RESP PDU`,MT的确认

`sub` 和 `dlvrd` 本应计算已投放部件和已投放消息的数量，但Adobe Campaign并未使用此功能，因为broadlog系统可提供更好、更集成的信息。

`submit date` 和 `done date` 字段是指示MT何时发送以及移动设备何时发送SR的时间戳。 设置了不正确日期的手机给出的时区、甚至错误的时间戳，可能会出现一些问题。

stat字段很重要，因为它可告知消息的状态。 唯一重要的状态是 `DELIVRD`, `UNDELIV` 和 `REJECTD`. 的 `DELIVRD` 状态表示成功，其他两个表示错误。 其他值可能存在，但通常是中间通知，例如MT到达了移动设备运营商，但不是手机。 这些中间通知被Adobe Campaign忽略。

错误字段包含特定于提供程序的错误代码。 提供程序必须提供可能的错误代码表及其含义才能解释此值。

最后，文本字段通常包含MT文本的开头。 这被Adobe Campaign忽略，某些提供商不会传输它以避免PII泄漏和网络带宽消耗。 它可在故障排除期间通过读取此字段来更轻松地发现与测试MT匹配的SR。

### Adobe Campaign Classic扩展通用SMPP中的SR处理示例 {#sr-processing}

此示例显示了遵循附录B推荐的实施案例、外部帐户中的默认值以及成功的短信MT。

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

首先， `id extraction` 将应用正则表达式来提取ID并将其与相应的MT协调。

然后， `status extraction` regex和 `error code extraction` 将应用正则表达式来提取这些字段并将其附加到字符串中。

broadlog消息将使用此信息构建，并附加原始的未更改字符串以供参考：

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

然后，该消息被标准化，删除MESSAGE部分，以便能够匹配具有相同状态和错误代码的多个消息。

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

如果该消息尚未在broadlog消息表中设置，则将使用整个消息作为 **firstText** 和正常的消息。 然后，连接器使用成功和 `error` regex确定是成功还是失败：

* 如果与 `success` 正则表达式，则会将其视为成功。

* 如果与 `error` 正则表达式时，该消息被限定为错误。

* 如果这两个正则表达式中没有一个匹配，则忽略SR。 它可能是中间通知，Adobe Campaign不处理。

默认情况下，所有错误都设置为软错误。 这意味着必须手动配置硬错误。

### 短信文本编码 {#sms-text-encoding}

您应该 **在出现编码问题时，请始终联系SMSC提供商**. 只有SMSC提供商了解其支持的编码以及可能因技术平台限制而适用的特殊规则。

短信消息使用特殊的7位编码，通常称为GSM7编码。

在SMPP协议中，GSM7文本将扩展为每个字符8位，以便更轻松地进行故障排除。 SMSC会先将其打包为每个字符7位，然后再将其发送到移动设备。 这意味着 `short_message` 短信的字段在SMPP帧中最长可能为160字节，而在移动网络上发送时，该字段的长度限制为140字节。

在出现编码问题时，请检查以下一些重要事项：

* 确保知道哪些字符属于哪种编码。 GSM7不完全支持音符号或重音符号。 特别是在法语中，“é”和“è”是GSM7的一部分，但“ê”和“ï”不是。 西班牙语也是如此。

* 带有变音符(ç)的C仅在GSM7字母的大写中存在，但有些手机在小写或“智能”大写中呈现。 一般建议是完全避免它，并删除变量或切换到UCS-2。

* **请勿在短信中使用ASCII。** 除非SMSC提供程序明确请求。 此编码浪费了空间，因为它具有8位字符，并且比GSM7的覆盖范围更小。 在北美使用的CDMA网络可能需要此编码。

* Latin-1并非始终受支持。 在尝试使用Latin-1之前，请检查与SMSC提供商的兼容性。

* Adobe Campaign连接器不支持国家语言班次表。 您必须使用UCS-2或其他 `data_coding` 中。

* UCS-2和UTF-16通常由手机混合使用。 使用UCS-2中不存在的表情符号和其他字符时，会出现此问题。

* 大多数手机没有所有UCS-2字符的字体字形。 智能手机往往能够非常轻松地显示稀有字符，但功能手机通常对购买国母语中有用功能的支持有限。 如果您想使用表情符号或ASCII-art，请在发送前在各种手机上测试它。 Adobe Campaign预览不模拟缺少的字形，将显示Web浏览器上可用的符号。

的 `data_coding` 字段可告知您使用的编码。 一个主要问题是，值0表示规范中的默认SMSC编码，通常指GSM7。 与与编码关联的SMSC合作伙伴联系 `data_coding` = 0，而Adobe Campaign仅支持。 其他 `data_coding` 值往往遵循规范，但确定的唯一方法是与SMSC提供商进行核实。

消息的最大大小取决于其编码。 下表汇总了所有相关信息：

| 编码 | 常用data_coding | 消息大小（字符） | 多部分短信的部件大小。 | 可用字符 |
|:-:|:-:|:-:|:-:|:-:|
| GSM7 | 0 | 160 | 152 | GSM7基本字符集+扩展（扩展字符需要2个字符） |
| Latin-1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode（因电话而异） |

## SMPP外部帐户参数 {#SMPP-parameters-external}

SMPP协议的每个实现都有许多变体。 为了提高兼容性和适应性，可使用许多设置来更改SMPP连接器的行为。 本节介绍每个参数及其对连接器的影响。

### 常规参数和路由 {#general-parameters-routing}

**限制此帐户的MTA实例**

可以设置允许连接到SMPP提供程序的MTA实例数限制。 选中此选项后，您最多可以指定使用的MTA数量。

此选项允许对连接数进行更精细的控制，请参阅 [同时连接](sms-protocol.md#connection-settings).

如果设置的值大于正在运行的MTA数，则所有MTA都将正常运行：此选项仅是限制，无法生成其他MTA。

如果您需要精确控制连接数（例如，提供商要求），则建议始终设置此选项，即使当前部署运行的MTA数量正确也是如此。 如果之后添加其他MTA，则仍将遵守连接限制。

### 连接设置 {#connection-settings}

#### SMSC实施名称 {#smsc-implementation-name}

设置SMSC实施的名称。 应将其设置为提供商的名称。 请联系管理员或投放能力团队，以了解在此字段中要添加的内容。 此字段的角色在 [SR错误管理](sms-protocol.md#sr-error-management) 中。

#### 服务器 {#server}

要连接到的服务器的DNS名称或IP地址。

#### 端口 {#port}

要连接的TCP端口。

#### 帐户 {#account}

连接的登录。 传入 `system_id` 绑定PDU的字段。

#### 密码 {#password}

SMPP连接的密码。 在BIND PDU的密码字段中传递。

#### 系统类型 {#system-type}

传入的值 `system_id` 绑定PDU的字段。 某些提供商需要在此处获得特定值。

#### MTA子连接数 {#number-mta-child}

在Adobe Campaign Classic中，它定义每个MTA子项的连接数。

Adobe Campaign Classic扩展SMPP连接器可以控制每个MTA子项的连接数。 要控制连接的全局限制，您必须限制MTA子进程的数量，这通常意味着拥有专用的短信中间源平台。

对于Adobe Campaign Classic，可能有不同数量的接收机和发射机连接：

* **发送器连接= MTA子连接数x MTA子进程数x MTA子进程数x MTA数（如果设置了自动回复）+ MTA子连接数**

如上所示，如果启用了自动回复，Adobe Campaign Classic SMS进程将打开更多发送器连接。 这些额外的连接用于发送自动回复。

* **接收器连接= MTA子连接数**

如果设置自动回复，短信流程将打开发送器/接收器对，从而增加发送器连接数。 如果未设置任何自动回复，则将仅打开接收器连接。

#### 通过SMPP启用TLS {#enable-TLS}

使用TLS连接到提供程序。 连接将被加密。 TLS连接由OpenSSL库管理，对于此连接，任何适用于OpenSSL的内容均为true。

#### 在日志文件中启用详细的SMPP跟踪 {#enable-verbose-log-file}

此设置会转储日志文件中的所有SMPP流量。 通常需要在初始设置期间调整参数。 在对连接器进行故障诊断时，必须启用此功能，并将其与提供商看到的流量进行比较。

在Adobe Campaign Classic中，日志输出位于与MT相关的流量的MTA日志中，以及与MO和SR相关的流量的短信日志中。

### 接收器连接设置 {#receiver-connection}

此部分仅以分隔的形式显示 **发射机+接收机** 模式。

#### 对接收器使用不同的参数 {#receiver-parameters}

如果未选中该框，则发送器和接收器的设置相同。

选中该框后， **连接设置** 部分将应用于 **接收器连接** 设置将应用于接收器。

**接收器服务器、端口、帐户、密码、系统类型**

这些设置适用于在发送器+接收器模式下的接收器。 它们的工作方式与发射机部分类似，有关更多详细信息，请参阅上文。

### SMPP渠道设置 {#smpp-channel-settings}

#### 允许字符音译 {#allow-character-transliteration}

音译是查找与缺失字符等效的过程。 例如，GSM编码中缺少法语“ê”（即带抑扬音符号）字符，但可以将其替换为“e”字符，而不会损害可读性。

如果未选中此框，则如果文本编码无法按原样对字符串进行完全编码，则文本编码将失败。

选中此框后，文本编码将尝试将字符串转换为近似版本，而不是失败。 如果某些字符在目标编码中没有对等字符，则文本编码将失败。

请参阅 [定义编码设置的特定映射](sms-protocol.md#SMSC-specifics) ，以了解编码过程的更一般说明。

#### 将传入的MO存储在数据库中 {#incoming-mo-storing}

启用后，传入的MO将存储在数据库的inSMS表中。 可以使用任何工作流的查询活动查询此表。

Adobe Campaign Classic始终将所有MO存储在inSMS数据库中，因此此选项不可用。

#### 在SR处理期间启用实时KPI更新 {#real-time-kpi}

启用后，当收到错误SR时，将在主投放页面上实时更新KPI。

缺点是性能较低，因为它会产生数据库争用。 如果禁用，则统计信息会由 **syncfromexec** 工作流，每20分钟运行一次。

Adobe Campaign Classic具有完全不同的KPI机制，因此此选项不可用。

#### 源编号 {#source-number}

定义消息的默认源地址。 仅当投放中的源编号留空时，此设置才适用。

默认情况下，不会传递源编号字段，因此提供程序将用它替换短代码。

这会启用发送者地址/oADC覆盖功能。

#### 短代码 {#short-code}

指示帐户的主短代码。 如果此帐户使用了多个短代码，或者短代码未知，请将此字段留空。

指定短代码有助于实现以下两项功能：

* 如果未提供源编号，则预览将显示短代码。 它将反映手机上的真实行为。

* 自动回阻止列表复功能的设置仅发送给对特定短代码的用户进行隔离。

#### 来源吨/NPI，目的地吨/NPI {#ton-npi}

TON（编号类型）和NPI（编号计划指标）在 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) （第117页）。 这些值应根据提供程序的需求进行设置。

它们会按原样在中传输 `source_addr_ton`, `source_addr_npi`, `dest_addr_ton` 和 `dest_addr_npi` 字段 `SUBMIT_SM PDU`.

#### 服务类型 {#service-type}

此字段按原样在 `service_type` 字段 `SUBMIT_SM PDU`. 根据提供商的需求设置此参数。

### 吞吐量和超时 {#throughput-timeouts}

这些设置控制SMPP渠道的所有计时方面。 某些提供程序需要非常精确地控制消息速率、窗口和重试计时。 这些设置应设置为与提供商的能力和合同中指明的条件相匹配的值。

#### 发送窗口 {#sending-window}

窗口是 `SUBMIT_SM PDU`可以在不等待匹配的情况下发送的 `SUBMIT_SM_RESP`.

最大窗口为4的传输示例：

![](assets/do-not-localize/sms_protocol_2.png)

当网络链路具有高延迟时，窗口有助于提高吞吐量。  窗口的值必须至少是SMS/s数乘以链接的延迟（以秒为单位），这样连接器就不会等待 `SUBMIT_SM_RESP` 发送下一条消息之前。
如果窗口太大，则在出现连接问题时，可能会发送更多重复的消息。 此外，大多数提供商对窗口和拒绝超出限制的消息都有非常严格的限制。

如何计算最佳发送窗口公式：

* 测量 `SUBMIT_SM` 和 `SUBMIT_SM_RESP`.

* 将此值（以秒为单位）乘以最大MT吞吐量。 这将提供最佳发送窗口值。

示例：如果在最大MT吞吐量中设置了300条短信，并且之间的延迟为100毫秒 `SUBMIT_SM` 和 `SUBMIT_SM_RESP` 平均而言，最佳值是 `300×0.1 = 30`.

#### 最大MT吞吐量 {#max-mt-throughput}

每秒和每个连接的最大MT数。 严格强制执行此设置，MTA将永远不会以超出此限制的速度推送消息。 对于需要精确限制的提供程序而言，此功能非常有用。

要了解总吞吐量限制，请将此数字乘以上述公式中详细描述的连接总数。

0表示无限制，MTA将尽快发送MT。

通常建议将此设置保持在1000以下，因为除非在最终架构上以适当的基准并专门请求的SMPP提供商进行基准，否则无法保证高于此数字的精确吞吐量。 增加连接数量以超过1000 MT/s可能更好。

#### 重新连接前逗留的时间 {#time-reconnection}

当TCP连接丢失时，连接器将等待此秒数后再尝试建立连接。

#### MT的过期期限 {#expiration-period}

超时时间 `SUBMIT_SM` 和它的匹配 `SUBMIT_SM_RESP`. 如果 `RESP` 未按时收到，则消息将被视为失败，并且将应用MTA的全局重试策略。

#### 绑定超时 {#bind-timeout}

TCP连接尝试与 `BIND_*_RESP` 回复。 超时时，连接将被Adobe Campaign连接器关闭，在重新连接之前将等待时间，然后再重试。

#### inquire_link期间 {#enquire-link-period}

`enquire_link` 是发送的一种特殊PDU，用于保持连接的活动状态。 此时段以秒为单位。 营销活动连接器仅发送 `enquire_link` 当连接空闲时，以节省带宽。 如果在此时间段后未收到RESP，则连接将被视为无效，并将触发重新连接过程。

### SMSC 详情 {#SMSC-specifics}

这些设置是高级设置，可使Adobe Campaign连接器适应大多数SMPP实施特性。

**定义编码的特定映射**

请参阅 [短信文本编码](sms-protocol.md#sms-text-encoding) 部分以了解有关文本编码的详细信息。

此设置允许您定义自定义编码映射，与规范不同。 您将能够声明编码列表及其编码 `data_coding` 值。

MTA将尝试使用列表中的第一种编码进行编码。 如果失败，则会尝试使用列表上的下一个编码，等等。 如果无法使用编码对消息进行编码，则会发生错误。 找到编码后，MTA将创建 `SUBMIT_SM PDU` 和 `data_coding` 字段集中指定的值。

表中项目的顺序很重要：编码从上到下进行尝试。 您应该将最便宜或最推荐的编码放在列表的顶部，然后是越来越昂贵的编码。

请注意，UCS-2永远不会失败，因为它可以对Adobe Campaign中支持的所有字符进行编码，并且UCS-2短信的最大长度要小得多：仅70个字符。

您还可以使用此设置强制特定编码始终通过在映射表中仅声明一行来使用。

未勾选复选框时使用的默认映射等效于下表：

| data_coding | 编码 |
|---|---|
| 0 | GSM |
| 9 | UCS-2 |

这意味着MTA将尝试对GSM中的消息进行编码。 如果成功，则将发送 `data_coding` 设置为0。

如果消息无法采用GSM编码，则将采用UCS-2编码，并进行设置 `data_coding` 到8。

#### 启用message_payload {#enable-message-payload}

如果未选中此选项，则长短信将被MTA拆分，并发送到多个 `SUBMIT_SM PDU`与UDH合作。 在UDH数据之后，手机将重组该消息。

选中此选项后，长短信将在一个SUBMIT_SM PDU中发送，并将文本置于message_payload可选字段中。 请参阅 [SMPP规范](sms-protocol.md#ACS-SMPP-connector) 以了解详细信息。

如果启用此功能，Adobe Campaign将无法单独计数短信部件：所有消息将计为一部分发送。

#### 发送完整电话号码 {#send-full-phone-number}

如果未选中此复选框，则只向提供商发送电话号码的位数(`destination_addr` 字段 `SUBMIT_SM` 字段。 这是默认行为，因为SMPP中的国际数字指示符（通常为+前缀）被替换为TON和NPI字段。

选中此复选框后，电话号码将按原样发送，且没有预处理和潜在空格， +前缀或井号/井号/星号。

此功能还会影响自动回复功阻止列表能的行为：未选中此复选框时，将在插入隔离表的电话号码中添加+前缀，以补偿SMPP协议本身从电话号码中删除的+前缀。

#### 跳过TLS证书检查 {#skip-tls}

启用TLS后，请跳过所有证书检查。

选中此选项后，连接不再安全，不应在生产中启用该连接。

它可用于调试或测试目的。

您可以为证书验证选择三个不同的值：

* 完整认证检查（包括主机名），默认。
* 跳过主机名验证。
* 跳过证书验证。

#### 绑定TON/NPI {#bind-ton-npi}

TON（编号类型）和NPI（编号计划指标），详见 [SMPP 3.4规范](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) （第117页）。 这些值应设置为提供程序需要的任何值。

它们会按原样在中传输 `addr_ton` 和 `addr_npi` 绑定PDU的字段。

#### 地址范围 {#address-range}

在BIND PDU的address_range字段中按原样发送。 此值应设置为提供程序需要的任何内容。

#### ID确认计数无效 {#invalid-id}

限制 **消息ID无效** `DELIVER_SM_RESP` 可以发送给单个SR的URL。

**此方法应仅用于故障诊断，作为解决方法** 并在正常情况下设置为0。

Fox示例，将设置为2时：

* 提供商发送SR(`DELIVER_SM`),ID为“1234”。

* 在数据库中找不到ID“1234”。

* 连接器计数1 **无效ID** 该ID的错误，因此会发送 `DELIVER_SM_RESP` 出现“消息ID无效”错误代码（正常行为）。

* 提供程序重试ID为“1234”的同一SR。

* 在数据库中仍找不到ID“1234”。

* 连接器计数2 **无效ID** 该ID的错误，因此会发送 `DELIVER_SM_RESP` “确定”，即使未正确处理。

* 当无效的SR块合法且无法处理消息时，此功能用于刷新提供方端的SR缓冲区。

将此字段设置为0将禁用 **消息ID无效** 始终返回，这是正常行为。

将此字段设置为1会使连接器始终响应“OK”（确定），即使ID无效。 此值应仅设置为1，以便在监管下进行故障排除，并且最短时间（例如从提供方端问题恢复）。

#### SR中ID的Extraction正则表达式 {#regex-extraction}

SMPP协议规范并未严格强制实施SR格式。 它只是 [附录B](sms-protocol.md#sr-error-management) （第167页）。 某些SMPP实施者对此字段的格式不同，因此Adobe Campaign需要一种方法来提取正确的字段。

默认情况下，此代码最多可捕获10个字母数字字符 `id:`.

正则表达式必须恰好具有一个包含括号中部分的捕获组。 括号必须包围ID部分。 正则表达式格式为PCRE。

调整此设置时，请确保尽可能多地包含上下文以避免触发false。 如果有特定前缀，例如 `id:` 在标准中，将它们包含在正则表达式中。 尽量使用单词分隔符(\b)，以避免捕获单词中间的文本。

正则表达式中未包含足够的上下文可能会引入一个小的安全漏洞：消息的实际内容可以包含在SR中。 如果您仅与没有上下文的特定ID格式（例如UUID）匹配，则它可能会解析实际的文本内容（例如嵌入在文本字段中的UUID），而不是ID。

#### 应用正则表达式确定成功/错误状态 {#regex-applied}

遇到具有未知stat/err字段组合的消息时，会将这些正则表达式应用于stat字段，以确定SR是成功还是错误。 如果SR的stat值与这些区域中的任何区域不匹配，则将忽略该SR。

默认情况下，以开头的stat值 `DELIV`，例如 `DELIVRD` 在 [附录B](sms-protocol.md#sr-error-management)，将被视为已成功交付以及与错误(例如， `REJECTED`, `UNDELIV`，则被视为错误。

#### MT确认中的ID格式 {#id-format-mt}

这表示 `message_id` 字段 `SUBMIT_SM_RESP PDU`.

* **不修改**:该ID按原样存储在数据库中，为ASCII编码的文本。 不进行预处理或过滤。

* **小数**:ID应为ASCII格式的小数。 使用此设置时，将删除前导和尾随空格以及前导零。

* **十六进制数**:ID应为ASCII格式的十六进制数，不带前导0x或尾随h。然后，该ID会先转换为十进制数，然后再存储到数据库中。

* **十六进制字符串**:ID应为ASCII编码的文本，其本身是以十六进制编码的字节字符串。 例如，在PDU中，您将找到 `0x34 0x31 0x34 0x32 0x34 0x33`，其中转换为ASCII“414243”。 然后，此字符串将解码为十六进制字节字符串，您将获得“ABC”，结果是：您将ID“ABC”存储在数据库中。

#### SR中的ID格式 {#id-format-sr}

这表示由 `Extraction` SR中ID的正则表达式。 值的含义与上述MT中的格式相同，行为也相同。

**可选字段中的SR ID或错误代码**

>[!NOTE]
>
>仅在Adobe Campaign Classic扩展SMPP连接器中可用。

如果选中，则可选字段的内容将附加到上面由区域处理的文本中。 文本将具有格式 `0xTAG:VALUE`, `0xTAG` 是标记的4位十六进制值，以大写表示，例如 `0x002E`.

例如，您可能想要在 `receipted_message_id` 字段。 为此，请启用此复选框，并将向状态添加以下文本：

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

在此示例中，0x001E是可选字段的标记，UUID是字段的值。

为了捕获此值，您现在可以在SR字段中ID的Extraction regex中设置以下正则表达式：

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>您只能捕获具有文本(ASCII/UTF-8)值的可选字段。 具体而言，无法使用当前正则表达式系统可靠地捕获二进制字段。

**文本字段中的SR ID或错误代码**

如果选中，则 **文本** 字段，以便在处理SR的状态文本期间保留该字段。

如果提供程序在此字段中放置重要数据（如ID或状态），则此操作非常有用。 通常，可以安全地丢弃此字段，因为它可能包含采用非ASCII编码的文本并中断正则表达式处理。

如果 `Extraction` SR字段中ID的正则表达式不够具体。 的内容 **文本** 字段可以解析为ID，攻击者可以使用它注入伪造的ID，这可能导致部分拒绝服务情况。

**服务ID标记**

允许添加自定义TLV。 此字段设置标记部分。 可以在 **服务或程序ID** 值。

此设置仅允许为每个消息添加一个TLV选项。

### 发送给 MO 的自动回复 {#automatic-reply}

>[!IMPORTANT]
>
>在Adobe Campaign Classic和混合架构中，对扩展的SMPP连接器应用自动回复时，需要在 **外部帐户** 文件夹。

此功能允许快速回复MO文本并处理发送给MO的短阻止列表代码。

的 **关键词** 和 **短代码** 列定义触发自动回复的条件。 如果两个字段匹配，则发送MO并触发其他操作。 要指定通配符，应将字段留空。 关键词与MO文本中的第一个字母数字词匹配，忽略标点和前导空格。 这意味着 **关键词** 字段不能包含空格，且必须是单个词。

的 **关键词** 设置是前缀。 例如，如果您指定“AD”，则它将匹配“AD”、“ADAPT”和“ADOBE”。 如果您有多个具有相同前缀的关键词，则需要注意订单，因为关键词是从上到下处理的。

的 **回复** 列是要回复的文本。 此字段中没有可用的个性化。 如果将此字段留空，则不会回复任何消息，但仍会触发其他操作。

的 **其他操作** 列在 **关键词** 和 **短代码** 匹配，空短代码匹配所有短代码。 您可以发送到隔离或从隔离中删除，但值为无对文本的回复。 如果您指定 **其他操作** 但离开 **回复** 字段为空时，将执行操作，但不会发送任何回复。 隔离仅应用于指定的短代码，如果字段留空，则应用于所有短代码。

>[!IMPORTANT]
>
>发送完整电话号码设置对自动回复隔离机制的行为产生影响：如果未勾选“发送完整电话号码”，则输入隔离的电话号码将添加加号(“+”)，以使其与国际电话号码格式兼容。

表中的所有条目将按照指定的顺序进行处理，直到一个规则匹配为止。 如果多个规则与一个MO匹配，则仅应用最顶部的规则。

## 短信投放模板参数 {#sms-delivery-template-parameters}

可以为每个投放模板设置某些参数。

### 从字段 {#from-field}

此字段为可选字段。 它允许覆盖发送者地址(oADC)。 此字段的内容位于 `source_addr` 字段 `SUBMIT_SM PDU`.

SMPP规范将字段限制为21个字符，但某些提供程序可能允许较长的值。 另请注意，某些国家/地区可能会应用非常严格的限制，例如长度、内容和允许使用的字符。

### 投放参数 {#delivery-parameters}

#### 每条消息的最大短信数 {#maximum-sms}

此设置仅在 **消息负载** 设置处于禁用状态。 如果消息需要的短信数量超过此值，则会触发错误。

短信协议将短信的数量限制为255个部分，但一些手机无法将长信息与大约10个部分拼合在一起，这个限制取决于具体型号。 我们建议您不要将每封邮件的5个部分以上。

由于个性化消息在Adobe Campaign中的工作方式，消息大小可能会有所不同。 长消息量大可能会增加发送成本。

#### 传输模式 {#transmission-mode}

此字段指示您希望传输的短信类型：正常或闪存消息，存储在移动或SIM卡上。

此设置将在 `dest_addr_subunit` 中的可选字段 `SUBMIT_SM PDU`.

* **未指定** 在PDU中不发送可选字段。

* **Flash** 将值设置为1。 它会发送一条闪存消息，该消息会在移动设备上弹出，且不会存储在内存中。

* **正常** 将值设置为0。 它会发出正常信息。

* **在移动设备上保存** 将值设置为2。 它告知手机将短信存储在内存中。

* **在终端上保存** 将值设置为3。 它让手机将短信存储在SIM卡中。

#### 有效期 {#validity-period}

有效期在 `validity_period` 字段 `SUBMIT_SM PDU`. 日期始终以绝对UTC时间格式设置，日期字段将以“00+”结尾。

## 扩展通用SMPP连接器 {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

箭头表示数据流。

发送投放部件时，MTA会生成MTA子项。 MTA子进程的数量是动态的，取决于serverConf.xml中的配置。 每个MTA子项都会实例化连接器 `CSmppConnectorWorker` 连接到SMPP提供程序。 只要MTA子项保持活动状态，连接就会保持活动状态，也可以在serverConf.xml中进行配置。

短信进程只处理SR，它连接到提供商并保持连接打开。 该进程每10分钟重新连接一次以重新加载新设置，这是正常操作。

### 匹配MT、SR和broadlog条目 {#matching-mt}

中间表 `nmsProviderMsgId` 用于在异步提交到broadlog之前临时存储MT和SR数据。

`nmsProviderMsgId` 表有3组列：

* 发送和确认MT时更新的列： `iBroadLogId`, `iDeliveryId`

* 收到SR时更新的列： `iMsgId`, `iStatus`

* 始终更新的列： `tsCreated`, `sProviderId`

当MT和SR都完成处理后，您应该有完整的行，行中同时包含broadlog信息和状态信息。

这里， `iMsgId` 链接到 `nmsBroadLogMsg` 表，指示完整状态/错误消息。

短信流程每分钟会检查是否有完整的行，然后异步处理它们：

* 将读取完整行。
* SMS进程根据投放映射计算broadlog表的名称。
* SMS进程会使用消息ID和状态更新broadlog表。

**吞吐量和并行连接**

每个MTA子级都会创建一个可配置的连接数量，因此限制MTA子级的数量将限制连接数量。 由于MTA子进程与流量之间的关联是相关的，因此这可以受到一些控制，但仍有些不可预知。

## 上线前 {#checklist}

此检查列表列出了您在上线前应检查的内容。 设置不完整可能会导致许多问题。

### 检查外部帐户冲突 {#external-account-conflict}

检查您没有旧的短信外部帐户。 如果禁用测试帐户，则可能会使测试帐户在生产系统上重新启用并产生潜在冲突。

如果您在同一Adobe Campaign实例上有多个帐户连接到同一提供商，请联系该提供商，以确保它们实际区分这些帐户之间的连接。 拥有多个具有相同登录名的帐户需要额外配置。

### 在检查期间启用详细的SMPP跟踪 {#enable-verbose}

您应始终在检查期间启用详细的SMPP跟踪。
即使您无法自行检查日志， [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 来帮你。

### 测试短信 {#test}

* **发送包含各种字符的短信**
如果您需要发送包含非GSM或非ASCII字符的短信，请尝试尽可能发送包含多种字符的消息。 如果设置自定义字符映射表，请至少发送一条短信，以供所有可能 
`data_coding` values.

* **检查SR是否已正确处理**
短信应在投放日志中标记为已接收。 投放日志应该成功，如下所示：检查您是否更改了投放提供商名称。 投放日志不应包含    `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
检查您是否更改了投放提供商名称。 投放日志不应包含 **SR通用** 在生产环境中。

* **检查是否已处理MO**
如果需要处理MO（自动回复、将MO存储在数据库中等） 尝试做一些测试。 发送几条短信给所有自动回复关键词，并检查回复是否足够快，不超过几秒钟。
在日志中检查Adobe Campaign是否成功回复了 
`DELIVER_SM_RESP` (command_status=0)。

### 检查PDU {#check-pdus}

即使消息看起来成功，检查PDU的格式是否正确也很重要。

连接到之前未连接到Adobe Campaign的提供程序时，需要执行此步骤。

#### 绑定 {#bind}

检查 `BIND_* PDUs` 正确发送。 要检查的最重要的一点是，提供程序始终会返回成功 `BIND_*_RESP PDUs` (command_status = 0)。

确认没有太多 `BIND_* PDU`s.如果这些参数太多，则可能表示连接不稳定。 请参阅 [连接不稳定的问题](sms-protocol.md#issues-unstable-connection) 的子菜单。

#### INQUIRE_LINK {#enquire-link-pdus}

检查 `ENQUIRE_LINK PDU`连接空闲时，会定期交换。

**SUBMIT_SM / DELIVER_SM**

发送消息，然后在日志中搜索其对应的 `SUBMIT_SM`, `SUBMIT_SM_RESP`, `DELIVER_SM` 和 `DELIVER_SM_RESP PDU`s.

使用 `SUBMIT_SM PDU`:

* 检查 `data_coding` 正确，默认为0。
* 检查 `short_message` 正确编码。 尝试使用支持多个编码的十六进制转换器对其进行解码。

使用 `SUBMIT_SM_RESP PDU`:

* 检查成功，command_status = 0。
* 检查其正文是否包含格式正确的ID，后跟“0”字节。

使用 `DELIVER_SM PDU`:

* 解码十六进制 `short_message` 字段。
* 使用正则表达式检查工具检查中定义的正则表达式 `Extraction` SR中ID的正则表达式只会返回一个捕获组，并且会捕获消息中的整个ID。
* 检查提取的ID是否与 `SUBMIT_SM_RESP`.
* 检查中定义的正则表达式 `Extraction` SR中状态的正则表达式将返回stat字段的内容。
* 检查中定义的正则表达式 `Extraction` SR中错误的正则表达式将返回err字段的内容。

使用 `DELIVER_SM_RESP PDU`:

* 检查是否在收到 `DELIVER_SM PDU`，通常小于1秒。
* 检查成功，command_status = 0。

### 咨询您的提供商 {#provider}

即使短信成功，请与提供商联系以查看所有内容是否均正确。

### 禁用详细的SMPP跟踪 {#disable-verbose}

完成所有检查后，最后的任务是 **禁用详细的SMPP跟踪** 不会生成太多日志。 即使在生产系统上，您也可以重新启用它们，以便进行故障排除。
