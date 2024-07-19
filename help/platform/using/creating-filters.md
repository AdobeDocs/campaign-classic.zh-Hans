---
product: campaign
title: 创建过滤器
description: 创建过滤器
feature: Profiles
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 58e54f67-dc87-42f1-8426-6f801e8e4fb6
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1979'
ht-degree: 1%

---

# 创建过滤器{#creating-filters}



在Adobe Campaign树中导航（从主页的&#x200B;**[!UICONTROL Explorer]**&#x200B;菜单）时，数据库中包含的数据将显示在列表中。 可以将这些列表配置为仅显示运算符所需的数据。 然后，可以对过滤的数据启动操作。 筛选器配置允许您从列表&#x200B;**[!UICONTROL dynamically]**&#x200B;中选择数据。 如果修改了数据，则更新过滤的数据。

>[!NOTE]
>
>用户界面配置设置在设备级别本地定义。 有时可能有必要清理此数据，尤其是在刷新数据时出现问题的情况下。 为此，请使用&#x200B;**[!UICONTROL File > Clear the local cache]**&#x200B;菜单。

## 可用过滤器的类型 {#typology-of-available-filters}

Adobe Campaign允许您将过滤器应用于数据列表。

这些过滤器只能使用一次，您也可以保存它们以供将来使用。 您可以同时应用多个过滤器。

Adobe Campaign中有以下过滤器类型：

* **默认筛选器**

  可以通过位于列表上方的字段访问&#x200B;**默认筛选器**。 它允许您根据预定义字段进行筛选（对于收件人用户档案，默认情况下是姓名和电子邮件地址）。 您可以使用字段输入要过滤的字符，或从下拉列表中选择过滤条件。

  ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an email address in the domain "yahoo.com".
