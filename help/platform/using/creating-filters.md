---
title: 创建滤镜
seo-title: 创建滤镜
description: 创建滤镜
seo-description: null
page-status-flag: never-activated
uuid: 9fa4a80d-8f03-4f24-92a1-44f6ae2a2337
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: filtering-data
discoiquuid: 066e730b-2527-4257-b11f-2e73f746a8a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 创建滤镜{#creating-filters}

## 简介 {#introduction}

当您在Adobe Campaign树中导航(从主页的菜 **[!UICONTROL Explorer]** 单中)时，数据库中包含的数据将显示在列表中。 这些列表可以配置为仅显示操作员需要的数据。 然后，可以对已过滤的数据启动操作。 过滤器配置允许您从列表中选择数据 **[!UICONTROL dynamically]**。 如果修改了数据，则更新过滤的数据。

>[!NOTE]
>
>显示配置在工作站级别本地定义。 它存储在隐藏文件中，有时可能需要清理此数据，尤其是在刷新数据时出现问题时。 为此，请使用菜 **[!UICONTROL File > Clear the local cache]** 单。

## 可用过滤器的类型学 {#typology-of-available-filters}

Adobe Campaign允许您将过滤器应用于数据列表。

这些过滤器可以使用一次，也可以保存以供将来使用。 可以同时应用多个过滤器。

Adobe Campaign中提供以下筛选器类型：

* 默认过滤器

   可 **通过列表上方的字段** ，访问默认过滤器。 它允许您筛选预定义的字段（对于收件人配置文件，默认情况下这些字段是名称和电子邮件地址）。 您可以使用字段输入字符以在下拉列表中进行筛选或从下拉列表中选择筛选条件。

   ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an e-mail address in the domain "yahoo.com".
-->
您可以更改列表的默认过滤器。 有关此功能的详细信息，请参 [阅更改默认过滤器](#altering-the-default-filter)。

* 简单滤镜

   **简单过滤器** ，是列上的一次性过滤器。 在显示的列上，这些搜索条件使用一个或多个简单的搜索条件进行定义。

   您可以将多个简单的筛选器组合到同一数据列表上以细化搜索。 过滤器字段显示在另一个下方。 可以相互独立地删除它们。

   ![](assets/filters_recipient_simple_filter.png)

   创建简单过滤器中 [详细介绍了简单过滤器](#creating-a-simple-filter)。

* 高级滤镜

   **高级过滤器** ，使用对数据的查询或查询的组合来创建。

   有关创建高级过滤器的详细信息，请参阅 [创建高级过滤器](#creating-an-advanced-filter)。

   您可以使用函数定义过滤器的内容。 有关此功能的详细信息，请参 [阅使用函数创建高级过滤器](#creating-an-advanced-filter-with-functions)。

   >[!NOTE]
   >
   >有关在Adobe Campaign中构建查询的详细信息，请参 [阅此部分](../../platform/using/about-queries-in-campaign.md)。

* 用户过滤器

   应 **用程序过滤器** ，是已保存的高级过滤器，用于与其他操作符使用和共享其配置。

   位于 **[!UICONTROL Filters]** 列表上方的按钮提供了一组应用程序过滤器，这些过滤器可以组合在一起来调整过滤。 在保存过滤器中介绍了创建这些过 [滤器的方法](#saving-a-filter)。

## 更改默认滤镜 {#altering-the-default-filter}

要更改收件人列表的默认过滤器，请单 **[!UICONTROL Profiles and Targets > Pre-defined filters]** 击树的节点。

对于所有其他类型的数据，请通过节点配置默认过 **[!UICONTROL Administration > Configuration > Predefined filters]** 滤器。

应用以下步骤：

1. 选择您要默认使用的过滤器。
1. 单击选 **[!UICONTROL Parameters]** 项卡并选择 **[!UICONTROL Default filter for the associated document type]**。

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >如果已将默认过滤器应用到列表，则需要在应用新过滤器之前禁用该过滤器。 为此，请单击筛选字段右侧的红叉。

1. 单 **[!UICONTROL Save]** 击以应用滤镜。

   >[!NOTE]
   >
   >创建高级过滤器和保存过 [滤器中详细介绍了过滤器](#creating-an-advanced-filter)[定义窗口](#saving-a-filter)。

## 创建简单的滤镜 {#creating-a-simple-filter}

要创建简单 **的过滤器**，请应用以下步骤：

1. 右键单击要筛选的字段，然后选择 **[!UICONTROL Filter on this field]**。

   ![](assets/s_ncs_user_sort_this_field.png)

   默认过滤器字段显示在列表上方。

1. 从下拉列表中选择筛选器选项，或输入要应用的筛选条件(选择或输入条件的方法取决于字段的类型：文本、枚举等。)

   ![](assets/s_ncs_user_sort_fields.png)

1. 要激活滤镜，请按键盘上的Enter，或单击滤镜字段右侧的绿色箭头。

如果要筛选数据的字段未以配置文件的形式显示，则可以在显示的列中添加它，然后对该列进行筛选。 为此，

1. 单击该 **[!UICONTROL Configure the list]** 图标。

   ![](assets/s_ncs_user_configure_list.png)

1. 选择要显示的列，例如收件人的年龄。

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. 右键单击收件 **人列表中** “年龄”列，然后选择 **[!UICONTROL Filter on this column]**。

   ![](assets/s_ncs_user_sort_this_column.png)

   然后，您可以选择年龄筛选选项。

   ![](assets/s_ncs_user_delete_filter.png)

## 创建高级过滤器 {#creating-an-advanced-filter}

要创建高级 **过滤器**，请应用以下步骤：

1. Click the **[!UICONTROL Filters]** button and select **[!UICONTROL Advanced filter...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   您还可以右键单击要筛选和选择的数据列表 **[!UICONTROL Advanced filter...]**。

   将显示过滤条件定义窗口。

1. 单击 **[!UICONTROL Expression]** 列以定义输入值。
1. 单 **[!UICONTROL Edit expression]** 击以选择要应用滤镜的字段。

   ![](assets/s_user_filter_choose_field.png)

1. 从列表中，选择要筛选数据的字段。 Click **[!UICONTROL Finish]** to confirm.
1. 单击列 **[!UICONTROL Operator]** 并从下拉列表中选择要应用的运算符。
1. 从列中选择一个预期 **[!UICONTROL Value]** 值。 您可以组合多个过滤器来优化查询。 要添加筛选条件，请单击 **[!UICONTROL Add]**。

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. 您可以为表达式分配层次，或使用工具栏箭头更改查询表达式的顺序。
1. 表达式之间的默认运算符是 **And**，但您可以通过单击字段来更改此值。 您可以选择 **Or** 运算符。

   ![](assets/s_ncs_user_filter_operator.png)

1. 单击 **[!UICONTROL OK]** 以确认创建过滤器并将其应用到列表。

应用的过滤器显示在列表上方。

![](assets/s_ncs_user_filter_adv_edit.png)

要编辑或修改此过滤器，请单击其标签。

要取消此过滤器，请单 **[!UICONTROL Remove this filter]** 击过滤器右侧的图标。

![](assets/s_ncs_user_filter_adv_remove.png)

您可以保存高级过滤器以将其保留以供将来使用。 有关此类过滤器的详细信息，请参阅 [保存过滤器](#saving-a-filter)。

### 使用函数创建高级过滤器 {#creating-an-advanced-filter-with-functions}

高级过滤器可以使用函数；具 **有函数的过滤器** ，通过表达式编辑器创建，该编辑器允许您使用数据库数据和高级函数创建公式。 要创建具有函数的过滤器，请重复创建高级过滤器步骤1、2和3，然后按如下步骤继续：

1. 在字段选择窗口中，单击 **[!UICONTROL Advanced selection]**。
1. 选择要使用的公式类型：聚合、现有用户过滤器或表达式。

   ![](assets/s_ncs_user_filter_formula_select.png)

   可以使用以下选项：

   * **[!UICONTROL Field only]** 中。 这是默认模式。
   * **[!UICONTROL Aggregate]** 选择要使用的汇总公式（计数、总和、平均、最大、最小值）。
   * **[!UICONTROL User filter]** 来选择现有用户筛选器之一。 保存过滤器中详细介绍了 [用户过滤器](#saving-a-filter)。
   * **[!UICONTROL Expression]** 访问表达式编辑器。

      表达式编辑器允许您定义高级过滤器。 它看起来如下所示：

      ![](assets/s_ncs_user_create_exp_exple01.png)

      它允许您选择数据库表中的字段，并为它们附加高级函数：选择要在中使用的函数 **[!UICONTROL List of functions]**。 功能列表中详细介绍 [了可用的功能](../../platform/using/defining-filter-conditions.md#list-of-functions)。 接下来，选择函数所关注的字段，然后单击以 **[!UICONTROL OK]** 批准表达式。

      >[!NOTE]
      >
      >有关基于表达式创建过滤器的示例，请参阅识 [别生日的收件人](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is)。

## 保存过滤器 {#saving-a-filter}

过滤器特定于每个操作员，并在每次操作员清除其客户端控制台的缓存时重新初始化。

您可以通过保存高 **级过滤器** 来创建应用程序过滤器：可通过右键单击任意列表或通过列表上方的按钮重 **[!UICONTROL Filters]** 新使用它。

这些过滤器还可以通过目标选择阶段的交付向导直接访问(有关创建分发的 [详细信息](../../delivery/using/creating-an-email-delivery.md) ，请参阅此部分)。 要创建应用程序过滤器，您可以：

* 将高级过滤器转换为应用程序过滤器。 为此，请在关闭高级 **[!UICONTROL Save]** 过滤器编辑器之前单击。

   ![](assets/s_ncs_user_filter_save.png)

* 通过树的（或收件人） **[!UICONTROL Administration > Configuration > Predefined filters]** 节点创 **[!UICONTROL Profiles and targets > Predefined filters]** 建此应用程序过滤器。 为此，请右键单击过滤器列表，然后选择 **[!UICONTROL New...]**。 该过程与创建高级过滤器的过程相同。

   该字 **[!UICONTROL Label]** 段允许您命名此过滤器。 此名称将显示在按钮的组合框 **[!UICONTROL Filters...]** 中。

   ![](assets/user_filter_apply.png)

您可以通过右键单击并选择或通过列表上方的图标，删除当 **[!UICONTROL No filter]** 前列表上 **[!UICONTROL Filters]** 的所有过滤器。

单击按钮并使用菜单，可 **[!UICONTROL Filters]** 以组合滤镜 **[!UICONTROL And...]** 。

![](assets/s_ncs_user_filter_combination.png)

## 筛选收件人 {#filtering-recipients}

预定义的过滤器( [请参阅保存过滤器](#saving-a-filter))使您能够过滤数据库中包含的收件人的配置文件。 您可以从树的节点 **[!UICONTROL Profiles and Targets > Predefined filters]** 编辑过滤器。 这些过滤器通过按钮列在工作区的上部 **[!UICONTROL Filters]** 分。

选择过滤器以显示其定义并访问已过滤数据的预览。

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>有关预定义过滤器创建的详细示例，请参阅 [用例](../../platform/using/use-case.md)。

预定义的过滤器有：

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>查询</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 已打开<br /> </td> 
   <td> 选择已打开分发的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已打开但未单击<br /> </td> 
   <td> 选择已打开分发但未单击链接的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不活动的收件人<br /> </td> 
   <td> 选择在X个月内未打开分发的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按设备类型列出的上次活动<br /> </td> 
   <td> 选择在最近Z天内使用设备X单击或打开传送Y的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按设备类型列出的上次活动（跟踪）<br /> </td> 
   <td> 选择在最近Z天内使用设备X单击或打开传送Y的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定向收件人<br /> </td> 
   <td> 选择在X个月内从未通过渠道Y定位的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 非常活跃的收件人<br /> </td> 
   <td> 选择在最近Y个月中点击了至少X次分发的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 列入黑名单的电子邮件地址<br /> </td> 
   <td> 选择其电子邮件地址列入黑名单的收件人。<br /> </td> 
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
   <td> 选择尚未打开分发或已单击分发的收件人。<br /> </td> 
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
   <td> 选择在最近X个月中创建的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按订阅<br /> </td> 
   <td> 按订阅选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击特定链接<br /> </td> 
   <td> 选择在分发中单击特定URL的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按帖子交付行为<br /> </td> 
   <td> 在收到分发后，根据收件人的行为选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按创建日期<br /> </td> 
   <td> 按创建日期，在从X个月（当前日期减n个月）到Y个月（当前日期减n月）的期间内选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按列表<br /> </td> 
   <td> 按列表选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按点击次数<br /> </td> 
   <td> 选择在最近X个月中单击了分发的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按收到的消息数<br /> </td> 
   <td> 根据接收到的消息数选择收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按打开次数<br /> </td> 
   <td> 选择在Z时间段内在X和Y传送之间打开的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按姓名或电子邮件<br /> </td> 
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
>所有与计数和期间相关的比较都应从更广义的角度理解（与查询限制相对应的接收者包含在比较中）。

数据的计算方式示例：

* 选择年龄小于30岁的收件人：

   ![](assets/predefined_filters_01.png)

* 选择年满18周岁的收件人：

   ![](assets/predefined_filters_03.png)

* 选择年龄在18到30岁之间的收件人：

   ![](assets/predefined_filters_02.png)

## 数据过滤器的高级设置 {#advanced-settings-for-data-filters}

单击选 **[!UICONTROL Settings]** 项卡以访问以下选项：

* **[!UICONTROL Default filter for the associated document type]**:此选项允许您默认在排序相关列表的编辑器中建议使用此过滤器。

   例如，过滤器 **[!UICONTROL By name or login]** 应用于操作符。 此选项处于选中状态，因此过滤器始终在所有运算符列表中提供。

* **[!UICONTROL Filter shared with other operators]**:此选项允许您使过滤器对当前数据库上的所有其他运算符可用。
* **[!UICONTROL Use parameter entry form]**:此选项允许您定义在选择此过滤器时要显示在列表上方的过滤器字段。 这些字段允许您定义过滤器设置。 必须通过按钮以XML格式输入此表 **[!UICONTROL Form]** 单。 例如，从收件人列表 **[!UICONTROL Recipients who have opened]**&#x200B;中可用的预配置过滤器会显示一个过滤器字段，通过该字段可以选择过滤器所针对的分发。

   该按 **[!UICONTROL Preview]** 钮显示所选滤镜的结果。

* 通过 **[!UICONTROL Advanced parameters]** 该链接可以定义其他设置。 特别是，您可以将SQL表与过滤器关联，以使共享表的所有编辑器都能使用它。

   如果要 **[!UICONTROL Do not restrict the filter]** 阻止用户覆盖此过滤器，请选择此选项。

   此选项针对在交付向导中提供的“交付的收件人”和“属于文件夹的交付的收件人”筛选器启用，这些筛选器无法过载。

   ![](assets/s_ncs_user_filter_advanced_param.png)

