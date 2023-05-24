---
product: campaign
title: A/B 测试入门
description: 详细了解Campaign中的A/B测试
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 3%

---

# A/B 测试入门 {#get-started-a-b-testing}



A/B测试允许您比较投放的多个版本，以确定哪个版本对目标群体产生最大的影响。

要实现此目的，您首先需要定义投放的多个变体。 然后，会将每个变体发送到群体样本，以确定哪个变体表现更好，具体取决于您选择的标准（打开、垃圾邮件投诉、点击特定链接……）。

在下面的示例中，投放目标已分成两组，每组代表目标人口的50%。 每个组会收到两个版本的投放以及两个不同的促销选件。 发送投放后，根据促销优惠的点击次数，可以推断出变体A的效果更好。

![](assets/a-b-testing-schema.png)

通过Campaign Classic，可通过工作流实施A/B测试，您可以在工作流中指定要定位的群体以及接收每个变体的组(请参阅 [配置a/b测试](configuring-a-b-testing.md))。

主要步骤包括：

1. **Target** 所需群体。
1. **拆分群体** 放入子集，您将在该子集上测试投放的变体。

   例如，您可以将投放的一个版本发送到目标群体的一小部分，而将另一个版本发送到其余群体。 这样，您就可以测试新版本的投放，而不是测试通常发送给客户的投放。 您还可以将目标群体分为3个组，以便向其发送投放的三个不同版本。

1. **创建多个版本** 与每个子集对应的投放的结束时间。 要测试的变体可以是主题、消息内容、发件人姓名等。
1. 启动工作流，然后使用 **投放日志** 分析每个变体的子集行为。

>[!NOTE]
>
>借助工作流，您还可以自动识别表现更好的投放变体，然后将其发送给其余群体，从而自动化您的流程。 有关更多信息，请参阅此专题 [用例](a-b-testing-use-case.md).
