---
product: campaign
title: 编辑架构
description: 了解有关编辑架构工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 9%

---

# 编辑架构{#edit-schema}



可以使用对数据进行转换、规范化并根据需要在工作流中对其进行丰富 **[!UICONTROL Edit schema]** 活动。 它通常用于标准化数据结构：您可以重命名输出列或修改其内容，例如通过计算字段或聚合的平均值。

此活动不更改工作表中的数据，只更改其架构，即数据的逻辑视图。

![](assets/wf_manipulation_box.png)

您还可以通过创建与其他工作表的联接 **[!UICONTROL Links]** 选项卡。

![](assets/wf_manipulation_box_link_tab.png)

下面的部分允许您配置连接条件的列表，即用于协调来自两个表的数据的标准。
