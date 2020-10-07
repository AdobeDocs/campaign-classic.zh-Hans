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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 3%

---


# 版本{#edition}

可通过节点访问用于创建和配置导航层次结构配置文档的 **[!UICONTROL Administration > Configuration > Navigation hierarchies]** 屏幕：

![](assets/d_ncs_integration_navigation_arbo.png)

导航层次结构配置被划分到多个XML文档。 它的运作原理与模式推广类似：所有文档都会合并，以生成包含整个配置的单个文档。 此文档无法编辑，并通过“预览”选项卡显示。

编辑字段提供XML文档的内容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>通过“名称”编辑控件，您可以输入由名称和文档组成的命名空间键。 元素的“name”和“命名空间”属 **`<navtree>`** 性会在模式的XML编辑字段中自动更新。

预览会自动生成包含完整配置的合并文档:

![](assets/d_ncs_integration_navigation_preview.png)

