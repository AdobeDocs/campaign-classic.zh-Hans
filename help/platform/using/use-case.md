---
solution: Campaign Classic
product: campaign
title: 用例
description: 用例
audience: platform
content-type: reference
topic-tags: filtering-data
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 3%

---


# 用例{#use-case}

## 在订阅者{#creating-a-filter-on-the-email-format-of-subscribers}的电子邮件格式上创建过滤器

此用例将向您显示如何创建筛选器以根据收件人订阅对新闻稿电子邮件格式进行排序。

为此，我们需要使用预定义的文件管理器：这些过滤器链接到文档类型，并通过&#x200B;**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;节点进行访问。 这些过滤器可用于应用程序中的每种类型的编辑器(或文档)。

数据过滤器的创建方式与预定义过滤器相同，但还有一个额外字段，用于选择要应用滤镜的文档类型。

应用以下步骤：

1. 通过&#x200B;**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;节点创建新筛选器。
1. 单击&#x200B;**[!UICONTROL Select link]**&#x200B;图标以选择相关文档:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. 选择订阅模式(nms:订阅)，然后单击&#x200B;**[!UICONTROL OK]**。

   ![](assets/s_ncs_user_filter_select_schema.png)

1. 单击&#x200B;**[!UICONTROL Edit link]**&#x200B;以视图所选文档的字段。

   ![](assets/s_ncs_user_filter_edit_schema.png)

   然后，您可以视图所选文档的内容：

   ![](assets/s_ncs_user_filter_view_schema.png)

   您可以访问这些字段以在过滤器编辑器的正文中定义过滤器条件。 应用程序过滤器的定义方式与高级过滤器完全相同。 请参阅[创建高级过滤器](../../platform/using/creating-filters.md#creating-an-advanced-filter)。

1. 在订阅上创建新筛选器以仅显示具有未定义电子邮件格式的订阅:

   ![](assets/s_ncs_user_filter_parameters.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;可向此类列表的预定义过滤器添加过滤器。
1. 您现在可以在收件人用户档案的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;选项卡中使用此过滤器；单击&#x200B;**[!UICONTROL Filters]**&#x200B;按钮可以访问“未知电子邮件格式”筛选器。

   ![](assets/s_ncs_user_filter_on_events.png)

   当前过滤器的名称显示在列表上方。 要取消筛选器，请单击&#x200B;**[!UICONTROL Delete this filter]**&#x200B;图标。

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

