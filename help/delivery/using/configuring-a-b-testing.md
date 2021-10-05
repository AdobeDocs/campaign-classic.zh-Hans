---
product: campaign
title: 配置 A/B 测试
description: 了解如何在Campaign Classic中配置A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 3%

---

# 配置 A/B 测试 {#configuring-a-b-testing}

![](../../assets/common.svg)

本节详细介绍如何构建用于执行A/B测试的工作流。

1. 创建新工作流，然后配置[查询](../../workflow/using/query.md)活动以定位所需的群体。

1. 添加[Split](../../workflow/using/split.md)活动，将目标群体划分为多个子集。

1. 打开活动，然后根据需要配置每个子集。 有关如何配置&#x200B;**[!UICONTROL Split]**&#x200B;活动的更多信息，请参阅[此部分](../../workflow/using/split.md)。

   在本例中，我们希望通过将新闻稿的2个新主题分别展示给目标群体的10%来测试新闻稿的2个新主题。

   ![](assets/ab-testing-split.png)

1. 添加过渡，以便将包含当前主题的新闻稿发送给其余群体。 为此，请激活&#x200B;**[!UICONTROL General]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项。

   ![](assets/ab-testing-complement.png)

1. 对于每个子集，添加要测试的投放版本。

   ![](assets/ab-testing-delivery.png)

您现在可以启动工作流。 发送投放后，您将能够跟踪投放日志中三个子集的行为，以查看哪个主题最成功。

工作流还允许您通过自动识别性能更佳的投放变体，然后将其发送给其余群体，来自动执行您的流程。 有关更多信息，请参阅此专用[用例](a-b-testing-use-case.md)。
