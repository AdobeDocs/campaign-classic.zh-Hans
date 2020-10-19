---
title: 报告的属性
description: 进一步了解报告属性设置
page-status-flag: never-activated
uuid: 56163f53-d115-45b8-94a5-c173ac4c6533
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 5ec88743-be51-438c-9064-dd0196fdd7d3
translation-type: tm+mt
source-git-commit: b0b9a0714075474bf52c3eed78d45bcef25b44fc
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 2%

---


# 报告的属性{#properties-of-the-report}

您可以完全个性化和配置报告，以满足您的需求。 为此，请编辑其属性。 报表属性通过活动顺 **[!UICONTROL Properties]** 序图表上方的按钮访问。

![](assets/s_ncs_advuser_report_properties_01.png)

常规属性如下所述。 本节介绍在中配 **[!UICONTROL Parameters]**&#x200B;置的 **[!UICONTROL Variables]** 高级 **[!UICONTROL Scripts]** 功能 [，以](../../reporting/using/advanced-functionalities.md)及选项卡。

## 常规属性 {#overall-properties}

在报表 **[!UICONTROL General]** 属性的选项卡中，您可以编辑以下列出的设置：

* 报表的标签和内部名称。 报 **[!UICONTROL Internal name]** 表最终URL中使用。 在创建报告后不应更改它。

* 在创建报 **表时** ，将选择报表文件夹。 最佳实践是为自定义报表创建专用文件夹，使其不与内置 [报表混合](../../reporting/using/about-campaign-built-in-reports.md)。

* 创 **建报** 告时，将选择存储。 要更改报表的数据表，请单 **[!UICONTROL Select link]** 击字段右侧的图 **[!UICONTROL Document type]** 标。

   ![](assets/s_ncs_advuser_report_properties_02.png)

* 访问控制 **参数** 。 这些设置如下所述。

## Controlling access to the report {#report-accessibility}

报表可在Adobe Campaign控制台中或通过Web浏览器访问。 在这种情况下，可以需要配置报告访问控制，如下所示。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的选项包括：

* **[!UICONTROL Anonymous access]**:此选项允许不受限制地访问报告。 但是，不可能进行任何操纵。

   “webapp”技术运营商的权限用于显示报告元素。 在本节 [中了解更多](../../platform/using/access-management.md#default-operators)。

* **[!UICONTROL Access control]**:此选项允许Adobe Campaign操作符在登录后访问它。
* **[!UICONTROL Specific account]**:通过此选项，可以在字段中选择操作员的权限后执行报 **[!UICONTROL Operator]** 告。

## 管理报告本地化 {#managing-report-localization}

您可以配置要将报表翻译为的语言。 为此，请单击选 **[!UICONTROL Localization]** 项卡。

![](assets/s_ncs_advuser_report_properties_06.png)

编辑语言是您编写的语言。 添加语言时，报表编辑页面中将显示子选项卡。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>有关活动中网页本地化的详细信息，请参 [阅此部分](../../web/using/translating-a-web-form.md)。

## 个性化HTML渲染 {#personalizing-html-rendering}

在选项卡 **[!UICONTROL Rendering]** 中，您可以个性化页面的数据显示模式。 您可以选择：

* 图表渲染引擎：Adobe Campaign优惠两种不同的模式来生成图表渲染。 默认情况下，渲染引擎为HTML 5。 如有必要，可以选择Flash渲染。
* 报告中的导航类型：按钮或链接。
* 报表元素标签的默认位置。 此位置可以为每个元素重载。
* 用于生成报表页面的模板或主题。

![](assets/s_ncs_advuser_report_properties_08.png)

## 个性化错误页面 {#personalizing-the-error-page}

通过 **[!UICONTROL Error page]** 该选项卡，可以配置报告显示出错时将显示的消息。

您可以定义文本并将其链接到特定标识符以管理报告本地化。 有关此内容的详细信息， [请参阅添加页眉和页脚](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

![](assets/s_ncs_advuser_report_properties_11.png)
