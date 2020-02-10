---
title: 跟踪Web应用程序
seo-title: 跟踪Web应用程序
description: 跟踪Web应用程序
seo-description: null
page-status-flag: never-activated
uuid: c087b40c-fd14-440f-8f38-33f5f68120a9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 8e52f927-dadd-44c8-a51d-f717bc083eef
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# 跟踪Web应用程序{#tracking-a-web-application}

Adobe Campaign允许您通过插入跟踪标记来跟踪和衡量Web应用程序页面上的访问。 此功能可用于所有Web应用程序类型（表单、在线调查、使用DCE创建的网页等）。

因此，您可以定义多个导航路径并评估其成功与否。 然后，恢复的数据会显示在每个应用程序的报告中。

此版本中的主要改进如下：

* 可能在同一页面上插入多个跟踪标记以简化导航路径定义（例如，购买、订阅、退回等）。
* 在Web应用程序功能板中查看不同页面的导航路径和跟踪标记。

   ![](assets/trackers_1.png)

* 生成完整跟踪报告。

   ![](assets/trackers_5.png)

   主要指标如下：

   * **转化率**:显示导航路径所有步骤的人数。
   * **跳出率**:仅显示第一步的人数
   * **转换通道**:每个步骤之间的丢失率。
   此外，Sector类 **型图表** 会根据人口来源显示人口。

## 识别流量源 {#identifying-the-traffic-source}

可使用两种不同的模式来识别访客访问Web应用程序时的来源：

1. 发送特定交付以授予对Web应用程序页面的访问权：在这种情况下，交通来源就是这个交付，
1. 将Web应用程序与专用流量源关联：在这种情况下，它必须是外部“流量源”类型的交付。 可以从Web应用程序属性或目标映射中选择它。

   ![](assets/trackers_6.png)

为了在Web应用程序中识别流量源，Adobe Campaign会连续查找以下信息：

1. 源交付标识符（如果存在）(nlId cookie),
1. 在Web应用程序属性中定义的外部交付的标识符（如果存在）,
1. 目标映射中定义的外部交付的标识符（如果存在）。

>[!NOTE]
>
>请记住，只有在部署向导中激活了相应的选项，才能进行匿名跟踪。
>
>有关详细信息，请参阅安装 [指南](../../installation/using/deploying-an-instance.md)。

## 使用数字内容编辑器(DCE)设计的Web应用程序 {#web-applications-designed-with-digital-content-editor--dce-}

当使用HTML内容编辑器——数字内容编辑器( **Digital Content Editor, DCE)创建Web应用程序时** ，将从编辑器的选项卡 **[!UICONTROL Properties]** 中插入跟踪标记。 有关数字内容编辑器(DCE)的详细信息，请参阅 [本节](../../web/using/about-campaign-html-editor.md)。

![](assets/trackers_2.png)

使用Web界面时，必须从页面属性中插入跟踪标记。

![](assets/trackers_3.png)

通过 **[!UICONTROL Display blocks]** 该图标可以查看为页面定义的跟踪标记数。

![](assets/trackers_4.png)

