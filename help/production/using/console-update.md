---
product: campaign
title: 控制台更新
description: 控制台更新
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# 控制台更新{#console-update}



如果您选择了 **[!UICONTROL Do not request console update]** 选项，并要重新激活更新请求，请应用以下过程：

1. 使用 **regedit** 命令 **[!UICONTROL Start > Execute]** 菜单。

   ![](assets/ncs_console_update_1.png)

1. 在树中，显示 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 节点。
1. 删除 **[!UICONTROL confAdvisedUpgrade]** 并关闭注册表编辑器。

   ![](assets/ncs_console_update_2.png)
