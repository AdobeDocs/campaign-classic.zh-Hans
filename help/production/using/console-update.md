---
product: campaign
title: 控制台更新
description: 控制台更新
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
TQID: https://experienceleague.adobe.com/oNVXa9DaMu-b-GpfxT-Z0jFbWEd-MnsSzu8Jdb0S0Fw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 55
ht-degree: 10%

---

# 控制台更新{#console-update}



如果您选择了&#x200B;**[!UICONTROL Do not request console update]**&#x200B;选项并希望重新激活更新请求，请应用以下过程：

1. 在Windows **[!UICONTROL Start > Execute]**&#x200B;菜单中，使用&#x200B;**regedit**&#x200B;命令打开注册表数据库的编辑器。

   ![](assets/ncs_console_update_1.png)

1. 在树中，显示&#x200B;**[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**&#x200B;节点的选项。
1. 删除&#x200B;**[!UICONTROL confAdvisedUpgrade]**&#x200B;条目并关闭注册表编辑器。

   ![](assets/ncs_console_update_2.png)
