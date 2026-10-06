---
product: campaign
title: 管理工作流
description: 管理工作流
feature: Workflows, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
TQID: 'https://experienceleague.adobe.com/dpHtLw4PYGg35t-ihmw9LGUSbjgeNloUhGXp9KPJaRU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 11%
---
# 管理工作流{#managing-workflows}



默认情况下，您的新工作流基于已预配置的工作流模板以及基于收件人表(nms:recipient)。 为了使它们自动基于&#x200B;**Nms_DefaultRcpSchema**&#x200B;选项中引用的自定义收件人表（请参阅[配置接口](../../configuration/using/configuring-the-interface.md)部分），您必须创建新的工作流模板。

通过&#x200B;**[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;节点创建新模板。 在模板的属性中，提供的维度与外部收件人表匹配。

通过将新工作流基于最近创建的模板，默认情况下将为工作流的全局定位和筛选维度选择个性化表。

因此，工作流中使用的所有活动将使用您的自定义表，而无需任何其他手动配置。

如需有关此工作流的详细信息，请参阅[本章节](../../workflow/using/about-workflows.md)。

![](assets/cfg_external_table_workflow.png)
