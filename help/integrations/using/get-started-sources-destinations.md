---
solution: Campaign Classic
product: campaign
title: 源和目标入门
description: 了解有关Adobe Experience Platform源和目标的更多信息。
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: b4da54c122e75a175f6f586a05955b3dfed00c1e
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# 源和目标{#rtcdp}入门

## 关于源和目标

借助Adobe Experience Platform，您可以在Campaign Classic和Adobe实时客户数据平台(RTCDP)之间共享数据。 这允许您在活动工作流中目标Adobe Experience Platform受众，然后发回到与这些受众相关的Adobe实时客户数据平台数据，如发送、打开和单击。

* 对于&#x200B;**目标**，将受众从Adobe Experience Platform收录到Campaign Classic。 这样，您就可以激活营销活动的已知和未知数据。
* 对于&#x200B;**源**，将Campaign Classic数据（例如发送、打开、单击）导出到Adobe Experience Platform。 这使您能够将从不同来源收集的数据集中到一个位置，并利用从中获得的洞察执行更多操作。

>[!IMPORTANT]
>
>执行此集成时，请记住SFTP存储限制、数据库存储限制和Adobe Campaign合同中的有效用户档案限制。

有关Adobe Real-time Customer Data Platform、Destinations和Sources的更详细概述，请参阅以下页面：

* [Adobe实时客户数据平台](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
* [目标文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html)
* [源文档](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

## 连接Campaign Classic与Adobe Experience Platform

要在Adobe Experience Platform和Campaign Classic之间共享数据，您首先需要将Adobe Campaign作为&#x200B;**目标**&#x200B;连接，并将AWS S3或Azure Blob存储位置作为Adobe体验平台中的&#x200B;**源**&#x200B;连接。

配置连接器后，可以设置工作流导入或导出到Campaign Classic。

![](assets/rtcdp-schema.png)

有关如何设置这些导入和导出流程的详细信息，请参阅以下部分：

* [将Adobe Experience Platform细分引入活动](../../integrations/using/ingest-aep-data.md)
* [将数据从活动导出到Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
