---
title: 创建 Web 跟踪标记
seo-title: 创建 Web 跟踪标记
description: 创建 Web 跟踪标记
seo-description: null
page-status-flag: never-activated
uuid: c5599bdd-e6b8-4db4-b0ca-aaee2adc1919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 647ca037-4efb-4524-9642-11056d096aea
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 6%

---


# 创建 Web 跟踪标记{#creating-web-tracking-tags}

您要跟踪的站点的每个页面都必须在Adobe Campaign平台中引用。 此引用可通过两种方式执行：

1. 要跟踪的URL的手动定义，
1. 要跟踪的URL的实时创建。

## 定义要在应用程序中跟踪的URL {#defining-the-urls-to-be-tracked-in-the-application}

此方法允许您手动定义要跟踪的页面，然后生成关联Web跟踪标签的示例。 此操作在客户端控 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 制台的节点中定义。

![](assets/d_ncs_integration_webtracking_screen.png)

要生成要插入页面的HTML代码，请执行以下操作：

* 输入标记的标签：它将在跟踪日志中显示，
* 指示源URL:此字段仅供参考，允许您指明跟踪的页面（可选）、
* 如果需要，请输入有效期，
* 单击 **[!UICONTROL Generate]** HTML代码。

然后复制生成的代码并将其粘贴到要跟踪的页面。

## 要跟踪的URL的即时创建 {#on-the-fly-creation-of-urls-to-be-tracked}

您可以通过向tagid参数的值添加信息来动态创建Web跟踪 **URL** :

* 跟踪的页面类型：“w”表示WEB,“t”表示TRANSACTION,
* 必须创建URL的文件夹的内部名称。

必须通过添加字符“|”，将这两条信息与跟踪页面的标识符连接起来：

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>当tagid参数用作URL参 **数时** ，请记住对它的值进行编码。

**示例**:创建事务类型Web跟踪URL。

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
