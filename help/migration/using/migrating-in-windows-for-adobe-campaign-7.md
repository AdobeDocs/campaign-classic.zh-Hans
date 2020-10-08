---
title: 在 Windows 中迁移到 Adobe Campaign 7
seo-title: 在 Windows 中迁移到 Adobe Campaign 7
description: 在 Windows 中迁移到 Adobe Campaign 7
seo-description: null
page-status-flag: never-activated
uuid: 74464400-bdd4-42f8-bcbe-ace7095ae4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: f459dc07-b7db-4526-b428-852b51c9c00e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1541'
ht-degree: 1%

---


# 在 Windows 中迁移到 Adobe Campaign 7{#migrating-in-windows-for-adobe-campaign}

## 一般程序 {#general-procedure}

对于Windows，迁移步骤如下：

1. 停止服务：请参阅 [服务停止](#service-stop)。
1. 备份数据库：请参阅 [备份数据库和当前安装](#back-up-the-database-and-the-current-installation)。
1. 迁移平台：请参阅 [部署Adobe Campaignv7](#deploying-adobe-campaign-v7)。
1. 迁移重定向服务器(IIS):请参阅 [迁移重定向服务器(IIS)](#migrating-the-redirection-server--iis-)。
1. 重新开始服务：请参阅 [重新启动服务](#re-starting-the-services)。
1. 删除和清除以前的Adobe Campaign版本：请参阅删 [除和清理Adobe Campaign先前版本](#deleting-and-cleansing-adobe-campaign-previous-version)。

## 服务停止 {#service-stop}

首先，通过访问相关所有计算机上的数据库来停止所有进程。

1. 必须使用重定向模块(**webmdl** 服务)的所有服务器都必须停止。 对于IIS，运行以下命令：

   ```
   iisreset /stop
   ```

1. 必须使用 **以下命** 令&#x200B;**，必须停止mta模块及其子模**&#x200B;块(mtachild):

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. 停止所有服务器上的Adobe Campaign服务。 使用管理员权限登录并运行以下命令：

   ```
   net stop nlserver6
   ```

   如果您是从v5.11迁移，请运行以下命令：

   ```
   net stop nlserver5
   ```

1. 对于每台服务器，确保正确停止Adobe Campaign服务。 使用管理员权限登录并运行以下命令：

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   将显示活动进程的列表及其ID(PID)。

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. 如果一个或多个Adobe Campaign进程在几分钟后仍处于活动状态或被阻止状态，请终止它们。 使用管理员权限登录并运行以下命令：

   ```
   taskkill /IM nlserver* /T
   ```

1. 如果某些进程在几分钟后仍处于活动状态，则可以使用命令强制它们关闭：

   ```
   taskkill /F /IM nlserver* /T
   ```

## 备份数据库和当前安装 {#back-up-the-database-and-the-current-installation}

该过程取决于您的Adobe Campaign先前版本。

### 从Adobe Campaignv5.11迁移 {#migrating-from-adobe-campaign-v5-11}

1. 备份Adobe Campaign库。
1. 使用以下命令 **备份Neolane v** 5目录：

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您将Neolane v5. **back文件夹压缩** ，并将其保存到服务器以外的安全位置。

1. 在windows服务管理控制台中，禁用5.11应用程序服务器服务的自动启动。 您还可以使用以下命令：

   ```
   sc config nlserver5 start= disabled
   ```

1. 编辑 **config-`<instance name>`.xml** (在 **Neolane v5中)。 返回** 文件夹)，以 **防止mta**、 **wfserver**、 **stat**&#x200B;等。 服务自动启动。 例如，将autoStart **替换****为_autoStart**。

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### 从Adobe Campaignv6.02迁移 {#migrating-from-adobe-campaign-v6-02}

1. 备份Adobe Campaign库。
1. 使用以下命令 **备份Neolane v** 6目录：

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您将Neolane v6. **back文件夹压缩** ，并将其保存到服务器以外的安全位置。

1. 在Windows服务管理器中，取消激活6.02应用程序服务器自动启动。 您还可以使用以下命令：

   ```
   sc config nlserver6 start= disabled
   ```

1. 编辑 **config-`<instance name>`.xml** (在 **Neolane v6中)。 返回** 文件夹)，以 **防止mta**、 **wfserver**、 **stat**&#x200B;等。 服务自动启动。 例如，将autoStart **替换****为_autoStart**。

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword" provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### 从Adobe Campaignv6.1迁移 {#migrating-from-adobe-campaign-v6-1}

1. 备份Adobe Campaign库。
1. 使用以下命令 **备份Adobe Campaignv** 6目录：

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您压缩 **Adobe Campaignv6.back文件夹** ，并将其保存到服务器以外的安全位置。

1. 在windows服务管理控制台中，禁用6.11应用程序服务器服务的自动启动。 您还可以使用以下命令：

   ```
   sc config nlserver6 start= disabled
   ```

## 部署Adobe Campaignv7 {#deploying-adobe-campaign-v7}

部署Adobe Campaign涉及两个阶段：

* 正在安装版本v7:必须在每台服务器上执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 运行setup.exe安装文件，安装最新的 **Adobe Campaignv** 7版本。 有关在Windows中安装Adobe Campaign服务器的详细信息，请参 [阅本节](../../installation/using/installing-the-server.md)。

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaignv7默认安装在C:\Program Files\Adobe\Adobe Campaign v7 **目录** 中。

1. 要使客户端控制台安装项目可 **用，请将setup-client-7.0.XXXX.exe文件复制到Adobe Campaign安装目录中** : **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**。

   >[!NOTE]
   >
   >有关在Windows中安装Adobe Campaign的详细信息，请参 [阅此部分](../../installation/using/installing-the-server.md)。

1. 将实例开始为首次使用，并使用以下命令：

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >通过这些命令可以创建Adobe Campaignv7内部文件系统： **conf** 目录( **带有config-default** .xml和 **serverConf.xml文件)** 、 **var** 目录等。

1. 通过Neolane v5.back、Neolane v6.back或 **Adobe Campaignv6.back备份文件(具体取决于您从迁移的版本——请参阅本节的**)复制和粘贴(覆 **盖)每个实例的配置文件和子文******[](#back-up-the-database-and-the-current-installation)件夹。
1. 根据要迁移的版本，执行以下命令：

   ```
   copy "Neolane v5.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v5.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v5.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Neolane v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Adobe Campaign v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Adobe Campaign v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Adobe Campaign v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   >[!IMPORTANT]
   >
   >对于以上第一个命令，请不 **要复制config-default.xml文件** 。

1. 在Adobe Campaign **v7的serverConf** .xml **** 和config-default.xml文件中，应用您在Adobe Campaign先前版本中的特定配置。 对于 **serverConf.xml** 文件，请使用 **Neolane v5/conf/serverConf.xml.diff**、 **Neolane v6/conf/serverConf.xml.diff** 或 **** Adobe Campaignv6/conf/serverConf.xml.diff文件。

   >[!NOTE]
   >
   >当报告配置从Adobe Campaign先前版本到Adobe Campaignv7时，请确保物理目录的路径导致Adobe Campaignv7(而非Neolane v5、Neolane v6或Adobe Campaignv6)。

1. 使用以下命令重新加载Adobe Campaignv7配置：

   ```
   nlserver config -reload
   ```

1. 使用以下命令开始postupgrade进程：

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>尚未开始Adobe Campaign服务：需要对IIS进行一些更改。

## 迁移重定向服务器(IIS) {#migrating-the-redirection-server--iis-}

此阶段必须停止IIS服务器。 请参阅 [服务停止](#service-stop)。

1. 打开 **Internet信息服务(IIS)管理器控制台** 。
1. 更改用于Adobe Campaign先前版本的站点的绑定（侦听端口）:

   * 右键单击用于Adobe Campaign先前版本的站点，然后选择 **[!UICONTROL Edit bindings]**。
   * 对于每种类型的监听端口(**[!UICONTROL http]** 和/ **[!UICONTROL https]**&#x200B;或)，选择相应的行并单击 **[!UICONTROL Edit]**。
   * 输入其他端口。 默认情况下，侦听端口为80(http)和443(https)。 检查新端口是否可用。

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >如果您的IIS服务器包含多个用于Adobe Campaign的网站，并具有高级配置（共享端口和不同的IP地址），请与管理员联系。

1. 为Adobe Campaignv7创建新网站：

   * 右键单击文件夹 **[!UICONTROL Sites]** 并选择 **[!UICONTROL Add Web Site...]**。

      ![](assets/_migration_iis_4.png)

   * 输入站点的名称， **Adobe Campaignv** 7作为实例。
   * 不使用网站基本目录的访问路径，但必 **[!UICONTROL Physical access path]** 须输入字段。 输入默认的IIS访问路径： **C:\inetpub\wwwroot**。
   * 单击“ **[!UICONTROL Connect as...]** 作为”按钮，并确保选 **[!UICONTROL Application user]** 择了该选项。
   * 您可以在和字段中保留默 **[!UICONTROL IP address]** 认 **[!UICONTROL Port]** 值。 如果要使用其他值，请确保IP地址和／或端口可用。
   * 选中 **[!UICONTROL Start Web site immediately]** 框。

      ![](assets/_migration_iis_5_7.png)

1. 执行 **iis_neolane_setup.vbs脚本** ，以自动配置Adobe Campaign服务器在先前创建的虚拟目录上使用的资源。

   * 此文件位于\tomcat-7\conf file **`[Adobe Campaign v7]`中**, **`[Adobe Campaign v7]`** 其中是Adobe Campaign安装目录的访问路径。 用于执行脚本的命令如下所示（对于管理员）:

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\tomcat-7\conf
      cscript iis_neolane_setup.vbs
      ```

   * 单击 **[!UICONTROL OK]** 以确认脚本执行。

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * 输入之前为Adobe Campaignv7创建的网站编号，然后单击 **[!UICONTROL OK]**。

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * 应显示确认消息：

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * 在选项卡 **[!UICONTROL Content view]** 中，确保已正确配置网站配置Adobe Campaign资源：

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >如果未显示树结构，请重新开始IIS。
      >
      >本节详细介绍了以下IIS [配置步骤](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server)。

## 安全区 {#security-zones}

如果您是从v6.02或更低版本迁移的，则必须先配置安全区域，然后才能启动服务。 有关详细信息，请参阅 [安全性](../../migration/using/general-configurations.md#security)。

## 重新启动服务 {#re-starting-the-services}

开始下列每台服务器上的IIS和Adobe Campaign服务：

1. 跟踪和重定向服务器。
1. 中间源服务器.
1. 营销服务器。

在执行下一步之前，请对新安装运行完整测试，确保没有回归，并且所有功能都可以遵循“常规配置”部分中的所有建议 [来工作](../../migration/using/general-configurations.md) 。

## 删除和清理Adobe Campaign先前版本 {#deleting-and-cleansing-adobe-campaign-previous-version}

该过程取决于您的Adobe Campaign先前版本。

### Adobe Campaign v5 {#adobe-campaign-v5}

在删除和清除Adobe Campaignv5安装之前，必须应用以下建议：

* 让功能团队对新安装进行完整检查。
* 只有确定不需要回滚时，才能卸载Adobe Campaignv5。

1. 在IIS中，删除 **Neolane v5网站** ，然后删 **除Neolane v5应用程** 序池。
1. 将Neolane v **5.back文件夹重命** 名为 **Neolane v5**。
1. 使用“添加／删除组件”向导卸载Adobe Campaignv5。

   ![](assets/migration_wizard_2.png)

1. 使用以下 **命令删除** nlserver5 Windows服务：

   ```
   sc delete nlserver5
   ```

1. 重新开始服务器。

### Adobe Campaign v6.02 {#adobe-campaign-v6-02}

在删除和清除Adobe Campaignv6.02安装之前，必须应用以下建议：

* 让功能团队对新安装进行完整检查。
* 只有在您确定不需要回滚时卸载Adobe Campaignv6.02。

1. 在IIS中，删除 **Neolane v6网站** ，然后删 **除Neolane v6应用程** 序池。
1. 将Neolane v **6.back文件夹重命** 名为 **Neolane v6**。
1. 使用“添加／删除组件”向导卸载Adobe Campaignv6.02。

   ![](assets/migration_wizard_2.png)

1. 重新开始服务器。

### Adobe Campaign v6.1 {#adobe-campaign-v6-1}

在删除和清除Adobe Campaignv6安装之前，必须应用以下建议：

* 让功能团队对新安装进行完整检查。
* 只有在确定不需要回滚时卸载Adobe Campaignv6。

1. 在IIS中，删除 **Adobe Campaignv6网站** ，然后删 **除Adobe Campaignv6应** 用程序池。
1. 将 **Adobe Campaignv6.back文件夹重命** 名为 **Adobe Campaignv6**。
1. 使用“添加／删除组件”向导卸载Adobe Campaignv6。

   ![](assets/migration_wizard_2.png)

1. 重新开始服务器。

