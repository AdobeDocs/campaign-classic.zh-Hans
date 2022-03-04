---
product: campaign
title: 执行聚合计算
description: 了解如何在查询中执行聚合计算
feature: Workflows
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
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

1. 在 **[!UICONTROL Data to extract]**，为主键定义计数（如上一个示例中所示）。 添加 **[!UICONTROL Gender]** 字段。 检查 **[!UICONTROL Group]** 选项 **[!UICONTROL Gender]** 列。 这样，收件人将按性别分组。

   ![](assets/query_editor_nveau_27.png)

1. 在 **[!UICONTROL Sorting]** 窗口，单击 **[!UICONTROL Next]**:此处不需要排序。
1. 配置数据过滤。 在此，您希望将选择限制为居住在伦敦的联系人。

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >值区分大小写。 如果在条件中输入“London”值时没有大写字母，且收件人列表中包含带大写字母的“London”一词，则查询将失败。

1. 在 **[!UICONTROL Data formatting]** 窗口，单击 **[!UICONTROL Next]**:此示例不需要格式设置。
1. 在预览窗口中，单击 **[!UICONTROL Launch data preview]**.

   按性别进行的每种排序有三个不同的值： **2** 对于女性， **1** 对于男性和 **0** 性别未知时。 在本例中，该名单包含10名妇女、16名男子和2名性别不详的人。

   ![](assets/query_editor_agregat_04.png)
