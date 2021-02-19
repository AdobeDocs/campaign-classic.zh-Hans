---
solution: Campaign Classic
product: campaign
title: 在 Facebook 上发布
description: 在 Facebook 上发布
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 2%

---


# 在 Facebook 上发布{#publishing-on-facebook}

配置完成后，Social Marketing允许您在Facebook页面的墙上发布出版物。

## 限制{#limitations}

Facebook固有以下限制。

* 消息不能超过1,000个字符。
* 不支持HTML。

## 创建投放 {#creating-the-delivery}

使用&#x200B;**[!UICONTROL Publish to a brand page]**&#x200B;投放创建新投放模板。

![](assets/social_facebook_delivery_001.png)

## 选择主目标{#selecting-the-main-target}

您需要选择要将发布发布发布到的页面。

1. 单击&#x200B;**[!UICONTROL To]**&#x200B;链接。

   ![](assets/social_facebook_delivery_010.png)

1. 单击 **[!UICONTROL Add]** 按钮。

   ![](assets/social_facebook_delivery_011.png)

1. 选择 **[!UICONTROL A Facebook page]**。

   ![](assets/social_facebook_delivery_012.png)

1. 在&#x200B;**[!UICONTROL Folder]**&#x200B;字段中，选择包含Facebook页面的服务文件夹。 默认情况下，页面存储在&#x200B;**[!UICONTROL Facebook]**&#x200B;服务文件夹的根文件夹中。 然后选择要在其上发布的Facebook页面。

   ![](assets/social_facebook_delivery_013.png)

## 选择验证目标{#selecting-the-proof-target}

**[!UICONTROL Target of the proofs]**&#x200B;选项卡允许您定义要在发出投放之前用于测试其的Facebook页面。 我们建议为此目的创建专用的Facebook专用页面。 有关创建专用Facebook页面的详细信息，请参阅[创建测试Facebook页面](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)。 要选择验证目标，请应用与主目标相同的步骤：[选择主目标](#selecting-the-main-target)。

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>如果对所有投放使用相同的Facebook测试页，则可以在&#x200B;**[!UICONTROL Publish to a brand page]**&#x200B;投放模板中保存验证目标，该通过&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;节点访问。 默认情况下，将为每个新验证输入投放目标。

## 定义受众{#defining-the-audience}

如果您希望使用本地区段来优化已授权视图发布的公共类型，我们建议您为每个区段创建一个Facebook页面(例如：Adobe Campaign巴黎、Adobe Campaign伦敦等)。

但是，也可以使用Facebook使用的受众过滤器。 **[!UICONTROL Select target window]**&#x200B;的&#x200B;**[!UICONTROL Audience]**&#x200B;选项卡优惠了四个过滤器:

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!IMPORTANT]
>
>谨慎使用此函数。 在投放报告中，**[!UICONTROL Number of fans]**&#x200B;指示符将不考虑这些Facebook过滤器。
>
>Facebook可能会更改受众过滤器的列表及其价值。

## 定义消息内容{#defining-message-content}

使用&#x200B;**[!UICONTROL Content type]**&#x200B;下拉菜单选择发布类型。

![](assets/social_facebook_delivery_006.png)

提供以下类型的投放:

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### 发布状态{#publishing-a-status}

状态类型投放只能包含文本，如下例所示：

![](assets/social_create_facebook_wall_post_004.png)

在输入区域中输入发布状态。

![](assets/social_facebook_delivery_015.png)

### 发布具有链接{#publishing-a-status-with-a-link}的状态

具有链接的状态类型投放可能包含文本、图像和链接。 下节详细介绍了投放编辑屏幕的字段与Facebook上的最终出版物之间的对称性：

![](assets/social_facebook_delivery_007.png)

输入各种字段：

>[!IMPORTANT]
>
>所有URL都必须与&#x200B;**&quot;http://&quot;**&#x200B;或&#x200B;**&quot;https://&quot;**&#x200B;开始。

