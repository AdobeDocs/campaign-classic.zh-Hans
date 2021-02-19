---
solution: Campaign Classic
product: campaign
title: Power Booster 和 Power Cluster
description: Power Booster 和 Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---


# Power Booster 和 Power Cluster{#power-booster-and-power-cluster}

## 概述 {#overview}

Adobe Campaign为您提供了两组预封装的体系结构选项，用于确定部署的尺寸：

* **动力助推器**

   此选项支持与主执行实例应用程序实例分离的单个附加Adobe Campaign。 专用执行实例可以远程或由第三方托管。 实施后，电子邮件执行、跟踪、镜像页面和弹回消息将独立于中央应用程序功能进行处理。

* **电源群集**

   此选项提供对2到N个群集执行实例的支持，这些群集Adobe Campaign与主应用程序实例相对于给定应用程序解耦。 群集可以远程托管、在分布式部署中托管，也可以由第三方托管。 除了流程隔离的好处，Adobe Campaign Power Cluster选项还支持冗余，并使用商品硬件扩展策略，以简化SLA或性能的发展。

![](assets/architectural_options_diagram.png)

## 符合条件的应用程序{#eligible-applications}

以下应用程序可以使用“Power Booster（电源升压）”和“Power Cluster（电源群集）”选项：

* 营销活动
* 投放
* 消息中心

## 架构建议矩阵{#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>标准架构</strong><br /> </td> 
   <td> <strong>动力助推器</strong><br /> </td> 
   <td> <strong>电源群集</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件活动和出站交互<br /> </td> 
   <td> 每月最多可能收到约3000万封电子邮件<br /> </td> 
   <td> 每月3000万到1亿封电子邮件<br /> </td> 
   <td> 每月超过1亿封电子邮件<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务型消息传递<br /> </td> 
   <td> 每个执行服务器每小时50,000<br /> </td> 
   <td> 每个执行服务器每小时50,000<br /> </td> 
   <td> 每个执行服务器每小时50,000<br /> </td> 
  </tr> 
  <tr> 
   <td> 可用性<br /> </td> 
   <td> 主数据库<br /> </td> 
   <td> 24/7,执行实例的维护窗口和下载时间除外<br /> </td> 
   <td> 24/7/365 service possible<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全性<br /> </td> 
   <td> 数据集市可从公共Internet<br />访问 </td> 
   <td> 数据集市与面向Internet的正面组件隔离<br /> </td> 
   <td> 数据集市与面向Internet的正面组件隔离<br /> </td> 
  </tr> 
  <tr> 
   <td> 部署模板<br /> </td> 
   <td> 全部在一个站点上（可以是内部部署或在云中）<br /> </td> 
   <td> 在云中执行内部部署营销<br /> </td> 
   <td> 在云中执行内部营销；可能在不同的geos中执行<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 建议{#recommendations}

* 执行实例必须专用于服务。 无法为尚未订阅的服务安装包。 例如，如果您订阅&#x200B;**消息中心**&#x200B;服务的&#x200B;**Power Booster**&#x200B;选项，则只能在专用执行实例上安装&#x200B;**[!UICONTROL Execution of transactional messages]**&#x200B;包。 请核实您的许可协议。
* 由于专用实例（或群集）是Adobe Campaign实例，因此建议与主实例相同。 有关详细信息，请参阅[此文档](../../production/using/foreword.md)。
* 要从视图库/硬件组件点正确配置实例，请与Adobe Campaign Professional Services联系。

