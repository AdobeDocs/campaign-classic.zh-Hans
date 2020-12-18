---
solution: Campaign Classic
product: campaign
title: 工作流生命周期
description: 进一步了解工作流的生命周期
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---


# 工作流生命周期 {#workflow-life-cycle}

工作流周期有三个主要步骤。

* **正在编辑**

   这是初始设计阶段：创建新工作流时，其状态为“正在编辑”。 该工作流尚未由服务器处理，可以无风险修改。

* **开始**

   初始设计阶段完成后，可以启动工作流。 在此阶段，实例由服务器处理，并执行单个任务。 仍然可以使用某些预防措施修改工作流。

* **已完成**

   当不再有任何任务正在进行或操作符已明确停止实例时，工作流为“已完成”。

例如，**开始**&#x200B;和&#x200B;**投放**&#x200B;活动概述，而&#x200B;**批准**&#x200B;活动在下面的工作区闪烁。

![](assets/new-workflow-6.png)

这意味着前两个活动已成功执行，且正在进行批准，即它已创建但尚未完成。

在&#x200B;**投放**&#x200B;过渡后，在活动上方显示的字符&#x200B;**574 -Ok**&#x200B;表示投放准备目标为574个收件人，并且操作已成功完成。 此信息在执行时添加到过渡，由处理数据的活动计算。

工作流已启动，正在等待属于&#x200B;**Approval**&#x200B;活动中指定组的操作员作出决定。 将通知属于该组的运营商和具有电子邮件地址或移动电话号码的运营商。

操作员管理详见此[部分](../../platform/using/access-management.md)。

有关如何监视工作流的详细信息，请参阅[本节](../../workflow/using/monitoring-workflow-execution.md)。
