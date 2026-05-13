---
product: campaign
title: 编辑Campaign资源管理器导航树
description: 编辑Campaign资源管理器导航树
feature: Application Settings
role: Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
TQID: https://experienceleague.adobe.com/k8LhZvPSYchAxnQew5eknkDbxHDznzPefl032auuYLc
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 131
ht-degree: 0%

---

# 编辑Campaign资源管理器导航树{#edition}

用于创建和配置导航层次结构配置文档的屏幕可通过&#x200B;**[!UICONTROL Administration > Configuration > Navigation hierarchies]**&#x200B;节点访问：

![](assets/d_ncs_integration_navigation_arbo.png)

导航层次结构配置分为多个XML文档。 它的工作原理与模式扩展类似：合并所有文档以生成包含整个配置的单个文档。 此文档无法编辑，将通过“预览”选项卡显示。

编辑字段提供XML文档的内容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>“名称”编辑控件允许您输入包含名称和命名空间的文档密钥。 **`<navtree>`**&#x200B;元素的“name”和“namespace”属性在架构的XML编辑字段中自动更新。

预览会自动生成包含完整配置的合并文档：

![](assets/d_ncs_integration_navigation_preview.png)
