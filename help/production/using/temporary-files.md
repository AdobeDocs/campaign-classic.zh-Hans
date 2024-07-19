---
product: campaign
title: 临时文件
description: 临时文件
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 4%

---

# 临时文件{#temporary-files}



系统投入生产时，可能会显示如下错误消息（特别是在投放日志中）：

*无法将文件“/tmp/tmp0000.tmp”重命名为/usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ；（errno=18，无效的跨设备链接）(iRc=-52)*

原因如下：

Adobe Campaign在&#x200B;**/tmp**&#x200B;下生成临时文件，然后将其重命名以将其移动到&#x200B;**/usr/local/neolane/nl6/var**。 当两个文件夹（**/tmp**&#x200B;和&#x200B;**/usr/local/neolane/nl6/var**，实际上是指向&#x200B;**/var/nl6**&#x200B;的符号链接）都对应到不同的设备时，会发生此错误。 **df**&#x200B;命令用于验证。

要更正此问题，必须在与目标相同的设备上生成临时文件。

例如，执行以下命令：

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

然后添加：

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
