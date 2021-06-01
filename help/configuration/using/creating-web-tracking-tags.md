---
product: campaign
title: 创建 Web 跟踪标记
description: 创建 Web 跟踪标记
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 4%

---

# 创建 Web 跟踪标记{#creating-web-tracking-tags}

您要跟踪的网站的每个页面都必须在Adobe Campaign平台中引用。 可通过两种方式执行此引用：

1. 要跟踪的URL的手动定义，
1. 即时创建要跟踪的URL。

## 定义要在应用程序{#defining-the-urls-to-be-tracked-in-the-application}中跟踪的URL

此方法允许您手动定义要跟踪的页面，然后生成关联的Web跟踪标记示例。 此操作在客户端控制台的&#x200B;**[!UICONTROL Campaign execution>Resources>Web tracking tags]**&#x200B;节点中定义。

![](assets/d_ncs_integration_webtracking_screen.png)

要生成要插入页面的HTML代码，请执行以下操作：

* 输入标记的标签：它将显示在跟踪日志中，
* 指示源URL:此字段仅供参考，允许您指示跟踪的页面（可选）、
* 如果需要，请输入有效期，
* 单击&#x200B;**[!UICONTROL Generate]** HTML代码。

然后，复制生成的代码并将其粘贴到要跟踪的页面中。

## 要跟踪的URL的动态创建{#on-the-fly-creation-of-urls-to-be-tracked}

您可以通过向&#x200B;**tagid**&#x200B;参数的值添加信息来快速创建Web跟踪URL:

* 跟踪的页面类型：“w”表示WEB，“t”表示TRANSACTION，
* 必须在其中创建URL的文件夹的内部名称。

必须通过添加字符“|”，将这两条信息与跟踪页面的标识符连接：

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>当&#x200B;**tagid**&#x200B;参数用作URL参数时，请记住对该参数的值进行编码。

**示例**:创建交易类型Web跟踪URL。

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