1. 在&#x200B;**[!UICONTROL Status]**&#x200B;字段中，输入将在页面名称下显示的文本。
1. 在&#x200B;**[!UICONTROL Name]**&#x200B;字段中，输入发布标题。
1. 在&#x200B;**[!UICONTROL Link]**&#x200B;字段中，输入发布指向的URL。

   >[!NOTE]
   >
   >如果您要将&#x200B;**[!UICONTROL Link]**&#x200B;字段添加到Facebook应用程序的URL以进行升级，建议您将其调整为智能手机显示条件：
   >
   >1. 选择Facebook应用程序[https://developers.facebook.com/apps](https://developers.facebook.com/apps)，然后选择&#x200B;**[!UICONTROL Settings > Basic]**&#x200B;选项卡。
   >1. 输入&#x200B;**[!UICONTROL Namespace]**&#x200B;字段。
   >1. 输入&#x200B;**[!UICONTROL Mobile Site URL]**&#x200B;字段：当用户在其智能手机上单击“发布”链接时，Facebook会自动将他们重定向到此字段中定义的URL。
   >1. 创建您的Web应用程序，以便Facebook显示个性化为所用设备（智能手机或PC）的功能。
   >1. 通过Adobe Campaign控制台转到发布的&#x200B;**[!UICONTROL Link]**&#x200B;字段，输入&#x200B;**[!UICONTROL Canvas page]**&#x200B;字段的URL。


1. 在&#x200B;**[!UICONTROL Image]**&#x200B;字段中，输入将在发布左侧显示的图像URL。

   >[!IMPORTANT]
   >
   >图像必须托管在公共互联网站点上，Facebook才能上传。

1. 在&#x200B;**[!UICONTROL Caption]**&#x200B;字段中，输入将在发布末尾显示的文本。
1. 转到&#x200B;**[!UICONTROL Description]**&#x200B;字段，并输入要在标题下显示的文本。

![](assets/social_facebook_delivery_005.png)

### 发布具有YouTube链接{#publishing-a-status-with-a-youtube-link}的状态

此类内容允许您发布指向YouTube视频的链接。 就像具有常规链接的状态一样，您可以定义状态、名称、题注、描述和其他链接。 图像由Facebook自动添加。 投放编辑屏幕的字段与Facebook上的最终出版物之间的对称性详述如下：

![](assets/social_facebook_delivery_youtube_1.png)

输入各种字段：

>[!IMPORTANT]
>
>所有URL都必须与&#x200B;**&quot;http://&quot;**&#x200B;或&#x200B;**&quot;https://&quot;**&#x200B;开始。

1. 在&#x200B;**[!UICONTROL Status]**&#x200B;字段中，输入将在页面名称下显示的文本。
1. 在&#x200B;**[!UICONTROL Name]**&#x200B;字段中，输入发布标题。
1. 在&#x200B;**[!UICONTROL Video code]**&#x200B;字段中，输入YouTube视频的代码。 例如，对于“https://www.youtube.com/watch?v=abc123456&#39;”链接，视频代码将为“abc123456”。
1. 在&#x200B;**[!UICONTROL Caption]**&#x200B;字段中，输入将在发布末尾显示的文本。
1. 转到&#x200B;**[!UICONTROL Description]**&#x200B;字段，并输入要在标题下显示的文本。

![](assets/social_facebook_delivery_youtube.png)

### 发布相册{#publishing-a-photo-album}

此类型的内容允许您发布相册。 您可以为影集添加名称和说明，并为每张照片添加题注。 投放编辑屏幕的字段与Facebook上的最终出版物之间的对称性详述如下：

![](assets/social_facebook_delivery_photos_1.png)

输入各种字段：

1. 开始。**[!UICONTROL Album name]**
1. 然后输入要显示在照片上方的&#x200B;**[!UICONTROL Description]**。
1. 要添加照片，请单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮，选择照片，然后单击&#x200B;**[!UICONTROL Open]**。
1. 可向每张照片添加题注。

![](assets/social_facebook_delivery_photos.png)

## 预览{#previewing}

使用&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡可以视图发布的呈现。

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡。
1. 单击&#x200B;**[!UICONTROL Test personalization]**&#x200B;下拉菜单并选择&#x200B;**[!UICONTROL Service]**。
1. 在&#x200B;**[!UICONTROL Folder]**&#x200B;字段中，选择包含您的Facebook页面的服务文件夹。 默认情况下，页面存储在&#x200B;**[!UICONTROL Facebook]**&#x200B;服务文件夹的根目录中。
1. 选择要测试其预览的Facebook页面。

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>预览可能与最终的Facebook出版物略有不同。 我们强烈建议在最终验证之前发送一个投放，以精确呈现出版物。 请参阅[发送验证](#sending-the-proof)。

## 配置跟踪{#configuring-tracking}

可以在投放报告和投放和服务的&#x200B;**[!UICONTROL Edit > Tracking]**&#x200B;选项卡中查看跟踪。

单击投放中包含的URL是按Adobe Campaign度量的。 单击&#x200B;**[!UICONTROL Like]**&#x200B;按钮的次数、评论数和粉丝数量由Facebook测量。

跟踪配置与电子邮件投放相同。 如需详细信息，请参阅[此部分](../../delivery/using/about-delivery-monitoring.md)。

>[!NOTE]
>
>在&#x200B;**[!UICONTROL Publish to a brand page]**&#x200B;投放模板中，默认情况下启用跟踪。

## 发送验证{#sending-the-proof}

我们强烈建议在最终投放之前发送您的出版物的验证，以在专用Facebook测试页面上视图出版物的确切呈现。 有关创建专用Facebook测试页的详细信息，请参阅[创建测试Facebook页面](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)。 选择目标验证的步骤详见[选择验证目标](#selecting-the-proof-target)。

验证投放与电子邮件投放相同。 请参阅[此章节](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) 。

## 发送消息{#sending-the-message}

1. 批准内容后，单击&#x200B;**[!UICONTROL Send]**&#x200B;按钮。
1. 选择&#x200B;**[!UICONTROL Deliver as soon as possible]**&#x200B;并单击&#x200B;**[!UICONTROL Analyze]**&#x200B;按钮。

   >[!NOTE]
   >
   >**[!UICONTROL Postpone the delivery]**&#x200B;选项允许您延后投放到以后的日期。

   ![](assets/social_facebook_delivery_009.png)

1. 分析完成后，检查结果。
1. 单击&#x200B;**[!UICONTROL Confirm delivery]**，然后单击&#x200B;**[!UICONTROL Yes]**。

   ![](assets/social_facebook_delivery_016.png)

