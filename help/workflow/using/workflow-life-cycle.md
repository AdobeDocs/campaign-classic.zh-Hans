---
product: campaign
title: 工作流生命周期
description: 了解有关工作流生命周期的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: fceb5752-dc73-4386-8c18-c4f3e6110ca5
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---

# 工作流生命周期 {#workflow-life-cycle}



工作流周期有三个主要步骤。

* **正在编辑**

   这是初始设计阶段：创建新工作流时，其状态为“正在编辑”。 该工作流尚未由服务器处理，可以修改而不会产生风险。

* **已开始**

   完成初始设计阶段后，即可启动工作流。 在此阶段中，实例由服务器处理，各个任务将执行。 仍可以使用某些预防措施来修改工作流。

* **已完成**

   当没有任何正在进行的任务或操作员已明确停止实例时，工作流为“已完成”。

例如， **开始** 和 **投放** 活动概述，而 **批准** 活动在以下工作流中闪烁。

![](assets/new-workflow-6.png)

这意味着前两个活动已成功执行，并且正在审批，即已创建但尚未完成。

字符 **574 — 确定** 显示在过渡上方，紧跟在 **投放** 活动是指投放准备已针对574位收件人，并且操作已成功完成。 此信息在执行过渡时添加到过渡中，由处理数据的活动计算。

工作流已启动，正在等待属于中指定组的操作员 **批准** 用于做出决定的活动。 将通知属于该组的操作员以及拥有电子邮件地址或移动电话号码的操作员。

操作员管理详见此 [部分](../../platform/using/access-management.md).

有关如何监控工作流的更多信息，请参阅 [本节](monitoring-workflow-execution.md).
