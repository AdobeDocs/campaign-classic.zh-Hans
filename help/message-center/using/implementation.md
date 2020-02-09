---
title: 实施
seo-title: 实施
description: 实施
seo-description: null
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 实施{#implementation}

下面是一个图，其中显示了此方案中涉及的不同步骤。

![](assets/message-center-uc1.png)

首先，设计附件。 请参阅此 [文章](../../delivery/using/attaching-files.md#attach-a-personalized-file)。 这允许您将文件附加到电子邮件，即使这些文件不在执行实例中托管。

您可以通过SOAP消息触发器发送电子邮件。 有关SOAP请求的详细信息，请参阅 [事件说明](../../message-center/using/event-description.md)。 在SOAP调用中，有一个URL参数(attachmentURL)。

设计电子邮件时，请单击 **[!UICONTROL Attachment]** 。 在屏幕 **[!UICONTROL Attachment definition]** 中，输入SOAP attachment参数：

```
<%= rtEvent.ctx.attachementUrl %>
```

当消息处理／部署时，系统将从远程位置（第三方服务器）获取该文件并将其附加到单个消息。

由于此参数可以是变量，因此它应接受通过SOAP调用发送的文件的完全格式的远程URL变量。

![](assets/message-center-uc2.png)

