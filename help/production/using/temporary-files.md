---
product: campaign
title: 临时文件
description: 临时文件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# 临时文件{#temporary-files}



系统投入生产时，可能会显示如下错误消息（特别是在投放日志中）：

*无法将文件&#39;/tmp/tmp0000.tmp&#39;重命名为/usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ；（errno=18，无效的跨设备链接）(iRc=-52)*

原因如下：

Adobe Campaign在下生成临时文件 **/tmp**，然后重命名它们，以将其移动到 **/usr/local/neolane/nl6/var**. 当两个文件夹(**/tmp** 和 **/usr/local/neolane/nl6/var**，实际上是指向的符号链接 **/var/nl6**)对应于不同的设备。 此 **df** 命令用于验证。

要更正此问题，临时文件必须在与目标相同的设备上生成。

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
