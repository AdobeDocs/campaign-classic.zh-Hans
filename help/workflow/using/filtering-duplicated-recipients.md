---
product: campaign
title: 过滤重复的收件人
description: 了解如何过滤重复的收件人
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# 过滤重复的收件人 {#filtering-duplicated-recipients}

在此示例中，我们希望过滤在投放中显示两次或更多次的收件人，以恢复重复的用户档案。

要创建此示例，请应用以下步骤：

1. 在工作流中拖放&#x200B;**[!UICONTROL Query]**&#x200B;活动并打开该活动。
1. 单击&#x200B;**[!UICONTROL Edit query]**&#x200B;并将目标和筛选维度设置为&#x200B;**[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 将以下筛选条件定义到投放日志中存在的目标收件人。 在&#x200B;**表达式**&#x200B;列中选择&#x200B;**收件人投放日志(broadlog)**，在&#x200B;**运算符**&#x200B;列中选择&#x200B;**存在，如**。

   ![](assets/query_recipients_2.png)

1. 定义以下筛选条件以定位投放。 在“表达式”列中选择&#x200B;**[!UICONTROL Internal name]**，在“运算符”列选择&#x200B;**[!UICONTROL equal to]**。
1. 在值列中，添加目标投放的内部名称。

   ![](assets/query_recipients_3.png)

1. 使用&#x200B;**[!UICONTROL AND]**&#x200B;运算符，重复相同的操作以定位其他投放。

   ![](assets/query_recipients_4.png)

您的叫客过渡包含投放中定向的重复收件人。
