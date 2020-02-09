---
title: 关于Adobe Campaign Classic数据模型
description: 本文档介绍了Adobe Campaign Classic数据模型的基础知识。
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2ce2a1a55e244180a4e62d6f3b5a5ed5bb8aff6e

---


# 关于Campaign Classic数据模型{#about-data-model}

本节介绍Adobe Campaign Classic数据模型的基础知识，以便更好地了解Campaign内置表及其交互。

Adobe Campaign数据库的概念数据模型由一组内置表及其交互组成。

要访问每个表的说明，请转到 **[!UICONTROL Admin > Configuration > Data schemas]**，从列表中选择一个资源，然后单击选 **[!UICONTROL Documentation]** 项卡。

![](assets/data-model_documentation-tab.png)

有关默认营销活动经典数据模型描述的详细信息，请参阅此 [文档](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html)。

XML描述了应用程序中所承载数据的物理和逻辑结构。 它遵循Adobe Campaign特有的语法（称为架构）。 有关Adobe Campaign架构的更多信息，请阅读此 [部分](../../configuration/using/about-schema-reference.md)。

## 概述 {#data-model-overview}

Adobe Campaign依赖于包含链接在一起的表的关系数据库。

Adobe Campaign数据模型的基本结构可以如下所述。

## 收件人表 {#recipient-table}

数据模型依赖于主表，该主表默认为“收件人”表(**NmsRecipient**)。 此表可存储所有营销配置文件。

有关“收件人”表格的详细信息，请参阅此 [部分](../../configuration/using/default-recipient-table.md)。

## 传送表 {#delivery-table}

数据模型还包括专用于存储所有营销活动的部件。 通常，它是“交付”表(**NmsDelivery**)。 此表中的每条记录都表示一个交付操作或一个交付模板。 它包含执行目标、内容等交付所需的所有参数。

## 日志表 {#log-tables}

数据模型的另一部分允许临时存储与执行营销活动相关的所有日志。

交付日志是所有渠道中发送给收件人或设备的所有消息。 主“交付日志”表(**NmsBroadLog**)包含所有收件人的交付日志。
主“跟踪日志”表(**NmsTrackingLog**)存储所有收件人的跟踪日志。 跟踪日志是指收件人的反应，如电子邮件打开次数和点击次数。 每个反应都对应一个跟踪日志。
交付日志和跟踪日志在特定时间段后被删除，该时间段在Adobe Campaign中指定，并可以修改。 因此，强烈建议定期导出日志。

## 技术表 {#technical-tables}

最后，部分数据模型包含用于应用程序过程的技术数据，包括操作员和用户权限(**NmsGroup**)、文件夹(**XtkFolder**)。