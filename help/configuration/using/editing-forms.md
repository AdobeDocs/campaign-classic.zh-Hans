---
product: campaign
title: 编辑表单
description: 编辑表单
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '1698'
ht-degree: 2%

---


# 编辑表单{#editing-forms}

![](../../assets/common.svg)

## 概述

营销人员和运营人员使用输入表单创建、修改和预览记录。 Forms显示信息的可视表示形式。

您可以创建和修改输入表单：

* 您可以修改默认提交的工厂输入表单。 工厂输入表单基于工厂数据架构。
* 您可以根据定义的数据架构创建自定义输入表单。

Forms是 `xtk:form` 类型。 您可以在 `xtk:form` 架构。 要查看此架构，请选择 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** 中。 有关更多信息 [窗体结构](form-structure.md).

To access input forms, choose **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** from the menu:

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


## 创建简单表单 {#create-simple-form}

要创建表单，请执行以下步骤：

1. 从菜单中，选择 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
1. 单击 **[!UICONTROL New]** 按钮。

   ![](assets/input-form-create-1.png)

1. 指定表单属性：

   * Specify the form name and the namespace.

      表单名称和命名空间可以匹配相关数据架构。  This example shows a form for the `cus:order` data schema:

      ```xml
      <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
        […]
      </form>
      ```

      或者，您也可以在 `entity-schema` 属性。

      ```xml
      <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
        […]
      </form>
      ```

   * 指定要在表单上显示的标签。
   * （可选）指定表单类型。 如果未指定表单类型，则默认使用控制台屏幕类型。

      ![](assets/input-form-create-2.png)

      如果要设计多页面表单，则可以在 `<form>` 元素，并在容器中指定类型。

1. 单击 **[!UICONTROL Save]**。

