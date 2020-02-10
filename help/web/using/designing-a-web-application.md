---
title: 设计Web应用程序
seo-title: 设计Web应用程序
description: 设计Web应用程序
seo-description: null
page-status-flag: never-activated
uuid: 29c11154-f056-4047-849a-739ba0a2c615
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 08efa472-d090-404d-9ad7-47adb3489c30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 设计Web应用程序{#designing-a-web-application}

Web应用程序是根据与在线调查相同的原则创建和管 [理的](../../web/using/about-surveys.md)。

然而，功能差异如下：

* Web应用程序不使用存档的字段。 因此，数据只能存储在数据库字段或本地变量中。
* Web应用程序上没有内置的报告。
* 还提供其他字段，主要用于创建表和图表。

>[!CAUTION]
>
>强烈建议持续检查所应用的配置，以便在Web应用程序构建过程中及早发现任何错误。 要检查修改的呈现，请保存应用程序，然后单击 **[!UICONTROL Preview]** 子选项卡。
>
>在发布Web应用程序之前，最终用户无法看到这些更改。

## 在Web应用程序中插入图表 {#inserting-charts-in-a-web-application}

您可以在Web应用程序中包含图表。 为此，请使用任务栏中图表的下拉列表选择要插入的图表类型。

![](assets/s_ncs_admin_webapps_bar_graph.png)

您还可以选择菜 **[!UICONTROL Add a chart]** 单。

![](assets/s_ncs_admin_webapps_graph.png)

## 在Web应用程序中插入表 {#inserting-tables-in-a-web-application}

要添加表，请使用任务栏中的表下拉列表选择要使用的表类型。

![](assets/s_ncs_admin_webapps_bar_table.png)

您还可以在下拉菜单中选择表的类型。

![](assets/s_ncs_admin_webapps_table.png)

## 概述类型的Web应用程序 {#overview-type-web-applications}

Adobe Campaign界面使用许多Web应用程序访问、管理收件人、分发、营销活动、股票等并与之交互。

在界面中，只有一页面的仪表板形式显示它们。

现成的Web应用程序存储在节 **[!UICONTROL Administration > Configuration > Web applications]** 点中。

## 编辑表单类型的Web应用程序 {#edit-forms-type-web-applications}

编辑外部网的表单Web应用程序的特点是：

* 预加载框

   在大多数情况下，必须预先加载要显示的数据。 由于访问这些表单的用户是通过访问控制进行标识的，因此预载不一定是加密的。

* 保存框
* 添加页面

   “概述”类型的Web应用程序都有单个页面，而编辑表单可以根据特定条件（测试、选择、连接操作员的配置文件等）提供一系列页面。

此类Web应用程序的操作与 **Surveys相似**，但没有历史记录管理或现场存档。 用户通常通过登录页面访问它，在登录页面中必须标识自己。
