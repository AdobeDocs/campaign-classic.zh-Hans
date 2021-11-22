---
product: campaign
title: 缺少图像
description: 缺少图像
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---

# 缺少图像{#images-missing}

![](../../assets/v7-only.svg)

在17.9版本中，多个文件（尤其是图标）已被移动。

对于托管客户，没有影响。 对于内部部署安装，请阅读以下内容。

**Apache用户：**

如果Apache用户使用提供的，则这对他们没有影响 **apache_neolane.conf**.

**IIS用户：**

对于IIS用户（在Windows上），在内部版本更新后，控制台中将缺少几个图标。 需要执行其他IIS更新步骤：

1. 更新内部版本后，双击 **iis_neolane_setup.vbs** 位于Campaign安装目录中。 默认路径为C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. 重新启动上一步中已更新的IIS站点。
