---
product: campaign
title: 网络配置
description: 学习系统通信指南
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 5%

---

# 网络配置{#network-configuration}



## 进程之间的通信 {#communication-between-processes}

应用程序的某些进程需要与他人通信或访问局域网和互联网。 这意味着需要为这些进程打开一些TCP端口。

将嵌入式Apache Tomcat端口用作优先级（默认为8080），用于Adobe Campaign平台各种应用程序服务器之间的内部通信。

### 投放服务器 {#delivery-server}

对于投放服务器(**nlserver mta**)，则以下端口必须打开：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 评论<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> 随处<br /> </td> 
   <td> 用于电子邮件广播的SMTP流量。<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp（域）<br /> </td> 
   <td> DNS服务器<br /> </td> 
   <td> DNS查询。<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp（默认端口）<br /> </td> 
   <td> 短信网关<br /> </td> 
   <td> 用于将短信流量发送到NetSize SMS路由器[option]。<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> 统计服务器<br /> </td> 
   <td> 访问统计信息服务器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 入站邮件 {#inbound-mail}

对于入站邮件恢复流程(**nlserver inMail**)，则以下端口必须打开：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 评论<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp(pop3)<br /> </td> 
   <td> 内部邮件服务器<br /> </td> 
   <td> 用于提取退回消息的POP3流量。<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> 内部邮件服务器<br /> </td> 
   <td> 用于发送未由预定义规则自动处理的剩余退回邮件的SMTP流量。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 应用程序服务器 {#application-server}

对于应用程序服务器(**nlserver web**)，则以下端口必须打开：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 评论<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp(http)<br /> 443/tcp(https)<br /> </td> 
   <td> 随处<br /> </td> 
   <td> HTTP或HTTPS流量（包括可交付性选件的流量）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

当Adobe Campaign平台的多个应用程序服务器需要相互通信时，我们建议使用Apache Tomcat服务器的端口(默认情况下：8080)，而不是Web服务器的HTTP端口，该HTTP端口与重定向模块集成。 这意味着需要在这些服务器之间打开端口。

### 短信投放状态 {#sms-delivery-status}

跟踪短信投放(**nlserver sms**)，则以下端口必须打开：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 评论<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp（默认端口）<br /> </td> 
   <td> 短信网关<br /> </td> 
   <td> 查询由NetSize SMS网关[选项]管理的投放队列状态。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 富客户端 {#rich-client}

对于Adobe Campaign富客户端(**nlclient**)，则以下端口必须打开：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 评论<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p>443/tcp(https)</p><br /> </td> 
   <td> 应用程序服务器<br /> </td> 
   <td> SOAP流量(HTTP)。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 数据库访问 {#database-access}

使用数据库的所有组件都必须能够连接到该数据库。 大多数组件都属于这种情况，但重定向服务器（可单独使用）和瘦Win32客户端(仅使用HTTP（或HTTPS）与应用程序服务器通信)除外。

默认端口如下：

<table> 
 <tbody> 
  <tr> 
   <td> 数据库类型<br /> </td> 
   <td> 端口（默认）<br /> </td> 
   <td> 目标<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> 数据库服务器<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL 服务器</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 外部访问 {#external-access}

此外，某些组件必须可从公共Internet访问，以便能够查看直接从Adobe Campaign执行的电子邮件促销活动。 这意味着需要为组件打开某些端口。

### 重定向服务器 {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> 侦听端口<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 随处可得。 对跟踪链接的每次点击都会在服务器上生成一个HTTP请求。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 外部Web服务器 {#external-web-server}

此服务器托管Web窗体、镜像页面等。 需要打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 侦听端口<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 随处可得。 直接从Adobe Campaign平台管理Web窗体或使用镜像页面时，必需。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 内部应用程序服务器(Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> 侦听端口<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 执行瘦客户机或富客户机的所有计算机。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 与Adobe Experience Manager集成 {#integration-with-adobe-experience-manager}

如果安装是“内部部署”的，则Adobe Campaign与Adobe Experience Manager之间的集成需要打开多个端口。 有关配置此集成的更多信息，请参阅 [详细文档](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> 侦听端口<br /> </td> 
   <td> 说明<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM连接到Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign与AEM“创作”和“发布”实例的连接。 要打开的端口可能与默认端口不同，具体取决于您的AEM配置。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 带宽 {#bandwidth}

要考虑的网络配置的另一个关键参数。 在电子邮件广播期间，它几乎总是叫客，而且需求很大。 以下是一些基于我们经验的配置示例：

* 每小时10,000封电子邮件为1 Mb/s（平均大小为30 Kb）
* 每小时10万封电子邮件为8到10 Mb/s（平均大小为30 Kb）

如果您在带宽方面存在限制，则可以安排营销活动在需求较低的夜晚运行。
