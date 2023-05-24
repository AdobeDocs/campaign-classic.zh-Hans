---
product: campaign
title: 报告的属性
description: 了解有关报表属性设置的更多信息
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 3%

---

# 报告的属性{#properties-of-the-report}



您可以根据自己的需求，对报表进行全面的个性化和配置。 为此，请编辑其属性。 通过访问报告属性 **[!UICONTROL Properties]** 按钮进行查看。

![](assets/s_ncs_advuser_report_properties_01.png)

常规属性如下所述。 在中配置的高级功能 **[!UICONTROL Parameters]**， **[!UICONTROL Variables]** 和 **[!UICONTROL Scripts]** 对选项卡进行了描述 [在此部分中](../../reporting/using/advanced-functionalities.md).

## 常规属性 {#overall-properties}

在 **[!UICONTROL General]** 选项卡中，您可以编辑下面列出的设置：

* 报告的标签和内部名称。 此 **[!UICONTROL Internal name]** 在报表最终URL中使用。 创建报告后不应对其进行更改。

* 报告 **文件夹** 在创建报告期间选择。 最佳实践是为自定义报表创建专用文件夹，以便它们不会与混合 [内置报告](../../reporting/using/about-campaign-built-in-reports.md).

* 此 **存储** 创建报告时选择。 要更改报表的数据表，请单击 **[!UICONTROL Select link]** 图标右侧的 **[!UICONTROL Document type]** 字段。

   ![](assets/s_ncs_advuser_report_properties_02.png)

* 此 **访问控制** 参数。 这些设置如下所述。

## 控制对报告的访问 {#report-accessibility}

可以在Adobe Campaign控制台中或通过Web浏览器访问报表。 在这种情况下，可能需要配置如下所示的报告访问控制。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的选项为：

* **[!UICONTROL Anonymous access]**：此选项允许不受限制地访问报表。 然而，操纵是不可能的。

   “webapp”技术操作员的权限用于显示报表元素。 了解详情 [在此部分中](../../platform/using/access-management-operators.md).

* **[!UICONTROL Access control]**：此选项允许Adobe Campaign操作员在登录后访问它。
* **[!UICONTROL Specific account]**：利用此选项可在 **[!UICONTROL Operator]** 字段。

## 翻译报告 {#report-localization}

您可以配置希望报告翻译成的语言。 要执行此操作，请单击 **[!UICONTROL Localization]** 选项卡。

![](assets/s_ncs_advuser_report_properties_06.png)

编辑语言是您编写的语言。 添加语言时，报告编辑页面中将显示子选项卡。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>有关Campaign中网页本地化的更多信息，请参阅 [本节](../../web/using/translating-a-web-form.md).

## 个性化HTML呈现 {#personalizing-html-rendering}

在 **[!UICONTROL Rendering]** 选项卡，您可以个性化页面的数据显示模式。 您可以选择：

* 报表中的导航类型：通过按钮或链接。
* 报表元素的默认标签位置。 可以为每个元素重载此位置。
* 用于生成报表页面的模板或主题。

![](assets/s_ncs_advuser_report_properties_08.png)

## 个性化错误页面 {#personalizing-the-error-page}

此 **[!UICONTROL Error page]** 选项卡用于配置在报表显示出错时将显示的消息。

您可以定义文本并将其链接到特定标识符，以管理报表本地化。 有关更多信息，请参阅 [添加页眉和页脚](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
