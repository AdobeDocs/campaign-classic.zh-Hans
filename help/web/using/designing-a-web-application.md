---
product: campaign
title: 设计 Web 应用程序
description: 设计 Web 应用程序
audience: web
content-type: reference
topic-tags: web-applications
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 4%

---

# 设计 Web 应用程序{#designing-a-web-application}

![](../../assets/common.svg)

Web应用程序是按照与 [Web窗体](about-web-forms.md).

>[!CAUTION]
>
>使用 **[!UICONTROL Preview]** 子选项卡，以检查web应用程序设计期间的错误。
>
>在Web应用程序发布之前，更改不会向最终用户显示。

## 在Web应用程序中插入图表 {#inserting-charts-in-a-web-application}

您可以在Web应用程序中包含图表。 要实现此目的，请使用任务栏中图表的下拉列表选择要插入的图表类型。

![](assets/s_ncs_admin_webapps_bar_graph.png)

您还可以选择 **[!UICONTROL Add a chart]** 菜单。

![](assets/s_ncs_admin_webapps_graph.png)

## 在Web应用程序中插入表 {#inserting-tables-in-a-web-application}

要添加表，请使用任务栏中表的下拉列表选择要使用的表类型。

![](assets/s_ncs_admin_webapps_bar_table.png)

您还可以在下拉菜单中选择表的类型。

![](assets/s_ncs_admin_webapps_table.png)

## 概述类型的Web应用程序 {#overview-type-web-applications}

Adobe Campaign界面使用许多Web应用程序来访问、管理收件人、投放、营销活动、库存等内容并与之进行交互。

在界面中，它们以功能板的形式显示，且仅包含一个页面。

现成的Web应用程序存储在 **[!UICONTROL Administration > Configuration > Web applications]** 节点。

## 编辑表单类型的Web应用程序 {#edit-forms-type-web-applications}

外联网的编辑表单Web应用程序的特征是：

* 预加载框

   在大多数情况下，必须预加载要显示的数据。 由于访问这些表单的用户是经过识别的（通过访问控制），因此预加载不一定是加密的。

* 保存框
* 添加页面

   虽然“概述”类型的Web应用程序都只有一个页面，但编辑表单可以根据特定条件（测试、选择、连接运算符的配置文件等）提供一系列页面。

