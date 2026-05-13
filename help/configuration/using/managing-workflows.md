---
product: campaign
title: 管理工作流
description: 管理工作流
feature: Workflows, Configuration
role: Developer
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
TQID: https://experienceleague.adobe.com/dpHtLw4PYGg35t-ihmw9LGUSbjgeNloUhGXp9KPJaRU
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 142
ht-degree: 10%

---

# 管理工作流{#managing-workflows}



默认情况下，您的新工作流基于已预配置的工作流模板以及基于收件人表(nms:recipient)。 为了使它们自动基于&#x200B;**Nms_DefaultRcpSchema**&#x200B;选项中引用的自定义收件人表（请参阅[配置接口](../../configuration/using/configuring-the-interface.md)部分），您必须创建新的工作流模板。

通过&#x200B;**[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;节点创建新模板。 在模板的属性中，提供的维度与外部收件人表匹配。

通过将新工作流基于最近创建的模板，默认情况下将为工作流的全局定位和筛选维度选择个性化表。

因此，工作流中使用的所有活动将使用您的自定义表，而无需任何其他手动配置。

如需有关此工作流的详细信息，请参阅[本章节](../../workflow/using/about-workflows.md)。

![](assets/cfg_external_table_workflow.png)
