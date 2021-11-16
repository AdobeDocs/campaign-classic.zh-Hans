---
product: campaign
title: Sources 与 Destinations 入门
description: 了解有关Adobe Experience Platform源和目标的更多信息。
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
source-git-commit: af40fe822c69979a478604595790d4deefd6d5b0
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 13%

---

# 使用源和目标 {#rtcdp}

![](../../assets/common.svg)

## 关于源和目标

通过Adobe Experience Platform，您可以在Campaign Classic与Adobe Real-time Customer Data Platform(RTCDP)之间共享数据。 这允许您在Campaign工作流中定位Adobe Experience Platform受众，然后发送回与这些受众相关的Adobe Real-time Customer Data Platform数据，如发送、打开和点击。

* 使用 **目标**，将受众从Adobe Experience Platform摄取到Campaign Classic。 这允许您激活营销活动的已知和未知数据。
* 使用 **源**，将Campaign Classic数据（例如发送、打开、单击）导出到Adobe Experience Platform。 这样，您可以将从不同来源收集的数据集中到一个位置，并利用从该位置获得的分析完成更多工作。

>[!IMPORTANT]
>
>执行此集成时，请牢记SFTP存储限制、数据库存储限制和根据您的Adobe Campaign合同规定的活动配置文件限制。

有关Adobe Real-time Customer Data Platform、目标和源的更多详细概述，请参阅以下页面：

* [Adobe Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=zh-Hans)
* [Destinations（目标）文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=zh-Hans)
* [Sources（源）文档](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=zh-Hans)

## 连接Campaign Classic与Adobe Experience Platform

要在Adobe Experience Platform和Campaign Classic之间共享数据，您首先需要将Adobe Campaign作为 **目标**，并将AWS S3或Azure Blob存储位置作为 **来源** Adobe体验平台中。

配置连接器后，您可以使用工作流设置数据导入或导出到Campaign Classic。

![](assets/rtcdp-schema.png)

有关如何设置这些导入和导出流程的更多详细信息，请参阅以下章节：

* [将Adobe Experience Platform区段摄取到Campaign中](../../integrations/using/ingest-aep-data.md)
* [将数据从 Campaign 导出到 Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
