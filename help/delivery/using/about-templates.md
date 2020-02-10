---
title: 关于模板
seo-title: 关于模板
description: 关于模板
seo-description: null
page-status-flag: never-activated
uuid: 13b5ad3a-aded-43b8-ae4d-c23aa7bc17bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 22e289d0-c33c-4daa-a893-b292e523f30b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 关于模板{#about-templates}

交付配置可保存在交付模板中以便重新使用。 模板可能包含交付的完整或部分配置。

可如本章所述手动执行传送模板，或根据事件（在设定时间启动，文件到达服务器等）执行。 可以通过树中的节点 **[!UICONTROL Resources > Templates > Delivery templates]** 配置交付模板。

![](assets/s_user_template_list.png)

模板有两种类型：

1. Adobe Campaign本机交付模板

   不得从系统中删除本机模板。 它们包括每个交付渠道的最小配置。 但是，管理员可以限制某些功能或为用户提供默认值（跟踪激活、发送者电子邮件地址等）。 本机场景以粗体显示在模板列表中。 要修改它们，必须复制它们。

1. 预定义的交付模板

   Adobe Campaign管理员可以创建新的分发模板。 操作员（具有适当访问权限的操作员）或服务器进程自动重用它们。 例如，您可以配置电子邮件分发模板，当用户使用此模板创建分发时，他只需输入文本或HTML内容，然后发送；其他选项已由管理员定义。

>[!NOTE]
>
>可用的模板取决于您的访问权限、实例配置和上下文。 例如，在创建信息服务时，您可以链接传送模板以发送确认消息：您随后只能访问其目标映射为订阅映射的模板。 有关此功能的详细信息，请参 [阅选择目标映射](../../delivery/using/selecting-a-target-mapping.md)[和关于服务和订阅](../../delivery/using/about-services-and-subscriptions.md)。
