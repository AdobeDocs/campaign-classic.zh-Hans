---
product: campaign
title: 创建Web跟踪标记
description: 了解如何创建Web跟踪标记
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# 创建Web跟踪标记{#creating-web-tracking-tags}

您要跟踪的网站的每个页面都必须在Adobe Campaign平台中引用。 可通过两种方式执行此引用：

1. 要跟踪的URL的手动定义，
1. 即时创建要跟踪的URL。

## 定义要在应用程序中跟踪的URL {#defining-the-urls-to-be-tracked-in-the-application}

此方法允许您手动定义要跟踪的页面，然后生成关联的Web跟踪标记示例。 此操作在 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 客户端控制台的节点。

![](assets/d_ncs_integration_webtracking_screen.png)

要生成要插入页面的HTML代码，请执行以下操作：

* 输入标记的标签：它将显示在跟踪日志中，
* 指示源URL:此字段仅供参考，允许您指示跟踪的页面（可选）、
* 如果需要，请输入有效期，
* 单击 **[!UICONTROL Generate]** HTML代码。

然后，复制生成的代码并将其粘贴到要跟踪的页面中。

## 要跟踪的URL的即时创建 {#on-the-fly-creation-of-urls-to-be-tracked}

您可以通过向 **tagid** 参数：

* 跟踪的页面类型：“w”表示WEB，“t”表示TRANSACTION，
* 必须在其中创建URL的文件夹的内部名称。

必须通过添加字符“|”，将这两条信息与跟踪页面的标识符连接：

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>请记住对的值进行编码 **tagid** 参数。

**示例**:创建交易类型Web跟踪URL。

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
