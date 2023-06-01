---
product: campaign
title: 企业部署
description: 企业部署
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 3%

---

# 企业部署{#enterprise-deployment}



这是最完整的配置。 它以标准配置为基础，以实现更高的安全性和可用性：

* HTTP或TCP负载平衡器后面的专用重定向服务器，用于实现可扩展性和可用性，
* 两个应用程序服务器，用于改进吞吐量和故障转移能力（容错），它们被隔离在LAN中。

服务器和进程之间的一般通信按照以下模式进行：

![](assets/s_901_ncs_install_enterpriseconfig.png)

使用此类型的配置，通过适当的带宽和调整，预计吞吐量可能超过每小时100,000个邮件。

## 功能 {#features}

### 优势 {#advantages}

* 优化的安全性：只有那些需要向外部公开的服务器才会安装在DMZ的计算机上。
* 高可用性更容易确保：只有从外部可见的计算机才需要以高可用性进行管理。

### 缺点 {#disadvantages}

更高的硬件和管理成本。

### 推荐的设备 {#recommended-equipment}

* 应用程序服务器：2 Ghz四核CPU、4 GB RAM、软件RAID 1 80 GB SATA硬盘。
* 重定向服务器：2 Ghz四核CPU、4 GB RAM、软件RAID 1 80 GB SATA硬盘。

>[!NOTE]
>
>可以针对流向重定向服务器的流量重用现有的负载平衡器。

## 安装和配置步骤 {#installation-and-configuration-steps}

### 先决条件 {#prerequisites}

* 两个应用程序服务器上的JDK，
* Web服务器(IIS、Apache)位于两个前端，
* 访问两个应用程序服务器上的数据库服务器，
* 通过POP3可访问的退回邮箱，
* 在负载平衡器上创建两个DNS别名：

   * 第一类是向公众开放，用于跟踪和指向虚拟IP地址(VIP)上的负载平衡器，然后将其分发到两个前端服务器，
   * 第二个IP地址向内部用户公开，以便通过控制台访问并指向虚拟IP地址(VIP)上的负载平衡器，然后将该负载平衡器分发到两个应用程序服务器。

