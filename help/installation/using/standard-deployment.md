---
title: 标准部署
seo-title: 标准部署
description: 标准部署
seo-description: null
page-status-flag: never-activated
uuid: e2f9c4d9-4b36-4899-9954-493135597057
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: d714b759-cc08-4656-876c-9820d5c56216
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 标准部署{#standard-deployment}

对于此配置，需要三台计算机：

* LAN中的应用程序服务器，供最终用户（准备营销活动、报告等）使用，
* DMZ中位于负载平衡器后面的两个前端服务器。

DMZ中的两台服务器处理跟踪、镜像页面和交付，并且为高可用性而冗余。

LAN中的应用程序服务器为最终用户提供服务并执行所有重复的进程（工作流引擎）。 因此，当到达前端服务器上的峰值负载时，应用程序用户不会受到影响。

数据库服务器可以与这三台服务器分别托管在单独的计算机上。 否则，只要Adobe Campaign（Linux或Windows）支持操作系统，应用程序服务器和数据库服务器就必须在局域网内共享同一台计算机。

服务器和进程之间的一般通信根据以下模式进行：

![](assets/s_001_ncs_install_standardconfig.png)

此类配置可以处理大量收件人（500,000到1,000,000），因为数据库服务器（以及可用带宽）是主要的限制因素。

## 功能 {#features}

### 优势 {#advantages}

* 故障转移功能：在另一台计算机上出现硬件问题时能够将进程切换到一台计算机。
* 由于MTA和重定向功能可部署在负载平衡器后面的两台计算机上，因此总体性能更好。 借助两个活动MTA和足够的带宽，在每小时100,000封邮件的区域实现广播速率是可能的。

## 安装和配置步骤 {#installation-and-configuration-steps}

### 先决条件 {#prerequisites}

* JDK,
* 两个前端上的Web服务器(IIS、Apache)、
* 访问所有三台计算机上的数据库服务器，
* 可通过POP3访问的弹回邮箱，
* 创建两个DNS别名：

   * 首先公开用于跟踪并指向虚拟IP地址(VIP)上的负载平衡器，然后分发到两个前端服务器，
   * 第二个控制台向内部用户公开，供他们通过控制台访问并指向同一应用程序服务器。

* 配置为打开STMP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL（1521 for Oracle,5432 for PostgreSQL，等等）的防火墙端口。 有关详细信息，请参阅“数据库 [访问”一节](../../installation/using/network-configuration.md#database-access)。

### 安装应用程序服务器 {#installing-the-application-server}

按照以下步骤从Adobe Campaign应用程序服务器安装独立实例以创建数据库（第12步）。 请参阅 [安装和配置（单台计算机）](#installing-and-configuring--single-machine-)。

由于计算机不是跟踪服务器，因此不要考虑与Web服务器的集成。

在以下示例中，实例的参数为：

* 实例的名称：演 **示**
* DNS掩码：console. **campaign.net*** （仅用于客户端控制台连接和报告）
* 语言：英语
* 数据库：营销 **活动：demo@dbsrv**

### 安装两个前沿服务器 {#installing-the-two-frontal-servers}

在两台计算机上的安装和配置过程相同。

步骤如下：

1. 安装Adobe Campaign服务器。

   有关详细信息，请参 [阅在Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux)中安装Campaign的先决条件和在Windows [](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows)中安装Campaign的先决条件。

1. 请按照以下各节中所述的Web服务器集成过程(IIS, Apache)操作：

   * 对于Linux:集 [成到Linux的Web服务器](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 对于Windows:与 [Windows版Web服务器集成](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 创建演 **示实** 例。 有两种方法可以实现此目的：

   * 通过控制台创建实例：

      ![](assets/install_create_new_connexion.png)

      有关详细信息，请参阅 [创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md)。

      或

   * 使用命令行创建实例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*
      ```

      有关详细信息，请参阅 [创建实例](../../installation/using/command-lines.md#creating-an-instance)。
   实例的名称与应用程序服务器的名称相同。

   将通过负载平衡器 **的URL** (tracking.campaign.net)与服务器连接（镜像页面、取消订阅）。

1. 将内部 **更改** ，使其与应用程序服务器相同。

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. 将数据库链接到实例：

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 在 **config-default.xml和** config-demo.xml文件中，启用 **web** 、 **trackinglogd**&#x200B;和 ******** mta模块。

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. 编辑 **serverConf.xml文件** ，并填充：

   * MTA模块的DNS配置：

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >nameServers **参数** ，仅在Windows中使用。

      For more on this, refer to [Delivery settings](../../installation/using/campaign-server-configuration.md#delivery-settings).

   * 重定向参数中的冗余跟踪服务器：

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      For more on this, refer to [Redundant tracking](../../installation/using/configuring-campaign-server.md#redundant-tracking).

1. 启动网站并从URL测试重定向： [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)。

   浏览器应显示以下消息（具体取决于负载平衡器重定向的URL）:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   或

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   有关此功能的详细信息，请参阅以下几节：

   * 对于Linux:启 [动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 对于Windows:启 [动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 启动Adobe Campaign服务器。
1. 在Adobe Campaign控制台中，使用管理员登录名( **无口令** )进行连接，然后启动部署向导。

   有关详细信息，请参阅 [部署实例](../../installation/using/deploying-an-instance.md)。

   除了跟踪模块的配置之外，配置与独立实例相同。

1. 填充用于重定向的外部URL（负载平衡器的外部URL）和两个前端服务器的内部URL。

   For more on this, refer to [Tracking configuration](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >我们使用之前创建的两个跟踪服务器的现有实例，并使用内部 **登录** 。

