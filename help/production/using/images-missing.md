---
product: campaign
title: 缺少图像
description: 缺少图像
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
TQID: https://experienceleague.adobe.com/GDlcjvzSGP70FlVGHmnhJHsqC3SFG5Y-kQOohR00j8c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 111
ht-degree: 5%

---

# 缺少图像{#images-missing}



在17.9版本中，移动了一些文件（尤其是图标）。

对于托管客户没有影响。 对于内部部署安装，请阅读以下内容。

**Apache用户：**

如果Apache用户使用提供的&#x200B;**apache_neolane.conf**，则不会对其产生任何影响。

**IIS用户：**

对于IIS用户（在Windows上），在内部版本更新后，控制台中会显示多个图标。 需要其他IIS更新步骤：

1. 内部版本更新后，双击Campaign安装目录中的&#x200B;**iis_neolane_setup.vbs**。 默认路径为C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. 重新启动上一步更新的IIS站点。
