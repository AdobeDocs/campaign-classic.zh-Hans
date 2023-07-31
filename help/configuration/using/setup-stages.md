---
product: campaign
title: 设置阶段
description: 设置阶段
feature: Configuration
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 3%

---

# 设置阶段{#setup-stages}

基本原则是在网站的某些页面中插入Web跟踪标记。

有两种类型的标记：

* **WEB**：此标记会告知您页面是否已被访问，
* **交易**：操作类似于Web标记，但可以添加有关所生成业务量的信息，例如（交易金额、购买的项目数等）。

应用以下步骤来设置这些标记：

1. 标识要跟踪的页面并确定其类型（WEB或事务）。
1. 确定要收集的其他信息，并扩展 **nms：webTrackingLog** 具有此信息说明的架构。 默认情况下，此架构可以存储每笔交易的交易金额和项目数。
1. 创建Web跟踪标记。 可通过两种方式来做到这一点：

   * 将与这些页面对应的URL插入到Adobe Campaign平台中，然后生成并提取关联的Web跟踪标记(从 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 节点)。
   * 在“动态创建”模式下自行创建Web跟踪标记：与这些页面对应的URL将自动插入到您的Adobe Campaign平台中。

1. 在要跟踪的页面中静态或动态添加这些标记。

   >[!NOTE]
   >
   >所有WEB类型的标记都可以按原样添加到网站页面。 必须动态修改或添加交易标记，以包含附加信息（金额、项目等）。

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
