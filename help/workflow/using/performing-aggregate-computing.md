---
product: campaign
title: 执行聚合计算
description: 了解如何在查询中执行聚合计算
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---

# 执行聚合计算 {#performing-aggregate-computing}

![](../../assets/common.svg)

在本例中，我们希望根据性别来计算住在伦敦的收件人数量。

* 需要选择哪个表？

   收件人表(**nms:recipient**)

* 输出列中应选择哪些字段？

   主键（包含计数）和性别

* 根据哪些条件过滤信息？

   根据住在伦敦的收件人

要创建此示例，请应用以下步骤：

1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;中，定义主键的计数（如上一个示例所示）。 在输出列中添加&#x200B;**[!UICONTROL Gender]**&#x200B;字段。 选中&#x200B;**[!UICONTROL Gender]**&#x200B;列中的&#x200B;**[!UICONTROL Group]**&#x200B;选项。 这样，收件人将按性别分组。

   ![](assets/query_editor_nveau_27.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**:此处不需要排序。
1. 配置数据过滤。 在此，您希望将选择限制为居住在伦敦的联系人。

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >值区分大小写。 如果在条件中输入“London”值时没有大写字母，且收件人列表中包含带大写字母的“London”一词，则查询将失败。

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**:此示例不需要格式设置。
1. 在预览窗口中，单击&#x200B;**[!UICONTROL Launch data preview]**。

   按性别进行的每种排序有三个不同的值：对于女性，**2**；对于男性，**1**；对于性别未知的女性，**0**。 在本例中，该名单包含10名妇女、16名男子和2名性别不详的人。

   ![](assets/query_editor_agregat_04.png)
