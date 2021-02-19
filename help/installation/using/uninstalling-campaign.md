---
solution: Campaign Classic
product: campaign
title: 卸载 Campaign
description: 了解如何卸载活动
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 19%

---


# 卸载 Campaign{#uninstalling-campaign}

>[!CAUTION]
>
>这些过程将永久卸载Adobe Campaign。 所有数据都将丢失。

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows：**

请参阅此[页](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version)。 不要忘记删除活动安装文件夹。
