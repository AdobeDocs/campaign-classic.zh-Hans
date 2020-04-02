---
title: 关于Web应用程序
seo-title: 关于Web应用程序
description: 关于Web应用程序
seo-description: null
page-status-flag: never-activated
uuid: acfa6e5e-b503-4a1a-871e-e70007874f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 3af763ad-6b0d-4f4c-aed1-c5e12efd4760
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 61c7681535dc08e1d705d7d239e96c603bbad339

---


# 关于Web应用程序{#about-web-applications}

Adobe Campaign允许您使用数据库中的数据和符合连接用户权限的内容创建和发布动态的交互式Web 应用程序。 您可以创建页面，如外部网上的编辑表单，或包括来自数据库的数据的通知表单，这些表单包含表、图表、输入表单等。 利用此功能，您可以设计和发布网页，用户可在其中查找或输入信息。

这可以是包含预加载了订阅数据库中包含信息的数据的Adobe Campaign表单，如下所示：

![](assets/webapp_form_sample.png)

本章概述了如何管理Web 应用程序。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## Web 应用程序范围 {#web-application-scope}

Adobe Campaign中的Web 应用程序可访问以下功能：

* 创建多页表单。 For more on this, refer to this [page](../../web/using/about-web-forms.md).
* 借助集成的翻译工具实现多语言调查管理。 For more on this, refer to this [page](../../web/using/translating-a-web-application.md).
* 图形页面管理界面，多列页面布局。 For more on this, refer to this [page](../../web/using/designing-a-web-application.md).
* 呈现个性化和现场位置。 For more on this, refer to this [page](../../web/using/editing-content.md#adding-personalization-content).
* 根据答案有条件地显示调查字段。 For more on this, refer to this [page](../../web/using/form-rendering.md#defining-fields-conditional-display).
* 随机显示问题。 For more on this, refer to this [page](../../web/using/building-a-survey.md#adding-questions).
* 条件页面显示。 For more on this, refer to this [page](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).
* 验证前的信息检查取决于预期的数据类型（编号、电子邮件地址、日期等）和必填字段。 For more on this, refer to this [page](../../web/using/form-rendering.md#defining-control-settings).
* 电子邮件邀请或通知。 For more on this, refer to this [page](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email).
* 个性化错误和结束消息。 For more on this, refer to this [page](../../web/using/defining-web-forms-properties.md#setting-up-an-error-page).
* 使用图像、视频、超文本链接、captcha等 For more on this, refer to this [page](../../web/using/editing-content.md).
* 实时监控响应。 For more on this, refer to this [page](../../web/using/publish--track-and-use-collected-data.md#response-tracking).

可选的 **调查创建** 模块优惠了以下附加功能：

* 数据库的动态扩展：创建未包含在初始数据模板中的响应。 For more on this, refer to this [page](../../web/using/managing-answers.md#storing-collected-answers).
* 生成专用报告。 For more on this, refer to this [page](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

与Web 应用程序相比，调查具有简化的图形界面，并减少了编辑控件的数量。

>[!NOTE]
>
>调查详见 [本节](../../web/using/about-surveys.md)。
>
>本节详细介绍了Adobe Campaign中Web 窗体的 [整体功能](../../web/using/about-web-forms.md)。

## Web 应用程序实施 {#web-application-implementation}

要创建和发布Web 应用程序，您必须：

1. 创建内容(字段、列表、表、图形等)。

   您还可以视图详细介绍表单可用字段的部分：所有这些字段也适用于Web 应用程序。 此信息在此页 [面中可用](../../web/using/adding-fields-to-a-web-form.md)。

1. 根据需要，您可以添加预加载、测试和保存步骤，并配置访问控制系统（主要在外部网出版物的框架内）。
1. 发布Web 应用程序以在外部网或Adobe Campaign中提供。

## Web 应用程序初始配置 {#web-application-initial-configuration}

Web 应用程序通过选项卡和 **[!UICONTROL Web Applications]** 选项卡中的链 **[!UICONTROL Campaigns]** 接创 **[!UICONTROL Profiles and targets]** 建。

Web 应用程序存储在 **[!UICONTROL Resources > Online > Web Applications]** Adobe Campaign树的节点中。 配置在以下文件夹中进行了划分：

* **[!UICONTROL Administration > Configuration > Form renderings]**:包含Web表单演示文稿(应用程序和调查)的渲染模板。 该模板允许您生成表单。 它还使用CSS样式表。 此样式表可能会在模板级别过载。 有关详细信息，请参见[此页面](../../web/using/form-rendering.md#selecting-the-form-rendering-template)。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表单模板。 要创建表单或Web 应用程序，您必须从模板中开始。

## Web 应用程序模板 {#web-application-templates}

默认情况下，Adobe Campaign为每个可用Web 应用程序提供一个模板。

>[!NOTE]
>
>您可以将现有Web 应用程序转换为模板。 为此，请选择表单并右键单击。 Select **[!UICONTROL Actions > Save as template...]**.

可以通过Adobe Campaign树的节 **[!UICONTROL Resources > Templates > Web Application templates]** 点创建新模板。

创建向导允许您选择要启用的选项，如下所示。

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>可用的应用程序取决于您的选项和模块。 请检查您的许可协议。

