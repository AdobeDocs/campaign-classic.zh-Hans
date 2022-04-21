---
product: campaign
title: 关于用户档案
description: 关于用户档案
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: fdb840a9e6349f074378899e07f794b62fb5b054
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 61%

---

# 开始使用用户档案{#about-profiles}

![](../../assets/v7-only.svg)

用户档案将集中在Adobe Campaign数据库中。 有许多可能的机制可获取用户档案并创建此数据库：通过 Web 窗体在线收集、手动或自动导入文本文件、复制公司数据库或其他信息系统的内容。借助Adobe Campaign，您可以整合营销历史、购买信息、偏好、CRM数据以及整合视图中任何相关的PI数据，以便进行分析并采取行动。

“**用户档案**”是指代表最终客户或潜在客户的信息记录（例如 nmsRecipient 表或外部表中的记录，包含 cookie ID、客户 ID、移动标识符或与特定渠道相关的其他信息）。

在 Adobe　Campaign 中，收件人是发送投放内容（电子邮件、SMS 等）所定位的默认用户档案。通过数据库中存储的收件人数据，您可以筛选将接收任何给定投放的目标，并在投放内容中添加个性化数据。 数据库中还有其他类型的用户档案。这些用户档案是针对不同用途而设计的。例如，种子用户档案用于在将投放内容发送给最终目标前测试该投放内容。

![](assets/do-not-localize/how-to-video.png) [了解视频中用户档案的概念](#create-profiles-video)

## 用户档案类型 {#profile-types}

您可以使用 Adobe Campaign 管理用户档案的整个生命周期：创建、导入、定位、操作跟踪、更新等。

每个用户档案都对应一个数据库条目。其中包含了定位、限定和跟踪个人所需的所有必要信息。

可根据存储空间来识别用户档案。这意味着可根据收件人、访客、操作员、订阅者、潜在客户等来识别用户档案。

## 收件人用户档案 {#recipient-profiles}

投放工作的收件人会以用户档案的形式存储在数据库中，并包含其所链接的信息，如姓氏、名字、地址、订阅、投放项目等。创建活动时，可以根据简单或高级标准从数据库中选定投放工作的目标客户。

也可以针对其用户档案存储于文件（而非数据库）中的收件人创建活动。这些称为“外部”投放。如需有关此类投放的详细信息，请参阅[此页面](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)。

创建收件人用户档案的主要方法如下：

* 在图形界面屏幕中直接输入、
* 导入收件人列表、
* 通过 Web 窗体在线收集。

>[!NOTE]
>
>要了解如何导入文件和Web窗体，请参阅 [一般导入和导出](../../platform/using/get-started-data-import-export.md).

## 用户档案和目标 {#profiles-and-targets}

的 **[!UICONTROL Profiles and targets]** 利用链接，可显示存储在Adobe Campaign数据库中的收件人。 您可以创建新的收件人、编辑现有的收件人以及访问其用户档案。有关详细信息，请参见[此页面](../../platform/using/editing-a-profile.md)。

![](assets/d_ncs_user_interface_target_link.png)

您还可以通过它访问：

* 列表 —  [了解更多](../../platform/using/creating-and-managing-lists.md)
* 订阅服务 —  [了解更多](../../delivery/using/managing-subscriptions.md)
* web应用程序 —  [了解更多](../../web/using/about-web-applications.md)
* 进出口（作业） —  [了解更多](../../platform/using/about-generic-imports-exports.md)
* 定位工作流 —  [了解更多](../../workflow/using/building-a-workflow.md#implementation-steps-)

收件人页面允许您对用户档案执行常见的操作：编辑、更新、添加、删除、排序。

如需更多高级用户档案操作，您需要编辑 Adobe Campaign 树状结构。为此可单击 Adobe Campaign 主页上的 **[!UICONTROL Explorer]** 链接。

默认情况下，收件人存储在 **[!UICONTROL Profiles and Targets > Recipients]** 树的节点。 您可通过此视图创建收件人，以及：

* 对数据库的用户档案进行排序和筛选 —  [了解更多](../../platform/using/filtering-options.md)
* 从数据库中移动、复制或删除用户档案 —  [了解更多](../../platform/using/managing-profiles.md),
* 更新用户档案 —  [了解更多](../../platform/using/updating-data.md)
* 导出收件人 —  [了解更多](../../platform/using/exporting-and-importing-profiles.md)
* 创建收件人组 —  [了解更多](../../platform/using/creating-and-managing-lists.md)

要访问各种高级功能和配置，需单击 **[!UICONTROL Explorer]** 图标。

![](assets/d_ncs_user_interface01.png)

Adobe Campaign资源管理器的常规布局在 [本页](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>也可以单击 **[!UICONTROL Profiles and targets > Recipients]** 链接，从 Adobe Campaign 树状结构中显示该列表的高级视图。可根据您的需求配置列表的显示。您可以添加或删除列、定义列顺序、对数据进行排序等。 列表显示配置在 [本页](../../platform/using/adobe-campaign-ui-lists.md).
>
>您也可以定义收件人视图。有关此功能的更多信息，请参阅 [此部分](../../platform/using/access-management-folders.md).

## 使用中的用户档案 {#active-profiles}

使用中的用户档案是指可计费开立账单的用户档案。

计费账单的开立仅会考虑&#x200B;**使用中**&#x200B;的用户档案。如果用户档案在过去 12 个月通过任何渠道被定位或进行了传输，则该用户档案被视为使用中。

已被多个投放定向的用户档案将仅计数一次。

>[!NOTE]
>
>Facebook 和 Twitter 渠道不包含在內。

活动用户档案计数可用于 **营销实例** 仅。 它不适用于执行实例，即MID（中间采购）和RT（消息中心/实时消息）实例。

>[!NOTE]
>
>您还可以直接从Campaign控制面板监控实例上的活动用户档案数。 有关更多信息，请参阅 [控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html).

## 教程视频 {#create-profiles-video}

了解如何访问用户档案数据、对用户档案进行排序和筛选以及手动创建和管理用户档案。

此视频还介绍了Adobe Campaign Classic是否遵守了《通用数据保护法规》。

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).

**另请参阅**

* [Campaign中的隐私管理](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)

* [定义目标群体](../../delivery/using/define-the-right-audience.md)

* [在工作流中创建查询和划分数据区段](../../workflow/using/targeting-data.md)

* [选择目标映射](../../delivery/using/selecting-a-target-mapping.md)

* [定义受众 — 最佳实践](../../delivery/using/define-the-right-audience.md)
