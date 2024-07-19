---
product: campaign
title: 输入表单
description: 了解如何在Campaign中使用输入表单
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Data Management
role: User, Developer
exl-id: 8ec52c96-44a2-4544-93b6-9ba251510682
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# 输入表单{#input-forms}

以下是有关在Adobe Campaign中使用输入表单的一些一般原则。

在[此部分](../../configuration/using/identifying-a-form.md)中详细介绍了Forms。

## 窗体结构 {#form-structure}

输入表单的XML文档必须包含具有&#x200B;**名称**&#x200B;和&#x200B;**命名空间**&#x200B;属性的&#x200B;**`<form>`**&#x200B;根元素，才能分别填充表单名称及其命名空间。

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

默认情况下，表单与具有相同名称和命名空间的数据架构关联。 若要将表单与其他名称关联，请在&#x200B;**`<form>`**&#x200B;元素的&#x200B;**entity-schema**&#x200B;属性中输入架构键。

为了说明输入表单的结构，我们基于示例模式“cus：book”描述了一个接口：

![](assets/d_ncs_content_form1.png)

这是相应的输入表单：

```xml
<form name="book" namespace="cus" type="contentForm">
  <input xpath="@name"/>
  <input xpath="@date"/>
  <input xpath="@language"/>
</form>
```

编辑元素的描述以&#x200B;**`<form>`**&#x200B;根元素开头。

在具有&#x200B;**xpath**&#x200B;属性的&#x200B;**`<input>`**&#x200B;元素中输入编辑控件，该属性包含其架构中的字段路径。

**有关XPath语法的提醒：**

XPath语言在Adobe Campaign中用于引用属于数据架构的元素或属性。

XPath是一种语法，允许您在XML文档的树中查找节点。

元素由名称指定，属性由名称指定，名称前面加有字符“@”。

示例：

* **@date**：选择名为“date”的属性
* **chapter/@title**：选择`<chapter>`元素下的“title”属性
* **../@date**：从当前元素的父元素中选择日期

编辑控件会自动适应对应的数据类型，并使用架构中定义的标签。

默认情况下，每个字段显示在一行中，并占用所有可用空间，具体取决于数据类型。

>[!CAUTION]
>
>输入表单必须引用&#x200B;**`<form>`**&#x200B;元素上的&#x200B;**type=&quot;contentForm&quot;**&#x200B;属性，才能自动添加输入内容所需的框架。

## 格式化 {#formatting}

控制项相对于彼此的排列方式与HTML表中使用的排列方式相似，有可能将控制项划分为若干列、交错元素或指定可用空间的占用。 但是，请记住，格式设置仅授权分配比例；您不能为对象指定固定维度。

如需详细信息，请参阅[此小节](../../configuration/using/form-structure.md#formatting)。

## 列表类型控件 {#list-type-controls}

要编辑收集要素，您必须使用列表类型控件。

### 列列表 {#column-list}

此控件显示可编辑的列列表，工具栏包含添加和删除按钮。

![](assets/d_ncs_content_form4.png)

```xml
<input xpath="chapter" type="list">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

列表控件必须使用&#x200B;**type=&quot;list&quot;**&#x200B;属性填充，且列表的路径必须引用集合元素。

这些列由列表的子元素&#x200B;**`<input>`**&#x200B;声明。

>[!NOTE]
>
>在数据架构中的集合元素完成&#x200B;**ordered=&quot;true&quot;**&#x200B;属性时，会自动添加向上和向下排序箭头。

默认情况下，工具栏按钮垂直对齐。 它们也可以水平对齐：

![](assets/d_ncs_content_form5.png)

```xml
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

**toolbarCaption**&#x200B;属性强制工具栏水平对齐，并填充列表上方的标题。

>[!NOTE]
>
>要使集合元素标签不显示在控件的左侧，请添加&#x200B;**nolabel=&quot;true&quot;**&#x200B;属性。

#### 放大列表 {#zoom-in-a-list}

列表数据的插入和编辑可以在单独的编辑表单中执行。

在下列情况下，将使用列表中的编辑表单：

* 为了便于信息输入，
* 存在多线路控件，
* 列表中的列仅包含主字段，表单将显示收集要素的所有字段。

![](assets/d_ncs_content_form7.png)

```xml
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter" zoom="true" zoomOnAdd="true">
  <input xpath="@name"/>
  <input xpath="@number"/>

  <form colcount="2" label="Editing a chapter">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </form>
</input>
```

编辑表单的定义通过list元素下的&#x200B;**`<form>`**&#x200B;元素指定。 其结构与输入表单的结构相同。

在列表定义中输入&#x200B;**zoom=&quot;true&quot;**&#x200B;属性时，将自动添加&#x200B;**[!UICONTROL Detail]**&#x200B;按钮。 这允许您在选定行上打开编辑表单。

>[!NOTE]
>
>添加&#x200B;**zoomOnAdd=&quot;true&quot;**&#x200B;属性会强制在插入列表的元素时调用编辑表单。

### 选项卡列表 {#tab-list}

此列表以选项卡的形式呈现对收藏集元素的编辑。

![](assets/d_ncs_content_form6.png)

```xml
<container toolbarCaption="List of chapters" type="notebooklist" xpath="chapter" xpath-label="@name">
  <container colcount="2">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </container>
</container>
```

列表控件必须使用&#x200B;**type=&quot;notebooklist&quot;**&#x200B;属性填充，并且列表的路径必须引用收藏集元素。

选项卡的标题包含通过&#x200B;**xpath-label**&#x200B;属性输入的数据值。

编辑控件必须在&#x200B;**`<container>`**&#x200B;元素（列表控件的子项）下声明。

使用工具栏按钮添加或删除列表元素。

>[!NOTE]
>
>在数据架构中为集合元素填充&#x200B;**ordered=&quot;true&quot;**&#x200B;属性时，会自动添加左右排序箭头。

## 容器 {#containers}

容器允许您对一组控件进行分组。 它们通过&#x200B;**`<container>`**&#x200B;元素存在。 它们已用于格式化多个列中的控件以及选项卡列表的控件。

有关容器以及如何在输入表单中使用这些容器的详细信息，请参阅[此部分](../../configuration/using/form-structure.md#containers)。

## 编辑窗体 {#editing-forms}

通过编辑区域，您可以输入输入表单的XML内容：

![](assets/d_ncs_content_form12.png)

**[!UICONTROL Preview]**&#x200B;选项卡允许您查看输入表单：

![](assets/d_ncs_content_form13.png)

阅读有关[编辑表单](../../configuration/using/editing-forms.md)和[表单结构](../../configuration/using/form-structure.md)的更多信息。
