---
title: 创建Experience ManagerNewsletter
seo-title: 创建Experience ManagerNewsletter
description: 创建Experience ManagerNewsletter
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 1%

---


# Creating an Experience Manager newsletter{#creating-an-experience-manager-newsletter}

此集成可用于创建Adobe Experience Manager的新闻稿，然后在Adobe Campaign中作为电子邮件活动的一部分使用。

有关如何使用此集成的更详细示例，请参 [阅此分步指南](https://helpx.adobe.com/campaign/kb/acc-aem.html)。

**来自Adobe Experience Manager:**

1. 从AEM作者实例中，单 **击页面左上** 方的 **[!UICONTROL Sites]**“Adobe Experience”徽标，然后选择。

   ![](assets/aem_uc_1.png)

1. 选择 **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**。
1. 单击页 **[!UICONTROL Create]** 面右上角的按钮，然后选择 **[!UICONTROL Page]**。

   ![](assets/aem_uc_2.png)

1. 选择模 **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 板并命名新闻稿。
1. 创建页面后，访问菜 **[!UICONTROL Page information]** 单并单击 **[!UICONTROL Open Properties]**。

   ![](assets/aem_uc_3.png)

1. 在选 **[!UICONTROL Cloud Services]** 项卡中， **[!UICONTROL Adobe Campaign]** 在第二 **[!UICONTROL Cloud service configuration]** 个下拉列表中选择“作为”和您的Adobe Campaign实例。

   ![](assets/aem_uc_4.png)

1. 通过添加组件(例如来自Adobe Campaign的个性化字段)编辑电子邮件内容。
1. 电子邮件准备就绪后，访问 **[!UICONTROL Page information]** 菜单并单击 **[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_5.png)

1. 从第一个下拉框中，选择作为工 **[!UICONTROL Publish to Adobe Campaign]** 作流模型，然后单击 **[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_6.png)

1. 然后，作为上一步，启动工作 **[!UICONTROL Approve for Campaign]** 流。
1. 免责声明将显示在页面顶部。 单击 **[!UICONTROL Complete]** 以确认审阅，然后单击 **[!UICONTROL Ok]**。

   ![](assets/aem_uc_7.png)

1. 再次单 **[!UICONTROL Complete]** 击， **[!UICONTROL Newsletter approval]** 然后在下 **[!UICONTROL Next Step]** 拉框中选择。

   ![](assets/aem_uc_8.png)

您的新闻稿现已就绪，并且已在Adobe Campaign中同步。

**来自Adobe Campaign:**

1. From the **[!UICONTROL Campaigns]** tab, click **[!UICONTROL Deliveries]** then **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. 在下 **[!UICONTROL Delivery template]** 拉框中，选择模 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 板。

   ![](assets/aem_uc_10.png)

1. 向投放 **[!UICONTROL Label]** 中添加一个，然后单击 **[!UICONTROL Continue]**。
1. 单击 **[!UICONTROL Synchronize]** 按钮。

   如果此按钮未出现在您的界面中，请单击该 **[!UICONTROL Properties]** 按钮并选择选 **[!UICONTROL Advanced]** 项卡。 字 **[!UICONTROL Content editing mode]** 段应设置为字 **[!UICONTROL AEM]** 段中的AEM实例 **[!UICONTROL AEM account]** 。

   ![](assets/aem_uc_11.png)

1. 选择以前在Adobe Experience Manager创建的投放，然后单击 **[!UICONTROL Ok]**。
1. 对AEM **[!UICONTROL Refresh content]** 投放进行一些更改后，单击该按钮。

   ![](assets/aem_uc_12.png)

您的电子邮件现已准备好发送到受众。
