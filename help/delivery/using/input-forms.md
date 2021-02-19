---
solution: Campaign Classic
product: campaign
title: 输入窗体
description: 输入窗体
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 2%

---


# 输入窗体{#input-forms}

以下是关于在Adobe Campaign中使用输入表格的一些一般原则。

Forms详见[本节](../../configuration/using/identifying-a-form.md)。

## 窗体结构 {#form-structure}

输入表单的XML文档必须包含&#x200B;**`<form>`**&#x200B;根元素，其中&#x200B;**name**&#x200B;和&#x200B;**命名空间**&#x200B;属性分别用于填充表单名称及其命名空间。

```
<form name="form_name" namespace="name_space">
...
</form>
```

默认情况下，表单与名称和命名空间相同的模式关联。 要将表单与其他名称关联，请在&#x200B;**`<form>`**&#x200B;元素的&#x200B;**entity-模式**&#x200B;属性中输入模式键。

为了说明输入表单的结构，我们在示例模式“cus:book”的基础上描述了一个接口：

![](assets/d_ncs_content_form1.png)

这是相应的输入表单：

```
<form name="book" namespace="cus" type="contentForm">
  <input xpath="@name"/>
  <input xpath="@date"/>
  <input xpath="@language"/>
</form>
```

编辑元素的描述以&#x200B;**`<form>`**&#x200B;根元素开头。

在&#x200B;**`<input>`**&#x200B;元素中输入编辑控件，该元素具有&#x200B;**xpath**&#x200B;属性，该属性包含字段在其模式中的路径。

**提醒您有关XPath语法：**

Adobe Campaign中使用XPath语言来引用属于数据模式的元素或属性。

XPath是一种语法，它允许您在XML文档的树中查找节点。

元素由其名称指定，属性由字符&quot;@&quot;前的名称指定。

示例:

* **@date**:选择名称为“date”的属性
* **章节/@title**:选择元素下的“title”属 `<chapter>` 性
* **../@date**:从当前元素的父元素中选择日期

编辑控件自动适应相应的数据类型，并使用在模式中定义的标签。

默认情况下，每个字段显示在一行中并占用所有可用空间，具体取决于数据类型。

>[!CAUTION]
>
>输入表单必须引用&#x200B;**`<form>`**&#x200B;元素上的&#x200B;**type=&quot;contentForm&quot;**&#x200B;属性，以自动添加要输入内容所需的框架。

## 格式化 {#formatting}

控件相对彼此的排列类似于HTML表中使用的排列，可以将控件分成几列、交错元素或指定可用空间的占用。 但是，请记住，格式仅允许分配比例；不能为对象指定固定尺寸。

如需详细信息，请参阅[此部分](../../configuration/using/form-structure.md#formatting)。

## 列表类型控件{#list-type-controls}

要编辑收藏集元素，必须使用列表类型控件。

### 列列表{#column-list}

此控件显示一个可编辑的列列表，其工具栏包含“添加”和“删除”按钮。

![](assets/d_ncs_content_form4.png)

```
<input xpath="chapter" type="list">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

必须使用&#x200B;**type=&quot;列表&quot;**&#x200B;属性填充列表控件，列表的路径必须引用集合元素。

列由列表的子&#x200B;**`<input>`**&#x200B;元素声明。

>[!NOTE]
>
>当数据模式中的收集元素完成&#x200B;**ordered=&quot;true&quot;**&#x200B;属性时，会自动添加向上和向下排序箭头。

默认情况下，工具栏按钮垂直对齐。 还可以水平对齐它们：

![](assets/d_ncs_content_form5.png)

```
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

**toolbarCaption**&#x200B;属性强制工具栏的水平对齐并填充列表上方的标题。

>[!NOTE]
>
>对于不显示在控件左侧的集合元素标签，请添加&#x200B;**nolabel=&quot;true&quot;**&#x200B;属性。

#### 放大列表{#zoom-in-a-list}

列表数据的插入和编辑可以在单独的编辑表单中执行。

在以下情况下，可以使用列表中的编辑表单：

* 为了方便信息输入，
* 存在多行控件，
* 列表中的列仅包含主字段，并且表单显示集合元素的所有字段。

![](assets/d_ncs_content_form7.png)

```
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

编辑表单的定义是通过列表元素下的&#x200B;**`<form>`**&#x200B;元素指定的。 其结构与输入形式的结构相同。

在列表定义中输入&#x200B;**zoom=&quot;true&quot;**&#x200B;属性时，会自动添加&#x200B;**[!UICONTROL Detail]**&#x200B;按钮。 这样，您就可以在所选行上打开编辑表单。

>[!NOTE]
>
>添加&#x200B;**zoomOnAdd=&quot;true&quot;**&#x200B;属性会强制在插入列表的元素时调用编辑表单。

### 制表符列表{#tab-list}

此列表以选项卡的形式显示集合元素的编辑。

![](assets/d_ncs_content_form6.png)

```
<container toolbarCaption="List of chapters" type="notebooklist" xpath="chapter" xpath-label="@name">
  <container colcount="2">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </container>
</container>
```

必须使用&#x200B;**type=&quot;notebooklist&quot;**&#x200B;属性填充列表控件，列表的路径必须引用集合元素。

选项卡的标题包含通过&#x200B;**xpath-label**&#x200B;属性输入的数据值。

编辑控件必须在&#x200B;**`<container>`**&#x200B;元素下声明，该元素是列表控件的子项。

使用工具栏按钮添加或删除列表元素。

>[!NOTE]
>
>在数据模式中为集合元素填充&#x200B;**ordered=&quot;true&quot;**&#x200B;属性时，会自动添加左右排序箭头。

## 容器{#containers}

容器允许您对一组控件进行分组。 它们通过&#x200B;**`<container>`**&#x200B;元素存在。 它们已用于设置多列中控件的格式以及选项卡列表的控件。

有关容器以及如何在输入表单中使用它们的详细信息，请参阅[本节](../../configuration/using/form-structure.md#containers)。

## 编辑窗体 {#editing-forms}

编辑区域允许您输入输入表单的XML内容：

![](assets/d_ncs_content_form12.png)

使用&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡可以视图输入表单：

![](assets/d_ncs_content_form13.png)
