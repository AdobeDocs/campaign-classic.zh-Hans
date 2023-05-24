---
product: campaign
title: 设计 Web 应用程序
description: 设计 Web 应用程序
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 4%

---

# 设计 Web 应用程序{#designing-a-web-application}



Web应用程序的创建和管理遵循与相同的原则 [Web窗体](about-web-forms.md).

>[!CAUTION]
>
>使用 **[!UICONTROL Preview]** 子选项卡，用于在Web应用程序设计期间检查错误。 请注意，用于预览Web应用程序的配置文件测试需要位于文件夹内， **[!UICONTROL Access rights]** 对于 **[!UICONTROL Web application agent]** 运算符。 </br>在发布Web应用程序之前，更改不会向最终用户公开。

## 在Web应用程序中插入图表 {#inserting-charts-in-a-web-application}

可以在Web应用程序中包含图表。 要执行此操作，请使用任务栏中的图表下拉列表选择要插入的图表类型。

![](assets/s_ncs_admin_webapps_bar_graph.png)

您也可以选择 **[!UICONTROL Add a chart]** 菜单。

![](assets/s_ncs_admin_webapps_graph.png)

## 在Web应用程序中插入表 {#inserting-tables-in-a-web-application}

要添加表，请使用任务栏中的表下拉列表选择要使用的表类型。

![](assets/s_ncs_admin_webapps_bar_table.png)

您还可以在下拉菜单中选择表类型。

![](assets/s_ncs_admin_webapps_table.png)

## 概述类型的Web应用程序 {#overview-type-web-applications}

Adobe Campaign界面使用许多Web应用程序来访问、管理收件人、投放、营销活动、库存等，并与之交互。

在界面中，它们以仅包含一个页面的功能板的形式显示。

现成的Web应用程序存储在 **[!UICONTROL Administration > Configuration > Web applications]** 节点。

## 编辑表单类型的Web应用程序 {#edit-forms-type-web-applications}

外联网的编辑表单Web应用程序的特点是：

* 预载盒

   在大多数情况下，必须预载要显示的数据。 由于访问这些表单的用户是经过识别的（通过访问控制），因此预加载不一定是加密的。

* 保存框
* 添加页面

   尽管“概述”类型的Web应用程序都有一个页面，但编辑表单可以根据特定条件（测试、选择、连接的运算符的配置文件等）提供一系列页面。

