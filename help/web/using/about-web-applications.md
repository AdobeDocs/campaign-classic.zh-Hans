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
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 关于Web应用程序{#about-web-applications}

Adobe Campaign允许您创建和发布动态的交互式Web应用程序，其中包含来自数据库的数据以及符合已连接用户权限的内容。 您可以创建页面，如外部网上的编辑表单，或包括来自数据库的数据的通知表单，这些表单包含表、图表、输入表单等。 利用此功能，您可以设计和发布网页，用户可在其中查找或输入信息。

这可以是包含预加载了Adobe Campaign数据库中包含的信息的数据的订阅表单，如下所示：

![](assets/webapp_form_sample.png)

本章概述如何管理Web应用程序。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## Web应用程序范围 {#web-application-scope}

Adobe Campaign中的Web应用程序提供了以下功能：

* 创建多页表单，
* 使用集成的翻译工具管理多语言调查，
* 图形页面管理界面，多列页面布局，
* 呈现个性化和现场定位，
* 根据答案有条件地显示调查字段，
* 随机展示问题，
* 条件式页面显示、
* 验证前的信息检查取决于预期的数据类型（编号、电子邮件地址、日期等）和必填字段，
* 电子邮件邀请或通知，
* 个性化错误和最终消息，
* 使用图像、视频、超文本链接、captcha等
* 实时监控响应。

可选的 **Survey** 创建模块提供以下附加功能：

* 数据库的动态扩展：创建未包含在初始数据模板中的响应，
* 生成专用报告。

与Web应用程序相比，调查具有简化的图形界面，并减少了编辑控件的数量。

>[!NOTE]
>
>本节详细介绍 [了调查](../../web/using/about-surveys.md)。
>
>Adobe Campaign中Web表单的整体功能在本节中有 [详细说明](../../web/using/about-web-forms.md)。

## Web应用程序实现 {#web-application-implementation}

要创建和发布Web应用程序，您必须：

1. 创建内容（字段、列表、表、图形等）。

   您还可以查看详细了解表单可用字段的部分：所有这些字段也适用于Web应用程序。 此信息在此页 [面中可用](../../web/using/adding-fields-to-a-web-form.md)。

1. 根据需要，您可以添加预加载、测试和保存步骤，并配置访问控制系统（主要在外部网发布的框架内）。
1. 发布Web应用程序，使其在外部网或Adobe Campaign中可用。

## Web应用程序初始配置 {#web-application-initial-configuration}

Web应用程序通过选项卡和选 **[!UICONTROL Web Applications]** 项卡中的链接 **[!UICONTROL Campaigns]** 创建 **[!UICONTROL Profiles and targets]** 而成。

Web应用程序存储在Adobe **[!UICONTROL Resources > Online > Web Applications]** Campaign树的节点中。 配置在以下文件夹中进行了划分：

* **[!UICONTROL Administration > Configuration > Form renderings]**:包含Web表单演示文稿（应用程序和调查）的呈现模板。 该模板允许您生成表单。 它还使用CSS样式表。 此样式表可能会在模板级别过载。 有关详细信息，请参见[此页面](../../web/using/form-rendering.md#selecting-the-form-rendering-template)。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表单模板。 要创建表单或Web应用程序，您必须从模板开始。

## Web应用程序模板 {#web-application-templates}

默认情况下，Adobe Campaign为每个可用的Web应用程序提供一个模板。

>[!NOTE]
>
>您可以将现有Web应用程序转换为模板。 为此，请选择表单并右键单击。 Select **[!UICONTROL Actions > Save as template...]**.

您可以通过Adobe Campaign树的 **[!UICONTROL Resources > Templates > Web Application templates]** 节点创建新模板。

创建向导允许您选择要启用的选项，如下所示。

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>可用的应用程序取决于您的选项和模块。 请检查您的许可协议。

