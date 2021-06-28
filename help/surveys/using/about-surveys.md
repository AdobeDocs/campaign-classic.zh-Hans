---
product: campaign
title: 调查入门
description: Campaign调查入门
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 4%

---

# 调查入门{#about-surveys}

Adobe Campaign包含一个用于定义和发布Web应用程序的图形模块。 它用于创建页面，如外联网上的编辑表单，或通知表单，包括来自数据库的数据，包括表、图表、输入表单等。 使用此功能可设计和发布网页，用户可在其中查找或输入信息。

可选的&#x200B;**Survey**&#x200B;附加组件允许您创建新类型的Web应用程序以创建和管理在线调查表，例如用于添加或修改用户档案信息、订阅或退订信息服务或竞争条目表单的表单。 收集了答案后，它们会存储在数据库或本地变量中。 该数据模型可通过对问卷的回答进行动态扩展。 您可以实时查看结果，过滤响应，并使用专用图表分析结果。

本章详细介绍如何创建和管理&#x200B;**调查**、字段和页面管理、存储模式和记录。

[!DNL :bulb:] 在此页面中了解如何创建您的第 [一个调查](getting-started-with-surveys.md)。

>[!NOTE]
>
>* [本文档](../../web/using/about-web-forms.md)中提供了创建标准Web窗体的详细步骤。
   >
   >
* [本文档](../../web/using/about-web-applications.md)中详细介绍了Web应用程序管理。 有关更多信息，请参阅本章。


## 功能范围 {#campaign-surveys-scope}

在Adobe Campaign中，使用[Web应用程序](../../web/using/about-web-forms.md)执行以下操作：

* 创建多页面表单，
* 使用集成的翻译工具管理多语言表单，
* 管理图形界面、多列页面布局、
* 添加个性化并定义字段位置，
* 根据答案显示调查字段的条件，
* 条件页面显示，
* 在批准前检查信息，具体取决于预期的数据类型（数字、电子邮件地址、日期等） 和必填字段，
* 发送电子邮件邀请/通知，
* 个性化错误和结束页面，
* 在表单中添加图像、视频、超文本链接、验证码等

可选的调查创建模块提供了用户友好UI和以下附加功能：

* 数据库的动态扩展：创建不属于初始数据模型的答案。 [了解详情](../../surveys/using/managing-answers.md#storing-collected-answers)。
* 评分管理。 [了解详情](../../surveys/using/managing-answers.md#score-management)。
* 随机显示问题。 [了解详情](../../surveys/using/building-a-survey.md#adding-questions)。
* 实时跟踪答案。 [了解详情](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking)。
* 生成专用报告。 [了解详情](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys)。


## 实施步骤 {#surveys-implementation-steps}

应用以下步骤来创建和提交调查并处理其结果：

1. 创建调查页面及其内容（输入字段、下拉列表、问题等）。
1. 定义应如何保存答案。 可以插入数据预加载步骤，以便使用数据库中已存在的数据预加载表单。 您还可以添加测试框。
1. 发布调查，然后将调查提交给收件人（例如，在投放或网站中包含链接）。
1. 监视响应并查看报告。

有关配置和排序这些步骤的更多信息，请参阅[本文档](../../web/using/about-web-forms.md)。 本章仅详细介绍特定于调查的配置。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## 设置 {#settings}

默认情况下，调查在Adobe Campaign树的&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;节点中可用。

设置存储在以下文件夹中：

* **[!UICONTROL Administration > Configuration > Form rendering]**:包含Web窗体演示文稿（应用程序和调查）的渲染模板。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表单模板。要创建表单，您需要从模板开始。

>[!NOTE]
>
>有关设置详细信息，请参见[本文档](../../web/using/about-web-forms.md)。
