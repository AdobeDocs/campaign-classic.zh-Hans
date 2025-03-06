---
product: campaign
title: 使用增量查询每季度更新列表
description: 在此使用案例中，增量查询用于自动更新收件人列表
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 5%

---

# 使用增量查询每季度更新列表 {#quarterly-list-update}



在以下示例中，[增量查询](incremental-query.md)用于自动更新收件人列表。 这些收件人作为季节性营销活动的一部分进行定位。

由于这些促销活动在每个季初启动以提供相关的体育活动，因此这些列表每季度更新一次。 但是，此营销活动只能每9个月定位此处的收件人一次。 这样，您就可以安排收件人的资格频度，并在这些年中针对不同的季节提供活动。

![](assets/incremental_query_example.png)

1. 将增量查询和列表更新活动添加到新工作流中。
1. 按照[创建查询](query.md#creating-a-query)中指定的方式配置活动的&#x200B;**[!UICONTROL Incremental query]**&#x200B;选项卡。
1. 选择&#x200B;**[!UICONTROL Scheduling & History]**&#x200B;选项卡，然后指定270天的历史记录。 已定向的收件人在270天（即大约9个月）内将不再被定向。

   然后单击&#x200B;**[!UICONTROL Change...]**&#x200B;按钮。

1. 若要确保在每季开始之前更新列表，请选择&#x200B;**[!UICONTROL Monthly]**。
1. 在下一个屏幕上，选择3月、6月、9月和12月。 选择每月的20日，然后选择要启动工作流的时间。
1. 接下来，选择查询的有效期。 例如，如果希望此活动永久处于活动状态，请选择&#x200B;**[!UICONTROL Permanent validity]**。

   ![](assets/incremental_query_example_2.png)

1. 在批准增量查询后，按照[列表更新](list-update.md)中的说明配置列表更新活动。

因此，该工作流将在每个季节开始之前自动启动。 列表将更新为符合条件的新收件人以接收优惠。
