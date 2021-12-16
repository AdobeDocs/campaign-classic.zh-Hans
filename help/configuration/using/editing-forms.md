---
product: campaign
title: 编辑表单
description: 编辑表单
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: a6549ad4d94b93d65752df66aeec39b90e4c3ec5
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 5%

---


# 编辑表单{#editing-forms}

![](../../assets/common.svg)

## 概述

营销人员和运营人员使用输入表单创建、修改和预览记录。 Forms显示信息的可视表示形式。

您可以创建和修改输入表单：

* 您可以修改默认提交的工厂输入表单。 工厂输入表单基于工厂数据架构。
* 您可以根据定义的数据架构创建自定义输入表单。

Forms是 `xtk:form` 类型。 您可以在 `xtk:form` 架构。 要查看此架构，请选择 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** 中。 有关更多信息 [窗体结构](form-structure.md).

要访问输入表单，请选择 **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** 从菜单：

![](assets/d_ncs_integration_form_arbo.png)

要设计表单，请在XML编辑器中编辑XML内容：

![](assets/d_ncs_integration_form_edit.png)

[阅读更多](form-structure.md#formatting)。

要预览表单，请单击 **[!UICONTROL Preview]** 选项卡：

![](assets/d_ncs_integration_form_preview.png)

## 表单类型

您可以创建不同类型的输入表单。 表单类型决定用户在表单中导航的方式：

* 控制台屏幕

   这是默认的表单类型。 表单包含单页。

   ![](assets/console_screen_form.png)

* 内容管理

   使用此表单类型进行内容管理。 请参阅 [用例](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* 向导

   该表单包括多个按特定顺序排列的浮动屏幕。 用户从一个屏幕导航到下一个屏幕。 [阅读更多](form-structure.md#wizards)。

* Iconbox

   此表单包含多个页面。 要导航表单，用户需选择表单左侧的图标。

   ![](assets/iconbox_form_preview.png)

* 笔记本

   此表单包含多个页面。 要导航表单，用户需选择表单顶部的选项卡。

   ![](assets/notebook_form_preview.png)

* 垂直窗格

   此窗体显示导航树。

* 水平窗格

   此表单显示项目列表。

