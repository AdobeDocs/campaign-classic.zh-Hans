---
solution: Campaign Classic
product: campaign
title: 用例
description: 用例
audience: platform
content-type: reference
topic-tags: filtering-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 3%

---


# 用例{#use-case}

## 为订阅者电子邮件格式创建过滤器 {#creating-a-filter-on-the-email-format-of-subscribers}

此用例将向您显示如何创建筛选器，以根据订阅电子邮件格式对Newsletter收件人进行排序。

为此，我们需要使用预定义的文件管理器：这些过滤器链接到文档类型，并通过节点进 **[!UICONTROL Administration > Configuration > Predefined filters]** 行访问。 这些过滤器可用于应用程序中的每种类型的编辑器(或文档)。

数据过滤器的创建方式与预定义过滤器相同，但还有一个附加字段，用于选择要应用筛选器的文档类型。

应用以下步骤：

1. 通过节点创建新的筛 **[!UICONTROL Administration > Configuration > Predefined filters]** 选器。
1. 单击图 **[!UICONTROL Select link]** 标以选择相关文档:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. 选择订阅模式(nms:订阅)并单击 **[!UICONTROL OK]**。

   ![](assets/s_ncs_user_filter_select_schema.png)

1. 单 **[!UICONTROL Edit link]** 击视图所选文档的字段。

   ![](assets/s_ncs_user_filter_edit_schema.png)

   然后，您可以视图选定文档的内容：

   ![](assets/s_ncs_user_filter_view_schema.png)

   您可以访问这些字段以在筛选器编辑器的主体中定义筛选器条件。 应用程序过滤器的定义方式与高级过滤器完全相同。 请参 [阅创建高级过滤器](../../platform/using/creating-filters.md#creating-an-advanced-filter)。

1. 在订阅上创建新过滤器，以仅显示具有未定义电子邮件格式的订阅:

   ![](assets/s_ncs_user_filter_parameters.png)

1. 单 **[!UICONTROL Save]** 击可为此类过滤器的预定义列表添加过滤器。
1. 您现在可以在收件人用户档案的 **[!UICONTROL Subscriptions]** 选项卡中使用此过滤器；单击该按钮即可访问“未知电子邮件格式”过 **[!UICONTROL Filters]** 滤器。

   ![](assets/s_ncs_user_filter_on_events.png)

   当前筛选器的名称显示在列表上方。 要取消筛选器，请单击 **[!UICONTROL Delete this filter]** 图标。

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

