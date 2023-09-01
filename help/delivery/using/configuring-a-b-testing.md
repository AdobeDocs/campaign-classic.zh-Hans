---
product: campaign
title: 配置 A/B 测试
description: 了解如何在Campaign中配置A/B测试
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 4%

---

# 配置 A/B 测试 {#configuring-a-b-testing}

本节详细介绍如何构建工作流以执行A/B测试。

1. 创建新工作流，然后配置 [查询](../../workflow/using/query.md) 活动以定向所需群体。

1. 添加 [Split](../../workflow/using/split.md) 活动，将目标群体划分为多个子集。

1. 打开活动，然后根据需要配置每个子集。 有关如何配置的详细信息 **[!UICONTROL Split]** 活动，请参阅 [本节](../../workflow/using/split.md).

   在本例中，我们希望通过向10%的目标群体展示新闻稿中的每一个，来测试2个新主题。

   ![](assets/ab-testing-split.png)

1. 添加过渡，以便向其余群体发送包含当前主题的新闻稿。 为此，请激活 **[!UICONTROL Generate complement]** 选项来自 **[!UICONTROL General]** 选项卡。

   ![](assets/ab-testing-complement.png)

1. 对于每个子集，添加要测试的投放版本。

   ![](assets/ab-testing-delivery.png)

您现在可以启动工作流。 发送投放后，您将能够在投放日志中跟踪三个子集的行为，以查看哪个主题最成功。

借助工作流，您还可以自动识别表现更好的投放变体，然后将其发送至剩余群体，从而自动执行流程。 有关更多信息，请参阅此专题 [用例](a-b-testing-use-case.md).
