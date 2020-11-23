---
solution: Campaign Classic
product: campaign
title: SMS 渠道
description: SMS 渠道
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '3149'
ht-degree: 20%

---


# SMS 渠道{#sms-channel}

Adobe Campaign使您能够执行大量个性化的SMS消息投放。 收件人用户档案必须至少包含移动电话号码。

>[!NOTE]
>
>Adobe Campaign还允许您通过其Adobe Campaign移动应用程序 **渠道(NMAC)选项在移动终端上提** 交通知。
> 
>有关此内容的详细信息，请参 [阅关于移动应用渠道](../../delivery/using/about-mobile-app-channel.md) 。

以下各节提供特定于SMS渠道的信息。 有关如何创建投放的全局信息，请参[阅此部分](../../delivery/using/steps-about-delivery-creation-steps.md)。

## 设置SMS渠道 {#setting-up-sms-channel}

要发送到移动电话，您需要：

1. 指定连接器和消息类型的外部帐户。

   请注意，从20.2版开始将弃用以下连接器：NetSize、通用SMPP（支持二进制模式的SMPP版本3.4）、Sybase365(SAP SMS 365)、 CLX Communications、Tele2、O2和iOS。 已弃用的功能仍然可用，但不会进一步增强，也不支持。 有关详细信息，请参见此 [ 页面](https://helpx.adobe.com/cn/campaign/kb/deprecated-and-removed-features.html)。

1. 引用此投放模板的外部帐户。

### Creating an SMPP external account {#creating-an-smpp-external-account}

要将SMS发送到移动电话，您首先需要创建SMPP外部帐户。
有关短信协议和设置的更多信息，请参阅此[技术说明](https://helpx.adobe.com/cn/campaign/kb/sms-connector-protocol-and-settings.html)。

为此请执行以下操作步骤：

1. 在树 **[!UICONTROL Platform]** 的 **[!UICONTROL External accounts]** >节点中，单击图 **[!UICONTROL New]** 标。
1. 将帐户类型定 **义为**&#x200B;路由，将 **渠道定义为移动(SMS)**，将投放模式定义为 **批量投放**。

   ![](assets/extended_smpp_create_account.png)

1. 选中 **[!UICONTROL Enabled]** 框。
1. 在选 **[!UICONTROL Mobile]** 项卡中， **[!UICONTROL Extended generic SMPP]** 从下 **[!UICONTROL Connector]** 拉列表中选择。

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > 从20.2版开始，已弃用传统连接器，不支持。 我们建议使用连 **[!UICONTROL Extended generic SMPP]** 接器。 有关如何迁移到推荐连接器的详细信息，请参阅本 [页](https://helpx.adobe.com/cn/campaign/kb/sms-connector.html)。

1. The **[!UICONTROL Enable verbose SMPP traces in the log file]** option allows you to dump all SMPP traffic in log files. 必须启用此选项才能对连接器进行故障诊断，并与提供商的通信记录进行对比。

1. 联系您的SMS服务提供商，他们将向您说明如何从选项卡中填写不同的外部帐户 **[!UICONTROL Connection settings]** 字段。

   然后，根据所选的提供商，联系您的提供商，该提供商将为您提供输入字段的 **[!UICONTROL SMSC implementation name]** 值。

   您可以为每个MTA子项定义与提供程序的连接数。 默认情况下，它设置为1。

1. 默认情况下，SMS中的字符数符合GSM标准。

   使用 GSM 编码的短信消息长度上限为 160 个字符，而对于分段发送的消息，每段短信的长度上限为 153 个字符。

   >[!NOTE]
   >
   >某些字符会被计为两个字符（大括号、方括号、欧元符号等）。
   >
   >可用GSM字符的列表如下。

   如果需要，您可通过勾选对应的方框来授权字符音译。

   ![](assets/extended_smpp_transliteration.png)

   如需详细信息，请参阅[此部分](#about-character-transliteration)。

1. In the **[!UICONTROL Throughput and delays]** tab, you can specify the maximum throughput of outbound messages (&quot;MT&quot;, Mobile Terminated) in MT per second. 如果在对应的字段中输入“0”，则吞吐量将没有限制。

   对应于持续时间的所有字段值，都必须填写以秒为单位的值。

1. 在选项卡 **[!UICONTROL Mapping of encodings]** 中，您可以定义编码。

   如需详细信息，请参阅[此部分](#about-text-encodings)。

1. 在选项 **[!UICONTROL SMSC specificities]** 卡中，该 **[!UICONTROL Send full phone number]** 选项默认处于禁用状态。 如果要遵守SMPP协议并仅将数字传输到SMS提供者(SMSC)的服务器，请不要启用它。

   但是，鉴于某些提供者需要使用“+”前缀，建议您与提供者进行核对，他们将建议在必要时启用此选项。

   The **[!UICONTROL Enable TLS over SMPP]** checkbox allows you to encrypt SMPP traffic. For more on this, refer to this [technical note](https://helpx.adobe.com/cn/campaign/kb/sms-connector-protocol-and-settings.html).

1. 如果要配置连接 **[!UICONTROL Extended generic SMPP]** 器，则可以设置自动回复。

   如需详细信息，请参阅[此部分](#automatic-reply)。

### 关于字音译 {#about-character-transliteration}

字符音译可在SMPP移动投放外部帐户中的选项卡下 **[!UICONTROL Mobile]** 设置。

音译指的是，如果 GSM 标准无法识别某个短信字符，则会用另一个字符替换该字符。

* If transliteration is **[!UICONTROL authorized]**, each character that is not taken into account is replaced by a GSM character when the message is sent. 例如，字母“ë”会被替换为“e”。因此，消息会有些微变化，但字符限制将保持不变。
* When transliteration is **[!UICONTROL not authorized]**, each message that contains characters that are not taken into account is sent in binary format (Unicode): all of the characters are therefore sent as they are. 但是，使用 Unicode 的短信消息长度上限为 70 个字符（对于分段发送的消息，每段短信的长度上限为 67 个字符）。如果超过最大字符数，则会分段发送多条消息，这可能会产生额外的费用。

>[!IMPORTANT]
>
>将个性化字段插入短信消息内容，可能会引入 GSM 编码无法识别的字符。

默认情况下，字符音译处于禁用状态。如果您希望将短信消息中的所有字符都按原样保留，以免名称等内容被错误地更改，我们建议您不要启用此选项。

但是，如果短信消息包含大量会生成 Unicode 消息的字符，则可以选择加入此选项以限制发送消息的成本。

下表显示GSM标准中考虑的字符。 除下方所列的字符外，插入消息正文的所有其他字符都会导致整个消息被转换为二进制格式 (Unicode)，从而使其长度限制变成 70 个字符。

**基本字符**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> ¡ </td> 
   <td> P </td> 
   <td> ¿ </td> 
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
   <td> ¤ </td> 
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
   <td> &lt; </td> 
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

### 关于文本编码 {#about-text-encodings}

发送短信消息时，Adobe Campaign 可以使用一个或多个文本编码。每个编码都有属于自己的特定字符集，可确定其适合短信消息的字符数。

配置新的SMPP移动投放外部帐户时，您可以在选项卡 **[!UICONTROL Mapping of encodings]** 中定义 **[!UICONTROL Mobile]** :该字 **[!UICONTROL data_coding]** 段允许Adobe Campaign向SMSC通信使用哪种编码。

>[!NOTE]
>
>**Data_coding** 值与实际使用的编码之间的映射，经过标准化处理。Nevertheless, certain SMSC have their own specific mapping: in this case, your **Adobe Campaign** administrator needs to declare this mapping. 有关更多信息，请咨询您的提供商。

You can declare **data_codings** and force the encoding if necessary: to do this, specify a single encoding in the table.

* 当未定义编码映射时，连接器采用通用行为：

   * 它会尝试将 GSM 编码用于分配值 **data_coding = 0**。
   * 如果 GSM 编码失败，则会将 **UCS2** 编码用于分配值 **data_coding = 8**。

* 当您定义要使用的编码以及链接的字段值时， **[!UICONTROL data_coding]** Adobe Campaign将尝试在列表中使用第一个编码，如果第一个编码被证明不可能，则使用下面的编码。

>[!IMPORTANT]
>
>声明的顺序很重要：建议您按照&#x200B;**成本**&#x200B;的升序方式排列编码列表，以选出可尽量减少短信消息发送条数的编码。
>
>仅声明您要使用的编码。如果SMSC提供的某些编码与您的使用目的不对应，请不要在列表中声明这些编码。

### 自动回复 {#automatic-reply}

在设置扩展的通用SMPP连接器时，您可以配置自动回复。

当Adobe Campaign回复通过SMS发送给他们的SMS消息并且其消息包含关键字（如“STOP”）时，您可以配置消息，该消息将自动发回给他们。 **[!UICONTROL Automatic reply sent to the MO]**

>[!NOTE]
>
>关键字不区分大小写。

对于每个关键字，指定一个简短的代码，该代码是通常用于发送投放并用作发送者姓名的编号，然后输入将发送给订阅者的消息。

您还可以将操作链接到自动响应： **[!UICONTROL Send to quarantine]** 或 **[!UICONTROL Remove from quarantine]**&#x200B;者 例如，如果收件人发送关键字“STOP”，则他们将自动收到退订确认并发送给隔离。

![](assets/extended_smpp_reply.png)

如果将操作链 **[!UICONTROL Remove from quarantine]** 接到自动响应，则发送相应关键字的收件人会自动从隔离中删除。

收件人列在可通过 **[!UICONTROL Non deliverables and addresses]** > >菜单 **[!UICONTROL Administration]** 查 **[!UICONTROL Campaign Management]** 看的表 **[!UICONTROL Non deliverables Management]** 中。

* 要发送相同的回复，无论使用什么短代码，请将该列 **[!UICONTROL Short code]** 留空。
* 要发送相同的回复，无论关键字是什么，请将列 **[!UICONTROL Keyword]** 留空。
* 要在不发送响应的情况下执行操作，请将该列 **[!UICONTROL Response]** 留空。 例如，这允许您从回复消息(“STOP”)的用户的隔离中删除。

如果您有多个外部帐户使用具有相同提供者帐户的扩展通用SMPP连接器，则可能会出现以下问题：在向短代码发送回复时，可能会在您的任何外部帐户连接上收到该回复。 因此，发送的自动回复不能是预期消息。
要避免这种情况，请根据您所使用的提供商，应用以下解决方案之一：

* 为每个外部帐户创建一个提供程序帐户。
* 使用> **[!UICONTROL System type]** 选项卡中的字 **[!UICONTROL Mobile]** 段 **[!UICONTROL Connection settings]** 来区分每个短代码。 为每个帐户向提供者询问不同的值。

   ![](assets/extended_smpp_system-type.png)

使用扩展通用SMPP连接器设置外部帐户的步骤在创建SMPP [外部帐户部分中有详细介绍](../../delivery/using/sms-channel.md#creating-an-smpp-external-account) 。

### 更改投放模板 {#changing-the-delivery-template}

Adobe Campaign为您提供了用于传送到移动设备的模板。 此模板在节点中 **[!UICONTROL Resources > Templates > Delivery templates]** 可用。 For more on this, refer to the [About templates](../../delivery/using/about-templates.md) section.

要通过SMS渠道进行传送，您必须创建引用渠道连接器的模板。

为了保持本机投放模板，我们建议您重复它，然后对其进行配置。

在以下示例中，我们创建一个模板，通过先前启用的SMPP帐户传送消息。 操作步骤：

1. Go to the **[!UICONTROL Delivery templates]** node.
1. 右键单击模 **[!UICONTROL Send to mobiles]** 板，然后选择 **[!UICONTROL Duplicate]**。

   ![](assets/s_user_mobile_template_change_01.png)

1. 更改模板的标签，例如“已 **发送到移动设备(SMPP)”**。

   ![](assets/s_user_mobile_template_change_02.png)

1. 单击 **[!UICONTROL Properties]**.
1. 在选 **[!UICONTROL General]** 项卡中，选择与您在前面的步骤中创建的路由对应的外部帐户模式。

   ![](assets/s_user_mobile_template_change_03.png)

1. 单击 **[!UICONTROL Save]** 以创建模板。

   ![](assets/s_user_mobile_template_list.png)

您现在拥有外部帐户和投放模板，可通过SMS提供。

## 创建SMS投放 {#creating-a-sms-delivery}

### 选择投放渠道 {#selecting-the-delivery-channel}

要创建新的SMS投放，请按照以下步骤操作：

>[!NOTE]
>
>本节介绍有关投放创建的全 [局概念](../../delivery/using/steps-about-delivery-creation-steps.md)。

1. 创建新投放，例如从投放仪表板创建。
1. 选择您之 **前创建的投放模板** “发送到手机”(SMPP)。 For more on this, refer to the [Changing the delivery template](#changing-the-delivery-template) section.

   ![](assets/s_user_mobile_wizard.png)

1. 用标签、代码和说明来识别投放。 如需详细信息，请参阅[此部分](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)。
1. 单击 **[!UICONTROL Continue]** 以确认此信息并显示消息配置窗口。

## 定义SMS内容 {#defining-the-sms-content}

要创建SMS内容，请执行以下步骤：

1. 在向导的部分中输 **[!UICONTROL Text content]** 入消息内容。 工具栏按钮允许您导入、保存或搜索内容。 最后一个按钮用于插入个性化字段。

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   个性化字段的使用情况在“关于个 [性化](../../delivery/using/about-personalization.md) ”部分。

1. 单 **[!UICONTROL Preview]** 击页面底部以视图消息呈现及其个性化。 要启动预览，请使用工具栏中的按 **[!UICONTROL Test personalization]** 钮选择收件人。 您可以从定义的收件人中选择一个目标或选择其他收件人。

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   您可以批准SMS消息。 您还可以在内容编辑器右侧显示的手机屏幕上视图SMS的内容。 单击屏幕，然后使用鼠标滚动浏览内容。

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 单击链 **[!UICONTROL Data loaded]** 接以视图与收件人相关的信息。

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >如果使用拉丁文-1(ISO-8859-1)代码页，SMS消息的长度限制为160个字符。 如果消息以Unicode编写，则不得超过70个字符。 某些特殊字符会影响消息长度。 有关消息长度的详细信息，请参阅“关 [于字符音译](#about-character-transliteration) ”部分。
   >
   >当存在个性化字段或条件内容字段时，消息的大小因收件人而异。 在进行个性化时，必须评估消息的长度。
   >
   >启动分析时，将检查消息的长度，并在溢出事件中显示警告。

1. 如果您使用NetSize连接器或SMPP连接器，则可以个性化投放发送者的姓名。 For more on this, refer to the [Advanced parameters](#advanced-parameters) section.

## 选择目标群 {#selecting-the-target-population}

本节介绍了选择目标的投放种群时的详细 [过程](../../delivery/using/steps-defining-the-target-population.md)。

有关个性化字段使用的详细信息，请参阅关 [于个性化](../../delivery/using/about-personalization.md)。

有关包含种子列表的详细信息，请参 [阅关于种子地址](../../delivery/using/about-seed-addresses.md)。

## 发送短信 {#sending-sms-messages}

要批准您的邮件并将其发送到所创建投放的收件人，请单击 **[!UICONTROL Send]**。

验证和发送投放时的详细过程将在以下各节中介绍：

* [验证投放](../../delivery/using/steps-validating-the-delivery.md)
* [发送投放](../../delivery/using/steps-sending-the-delivery.md)

### 高级参数 {#advanced-parameters}

按 **[!UICONTROL Properties]** 钮允许访问高级投放参数。 特定于SMS投放的参数位 **[!UICONTROL SMS parameters]** 于选项卡的 **[!UICONTROL Delivery]** 部分。

可以使用以下选项：

* **发件人地址**:允许您使用限制为11个字符的字母数字字符串，个性化投放发件人的姓名。 这个领域不能只由数字组成。 您可以定义一个条件来显示，例如，根据收件人的区域代码显示不同的名称：

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >检查您所在国家／地区有关编辑发件人姓名的法律。 您还应询问操作员是否优惠此功能。

* **传输模式**:短信发送
* **优先级**:消息的重要性级别。 **[!UICONTROL Normal]** 优先级默认为选中。 询问您的服务提供商优先发送的短信费 **[!UICONTROL High]** 用。
* **应用程序类型**:选择要分配给SMS投放的应用程序。 默认 **[!UICONTROL Direct Marketing]** 情况下，该选项处于选中状态，是最常用的选项。

**特定于NetSize连接器的参数**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **对单条消息使用多条SMS**:这样，您就可以通过多个SMS消息发送超过160个字符的消息。

**SMPP连接器特有的参数**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **每条消息的最大短信数**:通过此选项，可设置用于发送消息的SMS数。 如果数字设置为0，则可以使用SMS发送消息。 如果SMS的数量设置为1或2，并且消息超过此阈值，则不会发送该消息。

## 监控和跟踪SMS投放 {#monitoring-and-tracking-sms-deliveries}

发送消息后，您可以监视和跟踪投放。 有关更多信息，请参阅一下章节。

* [监控投放](../../delivery/using/monitoring-a-delivery.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [关于邮件跟踪](../../delivery/using/about-message-tracking.md)

## 处理入站消息 {#processing-inbound-messages}

nlserver **sms** 模块定期查询SMS路由器。 这允许Adobe Campaign跟踪投放进度并处理状态报告和收件人退订请求。

* **状态报告**:视图投放日志检查消息的状态。

   >[!NOTE]
   >
   >发送的每条短信都链接到外部帐户的主密钥。 这样：
   >
   > * 已删除的外部SMS帐户的状态报告未正确处理。
   > * SMS帐户只能链接到单个外部帐户，以确保状态报告归因到正确的帐户


* **退订**:希望停止接收SMS投放的收件人可以返回包含STOP字样的消息。 如果您的提供商根据合同条款允许它访问，您可以通过 **Inbound SMS工作流活动检索消息** ，然后创建一个查询，为相关收件人启 **用“不再联系此收件人** ”选项。

   请参阅 [工作流](../../workflow/using/architecture.md) 指南。

## InSMS模式 {#insms-schema}

InSMS模式包含与传入SMS相关的信息。 可通过desc属性描述这些字段。

* **消息**:收到的短信内容。
* **来源**:消息来源处的移动号码。
* **providerId**:SMSC（消息中心）返回的消息的标识符。
* **已创建**:将传入消息插入Adobe Campaign。
* **extAccount**:Adobe Campaign外部帐户。

   >[!IMPORTANT]
   >
   >以下字段特定于NetSize。
   >
   >如果使用的运算符不是NetSize，则这些字段被视为空。

* **别名**:传入消息的别名。
* **分隔符**:别名和邮件正文之间的分隔符。
* **messageDate**:运算符给出的消息日期。
* **receivalDate**:SMSC（消息中心）接收来自运营商的日期消息。
* **deliveryDate**:SMSC（消息中心）发送的日期消息。
* **largeAccount**:客户帐户代码链接到传入的SMS。
* **countryCode**:运营商国家／地区代码。
* **operatorCode**:运营商网络代码。
* **linkedSmsId**:Adobe Campaign标识符(broadlogId)，链接到传出SMS，其中此SMS是响应。

## 管理自动回复（美国法规） {#managing-automatic-replies--american-regulation-}

当用户回复通过Adobe Campaign发送给他们的SMS消息时，他们使用STOP、HELP或YES等关键字，在美国市场上有必要配置自动返回的消息。

例如，如果收件人发送关键字STOP，则他们会自动收到一条确认消息，表明他们已取消订阅。

此类邮件的发件人姓名是通常用于发送投放的简短代码。

>[!IMPORTANT]
>
>以下详细过程仅对SMPP连接器有效，扩展通用SMPP连接器除外。 有关此内容的详细信息，请参 [阅创建SMPP外部帐户](#creating-an-smpp-external-account) 。
>
>它构成了美国运营商为美国营销活动进行的认证过程的一部分。 对包含关键字的订户SMS消息的这些回复必须在收到来自它们的消息后立即发送回订户。

1. 创建此类型的XML文件：

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. 对于 **标记** name属 **`<shortcode>`** 性，指定将在消息发送者名称的位置显示的简短代码。

   在每个 **`<reply>`** 标记中，输 **入关键字属性** ，输入文本属 **** 性，并输入要为此关键字发送的消息。

   >[!NOTE]
   >
   >每个关键字都必须用大写字母写成。

   如果要为多个关键字发送相同的消息，请重复相应的行。

   例如：

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 完成后，以smsAutoReply.xml名称保 **存此文件**。

   请注意，在Linux中，文件名区分大小写。

1. 将此文件复制 **到Adobe Campaign** （与Web服务器位于同一位置）的conf目录中。

>[!IMPORTANT]
>
>这类自动消息不会保留历史记录。 因此，它们不会出现在 [投放仪表板中](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard)。
>
>这些消息不被视为商业压力 [规则的一部分](../../campaign/using/pressure-rules.md)。
