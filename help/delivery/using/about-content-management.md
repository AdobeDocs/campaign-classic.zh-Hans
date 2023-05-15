---
product: campaign
title: 关于内容管理
description: Campaign内容管理器模块快速入门
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Landing Pages, Email Design
exl-id: 87434cc2-1636-4558-ab60-255b7f873c0c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 2%

---

# 关于内容管理{#about-content-management}



Adobe Campaign内容管理器模块是一个特定的Campaign Classic [内置包](../../installation/using/installing-campaign-standard-packages.md) 可安装以创建定期新闻稿或网站的信息。 它可以帮助您创建、验证和发布消息。

>[!NOTE]
>
>本节将介绍内容管理模块。 有关如何设计电子邮件投放内容的更多信息，请参阅 [此部分](defining-the-email-content.md).

内容管理模块整合了工作组、工作流和内容聚合功能。 这允许自动设置消息的格式：电子邮件、邮件、短信、Web等

通过在投放中使用内容管理器，您可以为负责内容创建的操作员提供输入或选择字段。 此内容的布局和显示以及所做的任何更改均使用样式表自动进行管理。

![](assets/s_ncs_content_create_content_sample.png)

>[!CAUTION]
>
>对样式表所做的所有更改均基于所用的内容模板在交付级别实施。

内容管理具有以下优势：

* 通过输入接口进行结构化消息编辑，
* 数据内容及其呈现方式的分离（以XML格式生成），
* 以多种格式（html、txt、XML等）生成文档 基于样式表，以确保符合图形包，
* 恢复和自动汇总外部内容流，
* 与工作流协作以进行数据验证和检查。

但是，这种内容创建模式确实涉及一些限制；特别包括：

* 对最终文件设计的自由有限，
* 对要求的分析必须严格，这样最终用户就不会因为功能缺失而不便。
