---
product: campaign
title: 筛选重复的收件人
description: 了解如何筛选重复的收件人
feature: Workflows
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# 筛选重复的收件人 {#filtering-duplicated-recipients}



在本例中，我们要筛选在投放中出现两次或更多次的收件人，以恢复重复的用户档案。

要创建此示例，请应用以下步骤：

1. 拖放 **[!UICONTROL Query]** 活动，并打开该活动。
1. 单击 **[!UICONTROL Edit query]** 并将目标和筛选维度设置为 **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. 定义以下筛选条件，以定向投放日志中存在的收件人。 选择 **收件人投放日志(broadlog)** 在 **表达式** 列，选择 **存在，例如** 在 **运算符** 列。

   ![](assets/query_recipients_2.png)

1. 定义以下筛选条件以定向投放。 选择 **[!UICONTROL Internal name]** 在“表达式”列中和 **[!UICONTROL equal to]** 在“运算符”列中。
1. 在值列中，添加目标投放的内部名称。

   ![](assets/query_recipients_3.png)

1. 带有 **[!UICONTROL AND]** 运算符，重复相同的操作以定位其他投放。

   ![](assets/query_recipients_4.png)

叫客过渡包含投放中定向的重复收件人。
