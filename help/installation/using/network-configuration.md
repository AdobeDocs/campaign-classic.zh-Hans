---
solution: Campaign Classic
product: campaign
title: 网络配置
description: 学习系统通信指南
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---


# 网络配置{#network-configuration}

## 进程之间的通信{#communication-between-processes}

应用程序的某些进程需要与他人通信或访问LAN和Internet。 这意味着需要为这些进程打开某些TCP端口。

将嵌入式Apache Tomcat端口用作Adobe Campaign平台不同应用程序服务器之间内部通信的优先级（默认为8080）。

### 投放服务器{#delivery-server}

对于投放服务器(**nlserver mta**)，必须打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 注释<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> 电子邮件广播的SMTP通信。<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp(domain)<br /> </td> 
   <td> DNS服务器<br /> </td> 
   <td> DNS查询。<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp（默认端口）<br /> </td> 
   <td> SMS网关<br /> </td> 
   <td> 用于将SMS通信发送到NetSize SMS路由器[option]。<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> 统计服务器<br /> </td> 
   <td> 访问统计服务器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 入站邮件{#inbound-mail}

对于入站邮件恢复进程(**nlserver inMail**)，必须打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 注释<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp(pop3)<br /> </td> 
   <td> 内部邮件服务器<br /> </td> 
   <td> POP3流量以接收跳出消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> 内部邮件服务器<br /> </td> 
   <td> SMTP流量，用于发送未由预定义规则自动处理的剩余弹回邮件。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 应用程序服务器 {#application-server}

对于应用程序服务器(**nlserver web**)，必须打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 注释<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp(http)<br /> 443/tcp(https)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> HTTP或HTTPS通信(包括用于可交付性优惠)。<br /> </td> 
  </tr> 
 </tbody> 
</table>

当某个Adobe Campaign平台的多个应用程序服务器需要相互通信时，我们建议使用Apache Tomcat服务器的端口(默认情况下：8080)，而不是与进行重定向模块集成的Web服务器的HTTP端口。 这意味着需要在这些服务器之间打开端口。

### SMS投放状态{#sms-delivery-status}

要跟踪SMS投放(**nlserver sms**)，必须打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 注释<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp（默认端口）<br /> </td> 
   <td> SMS网关<br /> </td> 
   <td> 查询由NetSize SMS网关[选项]管理的投放队列状态。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 富客户端{#rich-client}

对于Adobe Campaign富客户端(**nlclient**)，必须打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 注释<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p>443/tcp(https)</p><br /> </td> 
   <td> 应用程序服务器<br /> </td> 
   <td> SOAP通信(HTTP)。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 数据库访问{#database-access}

使用数据库的所有组件都必须能够连接到它。 大多数组件都是如此，除了可以单独工作的重定向服务器和仅使用HTTP（或HTTPS）与应用程序服务器通信的瘦Win32客户端。

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
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 外部访问{#external-access}

此外，某些组件必须可从公共Internet访问，以便直接从Adobe Campaign执行的电子邮件活动可以查看。 这意味着某些端口需要为组件打开。

### 重定向服务器{#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> 侦听端口<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 随时随地。 每次点击跟踪的链接都会在服务器上生成一个HTTP请求。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 外部Web服务器{#external-web-server}

此服务器托管Web 窗体、镜像页面等。 需要打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 侦听端口<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 随时随地。 从Web 窗体平台直接管理Adobe Campaign或使用镜像页面时必需。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 内部应用程序服务器(Web){#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> 侦听端口<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 执行瘦客户端或富客户端的所有计算机。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 与Adobe Experience Manager {#integration-with-adobe-experience-manager}集成

如果安装是“内部部署”，则Adobe Campaign与Adobe Experience Manager之间的集成需要打开多个端口。 有关配置此集成的详细信息，请参阅[详细文档](../../integrations/using/about-adobe-experience-manager.md)。

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

## 带宽{#bandwidth}

要考虑的网络配置的另一个关键参数。 在电子邮件广播期间，它几乎总是对外发布，需求很大。 以下是一些基于我们经验的配置示例：

* 每小时10,000封电子邮件需要1 Mb/s（平均大小为30 Kb）
* 每小时100,000封电子邮件需要8到10 Mb/s（平均大小为30 Kb）

如果您在带宽方面有限制，则可以在需求较低的夜晚计划活动运行。
