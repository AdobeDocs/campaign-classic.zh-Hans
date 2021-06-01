---
product: campaign
title: 在 Windows 中迁移到 Adobe Campaign 7
description: 在 Windows 中迁移到 Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 3743d018-3316-4ce3-ae1c-25760aaf5785
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 1%

---

# 在 Windows 中迁移到 Adobe Campaign 7{#migrating-in-windows-for-adobe-campaign}

## 一般过程{#general-procedure}

对于Windows，迁移步骤如下：

1. 停止服务：请参阅[服务停止](#service-stop)。
1. 备份数据库：请参阅[备份数据库和当前安装](#back-up-the-database-and-the-current-installation)。
1. 迁移平台：请参阅[部署Adobe Campaign v7](#deploying-adobe-campaign-v7)。
1. 迁移重定向服务器(IIS):请参阅[迁移重定向服务器(IIS)](#migrating-the-redirection-server--iis-)。
1. 重新启动服务：请参阅[重新启动服务](#re-starting-the-services)。
1. 删除和清除以前的Adobe Campaign版本：请参阅[删除和清理Adobe Campaign以前版本](#deleting-and-cleansing-adobe-campaign-previous-version)。

## 服务停止{#service-stop}

首先，在所有相关计算机上停止所有具有数据库访问权限的进程。

1. 必须使用重定向模块（**webmdl**&#x200B;服务）的所有服务器都必须停止。 对于IIS，运行以下命令：

   ```
   iisreset /stop
   ```

1. 必须使用以下命令停止&#x200B;**mta**&#x200B;模块及其子模块(**mtachild**):

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. 在所有服务器上停止Adobe Campaign服务。 使用管理员权限登录并运行以下命令：

   ```
   net stop nlserver6
   ```

   如果从v5.11迁移，请运行以下命令：

   ```
   net stop nlserver5
   ```

1. 对于每个服务器，确保正确停止Adobe Campaign服务。 使用管理员权限登录并运行以下命令：

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

1. 如果某些进程在几分钟后仍处于活动状态，您可以使用命令强制它们关闭：

   ```
   taskkill /F /IM nlserver* /T
   ```

## 备份数据库和当前安装{#back-up-the-database-and-the-current-installation}

此过程取决于您之前的Adobe Campaign版本。

### 从Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}迁移

1. 备份Adobe Campaign数据库。
1. 使用以下命令备份&#x200B;**Neolane v5**&#x200B;目录：

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您压缩&#x200B;**Neolane v5.back**&#x200B;文件夹，并将其保存在服务器以外的安全位置。

1. 在windows服务管理控制台中，禁用5.11应用程序服务器服务的自动启动。 您还可以使用以下命令：

   ```
   sc config nlserver5 start= disabled
   ```

1. 编辑&#x200B;**config-`<instance name>`.xml**（在&#x200B;**Neolane v5中）。 返回**&#x200B;文件夹)以阻止&#x200B;**mta**、**wfserver**、**stat**&#x200B;等。 服务自动启动。 例如，将&#x200B;**autoStart**&#x200B;替换为&#x200B;**_autoStart**。

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

### 从Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}迁移

1. 备份Adobe Campaign数据库。
1. 使用以下命令备份&#x200B;**Neolane v6**&#x200B;目录：

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您压缩&#x200B;**Neolane v6.back**&#x200B;文件夹，并将其保存在服务器以外的安全位置。

1. 在Windows服务管理器中，停用6.02应用程序服务器自动启动。 您还可以使用以下命令：

   ```
   sc config nlserver6 start= disabled
   ```

1. 编辑&#x200B;**config-`<instance name>`.xml**（在&#x200B;**Neolane v6中）。 返回**&#x200B;文件夹)以阻止&#x200B;**mta**、**wfserver**、**stat**&#x200B;等。 服务自动启动。 例如，将&#x200B;**autoStart**&#x200B;替换为&#x200B;**_autoStart**。

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

### 从Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}迁移

1. 备份Adobe Campaign数据库。
1. 使用以下命令备份&#x200B;**Adobe Campaign v6**&#x200B;目录：

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您压缩&#x200B;**Adobe Campaign v6.back**&#x200B;文件夹，并将其保存在服务器以外的安全位置。

1. 在windows服务管理控制台中，禁用6.11应用程序服务器服务的自动启动。 您还可以使用以下命令：

   ```
   sc config nlserver6 start= disabled
   ```

## 部署Adobe Campaign v7 {#deploying-adobe-campaign-v7}

部署Adobe Campaign包含两个阶段：

* 安装版本v7:必须对每台服务器执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 通过运行&#x200B;**setup.exe**&#x200B;安装文件来安装最新的Adobe Campaign v7内部版本。 有关在Windows中安装Adobe Campaign服务器的更多信息，请参阅[此部分](../../installation/using/installing-the-server.md)。

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7默认安装在&#x200B;**C:\Program Files\Adobe\Adobe Campaign v7**&#x200B;目录中。

1. 要使客户端控制台安装程序可用，请将&#x200B;**setup-client-7.0.XXXX.exe**&#x200B;文件复制到Adobe Campaign安装目录中：**C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**。

   >[!NOTE]
   >
   >有关在Windows中安装Adobe Campaign的更多信息，请参阅[此部分](../../installation/using/installing-the-server.md)。

1. 通过以下命令启动实例以供首次使用：

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >以下命令允许您创建Adobe Campaign v7内部文件系统：**conf**&#x200B;目录（具有&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;文件）、**var**&#x200B;目录等。

1. 通过&#x200B;**Neolane v5.back**、**Neolane v6.back**&#x200B;或&#x200B;**Adobe Campaign v6.back**&#x200B;备份文件复制并粘贴（覆盖）每个实例的配置文件和子文件夹（具体取决于您从迁移的版本 — 请参阅[此部分](#back-up-the-database-and-the-current-installation)）。
1. 根据您从迁移的版本，执行以下命令：

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
   >对于上述第一个命令，请勿复制&#x200B;**config-default.xml**&#x200B;文件。

1. 在Adobe Campaign v7的&#x200B;**serverConf.xml**&#x200B;和&#x200B;**config-default.xml**&#x200B;文件中，应用您在Adobe Campaign以前版本中的特定配置。 对于&#x200B;**serverConf.xml**&#x200B;文件，请使用&#x200B;**Neolane v5/conf/serverConf.xml.diff**、**Neolane v6/conf/serverConf.xml.diff**&#x200B;或&#x200B;**Adobe Campaign v6/conf/serverConf.xml.diff**&#x200B;文件。

   >[!NOTE]
   >
   >在将配置从Adobe Campaign的先前版本报告到Adobe Campaign v7时，请确保物理目录的路径指向Adobe Campaign v7(而不是Neolane v5、Neolane v6或Adobe Campaign v6)。

1. 使用以下命令重新加载Adobe Campaign v7配置：

   ```
   nlserver config -reload
   ```

1. 使用以下命令启动升级后进程：

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>尚未启动Adobe Campaign服务：需要对IIS进行一些更改。

## 迁移重定向服务器(IIS){#migrating-the-redirection-server--iis-}

此时，必须停止IIS服务器。 请参阅[服务停止](#service-stop)。

1. 打开&#x200B;**Internet信息服务(IIS)管理器**&#x200B;控制台。
1. 更改用于Adobe Campaign早期版本的站点的绑定（侦听端口）：

   * 右键单击用于Adobe Campaign早期版本的站点，然后选择&#x200B;**[!UICONTROL Edit bindings]**。
   * 对于每种类型的监听端口（**[!UICONTROL http]**&#x200B;和/或&#x200B;**[!UICONTROL https]**），选择相应的行并单击&#x200B;**[!UICONTROL Edit]**。
   * 输入其他端口。 默认情况下， http的侦听端口为80,https的侦听端口为443。 检查新端口是否可用。

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >如果您的IIS服务器包含多个具有高级配置（共享端口和不同的IP地址）的Adobe Campaign网站，请联系您的管理员。

1. 为Adobe Campaign v7创建新网站：

   * 右键单击&#x200B;**[!UICONTROL Sites]**&#x200B;文件夹并选择&#x200B;**[!UICONTROL Add Web Site...]**。

      ![](assets/_migration_iis_4.png)

   * 输入站点名称，例如&#x200B;**Adobe Campaign v7**。
   * 不使用网站基本目录的访问路径，但必须输入&#x200B;**[!UICONTROL Physical access path]**&#x200B;字段。 输入默认IIS访问路径：**C:\inetpub\wwwroot**。
   * 单击&#x200B;**[!UICONTROL Connect as...]**&#x200B;作为按钮，并确保已选择&#x200B;**[!UICONTROL Application user]**&#x200B;选项。
   * 您可以保留&#x200B;**[!UICONTROL IP address]**&#x200B;和&#x200B;**[!UICONTROL Port]**&#x200B;字段中的默认值。 如果要使用其他值，请确保IP地址和/或端口可用。
   * 选中&#x200B;**[!UICONTROL Start Web site immediately]**&#x200B;框。

      ![](assets/_migration_iis_5_7.png)

1. 执行&#x200B;**iis_neolane_setup.vbs**&#x200B;脚本，以自动配置Adobe Campaign服务器在之前创建的虚拟目录上使用的资源。

   * 此文件位于&#x200B;**`[Adobe Campaign v7]`\conf**&#x200B;目录中，其中&#x200B;**`[Adobe Campaign v7]`**&#x200B;是Adobe Campaign安装目录的访问路径。 用于执行脚本的命令如下（对于管理员）：

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
      cscript iis_neolane_setup.vbs
      ```

   * 单击&#x200B;**[!UICONTROL OK]**&#x200B;以确认脚本执行。

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * 输入之前为Adobe Campaign v7创建的网站编号，然后单击&#x200B;**[!UICONTROL OK]**。

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * 此时应会显示一条确认消息：

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * 在&#x200B;**[!UICONTROL Content view]**&#x200B;选项卡中，确保使用Adobe Campaign资源正确配置了网站配置：

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >如果未显示树结构，请重新启动IIS。
      >
      >[此部分](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server)中详细介绍了以下IIS配置步骤。

## 安全区{#security-zones}

如果您是从v6.02或更低版本迁移，则必须先配置安全区，然后才能启动服务。 有关更多信息，请参阅[Security](../../migration/using/general-configurations.md#security)。

## 重新启动服务{#re-starting-the-services}

在以下每个服务器上启动IIS和Adobe Campaign服务：

1. 跟踪和重定向服务器。
1. 中间源服务器.
1. 营销服务器。

在执行下一步之前，请对新安装运行完整测试，确保没有回归，并且所有操作都可以遵循[常规配置](../../migration/using/general-configurations.md)部分中的所有建议。

## 删除和清理Adobe Campaign早期版本{#deleting-and-cleansing-adobe-campaign-previous-version}

此过程取决于您之前的Adobe Campaign版本。

### Adobe Campaign v5 {#adobe-campaign-v5}

在删除和清除Adobe Campaign v5安装之前，必须应用以下建议：

* 让功能团队对新安装进行完整检查。
* 只有在您确定不需要回滚时，才卸载Adobe Campaign v5。

1. 在IIS中，删除&#x200B;**Neolane v5**&#x200B;网站，然后删除&#x200B;**Neolane v5**&#x200B;应用程序池。
1. 将&#x200B;**Neolane v5.back**&#x200B;文件夹重命名为&#x200B;**Neolane v5**。
1. 使用“添加/删除组件”向导卸载Adobe Campaign v5。

   ![](assets/migration_wizard_2.png)

1. 使用以下命令删除&#x200B;**nlserver5** Windows服务：

   ```
   sc delete nlserver5
   ```

1. 重新启动服务器。

### Adobe Campaign v6.02 {#adobe-campaign-v6-02}

在删除和清除Adobe Campaign v6.02安装之前，必须应用以下建议：

* 让功能团队对新安装进行完整检查。
* 只有在您确定不需要回滚时，才卸载Adobe Campaign v6.02。

1. 在IIS中，删除&#x200B;**Neolane v6**&#x200B;网站，然后删除&#x200B;**Neolane v6**&#x200B;应用程序池。
1. 将&#x200B;**Neolane v6.back**&#x200B;文件夹重命名为&#x200B;**Neolane v6**。
1. 使用“添加/删除组件”向导卸载Adobe Campaign v6.02。

   ![](assets/migration_wizard_2.png)

1. 重新启动服务器。

### Adobe Campaign v6.1 {#adobe-campaign-v6-1}

在删除和清除Adobe Campaign v6安装之前，必须应用以下建议：

* 让功能团队对新安装进行完整检查。
* 只有在您确定不需要回滚时，才卸载Adobe Campaign v6。

1. 在IIS中，删除&#x200B;**Adobe Campaign v6**&#x200B;网站，然后删除&#x200B;**Adobe Campaign v6**&#x200B;应用程序池。
1. 将&#x200B;**Adobe Campaign v6.back**&#x200B;文件夹重命名为&#x200B;**Adobe Campaign v6**。
1. 使用“添加/删除组件”向导卸载Adobe Campaign v6。

   ![](assets/migration_wizard_2.png)

1. 重新启动服务器。
