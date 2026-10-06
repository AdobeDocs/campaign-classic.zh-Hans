---
product: campaign
title: 编辑架构
description: 了解有关编辑架构工作流活动的更多信息
feature: Workflows, Targeting Activity
hide: true
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
TQID: 'https://experienceleague.adobe.com/cxBDJJXifg7C4vtB5MPBYSluRpgnbsBkDiuSsnIHDYo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%
---
# 编辑架构{#edit-schema}



可以使用&#x200B;**[!UICONTROL Edit schema]**&#x200B;活动在工作流中转换、规范化和扩充数据（如有必要）。 它通常用于标准化数据结构：您可以重命名输出列或修改其内容，例如通过计算字段或聚合的平均值。

此活动不更改工作表中的数据，只更改其架构，即数据的逻辑视图。

![](assets/wf_manipulation_box.png)

您还可以通过&#x200B;**[!UICONTROL Links]**&#x200B;选项卡创建与其他工作表的联接。

![](assets/wf_manipulation_box_link_tab.png)

下面的部分允许您配置连接条件的列表，即用于协调来自两个表的数据的标准。
