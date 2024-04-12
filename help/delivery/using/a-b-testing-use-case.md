---
product: campaign
title: AB测试用例
description: 了解如何通过专用用例执行A/B测试
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: A/B Testing
role: User
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 4%

---

# AB测试：A/B测试此用例 {#ab-testing-use-case}

在此使用案例中，我们将通过定位工作流比较两个电子邮件投放内容。 消息和文本在两种投放中都相同：只有布局发生变化。

目标群体分为三类：两个测试群体和其余群体。 向每个测试组发送投放的不同版本。

投放后，在收集最佳打开率结果之前会配置5天的等待期。 得分最高的投放内容随后由脚本恢复，并发送给未用作测试组的群体。

请注意，可以更改用于确定哪个投放是最佳投放的标准，以满足您的需求。 它可以是打开率、点进率、订阅率、反应性等。

此外，此用例中详述的测试仅与两个投放相关，但您可以测试所需数量的版本。 只需将活动添加到工作流即可。

执行此用例的主要步骤包括：

* [步骤1：创建定位工作流](a-b-testing-uc-targeting-workflow.md)
* [步骤2：配置群体示例](a-b-testing-uc-population-samples.md)
* [步骤3：创建两个投放模板](a-b-testing-uc-delivery-templates.md)
* [步骤4：在工作流中配置投放](a-b-testing-uc-configuring-deliveries.md)
* [步骤5：创建脚本](a-b-testing-uc-script.md)
* [步骤6：定义最终投放](a-b-testing-uc-final-delivery.md)
* [步骤7：启动工作流](a-b-testing-uc-start-workflow.md)
* [步骤8：分析结果](a-b-testing-uc-analyzing.md)

**相关主题：**

* [A/B 测试入门](get-started-a-b-testing.md)
* [配置 A/B 测试](configuring-a-b-testing.md)
