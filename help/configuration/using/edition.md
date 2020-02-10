---
title: 版本
seo-title: 版本
description: 版本
seo-description: null
page-status-flag: never-activated
uuid: df9298fc-5f62-4afb-8118-ca7e3987e81f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: 820be231-af76-44ce-8f4d-cd5eae1eb169
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 版本{#edition}

可通过节点访问用于创建和配置导航层次结构配置文档的 **[!UICONTROL Administration > Configuration > Navigation hierarchies]** 屏幕：

![](assets/d_ncs_integration_navigation_arbo.png)

导航层次结构配置被分为多个XML文档。 它的运行原理与架构扩展类似：将合并所有文档以生成包含整个配置的单个文档。 此文档无法编辑，并通过“预览”选项卡显示。

编辑字段提供XML文档的内容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>使用“名称”编辑控件可以输入包含名称和命名空间的文档密钥。 元素的“name”和“namespace”属性会 **`<navtree>`** 在架构的XML编辑字段中自动更新。

预览会自动生成包含完整配置的合并文档：

![](assets/d_ncs_integration_navigation_preview.png)

