---
title: SMS渠道
seo-title: SMS渠道
description: SMS渠道
seo-description: null
page-status-flag: never-activated
uuid: be6a2abc-ba5c-4363-bf38-cc309ee3a8d9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
discoiquuid: 8b101c0b-3611-4f15-813b-7c0bf54fc48a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9773e8ae39133968e4e167d11715c123e00d22c2
workflow-type: tm+mt
source-wordcount: '3227'
ht-degree: 2%

---


# SMS渠道{#sms-channel}

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

   可用连接器包括： NetSize、通用SMPP（支持二进制模式的SMPP版本3.4）、Sybase365(SAP SMS 365)、 CLX Communications、Tele2、O2和扩展通用SMPP。

1. 引用此投放模板的外部帐户。

### 激活外部帐户 {#activating-an-external-account}

外部帐户的列表位于Adobe Campaign浏览器 **[!UICONTROL Platform]** 树 **[!UICONTROL External accounts]** 的>节点中。

* 例如，转到名为的默认帐户 **[!UICONTROL NetSize mobile delivery]**。
* 在选 **[!UICONTROL General]** 项卡中，选中 **[!UICONTROL Enabled]** 复选框。

   ![](assets/s_user_external_account_01.png)

* 检查是否 **[!UICONTROL Mobile]** 为字段选择了 **[!UICONTROL Channel]** 选项。
* 在选 **[!UICONTROL Mobile]** 项卡中，从下拉列表中选择连接器： NetSize、通用SMPP、Sybase365(SAP SMS 365)、 CLX Communications、Tele2、O2或扩展通用SMPP。 有关扩展通用SMPP连接器的详细信息，请参 [阅创建SMPP外部帐户](#creating-an-smpp-external-account) 。

   ![](assets/s_user_external_account_connect_01.png)

* 根据供应商提供的信息配置连接器。 在以下示例中，运算符为NetSize。

   ![](assets/s_user_external_account_param.png)

* 在选项 **[!UICONTROL Connector]** 卡中，将激活 **[!UICONTROL Call Web Service]** 模式保留为默认选中状态。

   ![](assets/s_user_external_account_param_02.png)

* 如果显 **[!UICONTROL Connector]** 示选项卡，则指定连接器的访问URL。 如果提供程序是 **NetSize，则该地址必须以** netsize.jsp结尾。 对于所有其他连接器，URL地址以 **smpp34.jsp结尾**。

### 创建SMPP外部帐户 {#creating-an-smpp-external-account}

如果要使用SMPP协议，还可以创建新外部帐户。

有关SMS协议和设置的详细信息，请参阅此技 [术说明](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)。

为此请执行以下操作步骤：

1. 在树 **[!UICONTROL Platform]** 的 **[!UICONTROL External accounts]** >节点中，单击图 **[!UICONTROL New]** 标。
1. 将帐户类型定 **义为**&#x200B;路由，将 **渠道定义为移动(SMS)**，将投放模式定义为 **批量投放**。

   ![](assets/extended_smpp_create_account.png)

1. 选中 **[!UICONTROL Enabled]** 框。
1. 在选 **[!UICONTROL Mobile]** 项卡中， **[!UICONTROL Extended generic SMPP]** 从下 **[!UICONTROL Connector]** 拉列表中选择。

   ![](assets/extended_smpp_connector.png)

   该 **[!UICONTROL Enable verbose SMPP traces in the log file]** 选项允许您将所有SMPP流量转储到日志文件中。 必须启用此选项才能对连接器进行故障诊断，并与提供者看到的流量进行比较。

1. 联系您的SMS服务提供商，他们将向您说明如何从选项卡中填写不同的外部帐户 **[!UICONTROL Connection settings]** 字段。

   然后，根据所选的提供商，联系您的提供商，该提供商将为您提供输入字段的 **[!UICONTROL SMSC implementation name]** 值。

   您可以为每个MTA子项定义与提供程序的连接数。 默认情况下，它设置为1。

1. 默认情况下，SMS中的字符数符合GSM标准。

   使用GSM编码的SMS消息限于160个字符，或对于多个部分发送的消息，每个SMS限制153个字符。

   >[!NOTE]
   >
   >某些字符计为两个（大括号、方括号、欧元符号等）。
   >
   >可用GSM字符的列表如下。

   如果您喜欢，可通过选中相应的框来授权字符音译。

   ![](assets/extended_smpp_transliteration.png)

   如需详细信息，请参阅[此部分](#about-character-transliteration)。

1. 在选 **[!UICONTROL Throughput and delays]** 项卡中，可以指定每秒MT的出站消息的最大吞吐量（“MT”，已终止移动设备）。 如果在相应字段中输入“0”，吞吐量将无限制。

   需要以秒完成与持续时间对应的所有字段的值。

1. 在选项卡 **[!UICONTROL Mapping of encodings]** 中，您可以定义编码。

   如需详细信息，请参阅[此部分](#about-text-encodings)。

1. 在选项 **[!UICONTROL SMSC specificities]** 卡中，该 **[!UICONTROL Send full phone number]** 选项默认处于禁用状态。 如果要遵守SMPP协议并仅将数字传输到SMS提供者(SMSC)的服务器，请不要启用它。

   但是，鉴于某些提供者需要使用“+”前缀，建议您与提供者进行核对，他们将建议在必要时启用此选项。

   通过 **[!UICONTROL Enable TLS over SMPP]** 此复选框可加密SMPP通信。 有关此的详细信息，请参阅此 [技术说明](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)。

1. 如果要配置连接 **[!UICONTROL Extended generic SMPP]** 器，则可以设置自动回复。

   如需详细信息，请参阅[此部分](#automatic-reply)。

### 关于字音译 {#about-character-transliteration}

字符音译可在SMPP移动投放外部帐户中的选项卡下 **[!UICONTROL Mobile]** 设置。

音译包括当GSM标准未考虑SMS字符时，用另一个字符替换该字符。

* 如果音译 **[!UICONTROL authorized]**&#x200B;是音译的，则在发送消息时，未考虑的每个字符将替换为GSM字符。 例如，字母“ë”被替换为“e”。 因此，消息会稍作更改，但字符限制将保持不变。
* 当音译 **[!UICONTROL not authorized]**&#x200B;时，包含未考虑的字符的每条消息都以二进制格式(Unicode)发送： 因此，所有字符都按原样发送。 但是，使用Unicode的SMS消息最多限制为70个字符（对于多部分发送的消息，每个SMS限制为67个字符）。 如果超过最大字符数，则会发送多条消息，这可能会产生额外费用。

>[!IMPORTANT]
>
>将个性化字段插入SMS消息内容可能会引入GSM编码未考虑的字符。

默认情况下，字符音译处于禁用状态。 如果您希望SMS消息中的所有字符都按原样保留，请不要更改正确的名称，例如，我们建议您不启用此选项。

但是，如果SMS消息包含大量生成Unicode消息的字符，则可以选择启用此选项来限制发送消息的成本。

下表显示GSM标准中考虑的字符。 除下面提到的字符外，插入消息正文的所有字符都会将整个消息转换为二进制格式(Unicode)，因此将其限制为70个字符。

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
   <td> " </td> 
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
   <td> 埃 </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> 耶 </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> 伊 </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> 奥 </td> 
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
   <td> 我 </td> 
   <td> Y </td> 
   <td> 我 </td> 
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
   <td> 岛 </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ä </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> 岛 </td> 
   <td> AE </td> 
   <td> , </td> 
   <td> &lt; </td> 
   <td> L </td> 
   <td> 厄 </td> 
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
   <td> - </td> 
  </tr> 
  <tr> 
   <td> 奥 </td> 
   <td> ß </td> 
   <td> . </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> 乌 </td> 
   <td> n </td> 
   <td> 女 </td> 
  </tr> 
  <tr> 
   <td> å </td> 
   <td> 埃 </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> 如 </td> 
  </tr> 
 </tbody> 
</table>

SP: 空间

ESC: 逃生

LF: 线源

CR: 回车

**高级字符（计数两次）**

^ { } `[ ~ ]` | €

### 关于文本编码 {#about-text-encodings}

在发送SMS消息时，Adobe Campaign可以使用一个或多个文本编码。 每个编码都有其自己的特定字符集，并确定适合SMS消息的字符数。

配置新的SMPP移动投放外部帐户时，您可以在选项卡 **[!UICONTROL Mapping of encodings]** 中定义 **[!UICONTROL Mobile]** : 该字 **[!UICONTROL data_coding]** 段允许Adobe Campaign向SMSC通信使用哪种编码。

>[!NOTE]
>
>data_coding值与实际 **使用的编码** 之间的映射是标准化的。 然而，某些中小企业供应链有自己的具体映射： 在这种情况下，您的 **Adobe Campaign** 管理员需要声明此映射。 请咨询您的提供商，了解更多信息。

您可以声 **明data_codings** ，并在必要时强制进行编码： 为此，请在表中指定单个编码。

* 当未定义编码映射时，连接器采用通用行为：

   * 它将尝试使用其分配值data_coding = **0的GSM编码**。
   * 如果GSM编码失败，它将 **使用** UCS2编码，它将值 **data_coding = 8**。

* 当您定义要使用的编码以及链接的字段值时， **[!UICONTROL data_coding]** Adobe Campaign将尝试在列表中使用第一个编码，如果第一个编码被证明不可能，则使用下面的编码。

>[!IMPORTANT]
>
>申报顺序很重要： 建议您按成本的升序排 **列列表** ，以便使用编码，在每条SMS消息中尽可能多地显示字符。
>
>仅声明要使用的编码。 如果SMSC提供的某些编码与您的使用目的不对应，请不要在列表中声明这些编码。

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
* 要发送相同的回复，无论关键字是什么，请将该 **[!UICONTROL Keyword]** 列留空。
* 要在不发送响应的情况下执行操作，请将该列 **[!UICONTROL Response]** 留空。 例如，这允许您从回复消息(“STOP”)的用户的隔离中删除。

如果您有多个外部帐户使用具有相同提供者帐户的扩展通用SMPP连接器，则可能会出现以下问题： 在向短代码发送回复时，可能会在您的任何外部帐户连接上收到该回复。 因此，发送的自动回复不能是预期消息。
要避免这种情况，请根据您所使用的提供商，应用以下解决方案之一：
* 为每个外部帐户创建一个提供程序帐户。
* 使用> **[!UICONTROL System type]** 选项卡中的字 **[!UICONTROL Mobile]** 段 **[!UICONTROL Connection settings]** 来区分每个短代码。 为每个帐户向提供者询问不同的值。

   ![](assets/extended_smpp_system-type.png)

使用扩展通用SMPP连接器设置外部帐户的步骤在创建SMPP [外部帐户部分中有详细介绍](../../delivery/using/sms-channel.md#creating-an-smpp-external-account) 。

### 更改投放模板 {#changing-the-delivery-template}

Adobe Campaign为您提供了用于传送到移动设备的模板。 此模板在节点中 **[!UICONTROL Resources > Templates > Delivery templates]** 可用。 有关此内容的详细信息，请参阅“关 [于模板](../../delivery/using/about-templates.md) ”部分。

要通过SMS渠道进行传送，您必须创建引用渠道连接器的模板。

为了保持本机投放模板，我们建议您重复它，然后对其进行配置。

在以下示例中，我们创建一个模板，通过先前启用的NetSize帐户传送消息。 操作步骤：

1. 转到节 **[!UICONTROL Delivery templates]** 点。
1. 右键单击模 **[!UICONTROL Send to mobiles]** 板，然后选择 **[!UICONTROL Duplicate]**。

   ![](assets/s_user_mobile_template_change_01.png)

1. 更改模板的标签。

   ![](assets/s_user_mobile_template_change_02.png)

1. 单击 **[!UICONTROL Properties]**.
1. 在选 **[!UICONTROL General]** 项卡中，选择与您配置的路由对应的外部帐户模式，例如 **[!UICONTROL NetSize mobile delivery]**。

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
1. 选择您之 **[!UICONTROL Send to mobiles (NetSize)]** 前创建的投放模板。 有关此内容的详细信息，请参 [阅更改投放模板](#changing-the-delivery-template) 。

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

1. 如果您使用NetSize连接器或SMPP连接器，则可以个性化投放发送者的姓名。 有关此内容的详细信息，请参 [阅高级参数](#advanced-parameters) 部分。

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

* **发件人地址** （仅适用于NetSize连接器和SMPP连接器）: 允许您使用限制为11个字符的字母数字字符串，个性化投放发件人的姓名。 这个领域不能只由数字组成。 您可以定义一个条件来显示，例如，根据收件人的区域代码显示不同的名称：

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >检查您所在国家／地区有关编辑发件人姓名的法律。 您还应询问操作员是否优惠此功能。

* **传输模式**: 短信发送
* **优先级**: 消息的重要性级别。 **[!UICONTROL Normal]** 优先级默认为选中。 询问您的服务提供商优先发送的短信费 **[!UICONTROL High]** 用。
* **应用程序类型**: 选择要分配给SMS投放的应用程序。 默认 **[!UICONTROL Direct Marketing]** 情况下，该选项处于选中状态，是最常用的选项。

**特定于NetSize连接器的参数**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **对单条消息使用多条SMS**: 这样，您就可以通过多个SMS消息发送超过160个字符的消息。

**SMPP连接器特有的参数**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **每条消息的最大短信数**: 通过此选项，可设置用于发送消息的SMS数。 如果数字设置为0，则可以使用SMS发送消息。 如果SMS的数量设置为1或2，并且消息超过此阈值，则不会发送该消息。

## 监控和跟踪SMS投放 {#monitoring-and-tracking-sms-deliveries}

发送消息后，您可以监视和跟踪投放。 有关此内容的详细信息，请参阅以下部分：

* [监控投放](../../delivery/using/monitoring-a-delivery.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [关于邮件跟踪](../../delivery/using/about-message-tracking.md)

## 处理入站消息 {#processing-inbound-messages}

nlserver **sms** 模块定期查询SMS路由器。 这允许Adobe Campaign跟踪投放进度并处理状态报告和收件人退订请求。

* **状态报告**: 视图投放日志检查消息的状态。

   >[!NOTE]
   >
   >发送的每条短信都链接到外部帐户的主密钥。 这样：
   >
   > * 未正确处理已删除外部SMS帐户的状态报告。
   > * SMS帐户只能链接到单个外部帐户，以确保状态报告归因到正确的帐户


* **退订**: 希望停止接收SMS投放的收件人可以返回包含STOP字样的消息。 如果您的提供商根据合同条款允许它访问，您可以通过 **Inbound SMS工作流活动检索消息** ，然后创建一个查询，为相关收件人启 **用“不再联系此收件人** ”选项。

   请参阅 [工作流](../../workflow/using/executing-a-workflow.md#architecture) 指南。

## InSMS模式 {#insms-schema}

InSMS模式包含与传入SMS相关的信息。 可通过desc属性描述这些字段。

* **消息**: 收到的短信内容。
* **来源**: 消息来源处的移动号码。
* **providerId**: SMSC（消息中心）返回的消息的标识符。
* **已创建**: 将传入消息插入Adobe Campaign。
* **extAccount**: Adobe Campaign外部帐户。

   >[!IMPORTANT]
   >
   >以下字段特定于NetSize。
   >
   >如果使用的运算符不是NetSize，则这些字段被视为空。

* **别名**: 传入消息的别名。
* **分隔符**: 别名和邮件正文之间的分隔符。
* **messageDate**: 运算符给出的消息日期。
* **receivalDate**: SMSC（消息中心）接收来自运营商的日期消息。
* **deliveryDate**: SMSC（消息中心）发送的日期消息。
* **largeAccount**: 客户帐户代码链接到传入的SMS。
* **countryCode**: 运营商国家代码。
* **operatorCode**: 运营商网络代码。
* **linkedSmsId**: Adobe Campaign标识符(broadlogId)，链接到传出SMS，其中此SMS是响应。

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
