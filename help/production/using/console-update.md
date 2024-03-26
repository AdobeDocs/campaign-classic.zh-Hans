---
product: campaign
title: 控制台更新
description: 控制台更新
feature: Monitoring, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 20%

---

# 控制台更新{#console-update}



如果您选择了 **[!UICONTROL Do not request console update]** 选项，并且您希望重新激活更新请求，请应用以下过程：

1. 使用打开注册表数据库的编辑器 **regedit** 命令在Windows中 **[!UICONTROL Start > Execute]** 菜单。

   ![](assets/ncs_console_update_1.png)

1. 在树中，显示 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 节点。
1. 删除 **[!UICONTROL confAdvisedUpgrade]** 输入并关闭注册表编辑器。

   ![](assets/ncs_console_update_2.png)
