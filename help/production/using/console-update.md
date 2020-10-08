---
title: 控制台更新
seo-title: 控制台更新
description: 控制台更新
seo-description: null
page-status-flag: never-activated
uuid: d2193d4f-b98c-47b1-88f1-7e5ccf4c453c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 9281808b-1c2f-4095-9051-f181f089f205
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '57'
ht-degree: 14%

---


# 控制台更新{#console-update}

如果您选择了该 **[!UICONTROL Do not request console update]** 选项并且希望重新激活更新请求，请应用以下过程：

1. 使用Windows菜单中的regedit命令打 **开注册** 表数据库的 **[!UICONTROL Start > Execute]** 编辑器。

   ![](assets/ncs_console_update_1.png)

1. 在树中，显示节点的选 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 项。
1. 删除该条 **[!UICONTROL confAdvisedUpgrade]** 目并关闭注册表编辑器。

   ![](assets/ncs_console_update_2.png)

