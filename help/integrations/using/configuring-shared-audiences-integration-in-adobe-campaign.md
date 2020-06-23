---
title: 在Adobe Campaign中配置共享受众集成
seo-title: 在Adobe Campaign中配置共享受众集成
description: 在Adobe Campaign中配置共享受众集成
seo-description: null
page-status-flag: never-activated
uuid: 6ed137e4-027f-4eb0-a0b5-4beb7deef51f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 4443b0ca-80c6-467d-a4df-50864aae8496
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c3737b22c7bf4e614c5a2fbe8e8fd954d3ece8a
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---


# 在Adobe Campaign中配置共享受众集成{#configuring-shared-audiences-integration-in-adobe-campaign}

提交此请求后，Adobe将继续为您提供集成，并与您联系以提供您必须完成配置的详细信息和信息：

1. [第1步： 在Adobe Campaign中配置或检查外部帐户](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [第2步： 配置数据源](#step-2--configure-the-data-source)
1. [第3步： 配置活动跟踪服务器](#step-3--configure-campaign-tracking-server)
1. [第4步： 配置访客ID服务](#step-4--configure-the-visitor-id-service)

## 第1步： 在Adobe Campaign中配置或检查外部帐户 {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

首先，我们需要按如下方式配置或检查Adobe Campaign中的外部帐户:

1. 单击该 **[!UICONTROL Explorer]** 图标。
1. 转到 **[!UICONTROL Administration > Platform > External accounts]**。 上述SFTP帐户应由Adobe配置，并且必要的信息应已传达给您。

   * **[!UICONTROL importSharedAudience]** : 专用于导入受众的SFTP帐户。
   * **[!UICONTROL exportSharedAudience]** : 专用于导出受众的SFTP帐户。
   ![](assets/aam_config_1.png)

1. 填写字 **[!UICONTROL Server]** 段： **ftp-out.demdex.com域** (用于导入外部帐户) **和ftp-in.demdex.com域(** 用于导出外部帐户)。

   请记住，从活动导出是Audience Manager或人员核心服务的导入。

   >[!NOTE]
   >
   >如果您使用S3，请输入以 **[!UICONTROL AWS S3 Account Server]** 下语法：\
   `<S3bucket name>.s3.amazonaws.com/<s3object path>`\
   有关如何配置S3帐户的详细信息，请参阅此 [页](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account)。

   ![](assets/aam_config_2.png)

1. 添加Adobe **[!UICONTROL Account]** 提供 **[!UICONTROL Password]** 的和由Adobe提供的。

您的外部帐户现已配置。

## Step 2: Configure the Data Source {#step-2--configure-the-data-source}

收件人 **-访客ID是在Audience Manager** 内创建的。 这是默认为访客ID配置的现成数据源。 从活动创建的区段将是此数据源的一部分。

要配置数 **[!UICONTROL Recipient - Visitor ID]** 据源：

1. 从节 **[!UICONTROL Explorer]** 点中选择 **[!UICONTROL Administration > Platform > AMC Data sources]**。
1. Select **[!UICONTROL Recipient - Visitor ID]**.
1. 输入 **[!UICONTROL Data Source ID]** Adobe **[!UICONTROL AAM Destination ID]** 提供的和。

   ![](assets/aam_config_3.png)

## 第3步： 配置活动跟踪服务器 {#step-3--configure-campaign-tracking-server}

要配置与People Core服务或受众管理器的集成，我们还需要配置活动跟踪服务器。

您需要确保活动跟踪服务器已注册到域(CNAME)。 您可以在本文中找到有关域名委托的更 [多信息](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)。

## 第4步： 配置访客ID服务 {#step-4--configure-the-visitor-id-service}

如果您的访客ID服务从未在您的Web属性或网站上配置过，请参阅以下 [文档](https://docs.adobe.com/content/help/en/id-service/using/implementation/setup-aam-analytics.html) ，了解如何配置服务或以下 [视频](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) 。

您的配置和配置已完成，该集成现在可用于导入和导出受众或区段。
