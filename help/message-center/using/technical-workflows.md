---
solution: Campaign Classic
product: campaign
title: 技术工作流
description: 技术工作流
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 11%

---


# 技术工作流{#technical-workflows}

在部署任何技术工作流之前，您必须确保控制实例和不同执行实例的事务性消息模板确实已创建并开始。

与事务消息（消息中心）相关的各种技术工作流在控制实例和执行实例之间被划分。

## 控制实例工作流 {#control-instance-workflows}

在控制实例上，无论您是注册了一个还是多个执行实例，都必须为每个外部帐户创建一个存档工作 **[!UICONTROL Message Center execution instance]** 流程。 单击按 **[!UICONTROL Create the archiving workflow]** 钮以创建和开始工作流。

![](assets/messagecenter_archiving_002.png)

然后，可以从“管理”>“生 **产”>“消息中心”文件夹访问** 这些工作流。 创建后，归档工作流将自动启动。

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

## 执行实例工作流 {#execution-instance-workflows}

在执行实例中，可以从“管理”>“生产”>“消息中心”文 **件夹访问事务消息传递的技术工作流** 。 你只需要开始他们。 列表中的工作流为：

* **[!UICONTROL Processing batch events]** (内部名称： **[!UICONTROL batchEventsProcessing]** ):通过此工作流，您可以先在队列中划分批次事件，然后再将其链接到消息模板。
* **[!UICONTROL Processing real time events]** (内部名称： **[!UICONTROL rtEventsProcessing]** ):通过此工作流，您可以先在队列中划分实时事件，然后再将其链接到消息模板。
* **[!UICONTROL Update event status]** (内部名称： **[!UICONTROL updateEventStatus]** ):通过此工作流，您可以将状态归为事件。

   以下事件状态可用：

   * **[!UICONTROL Pending]** :事件在队中。 尚未为其分配消息模板。
   * **[!UICONTROL Pending delivery]** :事件在队列中，已为其分配消息模板，投放正在处理该模板。
   * **[!UICONTROL Sent]** :此状态从投放日志复制。 这意味着投放已被发送。
   * **[!UICONTROL Ignored by the delivery]** :此状态从投放日志复制。 这意味着该投放被忽略。
   * **[!UICONTROL Delivery failed]** :此状态从投放日志复制。 这意味着投放失败了。
   * **[!UICONTROL Event not taken into account]** :事件无法链接到消息模板。 将不会处理该事件。

