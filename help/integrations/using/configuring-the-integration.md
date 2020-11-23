---
solution: Campaign Classic
product: campaign
title: 配置Adobe Experience Manager集成
description: 了解如何配置活动-AEM集成
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 2%

---


# 配置集成{#configuring-the-integration}

## Configuring in Adobe Campaign {#configuring-in-adobe-campaign}

要同时使用这两个解决方案，您必须配置它们以彼此连接。

按照以下步骤开始Adobe Campaign中的配置：

1. [以Adobe Campaign安装AEM集成包](#install-the-aem-integration-package-in-adobe-campaign)
1. [配置外部帐户](#configure-the-external-account)
1. [配置AEM资源筛选](#configure-aem-resources-filtering)

适用于高级配置，如管理个性化字段和块。 请参阅Adobe Experience Manager [文档](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)。

### 以Adobe Campaign安装AEM集成包 {#install-the-aem-integration-package-in-adobe-campaign}

您首先需要安装该 **[!UICONTROL AEM integration]** 包。

1. 在Adobe Campaign实例中，从上 **[!UICONTROL Tools]** 方工具栏中选择。
1. 选择 **[!UICONTROL Tools > Advanced > Import package...]**。

   ![](assets/aem_config_1.png)

1. 选择 **[!UICONTROL Install a standard package]**。
1. 选中 **[!UICONTROL AEM integration]** ，然后单击 **[!UICONTROL Next]** 按钮。

   ![](assets/aem_config_2.png)

1. 在下一个窗口中，单 **[!UICONTROL Start]** 击按钮以开始包的安装。 安装完成后，关闭窗口。

### 为AEM操作员配置安全区 {#configure-the-security-zone-for-aem-operator}

包 **[!UICONTROL AEM integration]** 以活动 **[!UICONTROL aemserver]** 设置运算符。 此运算符将用于将Adobe Experience Manager服务器连接到Adobe Campaign。

您需要为此操作员配置一个安全区，以通过Adobe Experience Manager连接到Adobe Campaign。

>[!CAUTION]
>
>我们强烈建议创建专用于AEM的安全区，以避免出现任何安全问题。 For more on this, refer to the Installation [guide](../../installation/using/configuring-campaign-server.md#defining-security-zones).

如果活动实例由Adobe托管，请与Adobe支持团队联系。 如果您使用活动内部部署，请按照以下步骤操作：

1. 打开 **serverConf.xml** 配置文件。
1. 访问选 **定安全区** 的allowUserPassword属性，并将其设置为 **true**。

   这将允许Adobe Experience Manager通过登录名／口令连接Adobe Campaign。

### 配置外部帐户 {#configure-the-external-account}

该包 **[!UICONTROL AEM integration]** 为Adobe Experience Cloud创建了外部帐户。 您现在需要配置它以与您的Adobe Experience Manager实例连接。

要混淆AEM外部帐户，请执行以下步骤：

1. 单击 **[!UICONTROL Explorer]** 按钮。

   ![](assets/aem_config_3.png)

1. 选择 **[!UICONTROL Administration > Platform > External accounts]**。
1. From the **[!UICONTROL External account]** list, select **[!UICONTROL AEM instance]**.
1. 输入AEM创作实例的参数：

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >确保您的地 **[!UICONTROL Server]** 址不以尾随斜杠结尾。

   ![](assets/aem_config_4.png)

1. 选中 **[!UICONTROL Enabled]** 框。
1. 单击 **[!UICONTROL Save]** 按钮。

### 配置AEM资源筛选 {#configure-aem-resources-filtering}

AEMR **esourceTypeFilter** 选项用于筛选可用于Adobe Campaign的Experience Manager资源类型。 这允许Adobe Campaign检索专门设计用于Adobe Campaign的Experience Manager内容。

要检查选项是 **[!UICONTROL AEMResourceTypeFilter]** 否已配置：

1. 单击 **[!UICONTROL Explorer]** 按钮。
1. 选择 **[!UICONTROL Administration > Platform > Options]**。
1. From the **[!UICONTROL Options]** list, select **[!UICONTROL AEMResourceTypeFilter]**.
1. 在字 **[!UICONTROL Value (text)]** 段中，路径应如下所示：

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   或者在某些情况下：

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## 在Adobe Experience Manager配置 {#configuring-in-adobe-experience-manager}

请按照以下步骤开始Adobe Experience Manager的配置：

1. 将复制 **配置为** 从AEM创作实例复制到AEM发布实例。

   要了解如何配置复制，请参阅Adobe Experience Manager [文档](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)。

1. 在创作实 **例上安装** FeaturePack集成，然后在发布实例上复制安装。 (仅适用于AEM 5.6.1和6.0版)。

   要了解如何安装FeaturePack，请参阅Adobe Experience Manager [文档](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)。

1. 通过配置专用Adobe Experience Manager将Cloud Service连接到 **Adobe Campaign**。

   要了解如何通过Cloud Services连接两种解决方案，请参阅Adobe Experience Manager [文档](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) 。

1. 配置 **Externalizer服务**。

   要了解如何配置，请参阅Adobe Experience Manager [文档](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)。

