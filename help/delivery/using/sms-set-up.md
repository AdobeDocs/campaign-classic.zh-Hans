---
product: campaign
title: 设置营销活动短信渠道
description: 了解如何在Campaign中配置短信渠道
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: a2783a5e-6d38-41a1-b5c6-24ab489116f8
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 35%

---

# 配置短信渠道 {#setting-up-sms-channel}

![](../../assets/common.svg)

要发送到移动电话，您需要：

1. 指定连接器和消息类型的外部帐户。

   请注意，现已弃用旧版连接器。 已弃用的功能仍然可用，但不会进一步增强或支持这些功能。请参阅[此页面](../../rn/using/deprecated-features.md)以了解详情。

1. 在其中引用此外部帐户的投放模板。

## 创建SMPP外部帐户 {#creating-an-smpp-external-account}

要向手机发送短信，您首先需要创建SMPP外部帐户。
有关短信协议和设置的更多信息，请参阅此[页面](sms-protocol.md)。

为此请执行以下操作步骤：

1. 在树的&#x200B;**[!UICONTROL Platform]** > **[!UICONTROL External accounts]**&#x200B;节点中，单击&#x200B;**[!UICONTROL New]**&#x200B;图标。
1. 将帐户类型定义为&#x200B;**Routing**，渠道定义为&#x200B;**Mobile(SMS)**，投放模式定义为&#x200B;**Bulk delivery**。

   ![](assets/extended_smpp_create_account.png)

1. 选中&#x200B;**[!UICONTROL Enabled]**&#x200B;框。
1. 在&#x200B;**[!UICONTROL Mobile]**&#x200B;选项卡的&#x200B;**[!UICONTROL Connector]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Extended generic SMPP]**。

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > 自20.2版起，已弃用旧版连接器，不支持该连接器。 我们建议使用&#x200B;**[!UICONTROL Extended generic SMPP]**&#x200B;连接器。 有关如何迁移到推荐连接器的更多信息，请参阅此[page](unsupported-connector-migration.md)。

1. 利用&#x200B;**[!UICONTROL Enable verbose SMPP traces in the log file]**&#x200B;选项，可将所有SMPP流量转储到日志文件中。 必须启用此选项才能对连接器进行故障诊断，并与提供商的通信记录进行对比。

1. 请联系短信服务提供商，该服务提供商将向您说明如何从&#x200B;**[!UICONTROL Connection settings]**&#x200B;选项卡填写不同的外部帐户字段。

   然后，根据所选的提供商，联系您的提供商，该提供商将为您提供输入到&#x200B;**[!UICONTROL SMSC implementation name]**&#x200B;字段中的值。

   您可以为每个MTA子级定义与提供程序的连接数。 默认情况下，该参数设置为1。

