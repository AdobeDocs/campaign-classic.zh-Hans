---
product: campaign
title: 编辑架构
description: 了解有关编辑模式工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---

# 编辑架构{#edit-schema}



数据可以进行转换、标准化，并在必要时使用 **[!UICONTROL Edit schema]** 活动。 它通常用于标准化数据结构：例如，您可以通过计算字段或聚合的平均值来重命名输出列或修改其内容。

此活动不会更改工作表中的数据，只会更改其架构，即数据的逻辑视图。

![](assets/wf_manipulation_box.png)

您还可以通过 **[!UICONTROL Links]** 选项卡。

![](assets/wf_manipulation_box_link_tab.png)

利用下部分，可配置连接条件的列表，即用于协调两个表中的数据的条件。
