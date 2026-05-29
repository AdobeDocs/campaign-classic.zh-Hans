---
product: campaign
title: Sources 与 Destinations 入门
description: 详细了解Adobe Experience Platform Sources和Destinations
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
TQID: https://experienceleague.adobe.com/xPpBR6NrQ315FIw1beLnw4c0gyLzEoYWzIXDljDg9H4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 15%

---

# 使用源和目标 {#rtcdp}



## 关于源和目标

借助Adobe Experience Platform，您可以在Campaign Classic和Adobe Real-time Customer Data Platform (RTCDP)之间共享数据。 这允许您在活动工作流中定位Adobe Experience Platform受众，然后将与这些受众相关的数据（如发送、打开和点击）发送回Adobe Real-time Customer Data Platform。

* 使用&#x200B;**目标**，将受众从Adobe Experience Platform引入到Campaign Classic中。 这样，您就可以为营销活动激活已知和未知数据。
* 使用&#x200B;**源**，将Campaign Classic数据（例如发送、打开、单击）导出到Adobe Experience Platform。 这样，您就可以将从不同来源收集的数据集中到一个地方，并利用从中获得的见解做更多事情。

>[!IMPORTANT]
>
>在执行此集成时，请记住Adobe Campaign合同规定的SFTP存储限制、数据库存储限制和活动配置文件限制。

有关Adobe Real-time Customer Data Platform、目标和源的更详细概述，请参阅以下页面：

* [Adobe 实时客户数据平台](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=zh-Hans)
* [目标文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=zh-Hans)
* [源文档](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=zh-Hans)

## 将Campaign Classic与Adobe Experience Platform连接

为了能够在Adobe Experience Platform和Campaign Classic之间共享数据，您首先需要将Adobe Campaign连接为&#x200B;**目标**，并在Adobe Experience Platform中将您的AWS S3或Azure Blob存储位置连接为&#x200B;**Source**。

配置连接器后，您可以使用工作流设置数据导入或导出到Campaign Classic中。

![](assets/rtcdp-schema.png)

有关如何设置这些导入和导出流程的更多详细信息，请参阅以下章节：

* [将Adobe Experience Platform区段引入Campaign](../../integrations/using/ingest-aep-data.md)
* [将数据从 Campaign 导出到 Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
