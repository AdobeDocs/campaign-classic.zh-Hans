---
product: campaign
title: 窗体结构
description: 窗体结构
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: e61f2b63-06d3-4b8c-867f-1c729176d2da
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2384'
ht-degree: 0%

---

# 窗体结构{#form-structure}

![](../../assets/v7-only.svg)

表单的描述是一种结构化的XML文档，用于观察表单模式&#x200B;**xtk:form**&#x200B;的语法。

输入表单的XML文档必须包含具有&#x200B;**name**&#x200B;和&#x200B;**namespace**&#x200B;属性的`<form>`根元素，以填充表单名称和命名空间。

```
<form name="form_name" namespace="name_space">
...
</form>
```

默认情况下，表单与具有相同名称和命名空间的数据架构相关联。 要将表单与其他名称相关联，请将`<form>`元素的&#x200B;**entity-schema**&#x200B;属性设置为架构键的名称。 为了说明输入表单的结构，让我们使用“cus:recipient”示例模式描述接口：

```
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="Male" value="1"/>   
    <value name="female" label="Female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
    <attribute name="birthDate" type="datetime" label="Date"/>
    <attribute name="gender" type="byte" label="Gender" enum="gender"/>
  </element>
</srcSchema>
```

基于示例架构的输入表单：

![](assets/d_ncs_integration_form_exemple1.png)

```
<form name="recipient" namespace="cus">
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email"/>
</form>
```

编辑控件的描述从`<form>`根元素开始。 在&#x200B;**`<input>`**&#x200B;元素中输入编辑控件，该元素具有&#x200B;**xpath**&#x200B;属性，该属性包含其架构中字段的路径。

编辑控件会自动适应相应的数据类型，并使用架构中定义的标签。

>[!NOTE]
>
>通过向`<input>`元素添加&#x200B;**label**&#x200B;属性，可以使其数据架构中定义的标签过载：\
>`<input label="E-mail address" xpath="@name" />`

默认情况下，每个字段都显示在一行中，并根据数据类型占用所有可用空间。

## 格式化 {#formatting}

控件的布局类似于HTML表中使用的布局，可能会将控件划分为多列、隔行元素或指定对可用空间的占用。 但是，请记住，格式仅允许您按比例划分区域；不能为对象指定固定维度。

要在两列中显示上述示例的控件：

