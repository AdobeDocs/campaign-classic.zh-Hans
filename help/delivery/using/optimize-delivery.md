---
solution: Campaign Classic
product: campaign
title: 优化消息投放
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 8bf1b5b1a6763cf933d86f2af61b2bb68e870222
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 6%

---


# 优化投放 {#optimize-delivery}

甚至在开始创建投放之前，您可以采取多个操作来保护和优化上游发送过程。

以下部分概述了实现最佳Adobe Campaign配置的最佳实践和建议步骤。 遵循这些做法将最大限度地减少您可能遇到的下游问题。

## 平台性能

几个因素会直接影响服务器性能并降低平台运行速度：

* 个性化元素的数量和类型：电子邮件中的个性化会将每个收件人的数据从数据库中提取出来。 如果存在许多个性化元素，则会增加准备投放所需的数据量。  了解有关[本节](../../delivery/using/about-personalization.md)中个性化的更多信息

* 服务器负载：当营销服务器同时处理许多不同的任务时，它会降低性能。 营销服务器需要协调所有投放的所有传入和传出数据，以确保数据准确、准时。

   **提示**  — 为避免这种情况，请与团队其他成员协调投放的计划以确保获得最佳性能。

* 工作流执行：监控工作流对于避免平台性能问题至关重要。 遵循本文档](../../workflow/using/workflow-best-practices.md#execution-and-performance)中列出的[准则。

* 作为托管客户，您可以使用[性能监控](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html)功能，利用[活动控制面板功能](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html)来监控您的平台。

## 正在检查网络配置{#network-config}

要在处理大量电子邮件时优化投放，并避免被误认为是垃圾邮件发送者，请确保您具有不尝试隐藏服务器标识的合法网络配置。

**提示**:使用与您品牌网站对应的透明发件人地址。例如，旅行社公司管理Valentino酒店连锁。 它拥有其网站的valentino.com域。 为了宣传巴黎的华伦天奴酒店，它使用paris.valentino.com子域。 因此，相关的发件人地址可以是hotel@paris.valentino.com。

## 可交付性管理 {#deliverability-management}

要访问收件人的收件箱而不会弹出邮件或标记为垃圾邮件，您需要提高消息的发送率。

* 什么是可交付性？

   * 它是指决定收件人服务器接受其能力的电子邮件的因素。 ISP(Internet服务提供商)会过滤其标识为垃圾邮件的电子邮件，或阻止图像下载。 如果他们确定某个域发送的电子邮件过多，他们将对从该发件人接收的电子邮件数量设置限制。

   * 在检查电子邮件的可交付性时，您希望重点关注四个主要类别:数据质量、消息和内容、发送基础架构和声誉。 有关此主题的更深入的介绍，请参阅[本节](../../delivery/using/about-deliverability.md)。

* 应用此文档](../../delivery/using/about-deliverability.md)中详细的[建议。

* 请联系您的Adobe代表以获得帮助。

## 隔离管理{#quarantine-management}

保持良好的隔离管理流程符合您的最佳利益。

开始在新平台上发送电子邮件时，您可能会使用列表未完全限定的地址。 如果您发送到无效地址或蜜罐地址（仅为欺骗垃圾邮件发送者而创建的邮箱），这将开始您平台的声誉。 良好的隔离管理流程有助于：保持地址质量，避阻止列表免Internet访问提供商的，并降低错误率，加快投放和吞吐量。

**提示**

* 如果列表的地址无效，Adobe建议将其导入到隔离表中，方法为： **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**。

* 其地址被隔离的收件人在投放分析期间默认会被排除：他们不是目标。 这样可加快投放速度，因为错误率对投放速度有显著的影响。可以隔离电子邮件地址，例如当收件箱已满或地址不存在时。 [了解详情](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign根据返回的错误类型管理错误地址。 如需详细信息，请参阅[此部分](../../delivery/using/understanding-quarantine-management.md)。


* 如果无效地址率过高，某些互联网访问提供商会自动将电子邮件判断为垃圾邮件。因此，隔离可以使您避免被这阻止列表些提供商添加到。

* 隔离管理还将通过排除投放中的错误电话号码，帮助降低短信发送成本。

## 多次参与机制{#double-opt-in}

为了避免向无效地址发送消息、限制不当通信并改善发送者信誉，Adobe建议实施多次选择加入机制以进行订阅后确认。 这有助于确保收件人有意订阅。

[本节](../../web/using/use-cases--web-forms.md)中概述了实现此机制的详细信息。
