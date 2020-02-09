---
title: 线路通道
seo-title: 线路通道
description: 线路通道
seo-description: null
page-status-flag: never-activated
uuid: 94b4e044-3f5d-42a6-b249-29f417386156
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
discoiquuid: 1d3cc650-3c79-4a1d-b2bc-e7eb6d59d2f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# 线路通道{#line-channel}

LINE是一个用于免费即时消息、语音和视频呼叫的应用程序，可在所有智能手机(iPhone、Android、Windows Phone、Blackberry、Nokia)和PC上使用。 Adobe Campaign允许您发送LINE消息。

LINE仅适用于内部部署或托管服务安装。

LINE还可以与事务消息模块结合，以在安装在消费性移动设备上的LINE应用程序上发送实时消息。 For more on this, refer to this [page](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line).

![](assets/line_message.png)

以下各节提供特定于LINE渠道的信息。 有关如何创建交付的全局信息，请参阅[此部分](../../delivery/using/steps-about-delivery-creation-steps.md)。

使用LINE渠道的步骤有：

1. 创建分发
1. 配置消息内容
1. 选择目标人群
1. 发送消息
1. 监视传送（跟踪、隔离、报告等）。

## 设置LINE渠道 {#setting-up-line-channel}

### 创建LINE帐户和外部帐户 {#creating-a-line-account-and-an-external-account-}

