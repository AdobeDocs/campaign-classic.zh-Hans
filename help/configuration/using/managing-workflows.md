---
title: 管理工作流
seo-title: 管理工作流
description: 管理工作流
seo-description: null
page-status-flag: never-activated
uuid: 8b6320c0-1aae-4acd-a698-03f9bebd916d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ee724240-c337-489d-a21b-5f3aec1f247a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 12%

---


# 管理工作流{#managing-workflows}

默认情况下，您的新工作流基于已预配置的工作流模板，并基于收件人表(nms:收件人)。 要自动基于Nms_DefaultRcpSchema选项中引用的自定义收件人 **表(请参阅配** 置接口部分 [](../../configuration/using/configuring-the-interface.md) )，您必须创建新的工作流模板。

通过节点创建新 **[!UICONTROL Resources > Templates > Workflow templates]** 模板。 在模板的属性中，提供的维与外部收件人表匹配。

通过将新工作流基于最近创建的模板，默认情况下将为工作流的全局定位和过滤维度选择您的个性化表。

因此，您的工作流程中使用的所有活动都将使用您的自定义表，无需任何额外的手动配置。

如需有关此工作流的详细信息，请参阅[本章节](../../workflow/using/about-workflows.md)。

![](assets/cfg_external_table_workflow.png)

