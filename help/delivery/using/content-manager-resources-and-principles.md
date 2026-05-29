---
product: campaign
title: 内容管理者资源和原则
description: 内容管理者资源和原则
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Templates
role: User, Developer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
TQID: https://experienceleague.adobe.com/xWBOrnm4v7N3XOVvOcPNqngz0cDvvT39tI3xJVKdFZg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: ce44533e-8ec8-4e11-a9e9-78b0fe561832
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 247
ht-degree: 4%

---

# 内容管理者资源和原则{#content-manager-resources-and-principles}


您需要定义一个发布模板，其中包含每个内容的转换模板。

内容块在XML文档中构造用于数据存储。 编辑界面用于从Adobe Campaign客户端控制台或通过Web浏览器输入内容。 通过捕获XML流或聚合到数据库中的数据，也可以自动输入内容。

组合XML文档和XSL或JavaScript模板样式表将自动生成各种格式（HTML、文本）的发布模板的投影。

![](assets/d_ncs_content_process.png)

内容配置需要以下资源：

* 数据架构： XML内容结构的描述。 有关详细信息，请参阅[数据架构](data-schemas.md)。
* 数据输入表单：构建数据输入屏幕。 有关详细信息，请参阅[输入表单](input-forms.md)。
* 图像：数据输入表单中使用的图像。 有关详情，请参阅[映像管理](formatting.md#image-management)。
* 样式表：使用XSLT语言设置输出文档的格式。 有关详细信息，请参阅[格式化](formatting.md)。
* JavaScript模板：使用JavaScript语言设置输出文档的格式。 有关详细信息，请参阅[发布模板](publication-templates.md)。
* JavaScript代码：用于数据聚合的JavaScript代码。 有关详细信息，请参阅[汇总](publication-templates.md#aggregator)。
* 发布模板：发布模板的定义。 有关详细信息，请参阅[发布模板](publication-templates.md)。
* 内容：要创建和发布的内容实例。 有关详细信息，请参阅[使用内容模板](using-a-content-template.md)。