>[!NOTE]
>
>在创建LINE帐户和外部帐户之前，您首先需要在实例上安装LINE包。 有关此信息，请参阅安 [装指南中](../../installation/using/installing-campaign-standard-packages.md#line-package) 的“LINE”部分。

您必须先创建LINE帐户，然后才能将其关联到Adobe Campaign。 然后，您可以向在其移动应用程序中添加LINE帐户的用户发送LINE消息。 外部帐户和LINE帐户只能由平台的功能管理员管理。

要创建和配置LINE帐户，请参 [阅https://developers.line.me/](https://developers.line.me/)。

要创建和配置LINE服务，请参阅管 [理订阅](../../delivery/using/managing-subscriptions.md)。

![](assets/line_service.png)

最后，要在Adobe Campaign上创建外部帐户：

1. 在“管 **理** ”>“平台 **”树结构中，单击“** 外部帐户 **** ”选项卡。
1. 然后单击“ **新建** ”图标。

   ![](assets/line_config.png)

1. 填写“标 **签** ”和“ **内部名称** ”字段。
1. 在字段 **[!UICONTROL Type]** 中，选择工艺路线，在渠道字 **段中** ，选择行。
1. 单击 **[!UICONTROL Save]** 以创建您的LINE外部帐户。
1. 然后 **,LINE** **personalization字段会显示在“常规”图** 标下方，填写以下字段：

   ![](assets/line_config_2.png)

   * **渠道别名**:是通过您的LINE帐户在 **[!UICONTROL Channels]** >标签中提 **[!UICONTROL Technical configuration]** 供的。
   * **渠道ID**:是通过“渠道”>“基本信息”面板选项 **卡中的** LINE **帐户提供的** 。
   * **通道密钥**:是通过“渠道”>“基本信息”面板选项 **卡中的** LINE **帐户提供的** 。
   * **访问令牌**:是通过开发人员门户中的LINE帐户或通过单击按钮提供的 **[!UICONTROL Get access token]** 。
   * **访问令牌到期日期**:允许您指定访问令牌的过期日期。
   * **LINE订阅服务**:允许您指定用户将订阅的服务。

>[!NOTE]
>
>您必须确认已开 **[!UICONTROL LINE access token update (updateLineAccessToken)]** 始和 **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** 工作流。 在资源管理器中，单 **[!UICONTROL Administration > Production > Technical workflows > LINE workflows]** 击以检查工作流的状态。

## 创建交付 {#creating-the-delivery}

要创建 **LINE交货** ，您必须执行以下步骤：

>[!NOTE]
>
>本节介绍有关交付创建的全 [局概念](../../delivery/using/steps-about-delivery-creation-steps.md)。

1. 在选项卡 **[!UICONTROL Campaigns]** 中，选择 **[!UICONTROL Deliveries]** 然后单击 **[!UICONTROL Create]** 按钮。
1. 在显示的窗口中，选择交 **[!UICONTROL LINE V2 delivery]** 付模板。

   ![](assets/line_message_01.png)

1. 用标签、代码和说明标识您的交付。 如需详细信息，请参阅[此部分](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)。
1. 单击 **[!UICONTROL Continue]** 以创建您的分发。

## 定义内容 {#defining-the-content}

要定义LINE交付的内容，您首先必须将消息类型添加到交付中。 每个LINE交付最多可包含5条消息。

您可以在两种消息类型之间进行选择：

* 文本消息
* 图像和链接

### 配置文本消息传送 {#configuring-a-text-message-delivery}

文本 **消息** LINE传送是以文本形式发送给收件人的消息。

![](assets/line_message_02.png)

此类型消息的配置与电子邮件中文本的 **配置** 类似。 For more information, refer to this [page](../../delivery/using/defining-the-email-content.md#message-content).

### 配置图像和链接交付 {#configuring-an-image-and-link-delivery}

图 **像和链接** LINE交付是以图像形式发送给收件人的消息，该图像可能包含一个或多个URL。

您可以使用：

* 个性化 **的图像**,

   >[!NOTE]
   >
   >可以使用 **%SIZE%** 变量：此变量允许您根据收件人移动设备的屏幕大小优化图像显示。

   ![](assets/line_message_04.png)

* 图 **像URL**,

   ![](assets/line_message_03.png)

   图像URL允许您使用不同的图像分辨率来优化移动设备上的交付可见性。 仅支持高度和宽度相同的图像。

   可以根据屏幕大小定义图像：

   * 1040px
   * 700px
   * 460px
   * 300px
   * 240px
   >[!NOTE]
   >
   >对于每幅带链接的LINE图像，大小必须为1040x1040像素。

   然后，您必须添加将在收件人的移动设备上弹出的替换文本。

* 和 **[!UICONTROL Links]**。

   ![](assets/line_message_05.png)

   该部 **[!UICONTROL Links]** 分允许您在不同的布局之间进行选择，这些布局会将图像分成多个可单击区域。 然后，您可以为每个用户分配一个专用链接。

>[!NOTE]
>
>&lt;%@ include option=&#39;NmsServer_URL&#39; %>/webApp/APP3?id=&lt;%=escapeUrl(cryptString(visitor.id))%>语法允许您在LINE消息中包含指向Web应用程序的链接。

### 建议 {#recommendations}

* 首次向新收件人发送LINE交付时，您必须在交付中添加有关使用条款和同意的正式LINE消息。 正式信息可通过以下链接获得： [https://terms.line.me/OA_privacy/](https://terms.line.me/OA_privacy/sp?lang=fr)。

## 选择目标人群 {#selecting-the-target-population}

选择LINE传送的收件人与定义电子邮件传送收件人类似。 有关详细信息，请参阅 [识别目标人群](../../delivery/using/steps-defining-the-target-population.md)。

对访客进行定 **位**。

## 发送消息 {#sending-messages}

在正确创建和配置交付后，您可以将其发送到先前定义的目标。

发送LINE分发与发送电子邮件分发类似。 有关发送传送的详细信息，请参阅发 [送消息](../../delivery/using/sending-messages.md)。

## 访问报告 {#accessing-reports}

可以通过在资源管理器中单击来查看LINE服 **[!UICONTROL Profiles and Targets > Services and Subscriptions > LINE]** 务上的报告。 然后，单击 **[!UICONTROL Reports]** LINE服务中的图标。

![](assets/line_reports.png)

要查看LINE交货的报表，请单 **[!UICONTROL Campaign Management > Deliveries]** 击，然后选择所需的交货。 跟踪报告指示点进率。 LINE未考虑开放率。

![](assets/line_reports_01.png)

## 示例：创建和发送个性化的LINE消息 {#example--create-and-send-a-personalized-line-message}

在此示例中，我们将创建并配置文本消息和包含将根据收件人个性化的数据的图像。

1. 通过单击标签中的按钮，创 **[!UICONTROL Create]** 建您的LINE交 **[!UICONTROL Campaign]** 货。

   ![](assets/line_usecase.png)

1. 选择交 **[!UICONTROL LINE V2 delivery]** 付模板并命名您的交付。

   ![](assets/line_usecase_01.png)

1. 在交付的配置窗口中，选择目标人群。

   ![](assets/line_usecase_02.png)

1. 单击 **[!UICONTROL Add]** 以创建消息，然后选择 **[!UICONTROL Message type]**。

   在此，我们首先要创建文本消息。

   ![](assets/line_usecase_03.png)

1. 将光标放在要插入个性化文本的位置，单击下拉图标，然后选择 **[!UICONTROL Visitor > First name]**。

   ![](assets/line_usecase_05.png)

1. 按照相同的过程添加图像，从 **[!UICONTROL Image and links]** 下拉框 **[!UICONTROL Message type]** 中选择。

   添加图像URL。

   ![](assets/line_usecase_07.png)

1. 在部分 **[!UICONTROL Links]** 中，选择将图像分割为多个可单击区域的布局。
1. 为图像的每个区域分配一个URL。

   ![](assets/line_usecase_08.png)

1. 保存您的交付，然 **[!UICONTROL Send]** 后单击以分析并将其发送到目标。

   将发送到目标。

   ![](assets/line_usecase_06.png)
