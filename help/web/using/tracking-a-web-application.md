---
solution: Campaign Classic
product: campaign
title: 跟踪 Web 应用程序
description: 跟踪 Web 应用程序
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 2%

---


# 跟踪 Web 应用程序{#tracking-a-web-application}

Adobe Campaign允许您通过插入跟踪标签来跟踪和衡量Web 应用程序页面上的访问。 此功能可用于所有Web 应用程序类型(表单、在线调查、使用数字内容编辑器创建的网页等)。

因此，您可以定义多个导航路径并评估其成功程度。 然后，恢复的数据会显示在每个应用程序的报告中。

此版本中的主要改进如下：

* 可能在同一页面上插入多个跟踪标签以简化导航路径定义(例如，购买、订阅、退货等)。
* 在Web 应用程序仪表板中查看不同页面的导航路径和跟踪标签。

   ![](assets/trackers_1.png)

* 生成完整跟踪报告。

   ![](assets/trackers_5.png)

   主要指标如下：

   * **转化率**:显示导航路径所有步骤的人数。
   * **跳出率**:仅显示第一步的人数
   * **转换漏斗**:每个步骤之间的丢失率。

   此外，Sector类 **型图** 则根据人口来源显示人口。

## 识别流量源 {#identifying-the-traffic-source}

两种不同的模式可用于识别访问访客时Web 应用程序的来源：

1. 发送特定投放以授予对Web 应用程序页面的访问权限：在这种情况下，交通来源是这个投放,
1. 将Web 应用程序关联到专用流量源：在这种情况下，它必须是外部“流量源”类型的投放。 它可以从Web 应用程序属性或目标映射中选择。

   ![](assets/trackers_6.png)

为了在Web 应用程序中识别流量源，Adobe Campaign会连续查找以下信息：

1. 源投放标识符（如果存在）(nlId cookie),
1. 在外部投放属性中定义的Web 应用程序的标识符（如果存在）,
1. 目标映射中定义的外部投放的标识符（如果存在）。

>[!NOTE]
>
>请记住，只有在部署向导中激活了相应的选项，才能进行匿名跟踪。
>
>For more on this, refer to the [Installation guide](../../installation/using/deploying-an-instance.md).

## Web 应用程序使用数字内容编辑器(数字内容编辑器) {#web-applications-designed-with-digital-content-editor--dce-}

当使用HTML内容编辑器创建Web 应用程序时- **数字内容编辑器(数字内容编辑器** )-从编辑器的选 **[!UICONTROL Properties]** 项卡中插入跟踪标签。 有关数字内容编辑器(数字内容编辑器)的详细信息，请参 [阅本节](../../web/using/about-campaign-html-editor.md)。

![](assets/trackers_2.png)

使用Web界面时，必须从页面属性中插入跟踪标签。

![](assets/trackers_3.png)

通过 **[!UICONTROL Display blocks]** 该图标，您可以视图为页面定义的跟踪标签数。

![](assets/trackers_4.png)