* 配置为打开STMP (25)、DNS (53)、HTTP (80)、HTTPS (443)、SQL (1521(Oracle)、5432(PostgreSQL)等的防火墙 端口。 有关更多信息，请参阅一节 [数据库访问](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>如果您的应用程序服务器指向单个数据库实例，则在一个实例上导入标准包后，该包中包含的架构不会加载到另一个实例上。
>  
>如果您的应用程序服务器指向单个数据库实例，则更改一个实例上的架构后，该架构不会加载到另一个实例上。
>
>要恢复这些问题，您需要在发生错误的第二个实例上重新启动“web@default”进程。

### 安装和配置应用程序服务器1 {#installing-and-configuring-the-application-server-1}

在以下示例中，实例的参数包括：

* 实例名称：演示
* DNS掩码： tracking.campaign.net&#42;， console.campaign.net&#42; （应用程序服务器为客户端控制台连接和报告以及镜像页面和退订页面处理URL）
* 语言：英语
* 数据库： campaign：demo@dbsrv

安装第一台服务器的步骤如下：

1. 请按照Adobe Campaign服务器的安装过程操作： **nlserver** Linux或 **setup.exe** 在Windows上。

   有关更多信息，请参阅 [在Linux中安装Campaign的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux)和 [在Windows中安装Campaign的先决条件](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows)。

1. 安装Adobe Campaign服务器后，使用命令启动应用程序服务器(web) **nlserver web -tomcat** （通过Web模块，您可以在独立Web服务器模式下启动在端口8080上监听的Tomcat），并确保Tomcat正确启动：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >首次执行Web模块时，它将创建 **config-default.xml** 和 **serverConf.xml** 中的文件 **会议** 目录。 所有参数均可在 **serverConf.xml** 在此列出 [部分](../../installation/using/the-server-configuration-file.md).

   按 **Ctrl+C** 停止服务器。

   有关更多信息，请参阅以下章节：

   * 对于Linux： [服务器的首次启动](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * 对于Windows： [服务器的首次启动](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. 更改 **内部** 使用命令的密码：

   ```
   nlserver config -internalpassword
   ```

   如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 创建 **演示** 具有DNS掩码的实例进行跟踪(在本例中， **tracking.campaign.net**)和对客户端控制台的访问权限(在本例中， **console.campaign.net**)。 有两种方法可以做到这一点：

   * 通过控制台创建实例：

      ![](assets/install_create_new_connexion.png)

      有关更多信息，请参阅 [创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md).

      或者

   * 使用命令行创建实例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      有关更多信息，请参阅 [创建实例](../../installation/using/command-lines.md#creating-an-instance).

1. 编辑 **config-demo.xml** 文件(通过上一命令创建，位于 **config-default.xml** 文件)，检查 **mta** （投放）， **wfserver** （工作流）， **inMail** （退回邮件）和 **stat** (statistics)启用进程，然后配置进程的 **应用程序** 统计服务器：

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

   如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#enabling-processes)。

1. 编辑 **serverConf.xml** 文件并指定投放域，然后指定MTA模块用于响应MX类型DNS查询的DNS服务器的IP（或主机）地址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >此 **nameServer** 参数仅在Windows中使用。

   有关更多信息，请参阅 [Campaign服务器配置](../../installation/using/configuring-campaign-server.md).

1. 复制客户端控制台安装程序 **setup-client-7.XX**， **YYYY.exe** 到 **/datakit/nl/eng/jsp** 文件夹。 [了解详情](../../installation/using/client-console-availability-for-windows.md)。

1. 启动Adobe Campaign服务器(**网络启动nlserver6** 在Windows中， **/etc/init.d/nlserver6启动** （在Linux中）并运行命令 **nlserver pdump** 再次检查所有已启用的模块是否存在。

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

   此命令还让您知道计算机上安装的Adobe Campaign服务器的版本号和内部版本号。

1. 测试 **nlserver web** 模块使用URL： [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   通过此URL，可访问客户端设置程序的下载页面。 [了解详情](../../installation/using/client-console-availability-for-windows.md)。

   输入 **内部** 登录和关联的密码。

   ![](assets/s_ncs_install_access_client.png)

### 安装和配置应用程序服务器2 {#installing-and-configuring-the-application-server-2}

应用以下步骤：

1. 安装Adobe Campaign服务器。
1. 将您创建的实例的文件复制到应用程序服务器1上。

   我们保留与应用程序服务器1相同的实例名称。

1. 更改 **内部** 与应用程序服务器1相同。
1. 将数据库链接到实例：

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 编辑 **config-demo.xml** 文件(通过上一命令创建，位于 **config-default.xml** 文件)，检查 **mta** （投放）， **wfserver** （工作流）， **inMail** （退回邮件）和 **stat** (statistics)启用进程，然后配置进程的 **应用程序** 统计服务器：

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

   如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#enabling-processes)。

1. 编辑 **serverConf.xml** 文件和填充MTA模块的DNS配置：

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >此 **nameServer** 参数仅在Windows中使用。

   有关更多信息，请参阅 [Campaign服务器配置](../../installation/using/configuring-campaign-server.md).

1. 启动Adobe Campaign服务器。

   有关更多信息，请参阅以下章节：

   * 对于Linux： [服务器的首次启动](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * 对于Windows： [服务器的首次启动](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### 安装和配置前端服务器 {#installing-and-configuring-the-frontal-servers}

两台计算机上的安装和配置过程相同。

步骤如下：

1. 安装Adobe Campaign服务器，
1. 请遵循以下部分中描述的Web服务器集成过程(IIS、Apache)：

   * 对于Linux： [集成到Linux版Web服务器](../../installation/using/integration-into-a-web-server-for-linux.md)，
   * 对于Windows： [集成到Windows版Web服务器](../../installation/using/integration-into-a-web-server-for-windows.md).

1. 复制 **config-demo.xml** 和 **serverConf.xml** 在安装期间创建的文件。 在 **config-demo.xml** 文件，激活 **trackinglogd** 处理和取消激活 **mta**， **inmail**， **wfserver** 和 **stat** 流程。
1. 编辑 **serverConf.xml** 文件并在重定向参数中填充冗余跟踪服务器：

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. 启动网站并从URL测试重定向： [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   浏览器应显示以下消息（取决于负载平衡器重定向的URL）：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   或者

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   有关更多信息，请参阅以下章节：

   * 对于Linux： [启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)，
   * 对于Windows： [启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. 启动Adobe Campaign服务器。
