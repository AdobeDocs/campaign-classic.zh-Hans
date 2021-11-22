---
product: campaign
title: 过滤重复的收件人
description: 了解如何过滤重复的收件人
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# 过滤重复的收件人 {#filtering-duplicated-recipients}

![](../../assets/common.svg)

在此示例中，我们希望过滤在投放中显示两次或更多次的收件人，以恢复重复的用户档案。

要创建此示例，请应用以下步骤：

1. 拖放 **[!UICONTROL Query]** 活动，然后打开活动。
1. 单击 **[!UICONTROL Edit query]** 并将目标和过滤维度设置为 **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. 将以下筛选条件定义到投放日志中存在的目标收件人。 选择 **收件人投放日志(broadlog)** 在 **表达式** 列，选择 **存在，如** 在 **运算符** 列。

   ![](assets/query_recipients_2.png)

1. 定义以下筛选条件以定位投放。 选择 **[!UICONTROL Internal name]** 在“表达式”列和 **[!UICONTROL equal to]** 在运算符列中。
1. 在值列中，添加目标投放的内部名称。

   ![](assets/query_recipients_3.png)

1. 使用 **[!UICONTROL AND]** 运算符，重复相同的操作以定位其他投放。

   ![](assets/query_recipients_4.png)

您的叫客过渡包含投放中定向的重复收件人。
