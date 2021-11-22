---
product: campaign
title: 配置集成
description: 配置集成
audience: integrations
content-type: reference
exl-id: 84399496-33fd-4936-85e7-32de8503740f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 1%

---

# 管道监测 {#pipeline-monitoring}

![](../../assets/common.svg)

的 [!DNL pipelined] 状态web服务提供有关 [!DNL pipelined] 进程。

它可以使用浏览器手动访问，也可以通过监控应用程序自动访问。

它采用REST格式，如下所述。

![](assets/triggers_8.png)

## 指标 {#indicators}

此部分列出状态Web服务中的指示器。

突出显示了建议要监控的指标。

* 消费者：提取触发器的客户端名称。 在管道选项中配置。
* http-request
   * last-alive-ms-ago:进行连接检查后的时间（以毫秒为单位）。
   * last-failed-cnx-ms-ago:自上次连接检查失败后的时间（以毫秒为单位）。
   * pipeline-host:从中提取管道数据的主机的名称。
* 指针
   * 当前偏移：指针在管道中的值（每个子线程）。
   * lastflush-ms-ago:自检索到批量触发器以来的时间（以毫秒为单位）。
   * 下一偏移刷新：等待到下一批完成的时间。
   * processed-since-last-flush:上一批中处理的触发器数。
* 路由
   * 触发器：已检索触发器列表。 在 [!DNL pipelined] 选项。
* 统计资料
   * average-pointer-flush-time（平均指针刷新时间毫秒）：一批触发器的平均处理时间。
   * average-trigger-processing-time-ms:分析触发器数据所花费的平均时间。
   * 字节读取：从队列中读取的字节数。
   * 当前消息：当前从队列中提取并等待处理的待处理消息数。 **此指示器应接近零**.
   * current-retries:处理失败并等待重试的消息的当前数量。
   * 峰值消息：进程自启动以来已处理的最大待处理消息数。
   * 指针刷新：自开始以来已处理的邮件批数。
   * routing-JS-custom:自定义JS处理的消息数。
   * trigger-discared:因处理错误而在重试过多后丢弃的消息数。
   * trigger-processed:未出错的消息数。
   * 触发器接收：从队列接收的消息数。

这些统计资料按处理线程显示。

* average-trigger-processing-time-ms:分析触发器数据所花费的平均时间。
* is-JS-processor:值“1”。
* trigger-discared:因处理错误而在重试过多后丢弃的消息数。 **此指标应为零**.
* 触发器失败：JS中的处理错误数。 **此指标应为零**.
* 触发器接收：从队列接收的消息数。

* 设置：配置文件中会设置这些参数。
   * flush-pointer-msg-count:批量消息数。
   * flush-pointer-period-ms:两批之间的时间（以毫秒为单位）。
   * processing-threads-JS:运行自定义JS的处理线程数。
   * retry-period-ms:发生处理错误时两次重试之间的间隔时间。
   * retry-validity-duration-ms:从时间处理开始的持续时间重试，直到消息被丢弃。
   * 管道消息报表

## 管道消息报告 {#pipeline-report}

此报表显示过去五天内每小时的消息数。

![](assets/triggers_9.png)