1. 默认情况下，短信的字符数符合GSM标准。

   使用 GSM 编码的短信消息长度上限为 160 个字符，而对于分段发送的消息，每段短信的长度上限为 153 个字符。

   >[!NOTE]
   >
   >某些字符会被计为两个字符（大括号、方括号、欧元符号等）。
   >
   >可用GSM字符列表如下所示。

   如果需要，您可通过勾选对应的方框来授权字符音译。

   ![](assets/extended_smpp_transliteration.png)

   如需详细信息，请参阅[此部分](#about-character-transliteration)。

1. 在&#x200B;**[!UICONTROL Throughput and delays]**&#x200B;选项卡中，可以指定出站消息的最大吞吐量（“MT”，“终止移动设备”）（以每秒MT为单位）。 如果在对应的字段中输入“0”，则吞吐量将没有限制。

   对应于持续时间的所有字段值，都必须填写以秒为单位的值。

1. 在&#x200B;**[!UICONTROL Mapping of encodings]**&#x200B;选项卡中，您可以定义编码。

   如需详细信息，请参阅[此部分](#about-text-encodings)。

1. 在&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;选项卡中，默认情况下禁用&#x200B;**[!UICONTROL Send full phone number]**&#x200B;选项。 如果要遵循SMPP协议并仅将数字传输到短信提供商(SMSC)的服务器，请勿启用它。

   但是，鉴于某些提供商需要使用“+”前缀，建议您与提供商进行核实，他们将在必要时建议您启用此选项。

   利用&#x200B;**[!UICONTROL Enable TLS over SMPP]**&#x200B;复选框，可加密SMPP通信。 有关详细信息，请参见此 [ 页面](sms-protocol.md)。

1. 如果要配置&#x200B;**[!UICONTROL Extended generic SMPP]**&#x200B;连接器，则可以设置自动回复。

   如需详细信息，请参阅[此部分](#automatic-reply)。

## 短信字符音译 {#about-character-transliteration}

可以在SMPP移动投放外部帐户的&#x200B;**[!UICONTROL Mobile]**&#x200B;选项卡下设置字符音译。

音译指的是，如果 GSM 标准无法识别某个短信字符，则会用另一个字符替换该字符。

* 如果音译为&#x200B;**[!UICONTROL authorized]**，则发送消息时，无法识别的每个字符都将被替换为GSM字符。 例如，字母“ë”会被替换为“e”。因此，消息会有些微变化，但字符限制将保持不变。
* 当音译为&#x200B;**[!UICONTROL not authorized]**&#x200B;时，包含无法识别字符的每条消息都将以二进制格式(Unicode)发送：因此，所有字符都会按原样发送。 但是，使用 Unicode 的短信消息长度上限为 70 个字符（对于分段发送的消息，每段短信的长度上限为 67 个字符）。如果超过最大字符数，则会分段发送多条消息，这可能会产生额外的费用。

>[!IMPORTANT]
>
>将个性化字段插入短信消息内容，可能会引入 GSM 编码无法识别的字符。

默认情况下，字符音译处于禁用状态。如果您希望将短信消息中的所有字符都按原样保留，以免名称等内容被错误地更改，我们建议您不要启用此选项。

但是，如果短信消息包含大量会生成 Unicode 消息的字符，则可以选择加入此选项以限制发送消息的成本。

下表显示GSM标准所考虑的字符。 除下方所列的字符外，插入消息正文的所有其他字符都会导致整个消息被转换为二进制格式 (Unicode)，从而使其长度限制变成 70 个字符。

**基本字符**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> recomplend </td> 
   <td> P </td> 
   <td> - </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
   <td> _ </td> 
   <td> ! </td> 
   <td> 1 </td> 
   <td> A </td> 
   <td> Q </td> 
   <td> a </td> 
   <td> q </td> 
  </tr> 
  <tr> 
   <td> $ </td> 
   <td> <img height="21px" src="assets/phi.png" /> </td> 
   <td> ” </td> 
   <td> 2 </td> 
   <td> B </td> 
   <td> R </td> 
   <td> b </td> 
   <td> r </td> 
  </tr> 
  <tr> 
   <td> ¥ </td> 
   <td> <img height="21px" src="assets/gamma.png" /> </td> 
   <td> # </td> 
   <td> 3 </td> 
   <td> C </td> 
   <td> S </td> 
   <td> c </td> 
   <td> s </td> 
  </tr> 
  <tr> 
   <td> è </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> 悠悠 </td> 
   <td> 4 </td> 
   <td> D </td> 
   <td> T </td> 
   <td> d </td> 
   <td> t </td> 
  </tr> 
  <tr> 
   <td> é </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> ù </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> ì </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> ò </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> Ç </td> 
   <td> <img height="21px" src="assets/theta.png" /> </td> 
   <td> ) </td> 
   <td> 9 </td> 
   <td> I </td> 
   <td> Y </td> 
   <td> i </td> 
   <td> y </td> 
  </tr> 
  <tr> 
   <td> LF </td> 
   <td> <img height="21px" src="assets/xi.png" /> </td> 
   <td> * </td> 
   <td> : </td> 
   <td> J </td> 
   <td> Z </td> 
   <td> j </td> 
   <td> z </td> 
  </tr> 
  <tr> 
   <td> Ø </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ä </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> ø </td> 
   <td> Æ </td> 
   <td> , </td> 
   <td> &lt;&gt; </td> 
   <td> L </td> 
   <td> Ö </td> 
   <td> l </td> 
   <td> ö </td> 
  </tr> 
  <tr> 
   <td> CR </td> 
   <td> æ </td> 
   <td> - </td> 
   <td> = </td> 
   <td> M </td> 
   <td> Ñ </td> 
   <td> m </td> 
   <td> ñ </td> 
  </tr> 
  <tr> 
   <td> Å </td> 
   <td> ß </td> 
   <td> 。 </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> Ü </td> 
   <td> n </td> 
   <td> ü </td> 
  </tr> 
  <tr> 
   <td> å </td> 
   <td> É </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> à </td> 
  </tr> 
 </tbody> 
</table>

SP：空格键

ESC：Escape 键

LF：换行

CR：回车

**高级字符（计为两个字符）**

^ { } `[ ~ ]` | €

## 文本编码 {#about-text-encodings}

发送短信消息时，Adobe Campaign 可以使用一个或多个文本编码。每个编码都有属于自己的特定字符集，可确定其适合短信消息的字符数。

配置新的SMPP移动投放外部帐户时，您可以在&#x200B;**[!UICONTROL Mobile]**&#x200B;选项卡中定义&#x200B;**[!UICONTROL Mapping of encodings]**:**[!UICONTROL data_coding]**&#x200B;字段允许Adobe Campaign向SMSC通信使用的编码。

>[!NOTE]
>
>**Data_coding** 值与实际使用的编码之间的映射，经过标准化处理。但是，某些SMSC有其自己的特定映射：在这种情况下，您的&#x200B;**Adobe Campaign**&#x200B;管理员需要声明此映射。 有关更多信息，请咨询您的提供商。

您可以声明&#x200B;**data_codings**，并在必要时强制进行编码：要实现此目的，请在表中指定单个编码。

* 未定义编码映射时，连接器会采取一般行为：

   * 它会尝试将 GSM 编码用于分配值 **data_coding = 0**。
   * 如果 GSM 编码失败，则会将 **UCS2** 编码用于分配值 **data_coding = 8**。

* 在定义要使用的编码以及链接的&#x200B;**[!UICONTROL data_coding]**&#x200B;字段值时，Adobe Campaign将尝试使用列表中的第一个编码，如果第一个编码被证明不可能，则使用下面的编码。

>[!IMPORTANT]
>
>声明的顺序很重要：建议您按照&#x200B;**成本**&#x200B;的升序方式排列编码列表，以选出可尽量减少短信消息发送条数的编码。
>
>仅声明您要使用的编码。如果SMSC提供的某些编码与您的使用目的不对应，请勿在列表中声明这些编码。

## 自动回复 {#automatic-reply}

在设置扩展的通用SMPP连接器时，您可以配置自动回复。

当订阅者回复通过Adobe Campaign发送给他们的短信消息且其消息包含“STOP”等关键字时，您可以在&#x200B;**[!UICONTROL Automatic reply sent to the MO]**&#x200B;部分配置自动发回给他们的消息。

>[!NOTE]
>
>关键词不区分大小写。

对于每个关键词，指定一个短代码（通常用于发送投放并用作发件人名称的数字），然后输入要发送给订阅者的消息。

您还可以将操作链接到自动响应：**[!UICONTROL Send to quarantine]**&#x200B;或&#x200B;**[!UICONTROL Remove from quarantine]**。 例如，如果收件人发送关键词“STOP”，则他们将自动收到退订确认并进行隔离。

![](assets/extended_smpp_reply.png)

如果将&#x200B;**[!UICONTROL Remove from quarantine]**&#x200B;操作链接到自动响应，则发送相应关键字的收件人将自动从隔离中删除。

通过&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**&#x200B;菜单提供的&#x200B;**[!UICONTROL Non deliverables and addresses]**&#x200B;表中列出了收件人。

* 要不管什么是短代码，都发送相同的回复，请将&#x200B;**[!UICONTROL Short code]**&#x200B;列留空。
* 要不管关键字是什么都发送相同的回复，请将&#x200B;**[!UICONTROL Keyword]**&#x200B;列留空。
* 要在不发送响应的情况下执行操作，请将&#x200B;**[!UICONTROL Response]**&#x200B;列留空。 例如，这允许您从隔离中删除回复了“STOP”以外消息的用户。

如果您使用具有相同提供商帐户的扩展通用SMPP连接器拥有多个外部帐户，则可能会出现以下问题：在发送短代码回复时，可能会在您的任何外部帐户连接上收到该回复。 因此，发送的自动回复不能是预期消息。
要避免这种情况，请根据您使用的提供商，应用以下解决方案之一：

* 为每个外部帐户创建一个提供程序帐户。
* 使用&#x200B;**[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]**&#x200B;选项卡中的&#x200B;**[!UICONTROL System type]**&#x200B;字段区分每个短代码。 为每个帐户向提供商请求不同的值。

   ![](assets/extended_smpp_system-type.png)

[创建SMPP外部帐户](#creating-an-smpp-external-account)一节中详细描述了使用扩展通用SMPP连接器设置外部帐户的步骤。

## 更改投放模板 {#changing-the-delivery-template}

Adobe Campaign为您提供了用于投放到手机的模板。 此模板在&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;节点中可用。 有关更多信息，请参阅[关于模板](about-templates.md)一节。

要通过SMS渠道进行投放，您必须创建引用渠道连接器的模板。

为了保留本机投放模板，我们建议您复制该模板，然后对其进行配置。

在以下示例中，我们创建了一个模板，以通过之前启用的SMPP帐户来投放消息。 操作步骤：

1. 转到&#x200B;**[!UICONTROL Delivery templates]**&#x200B;节点。
1. 右键单击&#x200B;**[!UICONTROL Send to mobiles]**&#x200B;模板，然后选择&#x200B;**[!UICONTROL Duplicate]**。

   ![](assets/s_user_mobile_template_change_01.png)

1. 更改模板的标签，例如&#x200B;**发送到手机(SMPP)**。

   ![](assets/s_user_mobile_template_change_02.png)

1. 单击 **[!UICONTROL Properties]**。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，选择与您在前面步骤中创建的外部帐户对应的路由模式。

   ![](assets/s_user_mobile_template_change_03.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建模板。

   ![](assets/s_user_mobile_template_list.png)

您现在拥有外部帐户和投放模板，可通过短信进行投放。
