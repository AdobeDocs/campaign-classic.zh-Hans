---
solution: Campaign Classic
product: campaign
title: 过滤重复的收件人
description: 了解如何过滤重复的收件人
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---


# 过滤重复的收件人 {#filtering-duplicated-recipients}

在此示例中，我们要过滤在投放中出现两次或两次以上的收件人，以恢复重复的用户档案。

要创建此示例，请应用以下步骤：

1. 在工作流中拖 **[!UICONTROL Query]** 放活动并打开活动。
1. 单击 **[!UICONTROL Edit query]** 并将目标和过滤维度设置为 **[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 为目标日志中存在的收件人定义以下筛选器条件。 在 **收件人列中选择投放日志** (broadlog) **，选** 择“表达式”列中存在 **(如操** 作符 **** 列中存在)。

   ![](assets/query_recipients_2.png)

1. 定义以下筛选条件以目标投放。 在“ **[!UICONTROL Internal name]** 表达式”列和“运 **[!UICONTROL equal to]** 算符”列中选择。
1. 在值列中，添加目标投放的内部名称。

   ![](assets/query_recipients_3.png)

1. 使用运 **[!UICONTROL AND]** 算符，重复相同的操作以目标其他投放。

   ![](assets/query_recipients_4.png)

您的出站过渡包含重复收件人中的目标投放。
