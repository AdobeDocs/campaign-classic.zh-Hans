---
solution: Campaign Classic
product: campaign
title: 控制台更新
description: 控制台更新
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---


# 控制台更新{#console-update}

如果您选择了该 **[!UICONTROL Do not request console update]** 选项并且希望重新激活更新请求，请应用以下过程：

1. 使用Windows菜单中的regedit命令打 **开注册** 表数据库的 **[!UICONTROL Start > Execute]** 编辑器。

   ![](assets/ncs_console_update_1.png)

1. 在树中，显示节点的选 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 项。
1. 删除该条 **[!UICONTROL confAdvisedUpgrade]** 目并关闭注册表编辑器。

   ![](assets/ncs_console_update_2.png)

