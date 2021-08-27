---
product: campaign
title: 创建Experience Manager新闻稿
description: 创建Experience Manager新闻稿
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 1%

---

# 创建Experience Manager新闻稿{#creating-an-experience-manager-newsletter}

![](../../assets/common.svg)

此集成可用于例如在Adobe Experience Manager中创建新闻稿，然后在Adobe Campaign中作为电子邮件促销活动的一部分使用。

有关如何使用此集成的更详细示例，请参阅此[分步指南](https://helpx.adobe.com/campaign/kb/acc-aem.html)。

**来自Adobe Experience Manager:**

1. 在您的AEM创作实例中，单击页面左上角的&#x200B;**Adobe Experience**&#x200B;徽标，然后选择&#x200B;**[!UICONTROL Sites]**。

   ![](assets/aem_uc_1.png)

1. 选择 **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**。
1. 单击页面右上方的&#x200B;**[!UICONTROL Create]**&#x200B;按钮，然后选择&#x200B;**[!UICONTROL Page]**。

   ![](assets/aem_uc_2.png)

1. 选择&#x200B;**[!UICONTROL Adobe Campaign Email (AC 6.1)]**&#x200B;模板并命名Newsletter。
1. 创建页面后，访问&#x200B;**[!UICONTROL Page information]**&#x200B;菜单，然后单击&#x200B;**[!UICONTROL Open Properties]**。

   ![](assets/aem_uc_3.png)

1. 在&#x200B;**[!UICONTROL Cloud Services]**&#x200B;选项卡的第二个下拉菜单中，选择&#x200B;**[!UICONTROL Adobe Campaign]**&#x200B;作为&#x200B;**[!UICONTROL Cloud service configuration]**，并选择Adobe Campaign实例。

   ![](assets/aem_uc_4.png)

1. 通过添加组件(例如Adobe Campaign中的个性化字段)来编辑电子邮件内容。
1. 电子邮件准备就绪后，访问&#x200B;**[!UICONTROL Page information]**&#x200B;菜单，然后单击&#x200B;**[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_5.png)

1. 从第一个下拉菜单中，选择&#x200B;**[!UICONTROL Publish to Adobe Campaign]**&#x200B;作为工作流模型，然后单击&#x200B;**[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_6.png)

1. 然后，像上一步一样，启动&#x200B;**[!UICONTROL Approve for Campaign]**&#x200B;工作流。
1. 免责声明将显示在页面顶部。 单击&#x200B;**[!UICONTROL Complete]**&#x200B;确认审阅，然后单击&#x200B;**[!UICONTROL Ok]**。

   ![](assets/aem_uc_7.png)

1. 再次单击&#x200B;**[!UICONTROL Complete]**&#x200B;并在&#x200B;**[!UICONTROL Next Step]**&#x200B;下拉菜单中选择&#x200B;**[!UICONTROL Newsletter approval]**。

   ![](assets/aem_uc_8.png)

您的新闻稿现已准备就绪，并可在Adobe Campaign中同步。

**来自Adobe Campaign:**

1. 在&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡中，依次单击&#x200B;**[!UICONTROL Deliveries]**&#x200B;和&#x200B;**[!UICONTROL Create]**。

   ![](assets/aem_uc_9.png)

1. 在&#x200B;**[!UICONTROL Delivery template]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL Email delivery with AEM content (mailAEMContent)]**&#x200B;模板。

   ![](assets/aem_uc_10.png)

1. 将&#x200B;**[!UICONTROL Label]**&#x200B;添加到投放中，然后单击&#x200B;**[!UICONTROL Continue]**。
1. 单击 **[!UICONTROL Synchronize]** 按钮。

   如果此按钮未显示在界面中，请单击&#x200B;**[!UICONTROL Properties]**&#x200B;按钮并选择&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡。 在&#x200B;**[!UICONTROL AEM account]**&#x200B;字段中，应将&#x200B;**[!UICONTROL Content editing mode]**&#x200B;字段设置为&#x200B;**[!UICONTROL AEM]**，并使用您的AEM实例。

   ![](assets/aem_uc_11.png)

1. 选择之前在Adobe Experience Manager中创建的投放，然后单击&#x200B;**[!UICONTROL Ok]**。
1. 对AEM投放进行某些更改后，请立即单击&#x200B;**[!UICONTROL Refresh content]**&#x200B;按钮。

   ![](assets/aem_uc_12.png)

您的电子邮件现已准备好发送给受众。
