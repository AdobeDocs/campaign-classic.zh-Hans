---
solution: Campaign Classic
product: campaign
title: 企业部署
description: 企业部署
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 1%

---


# 企业部署{#enterprise-deployment}

这是最完整的配置。 它以标准配置为基础，以提高安全性和可用性：

* 在HTTP或TCP负载平衡器后面的专用重定向服务器，以实现可伸缩性和可用性，
* 两台应用服务器，可提高吞吐量和故障转移能力（容错），它们在LAN中隔离。

服务器和进程之间的通用通信根据以下模式进行：

![](assets/s_901_ncs_install_enterpriseconfig.png)

通过这种配置，在适当的带宽和调整下，预期吞吐量可以超过每小时100,000封邮件。

## Features {#features}

### 优势 {#advantages}

* 优化的安全性：只有那些需要暴露到外部的服务器才安装在DMZ的计算机上。
* 高可用性更容易确保：只有外部可见的计算机需要管理，同时考虑高可用性。

### 缺点 {#disadvantages}

硬件和管理成本更高。

### 推荐设备 {#recommended-equipment}

* 应用程序服务器：2 Ghz四核CPU,4 GB RAM，软件RAID 1 80 GB SATA硬盘。
* 重定向服务器：2 Ghz四核CPU,4 GB RAM，软件RAID 1 80 GB SATA硬盘。

>[!NOTE]
>
>可以为重定向服务器的流量重用现有负载平衡器。

## 安装和配置步骤 {#installation-and-configuration-steps}

### 先决条件{#prerequisites}

* 两台应用程序服务器上的JDK
* 两个前端上的Web服务器(IIS、Apache),
* 访问两个应用程序服务器上的数据库服务器，
* 可通过POP3访问的弹回邮箱，
* 在负载平衡器上创建两个DNS别名：

   * 首先公开，以跟踪并指向虚拟IP地址(VIP)上的负载平衡器，然后分发给两台前端服务器，
   * 第二个控制台向内部用户公开，供其通过控制台访问，并指向虚拟IP地址(VIP)上的负载平衡器，然后该负载平衡器分发到两个应用程序服务器。

