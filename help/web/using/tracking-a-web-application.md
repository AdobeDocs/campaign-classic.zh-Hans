---
product: campaign
title: 跟踪 Web 应用程序访问
description: 跟踪 Web 应用程序访问
feature: Web Apps
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 4%

---

# 跟踪 Web 应用程序访问{#tracking-a-web-application}

![](../../assets/common.svg)

Adobe Campaign允许您通过插入跟踪标记来跟踪和测量Web应用程序页面上的访问量。 此功能可用于所有Web应用程序类型（表单、网页等）。

因此，您可以定义多个导航路径并评估其成功与否。 然后，恢复的数据将在每个应用程序的报告中提供。

此版本的主要改进如下：

* 可以在同一页面上插入多个跟踪标记，以便简化导航路径定义（例如，购买、订阅、回访等）。
* 在Web应用程序功能板中查看不同页面的导航路径和跟踪标记。

   ![](assets/trackers_1.png)

* 生成完整跟踪报告。

   ![](assets/trackers_5.png)

   主要指标如下：

   * **转化率**:显示导航路径所有步骤的人数。
   * **跳出率**:仅显示第一步的人数
   * **转化漏斗**:每个步骤之间的丢失率。

   此外， **部门** 类型图根据群体的来源显示群体。

## 识别流量源 {#identifying-the-traffic-source}

可使用两种不同的模式来识别访客访问Web应用程序时来自何处：

1. 发送特定投放以授予对Web应用程序页面的访问权限：在这种情况下，流量源是此投放，
1. 将Web应用程序关联到专用流量源：在这种情况下，它必须是外部“流量源”类型的投放。 可以从Web应用程序属性或目标映射中选择该属性。

   ![](assets/trackers_6.png)

为了识别Web应用程序中的流量源，Adobe Campaign先后查找以下信息：

1. 源交付标识符(如果存在(nlId cookie)),
1. Web应用程序属性中定义的外部投放的标识符（如果存在），
1. 目标映射中定义的外部投放的标识符（如果存在）。

>[!NOTE]
>
>仅当安装Campaign时部署向导中激活了选项时，才可使用匿名跟踪。

## 使用数字内容编辑器(DCE)设计的Web应用程序 {#web-applications-designed-with-digital-content-editor--dce-}

使用HTML内容编辑器创建Web应用程序时 —  **数字内容编辑器(DCE)**  — 从 **[!UICONTROL Properties]** 选项卡。 有关数字内容编辑器(DCE)的详细信息，请参阅 [此部分](about-campaign-html-editor.md).

![](assets/trackers_2.png)

使用Web界面时，必须从页面属性中插入跟踪标记。

![](assets/trackers_3.png)

的 **[!UICONTROL Display blocks]** 图标，可查看为页面定义的跟踪标记数。

![](assets/trackers_4.png)
