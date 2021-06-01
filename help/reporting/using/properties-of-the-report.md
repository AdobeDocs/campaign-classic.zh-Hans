---
product: campaign
title: 报告的属性
description: 了解有关报表属性设置的更多信息
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 2%

---

# 报告的属性{#properties-of-the-report}

您可以完全个性化并配置报表，以满足您的需求。 为此，请编辑其属性。 通过活动序列图表上方的&#x200B;**[!UICONTROL Properties]**&#x200B;按钮访问报表属性。

![](assets/s_ncs_advuser_report_properties_01.png)

常规属性描述如下。 在&#x200B;**[!UICONTROL Parameters]**、**[!UICONTROL Variables]**&#x200B;和&#x200B;**[!UICONTROL Scripts]**&#x200B;选项卡中配置的高级功能在此部分](../../reporting/using/advanced-functionalities.md)中有介绍。[

## 常规属性{#overall-properties}

在报表属性的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，您可以编辑下面列出的设置：

* 报表的标签和内部名称。 **[!UICONTROL Internal name]**&#x200B;用于报表的最终URL。 在创建报告后，不应更改该设置。

* 在报告创建期间，将选择报告&#x200B;**文件夹**。 最佳做法是为自定义报告创建专用文件夹，以便它们不会与[内置报告](../../reporting/using/about-campaign-built-in-reports.md)混合使用。

* 创建报告时，将选择&#x200B;**Storage**。 要更改报表的数据表，请单击&#x200B;**[!UICONTROL Document type]**&#x200B;字段右侧的&#x200B;**[!UICONTROL Select link]**&#x200B;图标。

   ![](assets/s_ncs_advuser_report_properties_02.png)

* **访问控制**&#x200B;参数。 以下介绍了这些设置。

## 控制对报告{#report-accessibility}的访问

可以在Adobe Campaign控制台中或通过Web浏览器访问报表。 在这种情况下，可能需要配置如下所示的报表访问控制。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的选项包括：

* **[!UICONTROL Anonymous access]**:此选项允许不受限制地访问报表。但是，不可能操纵。

   “webapp”技术操作员的权限用于显示报表元素。 在此部分](../../platform/using/access-management-operators.md)中了解更多[信息。

* **[!UICONTROL Access control]**:此选项允许Adobe Campaign运算符在登录后访问它。
* **[!UICONTROL Specific account]**:利用此选项，可使用在字段中选择的运算符的权限执行 **[!UICONTROL Operator]** 报告。

## 管理报表本地化{#managing-report-localization}

您可以配置希望将报表翻译成的语言。 要执行此操作，请单击&#x200B;**[!UICONTROL Localization]**&#x200B;选项卡。

![](assets/s_ncs_advuser_report_properties_06.png)

编辑语言是您所用的语言。 添加语言时，子选项卡会显示在报表编辑页面中。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>有关Campaign中网页本地化的更多信息，请参阅[此部分](../../web/using/translating-a-web-form.md)。

## 个性化HTML渲染{#personalizing-html-rendering}

在&#x200B;**[!UICONTROL Rendering]**&#x200B;选项卡中，您可以个性化页面的数据显示模式。 您可以选择：

* 图表渲染引擎：默认情况下，渲染引擎为HTML 5。
* 报表中的导航类型：按钮或链接。
* 报表元素的标签的默认位置。 此位置可为每个元素进行重载。
* 用于生成报表页面的模板或主题。

![](assets/s_ncs_advuser_report_properties_08.png)

## 个性化错误页面{#personalizing-the-error-page}

通过&#x200B;**[!UICONTROL Error page]**&#x200B;选项卡，可配置在报表显示出错时显示的消息。

您可以定义文本并将其链接到特定标识符以管理报表本地化。 有关更多信息，请参阅[添加页眉和页脚](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

![](assets/s_ncs_advuser_report_properties_11.png)
