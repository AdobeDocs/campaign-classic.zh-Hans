---
product: campaign
title: Power Booster 和 Power Cluster
description: Power Booster 和 Power Cluster
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 6%

---

# Power Booster 和 Power Cluster{#power-booster-and-power-cluster}



## 概述 {#overview}

Adobe Campaign为您提供两组预打包的架构选项，用于定义部署的维度：

* **Power Booster**

  此选项支持与主Adobe Campaign应用程序实例分离的单个附加执行实例。 专用执行实例可以远程托管，也可以由第三方托管。 实施后，电子邮件执行、跟踪、镜像页面和退回消息将与中央应用程序功能分开处理。

* **电源群集**

  此选项支持与主Adobe Campaign应用程序实例脱钩的2到N个群集执行实例与给定应用程序的关系。 群集可以远程托管、在分布式部署中托管，也可以由第三方托管。 除了流程隔离的好处外，Adobe Campaign电源群集选项还支持使用商品化硬件的冗余和横向扩展策略，以简化SLA或性能的演变。

![](assets/architectural_options_diagram.png)

## 符合条件的应用程序 {#eligible-applications}

Power Booster和Power Cluster选项可用于以下应用程序：

* 营销活动
* 投放
* 消息中心

## 体系结构建议矩阵 {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>标准架构</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>电源群集</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件营销活动和出站交互<br /> </td> 
   <td> 每月最多可发送约3000万封电子邮件<br /> </td> 
   <td> 每月3000万到1亿封电子邮件<br /> </td> 
   <td> 每月超过1亿封电子邮件<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务性消息<br /> </td> 
   <td> 每个执行服务器<br />每小时50,000次 </td> 
   <td> 每个执行服务器<br />每小时50,000次 </td> 
   <td> 每个执行服务器<br />每小时50,000次 </td> 
  </tr> 
  <tr> 
   <td> 可用性<br /> </td> 
   <td> 主数据库<br />的 </td> 
   <td> 执行实例<br />的维护时段和停机时间是全天候的，但维护时段和停机时间除外 </td> 
   <td> 24/7/365服务可能<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全性<br /> </td> 
   <td> 可以从公共Internet访问数据市场<br /> </td> 
   <td> 数据集市与面向Internet的前端组件隔离<br /> </td> 
   <td> 数据集市与面向Internet的前端组件隔离<br /> </td> 
  </tr> 
  <tr> 
   <td> 部署模板<br /> </td> 
   <td> 全部位于一个站点上（可以是内部部署或在云中）<br /> </td> 
   <td> 可在云中执行的内部部署营销<br /> </td> 
   <td> 在云中执行的内部部署营销；可能以不同的地理位置执行<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 推荐做法 {#recommendations}

* 执行实例必须专用于服务。 您无法为尚未订阅的服务安装包。 例如，如果您订阅&#x200B;**消息中心**&#x200B;服务的&#x200B;**Power Booster**&#x200B;选项，则只能在专用执行实例上安装&#x200B;**[!UICONTROL Execution of transactional messages]**&#x200B;包。 请核实您的许可协议。
* 由于专用实例（或集群）是Adobe Campaign实例，因此建议案与主实例的建议案相同。 有关详细信息，请参阅[本文档](../../production/using/foreword.md)。
* 要从数据库/硬件组件角度正确配置实例，请联系Adobe Campaign专业服务。
