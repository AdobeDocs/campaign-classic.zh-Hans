---
solution: Campaign Classic
product: campaign
title: 关于模板
description: 关于模板
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
translation-type: tm+mt
source-git-commit: 9237e11edec4114b2bd0932e6128775f36aad27c
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 2%

---


# 关于模板{#about-templates}

投放配置可以保存在投放模板中以便重新使用。 模板可能包含投放的完整或部分配置。

该投放模板可以手动执行，如本章所述，或根据事件（在设定时间启动，文件到达服务器等）。 投放模板可以通过树中的&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;节点进行配置。

![](assets/s_user_template_list.png)

模板有两种类型：

1. Adobe Campaign本机投放模板

   不得从系统中删除本机模板。 它们包括每个投放渠道的最低配置。 但是，管理员可以将某些功能或优惠默认值限制给用户(跟踪激活、发件人电子邮件地址等)。 模板列表中以粗体显示原生场景。 必须重复这些项，才能修改它们。

1. 预定义投放模板

   Adobe Campaign管理员可以创建新投放模板。 操作员（具有适当访问权限的操作员）或服务器进程自动重复使用它们。 例如，您可以配置电子邮件投放模板，当用户使用此模板创建投放时，他只需输入文本或HTML内容，然后发送；其他选项已由管理员定义。

>[!NOTE]
>
>可用的模板取决于您的访问权限、实例配置和上下文。 例如，在创建信息服务时，您可以链接投放模板以发送确认消息：您随后只能访问其目标映射为订阅映射的模板。 有关详细信息，请参阅[选择目标映射](../../delivery/using/selecting-a-target-mapping.md)和[关于服务和订阅](../../delivery/using/about-services-and-subscriptions.md)。
