---
product: campaign
title: Power Booster 和 Power Cluster
description: Power Booster 和 Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---

# Power Booster 和 Power Cluster{#power-booster-and-power-cluster}

![](../../assets/v7-only.svg)

## 概述 {#overview}

Adobe Campaign为您提供了两套预包装的体系结构选项，用于确定部署的尺寸：

* **Power Booster**

   此选项支持与主Adobe Campaign应用程序实例分离的单个其他执行实例。 专用执行实例可以远程或由第三方托管。 实施后，电子邮件执行、跟踪、镜像页面和退件消息会独立于中央应用程序功能进行处理。

* **电源群集**

   此选项支持2到N个群集执行实例，这些实例与主Adobe Campaign应用程序实例相对于给定应用程序去耦。 群集可以远程托管、在分布式部署中托管，也可以由第三方托管。 除了流程隔离的好处之外，Adobe Campaign Power Cluster选项还支持冗余，并使用商品硬件扩展策略，以简化SLA或性能的演变。

![](assets/architectural_options_diagram.png)

## 合格申请 {#eligible-applications}

Power Booster和Power Cluster选项可供以下应用程序使用：

* 营销活动
* 投放
* 消息中心

## 建筑建议矩阵 {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>标准架构</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>电源群集</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件促销活动和出站交互<br /> </td> 
   <td> 每月最多可发送约3000万封电子邮件<br /> </td> 
   <td> 每月3000万到1亿封电子邮件<br /> </td> 
   <td> 每月超过一亿封电子邮件<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务性消息<br /> </td> 
   <td> 每个执行服务器每小时5万次<br /> </td> 
   <td> 每个执行服务器每小时5万次<br /> </td> 
   <td> 每个执行服务器每小时5万次<br /> </td> 
  </tr> 
  <tr> 
   <td> 可用性<br /> </td> 
   <td> 主数据库的<br /> </td> 
   <td> 24/7，执行实例的维护窗口和下载时间除外<br /> </td> 
   <td> 24/7/365服务可能<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全性<br /> </td> 
   <td> 数据集市可从公共互联网访问<br /> </td> 
   <td> 数据集市与面向互联网的正面组件是隔离的<br /> </td> 
   <td> 数据集市与面向互联网的正面组件是隔离的<br /> </td> 
  </tr> 
  <tr> 
   <td> 部署模板<br /> </td> 
   <td> 所有内容都位于一个网站上（可以位于内部部署或云中）<br /> </td> 
   <td> 可在云中执行内部部署营销<br /> </td> 
   <td> 在云中执行内部部署营销；可能在不同的地理位置执行<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 推荐 {#recommendations}

* 执行实例必须专用于服务。 您无法为尚未订阅的服务安装包。 例如，如果您订阅了 **Power Booster** 选项 **消息中心** 服务，您只能安装 **[!UICONTROL Execution of transactional messages]** 包。 请核实您的许可协议。
* 由于专用实例（或群集）是Adobe Campaign实例，因此推荐与主实例相同。 有关更多信息，请参阅 [本文档](../../production/using/foreword.md).
* 要从数据库/硬件组件的角度正确配置实例，请联系Adobe Campaign专业服务部门。
