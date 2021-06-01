---
product: campaign
title: 其他配置
description: 了解如何在Adobe Campaign Classic中为事务型消息传递设置其他配置。
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
source-git-commit: e86350cf12db37e3f2c227563057b97922601729
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 7%

---

# 其他配置 {#mc-additional-configurations}

## 监测阈值 {#monitoring-thresholds}

您可以配置&#x200B;**消息中心服务级别**&#x200B;和&#x200B;**消息中心处理时间**&#x200B;报表中显示的指标的警告阈值（橙色）和警报阈值（红色）（请参阅[访问事务性消息报告](../../message-center/using/about-transactional-messaging-reports.md)）。

为此请执行以下操作步骤：

1. 在&#x200B;**执行实例**&#x200B;上打开部署向导。

1. 转到&#x200B;**[!UICONTROL Message Center]**&#x200B;页面。

1. 使用箭头更改阈值。

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>队列中待处理的事件数显示在Adobe Campaign进程监视页面的[系统指示器](../../production/using/monitoring-processes.md#system-indicators)部分中。 有关部署向导的详细信息，请参阅[此部分](../../installation/using/deploying-an-instance.md#deployment-wizard)。

## 清除事件 {#purging-events}

可以使用[部署向导](../../production/using/database-cleanup-workflow.md#deployment-wizard)配置数据在数据库中存储的时长。

事件清除由[数据库清理工作流](../../production/using/database-cleanup-workflow.md)自动执行。 此工作流会清除在执行实例上接收和存储的事件以及在控制实例上存档的事件。

根据需要使用箭头更改清除设置。

控制实例中的事件清除设置：

![](assets/messagecenter_delete_events_001.png)

执行实例中的事件清除设置：

![](assets/messagecenter_delete_events_002.png)

有关数据库清理工作流的更多信息，请参阅[此部分](../../production/using/database-cleanup-workflow.md)。


## 技术工作流 {#technical-workflows}

在部署任何事务型消息模板之前，必须确保确实已创建并启动了控制实例和不同执行实例的技术工作流。

在控制实例和执行实例之间，将划分与事务性消息传递（消息中心）相关的各种技术工作流。

### 控制实例工作流{#control-instance-workflows}

在控制实例上，无论您注册了一个还是多个执行实例，都必须为每个&#x200B;**[!UICONTROL Message Center execution instance]**&#x200B;外部帐户创建一个存档工作流。 单击&#x200B;**[!UICONTROL Create the archiving workflow]**&#x200B;按钮以创建并启动工作流。

![](assets/messagecenter_archiving_002.png)

然后，可从&#x200B;**Administration > Production > Message Center**&#x200B;文件夹访问这些工作流。 创建后，存档工作流将自动启动。

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### 执行实例工作流{#execution-instance-workflows}

在执行实例上，事务性消息传递的技术工作流可从&#x200B;**Administration > Production > Message Center**&#x200B;文件夹访问。 你只需要启动他们。 列表中的工作流包括：

* **[!UICONTROL Processing batch events]** (内部名称： **[!UICONTROL batchEventsProcessing]** ):利用此工作流，可在将批处理事件链接到消息模板之前，先在队列中对它们进行划分。
* **[!UICONTROL Processing real time events]** (内部名称： **[!UICONTROL rtEventsProcessing]** ):利用此工作流，可在将实时事件链接到消息模板之前，先对队列中的实时事件进行划分。
* **[!UICONTROL Update event status]** (内部名称： **[!UICONTROL updateEventStatus]** ):利用此工作流，可将状态归因到事件。

   以下事件状态可用：

   * **[!UICONTROL Pending]** :事件在队列中。尚未为其分配消息模板。
   * **[!UICONTROL Pending delivery]** :事件在队列中，已为其分配消息模板且投放正在处理该模板。
   * **[!UICONTROL Sent]** :此状态复制于投放日志。这意味着投放已发送。
   * **[!UICONTROL Ignored by the delivery]** :此状态复制于投放日志。这意味着该投放被忽略。
   * **[!UICONTROL Delivery failed]** :此状态复制于投放日志。这意味着投放失败了。
   * **[!UICONTROL Event not taken into account]** :该事件无法链接到消息模板。将不会处理该事件。

## 配置多品牌策略 {#configuring-multibranding}

本节介绍一个解决方案，用于在Adobe Campaign中为事务型消息配置每个品牌的跟踪和镜像页面URL。

### 先决条件 {#prerequisites}

* 必须将所有主机添加到实例的配置文件(`config-<instance>.xml`)。
* 必须为每个品牌分配一个子域。
* 如果在HTTPS页面上完成Web跟踪，则必须拥有适用于所有品牌的HTTPS证书。

要配置多品牌策略，您需要配置执行实例和控制实例。

### 执行实例{#execution-instance}

在执行实例上，执行以下步骤：

1. 为每个品牌创建一个外部帐户。

   >[!NOTE]
   >
   >了解如何在[此部分](../../message-center/using/configuring-instances.md#control-instance)中创建执行实例类型外部帐户。

1. 扩展nms:extAccount模式以添加跟踪URL:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >在[扩展架构](../../configuration/using/extending-a-schema.md)部分中了解如何扩展现有架构。

1. 修改nms:extAccount表单：

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. 修改NmsTracking_OpenFormula和NmsTracking_ClickFormula选项以使用外部帐户而不是全局选项。

   为此，请替换：

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   与：

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >升级时，这些更改可能会导致冲突。 您可能需要手动将这些公式与其新版本合并。

### 控制实例{#control-instance}

在控制实例上，您需要关联投放模板和外部帐户。

为此请执行以下操作步骤：

1. 使用与[执行实例](#execution-instance)中定义的相同内部名称为每个品牌创建一个外部帐户（步骤1）。

1. 为每个品牌创建一个默认投放模板。

   >[!NOTE]
   >
   >    了解如何在[此部分](../../delivery/using/creating-a-delivery-template.md#creating-a-new-template)中创建投放模板。

1. 在投放模板的&#x200B;**[!UICONTROL Properties]**&#x200B;中，设置到品牌外部帐户的路由。
