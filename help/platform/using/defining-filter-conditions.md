---
product: campaign
title: 定义筛选条件
description: 定义筛选条件
feature: Query Editor
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: b62e23e5-f1b7-44c4-82d9-95c6b3240352
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '3304'
ht-degree: 34%

---

# 定义过滤器条件{#defining-filter-conditions}



## 选择运算符 {#choosing-the-operator}

在筛选条件中，您需要使用运算符将两个值链接在一起。

![](assets/query_editor_nveau_96.png)

以下是可用的运算符列表：

<table> 
 <thead> 
  <tr> 
   <th> 运算符<br /> </th> 
   <th> 用途<br /> </th> 
   <th> 示例<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">等于</span> <br /> </td> 
   <td> 返回与在第二个“值”列中输入的数据相同的结果。<br /> </td> 
   <td> <strong>姓氏(@lastName)等于“Jones”</strong>，将仅返回姓氏为Jones的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">大于</span> <br /> </td> 
   <td> 返回大于输入值的值。<br /> </td> 
   <td> <strong>年龄(@age)大于50</strong>，将返回所有大于“50”的值，如“51”、“52”等。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">小于</span> <br /> </td> 
   <td> 返回小于输入值的值。<br /> </td> 
   <td> <strong>创建日期(@created)早于“DaysAgo(100)”</strong>，将返回之前100天创建的所有收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">大于或等于</span> <br /> </td> 
   <td> 返回所有等于或大于输入值的值。<br /> </td> 
   <td> <strong>年龄(@age)大于或等于“30”</strong>，将返回所有30岁或以上的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">小于或等于</span> <br /> </td> 
   <td> 返回等于或小于输入值的所有值。<br /> </td> 
   <td> <strong>年龄(@age)小于或等于“60”</strong>，将返回所有60岁或以下的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不等于</span> <br /> </td> 
   <td> 返回与输入值不相同的所有值。<br /> </td> 
   <td> <strong>等于“英语”的语言(@language)</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">开头为</span> <br /> </td> 
   <td> 返回以输入值开头的结果。<br /> </td> 
   <td> <strong>帐户# (@account)以“32010”开头。</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">开头不是</span> <br /> </td> 
   <td> 返回不以输入值开头的结果<br /> </td> 
   <td> <strong>帐户# (@account)不以“20”开头</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">包含</span> <br /> </td> 
   <td> 返回至少包含输入值的结果。<br /> </td> 
   <td> <strong>电子邮件域(@domain)包含“mail”</strong>，将返回包含“mail”的所有域名。 因此，也会返回“gmail.com”域。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不包含</span> <br /> </td> 
   <td> 返回不包含输入值的结果。<br /> </td> 
   <td> <strong>电子邮件域(@domain)不包含“vo”</strong>. 在这种情况下，将不返回包含“vo”的域名。 “voila.fr”域名将不会显示在结果中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">相似</span> <br /> </td> 
   <td> <span class="uicontrol">相似</span>与<span class="uicontrol">包含</span>运算符非常相似。它可让您插入 <span class="uicontrol">%</span> 值中的通配符。<br /> </td> 
   <td> <strong>姓氏(@lastName)，如“Jon%s”</strong>. 在本例中，如果操作员忘记了“n”和“s”之间缺少的字母，则使用通配符作为“绝招”来查找名称“Jones”。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不相似</span> <br /> </td> 
   <td> 类似于 <span class="uicontrol">点赞</span> . 用于不恢复输入的值。 在本例中，输入的值也必须包含 <span class="uicontrol">%</span> 个通配符字段。<br /> </td> 
   <td> <strong>姓氏(@lastName)不像“Smi%h”</strong>. 在此，将不会返回姓氏为“Smi%h”的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">为空</span> <br /> </td> 
   <td> 在这种情况下，我们要查找的结果与第二个“值”列中的空值匹配。<br /> </td> 
   <td> <strong>移动设备(@mobilePhone)为空</strong> 返回所有没有手机号码的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不为空</span> <br /> </td> 
   <td> 与的工作方式相反 <span class="uicontrol">为空</span> 运算符。 无需在第二个“值”列中输入数据。<br /> </td> 
   <td> <strong>电子邮件(@email)不为空</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">包含在</span> <br /> </td> 
   <td> 返回指定值中包含的结果。 这些值必须以逗号分隔。<br /> </td> 
   <td> <strong>出生日期(@birthDate)已列入`1979/10/1979,12/10/1984`</strong>，将返回这些日期之间出生的收件人。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中未包含</span> <br /> </td> 
   <td> 的工作方式与 <span class="uicontrol">包含在</span> 运算符。 在本例中，我们要根据输入的值排除收件人。<br /> </td> 
   <td> <strong>出生日期(@birthDate)不包括1979/12/10/1984</strong>. 与上一个示例不同，不会返回这些日期内出生的收件人。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 使用AND、OR，但 {#using-and--or--except}

对于使用多个筛选条件的查询，需要定义条件之间的链接。 有三种可能的链接：

* **[!UICONTROL And]** 可让您组合两个过滤条件，
* **[!UICONTROL Or]** 让你提供替代方案，
* **[!UICONTROL Except]** 用于定义例外。

单击 **[!UICONTROL And]** （默认提供）并从下拉列表中选择。

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**：添加条件并启用过度过滤。
* **[!UICONTROL Or]**：添加条件并启用过度过滤。

  以下示例允许您查找其电子邮件域包含“orange.co.uk”或其邮政编码以“NW”开头的收件人。

  ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**：如果您有两个过滤器，但第一个过滤器未返回值，则此类型的链接会创建一个例外。

  在以下示例中，我们希望返回其电子邮件域包含“orange.co.uk”的收件人，除非收件人的姓氏为“Smith”。

  ![](assets/query_condition_modif_03.png)

此示例显示了一个用于显示的过滤器：说西班牙语的收件人、使用手机号码的女性收件人、没有帐号且公司名称以字母“N”开头的收件人。

![](assets/query_editor_nveau_31.png)

## 区分条件的优先级 {#prioritizing-conditions}

本节将介绍如何借助工具栏中的蓝色箭头来排列条件的优先级。

* 通过指向右侧的箭头，可以向过滤器添加一定级别的圆括号。
* 通过指向左侧的箭头，可从筛选器中删除选定的括号级别。

  ![](assets/query_condition_modif_04.png)

* 垂直箭头允许您移动条件，从而更改其执行顺序。

此示例说明如何使用箭头删除括号级别。 从以下筛选条件开始： **[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**.

将光标放在 **[!UICONTROL Gender (@gender) equal to Male]** 过滤条件，然后单击 **[!UICONTROL Remove a parenthesis level]** 箭头。

![](assets/query_editor_nveau_32.png)

此 **[!UICONTROL Gender (@gender) equal to Male]** 条件已移出其圆括号。 它已经达到与“伦敦与金融城相等”的水平。 这些条件链接在一起(**[!UICONTROL And]**)。

## 选择要提取的数据 {#selecting-data-to-extract}

可用字段因表而异。 所有字段都存储在主节点(称为 **[!UICONTROL Main element]**. 在以下示例中，可用字段位于收件人表中。 字段始终按字母顺序显示。

所选字段的详细信息将显示在窗口底部。 例如， **[!UICONTROL Email domain]** 字段是 **[!UICONTROL Calculated SQL field]** 其扩展为 **[!UICONTROL (@domain)]**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>使用 **[!UICONTROL Search]** 用于查找可用字段的工具。

双击可用字段以将其添加到输出列。 在查询结束时，每个选定的字段都会在 **[!UICONTROL Data preview]** 窗口。

![](assets/query_editor_nveau_01.png)

默认情况下，不显示高级字段。 单击 **[!UICONTROL Display advanced fields]** 字段的右下角显示所有内容。 再次单击可返回到前视图。

例如，在收件人表中，高级字段为 **布尔值1**， **[!UICONTROL Boolean 2]**， **[!UICONTROL Boolean 3]**， **[!UICONTROL Foreign key of "Folder" link]**，等等。

以下示例显示了收件人表的高级字段。

![](assets/query_editor_nveau_53.png)

各种类别的字段：

<table> 
 <thead> 
  <tr> 
   <th> 图标<br /> </th> 
   <th> 说明<br /> </th> 
   <th> 示例<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> 简单字段<br /> </td> 
   <td> 电子邮件、性别等。<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> 主键。 此SQL字段用于标识表中的记录。<br /> </td> 
   <td> 标识符收件人为主键，标识符按定义是唯一的。<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> 外键。 用作指向另一个表的链接。<br /> </td> 
   <td> 收件人外键、服务外键等。<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> 计算字段。 根据请求，使用数据库中的值计算此类型的字段。<br /> </td> 
   <td> 年龄、电子邮件域等<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> 包含长文本的字段。<br /> </td> 
   <td> 评论、完整地址等<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> 已编制索引的SQL字段。 <br /> </td> 
   <td> 全名、ISO代码等。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

链接到表和收集要素：

<table> 
 <thead> 
  <tr> 
   <th> 图标<br /> </th> 
   <th> 说明<br /> </th> 
   <th> 示例<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> 尤其是指向表的链接。 这些规则与1-1类型关联一致。 源表的出现只能与目标表的一个出现一致。 例如，一个国家/地区只能链接一个收件人。<br /> </td> 
   <td> 文件夹、州/省、国家/地区等。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> 特定表上的收集要素。 它们与1-N类型关联一致。 一个源表格出现次数可以与目标表格的多个出现次数一致，但目标表格出现次数可以只与源表格出现次数一致。 例如，一位收件人可以订阅“n”个订阅信。<br /> </td> 
   <td> 订阅、列表、排除日志等。<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* 使用 **[!UICONTROL Add]** 按钮（侧图标栏上方），以添加要在其中编辑表达式的输出列。 有关编辑表达式的详细信息，请参阅 [本节](#building-expressions).
>* 通过单击红色的“x”删除输出列(**删除**)。
>* 使用箭头更改输出列的顺序。
>* 此 **[!UICONTROL Distribution of values]** 用于查看所选字段值的分布情况（例如，链接到收件人城镇、收件人语言等的分布情况）。

## 创建计算字段 {#creating-calculated-fields}

如有必要，请在设置数据格式期间添加列。 计算字段将列添加到数据预览部分。 单击 **[!UICONTROL Add a calculated field]**。

![](assets/query_editor_nveau_43.png)

有四种类型的计算字段：

* **[!UICONTROL Fixed string]**：用于添加字符串。

  ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**：计算字段的值将字符串和JavaScript指令组合在一起。

  ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**：计算字段的值是JavaScript函数求值的结果。 可以键入返回的值（数字、日期等）。

  ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**：利用此类型的字段，可使用/修改新列中某个输出列的内容。

  可以使用列的源值并为它指定目标值。 此目标值将显示在新输出列中。

  添加计算字段类型的示例 **[!UICONTROL Enumerations]** 可用，请参阅 [本节](../../workflow/using/adding-enumeration-type-calculated-field.md).

  ![](assets/query_editor_nveau_63.png)

  此 **[!UICONTROL Enumerations]** 类型计算字段可以包括4个条件：

   * **[!UICONTROL Keep the source value]** 将源值还原到目标而不更改它。
   * **[!UICONTROL Use the following value]** 允许您为未定义的源值输入默认目标值。
   * **[!UICONTROL Generate a warning and continue]** 警告用户无法更改源值。
   * **[!UICONTROL Generate an error and reject the line]** 阻止计算和导入该行。

单击 **[!UICONTROL Detail of calculated field]** 以查看插入字段的详细信息。

要删除此计算字段，请单击 **[!UICONTROL Remove the calculated field]** 十字。

![](assets/query_editor_nveau_58.png)

## 构建表达式 {#building-expressions}

表达式编辑工具允许您使用表达式计算聚合、生成函数或编辑公式。

以下示例说明如何对主键运行计数。

应用以下步骤：

1. 单击 **[!UICONTROL Add]** 在 **[!UICONTROL Data to extract]** 窗口。 在 **[!UICONTROL Formula type]** 窗口中，选择公式类型以输入表达式。

   有多种类型的公式可用： **[!UICONTROL Field only]**， **[!UICONTROL Aggregate]**， **[!UICONTROL Expression]**.

   选择 **[!UICONTROL Process on an aggregate function]**、和 **[!UICONTROL Count]**. 单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_nveau_54.png)

1. 计算主键。

   ![](assets/query_editor_nveau_88.png)

以下是 **[!UICONTROL Formula types]** 窗口：

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** 可让您返回 **[!UICONTROL Field to select]** 窗口。
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**. 以下是聚合使用的一些示例：

   * **[!UICONTROL Count]** 用于运行主键计数。
   * **[!UICONTROL Sum]** 允许您合计客户在一年以上的所有购买次数。
   * **[!UICONTROL Maximum value]** 允许您查找购买最多“n”个产品的客户。
   * **[!UICONTROL Minimum value]** 允许您对客户进行排序，并查找最近订阅了选件的客户。
   * **[!UICONTROL Average]**. 此函数允许您计算收件人的平均年龄。

     此 **[!UICONTROL Distinct]** 框用于恢复列的唯一值和非零值。 例如，您可以恢复所有收件人的跟踪日志，这些跟踪日志将更改为值1，因为它们都涉及同一收件人。

1. **[!UICONTROL Expression]** 打开 **[!UICONTROL Edit the expression]** 窗口。 这样，您就可以检测包含太多数字（可能是输入错误）的电话号码。

   ![](assets/query_editor_nveau_71.png)

   有关所有可用函数的列表，请参阅 [函数列表](#list-of-functions).

## 函数列表 {#list-of-functions}

如果 **[!UICONTROL Expression]** 选择了类型公式，您将被带到“编辑表达式”窗口。 可以将各种类别的函数关联到可用字段： **[!UICONTROL Aggregates]**， **[!UICONTROL String]**， **[!UICONTROL Date]**， **[!UICONTROL Numerical]**， **[!UICONTROL Currency]**， **[!UICONTROL Geomarketing]**， **[!UICONTROL Windowing function]** 和 **[!UICONTROL Others]**.

表达式编辑器如下所示：

![](assets/s_ncs_user_filter_define_expression.png)

它允许您选择数据库表中的字段并向它们添加高级函数。 可以使用以下函数：

**聚合**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>语法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>平均</strong><br /> </td> 
   <td> 返回数字类型列的平均值<br /> </td> 
   <td> 平均(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>计数</strong><br /> </td> 
   <td> 计算列的非空值<br /> </td> 
   <td> Count(&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>全部计数</strong><br /> </td> 
   <td> 计算返回的值（所有字段）<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Countdistinct</strong><br /> </td> 
   <td> 计算列的不同非空值<br /> </td> 
   <td> Countdistinct(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Max</strong><br /> </td> 
   <td> 返回数字、字符串或日期类型列的最大值<br /> </td> 
   <td> Max(&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>最小值</strong><br /> </td> 
   <td> 返回数字、字符串或日期类型列的最小值<br /> </td> 
   <td> Min(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>标准开发</strong><br /> </td> 
   <td> 返回数字、字符串或日期列的标准偏差<br /> </td> 
   <td> StdDev(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>总和</strong><br /> </td> 
   <td> 返回数字、字符串或日期类型列的值的总和<br /> </td> 
   <td> Sum(&lt;value&gt;)<br /></td> 
  </tr> 
 </tbody> 
</table>

**字符串**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>语法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> 指示所有参数是否为非 null 且不为空<br /> </td> 
   <td> AllNonNull2(&lt;string&gt;， &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> 指示所有参数是否为非 null 且不为空<br /> </td> 
   <td> AllNonNull3(&lt;string&gt;， &lt;string&gt;， &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> 返回字符串中第一个字符的ASCII值。<br /> </td> 
   <td> Ascii(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> 返回与 ASCII 代码"n"对应的字符<br /> </td> 
   <td> Char(&lt;number&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> 返回字符串1中字符串2的位置。<br /> </td> 
   <td> Charindex(&lt;string&gt;， &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> 返回字符串的 n（从 1 到 n）行<br /> </td> 
   <td> GetLine(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> 如果前两个参数相等，则返回第三个参数。 如果不能，则返回最后一个参数<br /> </td> 
   <td> IfEquals(&lt;string&gt;， &lt;string&gt;， &lt;string&gt;， &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> 指示作为参数传递的 Memo 是否为 null<br /> </td> 
   <td> IsMemoNull(&lt;memo&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> 将作为参数传递的字符串连接起来。 如有必要，在字符串之间添加空格。<br /> </td> 
   <td> JuxtWords(&lt;string&gt;， &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> 将作为参数传递的字符串连接起来。 如有必要，在字符串之间添加空格<br /> </td> 
   <td> JuxtWords3(&lt;string&gt;， &lt;string&gt;， &lt;string&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> 返回左侧的已完成字符串<br /> </td> 
   <td> LPad(&lt;string&gt;， &lt;number&gt;， &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> 返回字符串的前 n 个字符<br /> </td> 
   <td> Left(&lt;string&gt;， &lt;number&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> 返回字符串的长度<br /> </td> 
   <td> Length(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> 以小写形式返回字符串<br /> </td> 
   <td> Lower(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> 删除字符串左侧的空格<br /> </td> 
   <td> Ltrim(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> 返回字符串以十六进制表示的 MD5 键值<br /> </td> 
   <td> Md5Digest(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> 指定 Memo 是否包含作为参数传递的字符串<br /> </td> 
   <td> MemoContains(&lt;memo&gt;， &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> 返回右侧的已完成字符串<br /> </td> 
   <td> RPad(&lt;string&gt;， &lt;number&gt;， &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> 返回字符串的最后 n 个字符<br /> </td> 
   <td> Right(&lt;字符串&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> 删除字符串右侧的空格<br /> </td> 
   <td> Rtrim(&lt;字符串&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> 以大写方式返回带每个单词的第一个字母的字符串<br /> </td> 
   <td> Smart(&lt;字符串&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> 提取从字符串的字符n1开始且长度为n2的子字符串<br /> </td> 
   <td> Substring(&lt;字符串&gt;, &lt;偏移&gt;, &lt;长度&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> 将数字转换为字符串<br /> </td> 
   <td> ToString(&lt;number&gt;， &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> 返回以大写表示的字符串<br /> </td> 
   <td> Upper(&lt;字符串&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> 如果其他两个参数相等，则返回作为参数传递的链接的外键<br /> </td> 
   <td> VirtualLink(&lt;数字&gt;, &lt;数字&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> 如果其他两个参数相等，则返回作为参数传递的链接的外键（文本）<br /> </td> 
   <td> VirtualLinkStr(&lt;字符串&gt;, &lt;数字&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> 返回字符串大小<br /> </td> 
   <td> dataLength(&lt;string&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**日期**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>语法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> 向日期添加天数<br /> </td> 
   <td> AddDays(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> 向日期添加小时数<br /> </td> 
   <td> AddHours(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> 向日期添加分钟数<br /> </td> 
   <td> AddMinutes(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> 向日期添加月数<br /> </td> 
   <td> AddMonths(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> 向日期添加秒数<br /> </td> 
   <td> AddSeconds(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> 向日期添加年数<br /> </td> 
   <td> AddYears(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> 仅返回日期（且时间为00:00）*<br /> </td> 
   <td> DateOnly(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Day</strong><br /> </td> 
   <td> 返回表示日期天数的数字<br /> </td> 
   <td> Day(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> 返回日期年份中的天数<br /> </td> 
   <td> DayOfYear(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> 返回对应于当前日期n天的日期<br /> </td> 
   <td> DaysAgo(&lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> 返回对应于当前日期n天的日期（整数yyyymmdd）<br /> </td> 
   <td> DaysAgoInt(&lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> 两个日期之间的天数差<br /> </td> 
   <td> DaysDiff(&lt;结束日期&gt;, &lt;开始日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> 返回日期的年龄（以天为单位）<br /> </td> 
   <td> DaysOld(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> 返回服务器的当前系统日期<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> 返回日期的小时数<br /> </td> 
   <td> Hour(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> 返回两个日期之间的小时数之差<br /> </td> 
   <td> HoursDiff(&lt;结束日期&gt;, &lt;开始日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> 返回日期的分钟数<br /> </td> 
   <td> Minute(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> 返回两个日期之间的分钟数之差<br /> </td> 
   <td> MinutesDiff(&lt;结束日期&gt;, &lt;开始日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> 返回表示日期月份的数字<br /> </td> 
   <td> Month(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> 返回对应于当前日期 n 个月的日期<br /> </td> 
   <td> MonthsAgo(&lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> 返回两个日期之间的月数之差<br /> </td> 
   <td> MonthsDiff(&lt;结束日期&gt;, &lt;开始日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> 返回日期的年龄（以月为单位）<br /> </td> 
   <td> MonthsOld(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> 返回日期的秒数<br /> </td> 
   <td> Second(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> 返回两个日期之间的秒数之差<br /> </td> 
   <td> SecondsDiff(&lt;结束日期&gt;, &lt;开始日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> 从日期减去天数<br /> </td> 
   <td> SubDays(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> 从日期减去小时数<br /> </td> 
   <td> SubHours(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> 从日期减去分钟数<br /> </td> 
   <td> SubMinutes(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> 从日期减去月数<br /> </td> 
   <td> SubMonths(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> 从日期减去秒数<br /> </td> 
   <td> SubSeconds(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> 从日期减去年数<br /> </td> 
   <td> SubYears(&lt;日期&gt;, &lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> 将日期+时间转换为日期<br /> </td> 
   <td> ToDate(&lt;日期 + 时间&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> 将字符串转换为日期+时间<br /> </td> 
   <td> ToDateTime(&lt;字符串&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> 将日期+时间舍入到最接近的秒数<br /> </td> 
   <td> TruncDate(@lastModified, &lt;秒数&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> 将日期+时间舍入为以秒表示的精度<br /> </td> 
   <td> TruncDateTZ(&lt;日期&gt;, &lt;秒数&gt;, &lt;时区&gt;&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> 将日期舍入到季度<br /> </td> 
   <td> TruncQuarter(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> 将时间部分舍入到最接近的秒<br /> </td> 
   <td> TruncTim(e)&lt;date&gt;， &lt;number of="" seconds=""&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> 将日期舍入到周<br /> </td> 
   <td> TruncWeek(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> 将日期+时间舍入到年度的 1 月 1 日<br /> </td> 
   <td> TruncYear(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> 返回表示日期一周中某天的日期数字<br /> </td> 
   <td> WeekDay(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Year</strong><br /> </td> 
   <td> 返回表示日期年份的数字<br /> </td> 
   <td> Year(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearAnd Month</strong><br /> </td> 
   <td> 返回表示日期的年份和月份的数字<br /> </td> 
   <td> YearAndMonth(&lt;日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> 返回两个日期之间的年数之差<br /> </td> 
   <td> YearsDiff(&lt;结束日期&gt;, &lt;开始日期&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> 返回日期的年龄（以年为单位）<br /> </td> 
   <td> YearsOld(&lt;日期&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>请注意 **Dateonly** 函数会考虑服务器的时区，而不是运算符的时区。

**数值**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>语法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> 返回数字的绝对值<br /> </td> 
   <td> Abs(&lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> 返回大于或等于某个数字的最小整数<br /> </td> 
   <td> Ceil(&lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> 返回大于或等于某个数字的最大整数<br /> </td> 
   <td> Floor(&lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> 返回两个数字中的较大者<br /> </td> 
   <td> Greatest(&lt;数字 1&gt;, &lt;数字 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> 返回两个数字中的较小者<br /> </td> 
   <td> Least(&lt;数字 1&gt;, &lt;数字 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> 返回n1除以n2的整数除余数<br /> </td> 
   <td> Mod(&lt;数字 1&gt;, &lt;数字 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Percent</strong><br /> </td> 
   <td> 返回两个数字的比值，以百分比表示<br /> </td> 
   <td> Percent(&lt;数字 1&gt;, &lt;数字 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Random</strong><br /> </td> 
   <td> 返回随机值<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> 将数字舍入为 n 位小数<br /> </td> 
   <td> Round(&lt;数字&gt;, &lt;小数&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> 返回数字的符号<br /> </td> 
   <td> Sign(&lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> 将整数转换为浮点<br /> </td> 
   <td> ToDouble(&lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> 将浮点转换为 64 位整数<br /> </td> 
   <td> ToInt64(&lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> 将浮点转换为整数<br /> </td> 
   <td> ToInteger(&lt;数字&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> 将 n1 取整到 n2 位小数<br /> </td> 
   <td> Trunc(&lt;n1&gt;, &lt;n2&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

1. 货币

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>语法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ConversionCurrency</strong><br /> </td> 
   <td> 将以源货币表示的金额转换为以目标货币表示的金额<br /> </td> 
   <td> ConvertCurrency(&lt;amount&gt;， &lt;source currency=""&gt;， &lt;target currency=""&gt;， &lt;conversion date=""&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>格式货币</strong><br /> </td> 
   <td> 根据所选货币设置设置显示的金额格式<br /> </td> 
   <td> FormatCurrency(&lt;amount&gt;， &lt;currency&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**地理营销**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>语法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Distance</strong><br /> </td> 
   <td> 返回由经度和纬度定义的两点之间的距离，以度表示。<br /> </td> 
   <td> Distance(&lt;经度 A&gt;, &lt;纬度 A&gt;, &lt;经度 B&gt;, &lt;纬度 B&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**其他**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>语法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> 如果条件为true，则返回值1。 如果不存在，则返回值2。<br /> </td> 
   <td> Case(When(&lt;条件&gt;, &lt;值 1&gt;), Else(&lt;值 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> 删除值中的标志<br /> </td> 
   <td> ClearBit(&lt;标识符&gt;, &lt;标识&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> 如果值 1 为 0 或 null，则返回值 2，否则返回值 1<br /> </td> 
   <td> Coalesce(&lt;值 1&gt;, &lt;值 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> 如果值1 =值2，则返回值3。 如果不返回，则返回值4。<br /> </td> 
   <td> Decode(&lt;值 1&gt;, &lt;值 2&gt;, &lt;值 3&gt;, &lt;值 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> 返回值 1（只能用作 case 函数的参数）<br /> </td> 
   <td> Else(&lt;value&gt;， &lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> 从电子邮件地址提取域名<br /> </td> 
   <td> GetEmailDomain(&lt;值&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> 检索镜像页面服务器的 URL<br /> </td> 
   <td> GetMirrorURL(&lt;值&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> 如果表达式为true，则返回值1。 如果不存在，则返回值2<br /> </td> 
   <td> Iif(&lt;条件&gt;, &lt;值 1&gt;, &lt;值 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> 指示标志是否在值中<br /> </td> 
   <td> IsBitSet(&lt;标识符&gt;, &lt;标识&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> 如果字符串1为空，则返回值2，否则返回值3<br /> </td> 
   <td> IsEmptyString(&lt;value&gt;， &lt;value&gt;， &lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> 如果参数为 NULL，则返回空字符串<br /> </td> 
   <td> NoNull(&lt;值&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> 返回行号<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> 强制将标志设在值中<br /> </td> 
   <td> SetBit(&lt;标识符&gt;, &lt;标识&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> 将数字转换为布尔值<br /> </td> 
   <td> ToBoolean(&lt;数字&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> 如果表达式为true，则返回值1。 如果不存在，则返回值2（只能用作case函数的参数）<br /> </td> 
   <td> When(&lt;条件&gt;, &lt;值 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**窗口化函数**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>语法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> 应用降序排序<br /> </td> 
   <td> Desc(&lt;值 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> 对分区中的结果进行排序<br /> </td> 
   <td> OrderBy(&lt;值 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> 对表格上的查询结果进行分区<br /> </td> 
   <td> PartitionBy(&lt;值 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> 根据表分区和排序顺序生成行号。<br /> </td> 
   <td> RowNum(PartitionBy(&lt;值 1&gt;), OrderBy(&lt;值 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>
