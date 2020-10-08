---
title: LINE 渠道
seo-title: LINE 渠道
description: LINE 渠道
seo-description: null
page-status-flag: never-activated
uuid: 94b4e044-3f5d-42a6-b249-29f417386156
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
discoiquuid: 1d3cc650-3c79-4a1d-b2bc-e7eb6d59d2f1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 3%

---


# LINE 渠道{#line-channel}

LINE是免费即时消息、语音和视频呼叫的应用程序，可在所有智能手机(iPhone、Android、Windows Phone、Blackberry、Nokia)和PC上使用。 Adobe Campaign允许您发送LINE消息。

LINE仅可用于内部部署或托管服务安装。

LINE还可以与事务性消息模块结合，在安装在消费性移动设备上的LINE应用程序上发送实时消息。 有关详细信息，请参见此 [ 页面](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line)。

![](assets/line_message.png)

以下各节提供特定于LINE渠道的信息。 有关如何创建投放的全局信息，请参[阅此部分](../../delivery/using/steps-about-delivery-creation-steps.md)。

使用LINE渠道的步骤有：

1. 创建投放
1. 配置消息内容
1. 选择目标群
1. 发送消息
1. 监视投放（跟踪、隔离、报告等）。

## 设置LINE渠道 {#setting-up-line-channel}

### 创建LINE帐户和外部帐户 {#creating-a-line-account-and-an-external-account-}

