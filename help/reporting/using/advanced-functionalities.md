---
product: campaign
title: 高级功能
description: 了解有关使用报告时高级功能的更多信息
feature: Reporting, Monitoring
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 4%

---

# 高级功能{#advanced-functionalities}



作为技术用户，除了[常规属性](../../reporting/using/properties-of-the-report.md)之外，您还可以利用高级功能来配置报告，例如：

* 创建复杂查询以处理&#x200B;**脚本**&#x200B;活动中的数据。 [了解详情](#script-activity)

* 添加要在服务器或客户端上执行的外部脚本。 [了解详情](#external-script)

* 调用具有&#x200B;**跳转**&#x200B;活动的报告。 [了解详情](#calling-up-another-report)

* 为报表添加一个URL参数，使其更易于访问。 [了解详情](#calling-up-another-report)

* 添加要在报告上下文中使用的变量。 [了解详情](#adding-variables)

## 使用脚本 {#adding-a-script}

### 引用外部脚本 {#external-script}

您可以引用在调用报表页面时将在客户端和/或服务器端执行的JavaScript代码。

操作步骤：

1. 编辑[报告属性](../../reporting/using/properties-of-the-report.md)并单击&#x200B;**[!UICONTROL Scripts]**。
1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;并选择要引用的脚本。
1. 然后选择执行模式。

   如果添加多个脚本，请使用工具栏的箭头来定义其执行顺序。

   ![](assets/reporting_custom_js.png)

要在客户端正常执行，引用的脚本必须使用JavaScript编写，并且需要与常用浏览器兼容。 如需详细信息，请参阅[此小节](../../web/using/web-forms-answers.md)。

### 添加脚本活动 {#script-activity}

在[设计报表](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)时，请使用&#x200B;**[!UICONTROL Script]**&#x200B;活动来处理数据并轻松创建不启用SQL语言的复杂查询。 您可以在脚本窗口中直接输入查询。

**[!UICONTROL Texts]**&#x200B;选项卡允许您定义文本字符串。 然后可以使用以下语法： **$(Identifier)**。 有关使用文本的详细信息，请参阅[添加页眉和页脚](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

>[!CAUTION]
>
>我们不建议使用JavaScript代码创建聚合。

要创建报表历史记录，请将以下行添加到JavaScript查询中，以保存存档的数据：

```
if( ctx.@_historyId.toString().length == 0 )
```

否则，将只显示当前数据。

## 添加URL参数 {#defining-additional-settings}

[报告属性](../../reporting/using/properties-of-the-report.md)的&#x200B;**[!UICONTROL Parameters]**&#x200B;选项卡允许您为报告定义其他设置：这些设置将在调用期间传递到URL。

>[!CAUTION]
>
>出于安全原因，必须谨慎使用这些参数。

要创建新设置，请执行以下操作：

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并输入设置的名称。

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 如有必要，请指定是否强制使用该设置。

1. 选择要创建的设置的类型： **[!UICONTROL Filter]**&#x200B;或&#x200B;**[!UICONTROL Variable]**。

   **[!UICONTROL Filter entities]**&#x200B;选项允许您使用数据库的字段作为参数。

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   数据直接在实体级别恢复： **ctx/recipient/@account**。

   **[!UICONTROL Variable]**&#x200B;选项允许您创建或选择将作为URL参数传递的变量，该变量可用于过滤器。

通过&#x200B;**[!UICONTROL Response HTTP headers]**，您可以在使用iframe的HTML页面中包含报表页面时阻止点击劫持。 要避免点击劫持，可以选择&#x200B;**[!UICONTROL X-Frame-options header]**&#x200B;行为：

* **[!UICONTROL None]**：报告将没有&#x200B;**[!UICONTROL X-Frame-options header]**。
* **[!UICONTROL Same as origin]**：默认为新报告和重新发布的报告设置。 主机名将与报告的URL相同。
* **[!UICONTROL Deny]**：该报告不能包含在使用iframe的HTML页中。

![](assets/s_ncs_advuser_report_properties_09c.png)

## 添加变量 {#adding-variables}

**[!UICONTROL Variables]**&#x200B;选项卡包含报告中配置的变量列表。 这些变量将在报表的上下文中显示，并可用于计算。

单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以创建新变量。

要查看变量的定义，请选择该变量并单击&#x200B;**[!UICONTROL Detail...]**&#x200B;按钮。

![](assets/s_ncs_advuser_report_properties_10.png)

## 用例：在报表中使用变量和参数

在下面的视频示例中，您将了解如何添加“_type”参数，以根据此属性的值创建报告的不同视图。

<!--
![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&ref=helpx.adobe.com)-->


## 调用另一报表 {#calling-up-another-report}

**跳转**&#x200B;活动就像一个没有箭头的过渡：它允许您从一个活动转到另一个活动或访问另一个报告。
