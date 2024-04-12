---
product: campaign
title: 独立部署
description: 独立部署
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 3%

---

# 独立部署{#standalone-deployment}



此配置包含同一台计算机上的所有组件：

* 应用程序进程(Web)，
* 投放流程(mta)、
* 重定向流程（跟踪）、
* 工作流进程和计划任务(wfserver)、
* 退回邮件流程(inMail)、
* 统计过程(stat)。

进程之间的整体通信按照以下模式进行：

![](assets/s_900_ncs_install_standaloneconfig.png)

此类配置可在管理少于100,000个收件人的列表时运行，例如，可通过以下软件层运行：

* Linux，
* Apache
* PostgreSQL，
* Qmail。

随着卷的增长，此体系结构的一种变体将数据库服务器移动到另一台计算机，以获得更好的性能。

>[!NOTE]
>
>如果现有数据库服务器具有足够的资源，也可以使用该数据库服务器。

## 功能 {#features}

### 优点 {#advantages}

* 完全独立且配置成本低（如果使用下面列出的开源软件，则不需要收费许可证）。
* 简化了安装和网络配置。

### 缺点 {#disadvantages}

* 发生事故时的关键计算机。
* 广播邮件时带宽有限（根据我们的经验，大约每小时几万封邮件）。
* 播放时应用程序速度可能会减慢。
* 应用程序服务器必须从外部可用（例如，当它位于DMZ中时），因为它托管重定向服务器。

## 安装和配置步骤 {#installation-and-configuration-steps}

### 先决条件 {#prerequisites}

* JDK，
* Web服务器(IIS、Apache)、
* 访问数据库服务器，
* 通过POP3可访问的退回邮箱，
* 创建两个DNS别名：

   * 第一张公开给公众使用公共IP进行跟踪和指向计算机；
   * 向内部用户公开的第二个别名用于控制台访问并指向同一台计算机。

* 防火墙配置为打开SMTP (25)、DNS (53)、HTTP (80)、HTTPS (443)、SQL (1521(Oracle)、5432(PostgreSQL)等) 端口。 欲知更多信息，请参见 [网络配置](../../installation/using/network-configuration.md).

在以下示例中，实例的参数包括：

* 实例的名称： **演示**
* DNS掩码： **console.campaign.net&#42;** （仅适用于客户端控制台连接和报表）
* 数据库： **campaign：demo@dbsrv**

### 安装和配置（单机） {#installing-and-configuring--single-machine-}

应用以下步骤：

1. 请按照Adobe Campaign服务器的安装过程操作： **nlserver** Linux或 **setup.exe** 在Windows上。

   有关详细信息，请参见 [在Linux中安装Campaign的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux)和 [在Windows中安装Campaign的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows)。

