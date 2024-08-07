---
product: campaign
title: 使用Adobe Campaign资源管理器
description: 了解如何使用Campaign Explorer
feature: Overview
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f91d69a4-b794-40f0-b450-de862d7333e2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 14%

---

# 使用Adobe Campaign Explorer {#using-adobe-campaign-explorer}



可通过工具栏图标访问Adobe Campaign资源管理器。 它可用于访问 Adobe Campaign、所有 Adobe Campaign 功能、配置屏幕以及部分平台元素的更详细视图。

**[!UICONTROL Explorer]**&#x200B;工作区分为三个区域：

![](assets/s_ncs_user_navigation.png)

**1 — 树**：您可以个性化树的内容（添加、移动或删除节点）。 此过程仅适用于专家用户。 有关详细信息，请参阅[此部分](#about-navigation-hierarchy)。

**2 — 列表**：您可以筛选此列表、运行搜索、添加信息或排序数据。 [了解详情](adobe-campaign-ui-lists.md)。

**3 — 详细信息**：您可以显示选定元素的详细信息。 您可以使用右上角的图标以全屏形式显示这些信息。

## 文件夹和导航树{#about-navigation-hierarchy}

导航树的工作方式与文件浏览器类似（例如Windows资源管理器）。 文件夹可能包含子文件夹。 选择某个节点将显示与该节点对应的视图。

显示的视图是与架构关联的列表和用于编辑所选行的输入表单。

![](assets/d_ncs_integration_navigation.png)

要向树中添加新文件夹，请在要插入文件夹的分支中右键单击该文件夹，然后选择&#x200B;**[!UICONTROL Add new folder]** 。 在快捷菜单中，选择要创建的文件类型。

![](assets/d_ncs_integration_navigation_create.png)

在本节](../../configuration/using/configuration.md)中了解如何配置Campaign导航树[。

在本节](access-management-folders.md)中了解如何设置文件夹[的权限。

## 文件夹配置最佳实践

* **使用内置文件夹**

  通过使用内置文件夹，未参与项目的人可以更轻松地使用、维护应用程序和排除其故障。 您不应为收件人、列表、投放等创建自定义文件夹结构，而应使用标准文件夹，如管理、配置文件和目标、营销活动管理。

* **创建子文件夹**

  将技术工作流放置在标准文件夹“管理/生产/技术工作流”下，并根据工作流类型创建子目录。

* **设置命名约定**

  例如，您可以按字母顺序命名工作流，以使它们按执行顺序排序。

  例如：

   * A1 — 导入收件人，从10:00开始；
   * A2 — 导入票证，11:00开始。

* **为用户创建模板以开始**

  创建特定于用户的投放模板、工作流模板和活动模板。 此结构可以节省时间并确保为每个用户使用正确的投放映射和分类。

## 屏幕分辨率 {#screen-resolution}

为了获得最佳的导航和使用性，Adobe 建议您最低使用 1600x900 像素的屏幕分辨率。

>[!CAUTION]
>
>Adobe Campaign不支持小于1600x900像素的分辨率。

在&#x200B;**[!UICONTROL Explorer]**&#x200B;工作区中，如果&#x200B;**[!UICONTROL Details]**&#x200B;区域的某些部分似乎被截断，请使用区域顶部的箭头将其展开或单击&#x200B;**[!UICONTROL Enlarge]**&#x200B;按钮。

![](assets/s_ncs_user_resolution.png)

## 浏览和自定义列表 {#browsing-lists}

在本节](adobe-campaign-ui-lists.md)中了解如何浏览、管理和自定义列表[。
