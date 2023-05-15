---
product: campaign
title: 将数据从 Campaign 导出到 Adobe Experience Platform
description: 了解如何将数据从Campaign Classic导出到Adobe Experience Platform
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: integrations
content-type: reference
exl-id: 8d1404c5-030b-47fe-a4c3-e72f15f09bbb
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 4%

---

# 将数据从 Campaign 导出到 Adobe Experience Platform {#sources}



要将Campaign Classic数据导出到Adobe Real-time Customer Data Platform(RTCDP)，您首先需要在Campaign Classic中构建一个工作流，以将要共享的数据导出到S3或Azure Blob存储位置。

配置工作流并将数据发送到您的存储位置后，您需要将S3或Azure Blob存储位置作为 **来源** Adobe体验平台中。

>[!NOTE]
>
>请注意，我们建议仅导出Campaign生成的数据（例如，发送、打开、点击等） Adobe Experience Platform。 从第三方源（如CRM）摄取的数据应直接导入Adobe Experience Platform。

## 在Campaign Classic中创建导出工作流

要将Campaign Classic中的数据导出到S3或Azure Blob存储位置，您需要构建一个工作流以定向要导出的数据并将其发送到您的存储位置。

为此，请添加和配置：

* 安 **[!UICONTROL Data extraction (file)]** 活动，以将目标数据提取到CSV文件。 有关如何配置此活动的更多信息，请参阅 [此部分](../../workflow/using/extraction--file-.md).

   ![](assets/rtcdp-extract-file.png)

* A **[!UICONTROL File transfer]** 活动，以将CSV文件传输到您的存储位置。 有关如何配置此活动的更多信息，请参阅 [此部分](../../workflow/using/file-transfer.md).

   ![](assets/rtcdp-file-transfer.png)

例如，以下工作流会定期将日志提取到CSV文件中，然后将文件传输到存储位置。

![](assets/aep-export.png)

## 作为源连接存储位置

将S3或Azure Blob存储位置作为 **来源** 在Experience Platform中，如下所示。 有关每个步骤的详细信息，请参阅 [源连接器文档](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=zh-Hans).

1. 在Adobe Experience Platform中 **[!UICONTROL Sources]** 菜单，请创建与存储位置的连接：

   * [创建Amazon S3源连接](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/s3.html)
   * [Azure Blob连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob.html)

   >[!NOTE]
   >
   >存储位置可以是Amazon S3、带密码的SFTP、带SSH密钥的SFTP或Azure Blob连接。 将数据发送到Adobe Campaign的首选方法是通过Amazon S3或Azure Blob:

   ![](assets/rtcdp-connector.png)

1. 为云存储批处理连接配置数据流。 数据流是一项计划任务，用于从存储位置检索数据并将其摄取到Adobe Experience Platform数据集。 此步骤允许您配置从存储位置摄取的数据，包括数据选择和CSV字段映射到XDM架构。

   有关详细信息可在 [本页](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html).

   ![](assets/rtcdp-map-xdm.png)

1. 配置源后，Adobe Experience Platform将从您提供的存储位置导入文件。

   此操作可以根据您的需求进行计划。 我们建议每天最多执行6次导出，具体取决于实例上已存在的负载。
