---
solution: Campaign Classic
product: campaign
title: 标准部署
description: 标准部署
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 标准部署{#standard-deployment}

对于此配置，需要三台计算机：

* LAN中为最终用户(准备活动、报告等)提供的应用程序服务器，
* DMZ中的两台前端服务器位于负载平衡器后面。

DMZ中的两台服务器处理跟踪、镜像页面和投放，并且冗余以实现高可用性。

LAN中的应用程序服务器为最终用户提供服务，并执行所有重复的进程(工作流引擎)。 因此，当到达前端服务器的峰值负载时，应用程序用户不会受到影响。

数据库服务器可以独立于这三台计算机托管。 只有Adobe Campaign支持操作系统（Linux或Windows），应用程序服务器和数据库服务器才能在局域网内共享同一台计算机。

服务器和进程之间的通用通信根据以下模式进行：

![](assets/s_001_ncs_install_standardconfig.png)

此类配置可以处理大量收件人（500,000到1,000,000），因为数据库服务器（以及可用带宽）是主要限制因素。

## 功能{#features}

### 优势{#advantages}

* 故障转移功能：在另一台计算机出现硬件问题时，能够将进程切换到一台计算机。
* 总体性能更好，因为MTA和重定向功能可以部署在负载平衡器后的两台计算机上。 借助两个活动MTA和足够的带宽，在每小时100,000封邮件的区域内实现广播速率是可能的。

## 安装和配置步骤{#installation-and-configuration-steps}

### 先决条件{#prerequisites}

* JDK,
* 两个前端上的Web服务器(IIS、Apache),
* 访问所有三台计算机上的数据库服务器，
* 可通过POP3访问的弹回邮箱，
* 创建两个DNS别名：

   * 首先公开，以跟踪并指向虚拟IP地址(VIP)上的负载平衡器，然后分发给两台前端服务器，
   * 第二个控制台向内部用户公开，供他们通过控制台访问并指向同一应用程序服务器。

* 防火墙配置为打开STMP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL(1521(Oracle)、5432(PostgreSQL)等。 端口。 有关详细信息，请参阅[数据库访问](../../installation/using/network-configuration.md#database-access)一节。

### 安装应用程序服务器{#installing-the-application-server}

按照以下步骤从Adobe Campaign应用程序服务器安装独立实例以创建数据库（步骤12）。 请参阅[安装和配置（单台计算机）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-)。

由于计算机不是跟踪服务器，请不要考虑与Web服务器的集成。

在以下示例中，实例的参数为：

* 实例的名称：**demo**
* DNS掩码：**console.活动.net***（仅用于客户端控制台连接和报告）
* 语言：英语
* 数据库：**活动:demo@dbsrv**

### 安装两个前端服务器{#installing-the-two-frontal-servers}

在两台计算机上的安装和配置过程相同。

步骤如下：

1. 安装Adobe Campaign服务器。

   有关详细信息，请参阅[在Linux中安装活动的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)(Linux)和[在Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)(Windows)中安装活动的先决条件。

1. 按照以下各节中所述的Web服务器集成过程(IIS, Apache)操作：

   * 对于Linux:[集成到Linux的Web服务器](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 对于Windows:[集成到Windows的Web服务器](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 创建&#x200B;**demo**&#x200B;实例。 有两种方法可以实现此目的：

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

   将通过负载平衡器的URL(tracking.镜像页面.net)与具有&#x200B;**nlserver web**&#x200B;模块(退订、活动)的服务器建立连接。

1. 将&#x200B;**internal**&#x200B;更改为与应用程序服务器相同。

   有关详细信息，请参阅[内部标识符](../../installation/using/campaign-server-configuration.md#internal-identifier)。

1. 将数据库链接到实例：

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 在&#x200B;**config-default.xml**&#x200B;和&#x200B;**config-demo.xml**&#x200B;文件中，启用&#x200B;**web**、**trackinglogd**&#x200B;和&#x200B;**mta**&#x200B;模块。

   有关详细信息，请参阅[启用进程](../../installation/using/campaign-server-configuration.md#enabling-processes)。

1. 编辑&#x200B;**serverConf.xml**&#x200B;文件并填充：

   * MTA模块的DNS配置：

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >**nameServers**&#x200B;参数仅在Windows中使用。

      有关详细信息，请参阅[投放设置](../../installation/using/campaign-server-configuration.md#delivery-settings)。

   * 重定向参数中的冗余跟踪服务器：

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      有关详细信息，请参阅[冗余跟踪](../../installation/using/configuring-campaign-server.md#redundant-tracking)。

1. 开始网站并测试来自URL的重定向：[https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)。

   浏览器应显示以下消息（取决于负载平衡器重定向的URL）:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   或者

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   有关此方面的详细信息，请参阅以下各节：

   * 对于Linux:[启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 对于Windows:[启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 开始Adobe Campaign服务器。
1. 在Adobe Campaign控制台中，使用&#x200B;**admin**&#x200B;登录名（无口令）进行连接并启动部署向导。

   有关详细信息，请参阅[部署实例](../../installation/using/deploying-an-instance.md)。

   除了跟踪模块的配置之外，配置与独立实例相同。

1. 填充用于重定向的外部URL（负载平衡器的URL）和两个前端服务器的内部URL。

   有关详细信息，请参阅[跟踪配置](../../installation/using/deploying-an-instance.md#tracking-configuration)。

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >我们使用之前创建的两个跟踪服务器的现有实例，并使用&#x200B;**internal**&#x200B;登录名。

