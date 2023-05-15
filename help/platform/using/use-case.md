---
product: campaign
title: 用例
description: 用例
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 3%

---

# 用例{#use-case}



## 根据订阅者的电子邮件格式创建过滤器 {#creating-a-filter-on-the-email-format-of-subscribers}

此用例将向您展示如何创建过滤器，以根据收件人电子邮件格式对新闻稿订阅进行排序。

为此，我们需要使用预定义的文件管理器：这些过滤器链接到文档类型，并可通过 **[!UICONTROL Administration > Configuration > Predefined filters]** 节点。 这些数据过滤器可用于应用程序中的每种类型的编辑器（或文档）。

数据过滤器的创建方式与预定义过滤器相同，但还有一个额外的字段用于选择要应用过滤器的文档类型。

应用以下步骤：

1. 通过 **[!UICONTROL Administration > Configuration > Predefined filters]** 节点。
1. 单击 **[!UICONTROL Select link]** 图标以选择相关文档：

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. 选择订阅模式(nms:subscription)并单击 **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. 单击 **[!UICONTROL Edit link]** 查看所选文档的字段。

   ![](assets/s_ncs_user_filter_edit_schema.png)

   然后，您可以查看所选文档的内容：

   ![](assets/s_ncs_user_filter_view_schema.png)

   您可以访问这些字段，以在过滤器编辑器的正文中定义过滤器条件。 应用程序过滤器的定义方式与高级过滤器完全相同。 请参阅 [创建高级过滤器](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. 为订阅创建新筛选器，以仅显示电子邮件格式未定义的订阅：

   ![](assets/s_ncs_user_filter_parameters.png)

1. 单击 **[!UICONTROL Save]** 向此类型列表的预定义过滤器中添加过滤器。
1. 您现在可以在 **[!UICONTROL Subscriptions]** 选项卡；您可以通过单击 **[!UICONTROL Filters]** 按钮。

   ![](assets/s_ncs_user_filter_on_events.png)

   当前过滤器的名称显示在列表上方。 要取消过滤器，请单击 **[!UICONTROL Delete this filter]** 图标。

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
