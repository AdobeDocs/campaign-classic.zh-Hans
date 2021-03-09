---
solution: Campaign Classic
product: campaign
title: 版本
description: 版本
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: d6993725ed4060f2affce98c4a8a5211bda03bdf
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 1%

---


# 编辑活动资源管理器导航树{#edition}

可通过&#x200B;**[!UICONTROL Administration > Configuration > Navigation hierarchies]**&#x200B;节点访问用于创建和配置导航层次结构配置文档的屏幕：

![](assets/d_ncs_integration_navigation_arbo.png)

导航层次结构配置分为多个XML文档。 它的运作原理与模式推广类似：所有文档都将合并，以生成包含整个配置的单个文档。 此文档无法编辑，并通过“预览”选项卡显示。

编辑字段提供XML文档的内容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>通过“名称”编辑控件，可以输入由名称和文档组成的命名空间键。 **`<navtree>`**&#x200B;元素的“name”和“命名空间”属性会在模式的XML编辑字段中自动更新。

预览会自动生成包含完整配置的合并文档:

![](assets/d_ncs_integration_navigation_preview.png)

