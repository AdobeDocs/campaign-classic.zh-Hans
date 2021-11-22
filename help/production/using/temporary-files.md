---
product: campaign
title: 临时文件
description: 临时文件
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# 临时文件{#temporary-files}

![](../../assets/v7-only.svg)

在系统投入生产时，可能会显示以下错误消息（尤其是在投放日志中）：

*无法将文件“/tmp/tmp0000.tmp”重命名为/usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link)(iRc=-52)*

原因如下：

Adobe Campaign在 **/tmp**，然后将其重命名为 **/usr/local/neolane/nl6/var**. 当两个文件夹(**/tmp** 和 **/usr/local/neolane/nl6/var**，实际上是 **/var/nl6**)对应于不同的设备。 的 **df** 命令进行验证。

要更正此问题，临时文件必须在与目标相同的设备中生成。

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