>[!NOTE]
>
>在创建LINE帐户和外部帐户之前，您首先需要在实例上安装LINE包。 有关此信息，请参阅安 [装指南](../../installation/using/installing-campaign-standard-packages.md#line-package) 中的LINE部分。

您必须先创建LINE帐户，然后才能将其链接到Adobe Campaign。 然后，您可以向在移动应用程序中添加LINE帐户的用户发送LINE消息。 外部帐户和LINE帐户只能由平台的功能管理员管理。

要创建和配置LINE帐户，请参 [阅https://developers.line.me/](https://developers.line.me/)。

要创建和配置LINE服务，请参阅管 [理订阅](../../delivery/using/managing-subscriptions.md)。

![](assets/line_service.png)

最后，要创建Adobe Campaign外部帐户:

1. 在“管 **理** ”>“ **平台** ”树结构中，单 **击“外部帐户** ”选项卡。
1. 然后单击“ **新建** ”图标。

   ![](assets/line_config.png)

1. 填写“标 **签** ”和 **“内部名称** ”字段。
1. 在字 **[!UICONTROL Type]** 段中，选择路由，在 **渠道** 字段中选择LINE。
1. 单 **[!UICONTROL Save]** 击以创建LINE外部帐户。
1. LINE个 **性化** 字段随后会显示在“常规” **图标** 下方，并填写以下字段：

   ![](assets/line_config_2.png)

   * **渠道别名**:是通过您的LINE帐户在>标签中 **[!UICONTROL Channels]** 提 **[!UICONTROL Technical configuration]** 供的。
   * **渠道ID**:是通过“渠道”>“基本信息”面 **板选项卡** 中的 **LINE帐户提供的** 。
   * **渠道密钥**:是通过“渠道”>“基本信息”面 **板选项卡** 中的 **LINE帐户提供的** 。
   * **访问令牌**:通过开发人员门户中的LINE帐户或单击按钮提 **[!UICONTROL Get access token]** 供。
   * **访问令牌到期日**:允许您指定访问令牌的到期日期。
   * **行订阅服务**:允许您指定用户将订阅的服务。

>[!NOTE]
>
>您必须验证是 **[!UICONTROL LINE access token update (updateLineAccessToken)]** 否已 **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** 启动和工作流。 在资源管理器中，单 **[!UICONTROL Administration > Production > Technical workflows > LINE workflows]** 击以检查工作流的状态。

## 创建投放 {#creating-the-delivery}

要创建 **LINE** 投放，您必须执行以下步骤：

>[!NOTE]
>
>本节介绍有关投放创建的全 [局概念](../../delivery/using/steps-about-delivery-creation-steps.md)。

1. 在选项卡 **[!UICONTROL Campaigns]** 中，选择 **[!UICONTROL Deliveries]** ，然后单击 **[!UICONTROL Create]** 按钮。
1. 在出现的窗口中，选择 **[!UICONTROL LINE V2 delivery]** 投放模板。

   ![](assets/line_message_01.png)

1. 用标签、代码和说明来识别投放。 如需详细信息，请参阅[此部分](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)。
1. 单击 **[!UICONTROL Continue]** 以创建投放。

## 定义内容 {#defining-the-content}

要定义LINE投放的内容，您首先必须向投放添加消息类型。 每个LINE投放最多可包含5条消息。

您可以选择以下两种消息类型：

* 文本消息
* 图像和链接

### 配置文本消息投放 {#configuring-a-text-message-delivery}

文本 **消息** LINE投放是以文本形式发送给收件人的消息。

![](assets/line_message_02.png)

此类型邮件的配置与电子邮件中文本 **的配** 置类似。 For more information, refer to this [page](../../delivery/using/defining-the-email-content.md#message-content).

### 配置图像和链接投放 {#configuring-an-image-and-link-delivery}

图 **像和链接** LINE投放是以图像形式发送给收件人的消息，该图像可能包含一个或多个URL。

您可以使用：

* 个 **性化图像**,

   >[!NOTE]
   >
   >您可以使用 **%SIZE%** 变量：此变量允许您根据收件人移动设备的屏幕大小优化图像显示。

   ![](assets/line_message_04.png)

* 图 **像URL**,

   ![](assets/line_message_03.png)

   图像URL允许您使用不同的图像分辨率来优化移动设备上的投放可见性。 仅支持高度和宽度相同的图像。

   可以根据屏幕大小定义图像：

   * 1040px
   * 700px
   * 460px
   * 300px
   * 240px

   >[!NOTE]
   >
   >对于每幅带链接的LINE图像，大小为1040x1040像素是必填的。

   然后，您必须添加将在收件人的移动设备上弹出的替换文本。

* 和 **[!UICONTROL Links]**。

   ![](assets/line_message_05.png)

   该 **[!UICONTROL Links]** 部分允许您选择将图像分成多个可单击区域的不同布局。 然后，您可以为每个客户分配一个专用链接。

>[!NOTE]
>
>&lt;%@ include option=&#39;NmsServer_URL&#39; %>/webApp/APP3?id=&lt;%=escapeUrl(cryptString(访客.id))%>语法允许您在LINE消息中包含指向Web应用程序的链接。

### 建议{#recommendations}

* 首次向新投放发送LINE收件人时，必须在投放中添加有关使用条款和同意的正式LINE消息。 官方信息可通过以下链接获取： [https://terms.line.me/OA_privacy/](https://terms.line.me/OA_privacy/sp?lang=fr)。

## 选择目标群 {#selecting-the-target-population}

选择LINE收件人的投放与定义电子邮件投放收件人类似。 有关详细信息，请参阅 [确定目标群](../../delivery/using/steps-defining-the-target-population.md)。

目标定位对 **访客**。

## 发送消息 {#sending-messages}

正确创建和配置投放后，您可以将其发送到之前定义的目标。

发送LINE投放与发送电子邮件投放相似。 有关发送投放的详细信息，请参阅 [发送消息](../../delivery/using/sending-messages.md)。

## 访问报告 {#accessing-reports}

可以通过在资源管理器中单击来视图LINE **[!UICONTROL Profiles and Targets > Services and Subscriptions > LINE]** 服务上的报告。 然后单击 **[!UICONTROL Reports]** LINE服务中的图标。

![](assets/line_reports.png)

要视图LINE投放上的报表，请单 **[!UICONTROL Campaign Management > Deliveries]** 击，然后选择所需的投放。 跟踪报告指示点进率。 LINE未考虑开放率。

![](assets/line_reports_01.png)

## 示例：创建和发送个性化的LINE消息 {#example--create-and-send-a-personalized-line-message}

在此示例中，我们将创建和配置文本消息和包含数据的图像，这些数据将根据收件人进行个性化。

1. 通过单击选项卡中的按 **[!UICONTROL Create]** 钮创建您的LINE **[!UICONTROL Campaign]** 投放。

   ![](assets/line_usecase.png)

1. 选择投放模板 **[!UICONTROL LINE V2 delivery]** 并命名您的投放。

   ![](assets/line_usecase_01.png)

1. 在投放的配置窗口中，选择目标人口。

   ![](assets/line_usecase_02.png)

1. 单击 **[!UICONTROL Add]** 以创建消息并选择 **[!UICONTROL Message type]**。

   此处，我们首先要创建文本消息。

   ![](assets/line_usecase_03.png)

1. 将光标放在要插入个性化文本的位置，单击下拉图标，然后选择 **[!UICONTROL Visitor > First name]**。

   ![](assets/line_usecase_05.png)

1. 按照相同的过程添加图像， **[!UICONTROL Image and links]** 从下 **[!UICONTROL Message type]** 拉菜单中选择。

   添加图像URL。

   ![](assets/line_usecase_07.png)

1. 在部分 **[!UICONTROL Links]** 中，选择将图像分成多个可单击区域的布局。
1. 为图像的每个区域分配一个URL。

   ![](assets/line_usecase_08.png)

1. 保存投放，然 **[!UICONTROL Send]** 后单击以分析并发送给目标。

   投放被发送给目标。

   ![](assets/line_usecase_06.png)
