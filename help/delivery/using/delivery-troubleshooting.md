---
product: campaign
title: 投放发送疑难解答
description: 详细了解投放性能以及如何排查与投放监测相关的问题
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring, Deliverability
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 1%

---

# 投放发送疑难解答 {#delivery-troubleshooting}



此部分列出了发送投放时可能遇到的常见问题以及如何排除这些问题。

此外，请确保遵循中详述的最佳实践和核对清单 [此页面](delivery-performances.md) 以确保您的投放表现良好。

**相关主题：**

* [投放状态](delivery-statuses.md)
* [投放仪表板](delivery-dashboard.md)
* [了解投放失败](understanding-delivery-failures.md)

## 投放缓慢 {#slow-deliveries}

单击 **[!UICONTROL Send]** 按钮，您的投放时间似乎比平常长。 这可能是由于不同的元素造成的：

* 某些电子邮件提供商可能已将您的IP地址添加到阻止列表。 在这种情况下，请检查您的broadlog并查阅 [本节](about-deliverability.md).

* 您的投放可能因太大而无法快速处理，这种情况可能会出现在较高的JavaScript个性化设置中，或者您的投放重量超过60 KB时。 请参阅Adobe Campaign [投放最佳实践](delivery-best-practices.md) 以了解内容准则。

* Adobe Campaign MTA中可能已发生限制。 这是由以下原因造成的：

   * 挂起的消息(**[!UICONTROL quotas met]** message)：已满足Campaign中定义的声明MX规则声明的配额。 有关此消息的更多信息，请参阅 [此页面](deliverability-faq.md). 要了解有关MX规则的更多信息，请参阅 [本节](../../installation/using/email-deliverability.md#about-mx-rules).

   * 挂起的消息(**[!UICONTROL dynamic flow control]** message)：Campaign MTA在尝试为给定ISP投放消息时遇到错误，这会导致速度变慢以避免错误密度过大，从而面临潜在阻止列表。

* 系统问题可能会阻止服务器相互交互：这可能会减慢整个发送过程。 检查服务器以确保在获取个性化数据的过程中（例如），没有可能会影响Campaign的内存或资源问题。

## 计划的投放 {#scheduled-deliveries-}

如果投放未在确切的计划日期执行，则可能与服务器时区之间的差异有关。 中间源实例和生产实例可以位于不同的时区。

例如，如果中间源实例在布里斯班时区，而生产实例在达尔文时区，两个时区相隔半小时，则在审核日志中，您会清楚地看到，如果计划于11:56进行交付，则计划于mid进行的相同交付将为12:26，两者之间相差半小时。

## 失败状态 {#failed-status}

如果电子邮件投放的状态为 **[!UICONTROL Failed]**，它可以链接到个性化块的问题。 例如，当架构与投放映射不匹配时，投放中的个性化块可能会生成错误。

投放日志是了解投放失败原因的关键。 您可以从投放日志中检测以下可能的错误：

* 收件人消息失败，并出现“Unreachable”错误，指出：

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   此问题的原因几乎总是HTML内的个性化设置，该个性化设置试图调用尚未在上游定位或投放目标映射中定义或映射的表或字段。

   要更正此问题，需要审核工作流和投放内容，以明确决定尝试调用相关表的个性化设置以及该表是否可以映射。 从那里，在HTML中移除对此表的调用或修复到投放的映射将是解决问题的途径。

* 在中间源部署模型中，投放日志中可能会显示以下消息：

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   原因与性能问题相关。 这意味着营销实例在将数据发送到中间源服务器之前花费太多时间来构建数据。

   要解决此问题，我们建议对数据库执行真空和重新索引。 有关数据库维护的详细信息，请参见 [本节](../../production/using/recommendations.md).

   您还应该重新启动所有具有计划活动的工作流，以及所有处于失败状态的工作流。 请参阅[此小节](../../workflow/using/scheduler.md)。

* 投放失败时，投放日志中可能会显示以下错误：

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   通常，此错误意味着电子邮件中有一个个性化字段或块，该字段或块为收件人具有多个值。 正在使用个性化块，并且正在为特定收件人获取多个记录。

   要解决此问题，请检查使用的个性化数据，然后检查目标，以查找具有多个条目的收件人，以查找其中的任意字段。 您也可以使用 **[!UICONTROL Deduplication]** 活动之前，定向工作流中的活动，以检查一次只有一个个性化字段。 有关重复数据删除的更多信息，请参阅 [此页面](../../workflow/using/deduplication.md).

* 某些投放可能会失败，并出现“Unreachable”（无法访问）错误，并指出：

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   这意味着投放成功，但Adobe Campaign收到了来自收件人的与“Auto_replies”入站电子邮件规则匹配的自动回复（例如“不在办公室”回复）。

   自动回复电子邮件会被Adobe Campaign忽略，收件人的地址将不会被隔离。
