---
title: 独立部署
seo-title: 独立部署
description: 独立部署
seo-description: null
page-status-flag: never-activated
uuid: 48ce793e-cb9f-4102-898f-758512cb9bf2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 9834638f-a8bb-4969-9f8d-99b8d9fdb1ca
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

---


# 独立部署{#standalone-deployment}

此配置包括同一台计算机上的所有组件：

* 应用程序进程(web),
* 交付流程(mta),
* 重定向过程（跟踪）,
* 工作流程和计划任务(wfserver),
* 弹回邮件流程(inMail),
* 统计进程(stat)。

进程之间的整体通信根据以下模式进行：

![](assets/s_900_ncs_install_standaloneconfig.png)

在管理少于100,000个收件人的列表时，可以运行此类配置，例如，使用以下软件层：

* Linux、
* Apache,
* PostgreSQL,
* Qmail。

随着卷的增长，此体系结构的一个变体将数据库服务器移动到另一台计算机以获得更好的性能。

>[!NOTE]
>
>如果现有数据库服务器具有足够的资源，也可以使用它。

## 功能 {#features}

### 优势 {#advantages}

* 完全独立且配置成本低（如果使用下面列出的开放源码软件，则不需要收费许可证）。
* 简化安装和网络配置。

### 缺点 {#disadvantages}

* 发生事故时的关键计算机。
* 广播消息时的带宽有限（根据我们的经验，每小时大约有数万封邮件）。
* 广播时应用程序可能会减速。
* 应用程序服务器必须从外部（例如，当它位于DMZ中时）可用，因为它承载重定向服务器。

## 安装和配置步骤 {#installation-and-configuration-steps}

### 先决条件 {#prerequisites}

* JDK、
* Web服务器(IIS、Apache),
* 访问数据库服务器，
* 可通过POP3访问的弹回邮箱，
* 创建两个DNS别名：

   * 第一个公开，用于跟踪并指向其公共IP上的计算机；
   * 向内部用户公开的第二个别名，用于控制台访问并指向同一台计算机。

* 配置为打开STMP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL（1521 for Oracle,5432 for PostgreSQL，等等）的防火墙端口。 有关详细信息，请参阅 [网络配置](../../installation/using/network-configuration.md)。

在以下示例中，实例的参数为：

* 实例的名称：演 **示**
* DNS掩码：console. **campaign.net*** （仅用于客户端控制台连接和报告）
* 数据库：营销 **活动：demo@dbsrv**

### 安装和配置（单台计算机） {#installing-and-configuring--single-machine-}

应用以下步骤：

1. 按照Adobe Campaign服务器的安装过程操作：Linux **上的Nlserver** 包或Windows **上的setup.exe** 。

   有关详细信息，请参 [阅在Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux)中安装Campaign的先决条件和在Windows [](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows)中安装Campaign的先决条件。

