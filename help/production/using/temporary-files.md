---
title: 临时文件
seo-title: 临时文件
description: 临时文件
seo-description: null
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# 临时文件{#temporary-files}

如果系统投入生产时出现以下错误消息（尤其是在交付日志中）:

**无法将文件“/tmp/tmp0000.tmp”重命名为/usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link)(iRc=-52)**

原因如下：

Adobe Campaign在 **/tmp下生成临时文件**，然后重命名这些文件以将其移至 **/usr/local/neolane/nl6/var**。 当两个文件夹(**/tmp** and **/usr/local/neolane/nl6/var**，实际上是指向 ****/var/nl6的符号链接)对应于不同的设备时，会发生此错误。 df **命令** ，用于验证。

要解决此问题，必须在与目标相同的设备中生成临时文件。 例如，通过执行：

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

然后添加：

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

