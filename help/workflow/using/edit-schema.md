---
product: campaign
title: 编辑架构
description: 了解有关编辑模式工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---

# 编辑架构{#edit-schema}

可以使用&#x200B;**[!UICONTROL Edit schema]**&#x200B;活动在工作流中转换、标准化数据，并在必要时进行扩充。 它通常用于标准化数据结构：例如，您可以通过计算字段或聚合的平均值来重命名输出列或修改其内容。

此活动不会更改工作表中的数据，只会更改其架构，即数据的逻辑视图。

![](assets/wf_manipulation_box.png)

您还可以通过&#x200B;**[!UICONTROL Links]**&#x200B;选项卡创建与其他工作表的连接。

![](assets/wf_manipulation_box_link_tab.png)

利用下部分，可配置连接条件的列表，即用于协调两个表中的数据的条件。
