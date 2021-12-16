---
product: campaign
title: 编辑表单
description: 编辑表单
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: f4b9ac3300094a527b5ec1b932d204f0e8e5ee86
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 4%

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

## 容器

在表单中，您可以将容器用于各种目的：

* 在表单中组织内容
* 定义对输入字段的访问权限
* 将表单嵌套在其他表单中

[阅读更多](form-structure.md#containers)。

### 组织内容

使用容器组织表单中的内容：

* 您可以将字段分组为多个部分。
* 您可以将页面添加到多页面表单。

要插入容器，请使用 `<container>` 元素。 [阅读更多](form-structure.md#containers)。

#### 组字段

使用容器将输入字段分组为有组织的部分。

要在表单中插入部分，请使用以下元素： `<container type="frame">`. （可选）要添加节标题，请使用 `label` 属性。

语法： `<container type="frame" label="`*section_title*`"> […] </container>`

在本例中，容器定义 **创建** 部分，包括 **[!UICONTROL Created by]** 和 **[!UICONTROL Name]** 输入字段：

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### 将页面添加到多页面表单

对于多页面表单，请使用容器创建表单页面。

此示例显示 **常规** 和 **详细信息** 表单页面：

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### 定义对字段的访问权限

使用容器定义可见内容并定义对字段的访问权限。 您可以打开或关闭字段组。

### 嵌套表单

使用容器将表单嵌套在其他表单中。 [阅读更多](#add-pages-to-multipage-forms)。

## 对图像的引用

要查找图像，请选择 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** 中。

要将图像与表单中的元素（例如图标）关联，您可以添加对图像的引用。 使用 `img` 属性，例如 `<container>` 元素。

语法: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

此示例显示对 `book.png` 和 `detail.png` 图像 `ncm` 命名空间：

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

这些图像用于用户单击以导航多页面表单的图标：

![](assets/nested_forms_preview.png)
