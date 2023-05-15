---
product: campaign
title: Web 应用程序入门
description: 创建和共享动态Web应用程序、登陆页和调查
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 20%

---

# Web 应用程序入门{#about-web-applications}



Adobe Campaign允许您使用来自数据库的数据和适合连接用户权限的内容来创建和发布动态和交互式Web应用程序。

您可以创建页面，如外联网上的编辑表单，或通知表单，包括来自数据库的数据，包括表、图表、输入表单等。 利用此功能，可设计和发布网页，供用户查找或输入信息。

这可以是一个订阅表单，其中包含已预加载了Adobe Campaign数据库中包含的信息的数据，如下所示：

![](assets/webapp_form_sample.png)

本章概述如何管理Web应用程序。

>[!NOTE]
>
>请参阅 [安全和隐私检查列表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html) 了解如何优化web应用程序的安全性。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## Web应用程序范围 {#web-application-scope}

Adobe Campaign中的Web应用程序提供对以下功能的访问：

* 创建多页表单。 有关详细信息，请参见此 [ 页面](about-web-forms.md)。
* 使用集成翻译工具进行多语言调查管理。 有关详细信息，请参见此 [ 页面](translating-a-web-application.md)。
* 图形页面管理界面，多列页面布局。 有关详细信息，请参见此 [ 页面](designing-a-web-application.md)。
* 呈现个性化和字段位置。 有关详细信息，请参见此 [ 页面](editing-content.md#adding-personalization-content)。
* 根据答案有条件地显示调查字段。 有关详细信息，请参见此 [ 页面](form-rendering.md#defining-fields-conditional-display)。
* 随机显示问题。 有关详细信息，请参见此 [ 页面](../../surveys/using/building-a-survey.md#adding-questions)。
* 条件页面显示。 有关详细信息，请参见此 [ 页面](defining-web-forms-page-sequencing.md#conditional-page-display)。
* 验证前的信息检查取决于预期的数据类型（数字、电子邮件地址、日期等） 和必填字段。 有关详细信息，请参见此 [ 页面](form-rendering.md#defining-control-settings)。
* 电子邮件邀请或通知。 有关详细信息，请参见此 [ 页面](publishing-a-web-form.md#delivering-a-form-via-email)。
* 错误和结束消息的个性化。 有关详细信息，请参见此 [ 页面](defining-web-forms-properties.md#setting-up-an-error-page)。
* 使用图像、视频、超文本链接、验证码等。 有关详细信息，请参见此 [ 页面](editing-content.md)。
* 实时监控响应。 有关详细信息，请参见此 [ 页面](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking)。

可选 **调查** 创建模块提供了以下附加功能：

* 数据库的动态扩展：创建初始数据模板中未包含的响应。 有关详细信息，请参见此 [ 页面](../../surveys/using/managing-answers.md#storing-collected-answers)。
* 生成专用报告。 有关详细信息，请参见此 [ 页面](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys)。

与Web应用程序相比，调查具有简化的图形界面，编辑控件数量减少。

>[!NOTE]
>
>有关调查的详细信息，请参阅 [此部分](../../surveys/using/about-surveys.md).
>
>Adobe Campaign中Web窗体的总体功能详见 [此部分](about-web-forms.md).

## Web应用程序实施 {#web-application-implementation}

要创建和发布Web应用程序，您必须：

1. 创建内容（字段、列表、表、图形等）。

   您还可以查看详细介绍表单可用字段的部分：所有这些字段也可用于Web应用程序。 此信息可在 [本页](adding-fields-to-a-web-form.md).

1. 根据需要，您可以添加预加载、测试和保存步骤，以及配置访问控制系统（主要是在外联网发布的框架内）。
1. 发布Web应用程序，以在外联网或Adobe Campaign中提供。

## Web应用程序初始配置 {#web-application-initial-configuration}

Web应用程序通过 **[!UICONTROL Web Applications]** 链接 **[!UICONTROL Campaigns]** 和 **[!UICONTROL Profiles and targets]** 选项卡。

Web应用程序存储在 **[!UICONTROL Resources > Online > Web Applications]** Adobe Campaign树的节点。 配置在以下文件夹中进行划分：

* **[!UICONTROL Administration > Configuration > Form renderings]**:包含Web窗体演示文稿（应用程序和调查）的渲染模板。 利用模板可生成表单。 它还使用CSS样式表。 此样式表可能会在模板级别过载。 有关详细信息，请参见[此页面](form-rendering.md#selecting-the-form-rendering-template)。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表单模板。 要创建表单或Web应用程序，必须从模板开始。

## Web 应用程序模板 {#web-application-templates}

默认情况下，Adobe Campaign会为每个可用的Web应用程序提供一个模板。

>[!NOTE]
>
>您可以将现有Web应用程序转换为模板。 要执行此操作，请选择表单并右键单击。 选择 **[!UICONTROL Actions > Save as template...]**。

您可以通过 **[!UICONTROL Resources > Templates > Web Application templates]** Adobe Campaign树的节点。

创建向导允许您选择要启用的选项，如下所示。

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>可用的应用程序取决于您的选项和模块。 请核实您的许可协议。
