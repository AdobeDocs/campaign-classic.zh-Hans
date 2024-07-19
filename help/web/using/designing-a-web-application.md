---
product: campaign
title: 设计 Web 应用程序
description: 设计 Web 应用程序
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 4%

---

# 设计 Web 应用程序{#designing-a-web-application}



根据与[Web窗体](about-web-forms.md)相同的原则创建和管理Web应用程序。

>[!CAUTION]
>
>使用&#x200B;**[!UICONTROL Preview]**&#x200B;子选项卡检查Web应用程序设计期间的错误。 请注意，用于预览Web应用程序的配置文件测试需要位于&#x200B;**[!UICONTROL Web application agent]**&#x200B;运算符中包含&#x200B;**[!UICONTROL Access rights]**&#x200B;的文件夹中。 </br>在发布Web应用程序之前，更改不会向最终用户公开。

## 在Web应用程序中插入图表 {#inserting-charts-in-a-web-application}

可以在Web应用程序中包含图表。 要执行此操作，请使用任务栏中的图表下拉列表选择要插入的图表类型。

![](assets/s_ncs_admin_webapps_bar_graph.png)

您还可以选择&#x200B;**[!UICONTROL Add a chart]**&#x200B;菜单。

![](assets/s_ncs_admin_webapps_graph.png)

## 在Web应用程序中插入表 {#inserting-tables-in-a-web-application}

要添加表，请使用任务栏中的表下拉列表选择要使用的表类型。

![](assets/s_ncs_admin_webapps_bar_table.png)

您还可以在下拉菜单中选择表类型。

![](assets/s_ncs_admin_webapps_table.png)

## 概览类型的Web应用程序 {#overview-type-web-applications}

Adobe Campaign界面使用许多Web应用程序来访问、管理收件人、投放、营销活动、库存等，并与之交互。

在界面中，它们以仅包含一个页面的功能板的形式显示。

现成的Web应用程序存储在&#x200B;**[!UICONTROL Administration > Configuration > Web applications]**&#x200B;节点中。

## 编辑表单类型的Web应用程序 {#edit-forms-type-web-applications}

外联网的编辑表单Web应用程序具有以下特征：

* 预载盒

  在大多数情况下，必须预加载要显示的数据。 由于访问这些表单的用户是经过识别的（通过访问控制），因此预加载不一定是加密的。

* 保存框
* 添加页面

  尽管“概述”类型的Web应用程序都具有单个页面，但编辑表单可以根据特定条件（测试、选择、连接的操作员的配置文件等）提供一系列页面。

