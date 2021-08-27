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

如果您选择了&#x200B;**[!UICONTROL Do not request console update]**&#x200B;选项，并且希望重新激活更新请求，请应用以下过程：

1. 使用Windows **[!UICONTROL Start > Execute]**&#x200B;菜单中的&#x200B;**regedit**&#x200B;命令打开注册表数据库的编辑器。

   ![](assets/ncs_console_update_1.png)

1. 在树中，显示&#x200B;**[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**&#x200B;节点的选项。
1. 删除&#x200B;**[!UICONTROL confAdvisedUpgrade]**&#x200B;条目并关闭注册表编辑器。

   ![](assets/ncs_console_update_2.png)
