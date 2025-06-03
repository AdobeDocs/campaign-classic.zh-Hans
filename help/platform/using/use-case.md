---
product: campaign
title: 用例
description: 用例
feature: Subscriptions, Email, Data Management
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
hide: true
hidefromtoc: true
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---

# 用例{#use-case}



## 根据订阅者的电子邮件格式创建过滤器 {#creating-a-filter-on-the-email-format-of-subscribers}

此用例将向您展示如何创建过滤器，以根据收件人电子邮件格式对新闻稿订阅进行排序。

为此，我们需要使用预定义的文件管理器：这些过滤器链接到文档类型，可通过&#x200B;**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;节点访问。 这些数据过滤器可用于应用程序中的每种类型的编辑器（或文档）。

创建数据过滤器的方式与预定义过滤器的方式相同，但有一个附加字段可用于选择将应用过滤器的文档类型。

应用以下步骤：

1. 通过&#x200B;**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;节点创建新筛选器。
1. 单击&#x200B;**[!UICONTROL Select link]**&#x200B;图标以选择相关文档：

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. 选择订阅架构(nms：subscription)并单击&#x200B;**[!UICONTROL OK]**。

   ![](assets/s_ncs_user_filter_select_schema.png)

1. 单击&#x200B;**[!UICONTROL Edit link]**&#x200B;查看所选文档的字段。

   ![](assets/s_ncs_user_filter_edit_schema.png)

   然后，您可以查看所选文档的内容：

   ![](assets/s_ncs_user_filter_view_schema.png)

   您可以访问这些字段，以便在过滤器编辑器的正文中定义过滤器条件。 应用程序过滤器的定义方式与高级过滤器的定义方式完全相同。 请参阅[创建高级筛选器](../../platform/using/creating-filters.md#creating-an-advanced-filter)。

1. 在订阅上创建一个新的筛选器，以仅显示具有未定义电子邮件格式的订阅：

   ![](assets/s_ncs_user_filter_parameters.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;将筛选器添加到此类型列表的预定义筛选器。
1. 您现在可以在收件人配置文件的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;选项卡中使用此过滤器；您可以通过单击&#x200B;**[!UICONTROL Filters]**&#x200B;按钮访问“未知电子邮件格式”过滤器。

   ![](assets/s_ncs_user_filter_on_events.png)

   当前过滤器的名称显示在列表上方。 要取消过滤器，请单击&#x200B;**[!UICONTROL Delete this filter]**&#x200B;图标。

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