* 防火墙配置为打开STMP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL(1521(Oracle)、5432(PostgreSQL)等。 端口。 有关详细信息，请参阅“数据库 [访问”一节](../../installation/using/network-configuration.md#database-access)。

>[!CAUTION]
>
>如果应用程序服务器指向单个数据库实例，则在一个实例上导入标准包后，包中包含的模式不会加载到另一个实例上。
>  
>如果应用程序服务器指向单个模式库实例，则在更改一个实例的模式后，该数据库不会加载到另一个实例。
>
>要恢复这些问题，您需要在发生错误的第二个实例上重新启动“web@default”进程。

### 安装和配置应用程序服务器1 {#installing-and-configuring-the-application-server-1}

在以下示例中，实例的参数为：

* 实例的名称：演示
* DNS掩码：tracking.活动.net*、console.活动.net*(应用程序服务器处理客户端控制台连接和报告以及镜像页面和退订页面的URL)
* 语言：英语
* 数据库：活动:demo@dbsrv

安装第一台服务器的步骤有：

1. 按照Adobe Campaign服务器的安装过程操作： **Linux上** 的nlserver包或 **Windows上的setup** .exe。

   有关详细信息，请参 [阅Linux(Linux)中活动安装的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) ，以及Windows( [Windows)中活动安装的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) 。

1. 安装Adobe Campaign服务器后，使用命令nlserver web -tomcat **** (Web模块使您能够以独立的Web服务器模式开始Tomcat，监听端口8080)并确保Tomcat开始正确：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >首次执行Web模块时，它将在安 **装文件夹下的conf** 目录中创 **建config-default.xml和serverConf****** .xml文件。 serverConf.xml中的所 **有可用参数** 都列在本 [节中](../../installation/using/the-server-configuration-file.md)。

   按 **Ctrl+C** 可停止服务器。

   有关此方面的详细信息，请参阅以下各节：

   * 对于Linux: [服务器的首次开始](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * 对于Windows: [服务器的首次开始](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. 使用 **命令** :

   ```
   nlserver config -internalpassword
   ```

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. 使用DNS **掩码** (本例中为 **tracking.活动.net)创建演示实例，并访问客户端控制台(本例中为console.**&#x200B;活动.net ****)。 有两种方法可以实现此目的：

   * 通过控制台创建实例：

      ![](assets/install_create_new_connexion.png)

      有关此的详细信息，请参 [阅创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md)。

      或者

   * 使用命令行创建实例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      有关此的详细信息，请参 [阅创建实例](../../installation/using/command-lines.md#creating-an-instance)。

1. 编辑 **config-demo.xml文件** (通过命令创建，并位于 **config-default.xml文件旁)，检查mta** (投放) **()、wffServer****************** (Resople)MailMail（邮件反弹）和邮件（邮件）统计信息是否已启用，然后配置App Server的地址：

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. 编辑 **serverConf.xml文件** ，指定投放域，然后指定MTA模块用来应答MX类型DNS查询的DNS服务器的IP（或主机）地址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >nameServers **参数** 仅在Windows中使用。

   有关详细信息，请参阅 [活动服务器配置](../../installation/using/campaign-server-configuration.md)。

1. 将客户端设置项目(**v或** YYYY-client-6.XX **,************** EXE.exe setup v.1)复制到/Datat，它/Eng/JespJonsole文件夹中。

   有关此方面的详细信息，请参阅以下各节：

   * 对于Linux: [适用于Linux的客户端控制台可用性](../../installation/using/client-console-availability-for-linux.md)
   * 对于Windows: [适用于Windows的客户端控制台可用性](../../installation/using/client-console-availability-for-windows.md)。

1. 开始Adobe Campaign服务器(**Windows中的Net** 开始nlserver6 **,Linux中的** /etc/init.d/nlserver6开始)并再次运行命令 **nlserver pdump** ，检查是否存在所有已启用的模块。

   >[!NOTE]
   >
   >从20.1开始，我们建议改用以下命令（对于Linux）: **systemctl开始nlserver**


   ```
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   此命令还允许您了解安装在计算机上的Adobe Campaign服务器的版本和内部版本号。

1. 使用 **URL测试** nlserver web模块： [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test)。

   此URL允许您访问客户端设置项目的下载页。

   在进入 **访问控制** 页面时，输入内部登录名和关联密码。

   ![](assets/s_ncs_install_access_client.png)

   有关此方面的详细信息，请参阅以下各节：

   * 对于Linux: [适用于Linux的客户端控制台可用性](../../installation/using/client-console-availability-for-linux.md)
   * 对于Windows: [适用于Windows的客户端控制台可用性](../../installation/using/client-console-availability-for-windows.md)

### 安装和配置应用程序服务器2 {#installing-and-configuring-the-application-server-2}

应用以下步骤：

1. 安装Adobe Campaign服务器。
1. 将您创建的实例的文件复制到应用程序服务器1上。

   我们保留与应用程序服务器1相同的实例名称。

1. 将内部 **更改** 为与应用程序服务器1相同。
1. 将数据库链接到实例：

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 编辑 **config-demo.xml文件** (通过命令创建，并位于 **config-default.xml文件旁)，检查mta** (投放) **()、wffServer****************** (Resople)MailMail（邮件反弹）和邮件（邮件）统计信息是否已启用，然后配置App Server的地址：

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. 编辑 **serverConf.xml** 文件并填充MTA模块的DNS配置：

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >nameServers **参数** 仅在Windows中使用。

   有关详细信息，请参阅 [活动服务器配置](../../installation/using/campaign-server-configuration.md)。

1. 开始Adobe Campaign服务器。

   有关此方面的详细信息，请参阅以下各节：

   * 对于Linux: [服务器的首次开始](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * 对于Windows: [服务器的首次开始](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### 安装和配置前端服务器 {#installing-and-configuring-the-frontal-servers}

安装和配置过程在两台计算机上都相同。

步骤如下：

1. 安装Adobe Campaign服务器，
1. 符合以下各节中所述的Web服务器集成过程(IIS、Apache):

   * For Linux: [Integration into a Web server for Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * For Windows: [Integration into a Web server for Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. 复制 **安装过程中创建****的config-demo.xml和serverConf** .xml文件。 在config- **demo.xml文件中** ，激活 **inglogd进程并取消激活mta** 、 **inmail**、 ************ 服务器和进程。
1. 编辑 **serverConf.xml** 文件，并在重定向参数中填充冗余跟踪服务器：

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. 开始网站并测试来自URL的重定向： [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   浏览器应显示以下消息（取决于负载平衡器重定向的URL）:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   或者

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   有关此方面的详细信息，请参阅以下各节：

   * 对于Linux: [启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * 对于Windows: [启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)。

1. 开始Adobe Campaign服务器。

