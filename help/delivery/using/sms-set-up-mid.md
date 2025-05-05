---
product: campaign
title: 在中间源基础设施上配置Campaign SMS渠道
description: 了解如何在中端来源基础设施上配置Campaign中的SMS渠道
feature: SMS
role: User, Developer, Admin
level: Experienced
exl-id: 6987cb5e-8821-4619-b0e4-f0fad3355bfb
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 8%

---

# 在中端源基础设施上配置SMS渠道 {#setting-up-sms-channel}

要发送到带有中间服务器的手机，您需要：

1. 在中间服务器上创建的SMS操作员，用于在Marketing服务器上创建的SMS外部帐户。

1. 市场营销服务器上的外部帐户，指定“渠道”和“交付”模式。

1. Mid服务器上的外部帐户，详述连接器和消息类型。

1. 引用外部帐户以简化发送流程的交付模板。

>[!NOTE]
>
> 对于SMS传递，类型应使用在&#x200B;**one**&#x200B;专用应用程序服务器容器中创建的特定SMS关联。 [了解详情](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

## 在中端服务器上创建SMS操作员 {#create-sms-operator}

要开始配置过程，必须在中间服务器上专门为外部帐户创建短信运算符。

>[!IMPORTANT]
>
>每个短信连接器都需要一个唯一的短信操作员。

1. 在树的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Access management]** > **[!UICONTROL Operators node]**&#x200B;节点中，单击&#x200B;**[!UICONTROL New]**&#x200B;图标。

   ![](assets/sms_operator_mid_3.png)

1. 指定用户的&#x200B;**[!UICONTROL Identification parameters]**，包括其登录名、密码和名称。 操作员需要登录名和密码才能安全登录到Adobe Campaign。

   请注意，稍后将使用&#x200B;**[!UICONTROL Name (login)]**&#x200B;在中间服务器中命名您的SMPP外部帐户。

   ![](assets/sms_operator_mid_1.png)

1. 在“操作员访问权限”部分中选择授予操作员的权限。

   要向操作员分配权限，请单击权限列表上方的&#x200B;**[!UICONTROL Add]**&#x200B;按钮。 接下来，从可用组列表中选择&#x200B;**[!UICONTROL Operator group]**&#x200B;或&#x200B;**[!UICONTROL Named rights]**。

   ![](assets/sms_operator_mid_2.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;完成运算符的创建。 配置文件现在包含在现有运算符的列表中。

## 在营销服务器上创建短信外部帐户 {#create-accound-mkt}

要将SMS发送到带有Mid服务器的手机，您首先需要在营销服务器上创建SMS外部帐户。

1. 在树的&#x200B;**[!UICONTROL Platform]** > **[!UICONTROL External accounts]**&#x200B;节点中，单击&#x200B;**[!UICONTROL New]**&#x200B;图标。

   ![](assets/mid_external_account_2.png)

1. 键入&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]**。 请注意，稍后将使用“内部”名称在Mid服务器中命名您的SMPP外部帐户。

1. 将帐户类型定义为&#x200B;**[!UICONTROL Routing]**，渠道定义为&#x200B;**[!UICONTROL Mobile (SMS)]**，投放模式定义为&#x200B;**[!UICONTROL Mid-sourcing]**。

   ![](assets/mid_external_account_1.png)

1. 在&#x200B;**[!UICONTROL Mid-Sourcing]**&#x200B;选项卡中，指定中间源服务器连接参数。

   在&#x200B;**[!UICONTROL Account]**&#x200B;和&#x200B;**[!UICONTROL Password]**&#x200B;字段中输入[以前创建的SMS连接器](#create-sms-operator)的详细信息。

   ![](assets/mid_external_account_7.png)

1. 单击“**[!UICONTROL Test the connection]**”以确认配置。

1. 单击 **[!UICONTROL Save]**。

## 在Mid服务器上创建SMPP外部帐户 {#creating-smpp-mid}

>[!IMPORTANT]
>
>对多个外部SMS帐户使用相同的帐户和密码可能会导致帐户之间的冲突和重叠。 请参阅[SMS疑难解答页面](troubleshooting-sms.md#external-account-conflict)。

在营销服务器上成功设置短信外部帐户后，下一步是在中间服务器上建立SMPP外部帐户。

有关短信协议和设置的详细信息，请参阅此[页面](sms-protocol.md)。

为此请执行以下操作步骤：

1. 在树的&#x200B;**[!UICONTROL Platform]** > **[!UICONTROL External accounts]**&#x200B;节点中，单击&#x200B;**[!UICONTROL New]**&#x200B;图标。

1. 键入您的&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]**。

   >[!WARNING]
   >
   >分配&#x200B;**[!UICONTROL Internal name]**&#x200B;时，请确保遵循指定的命名约定：
   > </br>`SMS Operator Name_Internal Name of the Marketing SMS external account`

   ![](assets/mid_external_account_6.png)

