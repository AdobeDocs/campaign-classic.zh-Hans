---
product: campaign
title: 工作流生命周期
description: 了解有关工作流生命周期的更多信息
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: fceb5752-dc73-4386-8c18-c4f3e6110ca5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# 工作流生命周期 {#workflow-life-cycle}

工作流周期有三个主要步骤。

* **正在编辑**

   这是初始设计阶段：创建新工作流后，其状态为“正在编辑”。 该工作流尚未由服务器处理，可以无风险修改。

* **开始**

   初始设计阶段完成后，可以启动工作流。 在此阶段中，实例由服务器处理，并执行各个任务。 仍可以使用某些预防措施修改工作流。

* **已完成**

   当不再有任何正在进行的任务，或者当运算符明确停止实例时，工作流即为“已完成”。

例如，列出了&#x200B;**Start**&#x200B;和&#x200B;**Delivery**&#x200B;活动，而&#x200B;**Approval**&#x200B;活动在下面的工作流中闪烁。

![](assets/new-workflow-6.png)

这意味着前两个活动已成功执行，且正在进行批准，即已创建但尚未完成。

在&#x200B;**投放**&#x200B;活动后的过渡上方显示的字符&#x200B;**574 -Ok**&#x200B;表示投放准备已定向574个收件人，并且操作已成功完成。 此信息会在执行过渡时添加到过渡中，由处理数据的活动计算。

工作流已启动，正在等待属于&#x200B;**Approval**&#x200B;活动中指定组的运算符作出决定。 属于该组的操作员以及具有电子邮件地址或手机号码的操作员会收到通知。

此[部分](../../platform/using/access-management.md)中详细描述了操作员管理。

有关如何监控工作流的更多信息，请参阅[此部分](../../workflow/using/monitoring-workflow-execution.md)。
