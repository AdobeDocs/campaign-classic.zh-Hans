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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---


# 关于模板{#about-templates}

投放配置可保存在投放模板中以便重新使用。 模板可能包含投放的完整或部分配置。

投放模板可以手动执行，如本章所述，或者根据事件（在设定的时间启动，文件到达服务器等）。 投放模板可以通过树 **[!UICONTROL Resources > Templates > Delivery templates]** 中的节点进行配置。

![](assets/s_user_template_list.png)

模板有两种类型：

1. Adobe Campaign本地投放模板

   不得从系统中删除本机模板。 它们包括每个投放渠道的最低配置。 但是，管理员可以将某些功能或优惠默认值限制给用户(跟踪激活、发件人电子邮件地址等)。 本机场景以粗体显示在模板列表。 必须重复它们才能修改它们。

1. 预定义投放模板

   Adobe Campaign管理员可以创建新投放模板。 操作员（具有适当访问权限的操作员）或服务器进程自动重用它们。 例如，您可以配置电子邮件投放模板，当用户使用此模板创建投放时，他只需输入文本或HTML内容，然后发送；其他选项已由管理员定义。

>[!NOTE]
>
>可用的模板取决于您的访问权限、实例配置和上下文。 例如，在创建信息服务时，您可以链接投放模板以发送确认消息：您随后只能访问目标映射为订阅映射的模板。 有关此内容的详细信息，请参 [阅选择目标映射](../../delivery/using/selecting-a-target-mapping.md)[和关于服务和订阅](../../delivery/using/about-services-and-subscriptions.md)。
