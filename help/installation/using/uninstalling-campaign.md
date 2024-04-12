---
product: campaign
title: 卸载Campaign
description: 了解如何卸载Campaign
feature: Installation
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 2%

---

# 卸载Campaign{#uninstalling-campaign}



>[!CAUTION]
>
>这些步骤将永久卸载Adobe Campaign。 所有数据都将丢失。

**RHEL：**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian：**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows：**

请参阅此 [页面](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). 不要忘记删除Campaign安装文件夹。
