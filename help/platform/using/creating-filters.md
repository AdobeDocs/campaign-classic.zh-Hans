---
product: campaign
title: 创建过滤器
description: 创建过滤器
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 58e54f67-dc87-42f1-8426-6f801e8e4fb6
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '1963'
ht-degree: 1%

---

# 创建过滤器{#creating-filters}

![](../../assets/common.svg)

在Adobe Campaign树中导航时(从 **[!UICONTROL Explorer]** 菜单)，则数据库中包含的数据将显示在列表中。 这些列表可配置为仅显示操作员所需的数据。 然后，可以对过滤的数据启动操作。 过滤器配置允许您从列表中选择数据 **[!UICONTROL dynamically]**. 如果数据被修改，则会更新过滤的数据。

>[!NOTE]
>
>用户界面配置设置在设备级别本地定义。 有时可能需要清理此数据，尤其是在刷新数据时出现问题时。 为此，请使用 **[!UICONTROL File > Clear the local cache]** 菜单。

## 可用过滤器的分类 {#typology-of-available-filters}

Adobe Campaign允许您将过滤器应用到数据列表。

这些过滤器可以使用一次，也可以保存以备将来使用。 您可以同时应用多个过滤器。

Adobe Campaign中提供了以下过滤器类型：

* **默认过滤器**

   的 **默认过滤器** 可通过列表上方的字段访问。 它允许您过滤预定义的字段（对于收件人用户档案，默认为名称和电子邮件地址）。 您可以使用这些字段输入字符以进行筛选，或从下拉列表中选择筛选条件。

   ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an email address in the domain "yahoo.com".
