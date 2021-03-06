---
product: campaign
title: 高级功能
description: 进一步了解使用报表时的高级功能
feature: Reporting
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 4%

---

# 高级功能{#advanced-functionalities}

![](../../assets/common.svg)

作为技术用户，除 [常规属性](../../reporting/using/properties-of-the-report.md)，则可以利用高级功能来配置报表，例如：

* 创建复杂查询以处理 **脚本** 活动。 [了解详情](#script-activity)

* 添加要在服务器或客户端上执行的外部脚本。 [了解详情](#external-script)

* 使用 **跳转** 活动。 [了解详情](#calling-up-another-report)

* 向报表中添加URL参数以使其更易访问。 [了解详情](#calling-up-another-report)

* 添加要在报表上下文中使用的变量。 [了解详情](#adding-variables)

## 使用脚本 {#adding-a-script}

### 引用外部脚本 {#external-script}

您可以引用将在调用报表页面时在客户端和/或服务器端执行的JavaScript代码。

操作步骤：

1. 编辑 [报表属性](../../reporting/using/properties-of-the-report.md) ，然后单击 **[!UICONTROL Scripts]**.
1. 单击 **[!UICONTROL Add]** ，然后选择要引用的脚本。
1. 然后选择执行模式。

   如果添加多个脚本，请使用工具栏的箭头定义其执行顺序。

   ![](assets/reporting_custom_js.png)

要在客户端正常执行，引用的脚本必须使用JavaScript编写，并且需要与常用浏览器兼容。 如需详细信息，请参阅[此部分](../../web/using/web-forms-answers.md)。

### 添加脚本活动 {#script-activity}

When [设计报表](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)，则使用 **[!UICONTROL Script]** 活动，用于处理数据并轻松创建不启用SQL语言的复杂查询。 您可以在脚本窗口中直接输入查询。

的 **[!UICONTROL Texts]** 选项卡，用于定义文本字符串。 然后，可以将它们与以下语法一起使用： **$（标识符）**. 有关使用文本的更多信息，请参阅 [添加页眉和页脚](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>我们不建议使用JavaScript代码创建聚合。

要创建报表的历史记录，请将以下行添加到JavaScript查询中，以保存已存档的数据：

```
if( ctx.@_historyId.toString().length == 0 )
```

否则，将仅显示当前数据。

## 添加URL参数 {#defining-additional-settings}

的 **[!UICONTROL Parameters]** 选项卡 [报表属性](../../reporting/using/properties-of-the-report.md) 允许您为报表定义其他设置：这些设置将在调用期间传递到URL。

>[!CAUTION]
>
>出于安全考虑，必须非常谨慎地使用这些参数。

要创建新设置，请执行以下操作：

1. 单击 **[!UICONTROL Add]** 按钮，然后输入设置的名称。

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 如有必要，请指定是否强制设置。

1. 选择要创建的设置类型： **[!UICONTROL Filter]** 或 **[!UICONTROL Variable]**.

   的 **[!UICONTROL Filter entities]** 选项允许您将数据库的字段用作参数。

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   数据将直接在实体级别恢复： **ctx/recipient/@account**.

   的 **[!UICONTROL Variable]** 选项，可创建或选择一个变量，该变量将作为URL的参数进行传递，并可在过滤器中使用。

的 **[!UICONTROL Response HTTP headers]** 允许在使用iframe将报表页面包含在HTML页面中时阻止点击劫持。 要避免点击劫持，您可以选择 **[!UICONTROL X-Frame-options header]** 行为：

* **[!UICONTROL None]**:报告没有 **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**:默认情况下，为新报表和重新发布的报表设置。 主机名与报表的URL相同。
* **[!UICONTROL Deny]**:使用iFrame的HTML页面中不能包含报表。

![](assets/s_ncs_advuser_report_properties_09c.png)

## 添加变量 {#adding-variables}

的 **[!UICONTROL Variables]** 选项卡包含报表中配置的变量列表。 这些变量在报表上下文中显示，并可用于计算。

单击 **[!UICONTROL Add]** 按钮以创建新变量。

要查看变量的定义，请选择该变量，然后单击 **[!UICONTROL Detail...]** 按钮。

![](assets/s_ncs_advuser_report_properties_10.png)

## 用例：在报表中使用变量和参数

在以下视频示例中，您将了解如何添加“_type”参数，以根据此属性的值创建报表的不同视图。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## 调用另一个报表 {#calling-up-another-report}

A **跳转** 活动就像一个没有箭头的过渡：它允许您从一个活动转到另一个活动或访问其他报表。
