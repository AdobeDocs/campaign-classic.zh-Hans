---
title: 单元格
seo-title: 单元格
description: 单元格
seo-description: null
page-status-flag: never-activated
uuid: 1b18928f-04e1-4268-ab8e-ff74d78599de
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: f7187d42-56e9-4681-b172-22abd43ecd29
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 9%

---


# 单元格{#cells}

该 **[!UICONTROL Cells]** 活动以数据列的形式提供各种子集的视图。 它简化了子集操作，还设计为鼓励个性化可能性。

![](assets/wf_split_cells.png)

此活动可配置为根据用户需求输入特定参数。 默认情况下，每个子集的详细信息都会通过选项卡和选项卡在专用窗口中 **[!UICONTROL Selection]** 进行 **[!UICONTROL Advanced]** 详细介绍。 在以下示例中，表单已被修改：已添 **[!UICONTROL Data]** 加选项卡，以启用优惠与每个子集的优先级的关联。

![](assets/wf_split_cells_with_customization.png)

对于此配置，以下信息已添加到工作流表单(在Adobe Campaign **[!UICONTROL Administration > Configurations > Input forms]** 树的节点中):

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

Adobe Campaign中的入口表单个性化是专家用户专用的。 有关更多信息，请参阅此](../../configuration/using/identifying-a-form.md)章节[。
