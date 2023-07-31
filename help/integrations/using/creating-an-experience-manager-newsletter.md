---
product: campaign
title: 创建Experience Manager新闻稿
description: 创建Experience Manager新闻稿
feature: Experience Manager Integration
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 2%

---

# 创建Experience Manager新闻稿{#creating-an-experience-manager-newsletter}



例如，此集成可用于在Adobe Experience Manager中创建新闻稿，然后在Adobe Campaign中将其用作电子邮件营销活动的一部分。

**从Adobe Experience Manager：**

1. 在您的AEM创作实例中，单击 **Adobe Experience** 徽标，然后选择 **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. 选择 **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**。
1. 单击 **[!UICONTROL Create]** 按钮，然后选择 **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. 选择 **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 模板和命名您的新闻稿。
1. 创建页面后，访问 **[!UICONTROL Page information]** 菜单并单击 **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. 在 **[!UICONTROL Cloud Services]** 选项卡，选择 **[!UICONTROL Adobe Campaign]** 作为 **[!UICONTROL Cloud service configuration]** 和您的Adobe Campaign实例。

   ![](assets/aem_uc_4.png)

1. 通过添加组件(例如Adobe Campaign中的个性化字段)编辑电子邮件内容。
1. 当您的电子邮件准备就绪时，访问 **[!UICONTROL Page information]** 菜单并单击 **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. 从第一个下拉菜单中，选择 **[!UICONTROL Publish to Adobe Campaign]** 作为工作流模型，然后单击 **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. 然后，在上一步中，启动 **[!UICONTROL Approve for Campaign]** 工作流。
1. 免责声明将显示在页面顶部。 单击 **[!UICONTROL Complete]** 要确认审阅并单击 **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. 再次单击 **[!UICONTROL Complete]** 并选择 **[!UICONTROL Newsletter approval]** 在 **[!UICONTROL Next Step]** 下拉菜单。

   ![](assets/aem_uc_8.png)

您的新闻稿现已准备就绪，并已在Adobe Campaign中同步。

**从Adobe Campaign：**

1. 从 **[!UICONTROL Campaigns]** 选项卡，单击 **[!UICONTROL Deliveries]** 则 **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. 在 **[!UICONTROL Delivery template]** 下拉列表，选择 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 模板。

   ![](assets/aem_uc_10.png)

1. 添加 **[!UICONTROL Label]** 到您的投放，然后单击 **[!UICONTROL Continue]**.
1. 单击 **[!UICONTROL Synchronize]** 按钮。

   如果界面中未出现此按钮，请单击 **[!UICONTROL Properties]** 按钮并选择 **[!UICONTROL Advanced]** 选项卡。 此 **[!UICONTROL Content editing mode]** 字段应设置为 **[!UICONTROL AEM]** 将您的AEM实例放在 **[!UICONTROL AEM account]** 字段。

   ![](assets/aem_uc_11.png)

1. 选择之前在Adobe Experience Manager中创建的投放并单击 **[!UICONTROL Ok]**.
1. 单击 **[!UICONTROL Refresh content]** 对AEM投放做出更改后立即按钮。

   ![](assets/aem_uc_12.png)

您的电子邮件现已准备就绪，可发送给受众。
