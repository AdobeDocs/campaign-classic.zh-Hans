---
product: campaign
title: 标准部署
description: 标准部署
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 3%

---

# 标准部署{#standard-deployment}



对于此配置，需要三台计算机：

* LAN内面向最终用户的应用程序服务器（准备营销活动、报告等），
* DMZ中的两个前端服务器，位于负载平衡器后面。

DMZ中的两台服务器负责跟踪、镜像页面和交付，并且冗余以实现高可用性。

LAN中的应用程序服务器为最终用户提供服务，并执行所有循环过程（工作流引擎）。 因此，当前端服务器上的负载达到峰值时，应用程序用户不受影响。

数据库服务器可以托管在与这三台服务器不同的计算机上。 否则，只要Adobe Campaign（Linux或Windows）支持操作系统，应用程序服务器和数据库服务器就会在LAN内共享同一台计算机。

服务器和进程之间的一般通信按照以下模式进行：

![](assets/s_001_ncs_install_standardconfig.png)

这种类型的配置可以处理大量收件人（500,000到1,000,000），因为数据库服务器（以及可用带宽）是主要限制因素。

## 功能 {#features}

### 优点 {#advantages}

* 故障转移功能：能够在另一台计算机出现硬件问题时将进程切换到另一台计算机。
* 整体性能更高，因为MTA和重定向功能可以部署在负载平衡器后的两台计算机上。 有了两个活动的MTA和足够的带宽，就可以实现每小时100,000封邮件的广播速率。

## 安装和配置步骤 {#installation-and-configuration-steps}

### 先决条件 {#prerequisites}

* 三台电脑上都有JDK
* 位于两个前端的Web服务器(IIS、Apache)，
* 访问所有三台计算机上的数据库服务器，
* 通过POP3可访问的退回邮箱，
* 创建两个DNS别名：

   * 第一台服务器向公众开放，用于跟踪和指向虚拟IP地址(VIP)上的负载平衡器，然后将其分发到两个前端服务器，
   * 第二个客户端通过控制台向内部用户公开，以供访问并指向同一应用程序服务器。

* 防火墙配置为打开STMP (25)、DNS (53)、HTTP (80)、HTTPS (443)、SQL (1521(Oracle)、5432(PostgreSQL)等) 端口。 有关详细信息，请参阅[数据库访问](../../installation/using/network-configuration.md#database-access)部分。

### 安装应用程序服务器 {#installing-the-application-server}

按照从Adobe Campaign应用程序服务器安装独立实例到创建数据库的步骤操作（步骤12）。 请参阅[安装和配置（单台计算机）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-)。

由于计算机不是跟踪服务器，因此不要考虑与Web服务器的集成。

在以下示例中，实例的参数包括：

* 实例的名称： **演示**
* DNS掩码： **console.campaign.net&#42;** （仅适用于客户端控制台连接和报表）
* 语言：英语
* 数据库： **campaign：demo@dbsrv**

### 安装两个前端服务器 {#installing-the-two-frontal-servers}

两台计算机上的安装和配置过程相同。

步骤如下：

1. 安装Adobe Campaign服务器。

   有关详细信息，请参阅[在Linux中安装Campaign的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux)和[在Windows中安装Campaign的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows)。

1. 请按照以下部分中描述的Web服务器集成过程(IIS、Apache)进行操作：

   * 对于Linux： [集成到Linux的Web服务器](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 对于Windows： [集成到Windows的Web服务器](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 创建&#x200B;**演示**&#x200B;实例。 可通过两种方式来做到这一点：

   * 通过控制台创建实例：

     ![](assets/install_create_new_connexion.png)

     有关详细信息，请参阅[创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md)。

     或者

   * 使用命令行创建实例：

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*
     ```

     有关详细信息，请参阅[创建实例](../../installation/using/command-lines.md#creating-an-instance)。

   实例的名称与应用程序服务器的名称相同。

   将从负载平衡器(tracking.campaign.net)的URL连接到具有&#x200B;**nlserver web**&#x200B;模块（镜像页面、取消订阅）的服务器。

1. 将&#x200B;**internal**&#x200B;更改为与应用程序服务器相同。

   如需详细信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 将数据库链接到实例：

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 在&#x200B;**config-default.xml**&#x200B;和&#x200B;**config-demo.xml**&#x200B;文件中，启用&#x200B;**web**、**trackinglogd**&#x200B;和&#x200B;**mta**&#x200B;模块。

   如需详细信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#enabling-processes)。

1. 编辑&#x200B;**serverConf.xml**&#x200B;文件并填充：

   * mta模块的DNS配置：

     ```
     <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
     ```

     >[!NOTE]
     >
     >**nameServers**&#x200B;参数仅在Windows中使用。

     有关详细信息，请参阅[投放设置](configure-delivery-settings.md)。

   * 冗余跟踪服务器中的重定向参数：

     ```
     <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
     <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
     ```

     有关详细信息，请参阅[冗余跟踪](configuring-campaign-server.md#redundant-tracking)。

1. 启动网站并从URL测试重定向： [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)。

   浏览器应显示以下消息（具体取决于负载平衡器重定向的URL）：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   或者

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   有关更多信息，请参阅以下章节：

   * 对于Linux： [正在启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 对于Windows： [正在启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 启动Adobe Campaign服务器。
1. 在Adobe Campaign控制台中，使用&#x200B;**管理员**&#x200B;登录（无密码）进行连接，然后启动部署向导。

   有关详细信息，请参阅[部署实例](../../installation/using/deploying-an-instance.md)。

   除了跟踪模块的配置之外，配置与独立实例相同。

1. 填充用于重定向的外部URL（负载平衡器的外部URL）以及两个前端服务器的内部URL。

   有关详细信息，请参阅[跟踪配置](../../installation/using/deploying-an-instance.md#tracking-configuration)。

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >我们使用以前创建的两个跟踪服务器的现有实例，并使用&#x200B;**内部**&#x200B;登录。