1. 安装Adobe Campaign服务器后，使用命令启动应用程序服务器(web) **nlserver web -tomcat** （通过Web模块，您可以以独立Web服务器模式在端口8080上侦听以启动Tomcat），并确保Tomcat正确启动：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >首次执行Web模块时，它会创建 **config-default.xml** 和 **serverConf.xml** 中的文件 **会议** 目录。 中所有可用的参数，请参见 **serverConf.xml** 中列出 [部分](../../installation/using/the-server-configuration-file.md).

   按 **Ctrl+C** 停止服务器。

   有关更多信息，请参阅以下章节：

   * 对于Linux： [服务器的首次启动](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)，
   * 对于Windows： [服务器的首次启动](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. 更改 **内部** 使用命令的密码：

   ```
   nlserver config -internalpassword
   ```

   如需详细信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 创建 **演示** 具有DNS掩码的实例进行跟踪(在本例中， **tracking.campaign.net**)和对客户端控制台的访问权限(在本例中， **console.campaign.net**)。 可通过两种方式来做到这一点：

   * 通过控制台创建实例：

     ![](assets/install_create_new_connexion.png)

     有关详细信息，请参见 [创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md).

     或者

   * 使用命令行创建实例：

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     有关详细信息，请参见 [创建实例](../../installation/using/command-lines.md#creating-an-instance).

1. 编辑 **config-demo.xml** 文件(在上一步创建的，位于 **config-default.xml**)，并确保 **mta** （投放）， **wfserver** （工作流）， **inMail** （退回邮件）和 **stat** (statistics)进程已启用。 然后配置统计服务器的地址：

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

   如需详细信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#enabling-processes)。

1. 编辑 **serverConf.xml** 文件并指定投放域，然后指定MTA模块用于响应MX类型DNS查询的DNS服务器的IP（或主机）地址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >此 **nameServer** 参数仅在Windows中使用。

   有关详细信息，请参见 [Campaign服务器配置](../../installation/using/configuring-campaign-server.md).

1. 复制客户端控制台安装程序 **setup-client-7.XXX.exe** 到 **/datakit/nl/eng/jsp** 文件夹。 [了解详情](../../installation/using/client-console-availability-for-windows.md)。

1. 请按照以下部分中描述的Web服务器集成过程(IIS、Apache)进行操作：

   * 对于Linux： [集成到Linux版Web服务器](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 对于Windows： [集成到Windows版Web服务器](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 启动网站并使用URL测试重定向： https://tracking.campaign.net/r/test。

   浏览器必须显示以下消息：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   有关更多信息，请参阅以下章节：

   * 对于Linux： [启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 对于Windows： [启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 启动Adobe Campaign服务器(**网络启动nlserver6** 在Windows中， **/etc/init.d/nlserver6 start** （在Linux中）并运行命令 **nlserver pdump** 再次检查所有启用的模块是否存在。

   >[!NOTE]
   >
   >从20.1开始，我们建议改使用以下命令（对于Linux）： **systemctl启动nlserver**

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

   此命令还可让您知道计算机上安装的Adobe Campaign服务器的版本号和内部版本号。

1. 测试 **nlserver web** 模块（使用URL）： https://console.campaign.net/nl/jsp/logon.jsp

   此URL允许您访问客户端设置程序的下载页面。

   输入 **内部** 登录和关联的密码。 [了解详情](../../installation/using/client-console-availability-for-windows.md)。

   ![](assets/s_ncs_install_access_client.png)

1. 启动Adobe Campaign客户端控制台（从上一个下载页面启动，或直接在服务器上启动以进行Windows安装），将服务器连接URL设置为https://console.campaign.net ，然后使用 **内部** 登录。

   请参阅 [此页面](../../installation/using/creating-an-instance-and-logging-on.md) 和 [本节](../../installation/using/configuring-campaign-server.md#internal-identifier).

   首次登录时将显示数据库创建向导：

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   按照向导中的步骤创建与连接实例关联的数据库。

   有关详细信息，请参见 [创建和配置数据库](../../installation/using/creating-and-configuring-the-database.md).

   创建数据库后，注销。

1. 使用重新登录到客户端控制台 **管理员** 不使用密码登录并启动部署向导( **[!UICONTROL Tools > Advanced]** 菜单)以完成实例的配置。

   有关详细信息，请参见 [部署实例](../../installation/using/deploying-an-instance.md).

   要设置的主要参数如下：

   * 电子邮件投放：发件人和回复地址以及退回邮件的错误邮箱。
   * 跟踪：填充用于重定向的外部URL和内部URL，单击 **在跟踪服务器上注册** 然后在 **演示** 跟踪服务器的实例。

     有关详细信息，请参见 [跟踪配置](../../installation/using/deploying-an-instance.md#tracking-configuration).

     ![](assets/s_ncs_install_deployment_wiz_09.png)

     由于Adobe Campaign服务器同时用作应用程序服务器和重定向服务器，因此用于收集跟踪日志和传输URL的内部URL是与Tomcat的直接内部连接(https://localhost:8080)。

   * 退回管理：输入用于处理退回邮件的参数(请勿采用 **未处理的退回邮件** 部分)。
   * 访问自：为报表、Web窗体以及镜像页面提供两个URL。

     ![](assets/d_ncs_install_web_url.png)
