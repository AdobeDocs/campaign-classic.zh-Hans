---
product: campaign
title: 执行聚合计算
description: 了解如何在查询中执行聚合计算
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# 执行聚合计算 {#performing-aggregate-computing}



在本例中，我们要根据性别统计居住在伦敦的接收人数。

* 需要选择哪个表？

  收件人表(**nms：recipient**)

* 应在输出列中选择哪些字段？

  主键（计数）和性别

* 信息过滤基于什么条件？

  基于居住在伦敦的收件人

要创建此示例，请应用以下步骤：

1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;中，定义主键的计数（如上一个示例所示）。 在输出列中添加字段&#x200B;**[!UICONTROL Gender]**。 检查&#x200B;**[!UICONTROL Gender]**&#x200B;列中的&#x200B;**[!UICONTROL Group]**&#x200B;选项。 这样，收件人将按性别分组。

   ![](assets/query_editor_nveau_27.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**：此处不需要排序。
1. 配置数据筛选。 在此，您希望将选择限制为居住在伦敦的联系人。

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >值区分大小写。 如果在条件中输入“London”值时没有使用大写字母，并且收件人列表包含带大写字母的“London”一词，则查询将失败。

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**：此示例不需要格式化。
1. 在预览窗口中，单击&#x200B;**[!UICONTROL Launch data preview]**。

   每种按性别排序都有三个单独的值：女性为&#x200B;**2**，男性为&#x200B;**1**，性别未知时为&#x200B;**0**。 在本例中，名单上有10名妇女、16名男子和2名性别不明的妇女。

   ![](assets/query_editor_agregat_04.png)
