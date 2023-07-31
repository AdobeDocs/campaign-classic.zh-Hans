---
product: campaign
title: 高级功能
description: 了解有关使用报告时高级功能的更多信息
feature: Reporting, Monitoring
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 4%

---

# 高级功能{#advanced-functionalities}



作为技术用户，以及 [常规属性](../../reporting/using/properties-of-the-report.md)，您可以利用高级功能来配置报表，例如：

* 创建复杂查询以在 **脚本** 活动。 [了解详情](#script-activity)

* 添加要在服务器或客户端上执行的外部脚本。 [了解详情](#external-script)

* 调用具有的报表 **跳转** 活动。 [了解详情](#calling-up-another-report)

* 为报表添加一个URL参数，使其更易于访问。 [了解详情](#calling-up-another-report)

* 添加要在报告上下文中使用的变量。 [了解详情](#adding-variables)

## 使用脚本 {#adding-a-script}

### 引用外部脚本 {#external-script}

您可以引用调用报表页面时将在客户端和/或服务器端执行的JavaScript代码。

操作步骤：

1. 编辑 [报表属性](../../reporting/using/properties-of-the-report.md) 然后单击 **[!UICONTROL Scripts]**.
1. 单击 **[!UICONTROL Add]** 并选择要引用的脚本。
1. 然后选择执行模式。

   如果添加多个脚本，请使用工具栏的箭头来定义其执行顺序。

   ![](assets/reporting_custom_js.png)

要在客户端正常执行，引用的脚本必须使用JavaScript编写，并且需要与常用浏览器兼容。 如需详细信息，请参阅[此部分](../../web/using/web-forms-answers.md)。

### 添加脚本活动 {#script-activity}

时间 [设计报告](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)，使用 **[!UICONTROL Script]** 活动处理数据，并轻松创建不启用SQL语言的复杂查询。 您可以在脚本窗口中直接输入查询。

此 **[!UICONTROL Texts]** 制表符用于定义文本字符串。 然后可以使用以下语法： **$（标识符）**. 有关使用文本的详细信息，请参阅 [添加页眉和页脚](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>我们不建议使用JavaScript代码创建聚合。

要创建报表历史记录，请将以下行添加到JavaScript查询中，以保存存档的数据：

```
if( ctx.@_historyId.toString().length == 0 )
```

否则，将只显示当前数据。

## 添加URL参数 {#defining-additional-settings}

此 **[!UICONTROL Parameters]** 选项卡 [报表属性](../../reporting/using/properties-of-the-report.md) 可让您定义报表的其他设置：这些设置将在调用期间传递到URL中。

>[!CAUTION]
>
>出于安全原因，必须谨慎使用这些参数。

要创建新设置，请执行以下操作：

1. 单击 **[!UICONTROL Add]** 按钮并输入设置的名称。

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 如有必要，请指定是否强制使用该设置。

1. 选择要创建的设置类型： **[!UICONTROL Filter]** 或 **[!UICONTROL Variable]**.

   此 **[!UICONTROL Filter entities]** 选项允许您将数据库的字段用作参数。

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   数据直接在实体级别恢复： **ctx/recipient/@account**.

   此 **[!UICONTROL Variable]** 选项允许您创建或选择一个变量，该变量将作为URL的参数传递，并可在过滤器中使用。

此 **[!UICONTROL Response HTTP headers]** 可让您在使用iframe的HTML页面中包含报表页面时阻止点击劫持。 要避免点击劫持，您可以选择 **[!UICONTROL X-Frame-options header]** 行为：

* **[!UICONTROL None]**：报表将没有 **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**：默认为新报表和重新发布报表设置。 主机名将与报告的URL相同。
* **[!UICONTROL Deny]**：报表不能包含在使用iframe的HTML页面中。

![](assets/s_ncs_advuser_report_properties_09c.png)

## 添加变量 {#adding-variables}

此 **[!UICONTROL Variables]** 选项卡包含报告中配置的变量列表。 这些变量将在报表的上下文中显示，并可用于计算。

单击 **[!UICONTROL Add]** 按钮以创建新变量。

要查看变量的定义，请选择该变量并单击 **[!UICONTROL Detail...]** 按钮。

![](assets/s_ncs_advuser_report_properties_10.png)

## 用例：在报表中使用变量和参数

在下面的视频示例中，您将了解如何添加“_type”参数，以根据此属性的值创建报告的不同视图。

<!--
![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&ref=helpx.adobe.com)-->


## 调用另一报表 {#calling-up-another-report}

A **跳转** 活动就像一个没有箭头的过渡：通过它，您可以从一个活动转到另一个活动或访问其他报表。
