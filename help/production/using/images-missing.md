---
product: campaign
title: 缺少图像
description: 缺少图像
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 11%

---

# 缺少图像{#images-missing}



在17.9版本中，移动了一些文件（尤其是图标）。

对于托管客户没有影响。 对于内部部署安装，请阅读以下内容。

**Apache用户：**

如果Apache用户使用提供的，则不会给他们带来任何影响 **apache_neolane.conf**.

**IIS用户：**

对于IIS用户（在Windows上），在内部版本更新后，控制台中会显示多个图标。 需要其他IIS更新步骤：

1. 内部版本更新后，双击 **iis_neolane_setup.vbs** 位于Campaign安装目录中。 默认路径为C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. 重新启动上一步更新的IIS站点。
