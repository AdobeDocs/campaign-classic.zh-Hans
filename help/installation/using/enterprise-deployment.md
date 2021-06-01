---
product: campaign
title: 企业部署
description: 企业部署
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1221'
ht-degree: 3%

---

# 企业部署{#enterprise-deployment}

这是最完整的配置。 它以标准配置为基础，以提高安全性和可用性：

* 在HTTP或TCP负载平衡器后面的专用重定向服务器，用于实现可扩展性和可用性，
* 两个应用程序服务器，用于提高吞吐量和故障转移能力（容错），它们在LAN中被隔离。

服务器和进程之间的一般通信按照以下模式进行：

![](assets/s_901_ncs_install_enterpriseconfig.png)

使用此类配置，通过适当的带宽和调整，预期吞吐量可能会超过每小时100,000封邮件。

## 功能 {#features}

### 优势 {#advantages}

* 优化的安全性：只有需要暴露到外部的服务器才安装在DMZ的计算机上。
* 高可用性更容易确保：只需要考虑从外部可见的计算机，并考虑高可用性。

### 缺点 {#disadvantages}

硬件和管理成本更高。

### 推荐设备{#recommended-equipment}

* 应用程序服务器：2 Ghz四核CPU，4 GB RAM，软件RAID 1 80 GB SATA硬盘。
* 重定向服务器：2 Ghz四核CPU，4 GB RAM，软件RAID 1 80 GB SATA硬盘。

>[!NOTE]
>
>可以重复使用现有的负载平衡器，以便将流量重定向到重定向服务器。

## 安装和配置步骤{#installation-and-configuration-steps}

### 先决条件 {#prerequisites}

* 两个应用程序服务器上的JDK，
* 两个前端上的Web服务器(IIS、Apache),
* 访问两个应用程序服务器上的数据库服务器，
* 可通过POP3访问退回邮箱，
* 在负载平衡器上创建两个DNS别名：

   * 首次公开以跟踪虚拟IP地址(VIP)上的负载平衡器并指向该负载平衡器，然后该负载平衡器被分发到两个前端服务器，
   * 第二个向内部用户公开，以供通过控制台访问，并指向虚拟IP地址(VIP)上的负载平衡器，然后该负载平衡器被分发到两个应用程序服务器。

