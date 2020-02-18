---
title: 电源升压器和电源群集
seo-title: 电源升压器和电源群集
description: 电源升压器和电源群集
seo-description: null
page-status-flag: never-activated
uuid: 4d23ed42-a368-4bd6-afaf-48452e253d19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 715d2b69-5b47-4890-8b7d-1dc0a0d4ead8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c25e2a4f2280cdcc61e0522f8235149410b5dacf

---


# 电源升压器和电源群集{#power-booster-and-power-cluster}

## 概述 {#overview}

Adobe Campaign为您提供两组预先打包的架构选项，用于确定部署的尺寸：

* **增力器**

   此选项支持与主Adobe Campaign应用程序实例分离的单个附加执行实例。 专用执行实例可以远程或由第三方托管。 实施后，电子邮件执行、跟踪、镜像页面和弹回消息将独立于中央应用程序功能进行处理。

* **电源群集**

   此选项提供对2到N个群集执行实例的支持，这些实例与Adobe Campaign主应用程序实例相对于给定应用程序脱钩。 群集可以远程托管、在分布式部署中由第三方托管。 除了流程隔离的优势外，Adobe Campaign Power Cluster选项还支持冗余和扩展战略，使用商品硬件简化SLA或性能的演化。

![](assets/architectural_options_diagram.png)

## 符合条件的应用程序 {#eligible-applications}

Power Booster和Power Cluster选项可供以下应用程序使用：

* 营销活动
* 投放
* 消息中心

## 建筑推荐矩阵 {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>标准架构</strong><br /> </td> 
   <td> <strong>增力器</strong><br /> </td> 
   <td> <strong>电源群集</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件营销活动和出站互动<br /> </td> 
   <td> 每月最多约3000万封电子邮件<br /> </td> 
   <td> 每月3000万到1亿封电子邮件<br /> </td> 
   <td> 每月超过1亿封电子邮件<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易消息<br /> </td> 
   <td> 每台执行服务器每小时50,000<br /> </td> 
   <td> 每台执行服务器每小时50,000<br /> </td> 
   <td> 每台执行服务器每小时50,000<br /> </td> 
  </tr> 
  <tr> 
   <td> 可用性<br /> </td> 
   <td> 主数据库的数据库<br /> </td> 
   <td> 24/7，执行实例的维护窗口和下载时间除外<br /> </td> 
   <td> 24/7/365服务可能<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全性<br /> </td> 
   <td> 数据集市可从公共Internet访问<br /> </td> 
   <td> 数据集市与面向Internet的正面组件相分离<br /> </td> 
   <td> 数据集市与面向Internet的正面组件相分离<br /> </td> 
  </tr> 
  <tr> 
   <td> 部署模板<br /> </td> 
   <td> 全部在一个站点上（可以是内部部署或在云中）<br /> </td> 
   <td> 可在云中执行的内部部署营销<br /> </td> 
   <td> 在云中执行内部部署营销；在不同的可能地位执行<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 建议 {#recommendations}

* 执行实例必须专用于服务。 无法为尚未订阅的服务安装包。 例如，如果您订阅了 **Message Center** （消息中心）服务的 **Power Booster** （电源升级）选项，则只能在专用执行实例 **[!UICONTROL Execution of transactional messages]** 上安装该包。 请检查您的许可协议。
* 由于专用实例（或群集）是Adobe Campaign实例，因此推荐与主实例相同。 For more on this, refer to [this document](../../production/using/foreword.md).
* 要从数据库／硬件组件的视角正确配置实例，请与Adobe Campaign Professional services联系。

