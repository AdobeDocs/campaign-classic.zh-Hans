---
product: campaign
title: 设置阶段
description: 设置阶段
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# 设置阶段{#setup-stages}

![](../../assets/v7-only.svg)

基本原则是在网站的某些页面中插入Web跟踪标记。

标记有两种类型：

* **WEB**:此标记可告知您是否已访问页面，
* **交易**:操作类似于web标记，但可能会添加有关所生成业务量的信息，例如（交易金额、购买的项目数等）。

应用以下步骤以设置这些标记：

1. 确定要跟踪的页面并确定其类型（WEB或TRANSACTION）。
1. 确定您要收集的其他信息，并扩展&#x200B;**nms:webTrackingLog**&#x200B;模式，其中包含此信息的描述。 默认情况下，此架构可以存储每个交易的交易金额和项目数。
1. 创建Web跟踪标记。 可以通过两种方式来执行此操作：

   * 在Adobe Campaign平台中插入与这些页面对应的URL，然后生成并提取关联的Web跟踪标记（从客户端控制台的&#x200B;**[!UICONTROL Campaign execution>Resources>Web tracking tags]**&#x200B;节点）。
   * 自行在“即时创建”模式下创建Web跟踪标记：与这些页面对应的URL将自动插入到您的Adobe Campaign平台中。

1. 在要跟踪的页面中静态或动态添加这些标记。

   >[!NOTE]
   >
   >所有WEB类型标记均可按原样添加到您网站的页面。 必须动态修改或添加交易标记，以包含附加信息（金额、项目等）。

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
