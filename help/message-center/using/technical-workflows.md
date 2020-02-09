---
title: 技术工作流
seo-title: 技术工作流
description: 技术工作流
seo-description: null
page-status-flag: never-activated
uuid: dfd1b180-86b5-4740-9bad-a0e210f433c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2e648e63-06d2-4e8f-9934-066a41d18eac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 技术工作流{#technical-workflows}

在部署任何事务性消息模板之前，您必须确保确实已创建并启动了控件实例和不同执行实例上的技术工作流。

与事务消息（消息中心）相关的各种技术工作流在控制实例和执行实例之间被划分。

## 控制实例工作流 {#control-instance-workflows}

在控件实例上，必须为每个执行实例创建一个存档工作流。 然后，可以从“管理”>“生产”>“消息中 **心”文件夹访问存档工作流** 。 创建后，归档工作流程将自动启动。

**分布式架构**

如果您注册了一个或多个执行实例，则必须在控件实例上为每个外部帐户创建一个存档 **[!UICONTROL Message Center execution instance]** 工作流。 单击按 **[!UICONTROL Create the archiving workflow]** 钮以创建并启动工作流。

![](assets/messagecenter_archiving_002.png)

**最小架构**

将控件和执行模块安装到同一实例上后，您必须使用部署向导创建存档工作流。 单击按 **[!UICONTROL Create the archiving workflow]** 钮以创建并启动工作流。

![](assets/messagecenter_archiving_001.png)

## 执行实例工作流 {#execution-instance-workflows}

在执行实例上，可以从“管理”>“生产”>“消息中心”文件夹访问事务 **消息传递的技术工作流** 。 你只需要启动它们。 列表中的工作流包括：

* **[!UICONTROL Processing batch events]** (内部名称： **[!UICONTROL batchEventsProcessing]** ):通过此工作流，您可以在将队列中的批处理事件链接到消息模板之前，先在队列中对这些事件进行细分。
* **[!UICONTROL Processing real time events]** (内部名称： **[!UICONTROL rtEventsProcessing]** ):通过此工作流，您可以在将队列中的实时事件链接到消息模板之前，先在队列中分类这些事件。
* **[!UICONTROL Update event status]** (内部名称： **[!UICONTROL updateEventStatus]** ):通过此工作流，您可以将状态归因到活动。

   以下活动状态可用：

   * **[!UICONTROL Pending]** :该事件在队列中。 尚未为其分配消息模板。
   * **[!UICONTROL Pending delivery]** :该事件在队列中，已为其分配消息模板，并且正在由分发处理该消息模板。
   * **[!UICONTROL Sent]** :此状态将从交付日志中复制。 这意味着送货已经送出。
   * **[!UICONTROL Ignored by the delivery]** :此状态将从交付日志中复制。 这意味着交付被忽略。
   * **[!UICONTROL Delivery failed]** :此状态将从交付日志中复制。 这意味着交付失败。
   * **[!UICONTROL Event not taken into account]** :无法将活动链接到消息模板。 不会处理该事件。

