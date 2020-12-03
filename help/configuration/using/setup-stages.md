---
solution: Campaign Classic
product: campaign
title: 设置阶段
description: 设置阶段
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---


# 设置阶段{#setup-stages}

基本原则是在网站的某些页面中插入Web跟踪标签。

有两种标记：

* **WEB**:此标记会告诉您是否已访问过页面，
* **交易**:操作方式与web标签类似，但可添加有关所生成业务量的信息，例如（交易量、购买的物品数量等）。

应用以下步骤来设置这些标记：

1. 确定要跟踪的页面并确定其类型（WEB或事务）。
1. 确定要收集的其他信息，并使用此信息的说明扩展&#x200B;**nms:webTrackingLog**&#x200B;模式。 默认情况下，此模式可以存储每个事务处理的事务处理金额和项目数。
1. 创建Web跟踪标签。 有两种方法可以实现此目的：

   * 在Adobe Campaign平台中插入与这些页面对应的URL，然后生成并提取相关的Web跟踪标签（从客户端控制台的&#x200B;**[!UICONTROL Campaign execution>Resources>Web tracking tags]**&#x200B;节点）。
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

