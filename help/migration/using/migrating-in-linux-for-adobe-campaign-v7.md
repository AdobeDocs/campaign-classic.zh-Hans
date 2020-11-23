---
solution: Campaign Classic
product: campaign
title: 在 Linux 中迁移到 Adobe Campaign v7
description: 在 Linux 中迁移到 Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---


# 在 Linux 中迁移到 Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## 一般程序 {#general-procedure}

Linux中的迁移步骤如下：

1. 停止服务：请参 [阅服务停止](#service-stop)。
1. 保存数据库：请参 [阅备份数据库和现有安装](#back-up-the-database-and-the-existing-installation)。
1. 卸载以前的Adobe Campaign版本包：请参 [阅卸载Adobe Campaign先前版本的软件包](#uninstalling-adobe-campaign-previous-version-packages)。
1. 迁移平台：请参阅 [部署Adobe Campaignv7](#deploying-adobe-campaign-v7)。
1. 重新开始服务：请参阅 [重新启动服务](#re-starting-services)。

## 服务停止 {#service-stop}

首先，通过访问相关所有计算机上的数据库来停止所有进程。

1. 以根用户 **身份登录**。
1. 需要停止使用重定向模块(**webmdl** 服务)的所有服务器。 对于Apache，运行以下命令：

   ```
   /etc/init.d/apache2 stop
   ```

1. 以root用户身份再次 **登录**。
1. 停止Adobe Campaign所有服务器上的先前版本服务。

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

   活动进程的列表与其ID(PID)一起显示。

1. 如果一个或多个Adobe Campaign进程在几分钟后仍处于活动状态或被阻止状态，请终止它们。

   ```
   killall nlserver
   ```

1. 如果某些进程在几分钟后仍处于活动状态，则可以使用命令强制它们关闭：

   ```
   killall -9 nlserver
   ```

## 备份数据库和现有安装 {#back-up-the-database-and-the-existing-installation}

该过程取决于您的Adobe Campaign先前版本。

### 从Adobe Campaignv5.11迁移 {#migrating-from-adobe-campaign-v5-11}

1. 备份Adobe Campaign库。
1. 以Neolane身 **份登录** ，然后使用以下命 **令备份nl** 5目录：

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您将nl5. **back文件夹压缩** ，并将其保存到服务器以外的安全位置。

1. 编辑 **config-`<instance name>`.xml** (在5.back nl **文件夹中)，以防止mta** 、wfserver **、、********** 、等。 服务自动启动。 例如，将autoStart **替换为****_autoStart** (仍为 **neolane**)。

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
1. 以Neolane身 **份登录** ，然后使用以下命 **令备份nl** 6目录：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您将nl6. **back文件夹压缩** ，并将其保存到服务器以外的安全位置。

1. 编辑 **config-`<instance name>`.xml** (在 **6.back** 文件夹中)，以防止mta、 **wfserver**、、 ********、等。 服务自动启动。 例如，将autoStart **替换为****_autoStart** (仍为 **Adobe Campaign**)。

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

### 从Adobe Campaignv6.1迁移 {#migrating-from-adobe-campaign-v6-1}

1. 备份Adobe Campaign库。
1. 以Neolane身 **份登录** ，然后使用以下命 **令备份nl** 6目录：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >为防患未然，我们建议您将nl6. **back文件夹压缩** ，并将其保存到服务器以外的安全位置。

## 卸载Adobe Campaign先前版本的包 {#uninstalling-adobe-campaign-previous-version-packages}

该过程取决于您的Adobe Campaign先前版本。

### 卸载Adobe Campaignv5包 {#uninstalling-adobe-campaign-v5-packages}

1. 以根用户 **身份登录**。
1. 标识使用以下命令安装的Adobe Campaign包。

   * 在 **德比**:

      ```
      dpkg -l | grep nl
      ```

      将显示已安装包的列表:

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * 在 **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. 卸载Adobe Campaignv5包。

   * 在 **德比**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * 在 **Red Hat**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### 卸载Adobe Campaignv6包 {#uninstalling-adobe-campaign-v6-packages}

本节介绍如何卸载Adobe Campaignv6.02或v6.1包。

1. 以根用户 **身份登录**。
1. 标识使用以下命令安装的Adobe Campaign包。

   * 在 **德比**:

      ```
      dpkg -l | grep nl
      ```

      将显示已安装包的列表:

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * 在 **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. 卸载Adobe Campaignv6包。

   * 在 **德比**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * 在 **Red Hat**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## 部署Adobe Campaignv7 {#deploying-adobe-campaign-v7}

该过程取决于您的Adobe Campaign先前版本。

### 从Adobe Campaignv5.11迁移 {#migrating-from-adobe-campaign-v5_11-1}

部署Adobe Campaign涉及两个阶段：

* 安装Adobe Campaignv7包：必须在每台服务器上执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaignv7包：

   * 在 **德比**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * 在 **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >必须成功安装包，然后才能执行下一步。

   >[!NOTE]
   >
   >从v5.11迁移时，默认情况下，Adobe Campaign **安装在/usr/local/neolane/nl6/** directory中。
   >
   >安装包后，将显示以下消息： **缺少“WdbcTimeZone”选项**。 这很正常。

1. 要使客户端控制台安装项目可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参 [阅本节](../../installation/using/installing-campaign-standard-packages.md)。

1. 修改与 **Neolane** 用户匹配的 **.bashrd文件** 。 以Neolane身份登录 **并** 运行以下命令：

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >当您以Neolane身份登录 **时**，将显示以下消息： **nl5/env.sh:没有此类文件或目录**。 这很正常。

   在文件末尾，将nl5/env.sh **替换为****nl6/env.sh**。

1. 以root用户 **身份登录** ，然后使用以下命令准备实例：

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
   >通过这些命令，可以创建Adobe Campaignv6内部文件系统： **conf** 目录( **带有config-default** .xml和 **serverConf.xml文件),****var** 目录。

1. 转到nl5. **back** backup文件夹，复制（覆盖）每个实例的配置文件和子文件夹。 以Neolane身份登录 **并** 运行以下命令：

   >[!IMPORTANT]
   >
   >对于以下第一个命令，请不 **要复制config-default.xml** 文件。

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. 在Adobe Campaignv7 **serverConf.xml****** 和config-default.xml文件中，应用您对Adobe Campaignv5的特定配置。 对于 **serverConf.xml** 文件，请使 **用nl5/conf/serverConf.xml.diff** 文件。

   >[!NOTE]
   >
   >当报告配置从Adobe Campaignv5到Adobe Campaignv7时，请确保物理目录的路径通向Adobe Campaignv7，而不是Adobe Campaignv5。

1. 由于迁移不是通用安装，您需要强制重新启动跟踪 **日志** 。 为此，请打开 **nl6/conf/config-default.xml** 文件并确保已 **激活跟踪日志** （仅在跟踪／重定向服务器上）:

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果跟 **踪服** 务器上未启动跟踪日志服务，则不会转发跟踪信息。

1. 使用以下命令重新加载Adobe Campaignv7配置：

   ```
   nlserver config -reload
   ```

1. 使用以下命令开始postupgrade进程(仍为 **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >必须指定在播放期间用作引用的时区(使用- **时区选项** )。 在本例中，我们使用欧洲／巴黎时 **区时区：“欧洲／巴黎”**。

   >[!NOTE]
   >
   >我们强烈建议将您的用户群升级为“多时区”。 有关时区选项的详细信息，请参 [阅时区](../../migration/using/general-configurations.md#time-zones) 部分。

>[!IMPORTANT]
>
>尚未开始Adobe Campaign服务：仍需在Apache中进行更改。

### 从Adobe Campaignv6.02迁移 {#migrating-from-adobe-campaign-v6_02-1}

部署Adobe Campaign涉及两个阶段：

* 安装Adobe Campaignv7包：必须在每台服务器上执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaignv7包：

   * 在 **德比**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * 在 **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >必须成功安装包，然后才能执行下一步。

   >[!NOTE]
   >
   >Adobe Campaignv7默认安装在与Adobe Campaignv6.02相同的目录中： **/usr/local/neolane/nl6/**。

1. 要使客户端控制台安装项目可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参 [阅本节](../../installation/using/installing-campaign-standard-packages.md)。

1. 由于迁移不是通用安装，您需要强制重新启动跟踪 **日志** 。 为此，请打开 **nl6/conf/config-default.xml** 文件并确保已 **激活跟踪日志** （仅在跟踪／重定向服务器上）:

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果跟 **踪服** 务器上未启动跟踪日志服务，则不会转发跟踪信息。

1. 转到nl6. **back备份文件夹** ，并复制（覆盖）每个实例的配置文件和子文件夹。 以Neolane身份登录 **并** 运行以下命令：

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. 使用以下命令重新加载Adobe Campaignv7配置：

   ```
   nlserver config -reload
   ```

1. 使用以下命令开始postupgrade进程(仍为 **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >“多时区”模式仅在v6.02中对于PostgreSQL数据库引擎可用。 现在，无论使用哪个版本的数据库引擎，都可以使用它。 我们强烈建议将您的用户群升级为“多时区”。 有关时区选项的详细信息，请参 [阅时区](../../migration/using/general-configurations.md#time-zones) 部分。

### 从Adobe Campaignv6.1迁移 {#migrating-from-adobe-campaign-v6_1-1}

部署Adobe Campaign涉及两个阶段：

* 安装Adobe Campaignv7包：必须在每台服务器上执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaignv7包：

   * 在 **德比**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * 在 **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >必须成功安装包，然后才能执行下一步。

   >[!NOTE]
   >
   >Adobe Campaignv7默认 **安装在/usr/local/neolane/nl6/** directory中。

1. 要使客户端控制台安装项目可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参 [阅本节](../../installation/using/installing-campaign-standard-packages.md)。

1. 转到nl6. **back备份文件夹** ，并复制（覆盖）每个实例的配置文件和子文件夹。 以Neolane身份登录 **并** 运行以下命令：

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. 使用以下命令重新加载Adobe Campaignv7配置：

   ```
   nlserver config -reload
   ```

1. 使用以下命令开始postupgrade进程(仍为 **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## 迁移重定向服务器(Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>本条仅在从Adobe Campaignv5.11迁移时适用。

目前，阿帕奇需要停止。 请参阅： [服务停止](#service-stop)。

1. 以根用户 **身份登录**。
1. 更改Apache环境变量，使其链接到 **nl6** 目录。

   * 在 **德比**:

      ```
      vi /etc/apache2/envvars
      ```

   * 在 **Red Hat**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. 然后运行以下命令：

   * 在 **德比**:

      在nlsrv. **load文件中** ，将nl5 **替换为** nl **6**。

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      删除nlsrv.conf文 **件的链接** ，并创建新文件。

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * 在 **Red Hat**:

      转至/usr/ **local/apache/conf** directory，编辑 **http.conf文件，将** nl5 **替换为** 以 **** 下行中的nl6。

      在 **RHEL 7/Debian 8中**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. 转到alias. **conf文件** ，将所有nl5 **替换为** nl **6**。 要在Debian中执行此操作，请运行以下命令：

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## 安全区 {#security-zones}

如果您是从v6.02或更低版本迁移的，则必须先配置安全区域，然后才能启动服务。 有关详细信息，请参阅 [安全性](../../migration/using/general-configurations.md#security)。

## 重新启动服务 {#re-starting-services}

该过程取决于您的Adobe Campaign先前版本。

### 从Adobe Campaignv5.11迁移 {#migrating-from-adobe-campaign-v5_11-2}

在config- **`<instance name>`.xml文件中，重新激活** mta、wfserver **、****、**&#x200B;等的自动 ****&#x200B;启动。 服务。

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

开始Apache和Adobe Campaign服务，位于以下各台服务器上：

1. 跟踪和重定向服务器。
1. 中间源服务器.
1. 营销服务器。

在执行下一步之前，请对新安装运行完整测试，确保没有回归，并且所有功能都可以遵循“常规配置”部分中的所有建议 [来工作](../../migration/using/general-configurations.md) 。

### 从Adobe Campaignv6.02迁移 {#migrating-from-adobe-campaign-v6_02-2}

在config- **`<instance name>`.xml文件中，重新激活** mta、wfserver **、****、**&#x200B;等的自动 ****&#x200B;启动。 服务。

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

开始Apache和Adobe Campaign服务，位于以下各台服务器上：

1. 跟踪和重定向服务器。
1. 中间源服务器.
1. 营销服务器。

完全测试新安装，检查它没有倒回，并通过遵循“常规配置”部分中的所有建议确保一切正 [常工作](../../migration/using/general-configurations.md) 。

### 从Adobe Campaignv6.1迁移 {#migrating-from-adobe-campaign-v6_1-2}

开始Apache和Adobe Campaign服务，位于以下各台服务器上：

1. 跟踪和重定向服务器。
1. 中间源服务器.
1. 营销服务器。

完全测试新安装，检查它没有倒回，并通过遵循“常规配置”部分中的所有建议确保一切正 [常工作](../../migration/using/general-configurations.md) 。

## 删除和清理Adobe Campaignv5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>本条仅在从Adobe Campaignv5.11迁移时适用。

在删除和清除Adobe Campaignv5安装之前，必须应用以下建议：

* 让功能团队对新安装进行完整检查。
* 只有确定不需要回滚时，才能卸载Adobe Campaignv5。

删除 **nl5.back目录** 。 以Neolane身份登录 **并** 运行以下命令：

```
su - neolane
rm -rf nl5.back
```

重新开始服务器。