1. 插入表单元素。

   例如，要插入输入字段，请使用 `<input>` 元素。 设置 `xpath` 属性作为XPath表达式。 [阅读更多](schema-structure.md#referencing-with-xpath)。

   此示例显示基于 `nms:recipient` 架构。

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. 如果表单基于特定架构类型，则可以查找此架构的字段：

   1. 单击 **[!UICONTROL Insert]** > **[!UICONTROL Document fields]**.

      ![](assets/input-form-create-4.png)

   1. 选择字段并单击 **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. （可选）指定字段编辑器。

   默认的字段编辑器与每个数据类型关联：
   * 对于日期类型字段，表单显示输入日历。
   * 对于枚举类型字段，表单会显示选择列表。

   您可以使用以下字段编辑器类型：

   | 字段编辑器 | 表单属性 |
   | --- | --- |
   | 单选按钮 | `type="radiobutton"` |
   | 复选框 | `type="checkbox"` |
   | 编辑树 | `type="tree"` |

   有关更多信息 [内存列表控件](form-structure.md#memory-list-controls).

1. （可选）定义对以下字段的访问权限：

   | 元素 | 属性 | 说明 |
   | --- | --- | --- |
   | `<input>` | `read-only:"true"` | 提供对字段的只读访问权限 |
   | `<container>` | `type="visibleGroup" visibleIf="`*edit-expr*`"` | 有条件地显示一组字段 |
   | `<container>` | `type="enabledGroup" enabledIf="`*edit-expr*`"` | 有条件地启用一组字段 |

   示例:

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. （可选）使用容器将字段分组为多个部分。

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## 创建多页面表单 {#create-multipage-form}

您可以创建多页面表单。 您还可以将表单嵌套在其他表单中。

### 创建 `iconbox` 表单

使用 `iconbox` 表单类型，用于在表单左侧显示图标，使用户转到表单中的不同页面。

![](assets/iconbox_form_preview.png)

将现有表单的类型更改为 `iconbox`，请执行以下步骤：

1. 更改 `type` 属性 `<form>` 元素 `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. 为每个表单页面设置一个容器：

   1. 添加 `<container>` 元素作为的子项 `<form>` 元素。
   1. 要为图标定义标签和图像，请使用 `label` 和 `img` 属性。

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```
   或者，移除 `type="frame"` 属性 `<container>` 元素。

### 创建笔记本表单

使用 `notebook` 表单类型，用于在表单顶部显示选项卡，可将用户引导至不同的页面。

![](assets/notebook_form_preview.png)

将现有表单的类型更改为 `notebook`，请执行以下步骤：

1. 更改 `type` 属性 `<form>` 元素 `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. 为每个表单页面添加一个容器：

   1. 添加 `<container>` 元素作为的子项 `<form>` 元素。
   1. 要定义图标的标签和图像，请使用 `label` 和 `img` 属性。

   ```xml
     <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
         <container label="General">
             <input xpath="@label"/>
             <input xpath="@name"/>
             […]
         </container>
         <container label="Details">
             <input xpath="@address"/>
             […]
         </container>
         <container label="Services">
             […]
         </container>
     </form>
   ```

   或者，移除 `type="frame"` 属性 `<container>` 元素。

### 嵌套表单

您可以将表单嵌套在其他表单中。 例如，您可以在iconbox表单中嵌套笔记本表单。

嵌套级别控制导航。 用户可以向下展开到子表单。

要将表单嵌套在另一个表单中，请插入 `<container>` 元素并设置 `type` 属性。 对于顶级表单，您可以在外部容器或 `<form>` 元素。

### 示例

此示例显示了一个复杂的表单：

* 顶级表单是一个iconbox表单。 此表单包含两个标有 **常规** 和 **详细信息**.

   因此，外部窗体会显示 **常规** 和 **详细信息** 页面。 要访问这些页面，用户需单击表单左侧的图标。

* 子表单是嵌套在 **常规** 容器。 该子表单包括两个被标记的容器 **名称** 和 **联系人**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

因此， **常规** 外部表单的页面显示 **名称** 和 **联系人** 选项卡。

![](assets/nested_forms_preview.png)

要将表单嵌套在另一个表单中，请插入 `<container>` 元素并设置 `type` 属性。 对于顶级表单，您可以在外部容器或 `<form>` 元素。

### 示例

此示例显示了一个复杂的表单：

* 顶级表单是一个iconbox表单。 此表单包含两个标有 **常规** 和 **详细信息**.

   因此，外部窗体会显示 **常规** 和 **详细信息** 页面。 要访问这些页面，用户需单击表单左侧的图标。

* 子表单是嵌套在 **常规** 容器。 该子表单包括两个被标记的容器 **名称** 和 **联系人**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

因此， **常规** 外部表单的页面显示 **名称** 和 **联系人** 选项卡。

![](assets/nested_forms_preview.png)



## 修改工厂输入表单 {#modify-factory-form}

要修改工厂表单，请执行以下步骤：

1. 修改工厂输入表单：

   1. 从菜单中，选择 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
   1. Select an input form and modify it.

   您可以扩展工厂数据架构，但无法扩展工厂输入表单。 我们建议您直接修改工厂输入表单，而无需重新创建。 在软件升级期间，您在工厂输入表单中所做的修改将与升级合并。 如果自动合并失败，您可以解决冲突。 [阅读更多](../../production/using/upgrading.md#resolving-conflicts)。

   例如，如果扩展了工厂架构，并且添加了一个附加字段，则可以将此字段添加到相关的工厂表单中。

## 验证表单 {#validate-forms}

您可以在表单中包含验证控件。

### 授予字段的只读访问权限

要授予字段的只读访问权限，请使用 `readOnly="true"` 属性。 例如，您可能希望显示记录的主键，但具有只读访问权限。 [阅读更多](form-structure.md#non-editable-fields)。

在本例中，主键(`iRecipientId`) `nms:recipient` 架构以只读访问方式显示：

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### 检查必填字段

您可以检查必填信息：

* 使用 `required="true"` 属性。
* 使用 `<leave>` 节点来检查这些字段并显示错误消息。

在此示例中，需要提供电子邮件地址，如果用户未提供此信息，则会显示一条错误消息：

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

有关更多信息 [表达式字段](form-structure.md#expression-field) 和 [表单上下文](form-structure.md#context-of-forms).

### 验证值

您可以使用JavaScript SOAP调用从控制台验证表单数据。 例如，使用这些调用进行复杂的验证，以根据授权值列表检查值。 [阅读更多](form-structure.md#soap-methods)。

1. 在JS文件中创建验证函数。

   示例:

   ```js
   function nms_recipient_checkValue(value)
   {
     logInfo("checking value " + value)
     if (…)
     {
       logError("Value " + value + " is not valid")
     }
     return 1
   }
   ```

   在本例中，函数名为 `checkValue`. 此函数用于检查 `recipient` 中的数据类型 `nms` 命名空间。 正在检查的值将被记录。 如果值无效，则会记录一条错误消息。 如果值有效，则返回值1。

   您可以使用返回的值修改表单。

1. 在表单中，将 `<soapCall>` 元素 `<leave>` 元素。

   在此示例中，使用SOAP调用来验证 `@valueToCheck` 字符串：

   ```xml
   <form name="recipient" (…)>
   (…)
     <leave>
       <soapCall name="checkValue" service="nms:recipient">
         <param exprIn="@valueToCheck" type="string"/>
       </soapCall>
     </leave>
   </form>
   ```

   在本例中， `checkValue` 方法和 `nms:recipient` 使用服务：

   * 服务是命名空间和数据类型。
   * 方法是函数名称。 名称区分大小写。

   同步执行调用。

   将显示所有例外。 如果您使用 `<leave>` 元素，则用户在验证输入的信息之前无法保存表单。

此示例展示了如何从表单中发起服务调用：

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

在此示例中，输入的是ID，它是主键。 当用户填写此ID的表单时，将使用此ID作为输入参数进行SOAP调用。 输出是一个写入此字段的布尔值： `/tmp/@count`. 您可以在表单中使用此布尔值。 有关更多信息 [表单上下文](form-structure.md#context-of-forms).
