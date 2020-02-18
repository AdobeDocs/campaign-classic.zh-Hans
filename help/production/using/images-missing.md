---
title: 图像缺失
seo-title: 图像缺失
description: 图像缺失
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# 图像缺失{#images-missing}

在17.9版本中，已移动多个文件（特别是图标）。

对于托管客户，没有影响。 有关内部部署安装，请阅读以下内容。

**Apache用户：**

如果Apache用户使用提供的 **apache_neolane.conf，则不会对他们造成影响**

**IIS用户：**

对于IIS用户（在Windows上），在构建更新后，控制台中将显示缺少多个图标。 需要执行其他IIS更新步骤：

1. 在构建更新后，双击 **Campaign安装目录中的iis_neolane_setup** .vbs。 默认路径为C:\Program Files (x86)\Adobe\Adobe Campaign v7\tomcat-7\conf
1. 重新启动已通过上一步更新的IIS站点。

