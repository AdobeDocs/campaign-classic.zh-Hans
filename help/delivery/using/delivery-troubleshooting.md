---
solution: Campaign Classic
product: campaign
title: 故障排除
description: 进一步了解投放性能以及如何解决与投放监控相关的问题。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: f3ba836bbb5a5f82d6a7868dcb15edc8e61b9a5b
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 1%

---


# 投放发送疑难解答{#delivery-troubleshooting}

本节列表了您在发送投放时可能遇到的常见问题，以及如何对这些问题进行疑难解答。

此外，请确保遵循本页[中详细介绍的最佳实践和清单，确保您的投放表现良好。](../../delivery/using/delivery-performances.md)

**相关主题：**

* [投放状态](../../delivery/using/delivery-statuses.md)
* [投放仪表板](../../delivery/using/delivery-dashboard.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)

## 慢投放{#slow-deliveries}

单击&#x200B;**[!UICONTROL Send]**&#x200B;按钮后，投放的时间似乎比往常长。 这可能由不同元素引起：

* 某些电子邮件提供商可能已将您的IP地址添加阻止列表到。 在这种情况下，请检查广播并查阅[此部分](../../delivery/using/about-deliverability.md)。

* 您的投放可能太大，无法快速处理，高JavaScript个性化可能会发生这种情况，或者如果您的投放重量超过60kbytes。 请参阅Adobe Campaign[投放最佳实践](../../delivery/using/delivery-best-practices.md)，了解内容指南。

* Adobe CampaignMTA中可能已发生限制。 这是由以下原因造成的：

   * 已暂停的消息（**[!UICONTROL quotas met]**&#x200B;消息）:已满足在活动中定义的声明性MX规则声明的配额。 有关此消息的详细信息，请参阅[此页](../../delivery/using/deliverability-faq.md)。 要进一步了解MX规则，请参阅[此页](../../delivery/using/technical-recommendations.md#mx-rules)。

   * 已暂停的消息（**[!UICONTROL dynamic flow control]**&#x200B;消息）:活动MTA在尝试为给定ISP发送消息时遇到错误，这会导致延迟以避免错误密度过大，从而面临潜在阻止列表。

* 系统问题可能会阻止服务器进行交互：这会减慢整个发送过程。 检查服务器，以确保在获取个性化数据的过程中不存在可能影响活动的内存或资源问题。

## 计划投放{#scheduled-deliveries-}

如果投放未在确切的预定日期执行，则可能与服务器时区之间的差异有关。 中间源实例和生产实例可以位于不同的时区。

例如，如果中间源实例在布里斯班时区，生产实例在达尔文时区，两个时区彼此相距半小时，那么在审计日志中，您会清楚地看到，如果投放在11:56预定生产，则中间预定的同一投放将在12:26，这有半小时的差别。

## 失败状态{#failed-status}

如果电子邮件投放的状态为&#x200B;**[!UICONTROL Failed]**，则可以将其链接到个性化块的问题。 例如，个性化块中的模式与投放映射不匹配时，投放会生成错误。

投放日志是了解投放失败原因的关键。 以下是您可以从投放日志中检测到的可能错误：

* 收件人消息失败，并出现“不可到达”错误，提示：

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   此问题的原因几乎始终是HTML中的个性化，试图调用尚未在上游定位或投放目标映射中定义或映射的表或字段。

   要更正此问题，需要检查工作流和投放内容，以明确确定尝试调用该表的个性化内容以及是否可以映射该表。 从此处，在HTML中删除对此表的调用或将映射修复到投放将成为解析路径。

* 在中间源部署模型中，投放日志中可能显示以下消息：

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   原因与性能问题有关。 这意味着在将数据发送到中间源服务器之前，营销实例花费了太多时间构建数据。

   为此，我们建议对数据库执行真空并重新索引。 有关数据库维护的详细信息，请参阅[本节](../../production/using/recommendations.md)。

   您还应使用计划工作流重新启动所有活动，以及所有处于失败状态的工作流。 请参阅[此章节](../../workflow/using/scheduler.md) 。

* 投放失败时，投放日志中可能显示以下错误：

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   通常，此错误意味着电子邮件中存在一个个性化字段或块，该字段或块具有多个收件人值。 正在使用个性化块，它正在为特定收件人获取多个记录。

   要解决此问题，请检查所使用的个性化目标，然后检查这些字段中有多个条目的收件人。 在投放活动之前，您还可以在定位工作流中使用&#x200B;**[!UICONTROL Deduplication]**&#x200B;活动，以检查每次只有一个个性化字段。 有关外部重复数据删除的详细信息，请参阅[此页](../../workflow/using/deduplication.md)。

* 某些投放可能失败，并显示“不可到达”错误：

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   这意味着投放成功，但Adobe Campaign收到了来自收件人的自动回复(例如，与“Auto_replies”入站电子邮件规则匹配的“Out off”回复)。

   Adobe Campaign会忽略自动回复电子邮件，收件人的地址不会发送给隔离。
