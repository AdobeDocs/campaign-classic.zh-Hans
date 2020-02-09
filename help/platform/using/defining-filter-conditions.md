---
title: 定义过滤条件
seo-title: 定义过滤条件
description: 定义过滤条件
seo-description: null
page-status-flag: never-activated
uuid: 2ed5d0bd-88fd-4eff-baf0-ed1b097269da
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: 8e575da0-c51a-4106-a826-3e1771e63649
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 定义过滤条件{#defining-filter-conditions}

## 选择运算符 {#choosing-the-operator}

在筛选条件中，您需要使用运算符将两个值链接在一起。

![](assets/query_editor_nveau_96.png)

以下是可用操作符列表：

<table> 
 <thead> 
  <tr> 
   <th> 运算符<br /> </th> 
   <th> 用途<br /> </th> 
   <th> Example<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">等于</span><br /> </td> 
   <td> 返回与在第二个“值”列中输入的数据相同的结果。<br /> </td> 
   <td> <strong>姓氏(@lastName)等于“Jones”</strong>，将仅返回姓为Jones的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">大于</span><br /> </td> 
   <td> 返回大于输入值的值。<br /> </td> 
   <td> <strong>年龄(@age)大于50</strong>，将返回所有大于“50”的值，即“51”、“52”等。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">小于</span><br /> </td> 
   <td> 返回小于输入值的值。<br /> </td> 
   <td> <strong>创建日期(@created)早于“DaysAgo(100)”</strong>，将返回所有在100天前创建的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">大于或等于</span><br /> </td> 
   <td> 返回等于或大于输入值的所有值。<br /> </td> 
   <td> <strong>年龄(@age)大于或等于“30”</strong>，将返回所有年龄在30岁或以上的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">小于或等于</span><br /> </td> 
   <td> 返回等于或低于输入值的所有值。<br /> </td> 
   <td> <strong>年龄(@age)小于或等于“60”</strong>，将返回所有年龄在60岁或以下的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不等于</span><br /> </td> 
   <td> 返回与输入的值不相同的所有值。<br /> </td> 
   <td> <strong>语言(@language)等于“英语”</strong>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">开始于</span><br /> </td> 
   <td> 返回以输入的值开始的结果。<br /> </td> 
   <td> <strong>帐户#(@account)以'32010'开头。</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不从开始</span><br /> </td> 
   <td> 返回不以输入值开头的结果<br /> </td> 
   <td> <strong>帐户#(@account)不以'20'开头</strong>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">包含</span><br /> </td> 
   <td> 返回至少包含输入值的结果。<br /> </td> 
   <td> <strong>电子邮件域(@domain)包含“mail”</strong>，将返回所有包含“mail”的域名。 因此，“gmail.com”域也将被返回。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不包含</span><br /> </td> 
   <td> 返回不包含输入值的结果。<br /> </td> 
   <td> <strong>电子邮件域(@domain)不包含“vo”</strong>。 在这种情况下，将不返回包含“vo”的域名。 结果中不显示“voila.fr”域名。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">喜欢</span><br /> </td> 
   <td> <span class="uicontrol">Like</span> 与Contains运算符非 <span class="uicontrol">常相似</span> 。 它允许您在值中 <span class="uicontrol">插入%</span> 通配符。<br /> </td> 
   <td> <strong>姓氏(@lastName)，如“Jon%s”</strong>。 在此，如果操作员忘记了“n”和“s”之间缺少的字母，则通配符将用作“小丑”来查找“Jones”的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不喜欢</span><br /> </td> 
   <td> 与“赞”类 <span class="uicontrol">似</span> 。 不允许您恢复输入的值。 在此，输入的值也必须包含 <span class="uicontrol">%</span> 通配符。<br /> </td> 
   <td> <strong>姓氏(@lastName)与'Smi%h'不同</strong>。 此处，将不返回姓为“Smi%h”的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">为空</span><br /> </td> 
   <td> 在这种情况下，我们要查找的结果与第二个“值”列中的空值匹配。<br /> </td> 
   <td> <strong>移动(@mobilePhone)为空</strong> ，将返回所有没有移动号码的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不为空</span><br /> </td> 
   <td> 与“为空”运算符 <span class="uicontrol">相反</span> 。 无需在第二个值列中输入数据。<br /> </td> 
   <td> <strong>电子邮件(@email)不为空</strong>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">包含在</span><br /> </td> 
   <td> 返回包含在所指示值中的结果。 这些值必须用逗号分隔。<br /> </td> 
   <td> <strong>出生日期(@birthDate)包含在1979/12/10/1984'中</strong>，将返回在这些日期之间出生的收件人。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不包含在</span><br /> </td> 
   <td> 类似“包含在 <span class="uicontrol">操作符中</span> ”的作品。 在此，我们要根据输入的值排除收件人。<br /> </td> 
   <td> <strong>出生日期(@birthDate)不包括在1984年12月10日1979年12月12日</strong>。 与上一个示例不同，在这些日期内出生的收件人将不会返回。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 使用和，或，除 {#using-and--or--except}

对于使用多个筛选条件的查询，您需要定义这些条件之间的链接。 有三个可能的链接：

* **[!UICONTROL And]** 让您结合两个过滤条件，
* **[!UICONTROL Or]** 让你提供另一种选择，
* **[!UICONTROL Except]** 允许您定义例外。

单 **[!UICONTROL And]** 击（默认提供）并从下拉列表中选择。

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**:添加一个条件并启用过滤。
* **[!UICONTROL Or]**:添加一个条件并启用过滤。

   以下示例允许您查找电子邮件域包含“orange.co.uk”或其帖子代码以“NW”开头的收件人。

   ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**:如果您有两个过滤器，而第一个过滤器不返回值，则此类型的链接会创建异常。

   在以下示例中，我们希望返回其电子邮件域包含“orange.co.uk”的收件人，但收件人的姓是“Smith”的除外。

   ![](assets/query_condition_modif_03.png)

此示例显示了一个可显示的过滤器：说西班牙语的收件人或者是带有手机号码的女士，或者是没有帐号且公司名称以字母“N”开头的收件人。

![](assets/query_editor_nveau_31.png)

## 确定条件优先级 {#prioritizing-conditions}

此部分介绍如何利用工具栏中的蓝色箭头对条件进行排序。

* 通过指向右侧的箭头，可向滤镜添加一级括号。
* 指向左侧的箭头允许您从筛选器中删除选定的括号级别。

   ![](assets/query_condition_modif_04.png)

* 垂直箭头允许您移动条件，从而更改其执行顺序。

此示例说明如何使用箭头删除括号级别。 从以下筛选条件开始： **[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**.

将光标放在筛选条 **[!UICONTROL Gender (@gender) equal to Male]** 件上，然后单击箭 **[!UICONTROL Remove a parenthesis level]** 头。

![](assets/query_editor_nveau_32.png)

该条 **[!UICONTROL Gender (@gender) equal to Male]** 件已超出其括号。 它已升至与“伦敦城市相当”的水平。 这些条件是链接在一起的(**[!UICONTROL And]**)。

## 选择要提取的数据 {#selecting-data-to-extract}

可用字段因表而异。 所有字段都存储在称为的主节点中 **[!UICONTROL Main element]**。 在以下示例中，可用字段位于收件人表中。 字段始终按字母顺序显示。

选定字段的详细信息显示在窗口底部。 例如，字段 **[!UICONTROL Email domain]** 为a, **[!UICONTROL Calculated SQL field]** 其扩展名为 **[!UICONTROL (@domain)]**。

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>使用该 **[!UICONTROL Search]** 工具查找可用字段。

双击可用字段，将其添加到输出列。 在查询的结尾处，每个选定的字段在窗口中创建一 **[!UICONTROL Data preview]** 列。

![](assets/query_editor_nveau_01.png)

默认情况下，高级字段不显示。 单 **[!UICONTROL Display advanced fields]** 击可用字段右下角的以显示所有内容。 再次单击可返回到前一个视图。

例如，在收件人表中，高级字段为 **Boolean 1****[!UICONTROL Boolean 2]**、 **[!UICONTROL Boolean 3]**、 **[!UICONTROL Foreign key of "Folder" link]**&#x200B;等。

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
   <td> 电子邮件、性别等<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> 主键。 此SQL字段是标识表中记录的一种方法。<br /> </td> 
   <td> 标识符接收者是主键，标识符根据定义是唯一的。<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> 外键。 用作指向另一个表的链接。<br /> </td> 
   <td> 接收方外键、服务外键等<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> 计算字段。 此类型的字段是使用数据库中的值在请求时计算的。<br /> </td> 
   <td> 年龄、电子邮件域等<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> 包含长文本的字段。<br /> </td> 
   <td> 评论、完整地址等。<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> 索引SQL字段。 <br /> </td> 
   <td> 全名、ISO代码等 <br /> </td> 
  </tr> 
 </tbody> 
</table>

链接到表和集合元素：

<table> 
 <thead> 
  <tr> 
   <th> 图标<br /> </th> 
   <th> 说明<br /> </th> 
   <th> Example<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> 尤其是指向表的链接。 这些关联与1-1类型关联一致。 源表的出现只能与目标表的一个出现一致。 例如，只能将一个收件人链接到一个国家／地区。<br /> </td> 
   <td> 文件夹、状态、国家／地区等 <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> 特定表上的集合元素。 这些关联与1-N类型关联一致。 一个源表实例可以与目标表的几个实例一致，但目标表的一个实例可以与源表的一个实例一致。 例如，一个收件人可以订阅“n”订阅字母。<br /> </td> 
   <td> 订阅、列表、排除日志等。<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* 使用 **[!UICONTROL Add]** 按钮（侧图标栏上方）可添加要在其中编辑表达式的输出列。 有关编辑表达式的详细信息，请参阅构建 [表达式](#building-expressions)。
>* 通过单击红色的“x”（删除）删除输&#x200B;**出列**。
>* 使用箭头更改输出列的顺序。
>* 该 **[!UICONTROL Distribution of values]** 功能用于查看所选字段值的分布情况（例如，链接到收件人城镇的分布情况、收件人语言等）。


## 创建计算字段 {#creating-calculated-fields}

如有必要，请在数据格式化过程中添加一列。 计算字段会向数据预览部分添加一列。 单击 **[!UICONTROL Add a calculated field]**.

![](assets/query_editor_nveau_43.png)

有四种类型的计算字段：

* **[!UICONTROL Fixed string]**:允许您添加字符串。

   ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**:计算字段的值组合了一串字符和JavaScript指令。

   ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**:计算字段的值是JavaScript函数评估的结果。 可以键入返回的值（数字、日期等）。

   ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**:此类型的字段允许您使用／修改新列中某个输出列的内容。

   可以使用列的源值，并为其指定目标值。 此目标值将显示在新输出列中。

   有一个添加计算字段类 **[!UICONTROL Enumerations]** 型的示例，请参阅 [此部分](../../workflow/using/adding-enumeration-type-calculated-field.md)。

   ![](assets/query_editor_nveau_63.png)

   类型 **[!UICONTROL Enumerations]** 计算字段可以包括4个条件：

   * **[!UICONTROL Keep the source value]** 将源值恢复到目标，而不更改它。
   * **[!UICONTROL Use the following value]** 允许您为未定义的源值输入默认目标值。
   * **[!UICONTROL Generate a warning and continue]** 警告用户源值无法更改。
   * **[!UICONTROL Generate an error and reject the line]** 阻止计算和导入行。

单击该 **[!UICONTROL Detail of calculated field]** 按钮可查看插入字段的详细信息。

要删除此计算的字段，请单击 **[!UICONTROL Remove the calculated field]** 叉号。

![](assets/query_editor_nveau_58.png)

## 构建表达式 {#building-expressions}

表达式编辑工具允许您使用表达式计算聚合、生成函数或编辑公式。

以下示例显示如何运行对主键的计数。

应用以下步骤：

1. 在窗 **[!UICONTROL Add]** 口中单 **[!UICONTROL Data to extract]** 击。 在窗口 **[!UICONTROL Formula type]** 中，选择要输入表达式的公式类型。

   可用的公式有几种类型： **[!UICONTROL Field only]**, **[!UICONTROL Aggregate]**, **[!UICONTROL Expression]**。

   选 **[!UICONTROL Process on an aggregate function]**&#x200B;择和 **[!UICONTROL Count]**。 单击 **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_54.png)

1. 将计算主键。

   ![](assets/query_editor_nveau_88.png)

以下是窗口中可用选项的详细视 **[!UICONTROL Formula types]** 图：

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** 允许您返回窗 **[!UICONTROL Field to select]** 口。
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**. 以下是聚合使用的一些示例：

   * **[!UICONTROL Count]** 允许您运行主键计数。
   * **[!UICONTROL Sum]** 允许您将客户在一年以上进行的所有购买相加。
   * **[!UICONTROL Maximum value]** 允许您查找已购买最多“n”产品的客户。
   * **[!UICONTROL Minimum value]** 允许您对客户进行排序，并查找最近订阅了优惠的客户。
   * **[!UICONTROL Average]**. 此函数允许您计算收件人的平均年龄。

      通过 **[!UICONTROL Distinct]** 该框可恢复列的唯一值和非零值。 例如，您可以恢复收件人的所有跟踪日志，这些跟踪日志将更改为值1，因为它们都与同一收件人相关。

1. **[!UICONTROL Expression]** 打开窗 **[!UICONTROL Edit the expression]** 口。 这样，您就可以检测数字过多的电话号码，这可能是输入错误。

   ![](assets/query_editor_nveau_71.png)

   有关所有可用函数的列表，请参阅 [函数列表](#list-of-functions)。

## 功能列表 {#list-of-functions}

如果选 **[!UICONTROL Expression]** 择了类型公式，您将进入“编辑表达式”窗口。 各种类别的函数可以关联到可用字段： **[!UICONTROL Aggregates]**, **[!UICONTROL String]**, **[!UICONTROL Date]**, **[!UICONTROL Numerical]**, **[!UICONTROL Currency]**&#x200B;和 **[!UICONTROL Geomarketing]****[!UICONTROL Windowing function]****[!UICONTROL Others]**。

表达式编辑器如下所示：

![](assets/s_ncs_user_filter_define_expression.png)

它允许您选择数据库表中的字段，并向它们添加高级函数。 有以下功能可用：

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
   <td> Avg(&lt;value&gt;)<br /></td> 
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
   <td> <strong>最小</strong><br /> </td> 
   <td> 返回数字、字符串或日期类型列的最小值<br /> </td> 
   <td> Min(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> 返回数字、字符串或日期列的标准偏差<br /> </td> 
   <td> StdDev(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>总和</strong><br /> </td> 
   <td> 返回数字、字符串或日期类型列的值之和<br /> </td> 
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
   <td> 指示所有参数是否为非null且不为空<br /> </td> 
   <td> AllNonNull2(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> 指示所有参数是否为非null且不为空<br /> </td> 
   <td> AllNonNull3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> 返回字符串中第一个字符的ASCII值。<br /> </td> 
   <td> Ascii(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> 返回与“n”ASCII代码对应的字符<br /> </td> 
   <td> Char(&lt;number&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> 返回字符串1中字符串2的位置。<br /> </td> 
   <td> Charindex(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> 返回字符串的n（从1到n）行<br /> </td> 
   <td> GetLine(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> 如果前两个参数相等，则返回第三个参数。 如果不是，则返回最后一个参数<br /> </td> 
   <td> IfEquals(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> 指示作为参数传递的备忘录是否为null<br /> </td> 
   <td> IsMemoNull(&lt;memo&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> 连接作为参数传递的字符串。 如果需要，在字符串之间添加空格。<br /> </td> 
   <td> JuxtWords(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> 连接作为参数传递的字符串。 如果需要，在字符串之间添加空格<br /> </td> 
   <td> JuxtWords3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> 返回左边已完成的字符串<br /> </td> 
   <td> LPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>左侧</strong><br /> </td> 
   <td> 返回字符串的前n个字符<br /> </td> 
   <td> Left(&lt;string&gt;, &lt;number&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>长度</strong><br /> </td> 
   <td> 返回字符串的长度<br /> </td> 
   <td> Length(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>低</strong><br /> </td> 
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
   <td> 返回字符串MD5键的十六进制表示形式<br /> </td> 
   <td> Md5Digest(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>备忘录包含</strong><br /> </td> 
   <td> 指定备忘录是否包含作为参数传递的字符串<br /> </td> 
   <td> MemoContains(&lt;memo&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> 返回右侧的已完成字符串<br /> </td> 
   <td> RPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>右</strong><br /> </td> 
   <td> 返回字符串的最后n个字符<br /> </td> 
   <td> Right(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> 删除字符串右侧的空格<br /> </td> 
   <td> Rtrim(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>智能</strong><br /> </td> 
   <td> 返回带每个单词的第一个字母大写的字符串<br /> </td> 
   <td> Smart(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>子字符串</strong><br /> </td> 
   <td> 从字符串的字符n1和长度n2开始提取子字符串<br /> </td> 
   <td> 子字符串(&lt;string&gt;, &lt;offset&gt;, &lt;length&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> 将数字转换为字符串<br /> </td> 
   <td> ToString(&lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>上</strong><br /> </td> 
   <td> 返回大写字符串<br /> </td> 
   <td> Upper(&lt;string&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> 如果其他两个参数相等，则返回作为参数传递的链接的外键<br /> </td> 
   <td> VirtualLink(&lt;number&gt;, &lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> 如果其他两个参数相等，则返回作为参数传递的链接的外键（文本）<br /> </td> 
   <td> VirtualLinkStr(&lt;string&gt;, &lt;number&gt;, &lt;number&gt;)<br /> </td>  
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
   <td> AddDays(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> 向日期添加小时数<br /> </td> 
   <td> AddHours(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> 向日期添加分钟数<br /> </td> 
   <td> AddMinutes(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> 将月数添加到日期<br /> </td> 
   <td> AddMonths(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> 向日期添加秒数<br /> </td> 
   <td> AddSeconds(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> 在日期中添加年数<br /> </td> 
   <td> AddYears(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>仅日期</strong><br /> </td> 
   <td> 仅返回日期（时间为00:00）*<br /> </td> 
   <td> DateOnly(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>日</strong><br /> </td> 
   <td> 返回表示日期的数字<br /> </td> 
   <td> Day(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>年度日</strong><br /> </td> 
   <td> 返回日期年中的日数<br /> </td> 
   <td> DayOfYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> 返回与当前日期相应的日期减去n天<br /> </td> 
   <td> DaysAgo(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> 返回与当前日期减n天对应的日期（整数yyyymmdd）<br /> </td> 
   <td> DaysAgoInt(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> 两个日期之间的天数<br /> </td> 
   <td> DaysDiff（&lt;结束日期&gt;, &lt;开始日期&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> 返回日期的年龄（以天为单位）<br /> </td> 
   <td> DaysOld(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> 返回服务器的当前系统日期<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>小时</strong><br /> </td> 
   <td> 返回日期的小时<br /> </td> 
   <td> Hour(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>小时差异</strong><br /> </td> 
   <td> 返回两个日期之间的小时数<br /> </td> 
   <td> HoursDiff（&lt;结束日期&gt;, &lt;开始日期&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>分钟</strong><br /> </td> 
   <td> 返回日期的分钟数<br /> </td> 
   <td> Minute(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> 返回两个日期之间的分钟数<br /> </td> 
   <td> MinutesDiff（&lt;结束日期&gt;, &lt;开始日期&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>月</strong><br /> </td> 
   <td> 返回表示日期月份的数字<br /> </td> 
   <td> Month(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>数月前</strong><br /> </td> 
   <td> 返回与当前日期相应的日期减去n个月<br /> </td> 
   <td> MonthsAgo(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> 返回两个日期之间的月份数<br /> </td> 
   <td> MonthsDiff（&lt;结束日期&gt;, &lt;开始日期&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> 返回日期的月份数<br /> </td> 
   <td> MonthsOld(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>第二</strong><br /> </td> 
   <td> 返回日期的秒数<br /> </td> 
   <td> Second(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> 返回两个日期之间的秒数<br /> </td> 
   <td> SecondsDiff（&lt;结束日期&gt;, &lt;开始日期&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> 从日期减去天数<br /> </td> 
   <td> SubDays(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>小时数</strong><br /> </td> 
   <td> 从日期减去小时数<br /> </td> 
   <td> SubHours(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>子分钟</strong><br /> </td> 
   <td> 从日期减去分钟数<br /> </td> 
   <td> SubMinutes(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>子月份</strong><br /> </td> 
   <td> 从日期减去月数<br /> </td> 
   <td> SubMonths(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>子秒</strong><br /> </td> 
   <td> 从日期减去秒数<br /> </td> 
   <td> SubSeconds(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>子年</strong><br /> </td> 
   <td> 从日期减去数年<br /> </td> 
   <td> SubYears(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> 将日期+时间转换为日期<br /> </td> 
   <td> ToDate(&lt;date + time&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> 将字符串转换为日期+时间<br /> </td> 
   <td> ToDateTime(&lt;string&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> 将日期+时间舍入到最近的第二个<br /> </td> 
   <td> TruncDate（@lastModified, &lt;秒数&gt;）<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> 将日期+时间舍入为以秒为单位的给定精度<br /> </td> 
   <td> TruncDateTZ（&lt;date&gt;, &lt;秒数&gt;, &lt;时区&gt;）<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> 将日期舍入到季度<br /> </td> 
   <td> TruncQuarter(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> 将时间部分舍入到最近的第二个<br /> </td> 
   <td> TruncTim（e&lt;date&gt;, &lt;秒数&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> 将日期舍入到周<br /> </td> 
   <td> TruncWeek(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> 将日期+时间舍入到年度的1月1日<br /> </td> 
   <td> TruncYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> 返回表示日期周中某天的数字<br /> </td> 
   <td> WeekDay(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>年</strong><br /> </td> 
   <td> 返回表示日期年份的数字<br /> </td> 
   <td> Year(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>年和月</strong><br /> </td> 
   <td> 返回表示日期的年份和月份的数字<br /> </td> 
   <td> YearAndMonth(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> 返回两个日期之间的年数<br /> </td> 
   <td> YearsDiff（&lt;结束日期&gt;, &lt;开始日期&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> 返回日期的年龄<br /> </td> 
   <td> YearsOld(&lt;date&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>请注意， **Dateonly** 函数会考虑服务器的时区，而不是运算符的时区。

**数字**

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
   <td> Abs(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> 返回大于或等于数字的最低整数<br /> </td> 
   <td> Ceil(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> 返回大于或等于一个数字的最大整数<br /> </td> 
   <td> Floor(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>最伟大</strong><br /> </td> 
   <td> 返回两个数字中的较大者<br /> </td> 
   <td> 最大（&lt;数字1&gt;, &lt;数字2&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>最少</strong><br /> </td> 
   <td> 返回两个数字中的较小者<br /> </td> 
   <td> 最少（&lt;数字1&gt;, &lt;数字2&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> 返回n1除以n2的整数除的余数<br /> </td> 
   <td> Mod(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>百分比</strong><br /> </td> 
   <td> 返回以百分比表示的两个数字的比率<br /> </td> 
   <td> Percent(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>随机</strong><br /> </td> 
   <td> 返回随机值<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>圆形</strong><br /> </td> 
   <td> 将数字舍入为n小数<br /> </td> 
   <td> Round（&lt;number&gt;, &lt;小数&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>签名</strong><br /> </td> 
   <td> 返回数字的符号<br /> </td> 
   <td> Sign(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> 将整数转换为浮点<br /> </td> 
   <td> ToDouble(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> 将浮点数转换为64位整数<br /> </td> 
   <td> ToInt64(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> 将浮点转换为整数<br /> </td> 
   <td> ToInteger(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> 截断n1到n2小数<br /> </td> 
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
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> 将来源货币中的金额转换为目标货币中的金额<br /> </td> 
   <td> ConvertCurrency(&lt;amount&gt;, &lt;source currency&gt;, &lt;target currency&gt;, &lt;conversion date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>格式货币</strong><br /> </td> 
   <td> 设置根据所选货币设置显示金额的格式<br /> </td> 
   <td> FormatCurrency(&lt;amount&gt;, &lt;currency&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Geomarketing**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>语法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>距离</strong><br /> </td> 
   <td> 返回两个点之间的距离（以度表示），这两个点由其经度和纬度定义。<br /> </td> 
   <td> 距离（&lt;经度A&gt;、&lt;经度A&gt;、&lt;经度B&gt;、&lt;经度B&gt;）<br /> </td>  
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
   <td> <strong>案例</strong><br /> </td> 
   <td> 如果条件为true，则返回值1。 否则，返回值2。<br /> </td> 
   <td> Case(When(&lt;condition&gt;, &lt;value 1&gt;), Else(&lt;value 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> 删除值中的标记<br /> </td> 
   <td> ClearBit(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> 如果值1为零或null，则返回值2，否则返回值1<br /> </td> 
   <td> Coalesce(&lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>解码</strong><br /> </td> 
   <td> 如果值1 =值2，则返回值3。 如果不返回值4。<br /> </td> 
   <td> Decode(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;, &lt;value 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> 返回值1（只能用作case函数的参数）<br /> </td> 
   <td> Else(&lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> 从电子邮件地址提取域<br /> </td> 
   <td> GetEmailDomain(&lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> 检索镜像页面服务器的URL<br /> </td> 
   <td> GetMirrorURL(&lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>If</strong><br /> </td> 
   <td> 如果表达式为true，则返回值1。 否则，返回值2<br /> </td> 
   <td> Iif(&lt;condition&gt;, &lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> 指示标记是否在值中<br /> </td> 
   <td> IsBitSet(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> 如果字符串1为空，则返回值2，否则返回值3<br /> </td> 
   <td> IsEmptyString(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> 如果参数为NULL，则返回空字符串<br /> </td> 
   <td> NoNull(&lt;value&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> 返回行号<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> 强制值中的标记<br /> </td> 
   <td> SetBit(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> 将数字转换为布尔值<br /> </td> 
   <td> ToBoolean(&lt;number&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>何时</strong><br /> </td> 
   <td> 如果表达式为true，则返回值1。 否则，它返回值2（只能用作case函数的参数）<br /> </td> 
   <td> When(&lt;condition&gt;, &lt;value 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**窗口功能**

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
   <td> Desc(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> 对分区内的结果进行排序<br /> </td> 
   <td> OrderBy(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>分区依据</strong><br /> </td> 
   <td> 将查询结果分区到表<br /> </td> 
   <td> PartitionBy(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> 基于表分区和排序序列生成行号。<br /> </td> 
   <td> RowNum(PartitionBy(&lt;value 1&gt;), OrderBy(&lt;value 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>