* 防火墙配置为打开STMP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL(1521 for Oracle、5432 for PostgreSQL等) 端口。 有关详细信息，请参阅[数据库访问](../../installation/using/network-configuration.md#database-access)一节。

>[!CAUTION]
>
>如果应用程序服务器指向单个数据库实例，则在一个实例上导入标准包后，该包中包含的架构不会加载到另一个实例上。
>  
>如果应用程序服务器指向单个数据库实例，则在更改一个实例上的架构后，该架构不会加载到另一个实例上。
>
>要恢复这些问题，您需要在发生错误的第二个实例上重新启动“web@default”进程。

### 安装和配置应用程序服务器1 {#installing-and-configuring-the-application-server-1}

在以下示例中，实例的参数为：

* 实例的名称：演示
* DNS掩码：tracking.campaign.net*、console.campaign.net*（应用程序服务器处理客户端控制台连接和报表以及镜像页面和退订页面的URL）
* 语言：英语
* 数据库：campaign:demo@dbsrv

安装第一台服务器的步骤如下：

1. 按照Adobe Campaign服务器的安装过程操作：Linux上的&#x200B;**nlserver**&#x200B;包或Windows上的&#x200B;**setup.exe**&#x200B;包。

   有关更多信息，请参阅[在Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)(Linux)中安装Campaign的先决条件和[在Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)(Windows)中安装Campaign的先决条件。

1. 安装Adobe Campaign服务器后，使用命令&#x200B;**nlserver web -tomcat**&#x200B;启动应用程序服务器（Web模块允许您在端口8080上的独立Web服务器模式下启动Tomcat），并确保Tomcat正确启动：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >首次执行Web模块时，会在安装文件夹下的&#x200B;**conf**&#x200B;目录下创建&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;文件。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

   按&#x200B;**Ctrl+C**&#x200B;以停止服务器。

   有关更多信息，请参阅以下章节：

   * 对于Linux:[服务器的首次启动](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * 对于Windows:[服务器的首次启动](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. 使用命令更改&#x200B;**internal**&#x200B;密码：

   ```
   nlserver config -internalpassword
   ```

   如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 使用DNS掩码创建&#x200B;**demo**&#x200B;实例，以便进行跟踪（在本例中为&#x200B;**tracking.campaign.net**）并访问客户端控制台（在本例中为&#x200B;**console.campaign.net**）。 可以通过两种方式来执行此操作：

   * 通过控制台创建实例：

      ![](assets/install_create_new_connexion.png)

      有关更多信息，请参阅[创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md)。

      或者

   * 使用命令行创建实例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      有关更多信息，请参阅[创建实例](../../installation/using/command-lines.md#creating-an-instance)。

1. 编辑&#x200B;**config-demo.xml**&#x200B;文件（通过前一命令创建，位于&#x200B;**config-default.xml**&#x200B;文件旁边），检查&#x200B;**mta**（投放）、**wfserver**（工作流）、**inMail**（邮件反弹）和&#x200B;****（统计）进程是否已启用，然后配置&#x200B;**a13统计信息服务器：**

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

1. 编辑&#x200B;**serverConf.xml**&#x200B;文件并指定提交域，然后指定MTA模块用于回答MX类型DNS查询的DNS服务器的IP（或主机）地址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >**nameServers**&#x200B;参数仅在Windows中使用。

   有关更多信息，请参阅[Campaign服务器配置](../../installation/using/configuring-campaign-server.md)。

1. 将客户端控制台安装程序(**setup-client-7.XX**, **YYYY.exe**(v7或&#x200B;**setup-client-6.XX**, **YYYY.exe**(v6.1))复制到&#x200B;**/datakit/nl/eng/jsp**&#x200B;文件夹。 [了解详情](../../installation/using/client-console-availability-for-windows.md)。

1. 启动Adobe Campaign服务器(在Windows中&#x200B;**net start nlserver6**，在Linux中&#x200B;**/etc/init.d/nlserver6 start**)，然后再次运行命令&#x200B;**nlserver pdump**&#x200B;以检查是否存在所有已启用的模块。

   >[!NOTE]
   >
   >从20.1开始，我们建议改用以下命令（对于Linux）：**systemctl启动nlserver**


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

1. 使用URL测试&#x200B;**nlserver web**&#x200B;模块：[https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test)。

   此URL允许您访问客户端安装程序的下载页面。 [了解详情](../../installation/using/client-console-availability-for-windows.md)。

   在访问访问控制页面时，输入&#x200B;**internal**&#x200B;登录和关联的密码。

   ![](assets/s_ncs_install_access_client.png)

### 安装和配置应用程序服务器2 {#installing-and-configuring-the-application-server-2}

应用以下步骤：

1. 安装Adobe Campaign服务器。
1. 将您创建的实例的文件复制到应用程序服务器1中。

   我们保留与应用程序服务器1相同的实例名称。

1. 将&#x200B;**内部**&#x200B;更改为与应用程序服务器1相同。
1. 将数据库链接到实例：

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 编辑&#x200B;**config-demo.xml**&#x200B;文件（通过前一命令创建，位于&#x200B;**config-default.xml**&#x200B;文件旁边），检查&#x200B;**mta**（投放）、**wfserver**（工作流）、**inMail**（邮件反弹）和&#x200B;****（统计）进程是否已启用，然后配置&#x200B;**a13统计信息服务器：**

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

1. 编辑&#x200B;**serverConf.xml**&#x200B;文件并填充MTA模块的DNS配置：

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >**nameServers**&#x200B;参数仅在Windows中使用。

   有关更多信息，请参阅[Campaign服务器配置](../../installation/using/configuring-campaign-server.md)。

1. 启动Adobe Campaign服务器。

   有关更多信息，请参阅以下章节：

   * 对于Linux:[服务器的首次启动](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * 对于Windows:[服务器的首次启动](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### 安装和配置前端服务器{#installing-and-configuring-the-frontal-servers}

在两台计算机上的安装和配置过程是相同的。

步骤如下：

1. 安装Adobe Campaign服务器，
1. 遵循以下部分中所述的Web服务器集成过程(IIS、Apache):

   * 对于Linux:[集成到Linux的Web服务器](../../installation/using/integration-into-a-web-server-for-linux.md)中，
   * 对于Windows:[集成到Windows的Web服务器](../../installation/using/integration-into-a-web-server-for-windows.md)。

1. 复制在安装期间创建的&#x200B;**config-demo.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;文件。 在&#x200B;**config-demo.xml**&#x200B;文件中，激活&#x200B;**trackinglogd**&#x200B;进程并停用&#x200B;**mta**、**inmail**、**wfserver**&#x200B;和&#x200B;**stat**&#x200B;进程。
1. 编辑&#x200B;**serverConf.xml**&#x200B;文件，并在重定向的参数中填充冗余跟踪服务器：

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. 启动网站并测试从URL发出的重定向：[https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   浏览器应显示以下消息（具体取决于负载平衡器重定向的URL）：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   或者

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   有关更多信息，请参阅以下章节：

   * 对于Linux:[启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * 对于Windows:[启动Web服务器并测试配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)。

1. 启动Adobe Campaign服务器。
