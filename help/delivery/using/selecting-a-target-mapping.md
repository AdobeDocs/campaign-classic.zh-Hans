---
solution: Campaign Classic
product: campaign
title: 选择目标映射
description: 选择目标映射
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 8%

---


# 选择目标映射{#selecting-a-target-mapping}

默认情况下，投放模板目标 **[!UICONTROL Recipients]**。 因此，其目标映射使用nms: **收件人表的字段** 。 Adobe Campaign优惠其他目标映射以供投放根据您的需求使用。

![](assets/delivery_select_mapping.png)

这些映射如下所示：

| 名称 | 使用 | 标准模式 |
|---|---|---|
| 收件人 | 交付到收件人Adobe Campaign库 | nms:收件人 |
| 访客 | 向通过推荐（病毒式营销）或社交网络(Facebook、Twitter)收集用户档案的访客提供。 | mns:访客 |
| 订阅 | 交付给订阅新闻稿等信息服务的收件人 | nms:订阅 |
| 访客订阅 | 交付给订阅访客的信息服务 | nms:visitorSub |
| 服务 | 发布到Twitter帐户或Facebook页面 | nms：服务 |
| 运算符 | 交付给Adobe Campaign运营商 | nms：操作员 |
| 外部文件 | 通过包含投放所需所有信息的文件传送 | 无链接模式，无目标输入 |

>[!NOTE]
>
>您还可以创建新目标映射。 此操作为专家用户保留。 For more information, refer to the [Configuration guide](../../configuration/using/target-mapping.md).
