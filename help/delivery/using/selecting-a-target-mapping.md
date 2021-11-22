---
product: campaign
title: 选择目标映射
description: 选择目标映射
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 8%

---

# 选择目标映射{#selecting-a-target-mapping}

![](../../assets/common.svg)

默认情况下，投放模板定位 **[!UICONTROL Recipients]**. 因此，其目标映射使用 **nms:recipient** 表。 Adobe Campaign为您的投放提供了其他目标映射，可根据您的需求使用。

![](assets/delivery_select_mapping.png)

这些映射如下所示：

| 名称 | 使用 | 标准架构 |
|---|---|---|
| 收件人 | 向Adobe Campaign数据库的收件人传递 | nms:recipient |
| 访客 | 将其用户档案通过反向链接（病毒式营销）或社交网络(例如Facebook、Twitter)收集的访客交付给。 | mns:visitor |
| 订阅 | 向订阅新闻稿等信息服务的收件人发送 | nms:subscription |
| 访客订阅 | 向订阅了信息服务的访客提供 | nms:visitorSub |
| 服务 | 发布到Twitter帐户或Facebook页面 | nms:service |
| 运算符 | 交付给Adobe Campaign运营商 | nms:operator |
| 外部文件 | 通过包含投放所需所有信息的文件进行投放 | 未链接架构，未输入目标 |

>[!NOTE]
>
>您还可以创建新的目标映射。 此操作专家用户专用。 有关更多信息，请参阅 [配置指南](../../configuration/using/target-mapping.md).
