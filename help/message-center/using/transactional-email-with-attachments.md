---
solution: Campaign Classic
product: campaign
title: 使用Adobe Campaign Classic将附件添加到事务性消息
description: 了解如何使用Adobe Campaign Classic发送包含个人和/或个性化附件的交易电子邮件
audience: message-center
content-type: reference
topic-tags: use-case
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 1%

---


# 用例：发送包含附件的交易电子邮件{#transactional-email-with-attachments}

此用例的用途是将电子邮件附件快速添加到出站派单。

## 关键步骤{#key-steps}

在此方案中，您将学习如何发送包含个人和/或个性化附件的交易电子邮件。 附件不会预上传到Transactional Messaging服务器上：而是在飞机上生成。

捕获客户互动或详细信息时，您可能需要在流程结束时将此信息发回给客户，例如，在电子邮件附加的PDF文件中。

以下是此方案的主要步骤：

1. 客户进入网站，查找要购买的产品。
1. 客户选择产品并自定义一些选项。
1. 客户完成交易。
1. 将向客户发送确认交易的电子邮件。 由于不建议在电子邮件中发送PII（个人身份信息），因此会生成安全PDF并将其附加到该电子邮件。
1. 客户收到包含相关数据的电子邮件及其附件。

在此方案中，附件不是预先创建的，而是动态添加到出站电子邮件中，这优惠了以下优点：

* 这使您能够个性化附件的内容。
* 如果附件与事务关联（如上面所述的示例方案中），则它可能包含在客户流程期间生成的动态数据。
* 附加PDF文件将优化安全性，因为您可以加密它们并通过HTTPS发送它们。

>[!NOTE]
>
>为避免性能问题，如果您将动态下载的图像作为附件包含在个性化URL中，则默认情况下，每个图像大小不应超过100,000字节。 可以从[Campaign Classic选项的列表](../../installation/using/configuring-campaign-options.md#delivery)配置此推荐阈值。

## 建议{#important-notes}

在实施此方案之前，请仔细阅读以下准则：

* 不应使用“事务消息传递”实例存储、导出或上传文件或数据。 它们只能用于事件数据和相关信息。 它们不应被视为文件存储系统。
* 由于没有直接访问非Adobe事务消息实例或服务器的权限，因此没有在这些服务器上推送此类文件的标准方式（无FTP访问）。
* 在合同上使用Transactional Messaging实例上的磁盘空间存储任何类型的文件（甚至是附件）是不正确的。
* 您需要使用其他联机磁盘系统来托管这些文件。 您需要对此系统的FTP访问，并且必须能够写入和删除文件。

>[!NOTE]
>
>为避免出现性能问题，建议在每封电子邮件中不要包含多个附件。 建议的阈值可以从[Campaign Classic选项的列表](../../installation/using/configuring-campaign-options.md#delivery)配置。

## 实现{#implementation}

下图显示了实施此方案时的不同步骤：

![](assets/message-center-uc1.png)

要将电子邮件附件快速添加到事务性消息，请执行以下步骤：

1. 开始。 有关更多信息，请参阅[此章节](../../delivery/using/attaching-files.md#attach-a-personalized-file)。

   这允许您将文件附加到电子邮件，即使这些文件不在执行实例上托管。

1. 您可以通过SOAP消息触发器发送电子邮件。 在SOAP调用中，有一个URL参数(attachmentURL)。

   有关SOAP请求的详细信息，请参阅[事件说明](../../message-center/using/event-description.md)。

1. 设计电子邮件时，单击&#x200B;**[!UICONTROL Attachment]**。

1. 在&#x200B;**[!UICONTROL Attachment definition]**&#x200B;屏幕中，输入SOAP attachment参数：

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. 处理消息后，系统将从远程位置（第三方服务器）获取文件并将其附加到单个消息。

   由于此参数可以是变量，因此它应接受通过SOAP调用发送的文件的完全形式的远程URL变量。

   ![](assets/message-center-uc2.png)
