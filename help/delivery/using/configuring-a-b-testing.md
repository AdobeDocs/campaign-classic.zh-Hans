---
solution: Campaign Classic
product: campaign
title: 配置A/B测试
description: 了解如何在Campaign Classic中配置A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 1330d4658d039f27a98535bf9885bffbfa0be3c9
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# 配置A/B测试{#configuring-a-b-testing}

本节详细介绍如何构建执行A/B测试的工作流。

1. 创建新工作流，然后配置[查询](../../workflow/using/query.md)活动以目标所需的人口。

1. 添加[Split](../../workflow/using/split.md)活动，将目标人群分为多个子集。

1. 打开活动，然后根据您的需求配置每个子集。 有关如何配置&#x200B;**[!UICONTROL Split]**&#x200B;活动的详细信息，请参阅此部分。

   在此示例中，我们要测试新闻稿的两个新主题，将每个主题呈现给目标人口的10%。

   ![](assets/ab-testing-split.png)

1. 添加过渡，以便将包含当前主题的新闻稿发送给剩余人群。 为此，请从&#x200B;**[!UICONTROL General]**&#x200B;选项卡中激活&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项。

   ![](assets/ab-testing-complement.png)

1. 对于每个子集，添加要测试的投放版本。

   ![](assets/ab-testing-delivery.png)

您现在可以开始工作流。 发送投放后，您将能够跟踪投放日志中三个子集的行为，以便查看哪个主题最成功。

工作流还允许您通过自动识别性能更好的投放变体，然后将其发送到剩余人群，从而自动处理流程。 有关详细信息，请参阅此专用[用例](../../delivery/using/a-b-testing-use-case.md)。
