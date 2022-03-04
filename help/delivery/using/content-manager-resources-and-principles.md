---
product: campaign
title: 内容管理者资源和原则
description: 内容管理器资源和原则
feature: Templates
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 4%

---

# 内容管理者资源和原则{#content-manager-resources-and-principles}

![](../../assets/common.svg)

您需要定义发布模板，其中包含每个内容的转换模板。

内容块以XML文档结构用于数据存储。 编辑界面用于从Adobe Campaign客户端控制台或通过Web浏览器输入内容。 也可以通过捕获XML流或数据库中聚合的数据自动输入内容。

组合XML文档和XSL或JavaScript模板样式表会自动生成各种格式(HTML、文本)的发布模板的投影。

![](assets/d_ncs_content_process.png)

内容配置需要以下资源：

* 数据架构：XML内容结构的描述。 有关更多信息，请参阅 [数据模式](data-schemas.md).
* 数据输入表单：数据输入屏幕的构建。 有关更多信息，请参阅 [输入表单](input-forms.md).
* 图像：数据输入表单中使用的图像。 有关更多信息，请参阅 [映像管理](formatting.md#image-management).
* 样式表：使用XSLT语言设置输出文档的格式。 有关更多信息，请参阅 [格式](formatting.md).
* JavaScript模板：使用JavaScript语言设置输出文档的格式。 有关更多信息，请参阅 [发布模板](publication-templates.md).
* JavaScript代码：用于数据聚合的JavaScript代码。 有关更多信息，请参阅 [聚合器](publication-templates.md#aggregator).
* 发布模板：发布模板的定义。 有关更多信息，请参阅 [发布模板](publication-templates.md).
* 内容：要创建和发布的内容实例。 有关更多信息，请参阅 [使用内容模板](using-a-content-template.md).
