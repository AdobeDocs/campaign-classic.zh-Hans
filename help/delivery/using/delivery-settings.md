---
product: campaign
title: 关于投放设置
description: 了解特定的v7交付设置
feature: Channel Configuration
role: User
hide: true
hidefromtoc: true
exl-id: 66250817-f829-4b8b-92dd-2daa92a97fe0
source-git-commit: d3d731c64cb5a430de6adac3aeb326f74134c436
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 12%

---

# 投放设置 {#about-delivery-settings}

以下设置特定于Campaign Classic。 有关其他投放设置，请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=zh-Hans){target="_blank"}。

## 投放分析 {#delivery-analysis}

### 提高投放分析性能 {#improving-delivery-analysis}

要加快投放准备速度，您可以在启动分析之前选中&#x200B;**[!UICONTROL Prepare the delivery parts in the database]**&#x200B;选项。

启用此选项后，将直接在数据库中执行投放准备，这可以显着加快分析。

目前，仅当满足以下条件时，此选项才可用：

* 投放必须是电子邮件。 目前不支持其他渠道。
* 您不得使用中间源或外部路由，只能使用批量投放路由类型。 您可以检查&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中使用的路由。
* 无法定位来自外部文件的群体。 对于单个投放，请单击&#x200B;**[!UICONTROL Email parameters]**&#x200B;中的&#x200B;**[!UICONTROL To]**&#x200B;链接，并检查是否选择了&#x200B;**[!UICONTROL Defined in the database]**&#x200B;选项。 对于工作流中使用的投放，检查&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡中的收件人是否为&#x200B;**[!UICONTROL Specified by the inbound event(s)]**。
* 您必须使用PostgreSQL数据库。

### 配置分析优先级 {#analysis-priority-}

如果投放属于营销活动，**[!UICONTROL Advanced]**&#x200B;选项卡会提供一个额外的选项。 这样，您就可以在同一营销活动中组织投放的处理顺序。

在发送之前，会分析每个投放。 分析持续时间取决于投放提取文件。 文件大小越大，分析所需的时间就越长，从而会等待以下投放。

**[!UICONTROL Message preparation by the scheduler]**&#x200B;的选项允许您在营销活动工作流中优先考虑投放分析。

![](assets/delivery_analysis_priority.png)

如果投放过大，最好为其分配较低的优先级，以避免减慢对其他工作流投放的分析。

>[!NOTE]
>
>为了确保较大的投放分析不会减慢工作流的进度，您可以通过勾选&#x200B;**[!UICONTROL Schedule execution for a time of low activity]**&#x200B;来计划其执行。

## 投放发送 {#delivery-sending}

### 配置重试 {#configuring-retries}

由于&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;错误而临时取消传递的邮件将会自动重试。 此[部分](understanding-delivery-failures.md#delivery-failure-types-and-reasons)中介绍了投放失败类型和原因。

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到[Enhanced MTA](sending-with-enhanced-mta.md)，Campaign将不再使用投放中的重试设置。 软退回重试次数以及它们之间的时间长度由Enhanced MTA根据从消息的电子邮件域返回的退回响应的类型和严重性确定。

对于使用旧版Campaign MTA的内部部署安装和托管/混合安装，投放参数&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡的中心部分指示在投放后一天应执行多少次重试，以及重试之间的最小延迟。

![](assets/s_ncs_user_wizard_retry_param.png)

默认情况下，安排在投放的第一天进行五次重试，最小间隔为一小时分布在一天中的24小时内。 每天进行一次重试的程序在此之后并一直到投放截止日期（在&#x200B;**[!UICONTROL Validity]**&#x200B;选项卡中定义）。 请参阅[定义有效期](#defining-validity-period)。

### 定义有效期 {#defining-validity-period}

启动投放后，可发送消息（以及任何重试），直到投放截止日期为止。 通过&#x200B;**[!UICONTROL Validity]**&#x200B;选项卡在投放属性中指示此情况。

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]**&#x200B;字段允许您输入全局投放重试限制。 这意味着，Adobe Campaign 从开始日期开始发送消息，然后对于仅返回错误的消息，将执行定期、可配置的重试，直至达到有效期限。

  您也可以选择指定日期。为此，请选择&#x200B;**[!UICONTROL Explicitly set validity dates]**。 在此情况下，也可以使用投放和有效期限日期指定时间。默认情况下使用当前时间，但您可以直接在输入字段中修改此项。

  >[!IMPORTANT]
  >
  >对于托管或混合安装，如果您已升级到[Enhanced MTA](sending-with-enhanced-mta.md)，则仅当设置为&#x200B;**3.5天或更短时间时**，才会使用Campaign电子邮件投放中的&#x200B;**[!UICONTROL Delivery duration]**&#x200B;设置。 如果定义的值超过3.5天，则不会将其考虑在内。

* **资源的有效性限制**： **[!UICONTROL Validity limit]**&#x200B;字段用于已上传的资源，主要用于镜像页面和图像。 本页上的资源仅在限制时间内有效（以节省磁盘空间）。

  此字段中的值可以用[此节](../../platform/using/adobe-campaign-workspace.md#default-units)中列出的单位表示。
