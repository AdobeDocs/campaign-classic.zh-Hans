---
product: campaign
title: 单元格
description: 单元格
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 13%

---

# 单元格{#cells}



此 **[!UICONTROL Cells]** 活动以数据列的形式提供各种子集的视图。 它有助于子集操作，并且还旨在鼓励个性化可能性。

![](assets/wf_split_cells.png)

此活动可配置为根据用户需求输入特定参数。 默认情况下，每个子集的详细信息都会在专用窗口中通过 **[!UICONTROL Selection]** 和 **[!UICONTROL Advanced]** 选项卡。 在以下示例中，表单已修改： **[!UICONTROL Data]** 添加了选项卡，以启用选件与每个子集的优先级之间的关联。

![](assets/wf_split_cells_with_customization.png)

对于此配置，已将以下信息添加到工作流表单(在 **[!UICONTROL Administration > Configurations > Input forms]** Adobe Campaign节点)：

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

Adobe Campaign中的登录表单个性化是为专家用户保留的。 有关更多信息，请参阅此](../../configuration/using/identifying-a-form.md)章节[。
