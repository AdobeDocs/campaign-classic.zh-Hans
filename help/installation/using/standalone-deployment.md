---
product: campaign
title: 独立部署
description: 独立部署
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1086'
ht-degree: 3%

---

# 独立部署{#standalone-deployment}

![](../../assets/v7-only.svg)

此配置包含同一计算机上的所有组件：

* 应用程序进程(web),
* 投放流程(mta),
* 重定向流程（跟踪），
* 工作流流程和计划任务(wfserver),
* 退回邮件流程(inMail),
* 统计过程(stat)。

进程之间的整体通信按照以下模式进行：

![](assets/s_900_ncs_install_standaloneconfig.png)

在管理少于100,000个收件人的列表时，可以运行此类配置，例如，使用以下软件层：

* Linux，
* Apache,
* PostgreSQL,
* Qmail。

随着卷的增长，此体系结构的一个变体将数据库服务器移动到另一台计算机，以获得更好的性能。

>[!NOTE]
>
>如果现有数据库服务器具有足够的资源，则也可以使用它。

## 功能 {#features}

### 优势 {#advantages}

* 完全独立且配置成本低（如果使用下面列出的开源软件，则无需计费许可证）。
* 简化了安装和网络配置。

### 缺点 {#disadvantages}

* 发生事故时的关键计算机。
* 广播消息时的带宽有限（根据我们的经验，每小时大约有数万封邮件）。
* 在广播时应用程序可能会减慢。
* 应用程序服务器必须从外部可用（例如，当它位于DMZ中时），因为它承载着重定向服务器。

## 安装和配置步骤 {#installation-and-configuration-steps}

### 先决条件 {#prerequisites}

* JDK、
* Web服务器(IIS、Apache)、
* 访问数据库服务器，
* 可通过POP3访问退回邮箱，
* 创建两个DNS别名：

   * 首次公开跟踪并指向其公共IP上的计算机；
   * 第二个别名向内部用户公开，以便进行控制台访问并指向同一台计算机。

* 防火墙配置为打开SMTP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL(1521 for Oracle、5432 for PostgreSQL等) 端口。 有关详细信息，请参阅 [网络配置](../../installation/using/network-configuration.md).

在以下示例中，实例的参数为：

* 实例的名称： **演示**
* DNS掩码： **console.campaign.net*** （仅适用于客户端控制台连接和报表）
* 数据库： **campaign:demo@dbsrv**

### 安装和配置（单台计算机） {#installing-and-configuring--single-machine-}

应用以下步骤：

1. 按照Adobe Campaign服务器的安装过程操作： **nlserver** Linux或 **setup.exe** 在Windows上。

   有关更多信息，请参阅 [在Linux中安装Campaign的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux)和 [在Windows中安装Campaign的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows)。

