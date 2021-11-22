---
product: campaign
title: 控制台更新
description: 控制台更新
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# 控制台更新{#console-update}

![](../../assets/v7-only.svg)

如果您选择了 **[!UICONTROL Do not request console update]** 选项，并要重新激活更新请求，请应用以下过程：

1. 使用 **regedit** 命令 **[!UICONTROL Start > Execute]** 菜单。

   ![](assets/ncs_console_update_1.png)

1. 在树中，显示 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 节点。
1. 删除 **[!UICONTROL confAdvisedUpgrade]** 并关闭注册表编辑器。

   ![](assets/ncs_console_update_2.png)