-->
您可以更改列表的默认筛选器。 有关详细信息，请参阅[更改默认筛选器](#altering-the-default-filter)。

* **简单筛选器**

  **简单筛选器**&#x200B;是对列的一次性筛选器。 在显示的列上使用一个或多个简单搜索条件来定义它们。

  您可以在同一数据列表上组合多个简单过滤器来优化搜索。 过滤器字段显示在一个字段下方。 它们可以相互独立地删除。

  ![](assets/filters_recipient_simple_filter.png)

  [创建简单筛选器](#creating-a-simple-filter)中详细介绍了简单筛选器。

* **高级筛选器**

  **高级筛选器**&#x200B;是使用数据查询或查询组合创建的。

  有关创建高级筛选器的详细信息，请参阅[创建高级筛选器](#creating-an-advanced-filter)。

  您可以使用函数来定义过滤器的内容。 有关详细信息，请参阅[创建具有函数的高级筛选器](#creating-an-advanced-filter-with-functions)。

  >[!NOTE]
  >
  >有关在Adobe Campaign中构建查询的更多信息，请参阅[此章节](../../platform/using/about-queries-in-campaign.md)。

* **用户筛选器**

  **应用程序筛选器**&#x200B;是已保存的高级筛选器，用于与其他操作员使用和共享其配置。

  位于列表上方的&#x200B;**[!UICONTROL Filters]**&#x200B;按钮提供了一组应用程序过滤器，可以组合这些过滤器来优化过滤。 [保存筛选器](#saving-a-filter)中显示了创建这些筛选器的方法。

## 更改默认筛选器 {#altering-the-default-filter}

要更改收件人列表的默认筛选器，请单击树的&#x200B;**[!UICONTROL Profiles and Targets > Pre-defined filters]**&#x200B;节点。

对于所有其他类型的数据，通过&#x200B;**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;节点配置默认筛选器。

应用以下步骤：

1. 选择您希望默认使用的筛选器。
1. 单击&#x200B;**[!UICONTROL Parameters]**&#x200B;选项卡并选择&#x200B;**[!UICONTROL Default filter for the associated document type]**。

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >如果默认筛选器已应用于列表，则需要先禁用它，然后再应用新筛选器。 为此，请单击筛选字段右侧的红叉。

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以应用筛选器。

   >[!NOTE]
   >
   >[创建高级筛选器](#creating-an-advanced-filter)和[保存筛选器](#saving-a-filter)中详细介绍了筛选器定义窗口。

## 创建简单过滤器 {#creating-a-simple-filter}

要创建&#x200B;**简单筛选器**，请应用以下步骤：

1. 右键单击要过滤的字段并选择&#x200B;**[!UICONTROL Filter on this field]**。

   ![](assets/s_ncs_user_sort_this_field.png)

   默认筛选字段显示在列表上方。

1. 从下拉列表中选择过滤器选项，或输入要应用的过滤器条件（选择或输入条件的方法取决于字段类型：文本、枚举等）。

   ![](assets/s_ncs_user_sort_fields.png)

1. 要激活过滤器，请按键盘上的Enter键，或单击过滤器字段右侧的绿色箭头。

如果要过滤数据的字段未显示在用户档案的表单中，则可以在显示的列中添加该字段，然后过滤该列。 要执行此操作，

1. 单击&#x200B;**[!UICONTROL Configure the list]**&#x200B;图标。

   ![](assets/s_ncs_user_configure_list.png)

1. 选择要显示的列，例如收件人的年龄。

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. 右键单击收件人列表中的&#x200B;**Age**&#x200B;列，然后选择&#x200B;**[!UICONTROL Filter on this column]**。

   ![](assets/s_ncs_user_sort_this_column.png)

   然后，您可以选择年龄筛选选项。

   ![](assets/s_ncs_user_delete_filter.png)

## 创建高级过滤器 {#creating-an-advanced-filter}

要创建&#x200B;**高级筛选器**，请应用以下步骤：

1. 单击&#x200B;**[!UICONTROL Filters]**&#x200B;按钮并选择&#x200B;**[!UICONTROL Advanced filter...]**。

   ![](assets/filters_recipient_create_adv_filter.png)

   您还可以右键单击要过滤的数据列表并选择&#x200B;**[!UICONTROL Advanced filter...]**。

   此时将显示筛选条件定义窗口。

1. 单击&#x200B;**[!UICONTROL Expression]**&#x200B;列以定义输入值。
1. 单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;以选择要应用过滤器的字段。

   ![](assets/s_user_filter_choose_field.png)

1. 从列表中，选择要过滤数据的字段。 单击 **[!UICONTROL Finish]** 确认。
1. 单击&#x200B;**[!UICONTROL Operator]**&#x200B;列，然后从下拉列表中选择要应用的运算符。
1. 从&#x200B;**[!UICONTROL Value]**&#x200B;列中选择所需的值。 您可以合并多个筛选器以优化查询。 要添加筛选条件，请单击&#x200B;**[!UICONTROL Add]**。

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. 您可以为表达式分配层次结构，也可以使用工具栏箭头更改查询表达式的顺序。
1. 表达式之间的默认运算符是&#x200B;**和**，但您可以通过单击字段更改此运算符。 您可以选择&#x200B;**或**&#x200B;运算符。

   ![](assets/s_ncs_user_filter_operator.png)

1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;以确认创建过滤器并将其应用于列表。

应用的过滤器显示在列表上方。

![](assets/s_ncs_user_filter_adv_edit.png)

要编辑或修改此筛选器，请单击其标签。

要取消此筛选器，请单击筛选器右侧的&#x200B;**[!UICONTROL Remove this filter]**&#x200B;图标。

![](assets/s_ncs_user_filter_adv_remove.png)

您可以保存高级过滤器，以备将来使用。 有关此类型筛选器的详细信息，请参阅[保存筛选器](#saving-a-filter)。

### 使用函数创建高级过滤器 {#creating-an-advanced-filter-with-functions}

高级筛选器可以使用函数；具有函数&#x200B;**的**&#x200B;筛选器是通过表达式编辑器创建的，该编辑器允许您使用数据库数据和高级函数创建公式。 要创建包含函数的过滤器，请重复高级过滤器创建步骤1、2和3，然后按照以下步骤操作：

1. 在字段选择窗口中，单击&#x200B;**[!UICONTROL Advanced selection]**。
1. 选择要使用的公式类型：聚合、现有用户筛选器或表达式。

   ![](assets/s_ncs_user_filter_formula_select.png)

   可以使用以下选项：

   * **[!UICONTROL Field only]**&#x200B;以选择字段。 这是默认模式。
   * **[!UICONTROL Aggregate]**&#x200B;以选择要使用的聚合公式（计数、总和、平均值、最大值、最小值）。
   * **[!UICONTROL User filter]**&#x200B;以选择现有用户筛选器之一。 [保存筛选器](#saving-a-filter)中详细介绍了用户筛选器。
   * **[!UICONTROL Expression]**&#x200B;以访问表达式编辑器。

     表达式编辑器允许您定义高级过滤器。 它看起来如下所示：

     ![](assets/s_ncs_user_create_exp_exple01.png)

     它允许您选择数据库表中的字段并将高级函数附加到该表中：选择要在&#x200B;**[!UICONTROL List of functions]**&#x200B;中使用的函数。 可用函数在[函数列表](../../platform/using/defining-filter-conditions.md#list-of-functions)中详述。 接下来，选择函数涉及的字段并单击&#x200B;**[!UICONTROL OK]**&#x200B;以批准表达式。

     >[!NOTE]
     >
     >有关基于表达式创建过滤器的示例，请参阅[此章节](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is)。

## 保存过滤器 {#saving-a-filter}

过滤器特定于每个运算符，每当运算符清除其客户端控制台的缓存时，都会重新初始化过滤器。

您可以通过保存高级筛选器来创建&#x200B;**应用程序筛选器**：可通过在任何列表中右键单击或通过位于列表上方的&#x200B;**[!UICONTROL Filters]**&#x200B;按钮重复使用该筛选器。

也可以通过目标选择阶段中的投放向导直接访问这些筛选器（有关创建投放的更多信息，请参阅[此章节](../../delivery/using/creating-an-email-delivery.md)）。 要创建应用程序过滤器，您可以：

* 将高级筛选器转换为应用程序筛选器。 要执行此操作，请在关闭高级筛选器编辑器之前单击&#x200B;**[!UICONTROL Save]**。

  ![](assets/s_ncs_user_filter_save.png)

* 通过树的&#x200B;**[!UICONTROL Administration > Configuration > Predefined filters]**（或针对收件人&#x200B;**[!UICONTROL Profiles and targets > Predefined filters]**）节点创建此应用程序筛选器。 为此，请右键单击筛选器列表，然后选择&#x200B;**[!UICONTROL New...]**。 该过程与创建高级过滤器的过程相同。

  **[!UICONTROL Label]**&#x200B;字段允许您命名此筛选器。 此名称将出现在&#x200B;**[!UICONTROL Filters...]**&#x200B;按钮的组合框中。

  ![](assets/user_filter_apply.png)

您可以通过右键单击并选择&#x200B;**[!UICONTROL No filter]**&#x200B;或通过列表上方的&#x200B;**[!UICONTROL Filters]**&#x200B;图标来删除当前列表上的所有筛选器。

您可以通过单击&#x200B;**[!UICONTROL Filters]**&#x200B;按钮并使用&#x200B;**[!UICONTROL And...]**&#x200B;菜单来组合筛选器。

![](assets/s_ncs_user_filter_combination.png)

## 筛选收件人 {#filtering-recipients}

预定义过滤器（请参阅[保存过滤器](#saving-a-filter)）允许您过滤数据库中包含的收件人的用户档案。 您可以从树的&#x200B;**[!UICONTROL Profiles and Targets > Predefined filters]**&#x200B;节点编辑筛选器。 通过&#x200B;**[!UICONTROL Filters]**&#x200B;按钮，这些筛选器在工作区的上半部分列出。

选择一个筛选器以显示其定义并访问已筛选数据的预览。

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>有关预定义过滤器创建的详细示例，请参阅[用例](../../platform/using/use-case.md)。

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
   <td> 选择在X个月内未打开投放的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按设备类型列出的最后一个活动<br /> </td> 
   <td> 选择在过去Z天内使用设备X单击或打开了投放Y的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按设备类型（跟踪）列出上次活动<br /> </td> 
   <td> 选择在过去Z天内使用设备X单击或打开了投放Y的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定位的收件人<br /> </td> 
   <td> 选择在X个月内从未通过渠道Y进行定位的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 非常活跃的收件人<br /> </td> 
   <td> 选择在过去Y个月内至少点击过投放X次的收件人。<br /> </td> 
  </tr> 
  <tr> 
 <td> 列入阻止列表电子邮件地址<br /> </td> 
    <td> 选择电子邮件地址位于阻止列表上的收件人。<br/> </td>
  </tr> 
  <tr> 
   <td> 隔离的电子邮件地址<br /> </td> 
   <td> 选择其电子邮件地址已被隔离的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 在文件夹<br />中重复的电子邮件地址 </td> 
   <td> 选择其电子邮件地址在文件夹中重复的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未打开也未单击<br /> </td> 
   <td> 选择尚未打开投放或单击投放的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 新收件人（天）<br /> </td> 
   <td> 选择最近X天创建的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 新收件人（分钟）<br /> </td> 
   <td> 选择最近X分钟创建的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 新收件人（月）<br /> </td> 
   <td> 选择过去X个月中创建的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按订阅<br /> </td> 
   <td> 按订阅选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 通过单击特定链接<br /> </td> 
   <td> 选择点击了投放中特定URL的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按投递行为<br /> </td> 
   <td> 根据收件人在收到投放后的行为选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按创建日期<br /> </td> 
   <td> 按创建日期选择从X个月（当前日期减去n个月）到Y个月（当前日期减去n个月）的期间的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按列表<br /> </td> 
   <td> 按列表选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按点击次数<br /> </td> 
   <td> 选择过去X个月内点击过投放的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按接收的邮件数<br /> </td> 
   <td> 根据收件人收到的邮件数选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按打开次数<br /> </td> 
   <td> 选择在X和Y投放之间打开超过Z时间的收件人。<br /> </td> 
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
>所有与计数和周期有关的比较应从更广泛的意义上理解（与查询限制相对应的收件人包括在比较中）。

有关如何计算数据的示例：

* 选择小于30岁的收件人：

  ![](assets/predefined_filters_01.png)

* 选择18岁或以上的收件人：

  ![](assets/predefined_filters_03.png)

* 选择年龄在18到30岁之间的收件人：

  ![](assets/predefined_filters_02.png)

## 数据过滤器的高级设置 {#advanced-settings-for-data-filters}

单击&#x200B;**[!UICONTROL Settings]**&#x200B;选项卡以访问以下选项：

* **[!UICONTROL Default filter for the associated document type]**：此选项允许您在排序相关列表的编辑器中默认建议此过滤器。

  例如，**[!UICONTROL By name or login]**&#x200B;筛选器应用于运算符。 选择此选项后，将始终在所有运算符列表中提供过滤器。

* **[!UICONTROL Filter shared with other operators]**：通过此选项，可使筛选器可用于当前数据库上的所有其他操作员。
* **[!UICONTROL Use parameter entry form]**：利用此选项可定义在选中此筛选器时要在列表上方显示的筛选器字段。 这些字段允许您定义过滤器设置。 必须通过&#x200B;**[!UICONTROL Form]**&#x200B;按钮以XML格式输入此表单。 例如，收件人列表中提供的预配置过滤器&#x200B;**[!UICONTROL Recipients who have opened]**&#x200B;会显示一个过滤器字段，允许您选择过滤器所针对的投放。

  **[!UICONTROL Preview]**&#x200B;按钮显示所选筛选器的结果。

* **[!UICONTROL Advanced parameters]**&#x200B;链接允许您定义其他设置。 特别是，您可以将SQL表与过滤器关联，使其对共享该表的所有编辑器通用。

  如果要阻止用户覆盖此筛选器，请选择&#x200B;**[!UICONTROL Do not restrict the filter]**&#x200B;选项。

  为投放向导中提供的“投放的收件人”和“属于文件夹的投放的收件人”过滤器启用此选项，这些过滤器无法过载。

  ![](assets/s_ncs_user_filter_advanced_param.png)
