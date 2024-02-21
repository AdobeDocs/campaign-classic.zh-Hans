---
product: campaign
title: 关于流量控制活动
description: 关于流量控制活动
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows
exl-id: 3810cbd0-159c-4161-b568-1f61dcea0300
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 8%

---

# 工作流中的流量控制活动{#about-flow-control-activities}



以下活动是数据库活动：其主要任务是协调其他活动。

* **开始日期和结束日期**：用于显示工作流的开始点和结束点。 请参阅 [开始和结束](start-and-end.md).
* **分支**：用于激活所有叫客过渡。 请参阅 [分支](fork.md) 部分。
* **约会**：用于等待同时启动的多个任务完成后再继续。 请参阅 [分支](fork.md) 部分。
* **计划程序**：用于定义工作流执行计划。 请参阅 [计划程序](scheduler.md).
* **测试**：根据测试结果启用过渡。 请参阅 [测试](test.md).
* **等待**：在给定时间限制后启用叫客过渡。 请参阅 [等待](wait.md).
* **时间约束**：可让您暂停任务一段设定的时间。 请参阅 [时间约束](time-constraint.md).
* **子工作流**：用于执行其他工作流。 请参阅 [子工作流](sub-workflow.md).
* **跳转**：允许您实施不含链接的过渡。 请参阅 [跳转（起点和终点）](jump-start-point-and-end-point.md).
* **外部信号**：用于在接收外部信号后启用叫客过渡。 请参阅[外部信号](external-signal.md)一节。
* **批准**：用于向操作员或一组操作员发送电子邮件，并等待批准以继续执行。 请参阅 [批准](approval.md) 部分。
* **警报**：用于向操作员或操作员组发送警告。 请参阅 [警报](alert.md) 部分。
* **任务**：用于配置任务执行。 请参阅 [任务](task.md) 部分。
