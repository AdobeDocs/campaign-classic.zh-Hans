---
product: campaign
title: 开始使用轮廓
description: 在Adobe Campaign中使用用户档案
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: 471018f09e5a14635fcce07aeca1e2cf48d9144f
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 24%

---

# 开始使用轮廓{#about-profiles}



用户档案集中存储在Adobe Campaign数据库中。 有许多可能的机制可获取轮廓并创建此数据库：通过 Web 窗体在线收集、手动或自动导入文本文件、复制公司数据库或其他信息系统的内容。借助Adobe Campaign，您可以将营销历史、购买信息、偏好、CRM数据和任何相关的PI数据整合到一个整合视图中，以便进行分析并采取行动。

**用户档案**”是指代表最终客户、潜在客户或潜在客户的信息记录（例如：nmsRecipient表或外部表中的记录，包含cookie ID、客户ID、移动标识符或与特定渠道相关的其他信息）。

在 Adobe　Campaign 中，收件人是发送投放内容（电子邮件、短信等）所定位的默认轮廓。通过存储在数据库中的收件人数据，您可以筛选将接收任何给定投放的目标，并在投放内容中添加个性化数据。 数据库中还有其他类型的轮廓。这些用户档案是针对不同用途而设计的。例如，种子轮廓用于在将投放内容发送给最终目标前测试该投放内容。

![显示哪些配置文件及其工作方式的视频](assets/do-not-localize/how-to-video.png) [了解视频中配置文件的概念](#create-profiles-video)

>[!NOTE]
>
>要了解有关用户档案以及如何创建和编辑它们的更多信息，请参阅有关[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/audience/gs-audiences){target=_blank}的详细文档。

>[!BEGINTABS]

>[!TAB 配置文件文档]

要了解有关用户档案以及如何创建和编辑它们的更多信息，请参阅有关[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/audience/gs-audiences){target=_blank}的详细文档。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/audience/gs-audiences){target=_blank}

>[!TAB 创建和编辑用户档案]

请参阅Campaign v8文档以了解如何编辑、管理和添加用户档案：

