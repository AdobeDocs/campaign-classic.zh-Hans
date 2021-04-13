---
solution: Campaign Classic
product: campaign
title: 将Adobe Experience Platform细分引入活动
description: 了解如何将Adobe Experience Platform受众引入Campaign Classic。
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: 9b3254c16eed784846db87d27f9f5de009dafdc3
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# 将Adobe Experience Platform区段收录到活动{#destinations}

要将Adobe Experience Platform引入活动并在工作流中使用它们，您首先需要将Adobe Campaign作为Adobe Experience Platform **目标**&#x200B;连接，并配置要导出的区段。

配置目标后，数据将导出到您的存储位置，您需要在Campaign Classic中构建专用工作流才能收集它。

## 将Adobe Campaign连接为目标

在Adobe Experience平台中，通过为导出的区段选择存储位置，配置与Adobe Campaign的连接。 此步骤还允许您选择要导出的区段，并指定要包含的其他XDM字段。

有关详细信息，请参阅[目标文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html)。

配置目标后，Adobe Experience Platform会在您提供的存储位置创建制表符分隔的.txt或.csv文件。 此操作计划在每24小时执行一次。

您现在可以配置Campaign Classic工作流，以将区段引入活动。

## 在Campaign Classic中创建导入工作流

将Campaign Classic配置为目标后，您需要构建专用工作流以导入Adobe Experience Platform导出的文件。

为此，您需要添加并配置&#x200B;**[!UICONTROL File transfer]**&#x200B;活动。 有关如何配置此活动的详细信息，请参阅[此部分](../../workflow/using/file-transfer.md)。

![](assets/rtcdp-file-transfer.png)

然后，您可以根据自己的需要构建工作流(使用区段投放更新数据库，向区段发送跨渠道等)

例如，下面的工作流每天从您的存储位置下载文件，然后使用区段数据更新活动数据库。

![](assets/rtcdp-workflow.png)
