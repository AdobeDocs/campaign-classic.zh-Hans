---
product: campaign
title: 发送带有附件的事务性电子邮件
description: 了解如何使用Adobe Campaign发送包含单个和/或个性化附件的交易电子邮件
feature: Transactional Messaging
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 2%

---

# 用例：发送带有附件的交易电子邮件 {#transactional-email-with-attachments}

![](../../assets/v7-only.svg)

此用例的用途是将电子邮件附件快速添加到出站调度。

## 关键步骤 {#key-steps}

在此方案中，您将了解如何发送包含单个和/或个性化附件的交易电子邮件。 附件不会预上载到事务型消息传递服务器上：而是会即时生成。

在捕获客户交互或详细信息时，您可能需要在流程结束时将此信息发回给客户，例如在附加到电子邮件的PDF文件中。

以下是此方案的主要步骤：

1. 客户进入网站，找到要购买的产品。
1. 客户选择产品并自定义一些选项。
1. 客户完成交易。
1. 向客户发送确认交易的电子邮件。 由于不建议在电子邮件中发送PII（个人身份信息），因此会生成安全PDF并将其附加到电子邮件中。
1. 客户会收到包含相关数据的电子邮件及其附件。

在此方案中，不会预先创建附件，而是会即时添加到出站电子邮件中，这具有以下好处：

* 这样，您就可以将附件的内容个性化。
* 如果附件与事务关联（如上面所述的示例情景中所示），则它可能包含在客户流程期间生成的动态数据。
* 附加PDF文件会优化安全性，因为您可以对其加密并通过HTTPS发送它们。

>[!NOTE]
>
>为避免出现性能问题，如果您将从个性化URL动态下载的图像作为附件包含在内，则默认情况下每个图像大小不应超过100,000字节。 建议的阈值可从 [Campaign Classic选项列表](../../installation/using/configuring-campaign-options.md#delivery).

## 推荐 {#important-notes}

在实施此方案之前，请仔细阅读以下准则：

* 事务型消息传递实例不应用于存储、导出或上传文件或数据。 它们只能用于事件数据和相关信息。 它们不应被视为文件存储系统。
* 由于无法直接访问Adobe外的事务性消息传递实例或服务器，因此在这些服务器上没有推送此类文件的标准方法（无FTP访问权限）。
* 使用事务性消息传递实例上的磁盘空间存储任何类型的文件（甚至是附件）是不符合合同规定的。
* 您需要使用其他联机磁盘系统来托管这些文件。 您需要具有对此系统的FTP访问权限，并且必须能够写入和删除文件。

>[!NOTE]
>
>为避免出现性能问题，建议在每封电子邮件中不要包含多个附件。 建议的阈值可从 [Campaign Classic选项列表](../../installation/using/configuring-campaign-options.md#delivery).

## 实施 {#implementation}

下图显示了实施此方案时的不同步骤：

![](assets/message-center-uc1.png)

要即时将电子邮件附件添加到事务型消息，请执行以下步骤：

1. 首先，设计附件。 有关更多信息，请参阅[此章节](../../delivery/using/attaching-files.md#attach-a-personalized-file)。

   这样，即使未在执行实例上托管文件，您也可以将文件附加到电子邮件中。

1. 您可以通过SOAP消息触发器发送电子邮件。 在SOAP调用中，有一个URL参数(attachmentURL)。

   有关SOAP请求的更多信息，请参阅 [事件描述](../../message-center/using/event-description.md).

1. 设计电子邮件时，单击 **[!UICONTROL Attachment]**.

1. 在 **[!UICONTROL Attachment definition]** 屏幕中，输入SOAP附件参数：

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. 处理消息后，系统将从远程位置（第三方服务器）获取文件，并将其附加到单个消息。

   由于此参数可以是变量，因此它应接受通过SOAP调用发送的文件的完全格式的远程URL变量。

   ![](assets/message-center-uc2.png)
