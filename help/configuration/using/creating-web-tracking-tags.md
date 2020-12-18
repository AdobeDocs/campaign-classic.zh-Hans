---
solution: Campaign Classic
product: campaign
title: 创建 Web 跟踪标记
description: 创建 Web 跟踪标记
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 创建 Web 跟踪标记{#creating-web-tracking-tags}

您要跟踪的站点的每个页面都必须在Adobe Campaign平台中引用。 此引用可通过两种方式执行：

1. 要跟踪的URL的手动定义，
1. 要跟踪的URL的实时创建。

## 定义要在应用程序{#defining-the-urls-to-be-tracked-in-the-application}中跟踪的URL

此方法允许您手动定义要跟踪的页面，然后生成关联Web跟踪标签的示例。 此操作在客户端控制台的&#x200B;**[!UICONTROL Campaign execution>Resources>Web tracking tags]**&#x200B;节点中定义。

![](assets/d_ncs_integration_webtracking_screen.png)

要生成要插入页面的HTML代码，请执行以下操作：

* 输入标记的标签：它将在跟踪日志中显示，
* 指示源URL:此字段仅供参考，允许您指明跟踪的页面（可选）、
* 如果需要，请输入有效期，
* 单击&#x200B;**[!UICONTROL Generate]** HTML代码。

然后复制生成的代码并将其粘贴到要跟踪的页面。

## 要跟踪的URL的动态创建{#on-the-fly-creation-of-urls-to-be-tracked}

通过向&#x200B;**tagid**&#x200B;参数的值添加信息，可以动态创建Web跟踪URL:

* 跟踪的页面类型：“w”表示WEB,“t”表示TRANSACTION,
* 必须创建URL的文件夹的内部名称。

必须通过添加字符“|”，将这两条信息与跟踪页面的标识符连接起来：

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>当&#x200B;**tagid**&#x200B;参数用作URL参数时，请记住对其值进行编码。

**示例**:创建事务类型Web跟踪URL。

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
