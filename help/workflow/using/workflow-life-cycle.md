---
title: 工作流生命周期
description: 进一步了解工作流的生命周期。
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
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

例如，开始 **和投放****活动列出后** ，批准 **活动在下面的工作** 区闪烁。

![](assets/new-workflow-6.png)

这意味着前两个活动已成功执行，且正在进行批准，即它已创建但尚未完成。

在过渡 **后的投放** ,活动上方显示的字符 **574 -Ok** 表示投放准备针对574个收件人，并且操作已成功完成。 此信息在执行时添加到过渡，由处理数据的活动计算。

工作流已启动，正在等待属于“批准”活动中指定组 **的运** 算符作出决定。 将通知属于该组的运营商和具有电子邮件地址或移动电话号码的运营商。

操作员管理在本节中有 [详细介绍](../../platform/using/access-management.md)。

有关如何监控工作流的详细信息，请参 [阅本节](../../workflow/using/monitoring-workflow-execution.md)。
