---
title: 执行聚合计算
description: 了解如何在查询中执行聚合计算
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 执行聚合计算 {#performing-aggregate-computing}

在此示例中，我们希望根据性别计算住在伦敦的收件人数。

* 需要选择哪个表？

   收件人表(**nms:recipient**)

* 应在输出列中选择哪些字段？

   主要关键字（含计数）和性别

* 根据哪些条件筛选信息？

   根据住在伦敦的收件人

要创建此示例，请应用以下步骤：

1. 在 **[!UICONTROL Data to extract]**&#x200B;中，定义主键的计数（如上一个示例所示）。 在输出 **[!UICONTROL Gender]** 列中添加字段。 选中列 **[!UICONTROL Group]** 中的选 **[!UICONTROL Gender]** 项。 这样，收件人将按性别分组。

   ![](assets/query_editor_nveau_27.png)

1. 在窗口 **[!UICONTROL Sorting]** 中，单击 **[!UICONTROL Next]**:此处不需要排序。
1. 配置数据过滤。 此处，您希望将选择限制为居住在伦敦的联系人。

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >值区分大小写。 如果在条件中输入“伦敦”值时没有大写字母，收件人列表中包含带大写字母的“伦敦”一词，则查询将失败。

1. 在窗口 **[!UICONTROL Data formatting]** 中，单击 **[!UICONTROL Next]**:此示例不需要格式设置。
1. 在预览窗口中，单击 **[!UICONTROL Launch data preview]**。

   按性别分类的每个排序有三个不同的值：女 **性** 2人，男性 **1人，** 性别不明 **** 时0人。 在本例中，名单中有10名妇女、16名男子和2名性别不明的人。

   ![](assets/query_editor_agregat_04.png)