1. 安装Adobe Campaign服务器后，使用命令 **nlserver web -tomcat** （Web模块允许您在独立的Web服务器模式下启动Tomcat，监听端口8080）并确保Tomcat正确启动：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >首次执行Web模块时，它会在安装文件夹下的 **conf目录中创建** config-default.xml **** 和serverConf.xml **** 文件。 serverConf.xml中可用的所 **有参数都列在本节** 中 [](../../installation/using/the-server-configuration-file.md)。

   按 **Ctrl+C** 可停止服务器。

   有关此功能的详细信息，请参阅以下几节：

   * 对于Linux:服 [务器的首次启动](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * 对于Windows:服 [务器的首次启动](../../installation/using/installing-the-server.md#first-start-up-of-the-server)。

1. 使用命 **令** :

   ```
   nlserver config -internalpassword
   ```

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. 使用DNS **掩码创建演示实例** ，以便进行跟踪(本例中为 **tracking.campaign.net**)并访问客户端控制台(本例中为 **console.campaign.net**)。 有两种方法可以实现此目的：

   * 通过控制台创建实例：

      ![](assets/install_create_new_connexion.png)

      有关详细信息，请参阅 [创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md)。

      或

   * 使用命令行创建实例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      有关详细信息，请参阅 [创建实例](../../installation/using/command-lines.md#creating-an-instance)。

1. 编辑 **config-demo.xml** 文件(在 **config-default.xml旁边的上一步中创建)，并确保** ta **(** ,wfserver ************ (),InWinServerMail（邮件弹回）和Stat（统计信息）处理已启用“调出”(Stat)进程。 然后，配置统计信息服务器的地址：

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="localhost"/>
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. 编辑 **serverConf.xml文件并指定交付域** ，然后指定MTA模块用来回答MX类型DNS查询的DNS服务器的IP（或主机）地址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >nameServers **参数** ，仅在Windows中使用。

   有关详细信息，请参阅 [Campaign服务器配置](../../installation/using/campaign-server-configuration.md)。

1. 将客户端设置程序(**setup-client-7.XX**, **SETUP.exe(v或** client-6.XX))复制到 ************ YYYY.1的Jyyy.7文件夹的Adomat/datakit it/nl/eng/eng/jyyyy.7/jsp文件夹中。

   有关此功能的详细信息，请参阅以下几节：

   * 对于Linux:适用于 [Linux的客户端控制台可用性](../../installation/using/client-console-availability-for-linux.md)
   * 对于Windows:适用 [于Windows的客户端控制台可用性](../../installation/using/client-console-availability-for-windows.md)

1. 请按照以下各节中所述的Web服务器集成过程(IIS, Apache)操作：

   * 对于Linux:集 [成到Linux的Web服务器](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 对于Windows:与 [Windows版Web服务器集成](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 启动网站并使用URL测试重定向： [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)。

   浏览器必须显示以下消息：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   有关此功能的详细信息，请参阅以下几节：

   * 对于Linux:启 [动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 对于Windows:启 [动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 启动Adobe Campaign服务器(**Windows中的Net Start nlserver6** , **/etc/init.d/nlserver6在Linux中启动** )并再次运行命令 **nlserver pdump** ，以检查是否存在所有已启用的模块。

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

   此命令还可让您了解计算机上安装的Adobe Campaign服务器的版本和内部版本号。

1. 使用URL **测试Nlserver web** module: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test)

   此URL允许您访问客户端安装程序的下载页。

   当您到达 **访问控制页** 时，输入内部登录名和关联的口令。

   ![](assets/s_ncs_install_access_client.png)

   有关此功能的详细信息，请参阅以下几节：

   * 对于Linux:适用于 [Linux的客户端控制台可用性](../../installation/using/client-console-availability-for-linux.md)
   * 对于Windows:适用 [于Windows的客户端控制台可用性](../../installation/using/client-console-availability-for-windows.md)

1. 启动Adobe Campaign客户端控制台（从上一个下载页面启动或直接在服务器上为Windows安装启动），将服务器连接URL设置为 [https://console.campaign.net](https://console.campaign.net) ，然后使用内部登录 **进行连接** 。

   请参阅 [创建实例并登录和](../../installation/using/creating-an-instance-and-logging-on.md)[内部标识符](../../installation/using/campaign-server-configuration.md#internal-identifier)。

   首次登录时，将显示数据库创建向导：

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   按照向导中的步骤操作，并创建与连接实例关联的数据库。

   有关详细信息，请参阅创 [建和配置数据库](../../installation/using/creating-and-configuring-the-database.md)。

   创建数据库后，请注销。

1. 使用管理员登录(不带口令 **** )重新登录到客户端控制台，然后启动部署向导( **[!UICONTROL Tools > Advanced]** 菜单)以完成实例配置。

   有关详细信息，请参阅 [部署实例](../../installation/using/deploying-an-instance.md)。

   要设置的主要参数如下：

   * 电子邮件发送：发件人和回复地址以及弹回邮件的错误邮箱。
   * 跟踪：填充用于重定向的外部URL和内部URL，单击跟踪服务器上的 **Registration** （注册），然后在跟踪服务器的 **demo** 实例上验证它。

      For more on this, refer to [Tracking configuration](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      由于Adobe Campaign服务器既用作应用程序服务器又用作重定向服务器，用于收集跟踪日志和传输URL的内部URL是与Tomcat(https://localhost:8080)的直接内部连接。

   * 弹回管理：输入处理弹回邮件的参数(请勿将“未处理 **弹回邮件** ”部分考虑在内)。
   * 访问来源：为报告、Web表单和镜像页面提供两个URL。

      ![](assets/d_ncs_install_web_url.png)

