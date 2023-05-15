---
product: campaign
title: 单元格
description: 单元格
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 8%

---

# 单元格{#cells}



的 **[!UICONTROL Cells]** 活动以数据列的形式提供了各种子集的视图。 它有助于处理子集，还可鼓励实现个性化。

![](assets/wf_split_cells.png)

此活动可配置为根据用户需求输入特定参数。 默认情况下，每个子集的详细信息会通过 **[!UICONTROL Selection]** 和 **[!UICONTROL Advanced]** 选项卡。 在以下示例中，表单已被修改：a **[!UICONTROL Data]** 选项卡，以启用选件的关联和每个子集的优先级。

![](assets/wf_split_cells_with_customization.png)

对于此配置，向工作流表单中添加了以下信息(在 **[!UICONTROL Administration > Configurations > Input forms]** Adobe Campaign树节点):

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

Adobe Campaign中的登录表单个性化是专家用户保留的内容。 有关更多信息，请参阅此](../../configuration/using/identifying-a-form.md)章节[。
