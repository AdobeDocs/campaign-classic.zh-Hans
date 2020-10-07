---
title: 设置阶段
seo-title: 设置阶段
description: 设置阶段
seo-description: null
page-status-flag: never-activated
uuid: 4111a805-95ab-4e26-be51-2db1e5c20f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 76174374-af73-4da0-b62b-6979bca0102b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 3%

---


# 设置阶段{#setup-stages}

基本原则是在网站的某些页面中插入Web跟踪标签。

有两种标记：

* **WEB**:此标记会告诉您是否已访问过页面，
* **交易**:操作方式与Web标签类似，但可添加有关所生成业务量的信息，例如（交易金额、购买的物品数量等）。

应用以下步骤来设置这些标记：

1. 确定要跟踪的页面并确定其类型（WEB或事务）。
1. 确定要收集的其他信息，并用此 **信息的描述扩展nms** :webTrackingLog模式。 默认情况下，此模式可以存储每个事务处理的事务处理金额和项目数。
1. 创建Web跟踪标签。 有两种方法可以实现此目的：

   * 在您的Adobe Campaign平台中插入与这些页面对应的URL，然后生成并提取关联的Web跟踪标签(从客户 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 端控制台的节点)。
   * 以“即时创建”模式自己创建Web跟踪标签:与这些页面对应的URL将自动插入您的Adobe Campaign平台。

1. 在要跟踪的页面中静态或动态添加这些标记。

   >[!NOTE]
   >
   >所有WEB类型标记均可添加到站点的页面。 必须动态修改或添加TRANSACTION标记，以包含附加信息（amount、items等）。

**示例**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```

