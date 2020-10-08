---
title: 内容管理者资源和原则
seo-title: 内容管理者资源和原则
description: 内容管理者资源和原则
seo-description: null
page-status-flag: never-activated
uuid: 3560e392-129a-471d-a211-05481cdda224
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: b22b3abb-6fe5-4f4d-93fc-0d00d426edb6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 8%

---


# 内容管理者资源和原则{#content-manager-resources-and-principles}

您需要定义一个发布模板，其中包含每个内容的转换模板。

在XML文档中构造内容块以进行数据存储。 编辑界面用于从Adobe Campaign客户端控制台或通过Web浏览器输入内容。 也可以通过捕获XML流或数据库中聚集的数据自动输入内容。

将XML文档和XSL或JavaScript模板样式表组合在一起，可自动生成各种格式（HTML、文本）的发布模板投影。

![](assets/d_ncs_content_process.png)

内容配置需要以下资源：

* 数据模式:XML内容结构的描述。 For more on this, refer to [Data schemas](../../delivery/using/data-schemas.md).
* 数据输入表单：数据输入屏幕的构建。 For more on this, refer to [Input forms](../../delivery/using/input-forms.md).
* 图像：数据输入表单中使用的图像。 For more on this, refer to [Image management](../../delivery/using/formatting.md#image-management).
* 样式表：格式设置输出文档。 For more on this, refer to [Formatting](../../delivery/using/formatting.md).
* JavaScript模板：格式化输出文档。 For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* JavaScript代码：用于数据聚合的JavaScript代码。 For more on this, refer to [Aggregator](../../delivery/using/publication-templates.md#aggregator).
* 发布模板:发布模板的定义。 For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* 内容：要创建和发布的内容实例。 有关此内容的详细信息，请 [参阅使用内容模板](../../delivery/using/using-a-content-template.md)。
