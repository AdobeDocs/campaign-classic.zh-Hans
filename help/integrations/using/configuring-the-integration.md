---
solution: Campaign Classic
product: campaign
title: 配置Adobe Experience Manager集成
description: 了解如何配置活动-AEM集成
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: a157082070b22e3621cb81411a5ddde387fd5fcf
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 2%

---


# 配置集成{#configuring-the-integration}

## 在Adobe Campaign{#configuring-in-adobe-campaign}中配置

要同时使用这两个解决方案，您必须配置它们以彼此连接。

请按照以下步骤开始Adobe Campaign中的配置：

1. [在Adobe Campaign中安装AEM集成包](#install-the-aem-integration-package-in-adobe-campaign)
1. [配置外部帐户](#configure-the-external-account)
1. [配置AEM资源筛选](#configure-aem-resources-filtering)

适用于高级配置，如管理个性化字段和块。 请参阅Adobe Experience Manager [文档](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)。

### 在Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}中安装AEM集成包

您首先需要安装&#x200B;**[!UICONTROL AEM integration]**&#x200B;包。

1. 从您的Adobe Campaign实例中，从上部工具栏中选择&#x200B;**[!UICONTROL Tools]**。
1. 选择 **[!UICONTROL Tools > Advanced > Import package...]**。

   ![](assets/aem_config_1.png)

1. 选择 **[!UICONTROL Install a standard package]**。
1. 选中&#x200B;**[!UICONTROL AEM integration]**，然后单击&#x200B;**[!UICONTROL Next]**&#x200B;按钮。

   ![](assets/aem_config_2.png)

1. 在下一个窗口中，单击&#x200B;**[!UICONTROL Start]**&#x200B;按钮以开始包的安装。 安装完成后，关闭窗口。

### 为AEM运算符{#configure-the-security-zone-for-aem-operator}配置安全区

**[!UICONTROL AEM integration]**&#x200B;包以活动设置&#x200B;**[!UICONTROL aemserver]**&#x200B;运算符。 此运算符将用于将Adobe Experience Manager服务器连接到Adobe Campaign。

您需要为此操作员配置一个安全区域，以便通过Adobe Experience Manager连接到Adobe Campaign。

>[!CAUTION]
>
>我们强烈建议创建专用于AEM的安全区，以避免任何安全问题。 有关详细信息，请参阅安装[指南](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

如果活动实例由Adobe托管，请联系[Adobe客户关怀团队](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 如果您使用的是内部部署活动，请执行以下步骤：

1. 打开&#x200B;**serverConf.xml**&#x200B;配置文件。
1. 访问所选安全区域的&#x200B;**allowUserPassword**&#x200B;属性，并将其设置为&#x200B;**true**。

   这将允许Adobe Experience Manager通过登录名/口令连接Adobe Campaign。

### 配置外部帐户{#configure-the-external-account}

**[!UICONTROL AEM integration]**&#x200B;包创建了Adobe Experience Cloud的外部帐户。 您现在需要配置它以与Adobe Experience Manager实例连接。

要混淆AEM外部帐户，请执行以下步骤：

1. 单击 **[!UICONTROL Explorer]** 按钮。

   ![](assets/aem_config_3.png)

1. 选择 **[!UICONTROL Administration > Platform > External accounts]**。
1. 在&#x200B;**[!UICONTROL External account]**&#x200B;列表中，选择&#x200B;**[!UICONTROL AEM instance]**。
1. 输入AEM创作实例的参数：

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >确保&#x200B;**[!UICONTROL Server]**&#x200B;地址不以尾随斜杠结尾。

   ![](assets/aem_config_4.png)

1. 选中&#x200B;**[!UICONTROL Enabled]**&#x200B;框。
1. 单击 **[!UICONTROL Save]** 按钮。

### 配置AEM资源筛选{#configure-aem-resources-filtering}

**AEMResourceTypeFilter**&#x200B;选项用于筛选可在Adobe Campaign中使用的Experience Manager资源类型。 这允许Adobe Campaign检索专门设计为仅用于Adobe Campaign的Experience Manager内容。

检查是否配置了&#x200B;**[!UICONTROL AEMResourceTypeFilter]**&#x200B;选项：

1. 单击 **[!UICONTROL Explorer]** 按钮。
1. 选择 **[!UICONTROL Administration > Platform > Options]**。
1. 在&#x200B;**[!UICONTROL Options]**&#x200B;列表中，选择&#x200B;**[!UICONTROL AEMResourceTypeFilter]**。
1. 在&#x200B;**[!UICONTROL Value (text)]**&#x200B;字段中，路径应如下所示：

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   或者在某些情况下：

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## 在Adobe Experience Manager中配置{#configuring-in-adobe-experience-manager}

请按照以下步骤开始Adobe Experience Manager中的配置：

1. 配置&#x200B;**replication**&#x200B;以从AEM创作实例复制到AEM发布实例。

   要了解如何配置复制，请参阅Adobe Experience Manager [文档](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)。

1. 在创作实例上安装集成&#x200B;**FeaturePack**，然后在发布实例上复制安装。 (仅限AEM 5.6.1和6.0版)。

   要了解如何安装FeaturePack，请参阅Adobe Experience Manager [文档](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)。

1. 通过配置专用的&#x200B;**Cloud Service**&#x200B;将Adobe Experience Manager连接到Adobe Campaign。

   要了解如何通过Cloud Services连接这两个解决方案，请参阅Adobe Experience Manager [文档](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager)。

1. 配置&#x200B;**Externalizer服务**。

   要了解如何配置它，请参阅Adobe Experience Manager [文档](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)。

