---
product: campaign
title: 管理时区
description: 管理时区
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 4%

---

# 管理时区{#managing-time-zones}



Adobe Campaign允许您管理同一实例所涉及的不同国家/地区之间的时滞。 应用的配置是在实例创建期间配置的。

有关在Adobe Campaign中配置时区的详细信息，请参阅 [《Campaign Classicv7安装指南》](../../installation/using/time-zone-management.md).

在工作流中，您可以调整活动执行计划，并将特定时区链接到活动或整个工作流。 此配置在导入文件或投放计划框架内可能很有用。

## 执行计划 {#execution-scheduling}

您可以使用调度程序来调度任务的执行(请参阅 [调度程序](scheduler.md))。 您还可以使用提供此功能的活动中提供的计划选项。 这些活动提供 **[!UICONTROL Schedule]** 选项卡： **[!UICONTROL File collector]**， **[!UICONTROL File transfer]**， **[!UICONTROL Web download]**， **[!UICONTROL Email reception]** 和 **[!UICONTROL SMS]**&#x200B;等。

对于所有计划任务（即具有计划选项的所有活动），您可以选择要应用的时区。 时区是通过 **[!UICONTROL Advanced]** 相关活动的选项卡：

![](assets/wf-timezone-in-a-box.png)

可能的值包括：

* 服务器时区

   使用Adobe Campaign应用程序服务器的时区。

* 用户时区

   使用执行工作流的Adobe Campaign运算符的时区。

* 数据库时区

   使用所用数据库服务器的时区。

* 特定时区

   使用所选时区。

如果 **[!UICONTROL By default]** 值、应用工作流的时区或应用服务器的时区。

## 将时区链接到活动 {#linking-a-time-zone-to-an-activity}

此 **[!UICONTROL Advanced]** 通过工作流活动的选项卡，可选择其时区。 虽然在大多数情况下，工作流的时区就足够了，但可能需要为特定活动（例如数据导入）现在或反复地让时区过载以便将日期链接到其正确的时区。
