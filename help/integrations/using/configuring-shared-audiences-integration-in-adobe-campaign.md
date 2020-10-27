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
translation-type: tm+mt
source-git-commit: d567cb7dbc55d9c124d1cc83b7a5a9e2dfb5ab61
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 2%

---


# Configuring shared audiences integration in Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

提交此请求后，Adobe将继续为您提供集成，并与您联系以提供您必须完成配置的详细信息和信息：

1. [第1步：在Adobe Campaign中配置或检查外部帐户](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [第2步：配置数据源](#step-2--configure-the-data-source)
1. [第3步：配置活动跟踪服务器](#step-3--configure-campaign-tracking-server)
1. [第4步：配置访客ID服务](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>如果您使用demdex域并遵循 **ftp-out.demdex** .com语法导入外部帐户和 **** ftp-in.demdex.com外部帐户，则需要相应地调整实施并移至Amazon简单存储服务(S3)连接器以导入或导出数据。 有关如何使用AmazonS3配置外部帐户的详细信息，请参阅此 [部分](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)。

## 第1步：在Adobe Campaign中配置或检查外部帐户 {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

首先，我们需要按如下方式配置或检查Adobe Campaign中的外部帐户:

1. 单击该 **[!UICONTROL Explorer]** 图标。
1. 转到 **[!UICONTROL Administration > Platform > External accounts]**。 上述SFTP帐户应已按Adobe配置，并且必要的信息应已传达给您。

   * **[!UICONTROL importSharedAudience]**:专用于导入受众的帐户。
   * **[!UICONTROL exportSharedAudience]**:专用于导出受众的帐户。

   ![](assets/aam_config_1.png)

1. Select the **[!UICONTROL Export audiences to the Adobe Marketing Cloud]** external account.

1. From the **[!UICONTROL Type]** drop-down, select **[!UICONTROL AWS S3]**.

1. 提供以下详细信息：

   * **[!UICONTROL AWS S3 Account Server]**
服务器的URL，应按如下方式填写：

      ```
      <S3bucket name>.s3.amazonaws.com/<s3object path>
      ```

   * **[!UICONTROL AWS access key ID]**
要了解在何处找到您的AWS访问密钥ID，请参阅本 [页](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) 。

   * **[!UICONTROL Secret access key to AWS]**
要了解在何处找到AWS的秘密访问密钥，请参阅本 [页](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/)。

   * **[!UICONTROL AWS Region]**
要了解有关AWS区域的更多信息，请参阅本 [页](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)。
   ![](assets/aam_config_2.png)

1. 单 **[!UICONTROL Save]** 击并配置 **[!UICONTROL Import audiences from the Adobe Marketing Cloud]** 外部帐户，如前面的步骤所述。

您的外部帐户现已配置。

## Step 2: Configure the Data Source {#step-2--configure-the-data-source}

收件人 **-访客ID是在Audience Manager** 内创建的。 这是默认为访客ID配置的现成数据源。 从活动创建的区段将是此数据源的一部分。

要配置数 **[!UICONTROL Recipient - Visitor ID]** 据源：

1. From the **[!UICONTROL Explorer]** node, select **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. 选择 **[!UICONTROL Recipient - Visitor ID]**。
1. 输入Adobe **[!UICONTROL Data Source ID]** 提供 **[!UICONTROL AAM Destination ID]** 的和。

   ![](assets/aam_config_3.png)

## 第3步：配置活动跟踪服务器 {#step-3--configure-campaign-tracking-server}

要配置与People Core服务或受众管理器的集成，我们还需要配置活动跟踪服务器。

您需要确保活动跟踪服务器已注册到域(CNAME)。 您可以在本文中找到有关域名委托的更 [多信息](https://helpx.adobe.com/cn/campaign/kb/domain-name-delegation.html)。

## 第4步：配置访客ID服务 {#step-4--configure-the-visitor-id-service}

如果您的访客ID服务从未在您的Web属性或网站上配置过，请参阅以下 [文档](https://docs.adobe.com/content/help/en/id-service/using/implementation/setup-aam-analytics.html) ，了解如何配置服务或以下 [视频](https://helpx.adobe.com/cn/marketing-cloud/how-to/email-marketing.html#step-two) 。

您的配置和配置已完成，集成现在可用于导入和导出受众或区段。
