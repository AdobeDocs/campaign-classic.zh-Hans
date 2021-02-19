---
solution: Campaign Classic
product: campaign
title: 内容管理者资源和原则
description: 内容管理者资源和原则
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 6%

---


# 内容管理者资源和原则{#content-manager-resources-and-principles}

您需要定义一个发布模板，其中包含每个内容的转换模板。

内容块以XML文档结构化以用于数据存储。 编辑界面用于从Adobe Campaign客户端控制台或通过Web浏览器输入内容。 也可以通过捕获XML流或数据库中聚集的数据自动输入内容。

将XML文档与XSL或JavaScript模板样式表组合在一起，会自动生成各种格式（HTML、文本）的发布模板投影。

![](assets/d_ncs_content_process.png)

内容配置需要以下资源：

* 数据模式:XML内容结构的描述。 有关详细信息，请参阅[数据模式](../../delivery/using/data-schemas.md)。
* 数据输入表单：构建数据输入屏幕。 有关详细信息，请参阅[输入表单](../../delivery/using/input-forms.md)。
* 图像：数据输入表单中使用的图像。 有关详细信息，请参阅[映像管理](../../delivery/using/formatting.md#image-management)。
* 样式表：格式设置输出文档。 有关详细信息，请参阅[格式](../../delivery/using/formatting.md)。
* JavaScript模板：设置输出文档的格式。 有关详细信息，请参阅[发布模板](../../delivery/using/publication-templates.md)。
* JavaScript代码：用于数据聚合的JavaScript代码。 有关详细信息，请参阅[聚合器](../../delivery/using/publication-templates.md#aggregator)。
* 发布模板:发布模板的定义。 有关详细信息，请参阅[发布模板](../../delivery/using/publication-templates.md)。
* 内容：要创建和发布的内容实例。 有关详细信息，请参阅[使用内容模板](../../delivery/using/using-a-content-template.md)。
