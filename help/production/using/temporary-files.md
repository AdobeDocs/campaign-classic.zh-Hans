---
solution: Campaign Classic
product: campaign
title: 临时文件
description: 临时文件
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---


# 临时文件{#temporary-files}

在系统投入生产时，可能会显示以下错误消息(特别是投放日志):

*无法将文件“/tmp/tmp0000.tmp”重命名为/usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link)(iRc=-52)*

原因如下：

Adobe Campaign在&#x200B;**/tmp**&#x200B;下生成临时文件，然后重命名这些文件将其移动到&#x200B;**/usr/local/neolane/nl6/var**。 当两个文件夹（**/tmp**&#x200B;和&#x200B;**/usr/local/neolane/nl6/var**）对应于不同设备时，会发生此错误。 ******df**&#x200B;命令用于验证。

要解决此问题，必须在与目标相同的设备中生成临时文件。

例如，执行以下操作：

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

然后添加：

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
