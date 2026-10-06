---
product: campaign
title: 控制台更新
description: 控制台更新
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
TQID: 'https://experienceleague.adobe.com/oNVXa9DaMu-b-GpfxT-Z0jFbWEd-MnsSzu8Jdb0S0Fw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
  - id: eff19c99-440a-4318-b319-444edc4d8d8f
    internal-label: Upgrade
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%
---
# 控制台更新{#console-update}



如果您选择了&#x200B;**[!UICONTROL Do not request console update]**&#x200B;选项并希望重新激活更新请求，请应用以下过程：

1. 在Windows **[!UICONTROL Start > Execute]**&#x200B;菜单中，使用&#x200B;**regedit**&#x200B;命令打开注册表数据库的编辑器。

   ![](assets/ncs_console_update_1.png)

1. 在树中，显示&#x200B;**[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**&#x200B;节点的选项。
1. 删除&#x200B;**[!UICONTROL confAdvisedUpgrade]**&#x200B;条目并关闭注册表编辑器。

   ![](assets/ncs_console_update_2.png)