-->
您可以更改列表的默认过滤器。 有关更多信息，请参阅 [更改默认过滤器](#altering-the-default-filter).

* **简单过滤器**

   **简单过滤器** 是列上的一次性过滤器。 可使用一个或多个简单搜索条件在显示的列中定义搜索条件。

   您可以在同一数据列表上组合多个简单过滤器以优化搜索。 筛选器字段显示在另一个字段的下方。 它们可以相互独立地删除。

   ![](assets/filters_recipient_simple_filter.png)

   有关简单过滤器的详情，请参阅 [创建简单过滤器](#creating-a-simple-filter).

* **高级过滤器**

   **高级过滤器** 使用查询或数据查询组合创建。

   有关创建高级过滤器的更多信息，请参阅 [创建高级过滤器](#creating-an-advanced-filter).

   您可以使用函数定义过滤器的内容。 有关更多信息，请参阅 [创建包含函数的高级过滤器](#creating-an-advanced-filter-with-functions).

   >[!NOTE]
   >
   >有关在Adobe Campaign中构建查询的更多信息，请参阅 [此部分](../../platform/using/about-queries-in-campaign.md).

* **用户过滤器**

   安 **应用程序筛选器** 是已保存的高级过滤器，用于使用其配置并与其他运算符共享。

   的 **[!UICONTROL Filters]** 列表上方的按钮提供了一组应用程序过滤器，这些过滤器可以组合在一起来优化过滤。 创建这些过滤器的方法，请参见 [保存过滤器](#saving-a-filter).

## 更改默认过滤器 {#altering-the-default-filter}

要更改收件人列表的默认过滤器，请单击 **[!UICONTROL Profiles and Targets > Pre-defined filters]** 树的节点。

对于所有其他类型的数据，请通过 **[!UICONTROL Administration > Configuration > Predefined filters]** 节点。

应用以下步骤：

1. 选择您要默认使用的过滤器。
1. 单击 **[!UICONTROL Parameters]** 选项卡，选择 **[!UICONTROL Default filter for the associated document type]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >如果已将默认过滤器应用于列表，则需要先禁用该过滤器，然后再应用新过滤器。 为此，请单击筛选字段右侧的红十字。

1. 单击 **[!UICONTROL Save]** 以应用过滤器。

   >[!NOTE]
   >
   >过滤器定义窗口详见 [创建高级过滤器](#creating-an-advanced-filter) 和 [保存过滤器](#saving-a-filter).

## 创建简单过滤器 {#creating-a-simple-filter}

创建 **简单过滤器**，请应用以下步骤：

1. 右键单击要筛选的字段并选择 **[!UICONTROL Filter on this field]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   默认过滤器字段显示在列表上方。

1. 从下拉列表中选择筛选器选项，或输入要应用的筛选条件(选择或输入标准的方法取决于字段类型：文本、枚举等)。

   ![](assets/s_ncs_user_sort_fields.png)

1. 要激活过滤器，请按键盘上的Enter键，或单击过滤器字段右侧的绿色箭头。

如果要筛选数据的字段未以用户档案的形式显示，则可以将其添加到显示的列中，然后对该列进行筛选。 为此，

1. 单击 **[!UICONTROL Configure the list]** 图标。

   ![](assets/s_ncs_user_configure_list.png)

1. 选择要显示的列，例如收件人的年龄。

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. 右键单击 **年龄** 列，然后选择 **[!UICONTROL Filter on this column]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   然后，您可以选择年龄筛选选项。

   ![](assets/s_ncs_user_delete_filter.png)

## 创建高级过滤器 {#creating-an-advanced-filter}

创建 **高级过滤器**，请应用以下步骤：

1. 单击 **[!UICONTROL Filters]** 按钮，选择 **[!UICONTROL Advanced filter...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   您还可以右键单击要过滤和选择的数据列表 **[!UICONTROL Advanced filter...]**.

   将显示筛选条件定义窗口。

1. 单击 **[!UICONTROL Expression]** 列来定义输入值。
1. 单击 **[!UICONTROL Edit expression]** ，以选择要应用过滤器的字段。

   ![](assets/s_user_filter_choose_field.png)

1. 从列表中选择要过滤数据的字段。 单击 **[!UICONTROL Finish]** 确认。
1. 单击 **[!UICONTROL Operator]** 列，然后从下拉列表中选择要应用的运算符。
1. 从 **[!UICONTROL Value]** 列。 您可以组合多个过滤器来优化查询。 要添加过滤条件，请单击 **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. 您可以为表达式分配层级，或使用工具栏箭头更改查询表达式的顺序。
1. 表达式之间的默认运算符是 **和**，但您可以通过单击字段来更改此设置。 您可以选择 **或** 运算符。

   ![](assets/s_ncs_user_filter_operator.png)

1. 单击 **[!UICONTROL OK]** 确认创建过滤器，并将其应用到列表。

应用的过滤器显示在列表上方。

![](assets/s_ncs_user_filter_adv_edit.png)

要编辑或修改此过滤器，请单击其标签。

要取消此过滤器，请单击 **[!UICONTROL Remove this filter]** 图标。

![](assets/s_ncs_user_filter_adv_remove.png)

您可以保存高级过滤器，以备将来使用。 有关此类型过滤器的更多信息，请参阅 [保存过滤器](#saving-a-filter).

### 创建包含函数的高级过滤器 {#creating-an-advanced-filter-with-functions}

高级过滤器可以使用函数； **函数筛选器** 是通过表达式编辑器创建的，表达式编辑器允许您使用数据库数据和高级函数创建公式。 要创建具有函数的过滤器，请重复高级过滤器创建步骤1、2和3，然后按照以下步骤继续操作：

1. 在字段选择窗口中，单击 **[!UICONTROL Advanced selection]**.
1. 选择要使用的公式类型：聚合、现有用户筛选器或表达式。

   ![](assets/s_ncs_user_filter_formula_select.png)

   可以使用以下选项：

   * **[!UICONTROL Field only]** ，以选择字段。 这是默认模式。
   * **[!UICONTROL Aggregate]** 选择要使用的聚合公式（计数、总和、平均值、最大值、最小值）。
   * **[!UICONTROL User filter]** 来选择现有用户过滤器之一。 有关用户过滤器的详情，请参阅 [保存过滤器](#saving-a-filter).
   * **[!UICONTROL Expression]** 以访问表达式编辑器。

      利用表达式编辑器，可定义高级过滤器。 它看起来如下所示：

      ![](assets/s_ncs_user_create_exp_exple01.png)

      它允许您选择数据库表中的字段，并将高级函数附加到这些字段：选择要在 **[!UICONTROL List of functions]**. 有关可用功能的详情，请参阅 [函数列表](../../platform/using/defining-filter-conditions.md#list-of-functions). 接下来，选择函数所涉及的字段并单击 **[!UICONTROL OK]** 以批准表达式。

      >[!NOTE]
      >
      >有关基于表达式创建过滤器的示例，请参阅 [此部分](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is).

## 保存过滤器 {#saving-a-filter}

过滤器特定于每个运算符，并在每次运算符清除其客户端控制台的缓存时重新初始化。

您可以创建 **应用程序筛选器** 通过保存高级过滤器：可通过右键单击任意列表或通过 **[!UICONTROL Filters]** 按钮。

这些过滤器也可以直接通过投放向导在目标选择阶段访问(请参阅 [此部分](../../delivery/using/creating-an-email-delivery.md) ，以了解有关创建投放的更多信息)。 要创建应用程序过滤器，您可以：

* 将高级过滤器转换为应用程序过滤器。 为此，请单击 **[!UICONTROL Save]** 在关闭高级过滤器编辑器之前。

   ![](assets/s_ncs_user_filter_save.png)

* 通过 **[!UICONTROL Administration > Configuration > Predefined filters]** (或 **[!UICONTROL Profiles and targets > Predefined filters]** （对于收件人）节点。 为此，请右键单击过滤器列表，然后选择 **[!UICONTROL New...]**. 创建高级过滤器的过程与相同。

   的 **[!UICONTROL Label]** 字段中，您可以命名此过滤器。 此名称将显示在 **[!UICONTROL Filters...]** 按钮。

   ![](assets/user_filter_apply.png)

您可以通过右键单击并选择 **[!UICONTROL No filter]** 或通过 **[!UICONTROL Filters]** 图标。

您可以通过单击 **[!UICONTROL Filters]** 按钮和使用 **[!UICONTROL And...]** 菜单。

![](assets/s_ncs_user_filter_combination.png)

## 筛选收件人 {#filtering-recipients}

预定义过滤器(请参阅 [保存过滤器](#saving-a-filter))，用于筛选数据库中包含的收件人的用户档案。 您可以在 **[!UICONTROL Profiles and Targets > Predefined filters]** 树的节点。 过滤器通过 **[!UICONTROL Filters]** 按钮。

选择过滤器以显示其定义并访问过滤数据的预览。

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>有关创建预定义过滤器的详细示例，请参阅 [用例](../../platform/using/use-case.md).

预定义过滤器包括：

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>查询</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 已打开<br /> </td> 
   <td> 选择已打开投放的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已打开但未单击<br /> </td> 
   <td> 选择已打开投放但未单击链接的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不活动的收件人<br /> </td> 
   <td> 选择X个月内未打开投放的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 上次按设备类型划分的活动<br /> </td> 
   <td> 选择在最近Z天内使用设备X单击或打开投放Y的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按设备类型划分的上次活动（跟踪）<br /> </td> 
   <td> 选择在最近Z天内使用设备X单击或打开投放Y的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定向的收件人<br /> </td> 
   <td> 选择在X个月内从未通过渠道Y定向的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 非常活跃的收件人<br /> </td> 
   <td> 选择在过去Y个月内点击投放至少X次的收件人。<br /> </td> 
  </tr> 
  <tr> 
 <td> 列入阻止列表电子邮件地址<br /> </td> 
    <td> 选择电子邮件地址在上的收阻止列表件人。<br/> </td>
  </tr> 
  <tr> 
   <td> 隔离的电子邮件地址<br /> </td> 
   <td> 选择其电子邮件地址被隔离的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 文件夹中的电子邮件地址重复<br /> </td> 
   <td> 选择文件夹中电子邮件地址重复的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未打开或单击<br /> </td> 
   <td> 选择未打开投放或已单击投放的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 新收件人（天）<br /> </td> 
   <td> 选择在最近X天内创建的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 新收件人（分钟）<br /> </td> 
   <td> 选择在最近X分钟内创建的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 新收件人（月）<br /> </td> 
   <td> 选择过去X个月中创建的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 通过订阅<br /> </td> 
   <td> 按订阅选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 通过单击特定链接<br /> </td> 
   <td> 选择单击投放中特定URL的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按帖子投放行为<br /> </td> 
   <td> 在收到投放后，根据收件人的行为选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按创建日期<br /> </td> 
   <td> 按创建日期，在从X个月（当前日期减n个月）到Y个月（当前日期减n个月）的期间内选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按列表<br /> </td> 
   <td> 按列表选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按点击次数<br /> </td> 
   <td> 选择最近X个月内单击投放的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按收到的消息数<br /> </td> 
   <td> 根据收件人收到的消息数量选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按打开数<br /> </td> 
   <td> 选择在Z时间段内在X和Y投放之间打开的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按名称或电子邮件<br /> </td> 
   <td> 根据收件人的姓名或电子邮件选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按年龄范围<br /> </td> 
   <td> 根据收件人的年龄选择收件人。<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>所有与计数和期间有关的比较都将从更广泛的意义上理解（比较中包含与查询限制对应的收件人）。

数据的计算方式示例：

* 选择年龄小于30岁的收件人：

   ![](assets/predefined_filters_01.png)

* 选择18岁或以上的收件人：

   ![](assets/predefined_filters_03.png)

* 选择年龄在18到30岁之间的收件人：

   ![](assets/predefined_filters_02.png)

## 数据过滤器的高级设置 {#advanced-settings-for-data-filters}

单击 **[!UICONTROL Settings]** 选项卡访问以下选项：

* **[!UICONTROL Default filter for the associated document type]**:此选项允许您默认在排序相关列表的编辑器中建议使用此过滤器。

   例如， **[!UICONTROL By name or login]** 过滤器应用于运算符。 此选项处于选中状态，因此过滤器始终提供在所有运算符列表上。

* **[!UICONTROL Filter shared with other operators]**:利用此选项，可使过滤器可用于当前数据库上的所有其他运算符。
* **[!UICONTROL Use parameter entry form]**:利用此选项，可定义在选择此过滤器时，要在列表上方显示的过滤器字段。 利用这些字段，可定义过滤器设置。 必须通过 **[!UICONTROL Form]** 按钮。 例如，预配置的过滤器 **[!UICONTROL Recipients who have opened]**&#x200B;收件人列表中的过滤器字段允许您选择过滤器所针对的投放。

   的 **[!UICONTROL Preview]** 按钮可显示选定过滤器的结果。

* 的 **[!UICONTROL Advanced parameters]** 链接允许您定义其他设置。 特别是，您可以将SQL表与过滤器关联，以使其对共享该表的所有编辑器都通用。

   选择 **[!UICONTROL Do not restrict the filter]** 选项。

   在投放向导中提供的“投放的收件人”和“属于文件夹的投放的收件人”筛选器中启用了此选项，这些筛选器无法过载。

   ![](assets/s_ncs_user_filter_advanced_param.png)
