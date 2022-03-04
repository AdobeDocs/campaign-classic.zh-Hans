---
product: campaign
title: 投放发送疑难解答
description: 了解有关投放性能的更多信息以及如何对与投放监控相关的问题进行故障诊断
feature: Monitoring, Deliverability
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 1%

---

# 投放发送疑难解答 {#delivery-troubleshooting}

![](../../assets/common.svg)

本节列出了您在发送投放时可能遇到的常见问题，以及如何对其进行故障诊断。

此外，请确保遵循 [本页](delivery-performances.md) 以确保投放正常运行。

**相关主题：**

* [投放状态](delivery-statuses.md)
* [投放仪表板](delivery-dashboard.md)
* [了解投放失败](understanding-delivery-failures.md)

## 投放速度缓慢 {#slow-deliveries}

单击 **[!UICONTROL Send]** 按钮，您的投放似乎比平常花费的时间长。 这可能是由不同元素造成的：

* 某些电子邮件提供商可能已将您的IP地址添加到阻止列表。 在这种情况下，请检查您的广播并查阅 [此部分](about-deliverability.md).

* 您的投放可能太大，无法快速处理，在高度个性化的JavaScript中，或者如果投放的重量超过60k字节，可能会发生这种情况。 请参阅Adobe Campaign [投放最佳实践](delivery-best-practices.md) 以了解内容准则。

* 在Adobe Campaign MTA中可能已发生限制。 这是由以下原因造成的：

   * 已添加消息(**[!UICONTROL quotas met]** 消息):已满足在Campaign中定义的声明性MX规则声明的配额。 有关此消息的更多信息，请参阅 [本页](deliverability-faq.md). 要了解有关MX规则的更多信息，请参阅 [此部分](../../installation/using/email-deliverability.md#about-mx-rules).

   * 已添加消息(**[!UICONTROL dynamic flow control]** 消息):Campaign MTA在尝试为给定ISP发送消息时遇到错误，这会导致速度减慢，以避免错误密度过大，从而面临潜在阻止列表。

* 系统问题可能会阻止服务器一起交互：这会减慢整个发送过程。 例如，检查服务器以确保在获取个性化数据过程中不存在可能影响Campaign的内存或资源问题。

## 计划投放 {#scheduled-deliveries-}

如果不在确切的计划日期执行投放，则它可能与服务器时区之间的差异相关。 中间源实例和生产实例可以位于不同的时区。

例如，如果中间源实例位于布里斯班时区，生产实例位于达尔文时区，则两个时区彼此相距半小时，那么在审核日志中，您会清楚地看到，如果计划在11:56生产交付，则计划在中间交付的相同交付时间为12:26，其差异为半小时。

## 失败状态 {#failed-status}

如果电子邮件投放的状态为 **[!UICONTROL Failed]**，则可以将其链接到个性化块的问题。 例如，当架构与投放映射不匹配时，投放中的个性化块可能会生成错误。

投放日志是了解投放失败原因的关键。 以下是从投放日志中检测到的可能错误：

* 收件人消息失败，并出现“不可访问”错误，提示：

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   此问题的原因几乎总是HTML内的个性化，尝试调用尚未在上游定位或投放目标映射中定义或映射的表或字段。

   要更正此问题，需要对工作流和投放内容进行审核，以明确确定个性化尝试调用相关表的内容，以及是否可以映射表。 从此处，可以通过以下路径来解决：在HTML中删除对此表的调用，或者修复对投放的映射。

* 在中间源部署模型中，投放日志中会显示以下消息：

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   原因与性能问题有关。 这意味着营销实例在将数据发送到中间源服务器之前，在生成数据时花费了太多时间。

   为了解决此问题，我们建议对数据库执行真空和重新索引。 有关数据库维护的详细信息，请参阅 [此部分](../../production/using/recommendations.md).

   您还应使用计划活动重新启动所有工作流，以及所有处于失败状态的工作流。 请参阅[此小节](../../workflow/using/scheduler.md)。

* 投放失败时，投放日志中可能会显示以下错误：

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   通常，此错误表示电子邮件中有一个个性化字段或块，该字段或块的收件人具有多个值。 正在使用个性化块，它正在为特定收件人获取多个记录。

   要解决此问题，请检查使用的个性化数据，然后检查目标收件人的目标位置，这些收件人的任一字段具有多个条目。 您还可以使用 **[!UICONTROL Deduplication]** 投放活动之前的定位工作流中的活动，以检查一次只有一个个性化字段。 有关重复数据删除的更多信息，请参阅 [本页](../../workflow/using/deduplication.md).

* 某些投放可能会失败，并出现“不可访问”错误，提示：

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   这意味着投放成功，但Adobe Campaign收到了与“Auto_replies”入站电子邮件规则匹配的收件人的自动回复（例如“不在办公室”回复）。

   自动回复电子邮件会被Adobe Campaign忽略，并且收件人的地址不会被发送到隔离。
