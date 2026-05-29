---
product: campaign
title: 卸载Campaign
description: 了解如何卸载Campaign
feature: Installation
audience: installation
content-type: reference
hide: true
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
TQID: https://experienceleague.adobe.com/Dm4S9swh30hagUhayZHmaOS3Cjh1U-sWiG7crbI3Ciw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 36
ht-degree: 13%

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

请参见[此页面](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version)。 不要忘记删除Campaign安装文件夹。
