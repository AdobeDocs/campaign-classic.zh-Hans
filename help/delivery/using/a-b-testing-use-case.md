---
solution: Campaign Classic
product: campaign
title: 关于此用例
description: 了解如何通过专用用例执行A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# 关于此用例{#about-use-case}

在此用例中，我们将通过定位工作流来比较两个电子邮件投放内容。 消息和文本在两个投放中是相同的：只更改布局。

目标人口分为三个：两个测试组和剩余人口。 投放的不同版本将发送到每个测试组。

在投放之后，在收集最佳打开速率的结果之前配置5天的等待时间。 得分最高的投放的内容随后由脚本恢复，并发送给未用作测试组的人群。

请注意，将决定哪个投放最佳的标准可能会根据您的需要而更改。 可以是开放率、点击率、订阅率、反应性等。

此外，此用例中详细的测试仅与两个投放相关，但您可以根据需要测试任意多个版本。 只需向工作流中添加活动。

执行此用例的主要步骤有：

* [第1步：创建定位工作流](#step-1--creating-a-targeting-workflow)
* [第2步：配置填充样本](#step-2--configuring-population-samples)
* [第3步：创建两个投放模板](#step-3--creating-two-delivery-templates)
* [第4步：在工作流中配置投放](#step-4--configuring-the-deliveries-in-the-workflow)
* [第5步：创建脚本](#step-5--creating-the-script)
* [第7步：开始工作流](#step-7--starting-the-workflow)
* [第8步：分析结果](#step-8--analyzing-the-result)。

**相关主题：**

* [A/B测试入门](../../delivery/using/get-started-a-b-testing.md)
* [配置A/B测试](../../delivery/using/configuring-a-b-testing.md)
