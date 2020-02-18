---
title: 在Linux中迁移以用于Adobe Campaign v7
seo-title: 在Linux中迁移以用于Adobe Campaign v7
description: 在Linux中迁移以用于Adobe Campaign v7
seo-description: null
page-status-flag: never-activated
uuid: 47870ea4-b07b-4db7-8094-7a8b6f4b6936
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: 8f6519e8-5c8d-4974-b193-a9f1cf78b3a3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# 在Linux中迁移以用于Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## 一般程序 {#general-procedure}

Linux中的迁移步骤如下：

1. 停止服务：请参 [阅服务停止](#service-stop)。
1. 保存数据库：请参 [阅备份数据库和现有安装](#back-up-the-database-and-the-existing-installation)。
1. 卸载以前的Adobe Campaign版本包：请参 [阅卸载Adobe Campaign先前版本的包](#uninstalling-adobe-campaign-previous-version-packages)。
1. 迁移平台：请参阅 [部署Adobe Campaign v7](#deploying-adobe-campaign-v7)。
1. 重新启动服务：请参阅 [重新启动服务](#re-starting-services)。

## 服务停止 {#service-stop}

首先，通过访问相关所有计算机上的数据库来停止所有进程。

1. 以root身份登录 ****。
1. 需要停止使用重定向模块(**webmdl** 服务)的所有服务器。 对于Apache，运行以下命令：

   ```
   /etc/init.d/apache2 stop
   ```

1. 以root用户身份再次 **登录**。
1. 在所有服务器上停止Adobe Campaign先前版本的服务。

   ```
   /etc/init.d/nlserver6 stop
   ```

   如果您是从v5.11迁移，请运行以下命令：

   ```
   /etc/init.d/nlserver5 stop
   ```

1. 确保在每台服务器上停止Adobe Campaign服务。

   ```
   ps waux | grep nlserver
   ```

   活动进程的列表会与其ID(PID)一起显示。

1. 如果一个或多个Adobe Campaign进程在几分钟后仍处于活动状态或被阻止状态，请将其终止。

   ```
   killall nlserver
   ```

1. 如果某些进程在几分钟后仍处于活动状态，则可以使用命令强制它们关闭：

   ```
   killall -9 nlserver
   ```

## 备份数据库和现有安装 {#back-up-the-database-and-the-existing-installation}

该过程取决于您的Adobe Campaign先前版本。

### 从Adobe Campaign v5.11迁移 {#migrating-from-adobe-campaign-v5-11}

1. 备份Adobe Campaign数据库。
1. 以Neolane身 **份登录** ，然后使用以下命令备份 **nl5** 目录：

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您将 **nl5.back文件夹压缩** ，并将其保存到服务器以外的安全位置。

1. 编辑 **config-`<instance name>`.xml** (在 **nl5.back** 文件夹中)，以防止mta ************ 、wfserver、Stat等。 服务自动启动。 例如，将autoStart **替换为** _autoStart **(仍为** neolane ****)。

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

### 从Adobe Campaign v6.02迁移 {#migrating-from-adobe-campaign-v6-02}

1. 备份Adobe Campaign数据库。
1. 以Neolane身 **份登录** ，然后使用以下命令备份 **nl6** 目录：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您将 **nl6.back文件夹压缩** ，并将其保存到服务器以外的安全位置。

1. 编辑 **config-`<instance name>`.xml** (在 **nl6.back** 文件夹中)，以防止mta ************、wfstat服务器、Stat服务器、Etc. 服务自动启动。 例如，将autoStart **替换为****_autoStart** (仍作为 **Adobe Campaign**)。

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

### 从Adobe Campaign v6.1迁移 {#migrating-from-adobe-campaign-v6-1}

1. 备份Adobe Campaign数据库。
1. 以Neolane身 **份登录** ，然后使用以下命令备份 **nl6** 目录：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您将 **nl6.back文件夹压缩** ，并将其保存到服务器以外的安全位置。

## 卸载Adobe Campaign先前版本包 {#uninstalling-adobe-campaign-previous-version-packages}

该过程取决于您的Adobe Campaign先前版本。

### 卸载Adobe Campaign v5包 {#uninstalling-adobe-campaign-v5-packages}

1. 以root身份登录 ****。
1. 识别使用以下命令安装的Adobe Campaign包。

   * 在德 **比亚**:

      ```
      dpkg -l | grep nl
      ```

      此时将显示已安装包的列表：

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * 在 **Red Hat中**:

      ```
      rpm -qa | grep nl
      ```

1. 卸载Adobe Campaign v5包。

   * 在德 **比亚**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * 在 **Red Hat中**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### 卸载Adobe Campaign v6包 {#uninstalling-adobe-campaign-v6-packages}

本节介绍如何卸载Adobe Campaign v6.02或v6.1包。

1. 以root身份登录 ****。
1. 识别使用以下命令安装的Adobe Campaign包。

   * 在德 **比亚**:

      ```
      dpkg -l | grep nl
      ```

      此时将显示已安装包的列表：

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * 在 **Red Hat中**:

      ```
      rpm -qa | grep nl
      ```

1. 卸载Adobe Campaign v6包。

   * 在德 **比亚**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * 在 **Red Hat中**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## 部署Adobe Campaign v7 {#deploying-adobe-campaign-v7}

该过程取决于您的Adobe Campaign先前版本。

### 从Adobe Campaign v5.11迁移 {#migrating-from-adobe-campaign-v5_11-1}

部署Adobe Campaign涉及两个阶段：

* 安装Adobe Campaign v7包：必须在每台服务器上执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaign v7包：

   * 在德 **比亚**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * 在 **Red Hat中**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >必须成功安装包，然后才能继续执行下一步。

   >[!NOTE]
   >
   >从v5.11迁移时，Adobe Campaign默认安装在 **/usr/local/neolane/nl6/** directory中。
   >
   >安装包后，将显示以下消息：“ **WdbcTimeZone”选项缺失**。 这很正常。

1. 要使客户端控制台安装程序可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参阅 [本节](../../installation/using/installing-campaign-standard-packages.md)。

1. 修改与 **Neolane用户匹配** 的。bashrd **文件** 。 以Neolane身份登 **录** ，然后运行以下命令：

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >当您以Neolane身份登录 **时**，将显示以下消息： **nl5/env.sh:没有此类文件或目录**。 这很正常。

   在文件末尾，将nl5/env.sh **替换为****nl6/env.sh**。

1. 以root用户身 **份登录** ，然后使用以下命令准备实例：

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >通过这些命令，您可以创建Adobe Campaign v6内部文件系统： **conf目录(带有** config-default.xml **和** serverConf.xml文件), **var目****** 录。

1. 转到 **nl5.back** backup文件夹，并复制（覆盖）每个实例的配置文件和子文件夹。 以Neolane身份登录 **** ，然后运行以下命令：

   >[!IMPORTANT]
   >
   >对于以下第一个命令，请勿复制 **config-default.xml文件** 。

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. 在Adobe Campaign v7 serverConf.xml **和config-default** .xml文件 **** 中，应用您对Adobe Campaign v5的特定配置。 对于 **serverConf.xml文件** ，请使用 **nl5/conf/serverConf.xml.diff文件** 。

   >[!NOTE]
   >
   >在报告从Adobe Campaign v5到Adobe Campaign v7的配置时，请确保物理目录的路径指向Adobe Campaign v7，而不是Adobe Campaign v5。

1. 由于迁移不是通用安装，您需要强制重新启动 **trackinglogd服务** 。 为此，请打开 **nl6/conf/config-default.xml** 文件，并确保 **trackinglogd** service is activated（仅在跟踪／重定向服务器上）:

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果跟 **踪服务器上未启动** trackinglogd服务，则不会转发跟踪信息。

1. 使用以下命令重新加载Adobe Campaign v7配置：

   ```
   nlserver config -reload
   ```

1. 使用以下命令(仍为Neolane ****)启动Postupgrade进程：

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >必须指定在配置过程中用作引用的时区(使用 **时区选项** )。 在本例中，我们使用欧洲／巴黎时区 **时区：“欧洲／巴黎”**。

   >[!NOTE]
   >
   >我们强烈建议将您的用户群升级为“多时区”。 有关时区选项的详细信息，请参阅时 [区部分](../../migration/using/general-configurations.md#time-zones) 。

>[!IMPORTANT]
>
>尚未启动Adobe Campaign服务：仍需在Apache中进行更改。

### 从Adobe Campaign v6.02迁移 {#migrating-from-adobe-campaign-v6_02-1}

部署Adobe Campaign涉及两个阶段：

* 安装Adobe Campaign v7包：必须在每台服务器上执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaign v7包：

   * 在德 **比亚**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * 在 **Red Hat中**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >必须成功安装包，然后才能继续执行下一步。

   >[!NOTE]
   >
   >默认情况下，Adobe Campaign v7与Adobe Campaign v6.02安装在同一目录中： **/usr/local/neolane/nl6/**。

1. 要使客户端控制台安装程序可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参阅 [本节](../../installation/using/installing-campaign-standard-packages.md)。

1. 由于迁移不是通用安装，您需要强制重新启动 **trackinglogd服务** 。 为此，请打开 **nl6/conf/config-default.xml** 文件，并确保 **trackinglogd** service is activated（仅在跟踪／重定向服务器上）:

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果跟 **踪服务器上未启动** trackinglogd服务，则不会转发跟踪信息。

1. 转到 **nl6.back** backup文件夹，并复制（覆盖）每个实例的配置文件和子文件夹。 以Neolane身份登录 **** ，然后运行以下命令：

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. 使用以下命令重新加载Adobe Campaign v7配置：

   ```
   nlserver config -reload
   ```

1. 使用以下命令(仍为Neolane ****)启动Postupgrade进程：

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >“多时区”模式仅在v6.02中对于PostgreSQL数据库引擎可用。 现在，无论使用哪个版本的数据库引擎，它都可用。 我们强烈建议将您的用户群升级为“多时区”。 有关时区选项的详细信息，请参阅时 [区部分](../../migration/using/general-configurations.md#time-zones) 。

### 从Adobe Campaign v6.1迁移 {#migrating-from-adobe-campaign-v6_1-1}

部署Adobe Campaign涉及两个阶段：

* 安装Adobe Campaign v7包：必须在每台服务器上执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaign v7包：

   * 在德 **比亚**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * 在 **Red Hat中**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >必须成功安装包，然后才能继续执行下一步。

   >[!NOTE]
   >
   >默认情况下，Adobe Campaign v7 **安装在/usr/local/neolane/nl6/** directory中。

1. 要使客户端控制台安装程序可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参阅 [本节](../../installation/using/installing-campaign-standard-packages.md)。

1. 转到 **nl6.back** backup文件夹，并复制（覆盖）每个实例的配置文件和子文件夹。 以Neolane身份登录 **** ，然后运行以下命令：

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. 使用以下命令重新加载Adobe Campaign v7配置：

   ```
   nlserver config -reload
   ```

1. 使用以下命令(仍为Neolane ****)启动Postupgrade进程：

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## 迁移重定向服务器(Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>本条仅在从Adobe Campaign v5.11迁移时适用。

在此阶段，需要停止Apache。 请参阅：服 [务停止](#service-stop)。

1. 以root身份登录 ****。
1. 更改Apache环境变量，使其链接到 **nl6目录** 。

   * 在德 **比亚**:

      ```
      vi /etc/apache2/envvars
      ```

   * 在 **Red Hat中**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. 然后运行以下命令：

   * 在德 **比亚**:

      在 **nlsrv.load文件中** ，将nl5 **替换为****nl6**。

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      删除nlsrv.conf文 **件的链接** ，并创建新文件。

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * 在 **Red Hat中**:

      转到/usr/ **local/apache** /conf目录，编辑 **http.conf** 文件，将 **nl5** 替换为 **** nl6中的以下行。

      在 **RHEL 7/Debian 8中**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. 转到 **alias.conf文件** ，将所有 **nl5替换为****nl6**。 要在Debian中执行此操作，请运行以下命令：

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## 安全区 {#security-zones}

如果您是从v6.02或更低版本迁移的，则必须在启动服务之前配置安全区。 有关详细信息，请参阅安 [全性](../../migration/using/general-configurations.md#security)。

## 重新启动服务 {#re-starting-services}

该过程取决于您的Adobe Campaign先前版本。

### 从Adobe Campaign v5.11迁移 {#migrating-from-adobe-campaign-v5_11-2}

在config- **.xml文件中`<instance name>`，重新激活mta** 、fstat服务器、fstat服务器等 **的自动启**&#x200B;动 ********&#x200B;功能。 服务。

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

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

在以下每台服务器上启动Apache和Adobe Campaign服务：

1. 跟踪和重定向服务器。
1. 中间采购服务器。
1. 营销服务器。

在继续执行下一步之前，请对新安装运行完整测试，确保没有回归，并且所有功能都可以遵循“常规配置”部分中的所有建议 [来工作](../../migration/using/general-configurations.md) 。

### 从Adobe Campaign v6.02迁移 {#migrating-from-adobe-campaign-v6_02-2}

在config- **.xml文件中`<instance name>`，重新激活mta** 、fstat服务器、fstat服务器等 **的自动启**&#x200B;动 ********&#x200B;功能。 服务。

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

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

在以下每台服务器上启动Apache和Adobe Campaign服务：

1. 跟踪和重定向服务器。
1. 中间采购服务器。
1. 营销服务器。

完全测试新安装，检查它是否没有倒回，并通过遵循“常规配置”部分中的所有建议确保一切正 [常工作](../../migration/using/general-configurations.md) 。

### 从Adobe Campaign v6.1迁移 {#migrating-from-adobe-campaign-v6_1-2}

在以下每台服务器上启动Apache和Adobe Campaign服务：

1. 跟踪和重定向服务器。
1. 中间采购服务器。
1. 营销服务器。

完全测试新安装，检查它是否没有倒回，并通过遵循“常规配置”部分中的所有建议确保一切正 [常工作](../../migration/using/general-configurations.md) 。

## 删除和清理Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>本条仅在从Adobe Campaign v5.11迁移时适用。

在删除和清除Adobe Campaign v5安装之前，必须应用以下建议：

* 让功能团队对新安装进行全面检查。
* 只有在您确定不需要回滚后，才能卸载Adobe Campaign v5。

删除 **nl5.back目录** 。 以Neolane身份登录 **** ，然后运行以下命令：

```
su - neolane
rm -rf nl5.back
```

重新启动服务器。
