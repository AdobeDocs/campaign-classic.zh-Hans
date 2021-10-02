---
product: campaign
title: 将Adobe Experience Platform区段摄取到Campaign中
description: 了解如何将Adobe Experience Platform受众摄取到Campaign Classic。
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# 将Adobe Experience Platform区段摄取到Campaign中 {#destinations}

![](../../assets/common.svg)

要将Adobe Experience Platform受众摄取到Campaign中并在工作流中使用，您首先需要将Adobe Campaign作为Adobe Experience Platform **目标**&#x200B;连接，然后使用要导出的区段对其进行配置。

配置目标后，数据将导出到您的存储位置，您需要在Campaign Classic中构建专用工作流以摄取数据。

## 将Adobe Campaign连接为目标

在Adobe Experience Platform中，通过为导出的区段选择存储位置来配置与Adobe Campaign的连接。 此步骤还允许您选择要导出的区段，并指定要包含的其他XDM字段。

有关更多信息，请参阅[目标文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html)。

配置目标后，Adobe Experience Platform会在您提供的存储位置中创建一个以制表符分隔的.txt或.csv文件。 此操作计划每24小时执行一次。

您现在可以配置Campaign Classic工作流，以将区段摄取到Campaign中。

## 在Campaign Classic中创建导入工作流

将Campaign Classic配置为目标后，您需要构建专用工作流以导入Adobe Experience Platform导出的文件。

为此，您需要添加并配置&#x200B;**[!UICONTROL File transfer]**&#x200B;活动。 有关如何配置此活动的更多信息，请参阅[此部分](../../workflow/using/file-transfer.md)。

![](assets/rtcdp-file-transfer.png)

然后，您可以根据需要构建工作流（使用区段数据更新数据库、向区段发送跨渠道投放等）

例如，下面的工作流每天从您的存储位置下载文件，然后使用区段数据更新Campaign数据库。

![](assets/rtcdp-workflow.png)
