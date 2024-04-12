---
product: campaign
title: 网络配置
description: 学习系统通信准则
feature: Installation, Instance Settings
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 1%

---

# 网络配置{#network-configuration}



## 进程之间的通信 {#communication-between-processes}

某些应用进程需要与他人通信或访问LAN和Internet。 这意味着这些进程需要打开某些TCP端口。

使用嵌入式Apache Tomcat端口作为优先级（默认为8080），在Adobe Campaign平台的各种应用程序服务器之间进行内部通信。

### 投放服务器 {#delivery-server}

对于投放服务器(**nlserver mta**)，必须打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 评论<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> 随处<br /> </td> 
   <td> 用于电子邮件广播的SMTP流量。<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp（域）<br /> </td> 
   <td> DNS服务器<br /> </td> 
   <td> dns查询。<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp （默认端口）<br /> </td> 
   <td> 短信网关<br /> </td> 
   <td> 用于将短信通信发送到NetSize SMS路由器[选项]。<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> 统计服务器<br /> </td> 
   <td> 访问统计服务器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 入站邮件 {#inbound-mail}

对于入站邮件恢复过程(**nlserver inMail**)，必须打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 评论<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> 内部邮件服务器<br /> </td> 
   <td> 用于接收退回消息的POP3流量。<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> 内部邮件服务器<br /> </td> 
   <td> 用于发送未由预定义规则自动处理的剩余退回消息的SMTP流量。<br /> </td> 
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
   <td> 评论<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> 随处<br /> </td> 
   <td> HTTP或HTTPS流量（包括可投放性选件）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

当Adobe Campaign平台的多个应用程序服务器需要相互通信时，我们建议使用Apache Tomcat服务器的端口（默认为8080），而不是使用执行重定向模块集成的Web服务器的HTTP端口的端口。 这意味着需要打开这些服务器之间的端口。

### 短信投放状态 {#sms-delivery-status}

要跟踪短信投放，请执行以下操作(**nlserver sms**)，必须打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 评论<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp （默认端口）<br /> </td> 
   <td> 短信网关<br /> </td> 
   <td> 查询由NetSize SMS网关[选项]管理的投放队列状态。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 富客户端 {#rich-client}

对于Adobe Campaign富客户端(**nlclient**)，必须打开以下端口：

<table> 
 <tbody> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 目标<br /> </td> 
   <td> 评论<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> 应用程序服务器<br /> </td> 
   <td> SOAP流量(HTTP)。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 数据库访问 {#database-access}

使用该数据库的所有组件都必须能够连接到该数据库。 大多数组件都是这种情况，但重定向服务器和精简Win32客户端除外，前者可单独工作，后者仅使用HTTP（或HTTPS）与应用程序服务器通信。

默认端口如下：

<table> 
 <tbody> 
  <tr> 
   <td> 数据库类型<br /> </td> 
   <td> 端口（默认）<br /> </td> 
   <td> 目标<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>oracle</strong><br /> </td> 
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

## 外部访问 {#external-access}

此外，某些组件必须可从公共Internet访问，以便查看直接从Adobe Campaign执行的电子邮件营销活动。 这意味着某些端口需要为组件打开。

### 重定向服务器 {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> 侦听端口<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> 任何地方。 每次单击跟踪的链接时，都会在服务器上生成一个HTTP请求。<br /> </td> 
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
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> 任何地方。 在直接从Adobe Campaign平台管理Web窗体或使用镜像页面时，此变量是必需的。<br /> </td> 
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
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> 执行瘦客户端或富客户端的所有计算机。<br /> </td> 
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
   <td> AEM与Adobe Campaign的连接<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign与AEM“创作”和“发布”实例的连接。 要打开的端口可能与默认端口不同，具体取决于您的AEM配置。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 带宽 {#bandwidth}

要考虑的网络配置的另一个关键参数。 它几乎总是出站，在电子邮件广播中非常受欢迎。 以下是一些基于我们经验的配置示例：

* 1 Mb/s每小时10,000封电子邮件（平均大小为30 Kb）
* 每小时100,000封电子邮件时为8到10 Mb/s（平均大小为30 Kb）

如果您的带宽受到限制，则可以安排在需求较低的夜间运行营销活动。