1. 安装Adobe Campaign服务器后，使用命令启动应用程序服务器(Web) **nlserver web-tomcat** （通过Web模块，可以在独立Web服务器模式下在端口8080上侦听Tomcat），并确保Tomcat正确启动：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >首次执行Web模块时，会创建 **config-default.xml** 和 **serverConf.xml** 文件 **conf** 目录。 中所有可用的参数 **serverConf.xml** 此 [部分](../../installation/using/the-server-configuration-file.md).

   按 **Ctrl+C** 来停止服务器。

   有关更多信息，请参阅以下章节：

   * 对于Linux: [服务器的首次启动](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * 对于Windows: [服务器的首次启动](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. 更改 **内部** 密码：

   ```
   nlserver config -internalpassword
   ```

   如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 创建 **演示** 具有DNS掩码的实例进行跟踪(在本例中， **tracking.campaign.net**)和对客户端控制台的访问(在本例中， **console.campaign.net**)。 可以通过两种方式来执行此操作：

   * 通过控制台创建实例：

      ![](assets/install_create_new_connexion.png)

      有关更多信息，请参阅 [创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md).

      或者

   * 使用命令行创建实例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      有关更多信息，请参阅 [创建实例](../../installation/using/command-lines.md#creating-an-instance).

1. 编辑 **config-demo.xml** 文件(在 **config-default.xml**)，并确保 **mta** （投放）、 **wfserver** （工作流）、 **inMail** （退回邮件）和 **stat** （统计信息）进程已启用。 然后，配置统计信息服务器的地址：

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

   如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#enabling-processes)。

1. 编辑 **serverConf.xml** 文件并指定提交域，然后指定MTA模块用来应答MX类型DNS查询的DNS服务器的IP（或主机）地址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >的 **nameServers** 参数仅在Windows中使用。

   有关更多信息，请参阅 [Campaign服务器配置](../../installation/using/configuring-campaign-server.md).

1. 复制客户端控制台安装程序(**setup-client-7.XX**, **YYYY.exe** 对于v7或 **setup-client-6.XX**, **YYYY.exe** （对于v6.1） **/datakit/nl/eng/jsp** 文件夹。 [了解详情](../../installation/using/client-console-availability-for-windows.md)。

1. 按照以下部分中描述的Web服务器集成过程(IIS、Apache)操作：

   * 对于Linux: [集成到Linux版Web服务器中](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 对于Windows: [集成到Windows版Web服务器](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 启动网站并使用URL测试重定向：https://tracking.campaign.net/r/test。

   浏览器必须显示以下消息：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   有关更多信息，请参阅以下章节：

   * 对于Linux: [启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 对于Windows: [启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 启动Adobe Campaign服务器(**网络启动nlserver6** 在Windows中， **/etc/init.d/nlserver6开始** 在Linux中)并运行命令 **nlserver pdump** 再次检查是否存在所有已启用的模块。

   >[!NOTE]
   >
   >从20.1开始，我们建议改用以下命令（对于Linux）： **systemctl启动nlserver**

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

   此命令还允许您了解计算机上安装的Adobe Campaign服务器的版本号和内部版本号。

1. 测试 **nlserver web** 模块：https://console.campaign.net/nl/jsp/logon.jsp

   此URL允许您访问客户端安装程序的下载页面。

   输入 **内部** 访问访问控制页面时登录和关联的密码。 [了解详情](../../installation/using/client-console-availability-for-windows.md)。

   ![](assets/s_ncs_install_access_client.png)

1. 启动Adobe Campaign客户端控制台（从上一个下载页面启动或直接在服务器上启动以安装Windows），将服务器连接URL设置为https://console.campaign.net ，然后使用 **内部** 登录。

   请参阅 [本页](../../installation/using/creating-an-instance-and-logging-on.md) 和 [此部分](../../installation/using/configuring-campaign-server.md#internal-identifier).

   数据库创建向导将在您首次登录时显示：

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   按照向导中的步骤操作，并创建与连接实例关联的数据库。

   有关更多信息，请参阅 [创建和配置数据库](../../installation/using/creating-and-configuring-the-database.md).

   创建数据库后，注销。

1. 使用 **管理员** 无密码登录并启动部署向导( **[!UICONTROL Tools > Advanced]** 菜单)以完成实例的配置。

   有关更多信息，请参阅 [部署实例](../../installation/using/deploying-an-instance.md).

   要设置的主要参数如下：

   * 电子邮件投放：退回邮件的发件人和回复地址以及错误邮箱。
   * 跟踪：填充用于重定向的外部URL和内部URL，单击 **在跟踪服务器上注册** 然后在 **演示** 跟踪服务器的实例。

      有关更多信息，请参阅 [跟踪配置](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      由于Adobe Campaign服务器既用作应用程序服务器，又用作重定向服务器，因此用于收集跟踪日志和传输URL的内部URL是与Tomcat(https://localhost:8080)的直接内部连接。

   * 跳出管理：输入处理退回邮件的参数(请不要 **未处理的退回邮件** 部分)。
   * 从以下位置访问：为报表、Web窗体和镜像页面提供两个URL。

      ![](assets/d_ncs_install_web_url.png)
