---
solution: Campaign Classic
product: campaign
title: 配置集成
description: 配置集成
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 1%

---


# 管道监控 {#pipeline-monitoring}

[!DNL pipelined]状态Web服务提供有关[!DNL pipelined]进程状态的信息。

它可以使用浏览器手动访问，也可以通过监视应用程序自动访问。

它采用REST格式，如下所述。

![](assets/triggers_8.png)

## 指示器{#indicators}

此部分列表状态Web服务中的指示器。

将突出显示建议要监视的指示器。

* 消费者：调用触发器的客户端的名称。 在管道选项中配置。
* http-request
   * last-alive-ms-ago:进行连接检查后的毫秒数。
   * last-failed-cnx-ms-ago:自上次连接检查失败以来的毫秒数。
   * pipeline-host:从中提取管线数据的主机的名称。
* 指针
   * 当前偏移：每个子线程中指针进入管线的值。
   * last-flush-ms-ago:自检索一批触发器以来的时间（以毫秒为单位）。
   * next offsets-flush:等到下一批完成时。
   * processed-sicn-last-flush:上一批处理的触发器数。
* 路由
   * 触发器：已检索触发器列表。 已在[!DNL pipelined]选项中配置。
* 统计
   * average-pointer-flush-time-ms:一批触发器的平均处理时间。
   * average-trigger-processing-time-ms:分析触发器数据所花的平均时间。
   * 字节读取：自进程启动以来从队列中读取的字节数。
   * current-messages:已从队列中提取并正在等待处理的挂起消息的当前数量。 **该指标应接近于零**。
   * 当前重试:当前处理失败并等待重试的消息数。
   * 峰值消息：进程自启动以来处理的挂起消息的最大数量。
   * 指针刷新：自开始以来处理的邮件批数。
   * 路由-JS-custom:自定义JS处理的邮件数。
   * trigger-addised:因处理错误而在过多重试后丢弃的消息数。
   * trigger-processed:未出现错误处理的邮件数。
   * 触发器接收：从队列接收的消息数。

这些统计数据按处理线程显示。

* average-trigger-processing-time-ms:分析触发器数据所花的平均时间。
* is-JS-processor:值“1”（如果此线程使用自定义JS）。
* trigger-addised:因处理错误而在过多重试后丢弃的消息数。 **该指标应为零**。
* 触发失败：JS中的处理错误数。 **该指标应为零**。
* 触发器接收：从队列接收的消息数。

* 设置：在配置文件中设置它们。
   * flush-pointer-msg-count:批处理中的消息数。
   * flush-pointer-period-ms:两批之间的时间（以毫秒为单位）。
   * processing-threads-JS:运行自定义JS的处理线程数。
   * retry-period-ms:出现处理错误时两个重试之间的时间。
   * retry-validity-duration-ms:从时间处理开始的持续时间将重试，直到消息被丢弃。
   * 管道消息报告

## 管道消息报告{#pipeline-report}

此报表显示过去五天内每小时的消息数。

![](assets/triggers_9.png)
