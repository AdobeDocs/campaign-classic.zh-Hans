---
product: campaign
title: A/B 测试入门
description: 进一步了解Campaign Classic中的A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 3%

---

# A/B 测试入门 {#get-started-a-b-testing}

![](../../assets/common.svg)

A/B测试允许您比较一个投放的多个版本彼此的对比，以便确定哪个版本对目标群体的影响最大。

为此，您首先需要定义投放的多个变体。 然后，每个变体都会发送到群体样本，以根据您选择的标准（打开数、垃圾邮件投诉数、对特定链接的点击数……）确定哪个变体的效果更好。

在以下示例中，投放目标已拆分为两个组，每个组都占目标群体的50%。 每个组会收到包含两个不同促销优惠的两个版本的投放。 在发送投放后，根据促销优惠的点击次数得出的结论是，变体A的性能更好。

![](assets/a-b-testing-schema.png)

通过Campaign Classic,A/B测试通过工作流来实施，在工作流中，您可以指定要定向的群体以及接收每个变体的组（请参阅[配置a/b测试](configuring-a-b-testing.md)）。

主要步骤包括：

1. **** 定位所需的群体。
1. **将群** 体拆分为子集，您将在子集上测试投放的变体。

   例如，您可以向一小部分目标群体发送一个版本的投放，向其余群体发送另一个版本的投放。 这样，您就可以测试新版本的投放，而不是通常发送给客户的投放。 您还可以将目标群体划分为3个组，以便向其发送3个不同版本的投放。

1. **为每个** 子集对应的投放创建多个版本。要测试的变体可以是主题、消息内容、发件人名称等。
1. 启动工作流，然后使用&#x200B;**投放日志**&#x200B;分析每个变体的子集行为。

>[!NOTE]
>
>工作流还允许您通过自动识别性能更佳的投放变体，然后将其发送给其余群体，来自动执行您的流程。 有关更多信息，请参阅此专用[用例](a-b-testing-use-case.md)。
