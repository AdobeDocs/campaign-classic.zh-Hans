---
product: campaign
title: 创建Web跟踪标记
description: 了解如何创建Web跟踪标记
feature: Application Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 2%

---

# 创建Web跟踪标记{#creating-web-tracking-tags}

必须在Adobe Campaign平台中引用要跟踪的网站每个页面。 可以通过两种方式执行此引用：

1. 手动定义要跟踪的URL，
1. 动态创建要跟踪的URL。

## 定义要在应用程序中跟踪的URL {#defining-the-urls-to-be-tracked-in-the-application}

此方法允许您手动定义要跟踪的页面，然后生成关联的Web跟踪标记示例。 此操作在中定义 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 客户端控制台节点。

![](assets/d_ncs_integration_webtracking_screen.png)

要生成要插入到页面中的HTML代码，请执行以下操作：

* 输入标记的标签：它将显示在跟踪日志中，
* 指示源URL：此字段用于提供信息，并允许您指示跟踪的页面（可选），
* 如果需要，请输入有效期，
* 单击 **[!UICONTROL Generate]** 代码HTML。

然后，复制生成的代码并将其粘贴到要跟踪的页面中。

## 动态创建要跟踪的URL {#on-the-fly-creation-of-urls-to-be-tracked}

您可以通过将信息添加到的值来动态创建Web跟踪URL **tagid** 参数：

* 跟踪的页面类型：“w”表示WEB，“t”表示TRANSACTION，
* 必须创建URL的文件夹的内部名称。

必须通过添加字符“|”，将这两条信息与跟踪页面的标识符连接起来：

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>请记住对 **tagid** 参数作为URL参数时的情况。

**示例**：创建事务类型Web跟踪URL。

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
