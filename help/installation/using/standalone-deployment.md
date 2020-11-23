---
solution: Campaign Classic
product: campaign
title: 独立部署
description: 独立部署
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 1%

---


# 独立部署{#standalone-deployment}

此配置包括同一计算机上的所有组件：

* 应用程序进程(web),
* 投放流程(mta),
* 重定向过程（跟踪）,
* 工作流程和计划任务(wfserver),
* 弹回邮件流程(inMail),
* 统计过程(stat)。

进程之间的整体通信按照以下模式进行：

![](assets/s_900_ncs_install_standaloneconfig.png)

在管理少于100,000个列表的收件人时，可以运行此类配置，例如，使用以下软件层：

* Linux、
* 阿帕奇，
* PostgreSQL,
* Qmail。

随着卷的增长，此体系结构的一个变体将数据库服务器移动到另一台计算机上以获得更好的性能。

>[!NOTE]
>
>如果现有数据库服务器具有足够的资源，也可以使用它。

## Features {#features}

### 优势 {#advantages}

* 完全独立且配置成本低（如果使用下面列出的开源软件，则不需要收费许可证）。
* 简化安装和网络配置。

### 缺点 {#disadvantages}

* 发生事故时的关键计算机。
* 广播消息时带宽有限（根据我们的经验，每小时大约有数万封邮件）。
* 在广播时应用程序可能会减速。
* 应用程序服务器必须可从外部使用（例如，当它位于DMZ中时），因为它承载重定向服务器。

## 安装和配置步骤 {#installation-and-configuration-steps}

### 先决条件{#prerequisites}

* JDK、
* Web服务器(IIS、Apache)、
* 访问数据库服务器，
* 可通过POP3访问的弹回邮箱，
* 创建两个DNS别名：

   * 首次公开，用于跟踪并指向公共IP上的计算机；
   * 向内部用户公开的第二个别名用于控制台访问并指向同一台计算机。

* 防火墙配置为打开SMTP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL(Oracle1521、PostgreSQL5432等) 端口。 有关详细信息，请参 [阅网络配置](../../installation/using/network-configuration.md)。

在以下示例中，实例的参数为：

* 实例的名称： **演示**
* DNS掩码： **console.活动.net*** （仅用于客户端控制台连接和报告）
* 数据库： **活动:demo@dbsrv**

### 安装和配置（单台计算机） {#installing-and-configuring--single-machine-}

应用以下步骤：

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

   * 对于Linux: [服务器的首次开始](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * 对于Windows: [服务器的首次开始](../../installation/using/installing-the-server.md#first-start-up-of-the-server)。

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

1. 编辑 **config-demo.xml** 文件(在上一步 **config-default.xml旁创建)，确保启用**(投放、wfserver **************** )、邮件（弹回邮件）和（统计信息）进程()。 然后，配置统计信息服务器的地址：

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
   * 对于Windows: [适用于Windows的客户端控制台可用性](../../installation/using/client-console-availability-for-windows.md)

1. 按照以下各节中所述的Web服务器集成过程(IIS, Apache)操作：

   * For Linux: [Integration into a Web server for Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * For Windows: [Integration into a Web server for Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 开始网站并使用URL测试重定向：https://tracking.campaign.net/r/test。

   浏览器必须显示以下消息：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   有关此方面的详细信息，请参阅以下各节：

   * 对于Linux: [启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 对于Windows: [启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. 使用 **URL测试** nlserver web模块：https://console.campaign.net/nl/jsp/logon.jsp

   此URL允许您访问客户端设置项目的下载页。

   在进入 **访问控制** 页面时，输入内部登录名和关联密码。

   ![](assets/s_ncs_install_access_client.png)

   有关此方面的详细信息，请参阅以下各节：

   * 对于Linux: [适用于Linux的客户端控制台可用性](../../installation/using/client-console-availability-for-linux.md)
   * 对于Windows: [适用于Windows的客户端控制台可用性](../../installation/using/client-console-availability-for-windows.md)

1. 开始Adobe Campaign客户端控制台（从上一下载页或直接在服务器上启动Windows安装），将服务器连接URL设置为https://console.campaign.net，然后使用内部登录 **进行** 连接。

   请参阅 [创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md) 和 [内部标识符](../../installation/using/campaign-server-configuration.md#internal-identifier)。

   首次登录时，将显示数据库创建向导：

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   按照向导中的步骤操作，并创建与连接实例关联的数据库。

   有关此的详细信息，请参 [阅创建和配置数据库](../../installation/using/creating-and-configuring-the-database.md)。

   创建数据库后，注销。

1. 使用管理员登录(无口令 **)重新登录** ，并开始部署向导( **[!UICONTROL Tools > Advanced]** 菜单)以完成实例配置。

   有关此的详细信息，请参 [阅部署实例](../../installation/using/deploying-an-instance.md)。

   要设置的主要参数如下：

   * 电子邮件投放:发件人和回复地址以及弹回邮件的错误邮箱。
   * 跟踪：填充用于重定向的外部URL和内部URL，单 **击跟踪服务器上的“注册** ”，然后在跟踪服务器 **的demo** 实例上验证它。

      For more on this, refer to [Tracking configuration](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      由于Adobe Campaign服务器既用作应用程序服务器又用作重定向服务器，用于收集跟踪日志和传输URL的内部URL是与Tomcat(https://localhost:8080)的直接内部连接。

   * 弹回管理：输入处理弹回邮件的参数(不要将“未处理 **弹回邮件** ”部分考虑在内)。
   * 访问来源：提供两个URL，用于报告、Web 窗体和镜像页面。

      ![](assets/d_ncs_install_web_url.png)

