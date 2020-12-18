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

如果您选择了&#x200B;**[!UICONTROL Do not request console update]**&#x200B;选项并且要重新激活更新请求，请应用以下过程：

1. 使用Windows **[!UICONTROL Start > Execute]**&#x200B;菜单中的&#x200B;**regedit**&#x200B;命令打开注册表数据库的编辑器。

   ![](assets/ncs_console_update_1.png)

1. 在树中，显示&#x200B;**[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**&#x200B;节点的选项。
1. 删除&#x200B;**[!UICONTROL confAdvisedUpgrade]**&#x200B;条目并关闭注册表编辑器。

   ![](assets/ncs_console_update_2.png)

