---
solution: Campaign Classic
product: campaign
title: 报告的属性
description: 了解有关报表属性设置的更多信息
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 2%

---


# 报告的属性{#properties-of-the-report}

您可以完全个性化和配置报表以满足您的需求。 为此，请编辑其属性。 报表属性通过活动序列图上方的&#x200B;**[!UICONTROL Properties]**&#x200B;按钮进行访问。

![](assets/s_ncs_advuser_report_properties_01.png)

常规属性如下所述。 在&#x200B;**[!UICONTROL Parameters]**、**[!UICONTROL Variables]**&#x200B;和&#x200B;**[!UICONTROL Scripts]**&#x200B;选项卡中配置的高级功能在本节](../../reporting/using/advanced-functionalities.md)中有[的说明。

## 常规属性{#overall-properties}

在报表属性的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，可以编辑以下列出的设置：

* 报表的标签和内部名称。 **[!UICONTROL Internal name]**&#x200B;用于报表最终URL。 在创建报告后不应更改它。

* 报表&#x200B;**Folder**&#x200B;在创建报表时被选中。 最佳实践是为自定义报表创建一个专用文件夹，以使其不与[内置报表](../../reporting/using/about-campaign-built-in-reports.md)混合。

* 创建报告时，将选择&#x200B;**存储**。 要更改报表的数据表，请单击&#x200B;**[!UICONTROL Document type]**&#x200B;字段右侧的&#x200B;**[!UICONTROL Select link]**&#x200B;图标。

   ![](assets/s_ncs_advuser_report_properties_02.png)

* **访问控制**&#x200B;参数。 下面介绍了这些设置。

## 控制对报表{#report-accessibility}的访问

报表可以在Adobe Campaign控制台中或通过Web浏览器访问。 在这种情况下，可以需要配置报表访问控制，如下所示。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的选项有：

* **[!UICONTROL Anonymous access]**:此选项允许不受限制地访问报表。但是，不可能操纵。

   “webapp”技术操作员的权限用于显示报表元素。 请阅读本节](../../platform/using/access-management-operators.md)了解更多信息。[

* **[!UICONTROL Access control]**:此选项允许Adobe Campaign操作员在登录后访问它。
* **[!UICONTROL Specific account]**:通过此选项，可以在字段中选择运算符的权限下执行 **[!UICONTROL Operator]** 报告。

## 管理报告本地化{#managing-report-localization}

您可以配置要将报表翻译为的语言。 要执行此操作，请单击&#x200B;**[!UICONTROL Localization]**&#x200B;选项卡。

![](assets/s_ncs_advuser_report_properties_06.png)

编辑语言是您所用的语言。 添加语言时，子选项卡会显示在报表编辑页面中。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>有关活动中网页本地化的详细信息，请参阅[本节](../../web/using/translating-a-web-form.md)。

## 个性化HTML渲染{#personalizing-html-rendering}

在&#x200B;**[!UICONTROL Rendering]**&#x200B;选项卡中，您可以个性化页面的数据显示模式。 您可以选择：

* 图表渲染引擎：默认情况下，渲染引擎为HTML 5。
* 报表中的导航类型：。
* 报表元素的标签的默认位置。 此位置可以为每个元素重载。
* 用于生成报表页面的模板或主题。

![](assets/s_ncs_advuser_report_properties_08.png)

## 个性化错误页{#personalizing-the-error-page}

使用&#x200B;**[!UICONTROL Error page]**&#x200B;选项卡，可以配置在报告显示出现错误时将显示的消息。

您可以定义文本并将其链接到特定标识符以管理报表本地化。 有关详细信息，请参阅[添加页眉和页脚](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

![](assets/s_ncs_advuser_report_properties_11.png)
