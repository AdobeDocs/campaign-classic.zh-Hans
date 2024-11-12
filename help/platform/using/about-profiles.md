---
product: campaign
title: 开始使用配置文件
description: 在Adobe Campaign中使用用户档案
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 33%

---

# 开始使用配置文件{#about-profiles}



用户档案集中存储在Adobe Campaign数据库中。 有许多可能的机制可获取用户档案并创建此数据库：通过 Web 窗体在线收集、手动或自动导入文本文件、复制公司数据库或其他信息系统的内容。借助Adobe Campaign，您可以将营销历史、购买信息、偏好、CRM数据和任何相关的PI数据整合到一个整合视图中，以便进行分析并采取行动。

**用户档案**”是指代表最终客户、潜在客户或潜在客户的信息记录（例如：nmsRecipient表或外部表中的记录，包含cookie ID、客户ID、移动标识符或与特定渠道相关的其他信息）。

在 Adobe　Campaign 中，收件人是发送投放内容（电子邮件、短信等）所定位的默认用户档案。通过存储在数据库中的收件人数据，您可以筛选将接收任何给定投放的目标，并在投放内容中添加个性化数据。 数据库中还有其他类型的用户档案。这些用户档案是针对不同用途而设计的。例如，种子用户档案用于在将投放内容发送给最终目标前测试该投放内容。

![](assets/do-not-localize/how-to-video.png) [了解视频中配置文件的概念](#create-profiles-video)

## 用户档案类型 {#profile-types}

您可以使用 Adobe Campaign 管理用户档案的整个生命周期：创建、导入、定位、操作跟踪、更新等。

每个概要文件都与一个数据库条目匹配。 其中包含了定位、限定和跟踪个人所需的所有必要信息。

可以根据存储空间识别配置文件。 这意味着配置文件可以匹配：收件人、访客、操作员、订阅者、潜在客户等。

## 收件人用户档案 {#recipient-profiles}

投放工作的收件人会以用户档案的形式存储在数据库中，并包含其所链接的信息，如姓氏、名字、地址、订阅、投放项目等。创建活动时，可以根据简单或高级标准从数据库中选定投放工作的目标客户。

您还可以创建针对其用户档案存储在数据库中而非文件中的收件人的营销活动。 这些称为“外部”投放。 如需有关此类投放的详细信息，请参阅[此页面](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)。

创建收件人用户档案的主要方法如下：

* 在图形界面屏幕中直接输入、
* 导入收件人列表、
* 通过 Web 窗体在线收集。

>[!NOTE]
>
>要了解文件和Web窗体的导入方式，请参阅[通用导入和导出](../../platform/using/get-started-data-import-export.md)。

## 用户档案和目标 {#profiles-and-targets}

通过&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;链接，可显示存储在Adobe Campaign数据库中的收件人。 您可以创建新收件人、编辑现有收件人并访问其配置文件。 有关详细信息，请参见[此页面](../../platform/using/editing-a-profile.md)。

![](assets/d_ncs_user_interface_target_link.png)

您还可以通过它访问：

* 列表 — [了解详情](../../platform/using/creating-and-managing-lists.md)
* 订阅服务 — [了解详情](../../delivery/using/managing-subscriptions.md)
* Web应用程序 — [了解更多](../../web/using/about-web-applications.md)
* 导入和导出（作业） - [了解详情](../../platform/using/about-generic-imports-exports.md)
* 定位工作流 — [了解详情](../../workflow/using/building-a-workflow.md#implementation-steps-)

收件人页面允许您对用户档案执行常见的操作：编辑、更新、添加、删除、排序。

如需进行更高级的配置文件操作，您需要编辑Adobe Campaign树。 为此，请单击Adobe Campaign主页上的&#x200B;**[!UICONTROL Explorer]**&#x200B;链接。

默认情况下，收件人存储在树的&#x200B;**[!UICONTROL Profiles and Targets > Recipients]**&#x200B;节点中。 您可通过此视图创建收件人，以及：

* 对数据库的配置文件进行排序和筛选 — [了解更多](../../platform/using/filtering-options.md)
* 从数据库中移动、复制或删除配置文件 — [了解更多](../../platform/using/managing-profiles.md)，
* 更新配置文件 — [了解详情](../../platform/using/updating-data.md)
* 导出收件人 — [了解详情](../../platform/using/exporting-and-importing-profiles.md)
* 创建收件人组 — [了解更多](../../platform/using/creating-and-managing-lists.md)

要访问高级功能和配置，您需要单击&#x200B;**[!UICONTROL Explorer]**&#x200B;图标。

![](assets/d_ncs_user_interface01.png)

Adobe Campaign资源管理器的常规布局显示在[此页面](../../platform/using/adobe-campaign-explorer.md)中。

>[!NOTE]
>
>您还可以通过单击&#x200B;**[!UICONTROL Profiles and targets > Recipients]**&#x200B;链接从Adobe Campaign树中显示此列表的高级视图。 列表显示可以根据您的需求进行配置。 您可以添加或删除列、定义列顺序、对数据排序等。 列表显示配置在[此页面](../../platform/using/adobe-campaign-ui-lists.md)中描述。
>
>您还可以定义收件人视图。 有关此功能的详细信息，请参阅[此部分](../../platform/using/access-management-folders.md)。

## 使用中的用户档案 {#active-profiles}

活动用户档案是客户在过去12个月内尝试通过任何渠道与之通信的用户档案。

根据您的合同，您的每个 Campaign 实例都会配置特定数量的活动用户档案，并对这些活动用户档案进行计数以计费。请参阅您的最新合同，了解已购买的活动用户档案的数量。 在[Adobe Campaign产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}中了解详情。

您可以直接从Campaign控制面板监控实例上的活动用户档案数。 有关详细信息，请参阅[控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html){target="_blank"}。

以下护栏和限制适用：

* 被多次投放定向的用户档案只会被计数一次。
* 在X(Twitter)或Facebook的社交营销上下文中定位的用户档案不会计为活动用户档案。
* 活动用户档案的计数仅适用于&#x200B;**营销实例**。 它不适用于执行实例，即MID （中间源）和RT （消息中心/实时消息传递）实例。
* 计数基于收件人主键。 因此，如果某个用户档案存在于两个不同的收件人表中，则它可能会被计算为活动用户档案两次。


## 教程视频 {#create-profiles-video}

了解如何访问用户档案数据、对用户档案进行排序和筛选以及手动创建和管理用户档案。

此视频还介绍了Adobe Campaign Classic对《一般数据保护条例》的合规性。

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他Campaign Classic操作方法视频。

**另请参阅**

* Campaign中的[隐私管理](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)

* [在工作流中创建查询和区段数据](../../workflow/using/targeting-data.md)

* [选择目标映射](../../delivery/using/selecting-a-target-mapping.md)
