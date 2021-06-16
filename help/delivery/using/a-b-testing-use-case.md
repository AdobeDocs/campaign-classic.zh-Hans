---
product: campaign
title: AB测试用例
description: 了解如何通过专用用例执行A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 895aa2fd4fa9c7c71c0073e9be33c12d4e92c9fa
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 6%

---

# 关于此用例 {#about-use-case}

在此用例中，我们将通过定位工作流比较两个电子邮件投放内容。 消息和文本在两个投放中都相同：只有布局发生更改。

目标群体分为三个：两个测试组和其余群体。 投放的不同版本会发送到每个测试组。

投放后，在收集最佳打开率的结果之前，将配置5天的等待期。 分数最高的投放内容随后由脚本恢复并发送到未用作测试组的群体。

请注意，将决定哪个投放最适合的标准可能会根据您的需求而进行更改。 可以是打开率、点进率、订阅率、反应性等。

此外，此用例中详细说明的测试仅与两个投放相关，但您可以根据需要测试任意数量的版本。 只需将活动添加到工作流即可。

执行此用例的主要步骤包括：

* [步骤1:创建定位工作流](../../delivery/using/a-b-testing-uc-targeting-workflow.md)
* [步骤2:配置群体样本](../../delivery/using/a-b-testing-uc-population-samples.md)
* [步骤3:创建两个投放模板](../../delivery/using/a-b-testing-uc-delivery-templates.md)
* [步骤4:在工作流中配置投放](../../delivery/using/a-b-testing-uc-configuring-deliveries.md)
* [步骤5:创建脚本](../../delivery/using/a-b-testing-uc-script.md)
* [步骤6:定义最终投放](../../delivery/using/a-b-testing-uc-final-delivery.md)
* [步骤7:启动工作流](../../delivery/using/a-b-testing-uc-start-workflow.md)
* [步骤8:分析结果](../../delivery/using/a-b-testing-uc-analyzing.md)

**相关主题：**

* [A/B 测试入门](../../delivery/using/get-started-a-b-testing.md)
* [配置 A/B 测试](../../delivery/using/configuring-a-b-testing.md)
