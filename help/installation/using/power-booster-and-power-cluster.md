---
product: campaign
title: Power Booster 和 Power Cluster
description: Power Booster 和 Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---

# Power Booster 和 Power Cluster{#power-booster-and-power-cluster}

## 概述 {#overview}

Adobe Campaign为您提供了两套预包装的体系结构选项，用于确定部署的尺寸：

* **Power Booster**

   此选项支持与主Adobe Campaign应用程序实例分离的单个其他执行实例。 专用执行实例可以远程或由第三方托管。 实施后，电子邮件执行、跟踪、镜像页面和退件消息会独立于中央应用程序功能进行处理。

* **电源群集**

   此选项支持2到N个群集执行实例，这些实例与主Adobe Campaign应用程序实例相对于给定应用程序去耦。 群集可以远程托管、在分布式部署中托管，也可以由第三方托管。 除了流程隔离的好处之外，Adobe Campaign Power Cluster选项还支持冗余，并使用商品硬件扩展策略，以简化SLA或性能的演变。

![](assets/architectural_options_diagram.png)

## 符合条件的应用程序{#eligible-applications}

Power Booster和Power Cluster选项可供以下应用程序使用：

* 营销活动
* 投放
* 消息中心

## 体系结构建议矩阵{#matrix-of-architectural-recommendations}

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
   <td> 每月最多可能收到约3000万封电子邮件<br /> </td> 
   <td> 每月3000万到1亿封电子邮件<br /> </td> 
   <td> 每月超过1亿封电子邮件<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务性消息<br /> </td> 
   <td> 每个执行服务器每小时50,000个<br /> </td> 
   <td> 每个执行服务器每小时50,000个<br /> </td> 
   <td> 每个执行服务器每小时50,000个<br /> </td> 
  </tr> 
  <tr> 
   <td> 可用性<br /> </td> 
   <td> 主数据库的数据库<br /> </td> 
   <td> 24/7除维护窗口和执行实例的下载时间外<br /> </td> 
   <td> 24/7/365 service posible<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全性<br /> </td> 
   <td> 数据集市可从公共Internet访问<br /> </td> 
   <td> 数据集市与面向互联网的正面组件隔离<br /> </td> 
   <td> 数据集市与面向互联网的正面组件隔离<br /> </td> 
  </tr> 
  <tr> 
   <td> 部署模板<br /> </td> 
   <td> 所有内容都位于一个网站上（可以位于内部部署或云中）<br /> </td> 
   <td> 可在云中执行内部部署营销<br /> </td> 
   <td> 在云中执行内部部署营销；可能执行不同的geos<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 建议 {#recommendations}

* 执行实例必须专用于服务。 您无法为尚未订阅的服务安装包。 例如，如果订阅了&#x200B;**消息中心**&#x200B;服务的&#x200B;**Power Booster**&#x200B;选项，则只能在专用执行实例上安装&#x200B;**[!UICONTROL Execution of transactional messages]**&#x200B;包。 请核实您的许可协议。
* 由于专用实例（或群集）是Adobe Campaign实例，因此推荐与主实例相同。 有关更多信息，请参见[本文档](../../production/using/foreword.md)。
* 要从数据库/硬件组件的角度正确配置实例，请联系Adobe Campaign专业服务部门。
