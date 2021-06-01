---
product: campaign
title: 调查入门
description: Campaign调查入门
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 1%

---

# 调查入门{#about-surveys}

Adobe Campaign包含一个用于定义和发布Web应用程序的图形模块。 它用于创建页面，如外联网上的编辑表单，或通知表单，包括来自数据库的数据，包括表、图表、输入表单等。 利用此功能，可设计和发布网页，供用户查找或输入信息。

可选的&#x200B;**Survey**&#x200B;模块允许您创建新类型的Web应用程序，以创建和管理在线调查表，例如添加或修改用户档案信息、订阅或退订信息服务或竞争条目表单的表单。 收集了答案后，它们会存储在数据库或本地变量中。 该数据模型可通过对问卷的回答进行动态扩展。 您可以实时查看结果，过滤响应，并使用专用图表分析结果。

本章详细介绍创建和管理&#x200B;**调查**、字段和页面管理、存储模式和记录的方法。

有关创建标准Web窗体的详细步骤，请参见[此部分](../../web/using/about-web-forms.md)。

[此部分](../../web/using/about-web-applications.md)中详细介绍了Web应用程序管理。 有关更多信息，请参阅本章。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## 功能范围{#campaign-surveys-scope}

在Adobe Campaign中，Web应用程序通常允许您访问以下功能：

* 创建多页表单，
* 使用集成翻译工具进行多语言调查管理，
* 图形页面管理界面，多列页面布局，
* 呈现个性化和字段位置，
* 根据答案有条件地显示调查字段，
* 条件页面显示、
* 在批准前检查信息，具体取决于预期数据类型（数字、电子邮件地址、日期等） 和必填字段，
* 电子邮件邀请/通知、
* 个性化错误和结束消息，
* 使用图像、视频、超文本链接、验证码等。

>[!NOTE]
>
>[此部分](../../web/using/about-web-forms.md)中详细描述了链接到Web表单的所有配置。 有关使用Adobe Campaign的概念和Web窗体功能的详细信息，请参阅本文档。

可选的调查创建模块(**Survey**)提供以下附加功能：

* 数据库的动态扩展：创建不属于初始数据模型的答案。 有关更多信息，请参见[存储收集的答案](../../web/using/managing-answers.md#storing-collected-answers)。
* 评分管理。 有关更多信息，请参阅[得分管理](../../web/using/managing-answers.md#score-management)。
* 随机显示问题。 有关更多信息，请参阅[添加问题](../../web/using/building-a-survey.md#adding-questions)。
* 实时跟踪答案。 有关更多信息，请参阅[响应跟踪](../../web/using/publish--track-and-use-collected-data.md#response-tracking)。
* 生成专用报告。 有关更多信息，请参阅[调查报告](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys)。

与Web应用程序相比，调查具有简化的图形界面，编辑控件数量减少。

## 调查实施步骤{#surveys-implementation-steps}

应用以下步骤来创建和提交调查并处理其结果：

1. 创建调查页面及其内容（输入字段、下拉列表、问题等）。
1. 定义应如何保存答案。

   可以插入数据预加载步骤，以便使用数据库中已存在的数据预加载表单。 您还可以添加测试框。

1. 发布调查，然后将调查提交给收件人（例如，在投放或网站中包含链接）。
1. 监视响应并查看报告。

有关配置和排序这些步骤的更多信息，请参阅[此部分](../../web/using/about-web-forms.md)。 本章仅详细介绍特定于调查的配置。

## 调查配置{#surveys-configuration}

调查存储在Adobe Campaign树的&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;节点中。 配置位于以下文件夹中：

* **[!UICONTROL Administration > Configuration > Form rendering]**:包含Web窗体演示文稿（应用程序和调查）的渲染模板。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表单模板。要创建表单，您需要从模板开始。

>[!NOTE]
>
>[此部分](../../web/using/about-web-forms.md)中提供了配置信息。
