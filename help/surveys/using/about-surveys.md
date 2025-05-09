---
product: campaign
title: 调查入门
description: Campaign调查入门
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 3%

---

# 调查入门{#about-surveys}

Adobe Campaign包括一个用于定义和发布Web应用程序的图形模块。 这用于创建页面，例如外部网上的编辑表单或通知表单，其中包含来自具有表、图表、输入表单等数据库的数据。 使用此功能可以设计和发布用户可以在其中查找或输入信息的网页。

>[!AVAILABILITY]
>
>在企业(FFDA)部署的Campaign v8中，调查管理不可用。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/config/architecture/ffda/enterprise-deployment){target="_blank"}以了解详情。


可选的&#x200B;**调查**&#x200B;加载项允许您创建新的类型的Web应用程序来创建和管理联机调查表，例如用于添加或修改配置文件信息、订阅或取消订阅信息服务或竞争登录表单的表单。 收集完答案后，它们会存储在数据库中或本地变量中。 数据模型可以通过问卷回答进行动态扩展。 您可以实时查看结果、筛选响应并使用专用图表分析它们。

本章详细介绍如何创建和管理&#x200B;**调查**、字段和页面管理、存储模式和记录。

在[此页面](getting-started-with-surveys.md)中了解如何创建您的第一个调查。

>[!NOTE]
>
>* 有关创建标准Web表单的详细步骤，请参阅[本文档](../../web/using/about-web-forms.md)。
>
>* [此文档](../../web/using/about-web-applications.md)中详细介绍了Web应用程序管理。 请参阅本章以了解更多信息。

## 功能范围 {#campaign-surveys-scope}

在Adobe Campaign中，使用[Web应用程序](../../web/using/about-web-forms.md)可以：

* 创建多页表单，
* 使用集成的翻译工具管理多语言表单，
* 管理图形界面，多列页面布局，
* 添加个性化和定义字段位置，
* 根据答案显示调查字段的条件，
* 条件页面显示，
* 在批准之前检查信息，具体取决于预期的数据类型（数字、电子邮件地址、日期等）和必填字段，
* 发送电子邮件邀请/通知，
* 个性化错误和结束页面，
* 在表单中添加图像、视频、超文本链接、验证码等

可选的调查创建模块提供了用户友好的UI和以下附加功能：

* 数据库的动态扩展：创建不属于初始数据模型的答案。 [了解详情](../../surveys/using/managing-answers.md#storing-collected-answers)。
* 得分管理。 [了解详情](../../surveys/using/managing-answers.md#score-management)。
* 随机显示问题。 [了解详情](../../surveys/using/building-a-survey.md#adding-questions)。
* 实时跟踪答案。 [了解详情](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking)。
* 生成专用报告。 [了解详情](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys)。


## 实施步骤 {#surveys-implementation-steps}

应用以下步骤创建和提供调查并处理其结果：

1. 创建调查的页面及其内容（输入字段、下拉列表、问题等）。
1. 定义应如何保存答案。 可以插入数据预加载步骤，以便使用数据库中已存在的数据预加载表单。 您还可以添加测试框。
1. 然后，在Publish中将调查交付给收件人（例如，在交付或网站中包含链接）。
1. 监视响应并查看报告。

有关这些步骤的配置和顺序的更多信息，请参阅[本文档](../../web/using/about-web-forms.md)。 本章只详细介绍了特定于调查的配置。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## 设置 {#settings}

默认情况下，调查在Adobe Campaign树的&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;节点中可用。

设置存储在以下文件夹中：

* **[!UICONTROL Administration > Configuration > Form rendering]**：包含Web窗体演示（应用程序和调查）的渲染模板。
* **[!UICONTROL Resources > Templates > Web application templates]**：包含表单模板。 要创建表单，您需要从模板开始。

>[!NOTE]
>
>设置详细信息可在[此文档](../../web/using/about-web-forms.md)中找到。
