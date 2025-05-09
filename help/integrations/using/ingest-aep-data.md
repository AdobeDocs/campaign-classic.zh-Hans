---
product: campaign
title: 将Adobe Experience Platform区段引入Campaign
description: 了解如何将Adobe Experience Platform受众纳入Campaign Classic
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 将Adobe Experience Platform区段引入Campaign {#destinations}



要将Adobe Experience Platform受众摄取到Campaign并在您的工作流中使用它们，您首先需要将Adobe Campaign as a Adobe Experience Platform **目标**&#x200B;连接起来，并使用要导出的区段对其进行配置。

目标配置完成后，数据将导出到您的存储位置，您将需要在Campaign Classic中构建专用工作流来摄取数据。

## 连接Adobe Campaign作为目标

在AdobeExperience Platform中，通过为导出的区段选择存储位置来配置与Adobe Campaign的连接。 此步骤还允许您选择要导出的区段并指定要包含的其他XDM字段。

有关详细信息，请参阅[目标文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=zh-Hans)。

配置目标后，Adobe Experience Platform会在您提供的存储位置创建一个以制表符分隔的.txt或.csv文件。 每24小时安排并执行一次此操作。

您现在可以配置Campaign Classic工作流以将区段摄取到Campaign。

## 在Campaign Classic中创建导入工作流

将Campaign Classic配置为目标后，您需要构建一个专用工作流来导入Adobe Experience Platform已导出的文件。

为此，您需要添加和配置&#x200B;**[!UICONTROL File transfer]**&#x200B;活动。 有关如何配置此活动的详细信息，请参阅[此部分](../../workflow/using/file-transfer.md)。

![](assets/rtcdp-file-transfer.png)

然后，您可以根据需要构建工作流（使用区段数据更新数据库，向区段发送跨渠道投放等）

例如，以下工作流每天从您的存储位置下载文件，然后使用区段数据更新Campaign数据库。

![](assets/rtcdp-workflow.png)
