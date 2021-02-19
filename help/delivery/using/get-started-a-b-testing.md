---
solution: Campaign Classic
product: campaign
title: A/B测试入门
description: 进一步了解Campaign Classic中的A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# 开始使用A/B测试{#get-started-a-b-testing}

A/B测试允许您比较投放的多个版本，以便确定哪个版本对目标群体的影响最大。

为此，您首先需要定义投放的多个变体。 然后，每个变体都被发送到人口样本，以确定哪个变量根据您选择的标准（打开、垃圾信息投诉、点击特定链接……）表现更好。

在以下示例中，投放目标已分为两个组，每个组占目标人口的50%。 每个组接收两个版本的投放，其中有两个不同的促销优惠。 在发送投放后，根据对促销优惠的点击次数得出变体A的性能更好的结论。

![](assets/a-b-testing-schema.png)

对于Campaign Classic,A/B测试是通过工作流实现的，在中，您可以指定要目标的群体以及将接收每个变体的组（请参阅[配置a/b测试](../../delivery/using/configuring-a-b-testing.md)）。

主要步骤是：

1. **定** 位所需人口。
1. **将填充** 拆分为子集，您将在其上测试投放的变体。

   例如，可以将投放的一个版本发送给目标人口的一小部分，将另一个版本发送给其余人口。 这允许您测试新版本的投放，而不是通常发送给客户的投放。 您还可以将目标人群分为3个组，以便向他们发送三个不同版本的投放。

1. **创建与** 每个子集对应的投放的多个版本。要测试的变体可以是主题、邮件内容、发件人姓名等。
1. 开始工作流，然后使用&#x200B;**投放日志**&#x200B;分析具有每个变体的子集的行为。

>[!NOTE]
>
>工作流还允许您通过自动识别性能更好的投放变体，然后将其发送到剩余人群，来自动处理流程。 有关详细信息，请参阅此专用[用例](../../delivery/using/a-b-testing-use-case.md)。
