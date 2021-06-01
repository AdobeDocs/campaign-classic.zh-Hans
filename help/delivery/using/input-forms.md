---
product: campaign
title: 输入窗体
description: 输入窗体
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: 8ec52c96-44a2-4544-93b6-9ba251510682
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 2%

---

# 输入窗体{#input-forms}

以下是关于在Adobe Campaign使用输入表的一些一般原则。

[此部分](../../configuration/using/identifying-a-form.md)中详细介绍了Forms。

## 窗体结构 {#form-structure}

输入表单的XML文档必须包含具有&#x200B;**name**&#x200B;和&#x200B;**namespace**&#x200B;属性的&#x200B;**`<form>`**&#x200B;根元素，以分别填充表单名称及其命名空间。

```
<form name="form_name" namespace="name_space">
...
</form>
```

默认情况下，表单与具有相同名称和命名空间的数据架构相关联。 要将表单与其他名称关联，请在&#x200B;**`<form>`**&#x200B;元素的&#x200B;**entity-schema**&#x200B;属性中输入架构键。

为了说明输入表单的结构，我们基于示例模式“cus:book”描述了一个界面：

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

在&#x200B;**`<input>`**&#x200B;元素中输入编辑控件，该元素具有&#x200B;**xpath**&#x200B;属性，该属性包含其架构中字段的路径。

**有关XPath语法的提醒：**

Adobe Campaign中使用XPath语言来引用属于数据模式的元素或属性。

XPath是一种语法，用于在XML文档的树中查找节点。

元素由其名称指定，属性由名称前面的字符“@”指定。

示例:

* **@date**:选择名称为“date”的属性
* **章节/@title**:选择元素下的“title”属 `<chapter>` 性
* **../@date**:从当前元素的父元素中选择日期

编辑控件会自动适应相应的数据类型，并使用架构中定义的标签。

默认情况下，每个字段都显示在一行中，并占用所有可用空间，具体取决于数据类型。

>[!CAUTION]
>
>输入表单必须引用&#x200B;**`<form>`**&#x200B;元素上的&#x200B;**type=&quot;contentForm&quot;**&#x200B;属性，以自动添加输入内容所需的帧。

## 格式化 {#formatting}

控件相对彼此的布置类似于HTML表中使用的布置，其可能将控件分割成若干列、元件交错或指定可用空间的占用。 但是，请记住，格式仅允许分配比例；不能为对象指定固定维度。

如需详细信息，请参阅[此部分](../../configuration/using/form-structure.md#formatting)。

## 列表类型控件{#list-type-controls}

要编辑收藏集元素，必须使用列表类型控件。

### 列列表{#column-list}

此控件显示可编辑的列列表，其中的工具栏包含“添加”和“删除”按钮。

![](assets/d_ncs_content_form4.png)

```
<input xpath="chapter" type="list">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

必须使用&#x200B;**type=&quot;list&quot;**&#x200B;属性填充列表控件，并且列表的路径必须引用集合元素。

列由列表的子&#x200B;**`<input>`**&#x200B;元素声明。

>[!NOTE]
>
>当为数据架构中的收集元素填写&#x200B;**ordered=&quot;true&quot;**&#x200B;属性时，将自动添加向上和向下排序箭头。

默认情况下，工具栏按钮垂直对齐。 也可以水平对齐：

![](assets/d_ncs_content_form5.png)

```
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

**toolbarCaption**&#x200B;属性强制工具栏的水平对齐方式并填充列表上方的标题。

>[!NOTE]
>
>对于集合元素标签不显示在控件左侧，请添加&#x200B;**nolabel=&quot;true&quot;**&#x200B;属性。

#### 放大列表{#zoom-in-a-list}

列表数据的插入和编辑可以以单独的编辑表单执行。

在以下情况下，会使用列表中的编辑表单：

* 为便于信息输入，
* 存在多线控，
* 列表中的列仅包含主字段，并且表单显示收藏集元素的所有字段。

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

编辑表单的定义通过列表元素下的&#x200B;**`<form>`**&#x200B;元素指定。 其结构与输入形式的结构相同。

在列表定义中输入&#x200B;**zoom=&quot;true&quot;**&#x200B;属性时，会自动添加&#x200B;**[!UICONTROL Detail]**&#x200B;按钮。 这样，您就可以在选定行上打开编辑表单。

>[!NOTE]
>
>添加&#x200B;**zoomOnAdd=&quot;true&quot;**&#x200B;属性会强制在插入列表元素时调用编辑表单。

### 选项卡列表{#tab-list}

此列表以选项卡的形式显示对收藏集元素的编辑。

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

必须使用&#x200B;**type=&quot;notebooklist&quot;**&#x200B;属性填充列表控件，并且列表的路径必须引用集合元素。

选项卡的标题包含通过&#x200B;**xpath-label**&#x200B;属性输入的数据值。

编辑控件必须在作为列表控件子项的&#x200B;**`<container>`**&#x200B;元素下声明。

使用工具栏按钮添加或删除列表元素。

>[!NOTE]
>
>为数据架构中的收集元素填充&#x200B;**ordered=&quot;true&quot;**&#x200B;属性时，将自动添加左和右排序箭头。

## 容器 {#containers}

容器允许您对一组控件进行分组。 它们通过&#x200B;**`<container>`**&#x200B;元素存在。 已使用它们设置多列控件的格式以及选项卡列表的控件。

有关容器以及如何在输入表单中使用容器的详细信息，请参阅[此部分](../../configuration/using/form-structure.md#containers)。

## 编辑窗体 {#editing-forms}

编辑区域允许您输入输入表单的XML内容：

![](assets/d_ncs_content_form12.png)

**[!UICONTROL Preview]**&#x200B;选项卡允许您查看输入表单：

![](assets/d_ncs_content_form13.png)
