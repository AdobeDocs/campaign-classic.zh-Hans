---
product: campaign
title: 跟踪 Web 应用程序访问
description: 跟踪 Web 应用程序访问
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Web Apps, Reporting, Monitoring
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 4%

---

# 跟踪 Web 应用程序访问{#tracking-a-web-application}



Adobe Campaign允许您通过插入跟踪标记来跟踪和测量Web应用程序页面上的访问次数。 此功能可用于所有Web应用程序类型（表单、网页等）。

因此，您可以定义多个导航路径并评估其成功与否。 然后，恢复的数据便可在每个应用程序的报表中使用。

此版本中的主要改进如下：

* 可以在同一页面上插入多个跟踪标记，以便简化导航路径定义（例如购买、订阅、返回等）。
* 在Web应用程序仪表板中查看不同页面的导航路径和跟踪标记。

  ![](assets/trackers_1.png)

* 生成完整的跟踪报表。

  ![](assets/trackers_5.png)

  主要指标如下：

   * **转化率**：显示导航路径所有步骤的人数。
   * **跳出率**：仅显示第一步的人数
   * **转化漏斗**：每一步之间的丢失率。

  此外，**扇区**&#x200B;类型图表根据源显示群体。

## 识别流量源 {#identifying-the-traffic-source}

在访问Web应用程序时，可以使用两种不同的模式来识别访客的来源：

1. 发送特定投放以授予对Web应用程序页面的访问权限：在这种情况下，流量源为此投放，
1. 将Web应用程序关联到专用流量源：在这种情况下，它必须是外部“流量源”类型的投放。 可以从Web应用程序属性或目标映射中选择它。

   ![](assets/trackers_6.png)

为了识别Web应用程序中的流量源，Adobe Campaign会依次查找以下信息：

1. 源投放标识符（如果存在）(nlId Cookie)，
1. Web应用程序属性中定义的外部投放的标识符（如果存在），
1. 目标映射中定义的外部投放的标识符（如果存在）。

>[!NOTE]
>
>只有在安装Campaign时已在部署向导中激活该选项的情况下，匿名跟踪才可用。

## 使用数字内容编辑器(DCE)设计的Web应用程序 {#web-applications-designed-with-digital-content-editor--dce-}

使用HTML内容编辑器 — **数字内容编辑器(DCE)**&#x200B;创建Web应用程序时 — 将从编辑器的&#x200B;**[!UICONTROL Properties]**&#x200B;选项卡插入跟踪标记。 有关数字内容编辑器(DCE)的详细信息，请参阅[此部分](about-campaign-html-editor.md)。

![](assets/trackers_2.png)

使用Web界面时，必须从页面属性插入跟踪标记。

![](assets/trackers_3.png)

通过&#x200B;**[!UICONTROL Display blocks]**&#x200B;图标，可查看为页面定义的跟踪标记数量。

![](assets/trackers_4.png)
