---
solution: Campaign Classic
product: campaign
title: 编辑模式
description: 进一步了解编辑模式工作流活动
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---


# 编辑模式{#edit-schema}

数据可以使用&#x200B;**[!UICONTROL Edit schema]**&#x200B;活动进行转换、标准化，并在必要时在工作流中进行丰富。 它通常用于标准化数据结构：您可以重命名输出列或修改其内容，例如，计算字段或聚合的平均值。

此活动不会更改工作表中的数据，只更改其模式，即数据的逻辑视图。

![](assets/wf_manipulation_box.png)

还可以通过&#x200B;**[!UICONTROL Links]**&#x200B;选项卡创建与其他工作表的连接。

![](assets/wf_manipulation_box_link_tab.png)

下部分允许您配置连接条件的列表，即用于协调来自两个表的数据的条件。
