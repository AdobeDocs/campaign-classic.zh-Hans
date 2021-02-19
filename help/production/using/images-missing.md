---
solution: Campaign Classic
product: campaign
title: 缺少图像
description: 缺少图像
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---


# 缺少图像{#images-missing}

在17.9版本中，已移动多个文件（尤其是图标）。

对于托管客户，没有影响。 对于内部部署安装，请阅读以下内容。

**Apache用户：**

如果Apache用户使用提供的&#x200B;**apache_neolane.conf**，则不会对他们造成影响。

**IIS用户：**

对于IIS用户（在Windows上），生成更新后控制台中将显示缺少多个图标。 需要执行其他IIS更新步骤：

1. 在生成更新后，多次单击位于活动安装目录中的&#x200B;**iis_neolane_setup.vbs**。 默认路径为C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. 重新启动已通过上一步更新的IIS站点。
