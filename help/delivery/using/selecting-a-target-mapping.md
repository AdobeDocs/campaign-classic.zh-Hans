---
title: 选择目标映射
seo-title: 选择目标映射
description: 选择目标映射
seo-description: null
page-status-flag: never-activated
uuid: 29a666a3-2ecc-4732-b068-c93935929771
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: e2c6e273-1640-4f46-a80e-0cecb06e2769
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 选择目标映射{#selecting-a-target-mapping}

默认情况下，交付模板为目标 **[!UICONTROL Recipients]**。 因此，他们的目标映射使用 **nms:recipient表的字段** 。 Adobe Campaign为您的分发提供了其他目标映射，以根据您的需求使用。

![](assets/delivery_select_mapping.png)

这些映射如下所示：

| 名称 | 使用 | 标准架构 |
|---|---|---|
| 收件人 | 交付给Adobe Campaign数据库的收件人 | nms：收件人 |
| 访客 | 向通过推荐（病毒式营销）或社交网络(Facebook、Twitter)收集其个人资料的访客提供。 | mns:visitor |
| 订阅 | 向订阅新闻快讯等信息服务的收件人传送 | nms：订阅 |
| 访客订阅 | 为订阅信息服务的访客提供 | nms:visitorSub |
| 服务 | 发布到Twitter帐户或Facebook页面 | nms:service |
| 运营商 | 交付给Adobe Campaign运营商 | nms:operator |
| 外部文件 | 通过包含交付所需所有信息的文件进行交付 | 没有链接的架构，没有输入目标 |

>[!NOTE]
>
>您还可以创建新的目标映射。 此操作为专家用户保留。 有关详细信息，请参阅配 [置指南](../../configuration/using/target-mapping.md)。
