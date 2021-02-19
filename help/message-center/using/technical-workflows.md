---
solution: Campaign Classic
product: campaign
title: 技术工作流
description: 技术工作流
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: d1130691e40c0cac183db37a4c0b410d00bb696a
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 11%

---


# 技术工作流{#technical-workflows}

在部署任何技术工作流之前，您必须确保确实已创建和启动了控制实例和不同执行实例。

与事务性消息传递（消息中心）相关的各种技术工作流在控制实例和执行实例之间被划分。

## 控制实例工作流{#control-instance-workflows}

在控制实例中，无论您注册了一个还是多个执行实例，都必须为每个&#x200B;**[!UICONTROL Message Center execution instance]**&#x200B;外部帐户创建一个归档工作流。 单击&#x200B;**[!UICONTROL Create the archiving workflow]**&#x200B;按钮以创建和开始工作流。

![](assets/messagecenter_archiving_002.png)

然后，可以从&#x200B;**“管理”>“生产”>“消息中心”**&#x200B;文件夹访问这些工作流。 创建后，将自动启动存档工作流。

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

## 执行实例工作流{#execution-instance-workflows}

在执行实例中，可以从&#x200B;**“管理”>“生产”>“消息中心”**&#x200B;文件夹访问事务消息传递的技术工作流。 你只需要开始他们。 列表中的工作流有：

* **[!UICONTROL Processing batch events]** (内部名称： **[!UICONTROL batchEventsProcessing]** ):通过此工作流，您可以先划分队列中的批次事件，然后再将其链接到消息模板。
* **[!UICONTROL Processing real time events]** (内部名称： **[!UICONTROL rtEventsProcessing]** ):通过此工作流，您可以先划分队列中的实时事件，然后再将其链接到消息模板。
* **[!UICONTROL Update event status]** (内部名称： **[!UICONTROL updateEventStatus]** ):通过此工作流，您可以将状态归为事件。

   以下事件状态可用：

   * **[!UICONTROL Pending]** :事件在队列中。尚未为其分配消息模板。
   * **[!UICONTROL Pending delivery]** :事件在队列中，已为其分配了消息模板，投放正在处理该消息模板。
   * **[!UICONTROL Sent]** :此状态将从投放日志中复制。这意味着投放已发送。
   * **[!UICONTROL Ignored by the delivery]** :此状态将从投放日志中复制。这意味着该投放被忽略。
   * **[!UICONTROL Delivery failed]** :此状态将从投放日志中复制。这意味着投放失败了。
   * **[!UICONTROL Event not taken into account]** :事件无法链接到消息模板。将不会处理该事件。
