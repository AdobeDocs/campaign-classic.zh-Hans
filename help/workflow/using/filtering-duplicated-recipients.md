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

在此示例中，我们要过滤在投放中显示两次或两次以上的收件人，以恢复重复的用户档案。

要创建此示例，请应用以下步骤：

1. 在工作流中拖放&#x200B;**[!UICONTROL Query]**&#x200B;活动并打开活动。
1. 单击&#x200B;**[!UICONTROL Edit query]**，将目标和过滤维度设置为&#x200B;**[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 定义以下筛选器条件以目标收件人日志中存在的筛选器条件。 在&#x200B;**收件人**&#x200B;列中选择&#x200B;**表达式投放日志(broadlog)**，在&#x200B;**运算符**&#x200B;列中选择&#x200B;**存在，如**。

   ![](assets/query_recipients_2.png)

1. 定义以下筛选器条件以目标投放。 在“表达式”列中选择&#x200B;**[!UICONTROL Internal name]**，在“运算符”列中选择&#x200B;**[!UICONTROL equal to]**。
1. 在值列中，添加目标投放的内部名称。

   ![](assets/query_recipients_3.png)

1. 使用&#x200B;**[!UICONTROL AND]**&#x200B;运算符，重复相同的操作以目标其他投放。

   ![](assets/query_recipients_4.png)

您的出站过渡包含重复收件人中的目标投放。
