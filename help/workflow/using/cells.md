---
product: campaign
title: 单元格
description: 单元格
feature: Workflows, Targeting Activity
hide: true
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
TQID: https://experienceleague.adobe.com/hYy1-NOxnpCxVNYLV4QfiLJPec0IAQ4NlNy6RM6pYjA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 127
ht-degree: 8%

---

# 单元格{#cells}



**[!UICONTROL Cells]**&#x200B;活动以数据列的形式提供各种子集的视图。 它有助于子集操作，并且还旨在鼓励个性化可能性。

![](assets/wf_split_cells.png)

此活动可配置为根据用户需求输入特定参数。 默认情况下，每个子集的详细信息通过&#x200B;**[!UICONTROL Selection]**&#x200B;和&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡在专用窗口中进行详细介绍。 在以下示例中，表单已修改：添加了&#x200B;**[!UICONTROL Data]**&#x200B;选项卡以启用每个子集的选件和优先级之间的关联。

![](assets/wf_split_cells_with_customization.png)

对于此配置，已将以下信息添加到工作流表单（在Adobe Campaign树的&#x200B;**[!UICONTROL Administration > Configurations > Input forms]**&#x200B;节点中）：

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

Adobe Campaign中的登录表单个性化是为专家用户保留的。 有关更多信息，请参阅此[&#128279;](../../configuration/using/identifying-a-form.md)章节。
