---
product: campaign
title: 关于模板
description: 投放模板快速入门
feature: Delivery Templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 1%

---

# 关于模板{#about-templates}

![](../../assets/common.svg)

投放配置可保存在投放模板中以便重复使用。 模板可以包含投放的完整或部分配置。

可以手动执行投放模板，如本章所述，或根据事件（在设定时间启动，文件到达服务器时启动等）。 投放模板可通过 **[!UICONTROL Resources > Templates > Delivery templates]** 树中的节点。

![](assets/s_user_template_list.png)

模板有两种类型：

1. Adobe Campaign本地投放模板

   不得从系统中删除本机模板。 这些渠道包括每个投放渠道的最小配置。 但是，管理员可以限制某些功能或为用户提供默认值（跟踪激活、发件人电子邮件地址等）。 模板列表中的本机方案以粗体显示。 必须复制这些参数才能对其进行修改。

1. 预定义投放模板

   Adobe Campaign管理员可以创建新投放模板。 它们可由操作员（那些具有适当访问权限的用户）重复使用，或由服务器进程自动重复使用。 例如，您可以配置电子邮件投放模板，当用户使用此模板创建投放时，只需输入文本或HTML内容，然后投放即可；管理员已经定义了其他选项。

>[!NOTE]
>
>可用的模板取决于您的访问权限、实例配置和上下文。 例如，在创建信息服务时，您可以链接确认消息的投放模板：然后，您只能访问其目标映射为订阅映射的模板。 有关更多信息，请参阅 [选择目标映射](selecting-a-target-mapping.md) 和 [服务和订阅](about-services-and-subscriptions.md).
