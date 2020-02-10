---
title: 关于Campaign HTML编辑器
seo-title: 关于Campaign HTML编辑器
description: 关于Campaign HTML编辑器
seo-description: null
page-status-flag: never-activated
uuid: 1b1d392d-4f19-4092-b57d-02051a242675
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 1ffe9f58-7258-4794-a314-524065f8a33b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 关于Campaign HTML编辑器{#about-campaign-html-editor}

数字 **内容编辑器(DCE)** 是HTML内容编辑器，可让您在Adobe Campaign中轻松创建或修改HTML格式的模板或内容。

数字内容编辑器允许您插入页面元素并设置其格式，以及将数据库字段与HTML页面的元素相关联。 默认情况下，在为Web应用程序创建页面时会提供该属性，或在基于其处于活动状态的模板创建分发时提供该属性。

>[!NOTE]
>
>DCE仅允许您执行本节中详细介绍的操作。
>
>如果要添加服务器端JavaScript代码，最好将其添加到个性化基块中。 有关创建和修改个性化基块的详细信息，请参阅 [本页](../../delivery/using/personalization-blocks.md)。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## 内容编辑器常规操作 {#content-editor-general-operation}

本节介绍在Web应用程序框架和交付环境中编辑和上传使用DCE编辑的内容的主要步骤。

一般操作如下：

![](assets/dce_schema.png)

要创建简单的Web应用程序，步骤如下：

* 创建Web应用程序，有关详细信息，请参阅创 [建登陆页面](../../web/using/creating-a-landing-page.md),
* 选择现有内容或从标准模板创建内容，有关详细信息，请参阅模 [板管理](../../web/using/template-management.md),
* 编辑和配置内容，有关详细信息，请参阅编辑 [内容](../../web/using/editing-content.md),
* 发布Web应用程序，有关详细信息，请参阅 [发布内容](../../web/using/creating-a-landing-page.md#step-3---publishing-content)[和本页](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking)。

>[!NOTE]
>
>有关详细说明在Web应用程序框架内实施DCE的完整示例，请参阅 [创建登录页](../../web/using/creating-a-landing-page.md)。

要创建电子邮件分发，步骤如下：

* 从DCE处于活动状态的电子邮件类型模板创建分发，
* 选择现有内容或从标准模板创建内容，
* 编辑和配置在线内容，
* 发送送货，有关详细信息，请参阅 [本节](../../delivery/using/communication-channels.md)。

>[!NOTE]
>
>有关详细说明在电子邮件发送框架内实施DCE的完整示例，请参阅 [此用例](../../web/using/use-case--creating-an-email-delivery.md)。