* [添加配置文件](https://experienceleague.adobe.com/zh-hans/docs/campaign-classic/using/getting-started/profile-management/adding-profiles){target=_blank}：了解添加和创建新配置文件的关键步骤。
* [编辑配置文件](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/audience/view-profiles?lang=en#_blank){target=_blank}：查看和编辑现有配置文件。
* [管理配置文件](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/config/configuration/folders-and-views?lang=en#_blank){target=_blank}：使用文件夹管理工具访问和管理现有配置文件。

>[!TAB 导入/导出用户档案]

请参阅Campaign v8文档以了解如何导入和导出用户档案和数据：

* [导入用户档案](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/audience/add-profiles/import-profiles){target=_blank}：您可以使用工作流导入用户档案。
* [导入/导出数据](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/data/import){target=_blank}：了解如何使用通用导入/导出功能导入或导出数据和配置文件。

>[!ENDTABS]

<!--
## Profile types {#profile-types}

Adobe Campaign lets you manage profiles throughout their entire lifecycle: creation, import, targeting, action tracking, updates, etc.

Each profile matches a database entry. They contain all the information required for targeting, qualifying and tracking individuals.

Profiles can be identified based on storage space. This means that a profile can match: a recipient, a visitor, an operator, a subscriber, a prospect, etc.

## Recipient profiles {#recipient-profiles}

Delivery recipients are stored in the database as profiles containing the information linked to them: last name, first name, address, subscriptions, deliveries, etc. When you create campaigns, you can define the target of the deliveries to a selection of the profiles in the base according to simple or advanced criteria.

You can also create campaigns aimed at recipients whose profiles are stored not in the database, but in files. These are known as "external" deliveries. For more information about this type of delivery, refer to [this page](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

The main methods for creating recipient profiles are as follows:

* direct input in the graphical interface screens,
* importing recipient lists,
* on-line collection via web forms.

>[!NOTE]
>
>To find out how files and web forms are imported, refer to [Generic imports and exports](../../platform/using/get-started-data-import-export.md).

## Profiles and targets {#profiles-and-targets}

The **[!UICONTROL Profiles and targets]** link lets you display recipients stored in Adobe Campaign database. You can create new recipient, edit an existing recipient and access its profile. For more on this, refer to [this page](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

It also gives you access to:

* lists - [Learn more](../../platform/using/creating-and-managing-lists.md)
* subscription services - [Learn more](../../delivery/using/managing-subscriptions.md)
* web applications - [Learn more](../../web/using/about-web-applications.md)
* imports and exports (jobs) - [Learn more](../../platform/using/about-generic-imports-exports.md)
* targeting workflows - [Learn more](../../workflow/using/building-a-workflow.md#implementation-steps-)

The recipients page lets you perform frequent operations on profiles: edits, updates, adds, deletions, sorts.

For more advanced profile manipulations, you need to edit the Adobe Campaign tree. To do this, click the **[!UICONTROL Explorer]** link on the Adobe Campaign home page.

By default, recipients are stored in the **[!UICONTROL Profiles and Targets > Recipients]** node of the tree. You can create recipients from this view, as well as:

* sort and filter the profiles of the database - [Learn more](../../platform/using/filtering-options.md)
* move, copy or delete profiles from the database - [Learn more](../../platform/using/managing-profiles.md),
* update profiles - [Learn more](../../platform/using/updating-data.md)
* export recipients - [Learn more](../../platform/using/exporting-and-importing-profiles.md)
* create recipient groups - [Learn more](../../platform/using/creating-and-managing-lists.md)

To access advanced functionalities and configurations, you need to click the **[!UICONTROL Explorer]** icon. 

![](assets/d_ncs_user_interface01.png)

The general layout of the Adobe Campaign explorer is presented in [this page](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>You can also display an advanced view of this list from the Adobe Campaign tree by clicking the **[!UICONTROL Profiles and targets > Recipients]** link. The list display can be configured to suit your needs. You can add or delete columns, define column order, sort data, etc. List display configuration is described in [this page](../../platform/using/adobe-campaign-ui-lists.md).  
>
>You can also define recipient views. For further information about this functionality, refer to [this section](../../platform/using/access-management-folders.md).

## Active profiles {#active-profiles}

An active profile is a profile that customer has attempted to communicate with during the past 12 months via any channel.

According to your contract, each of your Campaign instances is provisioned with a specific amount of active profiles that are counted for billing purposes. Please refer to your latest contract for reference on number of purchased active profiles. Learn more in [Adobe Campaign product description](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

You can monitor the number of active profiles on your instance directly from Campaign Control Panel. For more on this, refer to the [Control Panel documentation](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html?lang=zh-Hans){target="_blank"}.

The following guardrails and limitations apply:

* A profile that has been targeted by several deliveries is counted only once. 
* Profiles targeted in the context of Social marketing on X (Twitter) or Facebook are not taken into account as active profiles.
* The count of active profiles is available for **Marketing instances** only. It is not available for Execution instances, meaning MID (mid sourcing) and RT (Message Center / Real-time messaging) instances.
* The count is based on the recipient primary key. As a consequence, if a profile is present in two different recipient tables, it can be counted twice as an active profile.


## Tutorial video {#create-profiles-video}

Learn how to access profile data, sort and filter profiles and manually create and manage profiles.

This video also explains the compliance of Adobe Campaign Classic with General Data Protection Regulations. 

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Additional Campaign Classic how-to videos are available [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).

**See also**

* [Privacy management in Campaign](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

* [Create queries and segment data in workflows](../../workflow/using/targeting-data.md)

* [Select target mapping](../../delivery/using/steps-defining-the-target-population.md#select-a-target-mapping)

-->