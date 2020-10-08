---
title: 在 Facebook 上发布
seo-title: 在 Facebook 上发布
description: 在 Facebook 上发布
seo-description: null
page-status-flag: never-activated
uuid: f15170fa-0e7d-4913-81d6-0072c1ece482
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 335cf2de-1874-4e48-9538-f0937641cf96
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1151'
ht-degree: 3%

---


# 在 Facebook 上发布{#publishing-on-facebook}

配置完成后，Social Marketing允许您在Facebook页面的墙上发布出版物。

## 限制{#limitations}

Facebook固有以下限制。

* 邮件长度不得超过1,000个字符。
* 不支持HTML。

## 创建投放 {#creating-the-delivery}

使用投放创建新投放模板 **[!UICONTROL Publish to a brand page]** 。

![](assets/social_facebook_delivery_001.png)

## Selecting the main target {#selecting-the-main-target}

您需要选择要将出版物发布到的页面。

1. 单击链 **[!UICONTROL To]** 接。

   ![](assets/social_facebook_delivery_010.png)

1. 单击 **[!UICONTROL Add]** 按钮。

   ![](assets/social_facebook_delivery_011.png)

1. 选择 **[!UICONTROL A Facebook page]**。

   ![](assets/social_facebook_delivery_012.png)

1. 在字段 **[!UICONTROL Folder]** 中，选择包含Facebook页面的服务文件夹。 默认情况下，页面存储在服务文件夹的 **[!UICONTROL Facebook]** 根目录中。 然后选择要发布到的Facebook页面。

   ![](assets/social_facebook_delivery_013.png)

## 选择验证目标 {#selecting-the-proof-target}

在 **[!UICONTROL Target of the proofs]** 选项卡中，您可以定义要在发出投放之前用于测试其的Facebook页面。 我们建议为此目的创建专用的Facebook专用页面。 有关创建专用Facebook页面的详细信息，请参 [阅创建测试Facebook页面](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)。 要选择验证目标，请应用与主目标相同的步骤： [选择主目标](#selecting-the-main-target)。

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>如果对所有投放使用同一Facebook测试页，则可以在目标中保存验证，该投放模板通过节点 **[!UICONTROL Publish to a brand page]** 进行访问 **[!UICONTROL Resources > Templates > Delivery templates]** 。 默认情况下，将为每个新验证输入目标。

## 定义受众 {#defining-the-audience}

如果您要使用本地区段来优化已授权视图发布的公共类型，我们建议您为每个区段创建一个Facebook页面(例如：Adobe Campaign巴黎、Adobe Campaign伦敦等)。

但是，也可以使用Facebook使用的受众过滤器。 优惠 **[!UICONTROL Audience]****[!UICONTROL Select target window]** 四个过滤器的选项卡：

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!IMPORTANT]
>
>谨慎使用此函数。 在投放报告中， **[!UICONTROL Number of fans]** 该指标不会考虑这些Facebook过滤器。
>
>Facebook可能会改变受众过滤器的列表及其价值观。

## 定义消息内容 {#defining-message-content}

使用下拉菜单选择发 **[!UICONTROL Content type]** 布类型。

![](assets/social_facebook_delivery_006.png)

提供以下类型的投放:

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### 发布状态 {#publishing-a-status}

状态类型投放只能包含文本，如下例所示：

![](assets/social_create_facebook_wall_post_004.png)

在输入区域中输入发布状态。

![](assets/social_facebook_delivery_015.png)

### 发布包含链接的状态 {#publishing-a-status-with-a-link}

具有链接的状态类型投放可能包含文本、图像和链接。 以下部分详细介绍了投放编辑屏幕的字段与Facebook上的最终出版物之间的对称性：

![](assets/social_facebook_delivery_007.png)

输入各个字段：

>[!IMPORTANT]
>
>所有URL都必须用 **“http://”** 或 **“https://”开始**。

