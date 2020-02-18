---
title: 配置集成
seo-title: 配置集成
description: 配置集成
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 31f30db6eaf1fee43f9f757124e3fa8ed1d0075f

---


# Configuring the integration{#configuring-the-integration}

## 在Adobe Campaign中配置 {#configuring-in-adobe-campaign}

要同时使用这两个解决方案，您必须将它们配置为彼此连接。

请按照以下步骤在Adobe Campaign中启动配置：

1. [在Adobe Campaign中安装AEM集成包](#install-the-aem-integration-package-in-adobe-campaign)
1. [配置外部帐户](#configure-the-external-account)
1. [配置AEM资源筛选](#configure-aem-resources-filtering)

适用于高级配置，如管理个性化字段和块。 请参阅Adobe Experience manager文 [档](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)。

### 在Adobe Campaign中安装AEM集成包 {#install-the-aem-integration-package-in-adobe-campaign}

您首先需要安装该 **[!UICONTROL AEM integration]** 包。

1. 从您的Adobe Campaign实例中，从上 **[!UICONTROL Tools]** 方工具栏中选择。
1. Select **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Select **[!UICONTROL Install a standard package]**.
1. 选中 **[!UICONTROL AEM integration]** ，然后单击 **[!UICONTROL Next]** 按钮。

   ![](assets/aem_config_2.png)

1. 在下一个窗口中，单 **[!UICONTROL Start]** 击按钮以开始安装包。 安装完成后，关闭窗口。

### 为AEM运营商配置安全区 {#configure-the-security-zone-for-aem-operator}

该包 **[!UICONTROL AEM integration]** 会在Campaign中设 **[!UICONTROL aemserver]** 置运算符。 此运营商将用于将Adobe Experience Manager服务器连接到Adobe Campaign。

您需要为此运营商配置安全区，以便通过Adobe Experience Manager连接到Adobe Campaign。

>[!CAUTION]
>
>我们强烈建议创建专用于AEM的安全区，以避免任何安全问题。 有关详细信息，请参阅安装 [指南](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

如果您的Campaign实例由Adobe托管，请与Adobe支持团队联系。 如果您使用的是营销活动内部部署，请执行以下步骤：

1. 打开 **serverConf.xml配置文件** 。
1. 访问选 **定安全区域的allowUserPassword** 属性，并将其设置为 **true**。

   这将允许Adobe Experience Manager通过登录名／密码连接Adobe Campaign。

### 配置外部帐户 {#configure-the-external-account}

该包 **[!UICONTROL AEM integration]** 创建了Adobe Experience cloud的外部帐户。 您现在需要配置它以与Adobe Experience manager实例连接。

要混淆AEM外部帐户，请执行以下步骤：

1. Click the **[!UICONTROL Explorer]** button.

   ![](assets/aem_config_3.png)

1. Select **[!UICONTROL Administration > Platform > External accounts]**.
1. 从列表 **[!UICONTROL External account]** 中，选择 **[!UICONTROL AEM instance]**。
1. 输入AEM创作实例的参数：

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**
   >[!NOTE]
   >
   >确保您的地 **[!UICONTROL Server]** 址不以尾随斜杠结尾。

   ![](assets/aem_config_4.png)

1. 选中 **[!UICONTROL Enabled]** 框。
1. Click the **[!UICONTROL Save]** button.

### 配置AEM资源筛选 {#configure-aem-resources-filtering}

AEMResourceTypeFilter **** 选项用于过滤Experience manager资源的类型，这些资源可用于Adobe Campaign。 这允许Adobe Campaign检索专门设计用于Adobe Campaign的Experience manager内容。

要检查选项是否 **[!UICONTROL AEMResourceTypeFilter]** 已配置：

1. Click the **[!UICONTROL Explorer]** button.
1. Select **[!UICONTROL Administration > Platform > Options]**.
1. 从列表 **[!UICONTROL Options]** 中，选择 **[!UICONTROL AEMResourceTypeFilter]**。
1. 在字 **[!UICONTROL Value (text)]** 段中，路径应如下：

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   或者在某些情况下：

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## 在Adobe Experience manager中配置 {#configuring-in-adobe-experience-manager}

请按照以下步骤在Adobe Experience Manager中启动配置：

1. 配置复 **制** ，以从AEM创作实例复制到AEM发布实例。

   要了解如何配置复制，请参阅Adobe Experience manager文 [档](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)。

1. 在创作实 **例上安装集成FeaturePack** ，然后在发布实例上复制安装。 （仅限AEM版本5.6.1和6.0）。

   要了解如何安装FeaturePack，请参阅Adobe Experience manager文 [档](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)。

1. 通过配置专用云服务，将Adobe Experience manager连接到Adobe **Campaign**。

   要了解如何通过云服务连接这两个解决方案，请参阅Adobe Experience manager文 [档](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) 。

1. 配置 **Externalizer服务**。

   要了解如何配置它，请参阅Adobe Experience manager文 [档](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)。