1. 将帐户类型定义为&#x200B;**路由**，渠道定义为&#x200B;**移动设备(SMS)**，投放模式定义为&#x200B;**批量投放**。

   ![](assets/mid_external_account_3.png)

1. 选中&#x200B;**[!UICONTROL Enabled]**&#x200B;框。

1. 在&#x200B;**[!UICONTROL Mobile]**&#x200B;选项卡中，从&#x200B;**[!UICONTROL Connector]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Extended generic SMPP]**。

   ![](assets/mid_external_account_4.png)

1. 使用&#x200B;**[!UICONTROL Enable verbose SMPP traces in the log file]**&#x200B;选项可将所有SMPP通信转储到日志文件中。 仅应启用此选项对连接器进行故障排除，并与提供商的通信记录进行比较。

1. 请与您的SMS服务提供商联系，提供商将向您说明如何填写&#x200B;**[!UICONTROL Connection settings]**&#x200B;选项卡中的不同外部帐户字段。

   然后，根据所选提供商，联系您的提供商，他们将为您提供在&#x200B;**[!UICONTROL SMSC implementation name]**&#x200B;字段中输入的值。

   您可以定义每个MTA子级与提供程序的连接数。 默认情况下，设置为1。

1. 默认情况下，短信的字符数应符合GSM标准。

   使用 GSM 编码的短信消息长度上限为 160 个字符，而对于分段发送的消息，每段短信的长度上限为 153 个字符。

   >[!NOTE]
   >
   >某些字符会被计为两个字符（大括号、方括号、欧元符号等）。
   >
   >可用GSM字符的列表显示在[此部分](sms-set-up.md#about-character-transliteration)中。

   您还可以通过勾选对应的方框来授权字符音译。

   ![](assets/mid_external_account_5.png)

1. 在&#x200B;**[!UICONTROL Throughput and delays]**&#x200B;选项卡中，您可以指定出站消息(“MT”，Mobile Terminated)的最大吞吐量，以每秒MT为单位。 如果在对应的字段中输入“0”，则吞吐量将没有限制。

   对应于持续时间的所有字段值，都必须填写以秒为单位的值。

1. 在&#x200B;**[!UICONTROL Mapping of encodings]**&#x200B;选项卡中，您可以定义编码。

   如需详细信息，请参阅[此小节](sms-set-up.md#about-text-encodings)。

1. 在&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;选项卡中，**[!UICONTROL Send full phone number]**&#x200B;选项默认处于禁用状态。 如果要遵守SMPP协议，并且只向SMS提供商(SMSC)的服务器传输数字，请勿启用此项。

   但是，鉴于某些提供商需要使用“+”前缀，建议您与提供商进行核实，他们将会提供是否有必要启用此选项的建议。

   **[!UICONTROL Enable TLS over SMPP]**&#x200B;复选框允许您加密SMPP通信。 有关详细信息，请参见此 [ 页面](sms-protocol.md)。

1. 如果您正在配置&#x200B;**[!UICONTROL Extended generic SMPP]**&#x200B;连接器，则可以设置自动回复。

   如需详细信息，请参阅[此小节](sms-set-up.md#automatic-reply)。

## 更改交付模板 {#changing-the-delivery-template}

Adobe Campaign提供了一个位于&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;节点中的移动投放模板。 有关此方面的更多信息，请参阅[关于模板](about-templates.md)部分。

要通过短信渠道发送消息，您必须创建包含渠道连接器引用的模板。

要保留本机交付模板，我们建议您复制它，然后对其进行配置。

在下面的示例中，我们生成了一个模板以方便通过之前创建的SMPP帐户传送报文。 操作步骤：

1. 在树的&#x200B;**[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**&#x200B;节点中，右键单击&#x200B;**[!UICONTROL Send to mobiles]**&#x200B;模板，然后选择&#x200B;**[!UICONTROL Duplicate]**。

   ![](assets/delivery_template_mid_1.png)

1. 更改模板的标签，例如&#x200B;**发送到移动设备(SMPP)**。

   ![](assets/delivery_template_mid_2.png)

1. 单击 **[!UICONTROL Properties]**。

1. 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，选择与您在[在营销服务器上创建SMS外部帐户](#create-accound-mkt)部分创建的外部帐户对应的路由模式。

   ![](assets/delivery_template_mid_3.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建模板。

   ![](assets/delivery_template_mid_4.png)

现在，您有一个外部帐户和一个投放模板，可让您通过短信投放。

## 相关主题 {#related-topics}

* [短信字符音译](sms-set-up.md#about-character-transliteration)
* [文本编码](sms-set-up.md#about-text-encodings)
* [自动回复](sms-set-up.md#automatic-reply)
