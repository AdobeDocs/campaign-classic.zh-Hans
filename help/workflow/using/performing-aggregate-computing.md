---
solution: Campaign Classic
product: campaign
title: 执行聚合计算
description: 了解如何在查询中执行聚合计算
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---


# 执行聚合计算 {#performing-aggregate-computing}

在这个例子中，我们想根据性别来计算住在伦敦的收件人的数量。

* 需要选择哪个表？

   收件人表(**nms:收件人**)

* 应在输出列中选择哪些字段？

   主键（含数）和性别

* 信息过滤所依据的条件是什么？

   根据住在伦敦的收件人

要创建此示例，请应用以下步骤：

1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;中，定义主键的计数（如上例所示）。 在输出列中添加&#x200B;**[!UICONTROL Gender]**&#x200B;字段。 检查&#x200B;**[!UICONTROL Gender]**&#x200B;列中的&#x200B;**[!UICONTROL Group]**&#x200B;选项。 这样，收件人将按性别分组。

   ![](assets/query_editor_nveau_27.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**:此处不需要排序。
1. 配置数据过滤。 此处，您希望将选择限制为居住在伦敦的联系人。

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >值区分大小写。 如果输入条件中的“伦敦”值时没有大写字母，而收件人的列表包含带大写字母的“伦敦”一词，则查询将失败。

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**:此示例不需要格式设置。
1. 在预览窗口中，单击&#x200B;**[!UICONTROL Launch data preview]**。

   每个按性别排序有三个不同的值：对于女性，**2**&#x200B;对于男性，**1**；对于性别未知的女性，**0**。 在本例中，该列表有10名妇女、16名男子和2名性别不明的人。

   ![](assets/query_editor_agregat_04.png)
