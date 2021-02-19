---
solution: Campaign Classic
product: campaign
title: 调查入门
description: 开始使用活动调查
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: e76eb171aac1f7088ff8647f99c928ec349b24fc
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 1%

---


# 调查入门{#about-surveys}

Adobe Campaign包括一个图形模块，用于定义和发布Web 应用程序。 它用于创建页面，如外部网上的编辑表单，或包括来自数据库的数据的通知表单（包括表、图表、输入表单等）。 利用此功能，您可以设计和发布网页，以便用户查找或输入信息。

可选的&#x200B;**调查**&#x200B;模块允许您创建新类型的Web 应用程序以创建和管理在线调查表，如添加或修改用户档案信息的表单、订阅或取消订阅信息服务或竞赛条目表单。 收集答案后，它们会存储在数据库或本地变量中。 通过对问卷的回答，可以动态地扩展数据模型。 您可以实时视图结果，过滤响应，并使用专用图表分析它们。

本章详细介绍了创建和管理&#x200B;**调查**、字段和页面管理、存储模式和记录的方法。

创建标准Web表单的步骤详见[本节](../../web/using/about-web-forms.md)。

Web 应用程序管理详见[本节](../../web/using/about-web-applications.md)。 请参阅本章以了解更多信息。

>[!CAUTION]
>
>出于隐私考虑，我们建议对所有外部资源使用HTTPS。

## 功能范围{#campaign-surveys-scope}

在Adobe Campaign中，Web 应用程序通常允许您访问以下功能：

* 创建多页表单，
* 多语言调查管理，
* 图形页面管理界面，多列页面布局，
* 呈现个性化和现场定位，
* 根据答案有条件显示调查字段，
* 条件页面显示，
* 在批准前检查信息，具体取决于预期数据类型（数字、电子邮件地址、日期等） 和必填字段，
* 电子邮件邀请/通知、
* 个性化错误和最终消息，
* 使用图像、视频、超文本链接、captcha等

>[!NOTE]
>
>链接到Web 窗体的所有配置详见[本节](../../web/using/about-web-forms.md)。 有关使用文档的概念和Web表单功能的详细信息，请参阅本Adobe Campaign。

可选的调查创建模块(**调查**)优惠以下附加功能：

* 数据库的动态扩展：创建不属于初始数据模型的答案。 有关此问题的详细信息，请参阅[存储收集的答案](../../web/using/managing-answers.md#storing-collected-answers)。
* 分数管理。 有关详细信息，请参阅[得分管理](../../web/using/managing-answers.md#score-management)。
* 随机显示问题。 有关此问题的详细信息，请参阅[添加问题](../../web/using/building-a-survey.md#adding-questions)。
* 实时跟踪答案。 有关详细信息，请参阅[响应跟踪](../../web/using/publish--track-and-use-collected-data.md#response-tracking)。
* 生成专用报告。 有关详细信息，请参阅[关于调查的报告](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys)。

与Web 应用程序相比，调查具有简化的图形界面，编辑控件数量减少。

## 调查实施步骤{#surveys-implementation-steps}

应用以下步骤创建和传送调查并处理结果：

1. 创建调查的页面及其内容(输入字段、下拉列表、问题等)。
1. 定义如何保存答案。

   可以插入数据预加载步骤，以预加载表单中已有数据的表单。 您还可以添加测试框。

1. 发布，然后将调查交付给收件人(例如，在投放或网站中包含链接)。
1. 监控响应和视图报告。

有关配置和排序这些步骤的详细信息，请参阅[此部分](../../web/using/about-web-forms.md)。 本章仅详细介绍特定于调查的配置。

## 调查配置{#surveys-configuration}

调查存储在Adobe Campaign树的&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;节点中。 配置位于以下文件夹中：

* **[!UICONTROL Administration > Configuration > Form rendering]**:包含Web表单演示文稿(应用程序和调查)的渲染模板。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表单模板。要创建表单，您需要使用模板进行开始。

>[!NOTE]
>
>配置信息位于[此部分](../../web/using/about-web-forms.md)中。

