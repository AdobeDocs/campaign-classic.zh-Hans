---
product: campaign
title: 卸载 Campaign
description: 了解如何卸载Campaign
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 19%

---

# 卸载 Campaign{#uninstalling-campaign}

![](../../assets/v7-only.svg)

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

请参阅 [页面](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). 不要忘记删除Campaign安装文件夹。
