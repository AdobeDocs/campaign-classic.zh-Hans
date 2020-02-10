---
title: 创建Experience Manager新闻快讯
seo-title: 创建Experience Manager新闻快讯
description: 创建Experience Manager新闻快讯
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 创建Experience Manager新闻快讯{#creating-an-experience-manager-newsletter}

此集成可用于在Adobe Experience manager中创建新闻稿，然后在Adobe Campaign中将该新闻稿用作电子邮件营销活动的一部分。

有关如何使用此集成的更详细示例，请参阅 [此分步指南](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/aem.html)。

**从Adobe Experience Manager:**

1. 在您的AEM作者实例中，单击页面左上角的 **Adobe Experience** 徽标，然后选择 **[!UICONTROL Sites]**。

   ![](assets/aem_uc_1.png)

1. Select **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Master Area > Email campaigns]**.
1. 单击 **[!UICONTROL Create]** 页面右上方的按钮，然后选择 **[!UICONTROL Page]**。

   ![](assets/aem_uc_2.png)

1. 选择模 **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 板并命名新闻稿。
1. 创建页面后，访问菜 **[!UICONTROL Page information]** 单并单击 **[!UICONTROL Open Properties]**。

   ![](assets/aem_uc_3.png)

1. 在选 **[!UICONTROL Cloud Services]** 项卡中，选 **[!UICONTROL Adobe Campaign]** 择作 **[!UICONTROL Cloud service configuration]** 为，然后在第二个下拉框中选择您的Adobe Campaign实例。

   ![](assets/aem_uc_4.png)

1. 通过添加组件（例如Adobe Campaign中的个性化字段）来编辑电子邮件内容。
1. 电子邮件准备就绪后，访问 **[!UICONTROL Page information]** 菜单并单击 **[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_5.png)

1. 从第一个下拉列表中，选择作为 **[!UICONTROL Publish to Adobe Campaign]** 工作流模型，然后单击 **[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_6.png)

1. 然后，作为上一步，启动工作 **[!UICONTROL Approve for Campaign]** 流。
1. 免责声明显示在页面顶部。 单击 **[!UICONTROL Complete]** 以确认审阅，然后单击 **[!UICONTROL Ok]**。

   ![](assets/aem_uc_7.png)

1. 再次单 **[!UICONTROL Complete]** 击并 **[!UICONTROL Newsletter approval]** 在下拉 **[!UICONTROL Next Step]** 框中选择。

   ![](assets/aem_uc_8.png)

您的新闻稿现已在Adobe Campaign中准备就绪并同步。

**从Adobe Campaign:**

1. 在选项 **[!UICONTROL Campaigns]** 卡中，单 **[!UICONTROL Deliveries]** 击 **[!UICONTROL Create]**。

   ![](assets/aem_uc_9.png)

1. 在下 **[!UICONTROL Delivery template]** 拉框中，选择模 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 板。

   ![](assets/aem_uc_10.png)

1. 在您的 **[!UICONTROL Label]** 分发中添加并单击 **[!UICONTROL Continue]**。
1. Click the **[!UICONTROL Synchronize]** button.

   如果此按钮未出现在您的界面中，请单击该按 **[!UICONTROL Properties]** 钮并选择该选 **[!UICONTROL Advanced]** 项卡。 字 **[!UICONTROL Content editing mode]** 段中的字段应 **[!UICONTROL AEM]** 当设置为与AEM实例一起使 **[!UICONTROL AEM account]** 用。

   ![](assets/aem_uc_11.png)

1. 选择之前在Adobe Experience Manager中创建的分发，然后单击 **[!UICONTROL Ok]**。
1. 对AEM **[!UICONTROL Refresh content]** 交付进行某些更改后，请立即单击按钮。

   ![](assets/aem_uc_12.png)

您的电子邮件现已准备好发送给您的受众。
