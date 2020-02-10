---
title: 一般架构
seo-title: 一般架构
description: 一般架构
seo-description: null
page-status-flag: never-activated
uuid: 686bc660-2403-4bab-a4ea-9b872adf8fa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 7c28c179-eb18-437e-baf2-25829566c766
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 一般架构{#general-architecture}

典型的Adobe Campaign解决方案部署包括以下组件：

* **个性化的客户端环境**

   直观的图形界面，用户可在该界面中交流和跟踪营销推广信息、创建营销活动、审查和管理所有营销活动、计划和计划（包括电子邮件、工作流和登录页面）、创建和管理客户档案以及定义客户受众类型。

* **开发环境**

   服务器端软件，它根据用户界面中定义的规则和工作流，通过选定的通信渠道（包括电子邮件、短信、推送通知、直邮、Web或社交）执行营销活动。

* **数据库容器**

   基于关系数据库技术，Adobe Campaign数据库将所有客户信息、营销活动组件、优惠和工作流以及营销活动结果存储在客户数据库容器中。

Adobe Campaign基于面向服务的体系架构(SOA)，包括多个功能模块。 这些模块可以部署在一个或多个计算机上，在单个或多个实例中，具体取决于可伸缩性、可用性和服务隔离方面的限制。 因此，部署配置的范围非常广泛，并且跨单个中央计算机到包括多个站点上的多个专用服务器的配置。

>[!NOTE]
>
>作为软件供应商，我们指定了兼容的硬件和软件基础结构。 此处提供的硬件建议仅供参考，并基于我们的经验。 Adobe不对根据这些决定作出的任何决定负责。 它还取决于您的业务规则和实践，以及项目的关键程度和所需的性能级别。

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>如果没有明确说明，则Adobe Campaign平台的所有组件上的安装、更新和维护由托管这些组件的计算机管理员负责。 这包括实施Adobe Campaign应用程序的先决条件，以及遵守组件之间 [的兼容性表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) 。

## 表示层 {#presentation-layer}

根据用户的需求，可以通过不同的方式访问应用程序：富客户端、瘦客户端或API集成。

* **富客户端**:应用程序的主用户界面是富客户端，换句话说，是仅与Adobe Campaign应用程序服务器通信的标准Internet协议（SOAP、HTTP等）的本机应用程序(Windows)。 此控制台为工作效率提供了极好的用户友好性，使用很少的带宽（通过使用本地缓存），并且设计为便于部署。 此控制台可以从因特网浏览器部署，可以自动更新，并且不需要任何特定的网络配置，因为它只生成HTTP(S)通信。
* **瘦客户端**:应用程序的某些部分可以使用HTML用户界面通过简单的Web浏览器访问，包括报告模块、交付批准阶段、分布式营销模块的功能（中央／本地）、实例监控等。 通过此模式，可以在内部网或外部网中包含Adobe Campaign功能。
* **通过API进行集成**:在某些情况下，可以使用通过SOAP协议公开的Web服务API从外部应用程序调用系统。

## 逻辑应用层 {#logical-application-layer}

Adobe Campaign是一个具有不同应用程序的平台，这些应用程序结合在一起可创建开放、可扩展的架构。 Adobe Campaign平台编写在灵活的应用程序层上，可轻松配置以满足公司的业务需求。 这从功能和技术角度满足了企业日益增长的需求。 分布式架构确保了线性系统可伸缩性，从数千条消息扩展到数百万条消息。

Adobe Campaign依靠一组可协同工作的服务器端流程。

主要流程有：

**应用程序服务器** (nlserver web)

此过程通过Web服务API(SOAP - HTTP + XML)显示Adobe Campaign的所有功能。 此外，它还可以动态生成用于基于HTML的访问的网页（报告、Web表单等）。 为此，该过程包括Apache Tomcat JSP服务器。 这是控制台连接到的进程。

**工作流引擎** (nlserver wfserver)

它执行应用程序中定义的工作流进程。

它还负责处理定期执行的技术工作流，包括：

* 跟踪：恢复和整合跟踪日志。 它允许您从重定向服务器检索日志并创建报告模块使用的聚合指示符。
* 清除：数据库清理。 用于清除旧记录并避免数据库呈指数级增长。
* 帐单：自动发送平台的活动报告（数据库大小、营销操作数等）。

**Delivery Server** (nlserver mta)

Adobe Campaign具有本机电子邮件广播功能。 此过程用作SMTP邮件传输代理(MTA)。 它对消息执行“一对一”个性化并处理其实际交付。 它使用交付作业来运行并处理自动重试。 此外，启用跟踪后，会自动替换URL，以便它们指向重定向服务器。

该过程可以处理SMS、传真和直邮的自定义和自动发送给第三方路由器。

**重定向服务器** (nlserver webmdl)

对于电子邮件，Adobe Campaign会自动处理打开和点击跟踪（更有可能的是，在网站级别进行事务跟踪）。 为此，将重写包含在电子邮件中的URL，以指向此模块，该模块在将Internet用户重定向到所需URL之前注册其通过。

为保证最高可用性，此过程完全独立于数据库：其他服务器进程仅使用SOAP调用（HTTP、HTTP和XML）与其通信。 从技术上讲，此功能是在HTTP服务器的扩展模块（IIS中的ISAPI扩展或DSO Apache模块等）中实现的并且仅在Windows中可用。

还提供了其他技术流程：

**管理弹回的电子邮件** (nlserver inMail)

此过程允许您从配置为接收退回邮件的邮箱中自动获取电子邮件，这些邮件在发送失败时会返回。 然后，这些消息将进行基于规则的处理以确定未发送的原因（未知的收件人、超出配额等）以及更新数据库中的交付状态。

所有这些操作都是完全自动和预配置的。

**SMS交付状态** (nlserver sms)

此过程会轮询SMS路由器以收集进度状态并更新数据库。

**写入日志消息** (nlserver syslogd)

此技术过程捕获由其他进程生成的日志消息和跟踪，并将其写入硬盘。 这使得在出现问题时可以诊断大量信息。

**写入跟踪日志** (nlserver trackinglogd)

此进程会将重定向进程生成的跟踪日志保存到磁盘。

**写入入站事件** (nlserver interactiond)

此过程确保在交互框架内将入站事件记录到磁盘。

**监视模块** （nlserver监视程序）

此技术流程充当主流程，使其他流程繁多。 它还可以在发生事故时自动监控并重新启动它们，从而保持系统的最长正常运行时间。

**统计服务器** (nlserver stat)

该过程保留有关连接数、发送给每个邮件服务器的消息以及其限制（最高同时连接数、每小时消息数和／或连接数）的统计信息。 如果多个实例或计算机共享相同的公共IP地址，则还可以联合这些实例或计算机。

>[!NOTE]
>
>本文档提供Adobe Campaign模块的完整 [列表](../../production/using/operating-principle.md)。

## 持久层 {#persistence-layer}

数据库用作持久层，并包含Adobe Campaign管理的几乎所有信息。 这包括功能数据（配置文件、订阅、内容等）、技术数据（交付作业和日志、跟踪日志等）和工作数据（购买、潜在客户）。

数据库的可靠性至关重要，因为大多数Adobe Campaign组件都需要访问数据库才能执行其任务（重定向模块的显着例外）。

该平台是使用以营销为中心的数据集市预定义的，或者可以使用任何主要的关系数据库管理系统(RDBMS)轻松地置于现有数据集市和架构之上。 Adobe Campaign平台通过从Adobe Campaign到数据库的SQL调用访问数据集市中的所有数据。 Adobe Campaign还提供了对提取转换和加载(ETL)工具的完整补充，用于执行数据导入和数据进出系统。
