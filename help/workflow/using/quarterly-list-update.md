---
product: campaign
title: 使用增量查询每季度更新列表
description: 在此用例中，使用增量查询自动更新收件人列表。
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 5%

---

# 使用增量查询每季度更新列表 {#quarterly-list-update}

![](../../assets/common.svg)

在以下示例中， [增量查询](incremental-query.md) 用于自动更新收件人列表。 这些收件人作为季节性营销活动的一部分进行定位。

由于这些营销活动在每季开始时启动以提供相关的体育活动，因此这些列表会在每季度进行更新。 但是，此营销活动每9个月只能定位一位此处的收件人。 这样，您就可以排除收件人的资格频率，并为多年来的不同季节提供活动。

![](assets/incremental_query_example.png)

1. 将增量查询和列表更新活动添加到新工作流中。
1. 配置 **[!UICONTROL Incremental query]** 选项卡(在 [创建查询](query.md#creating-a-query).
1. 选择 **[!UICONTROL Scheduling & History]** 选项卡，然后指定270天的历史记录。 已经定向的收件人将不再定向270天，即大约9个月。

   然后，单击 **[!UICONTROL Change...]** 按钮。

1. 要确保列表在每个季节开始之前更新，请选择 **[!UICONTROL Monthly]**.
1. 在下一个屏幕中，选择3月、6月、9月和12月。 选择每月的20号，然后选择要启动工作流的时间。
1. 接下来，选择查询的有效期。 例如，如果您希望此活动永久处于活动状态，请选择 **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. 批准增量查询后，请按照 [列表更新](list-update.md).

因此，工作流将在每个季节开始之前自动启动。 该列表将更新，显示有资格接收选件的新收件人。