1. 在字 **[!UICONTROL Status]** 段中，输入将在页面名称下显示的文本。
1. 在字 **[!UICONTROL Name]** 段中，输入发布标题。
1. 在字 **[!UICONTROL Link]** 段中，输入发布指向的URL。

   >[!NOTE]
   >
   >如果您要将该字段添 **[!UICONTROL Link]** 加到Facebook应用程序的URL以进行推广，我们建议您将其改编为智能手机显示标准：
   >
   >1. 选择Facebook应用程序 [https://developers.facebook.com/apps](https://developers.facebook.com/apps)，然后选择选 **[!UICONTROL Settings > Basic]** 项卡。
   >1. 输入字 **[!UICONTROL Namespace]** 段。
   >1. 输入字 **[!UICONTROL Mobile Site URL]** 段：当用户单击其智能手机上的发布链接时，Facebook会自动将其重定向到该字段中定义的URL。
   >1. 创建您的Web应用程序，使Facebook显示屏根据所使用的设备（智能手机或PC）进行个性化。
   >1. 通过Adobe Campaign **[!UICONTROL Link]** 控制台转到发布的字段，输入该字段的 **[!UICONTROL Canvas page]** URL。


1. 在字 **[!UICONTROL Image]** 段中，输入将在发布左侧显示的图像URL。

   >[!IMPORTANT]
   >
   >图像必须托管在公共互联网站点上，Facebook才能上传。

1. 在字 **[!UICONTROL Caption]** 段中，输入将在发布末尾显示的文本。
1. 转到字 **[!UICONTROL Description]** 段并输入要在标题下显示的文本。

![](assets/social_facebook_delivery_005.png)

### 通过YouTube链接发布状态 {#publishing-a-status-with-a-youtube-link}

此类内容允许您发布指向YouTube视频的链接。 就像具有常规链接的状态一样，您可以定义状态、名称、题注、描述和其他链接。 图像由Facebook自动添加。 投放编辑屏幕的字段与Facebook上的最终出版物之间的对称性详述如下：

![](assets/social_facebook_delivery_youtube_1.png)

输入各个字段：

>[!CAUTION]
>
>所有URL都必须用 **“http://”** 或 **“https://”开始**。

1. 在字 **[!UICONTROL Status]** 段中，输入将在页面名称下显示的文本。
1. 在字 **[!UICONTROL Name]** 段中，输入发布标题。
1. 在字 **[!UICONTROL Video code]** 段中，输入YouTube视频的代码。 例如，对于“https://www.youtube.com/watch?v=abc123456&#39;”链接，视频代码将为“abc123456”。
1. 在字 **[!UICONTROL Caption]** 段中，输入将在发布末尾显示的文本。
1. 转到字 **[!UICONTROL Description]** 段并输入要在标题下显示的文本。

![](assets/social_facebook_delivery_youtube.png)

### 发布相册 {#publishing-a-photo-album}

此类型的内容允许您发布相册。 您可以为相册添加名称和描述，并为每张照片添加题注。 投放编辑屏幕的字段与Facebook上的最终出版物之间的对称性详述如下：

![](assets/social_facebook_delivery_photos_1.png)

输入各个字段：

1. 开始 **[!UICONTROL Album name]**。
1. 然后，输 **[!UICONTROL Description]** 入要在照片上方显示的内容。
1. 要添加照片，请单击按 **[!UICONTROL Add]** 钮，选择照片，然后单击 **[!UICONTROL Open]**。
1. 可向每张照片添加题注。

![](assets/social_facebook_delivery_photos.png)

## 预览 {#previewing}

使用 **[!UICONTROL Preview]** 该选项卡可视图发布的呈现。

1. 单击选 **[!UICONTROL Preview]** 项卡。
1. 单击下 **[!UICONTROL Test personalization]** 拉菜单并选择 **[!UICONTROL Service]**。
1. 在字段 **[!UICONTROL Folder]** 中，选择包含您的Facebook页面的服务文件夹。 默认情况下，页面存储在服务文件夹的 **[!UICONTROL Facebook]** 根目录下。
1. 选择要测试预览的Facebook页面。

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>预览可能与最终的Facebook出版物略有不同。 我们强烈建议在最终验证之前发送投放，以精确呈现出版物。 请参阅 [发送验证](#sending-the-proof)。

## 配置跟踪 {#configuring-tracking}

跟踪可在投放报告以及投放和服 **[!UICONTROL Edit > Tracking]** 务的选项卡中查看。

单击投放中包含的URL是按Adobe Campaign度量的。 按钮的点击次 **[!UICONTROL Like]** 数、评论数和粉丝数量数由Facebook衡量。

跟踪配置与电子邮件投放相同。 如需详细信息，请参阅[此部分](../../delivery/using/monitoring-a-delivery.md)。

>[!NOTE]
>
>在投放模板 **[!UICONTROL Publish to a brand page]** 中，默认情况下启用跟踪。

## 发送验证 {#sending-the-proof}

我们强烈建议在最终验证之前发送出版物的视图，以在专用Facebook测试页上投放出版物的确切呈现。 有关创建专用Facebook测试页的详细信息，请参 [阅创建测试Facebook页](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)。 选择目标验证的步骤详见选 [择验证目标](#selecting-the-proof-target)。

验证投放与电子邮件投放相同。 请参阅[此章节](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) 。

## 发送消息 {#sending-the-message}

1. 批准内容后，单击按 **[!UICONTROL Send]** 钮。
1. 选 **[!UICONTROL Deliver as soon as possible]** 择并单击 **[!UICONTROL Analyze]** 按钮。

   >[!NOTE]
   >
   >通过 **[!UICONTROL Postpone the delivery]** 此选项，您可以延后投放到以后的日期。

   ![](assets/social_facebook_delivery_009.png)

1. 分析完成后，检查结果。
1. 单 **[!UICONTROL Confirm delivery]**&#x200B;击，然后单击 **[!UICONTROL Yes]**。

   ![](assets/social_facebook_delivery_016.png)

