---
product: campaign
title: 使用Adobe Campaign Explorer
description: 了解如何使用Campaign Explorer
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f91d69a4-b794-40f0-b450-de862d7333e2
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 34%

---

# 使用Adobe Campaign资源管理器 {#using-adobe-campaign-explorer}



可通过工具栏图标访问 Adobe Campaign Explorer。它可用于访问 Adobe Campaign、所有 Adobe Campaign 功能、配置屏幕以及部分平台元素的更详细视图。

**[!UICONTROL Explorer]** 工作区分成三个区域：

![](assets/s_ncs_user_navigation.png)

**1 - 树状结构**：您可以个性化树状结构的内容（添加、移动或删除节点）。此程序仅适用于专家级用户。有关更多信息，请参阅  [本节](#about-navigation-hierarchy).)。

**2 - 列表**：您可以过滤列表、执行搜索、添加信息或排序数据。[了解详情](adobe-campaign-ui-lists.md)。

**3 - 详细信息**：您可以显示所选元素的详细信息。您可以使用右上角的图标以全屏形式显示这些信息。

## 文件夹和导航树{#about-navigation-hierarchy}

导航树的工作方式与文件浏览器类似（例如Windows资源管理器）。 文件夹可能包含子文件夹。 选择节点将显示与该节点对应的视图。

显示的视图是与架构关联的列表和用于编辑所选行的输入表单。

![](assets/d_ncs_integration_navigation.png)

要向树中添加新文件夹，请在要插入文件夹的分支中右键单击该文件夹，然后选择 **[!UICONTROL Add new folder]** . 在快捷菜单中，选择要创建的文件类型。

![](assets/d_ncs_integration_navigation_create.png)

了解如何配置Campaign导航树 [在此部分中](../../configuration/using/configuration.md).

了解如何设置文件夹权限 [在此部分中](access-management-folders.md).

## 文件夹配置最佳实践

* **使用内置文件夹**

   使用内置文件夹使未参与项目的人更轻松地使用、维护应用程序和排除其故障。 您不应为收件人、列表、投放等创建自定义文件夹结构，而应使用标准文件夹，如管理、配置文件和目标、营销活动管理。

* **创建子文件夹**

   将技术工作流放在标准文件夹“管理/生产/技术工作流”下，并根据工作流类型创建子目录。

* **设置命名约定**

   例如，您可以按字母顺序命名工作流，以使它们按执行顺序排序。

   例如：

   * A1 — 导入收件人，从10:00开始；
   * A2 — 导入票证，11:00开始。

* **为用户创建模板，以便开始使用**

   创建特定于用户的投放模板、工作流模板和活动模板。 此结构可以节省时间并确保为每个用户使用正确的投放映射和类型。

## 屏幕分辨率 {#screen-resolution}

为了获得最佳的导航和使用性，Adobe 建议您最低使用 1600x900 像素的屏幕分辨率。

>[!CAUTION]
>
>Adobe Campaign不支持低于1600x900像素的分辨率。

在 **[!UICONTROL Explorer]** 工作区中，如果出现部分 **[!UICONTROL Details]** 区域被截断，可通过区域顶端的箭头或单击 **[!UICONTROL Enlarge]** 按钮展开该区域。

![](assets/s_ncs_user_resolution.png)

## 浏览和自定义列表 {#browsing-lists}

了解如何浏览、管理和自定义列表 [在此部分中](adobe-campaign-ui-lists.md).
