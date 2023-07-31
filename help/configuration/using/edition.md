---
product: campaign
title: 编辑Campaign资源管理器导航树
description: 编辑Campaign资源管理器导航树
feature: Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---


# 编辑Campaign资源管理器导航树{#edition}

用于创建和配置导航层次结构配置文档的屏幕可通过 **[!UICONTROL Administration > Configuration > Navigation hierarchies]** 节点：

![](assets/d_ncs_integration_navigation_arbo.png)

导航层次结构配置分为多个XML文档。 它的工作原理与模式扩展类似：合并所有文档以生成包含整个配置的单个文档。 此文档无法编辑，将通过“预览”选项卡显示。

编辑字段提供XML文档的内容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>“名称”编辑控件允许您输入包含名称和命名空间的文档密钥。 的“名称”和“命名空间”属性 **`<navtree>`** 元素会在架构的XML编辑字段中自动更新。

预览会自动生成包含完整配置的合并文档：

![](assets/d_ncs_integration_navigation_preview.png)
