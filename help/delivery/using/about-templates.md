---
product: campaign
title: 关于模板
description: 投放模板入门
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Delivery Templates
role: User
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 1%

---

# 关于模板{#about-templates}

投放配置可以保存在投放模板中以便重复使用。 模板可能包含投放的完整或部分配置。

可以按照本章所述或根据事件（在设置时间启动、在文件到达服务器时启动等）手动执行投放模板。 投放模板可通过以下方式配置 **[!UICONTROL Resources > Templates > Delivery templates]** 树中的节点。

![](assets/s_user_template_list.png)

模板有两种类型：

1. Adobe Campaign本机投放模板

   不得从系统中删除本机模板。 它们包括每个投放渠道的最低配置。 但是，管理员可以限制某些功能，或为用户提供默认值（跟踪激活、发件人电子邮件地址等）。 本机方案在模板列表中以粗体显示。 必须复制它们才能修改它们。

1. 预定义的投放模板

   Adobe Campaign管理员可以创建新的投放模板。 操作员（拥有适当访问权限的用户）可重复使用这些变量，服务器进程也可自动使用这些变量。 例如，您可以配置电子邮件投放模板，当用户使用此模板创建投放时，他们只需输入文本或HTML内容即可投放；管理员已定义其他选项。

>[!NOTE]
>
>可用的模板取决于您的访问权限、实例配置和上下文。 例如，在创建信息服务时，可以链接确认消息的投放模板：然后只能访问其目标映射为订阅映射的模板。 有关详细信息，请参见 [选择目标映射](selecting-a-target-mapping.md) 和 [服务和订阅](about-services-and-subscriptions.md).
