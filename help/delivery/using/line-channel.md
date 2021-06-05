---
product: campaign
title: LINE 渠道
description: LINE 渠道
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: 1baaabbd-9fd7-4d9b-b78e-d2a559d7dddb
source-git-commit: 4a41aea9edfe5e6ca0454049cbb2892449eec153
workflow-type: tm+mt
source-wordcount: '1162'
ht-degree: 2%

---

# 创建LINE投放{#line-channel}

>[!NOTE]
>
>[!DNL LINE] 仅可用于内部部署或托管服务安装。

[!DNL LINE] 是免费即时消息、语音和视频呼叫的应用程序，适用于每个移动操作系统和PC上。

[!DNL LINE] 还可以与事务型消息模块结合使用，在消费者移动设备中安装的 [!DNL LINE] 应用程序上发送实时消息。有关详细信息，请参见此 [ 页面](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line)。

![](assets/line_message.png)

使用[!DNL LINE]通道的步骤如下：

1. [设置LINE渠道](#setting-up-line-channel)
1. [创建投放](#creating-the-delivery)
1. [配置内容类型](#defining-the-content)
1. [监控投放（跟踪、隔离、报告等）](#accessing-reports)

## 设置LINE通道{#setting-up-line-channel}

在创建[!DNL LINE]帐户和外部帐户之前，您首先需要在实例上安装LINE包。 有关此内容的详细信息，请参阅《安装指南》中的[LINE](../../installation/using/installing-campaign-standard-packages.md#line-package)部分。

您必须先创建一个[!DNL LINE]帐户，然后才能将其链接到Adobe Campaign。 然后，您可以向在移动应用程序中添加了[!DNL LINE]帐户的用户发送[!DNL LINE]消息。 外部帐户和[!DNL LINE]帐户只能由平台的功能管理员管理。

要创建和配置[!DNL LINE]帐户，请参阅[LINE开发人员文档](https://developers.line.me/)。

### 创建和配置LINE服务{#configure-line-service}

要创建[!DNL LINE]服务，请执行以下操作：

1. 从Adobe Campaign Classic主页中，选择&#x200B;**[!UICONTROL Profiles and Targets]**&#x200B;选项卡。

1. 在左侧菜单中，选择&#x200B;**[!UICONTROL Services and Subscriptions]**&#x200B;并单击&#x200B;**[!UICONTROL Create]**。

   ![](assets/line_service_1.png)

1. 向新服务中添加&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]**。

1. 从&#x200B;**[!UICONTROL Type]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL LINE]**。

   ![](assets/line_service_2.png)

1. 单击 **[!UICONTROL Save]**。

有关订阅和服务的更多信息，请参阅[管理订阅](../../delivery/using/managing-subscriptions.md)。

### 配置LINE外部帐户{#configure-line-external}

创建[!DNL LINE]服务后，您需要在Adobe Campaign上配置[!DNL LINE]外部帐户：

1. 在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]**&#x200B;树结构中，单击&#x200B;**[!UICONTROL External Accounts]**&#x200B;选项卡。

1. 选择内置&#x200B;**[!UICONTROL LINE V2 routing]**&#x200B;外部帐户。

   ![](assets/line_config.png)

1. 单击外部帐户中的&#x200B;**[!UICONTROL LINE]**&#x200B;选项卡以开始配置外部帐户。 填写以下字段：

   ![](assets/line_config_2.png)

   * **[!UICONTROL Channel Alias]**:通过您的帐户在 [!DNL LINE] >选项卡 **[!UICONTROL Channels]** 中提 **[!UICONTROL Technical configuration]** 供。
   * **[!UICONTROL Channel ID]**:通过您的帐户在 [!DNL LINE] >选项卡 **[!UICONTROL Channels]** 中提 **[!UICONTROL Basic Information panel]** 供。
   * **[!UICONTROL Channel secret key]**:通过您的帐户在 [!DNL LINE] >选项卡 **[!UICONTROL Channels]** 中提 **[!UICONTROL Basic Information panel]** 供。
   * **[!UICONTROL Access token]**:可通过您的帐 [!DNL LINE] 户（位于开发人员门户）或单击按 **[!UICONTROL Get access token]** 钮来提供。
   * **[!UICONTROL Access token expiration date]**:允许您指定访问令牌的过期日期。
   * **[!UICONTROL LINE subscription service]**:用于指定用户将订阅的服务。

1. 完成配置后，单击 **[!UICONTROL Save]**。

1. 从&#x200B;**[!UICONTROL Explorer]**&#x200B;中，选择&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL LINE workflows]**&#x200B;以检查&#x200B;**[!UICONTROL LINE V2 access token update (updateLineAccessToken)]**&#x200B;和&#x200B;**[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]**&#x200B;工作流是否已启动。

[!DNL LINE]现在在Adobe Campaign中配置，您可以开始创建LINE投放并将其发送给订阅者。

## 创建LINE投放{#creating-the-delivery}

>[!NOTE]
>
>首次向新收件人发送[!DNL LINE]投放时，必须向投放添加有关使用条款和同意条款的官方LINE消息。 该正式消息位于[以下链接](https://terms.line.me/OA_privacy/)。

要创建[!DNL LINE]投放，您必须执行以下步骤：

1. 在&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Deliveries]** ，然后单击&#x200B;**[!UICONTROL Create]**&#x200B;按钮。

   ![](assets/line_message_07.png)

1. 选择&#x200B;**[!UICONTROL LINE V2 delivery]**&#x200B;投放模板。

   ![](assets/line_message_01.png)

1. 使用&#x200B;**[!UICONTROL Label]**、**[!UICONTROL Delivery code]**&#x200B;和&#x200B;**[!UICONTROL Description]**&#x200B;标识投放。 如需详细信息，请参阅[此部分](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)。

1. 单击&#x200B;**[!UICONTROL Continue]**&#x200B;以创建投放。

1. 在投放编辑器中，选择&#x200B;**[!UICONTROL To]**&#x200B;以定位[!DNL LINE]投放的收件人。 对&#x200B;**[!UICONTROL Visitor subscriptions (nms:visitorSub)]**&#x200B;进行定位。

   有关更多信息，请参阅[识别目标群体](../../delivery/using/steps-defining-the-target-population.md)。

   ![](assets/line_message_08.png)

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;选择&#x200B;**[!UICONTROL Delivery target population]**。

   ![](assets/line_message_09.png)

1. 选择是要直接定位[!DNL LINE]订阅者，还是要根据用户的[!DNL LINE]订阅来定位用户，然后单击&#x200B;**[!UICONTROL Next]**。 在本例中，我们选择了&#x200B;**[!UICONTROL By LINE V2 subscription]**。

1. 在&#x200B;**[!UICONTROL Folder]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Line-V2]** ，然后选择[!DNL LINE]服务。 单击&#x200B;**[!UICONTROL Finish]**，然后单击&#x200B;**[!UICONTROL Ok]**&#x200B;以开始个性化投放。

   ![](assets/line_message_10.png)

1. 在投放编辑器中，单击&#x200B;**[!UICONTROL Add]**&#x200B;以添加一条或多条消息，然后选择&#x200B;**[!UICONTROL Content type]**。

   有关可用的不同&#x200B;**[!UICONTROL Content type]**&#x200B;的更多信息，请参阅[定义内容类型](#defining-the-content)。

   ![](assets/line_message_11.png)

1. 正确创建和配置投放后，您可以将其发送到之前定义的目标。

   有关发送投放的更多信息，请参阅[发送消息](../../delivery/using/sending-messages.md)。

1. 发送消息后，访问报表以衡量投放的有效性。

   有关[!DNL LINE]报表的更多信息，请参阅[访问报表](#accessing-reports)。

## 定义内容类型{#defining-the-content}

要定义[!DNL LINE]投放的内容，您首先必须向投放添加消息类型。 每个[!DNL LINE]投放最多可包含5条消息。

您可以选择以下三种消息类型：

* [文本消息](#configuring-a-text-message-delivery)
* [图像和链接](#configuring-an-image-and-link-delivery)
* [视频消息](#configuring-a-video-message-delivery)

### 配置文本消息投放{#configuring-a-text-message-delivery}

>[!NOTE]
>
>`<%@ include option='NmsServer_URL' %>/webApp/APP3?id=<%=escapeUrl(cryptString(visitor.id))%>`语法允许您在LINE消息中包含指向Web应用程序的链接。

**[!UICONTROL Text message]** [!DNL LINE]投放是以文本形式发送给收件人的消息。

![](assets/line_message_02.png)

此类型消息的配置与电子邮件中&#x200B;**[!UICONTROL Text]**&#x200B;的配置类似。 有关详细信息，请参见此[页面](../../delivery/using/defining-the-email-content.md#message-content)。

### 配置图像和链接投放{#configuring-an-image-and-link-delivery}

**[!UICONTROL Image and link]** [!DNL LINE]投放是以包含一个或多个URL的图像形式发送给收件人的消息。

您可以使用：

* a **[!UICONTROL Personalized image]**,

   >[!NOTE]
   >
   >您可以使用&#x200B;**%SIZE%**&#x200B;变量根据收件人移动设备的屏幕大小优化图像显示。

   ![](assets/line_message_04.png)

* 每个设备屏幕大小&#x200B;**[!UICONTROL Image URL]**,

   ![](assets/line_message_03.png)

   **[!UICONTROL Define images per device screen size]**&#x200B;选项允许您使用不同的图像分辨率来优化移动设备上的投放可见性。 仅支持高度和宽度相同的图像。

   可根据屏幕大小定义图像：

   * 1040像素
   * 700px
   * 460px
   * 300px
   * 240px

   >[!CAUTION]
   >
   >对于具有链接的每个LINE图像，大小必须为1040x1040像素。

   然后，您必须添加将在收件人移动设备上弹出的替换文本。

* 和&#x200B;**[!UICONTROL Links]**。

   **[!UICONTROL Links]**&#x200B;部分允许您在不同的布局之间进行选择，这些布局会将图像划分到多个可单击区域。 然后，您可以为每个用户分配一个专用的&#x200B;**[!UICONTROL Link URL]**。

   ![](assets/line_message_05.png)

### 配置视频消息投放{#configuring-a-video-message-delivery}

**[!UICONTROL Video message]** [!DNL LINE]投放是以包含URL的视频形式发送给收件人的消息。

利用&#x200B;**[!UICONTROL Preview Image URL]**&#x200B;字段，可添加预览图像的URL，字符限制为1000。 文件大小限制为1 MB，支持JPEG和PNG。

利用&#x200B;**[!UICONTROL Video Image URL]**&#x200B;字段，可添加视频文件的URL，字符限制为1000。 仅支持mp4格式，文件大小限制为200 MB。

请注意，在某些设备上播放宽视频或高视频时，可能会被裁剪。

![](assets/line_message_06.png)

## 访问报告{#accessing-reports}

发送投放后，您可以通过&#x200B;**[!UICONTROL Explorer]**&#x200B;中的&#x200B;**[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]**&#x200B;菜单查看[!DNL LINE]报表。

>[!NOTE]
>
>跟踪报表指示点进率。 [!DNL LINE] 不考虑开放率。

![](assets/line_reports_01.png)

对于[!DNL LINE]服务报表，从&#x200B;**[!UICONTROL Explorer]**&#x200B;选项卡中访问菜单&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Services and Subscriptions]** > **[!UICONTROL LINE-V2]**。 然后，单击[!DNL LINE]服务中的&#x200B;**[!UICONTROL Reports]**&#x200B;图标。

![](assets/line_reports.png)

## 示例：创建并发送个性化的LINE消息{#example--create-and-send-a-personalized-line-message}

在此示例中，我们将创建并配置文本消息和包含将根据收件人进行个性化数据的图像。

1. 单击&#x200B;**[!UICONTROL Campaign]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Create]**&#x200B;按钮以创建[!DNL LINE]投放。

   ![](assets/line_usecase.png)

1. 选择&#x200B;**[!UICONTROL LINE V2 delivery]**&#x200B;投放模板并命名您的投放。

   ![](assets/line_usecase_01.png)

1. 在投放的配置窗口中，选择目标群体。

   有关更多信息，请参阅[识别目标群体](../../delivery/using/steps-defining-the-target-population.md)。

   ![](assets/line_usecase_02.png)

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;以创建消息，然后选择&#x200B;**[!UICONTROL Content type]**。

   在此，我们首先要创建&#x200B;**[!UICONTROL Text message]**。

   ![](assets/line_usecase_03.png)

1. 将光标放在要插入个性化文本的位置并单击下拉图标，然后选择&#x200B;**[!UICONTROL Visitor]** > **[!UICONTROL First name]**。

   ![](assets/line_usecase_05.png)

1. 按照相同的步骤添加图像，在&#x200B;**[!UICONTROL Message type]**&#x200B;下拉菜单中选择&#x200B;**[!UICONTROL Image and links]**。

   添加&#x200B;**[!UICONTROL Image URL]**。

   ![](assets/line_usecase_07.png)

1. 在&#x200B;**[!UICONTROL Links]**&#x200B;部分中，选择将图像划分到多个可单击区域的布局。

1. 为图像的每个区域分配一个URL。

   ![](assets/line_usecase_08.png)

1. 保存投放，然后单击&#x200B;**[!UICONTROL Send]**&#x200B;进行分析并将其发送到目标。

   投放会发送到目标。

   ![](assets/line_usecase_06.png)

