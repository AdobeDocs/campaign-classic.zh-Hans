---
product: campaign
title: 使用Adobe Campaign Explorer
description: 了解如何使用Campaign Explorer
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f91d69a4-b794-40f0-b450-de862d7333e2
source-git-commit: fdb840a9e6349f074378899e07f794b62fb5b054
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 34%

---

# 使用Adobe Campaign Explorer {#using-adobe-campaign-explorer}

![](../../assets/v7-only.svg)

可通过工具栏图标访问 Adobe Campaign Explorer。它可用于访问 Adobe Campaign、所有 Adobe Campaign 功能、配置屏幕以及部分平台元素的更详细视图。

**[!UICONTROL Explorer]** 工作区分成三个区域：

![](assets/s_ncs_user_navigation.png)

**1 - 树状结构**：您可以个性化树状结构的内容（添加、移动或删除节点）。此程序仅适用于专家级用户。有关更多信息，请参阅  [此部分](#about-navigation-hierarchy).)。

**2 - 列表**：您可以过滤列表、执行搜索、添加信息或排序数据。[了解详情](adobe-campaign-ui-lists.md)。

**3 - 详细信息**：您可以显示所选元素的详细信息。您可以使用右上角的图标以全屏形式显示这些信息。

## 文件夹和导航树{#about-navigation-hierarchy}

导航树的工作方式类似于文件浏览器（例如Windows资源管理器）。 文件夹可能包含子文件夹。 选择节点后，将显示与该节点对应的视图。

显示的视图是与架构关联的列表以及用于编辑所选行的输入表单。

![](assets/d_ncs_integration_navigation.png)

要向树中添加新文件夹，请右键单击要在其中插入文件夹的分支中的文件夹，然后选择 **[!UICONTROL Add new folder]** . 在快捷菜单中，选择要创建的文件类型。

![](assets/d_ncs_integration_navigation_create.png)

了解如何配置Campaign导航树 [在此部分中](../../configuration/using/configuration.md).

了解如何设置文件夹权限 [在此部分中](access-management-folders.md).

## 文件夹配置最佳实践

* **使用内置文件夹**

   使用内置文件夹，可让未参与项目的人员更轻松地使用、维护和排查应用程序问题。 您不应为收件人、列表、投放等创建自定义文件夹结构，而应使用标准文件夹，如“管理”、“配置文件和目标”、“营销活动管理”。

* **创建子文件夹**

   将技术工作流放置在标准文件夹下：管理/生产/技术工作流，并按工作流类型创建子目录。

* **设置命名约定**

   例如，您可以按字母顺序命名工作流，以便它们按执行顺序显示。

   例如：

   * A1 — 导入收件人，从10:00开始；
   * A2 — 导入票证，于11:00开始。

* **为用户创建模板以开始**

   创建投放模板、工作流模板、特定于用户的营销活动模板。 此结构可以节省时间，并确保为每个用户使用正确的投放映射和分类。

## 屏幕分辨率 {#screen-resolution}

为了获得最佳的导航和使用性，Adobe 建议您最低使用 1600x900 像素的屏幕分辨率。

>[!CAUTION]
>
>1600x900像素以下的分辨率不受Adobe Campaign支持。

在 **[!UICONTROL Explorer]** 工作区中，如果出现部分 **[!UICONTROL Details]** 区域被截断，可通过区域顶端的箭头或单击 **[!UICONTROL Enlarge]** 按钮展开该区域。

![](assets/s_ncs_user_resolution.png)

## 浏览和自定义列表 {#browsing-lists}

了解如何浏览、管理和自定义列表 [在此部分中](adobe-campaign-ui-lists.md).
