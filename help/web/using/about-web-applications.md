---
title: 关于 Web 应用程序
description: 创建和共享动态 Web 应用程序、登陆页和调查。
page-status-flag: never-activated
uuid: acfa6e5e-b503-4a1a-871e-e70007874f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 3af763ad-6b0d-4f4c-aed1-c5e12efd4760
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 20%

---


# 开始使用Web应用程序{#about-web-applications}

Adobe Campaign允许您使用来自Web 应用程序库的数据和根据连接用户权限调整的内容创建和发布动态的交互式数据。

您可以创建页面，如外部网上的编辑表单，或通知表单，包括来自数据库的数据以及表、图表、输入表单等。 利用此功能，您可以设计和发布网页，用户可在其中查找或输入信息。

这可以是包含订阅表单的Adobe Campaign表单，该表单已预加载数据库中包含的信息，如下所示：

![](assets/webapp_form_sample.png)

本章概述如何管理Web 应用程序。

>[!NOTE]
>
>请参阅安 [全和隐私检查表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html) ，了解如何优化Web应用程序的安全性。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## Web 应用程序范围 {#web-application-scope}

Adobe Campaign中的Web 应用程序可访问以下功能：

* 创建多页表单。 有关详细信息，请参见此 [ 页面](../../web/using/about-web-forms.md)。
* 借助集成的翻译工具实现多语言调查管理。 有关详细信息，请参见此 [ 页面](../../web/using/translating-a-web-application.md)。
* 图形页面管理界面，多列页面布局。 有关详细信息，请参见此 [ 页面](../../web/using/designing-a-web-application.md)。
* 呈现个性化和现场定位。 有关详细信息，请参见此 [ 页面](../../web/using/editing-content.md#adding-personalization-content)。
* 根据答案条件显示调查字段。 有关详细信息，请参见此 [ 页面](../../web/using/form-rendering.md#defining-fields-conditional-display)。
* 随机显示问题。 有关详细信息，请参见此 [ 页面](../../web/using/building-a-survey.md#adding-questions)。
* 条件页面显示。 有关详细信息，请参见此 [ 页面](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。
* 验证前的信息检查取决于预期的数据类型（编号、电子邮件地址、日期等） 和必填字段。 有关详细信息，请参见此 [ 页面](../../web/using/form-rendering.md#defining-control-settings)。
* 电子邮件邀请或通知。 有关详细信息，请参见此 [ 页面](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email)。
* 个性化错误和结束消息。 有关详细信息，请参见此 [ 页面](../../web/using/defining-web-forms-properties.md#setting-up-an-error-page)。
* 使用图像、视频、超文本链接、captcha等 有关详细信息，请参见此 [ 页面](../../web/using/editing-content.md)。
* 实时监控响应。 有关详细信息，请参见此 [ 页面](../../web/using/publish--track-and-use-collected-data.md#response-tracking)。

可选的 **调查** 创建模块优惠以下附加功能：

* 数据库的动态扩展：创建未包含在初始数据模板中的响应。 有关详细信息，请参见此 [ 页面](../../web/using/managing-answers.md#storing-collected-answers)。
* 生成专用报告。 有关详细信息，请参见此 [ 页面](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys)。

与Web 应用程序相比，调查具有简化的图形界面，并减少了编辑控件的数量。

>[!NOTE]
>
>调查详见 [本节](../../web/using/about-surveys.md)。
>
>Adobe Campaign中Web 窗体的总体功能在本节 [中详述](../../web/using/about-web-forms.md)。

## Web 应用程序实施 {#web-application-implementation}

要创建并发布Web 应用程序，您必须：

1. 创建内容(字段、列表、表、图形等)。

   您还可以视图详细介绍表单可用字段的部分：所有这些字段也适用于Web 应用程序。 此信息在此页 [面中可用](../../web/using/adding-fields-to-a-web-form.md)。

1. 根据需要，您可以添加预加载、测试和保存步骤，并配置访问控制系统（主要在外部网出版物的框架内）。
1. 发布Web 应用程序以在外部网或Adobe Campaign中提供。

## Web 应用程序初始配置 {#web-application-initial-configuration}

Web 应用程序通过选项卡 **[!UICONTROL Web Applications]** 和选项卡中的 **[!UICONTROL Campaigns]** 链接 **[!UICONTROL Profiles and targets]** 创建。

Web 应用程序存储在 **[!UICONTROL Resources > Online > Web Applications]** Adobe Campaign树的节点中。 配置在以下文件夹中进行划分：

* **[!UICONTROL Administration > Configuration > Form renderings]**:包含Web表单演示文稿(应用程序和调查)的渲染模板。 模板允许您生成表单。 它还使用CSS样式表。 此样式表在模板级别可能会过载。 有关详细信息，请参见[此页面](../../web/using/form-rendering.md#selecting-the-form-rendering-template)。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表单模板。 要创建表单或Web 应用程序，您必须从模板进行开始。

## Web 应用程序模板 {#web-application-templates}

默认情况下，Adobe Campaign为每个可用Web 应用程序提供一个模板。

>[!NOTE]
>
>您可以将现有Web 应用程序转换为模板。 为此，请选择表单并右键单击。 选择 **[!UICONTROL Actions > Save as template...]**。

您可以通过Adobe Campaign树的 **[!UICONTROL Resources > Templates > Web Application templates]** 节点创建新模板。

创建向导允许您选择要启用的选项，如下所示。

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>可用的应用程序取决于您的选项和模块。 请核实您的许可协议。

