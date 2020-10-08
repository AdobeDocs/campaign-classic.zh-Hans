---
title: 配置集成
seo-title: 配置集成
description: 配置集成
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 2%

---


# 管道监控 {#pipeline-monitoring}

状 [!DNL pipelined] 态Web服务提供有关进程状态的 [!DNL pipelined] 信息。

它可以使用浏览器手动访问，也可以通过监视应用程序自动访问。

它采用REST格式，如下所述。

![](assets/triggers_8.png)

## 指标 {#indicators}

此部分列表状态Web服务中的指示器。

高亮显示建议的监视指示器。

* 消费者：调用触发器的客户端的名称。 在管道选项中配置。
* http-request
   * last-alive-ms-ago:进行连接检查后的毫秒数。
   * last-failed-cnx-ms-ago:自上次连接检查失败以来的毫秒数。
   * pipeline-host:从中提取管线数据的主机的名称。
* 指针
   * 当前偏移：指针进入管道的值，每个子线程。
   * last flush-ms-ago:检索一批触发器后的时间（以毫秒为单位）。
   * next offsets-flush:等到下一批完成时。
   * processed-since-last-flush:上一批处理的触发器数。
* 路由
   * 触发器：已检索触发器列表。 在选项中 [!DNL pipelined] 配置。
* 统计
   * average-pointer-flush-time-ms:一批触发器的平均处理时间。
   * average-trigger-processing-time-ms:分析触发器数据所用的平均时间。
   * bytes-read:从队列中读取的字节数。
   * current-messages:已从队列中提取并正在等待处理的挂起消息的当前数量。 **此指示器应接近零**。
   * 当前重试:当前处理失败并正在等待重试的消息数。
   * 峰值消息：进程自启动以来一直处理的挂起消息的最大数量。
   * 指针刷新：自开始后处理的邮件批数。
   * 路由-JS-custom:自定义JS处理的邮件数。
   * 触发器丢弃：由于处理错误而在过多重试后丢弃的消息数。
   * trigger-processed:未出错的消息数。
   * 触发器接收：从队列接收的消息数。

这些统计数据按处理线程显示。

* average-trigger-processing-time-ms:分析触发器数据所用的平均时间。
* is-JS-processor:值“1”。
* 触发器丢弃：由于处理错误而在过多重试后丢弃的消息数。 **此指标应为零**。
* 触发失败：JS中的处理错误数。 **此指标应为零**。
* 触发器接收：从队列接收的消息数。

* 设置：它们在配置文件中设置。
   * flush-pointer-msg-count:批处理中的消息数。
   * flush-pointer-period-ms:两批之间的时间（以毫秒为单位）。
   * processing-threads-JS:运行自定义JS的处理线程数。
   * retry-period-ms:处理错误时两重试之间的时间。
   * retry-validity-duration-ms:从时间处理开始的持续时间将重试，直到消息被丢弃。
   * 管道消息报告

## 管道消息报告 {#pipeline-report}

此报告显示过去五天内每小时的消息数。

![](assets/triggers_9.png)
