---
product: campaign
title: 报告的属性
description: 了解有关报表属性设置的更多信息
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Reporting, Monitoring
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# 报告的属性{#properties-of-the-report}



您可以根据自己的需求，对报表进行充分的个性化和配置。 为此，请编辑其属性。 通过访问报告属性 **[!UICONTROL Properties]** 按钮进行查看。

![](assets/s_ncs_advuser_report_properties_01.png)

常规属性如下所述。 在中配置的高级功能 **[!UICONTROL Parameters]**， **[!UICONTROL Variables]** 和 **[!UICONTROL Scripts]** 选项卡说明 [在此部分中](../../reporting/using/advanced-functionalities.md).

## 常规属性 {#overall-properties}

在 **[!UICONTROL General]** 选项卡中，您可以编辑下面列出的设置：

* 报告的标签和内部名称。 此 **[!UICONTROL Internal name]** 在报表最终URL中使用。 在创建报告后不应对其进行更改。

* 报告 **文件夹** 在创建报告期间选择。 最佳实践是为自定义报表创建专用文件夹，以便它们不会与混合 [内置报告](../../reporting/using/about-campaign-built-in-reports.md).

* 此 **存储** 在创建报告时选择。 要更改报表的数据表，请单击 **[!UICONTROL Select link]** 图标（位于页面右侧） **[!UICONTROL Document type]** 字段。

  ![](assets/s_ncs_advuser_report_properties_02.png)

* 此 **访问控制** 参数。 这些设置如下所述。

## 控制对报告的访问 {#report-accessibility}

可以在Adobe Campaign控制台中或通过Web浏览器访问报表。 在这种情况下，可能有必要如下所示配置报表访问控制。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的选项为：

* **[!UICONTROL Anonymous access]**：此选项启用对报表的无限制访问。 但是，操作是不可能的。

  “webapp”技术操作员的权限用于显示报表元素。 了解详情 [在此部分中](../../platform/using/access-management-operators.md).

* **[!UICONTROL Access control]**：此选项允许Adobe Campaign操作员在登录后访问它。
* **[!UICONTROL Specific account]**：利用此选项可在 **[!UICONTROL Operator]** 字段。

## 翻译报告 {#report-localization}

您可以配置希望将报告翻译成的语言。 要执行此操作，请单击 **[!UICONTROL Localization]** 选项卡。

![](assets/s_ncs_advuser_report_properties_06.png)

编辑语言是您编写的语言。 添加语言时，子选项卡会显示在报告编辑页面中。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>有关Campaign中网页本地化的更多信息，请参阅 [本节](../../web/using/translating-a-web-form.md).

## 个性化HTML呈现 {#personalizing-html-rendering}

在 **[!UICONTROL Rendering]** 选项卡上，您可以个性化页面的数据显示模式。 您可以选择：

* 报表中的导航类型：通过按钮或链接。
* 报表元素标签的默认位置。 可针对每个元素重载此位置。
* 用于生成报表页面的模板或主题。

![](assets/s_ncs_advuser_report_properties_08.png)

## 个性化错误页面 {#personalizing-the-error-page}

此 **[!UICONTROL Error page]** 选项卡允许您配置在报表显示中出现错误时将显示的消息。

您可以定义文本并将它们链接到特定标识符，以管理报告本地化。 有关详细信息，请参见 [添加页眉和页脚](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
