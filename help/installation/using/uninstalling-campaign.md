---
product: campaign
title: 卸载Campaign
description: 了解如何卸载Campaign
feature: Installation
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 18%

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
