---
product: campaign
title: 内容管理者资源和原则
description: 内容管理者资源和原则
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Templates
role: User, Developer, Data Engineer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 4%

---

# 内容管理者资源和原则{#content-manager-resources-and-principles}


您需要定义一个发布模板，其中包含每个内容的转换模板。

内容块在XML文档中构造用于数据存储。 编辑界面用于从Adobe Campaign客户端控制台或通过Web浏览器输入内容。 通过捕获XML流或聚合到数据库中的数据，也可以自动输入内容。

将XML文档与XSL或JavaScript Template样式表组合在一起将自动生成各种格式(HTML、文本)的发布模板的投影。

![](assets/d_ncs_content_process.png)

内容配置需要以下资源：

* 数据架构： XML内容结构的描述。 有关详细信息，请参见 [数据架构](data-schemas.md).
* 数据输入表单：构建数据输入屏幕。 有关详细信息，请参见 [输入表单](input-forms.md).
* 图像：数据输入表单中使用的图像。 有关详细信息，请参见 [映像管理](formatting.md#image-management).
* 样式表：使用XSLT语言设置输出文档的格式。 有关详细信息，请参见 [格式化](formatting.md).
* JavaScript模板：使用JavaScript语言设置输出文档的格式。 有关详细信息，请参见 [发布模板](publication-templates.md).
* JavaScript代码：用于数据聚合的JavaScript代码。 有关详细信息，请参见 [汇总](publication-templates.md#aggregator).
* 发布模板：发布模板的定义。 有关详细信息，请参见 [发布模板](publication-templates.md).
* 内容：要创建和发布的内容实例。 有关详细信息，请参见 [使用内容模板](using-a-content-template.md).
