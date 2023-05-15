---
product: campaign
title: 管理工作流
description: 管理工作流
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 11%

---

# 管理工作流{#managing-workflows}



默认情况下，您的新工作流基于预配置的工作流模板，并基于收件人表(nms:recipient)。 以便能够根据 **Nms_DefaultRcpSchema** 选项(请参阅 [配置接口](../../configuration/using/configuring-the-interface.md) 部分)，则必须创建新的工作流模板。

通过 **[!UICONTROL Resources > Templates > Workflow templates]** 节点。 在模板的属性中，提供的维度与外部收件人表相匹配。

通过将新工作流基于最近创建的模板，默认情况下会为工作流的全局定位和过滤维度选择您的个性化表。

因此，工作流中使用的所有活动都将使用您的自定义表，而无需任何其他手动配置。

如需有关此工作流的详细信息，请参阅[本章节](../../workflow/using/about-workflows.md)。

![](assets/cfg_external_table_workflow.png)
