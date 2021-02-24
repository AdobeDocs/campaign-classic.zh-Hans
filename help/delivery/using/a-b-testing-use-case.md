---
solution: Campaign Classic
product: campaign
title: 关于此用例
description: 了解如何通过专用的用例执行A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---


# 关于此用例{#about-use-case}

在此用例中，我们将通过定位工作流来比较两个电子邮件投放内容。 消息和文本在以下两个投放中都相同：只有布局会更改。

目标人口分为三类：两个测试组和剩余人口。 将向每个测试组发送不同版本的投放。

在投放后，在收集最佳打开速率的结果之前配置5天的等待时间。 得分最高的投放内容随后由脚本恢复并发送给未用作测试组的人群。

请注意，将决定哪种投放最佳的标准可能会根据您的需求而更改。 可以是开放率、点击率、订阅率、反应性等。

此外，此用例中详细介绍的测试仅与两个投放相关，但您可以根据需要测试任意多个版本。 只需向工作流中添加活动。

执行此用例的主要步骤有：

* [第1步：创建定位工作流](../../delivery/using/a-b-testing-uc-targeting-workflow.md)
* [第2步：配置填充样本](../../delivery/using/a-b-testing-uc-population-samples.md)
* [第3步：创建两个投放模板](../../delivery/using/a-b-testing-uc-delivery-templates.md)
* [第4步：在工作流中配置投放](../../delivery/using/a-b-testing-uc-configuring-deliveries.md)
* [第5步：创建脚本](../../delivery/using/a-b-testing-uc-script.md)
* [第6步：定义最终投放](../../delivery/using/a-b-testing-uc-final-delivery.md)
* [第7步：开始工作流](../../delivery/using/a-b-testing-uc-start-workflow.md)
* [第8步：分析结果](../../delivery/using/a-b-testing-uc-analyzing.md)

**相关主题：**

* [A/B测试入门](../../delivery/using/get-started-a-b-testing.md)
* [配置A/B测试](../../delivery/using/configuring-a-b-testing.md)
