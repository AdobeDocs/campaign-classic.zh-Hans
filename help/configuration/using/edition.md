---
product: campaign
title: 版本
description: 编辑
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# 编辑Campaign Explorer导航树{#edition}

![](../../assets/v7-only.svg)

创建和配置导航层次结构配置文档的屏幕可通过 **[!UICONTROL Administration > Configuration > Navigation hierarchies]** 节点：

![](assets/d_ncs_integration_navigation_arbo.png)

导航层次结构配置分为多个XML文档。 它遵循与模式扩展类似的原则：将合并所有文档以生成包含整个配置的单个文档。 无法编辑此文档，该文档通过“预览”选项卡显示。

编辑字段提供XML文档的内容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>“名称”编辑控件允许您输入包含名称和命名空间的文档键。 的“name”和“namespace”属性 **`<navtree>`** 元素会在架构的XML edit字段中自动更新。

预览会自动生成包含完整配置的合并文档：

![](assets/d_ncs_integration_navigation_preview.png)
