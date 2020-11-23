---
solution: Campaign Classic
product: campaign
title: 高级功能
description: 高级功能
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 4%

---


# 高级功能{#advanced-functionalities}

作为技术用户，除了常规属 [性外](../../reporting/using/properties-of-the-report.md)，您还可以利用高级功能配置报表，例如：

* 创建复杂查询以在脚本活动 **中处理** 数据。 [了解详情](#script-activity)

* 添加要在服务器或客户端执行的外部脚本。 [了解详情](#external-script)

* 使用跳转活动调 **用报** 告。 [了解详情](#calling-up-another-report)

* 向报表添加URL参数，使其更易于访问。 [了解详情](#calling-up-another-report)

* 添加要在报表上下文中使用的变量。 [了解详情](#adding-variables)

## 使用脚本 {#adding-a-script}

### 引用外部脚本 {#external-script}

您可以引用将在调用报告页时在客户端和／或服务器端执行的JavaScript代码。

操作步骤：

1. 编辑报 [表属性](../../reporting/using/properties-of-the-report.md) ，然后单击 **[!UICONTROL Scripts]**。
1. 单 **[!UICONTROL Add]** 击并选择要引用的脚本。
1. 然后选择执行模式。

   如果添加多个脚本，请使用工具栏的箭头定义其执行顺序。

   ![](assets/reporting_custom_js.png)

要在客户端正常执行，引用的脚本必须用JavaScript编写，并且需要与通用浏览器兼容。 如需详细信息，请参阅[此部分](../../web/using/web-forms-answers.md)。

### 添加脚本活动 {#script-activity}

设 [计报表时](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)，使用该 **[!UICONTROL Script]** 活动处理数据并轻松创建不启用SQL语言的复杂查询。 您可以直接在脚本窗口中输入查询。

该选 **[!UICONTROL Texts]** 项卡允许您定义文本字符串。 然后，可以使用以下语法： **$（标识符）**。 有关使用文本的详细信息， [请参阅添加页眉和页脚](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

>[!CAUTION]
>
>我们不建议使用JavaScript代码创建聚合。

要创建报表的历史记录，请在JavaScript查询中添加以下代码行以保存存档数据：

```
if( ctx.@_historyId.toString().length == 0 )
```

否则，将仅显示当前数据。

## 添加URL参数 {#defining-additional-settings}

通过 **[!UICONTROL Parameters]** 报表属性的 [选项卡](../../reporting/using/properties-of-the-report.md) ，您可以为报表定义其他设置：这些设置将在调用期间传递到URL。

>[!CAUTION]
>
>出于安全原因，必须谨慎使用这些参数。

要创建新设置，请执行以下操作：

1. 单击按 **[!UICONTROL Add]** 钮并输入设置的名称。

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 如有必要，请指定设置是否为必需设置。

1. Select the type of setting you want to create: **[!UICONTROL Filter]** or **[!UICONTROL Variable]**.

   该 **[!UICONTROL Filter entities]** 选项允许您使用数据库的字段作为参数。

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   数据直接在实体级别恢复： **ctx/收件人/@account**。

   通过 **[!UICONTROL Variable]** 此选项，可创建或选择一个变量，该变量将作为URL的参数进行传递，并可用于过滤器。

使 **[!UICONTROL Response HTTP headers]** 用iframe将报表页面包含在HTML页面中时，可防止点击劫持。 要避免点击劫持，您可以选择 **[!UICONTROL X-Frame-options header]** 行为：

* **[!UICONTROL None]**:报告没有 **[!UICONTROL X-Frame-options header]**。
* **[!UICONTROL Same as origin]**:默认情况下，为新报表和重新发布的报表设置。 主机名与报告的URL相同。
* **[!UICONTROL Deny]**:无法使用iframe将报告包含在HTML页面中。

![](assets/s_ncs_advuser_report_properties_09c.png)

## 添加变量 {#adding-variables}

该选 **[!UICONTROL Variables]** 项卡包含在报表中配置的变量列表。 这些变量会在报表的上下文中显示，并可用于计算。

单击按 **[!UICONTROL Add]** 钮以创建新变量。

要视图变量的定义，请选择该变量，然后单击 **[!UICONTROL Detail...]** 按钮。

![](assets/s_ncs_advuser_report_properties_10.png)

## 用例：在报表中使用变量和参数

在以下视频示例中，您将学习如何添加“_type”参数，以根据此属性的值创建报表的不同视图。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## 调用另一个报告 {#calling-up-another-report}

跳 **跃活动** ，就像没有箭头的过渡:它允许您从一个活动转到另一个报表或访问另一个报表。
