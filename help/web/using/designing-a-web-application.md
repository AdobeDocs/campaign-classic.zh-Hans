---
product: campaign
title: 设计 Web 应用程序
description: 设计 Web 应用程序
audience: web
content-type: reference
topic-tags: web-applications
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 3%

---

# 设计 Web 应用程序{#designing-a-web-application}

根据与[在线调查](../../web/using/about-surveys.md)相同的原则创建和管理Web应用程序。

但功能差异如下：

* Web应用程序不使用存档字段。 因此，数据只能存储在数据库字段或局部变量中。
* Web应用程序上没有内置报告。
* 还提供其他字段，主要用于创建表和图表。

>[!CAUTION]
>
>强烈建议持续检查所应用的配置，以便在Web应用程序构建过程中尽早检测到任何错误。 要检查修改的呈现，请保存应用程序，然后单击&#x200B;**[!UICONTROL Preview]**&#x200B;子选项卡。
>
>在发布Web应用程序之前，最终用户无法看到这些更改。

## 在Web应用程序{#inserting-charts-in-a-web-application}中插入图表

您可以在Web应用程序中包含图表。 要实现此目的，请使用任务栏中图表的下拉列表选择要插入的图表类型。

![](assets/s_ncs_admin_webapps_bar_graph.png)

您还可以选择&#x200B;**[!UICONTROL Add a chart]**&#x200B;菜单。

![](assets/s_ncs_admin_webapps_graph.png)

## 在Web应用程序{#inserting-tables-in-a-web-application}中插入表

要添加表，请使用任务栏中表的下拉列表选择要使用的表类型。

![](assets/s_ncs_admin_webapps_bar_table.png)

您还可以在下拉菜单中选择表的类型。

![](assets/s_ncs_admin_webapps_table.png)

## 概述类型的Web应用程序{#overview-type-web-applications}

Adobe Campaign界面使用许多Web应用程序来访问、管理收件人、投放、营销活动、库存等内容并与其进行交互。

在界面中，它们以功能板的形式显示，且仅包含一个页面。

现成的Web应用程序存储在&#x200B;**[!UICONTROL Administration > Configuration > Web applications]**&#x200B;节点中。

## 编辑表单类型Web应用程序{#edit-forms-type-web-applications}

外联网的编辑表单Web应用程序的特征是：

* 预加载框

   在大多数情况下，必须预加载要显示的数据。 由于访问这些表单的用户是经过识别的（通过访问控制），因此预加载不一定是加密的。

* 保存框
* 添加页面

   虽然“概述”类型的Web应用程序都只有一个页面，但编辑表单可以根据特定条件（测试、选择、连接运算符的配置文件等）提供一系列页面。

此类Web应用程序的操作与&#x200B;**调查**&#x200B;类似，但没有历史记录管理或字段存档。 用户通常通过登录页面访问该页面，在登录页面中，他们必须自己进行标识。