![](assets/d_ncs_integration_form_exemple2.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email"/>
  </container>
</form>
```

具有&#x200B;**colcount**&#x200B;属性的&#x200B;**`<container>`**&#x200B;元素允许您将子控件的显示强制到两列上。

控件上的&#x200B;**colspan**&#x200B;属性会将控件扩展为在其值中输入的列数：

![](assets/d_ncs_integration_form_exemple3.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form> 
```

通过填充&#x200B;**type=&quot;frame&quot;**&#x200B;属性，容器在子控件周围添加一个帧，该帧的标签包含在&#x200B;**label**&#x200B;属性中：

![](assets/d_ncs_integration_form_exemple4.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2" type="frame" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form>
```

**`<static>`**&#x200B;元素可用于设置输入表单的格式：

![](assets/d_ncs_integration_form_exemple5.png)

```
<form name="recipient" namespace="cus">
  <static type="separator" colspan="2" label="General"/>
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email" colspan="2"/>
  <static type="help" label="General information about recipient with date of birth, gender, and e-mail address." colspan="2"/>
</form>
```

使用&#x200B;**分隔符**&#x200B;类型的&#x200B;**`<static>`**&#x200B;标记，可以添加一个分隔符栏，其中的标签包含在&#x200B;**label**&#x200B;属性中。

使用带有帮助类型的`<static>`标记添加了帮助文本。 文本的内容在&#x200B;**label**&#x200B;属性中输入。

## 容器 {#containers}

容器允许您对一组控件进行分组。 它们由&#x200B;**`<container>`**&#x200B;元素表示。 上面使用它们设置多列控件的格式。

通过`<container>`上的&#x200B;**xpath**&#x200B;属性，可以简化子控件的引用。 然后，控件的引用相对于父级`<container>`。

不带“xpath”的容器示例：

```
<container colcount="2">
  <input xpath="location/@zipCode"/>
  <input xpath="location/@city"/>
</container>
```

在名为“location”的元素中添加“xpath”的示例：

```
<container colcount="2" xpath="location">
  <input xpath="@zipCode"/>
  <input xpath="@city"/>
</container>
```

### 容器类型 {#types-of-container}

容器用于使用一组在页面中格式的字段来构建复杂的控件。

#### 制表符容器 {#tab-container}

制表符容器可设置从制表符访问的页面中的数据的格式。

![](assets/d_ncs_integration_form_exemple6.png)

```
<container type="notebook">
  <container colcount="2" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location">
    ...
  </container>
</container>
```

主容器由&#x200B;**type=&quot;notebook&quot;**&#x200B;属性定义。 在子容器中声明制表符，并从&#x200B;**label**&#x200B;属性填充制表符的标签。

>[!NOTE]
>
>**style=&quot;down|up**（默认情况下）**&quot;**功能强制选项卡标签在控件下方或上方的垂直定位。 此功能属于可选功能。
>![](assets/d_ncs_integration_form_exemple7.png)
>`<container style="down" type="notebook">  ... </container>`

#### 图标列表 {#icon-list}

此容器显示一个垂直图标栏，用于选择要显示的页面。

![](assets/d_ncs_integration_form_exemple8.png)

```
<container type="iconbox">
  <container colcount="2" label="General" img="xtk:properties.png">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location" img="nms:msgfolder.png">
    ...
  </container>
</container>
```

主容器由&#x200B;**type=&quot;iconbox&quot;**&#x200B;属性定义。 与图标关联的页面在子容器中声明。 图标的标签是从&#x200B;**label**&#x200B;属性填充的。

页面的图标会从`img="<image>"`属性填充，其中`<image>`是与由名称和命名空间（例如&quot;xtk:properties.png&quot;）组成的键所对应的图像名称。

可从&#x200B;**[!UICONTROL Administration > Configuration > Images]**&#x200B;节点获取这些图像。

#### 可见性容器 {#visibility-container}

您可以通过动态条件掩盖一组控件。

此示例说明了“性别”字段值控件的可见性：

```
<container type="visibleGroup" visibleIf="@gender=1">
  ...
</container>
<container type="visibleGroup" visibleIf="@gender=2">
  ...
</container>
```

可见性容器由属性&#x200B;**type=&quot;visibleGroup&quot;**&#x200B;定义。 **visibleIf**&#x200B;属性包含可见性条件。

条件语法的示例：

* **visibleIf=&quot;@email=&#39;peter.martinezATneeolane.net&#39;&quot;**:测试字符串类型数据上的等同性。比较值必须用引号括起来。
* **visibleIf=&quot;@gender >= 1和@gender != 2&quot;**:条件。
* **visibleIf=&quot;@boolean1=true或@boolean2=false&quot;**:测试布尔字段。

#### 启用容器 {#enabling-container}

利用此容器，可启用或禁用动态条件中的一组数据。 禁用控件会阻止对其进行编辑。 以下示例说明如何启用“Gender”字段值中的控件：

```
<container type="enabledGroup" enabledIf="@gender=1">
  ...
</container>
<container type="enabledGroup" enabledIf="@gender=2">
  ...
</container>
```

启用容器由&#x200B;**type=&quot;enabledGroup&quot;**&#x200B;属性定义。 **enabledIf**&#x200B;属性包含激活条件。

## 编辑链接 {#editing-a-link}

请记住，链接在数据架构中声明如下：

```
<element label="Company" name="company" target="cus:company" type="link"/>
```

链接在其输入表单中的编辑控制如下：

![](assets/d_ncs_integration_form_exemple9.png)

```
<input xpath="company"/>
```

可通过编辑字段访问目标选择。 输入由提前键入辅助，以便能够从输入的前几个字符中轻松找到目标元素。 然后，根据目标架构中定义的&#x200B;**计算字符串**&#x200B;进行搜索。 如果在控件中进行验证后架构不存在，则会显示即时创建目标的确认消息。 确认后，将在目标表中创建新记录，并将其与链接关联。

下拉列表用于从已创建的记录列表中选择目标元素。

**[!UICONTROL Modify the link]**（文件夹）图标会启动一个选择表单，其中包含目标元素列表和过滤器区域：

![](assets/d_ncs_integration_form_exemple10.png)

**[!UICONTROL Edit link]**（放大镜）图标会启动链接元素的编辑表单。 默认情况下，目标模式的键上会推导使用的形式。 通过&#x200B;**form**&#x200B;属性，您可以强制指定编辑表单的名称(例如，“cus:company2”)。

您可以通过在输入表单的链接定义中添加&#x200B;**`<sysfilter>`**&#x200B;元素来限制目标元素的选择：

```
<input xpath="company">
  <sysFilter>
    <condition expr="[location/@city] =  'Newton"/>
  </sysFilter>
</input>
```

您还可以使用&#x200B;**`<orderby>`**&#x200B;元素对列表进行排序：

```
<input xpath="company">
  <orderBy>
    <node expr="[location/@zipCode]"/>
  </orderBy>
</input>
```

### 控制属性 {#control-properties}

* **noAutoComplete**:禁用“提前键入”（值为“true”）
* **createMode**:如果链接不存在，则即时创建该链接。可能的值包括：

   * **无**:禁用创建。如果链接不存在，则会显示错误消息
   * **内联**:创建与编辑字段中的内容的链接
   * **版本**:在链接上显示编辑表单。验证表单后，将保存数据（默认模式）

* **noZoom**:链接上没有编辑窗体（值为“true”）
* **表单**:覆盖目标元素的编辑表单

## 链接列表 {#list-of-links}

在数据架构中作为收集元素输入的链接(unbound=&quot;true&quot;)必须经过列表才能查看与其关联的所有元素。

其原理是显示具有优化数据加载的链接元素列表（通过数据批量下载，仅当列表可见时才执行）。

架构中的集合链接示例：

```
<element label="Events" name="rcpEvent" target="cus:event" type="link" unbound="true">
...
</element>
```

其输入形式的列表：

![](assets/d_ncs_integration_form_exemple11.png)

```
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

列表控件由&#x200B;**type=&quot;linklist&quot;**&#x200B;属性定义。 列表路径必须引用集合链接。

列通过列表的&#x200B;**`<input>`**&#x200B;元素进行声明。 **xpath**&#x200B;属性引用目标架构中字段的路径。

带有标签的工具栏（在架构的链接上定义）会自动置于列表上方。

该列表可通过&#x200B;**[!UICONTROL Filters]**&#x200B;按钮进行过滤，并配置为添加列和对列进行排序。

通过&#x200B;**[!UICONTROL Add]**&#x200B;和&#x200B;**[!UICONTROL Delete]**&#x200B;按钮，您可以在链接上添加和删除集合元素。 默认情况下，添加元素会启动目标架构的编辑表单。

当列表&#x200B;**`<input>`**&#x200B;标记上的&#x200B;**zoom=&quot;true&quot;**&#x200B;属性已完成时，会自动添加&#x200B;**[!UICONTROL Detail]**&#x200B;按钮：它允许您启动选定行的编辑表单。

在加载列表时，可以应用过滤和排序：

```
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
  <orderBy>
    <node expr="@date" sortDesc="true"/>
  </orderBy>
</input>
```

### 关系表 {#relationship-table}

使用关系表可以将两个表与N-N基数链接。 关系表仅包含两个表的链接。

因此，向列表添加元素应允许您从关系表中的两个链接之一完成列表。

模式中的关系表示例：

```
<srcSchema name="subscription" namespace="cus">
  <element name="recipient" type="link" target="cus:recipient" label="Recipient"/>
  <element name="service" type="link" target="cus:service" label="Subscription service"/>
</srcSchema>
```

例如，我们首先从“cus:recipient”架构的输入形式开始。 该列表必须显示与服务订阅的关联，并且必须允许您通过选择现有服务来添加订阅。

![](assets/d_ncs_integration_form_exemple12.png)

```
<input type="linklist" xpath="subscription" xpathChoiceTarget="service" xpathEditTarget="service" zoom="true">
  <input xpath="recipient"/>
  <input xpath="service"/>
</input>
```

通过&#x200B;**xpathChoiceTarget**&#x200B;属性，您可以从输入的链接中启动选择表单。 创建关系表记录将自动更新指向当前收件人和选定服务的链接。

>[!NOTE]
>
>通过&#x200B;**xpathEditTarget**&#x200B;属性，您可以在输入的链接上强制编辑所选行。

### 列表属性 {#list-properties}

* **noToolbar**:隐藏工具栏（其值为“true”）
* **toolbarCaption**:过载工具栏标签
* **工具栏对齐**:修改工具栏的垂直或水平几何(可能值：&quot;vertical&quot;|&quot;horizontal&quot;)
* **img**:显示与列表关联的图像
* **表单**:覆盖目标元素的编辑表单
* **缩放**:添加用 **[!UICONTROL Zoom]** 于编辑目标元素的按钮
* **xpathEditTarget**:设置对输入的链接的编辑
* **xpathChoiceTarget**:此外，在输入的链接上启动选择表单

## 内存列表控件 {#memory-list-controls}

内存列表允许您使用列表数据预加载功能编辑收集元素。 此列表无法过滤或配置。

这些列表用于XML映射的集合元素或低容量链接。

### 列列表 {#column-list}

此控件显示可编辑的列列表，其中的工具栏包含“添加”和“删除”按钮。

![](assets/d_ncs_integration_form_exemple13.png)

```
<input xpath="rcpEvent" type="list">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

必须使用&#x200B;**type=&quot;list&quot;**&#x200B;属性填充列表控件，并且列表的路径必须引用集合元素。

列在列表的子&#x200B;**`<input>`**&#x200B;标记中声明。 列标签和大小可以使用&#x200B;**标签**&#x200B;和&#x200B;**colSize**&#x200B;属性强制设置。

>[!NOTE]
>
>将&#x200B;**ordered=&quot;true&quot;**&#x200B;属性添加到数据架构中的收集元素时，会自动添加排序箭头。

工具栏按钮可水平对齐：

![](assets/d_ncs_integration_form_exemple14.png)

```
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

**toolbarCaption**&#x200B;属性强制工具栏的水平对齐方式并输入列表上方的标题。

#### 放大列表 {#zoom-in-a-list}

可以在单独的编辑表单中输入列表中数据的插入和编辑。

![](assets/d_ncs_integration_form_exemple15.png)

```
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true" zoomOnAdd="true">
  <input xpath="@label"/>
  <input xpath="@date"/>

  <form colcount="2" label="Event">
    <input xpath="@label"/>
    <input xpath="@date"/>
  </form>
</input>
```

在列表定义下，从`<form>`元素填写编辑表单。 其结构与输入形式的结构相同。 当列表&#x200B;**`<input>`**&#x200B;标记上的&#x200B;**zoom=&quot;true&quot;**&#x200B;属性已完成时，会自动添加&#x200B;**[!UICONTROL Detail]**&#x200B;按钮。 此属性允许您启动选定行的编辑表单。

>[!NOTE]
>
>添加&#x200B;**zoomOnAdd=&quot;true&quot;**&#x200B;属性会强制在插入列表元素时调用编辑表单。

### 列表属性 {#list-properties-1}

* **noToolbar**:隐藏工具栏（其值为“true”）
* **toolbarCaption**:过载工具栏标签
* **工具栏对齐**:修改工具栏的位置(可能值：&quot;vertical&quot;|&quot;horizontal&quot;)
* **img**:显示与列表关联的图像
* **表单**:覆盖目标元素的编辑表单
* **缩放**:添加用 **[!UICONTROL Zoom]** 于编辑目标元素的按钮
* **zoomOnAdd**:在添加的
* **xpathChoiceTarget**:此外，在输入的链接上启动选择表单

## 不可编辑的字段 {#non-editable-fields}

要显示字段并阻止对其进行编辑，请使用&#x200B;**`<value>`**&#x200B;标记或完成&#x200B;**`<input>`**&#x200B;标记上的&#x200B;**readOnly=&quot;true&quot;**&#x200B;属性。

“性别”字段示例：

![](assets/d_ncs_integration_form_exemple16.png)

```
<value value="@gender"/>
<input xpath="@gender" readOnly="true"/>
```

## 单选按钮 {#radio-button}

单选按钮允许您从多个选项中进行选择。 **`<input>`**&#x200B;标记用于列出可能的选项，而&#x200B;**checkedValue**&#x200B;属性指定与选项关联的值。

“性别”字段示例：

```
<input type="RadioButton" xpath="@gender" checkedValue="0" label="Choice 1"/>
<input type="RadioButton" xpath="@gender" checkedValue="1" label="Choice 2"/>
<input type="RadioButton" xpath="@gender" checkedValue="2" label="Choice 3"/>
```

![](assets/d_ncs_integration_form_exemple17.png)

## 复选框 {#checkbox}

复选框反映布尔状态（选中或未选中）。 默认情况下，此控件由“Boolean”(true/false)字段使用。 默认值为0或1的变量可与此按钮关联。 此值可通过&#x200B;**checkValue**&#x200B;属性进行重载。

```
<input xpath="@boolean1"/>
<input xpath="@field1" type="checkbox" checkedValue="Y"/>
```

![](assets/d_ncs_integration_form_exemple20.png)

## 导航层次结构编辑 {#navigation-hierarchy-edit}

此控件在要编辑的一组字段上构建树。

要编辑的控件将分组到树控件&#x200B;**`<input>`**&#x200B;标记下输入的&#x200B;**`<container>`**&#x200B;中：

```
<input nolabel="true" type="treeEdit">
  <container label="Text fields">
    <input xpath="@text1"/>
    <input xpath="@text2"/>
  </container>
  <container label="Boolean fields">
    <input xpath="@boolean1"/>
    <input xpath="@boolean2"/>
  </container>
</input>
```

![](assets/d_ncs_integration_form_exemple18.png)

## 表达式字段 {#expression-field}

表达式字段会从表达式动态更新字段；**`<input>`**&#x200B;标记与&#x200B;**xpath**&#x200B;属性一起使用，用于输入要更新的字段的路径以及包含更新表达式的&#x200B;**expr**&#x200B;属性。

```
<!-- Example: updating the boolean1 field from the value contained in the field with path /tmp/@flag -->
<input expr="Iif([/tmp/@flag]=='On', true, false)" type="expr" xpath="@boolean1"/>
<input expr="[/ignored/@action] == 'FCP'" type="expr" xpath="@launchFCP"/>
```

## 表单上下文 {#context-of-forms}

输入表单的执行初始化包含被编辑实体数据的XML文档。 本文档表示表单的上下文，可用作工作区。

### 更新上下文 {#updating-the-context}

要修改表单的上下文，请使用`<set expr="<value>" xpath="<field>"/>`标记，其中`<field>`是目标字段，`<value>`是更新表达式或值。

`<set>`标记的使用示例：

* **`<set expr="'Test'" xpath="/tmp/@test" />`**:将“测试”值定位在临时位置/tmp/@test1
* **`<set expr="'Test'" xpath="@lastName" />`**:使用“Test”值更新“lastName”属性上的实体
* **`<set expr="true" xpath="@boolean1" />`**:将“boolean1”字段的值设置为“true”
* **`<set expr="@lastName" xpath="/tmp/@test" />`**:更新了“lastName”属性的内容

通过&#x200B;**`<enter>`**&#x200B;和&#x200B;**`<leave>`**&#x200B;标记初始化和关闭表单时，可以更新表单的上下文。

```
<form name="recipient" namespace="cus">
  <enter>
    <set...
  </enter>
  ...
  <leave>
    <set...
  </leave>
</form>
```

>[!NOTE]
>
>`<enter>`和`<leave>`   标记可用于页面的`<container>`（“notebook”和“iconbox”类型）。

### 表达语言 {#expression-language-}

可以在表单定义中使用宏语言来执行条件测试。

如果验证了表达式，**`<if expr="<expression>" />`**&#x200B;标记将执行标记下指定的指令：

```
<if expr="([/tmp/@test] == 'Test' or @lastName != 'Doe') and @boolean2 == true">
  <set xpath="@boolean1" expr="true"/>
</if>
```

与&#x200B;**`<error>`**&#x200B;标记结合的&#x200B;**`<check expr="<condition>" />`**&#x200B;标记会阻止对表单的验证，并在不满足条件时显示错误消息：

```
<leave>
  <check expr="/tmp/@test != ''">
    <error>You must populate the 'Test' field!</error> 
  </check>
</leave>
```

## 向导 {#wizards}

向导会引导您完成页面形式的一组数据输入步骤。 验证表单时，将保存输入的数据。

向导具有以下结构：

```
<form type="wizard" name="example" namespace="cus" img="nms:rcpgroup32.png" label="Wizard example" entity-schema="nms:recipient">
  <container title="Title of page 1" desc="Long description of page 1">
    <input xpath="@lastName"/>
    <input xpath="comment"/>
  </container>
  <container title="Title of page 2" desc="Long description of page 2">
    ...
  </container>
  ...
</form>
```

![](assets/d_ncs_integration_form_exemple19.png)

`<form>`元素上存在&#x200B;**type=&quot;wizard&quot;**&#x200B;属性，该属性允许您在表单结构中定义向导模式。 从`<container>`元素（即`<form>`元素的子元素）中完成页面。 页面的`<container>`元素中填充了标题的标题属性，并且该元素用于在页面标题下显示描述。 会自动添加&#x200B;**[!UICONTROL Previous]**&#x200B;和&#x200B;**[!UICONTROL Next]**&#x200B;按钮，以允许在页面之间浏览。

**[!UICONTROL Finish]**&#x200B;按钮保存输入的数据并关闭表单。

### SOAP方法 {#soap-methods}

可以从页面末尾填充的&#x200B;**`<leave>`**&#x200B;标记中启动SOAP方法执行。

**`<soapcall>`**&#x200B;标记包含对具有以下输入参数的方法的调用：

```
<soapCall name="<name>" service="<schema>">
  <param type="<type>" exprIn="<xpath>"/>  
  ...
</soapCall>
```

服务的名称及其实现架构通过&#x200B;**`<soapcall>`**&#x200B;标记的&#x200B;**name**&#x200B;和&#x200B;**service**&#x200B;属性输入。

有关输入参数的说明，请参见&#x200B;**`<soapcall>`**&#x200B;标记下的&#x200B;**`<param>`**&#x200B;元素。

必须通过&#x200B;**type**&#x200B;属性指定参数类型。 可能的类型如下：

* **字符串**:字符串
* **布尔值**:布尔值
* **字节**:8位整数
* **简短**:16位整数
* **长**:32位整数
* **简短**:16位整数
* **双重**:双精度浮点数
* **DOMElement**:元素类型节点

**exprIn**&#x200B;属性包含要作为参数传递的数据的位置。

**示例**:

```
<leave>
  <soapCall name="RegisterGroup" service="nms:recipient">         
    <param type="DOMElement" exprIn="/tmp/entityList"/>         
    <param type="DOMElement" exprIn="/tmp/choiceList"/>         
    <param type="boolean"    exprIn="true"/>       
  </soapCall>
</leave>
```
