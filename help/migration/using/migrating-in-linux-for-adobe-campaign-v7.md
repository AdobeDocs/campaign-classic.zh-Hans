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

## 一般过程{#general-procedure}

Linux中的迁移步骤如下：

1. 停止服务：请参阅[服务停止](#service-stop)。
1. 保存数据库：请参阅[备份数据库和现有安装](#back-up-the-database-and-the-existing-installation)。
1. 卸载以前的Adobe Campaign版本包：请参阅[卸载Adobe Campaign先前版本的软件包](#uninstalling-adobe-campaign-previous-version-packages)。
1. 迁移平台：请参阅[部署Adobe Campaign v7](#deploying-adobe-campaign-v7)。
1. 重新开始服务：请参阅[重新启动服务](#re-starting-services)。

## 服务停止{#service-stop}

首先，在所有相关计算机上通过访问数据库停止所有进程。

1. 以&#x200B;**root**&#x200B;身份登录。
1. 需要停止使用重定向模块（**webmdl**&#x200B;服务）的所有服务器。 对于Apache，运行以下命令：

   ```
   /etc/init.d/apache2 stop
   ```

1. 以&#x200B;**root**&#x200B;身份登录。
1. 停止Adobe Campaign所有服务器上的以前版本服务。

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

1. 如果某些进程在几分钟后仍处于活动状态，则可以使用以下命令强制它们关闭：

   ```
   killall -9 nlserver
   ```

## 备份数据库和现有安装{#back-up-the-database-and-the-existing-installation}

该过程取决于您的Adobe Campaign先前版本。

### 从Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}迁移

1. 备份Adobe Campaign数据库。
1. 以&#x200B;**neolane**&#x200B;身份登录，并使用以下命令备份&#x200B;**nl5**&#x200B;目录：

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >为防患未然，建议您将&#x200B;**nl5.back**&#x200B;文件夹压缩并保存到服务器以外的安全位置。

1. 编辑&#x200B;**config-`<instance name>`.xml**（在&#x200B;**nl5.back**&#x200B;文件夹中），以防止&#x200B;**mta**、**wfserver**、**stat**&#x200B;等。 服务自动启动。 例如，将&#x200B;**autoStart**&#x200B;替换为&#x200B;**_autoStart**（仍为&#x200B;**neolane**）。

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
1. 以&#x200B;**neolane**&#x200B;身份登录，并使用以下命令备份&#x200B;**nl6**&#x200B;目录：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >为防患未然，建议您将&#x200B;**nl6.back**&#x200B;文件夹压缩并保存到服务器以外的安全位置。

1. 编辑&#x200B;**config-`<instance name>`.xml**（在&#x200B;**nl6.back**&#x200B;文件夹中）以防止&#x200B;**mta**、**wfserver**、**stat**&#x200B;等。 服务自动启动。 例如，将&#x200B;**autoStart**&#x200B;替换为&#x200B;**_autoStart**(仍为&#x200B;**Adobe Campaign**)。

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

### 从Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}迁移

1. 备份Adobe Campaign数据库。
1. 以&#x200B;**neolane**&#x200B;身份登录，并使用以下命令备份&#x200B;**nl6**&#x200B;目录：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >为防患未然，建议您将&#x200B;**nl6.back**&#x200B;文件夹压缩并保存到服务器以外的安全位置。

## 正在卸载Adobe Campaign早期版本包{#uninstalling-adobe-campaign-previous-version-packages}

该过程取决于您的Adobe Campaign先前版本。

### 卸载Adobe Campaign v5包{#uninstalling-adobe-campaign-v5-packages}

1. 以&#x200B;**root**&#x200B;身份登录。
1. 标识使用以下命令安装的Adobe Campaign包。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -l | grep nl
      ```

      将显示已安装包的列表:

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rpm -qa | grep nl
      ```

1. 卸载Adobe Campaign v5包。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### 卸载Adobe Campaign v6包{#uninstalling-adobe-campaign-v6-packages}

本节说明如何卸载Adobe Campaign v6.02或v6.1包。

1. 以&#x200B;**root**&#x200B;身份登录。
1. 标识使用以下命令安装的Adobe Campaign包。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -l | grep nl
      ```

      将显示已安装包的列表:

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rpm -qa | grep nl
      ```

1. 卸载Adobe Campaign v6包。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## 部署Adobe Campaign v7 {#deploying-adobe-campaign-v7}

该过程取决于您的Adobe Campaign先前版本。

### 从Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}迁移

部署Adobe Campaign涉及两个阶段：

* 安装Adobe Campaign v7包：必须在每台服务器上执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaign v7包：

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >必须成功安装包，然后才能执行下一步。

   >[!NOTE]
   >
   >从v5.11迁移时，默认情况下，Adobe Campaign安装在&#x200B;**/usr/local/neolane/nl6/**&#x200B;目录中。
   >
   >安装包后，将显示以下消息：**&#39;WdbcTimeZone&#39;选项缺失**。 这很正常。

1. 要使客户端控制台安装项目可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参阅[本节](../../installation/using/installing-campaign-standard-packages.md)。

1. 修改与&#x200B;**neolane**&#x200B;用户匹配的&#x200B;**.bashrd**&#x200B;文件。 以&#x200B;**neolane**&#x200B;身份登录并运行以下命令：

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >当您以&#x200B;**neolane**&#x200B;身份登录时，将显示以下消息：**nl5/env.sh:没有此类文件或目录**。 这很正常。

   在文件末尾，将&#x200B;**nl5/env.sh**&#x200B;替换为&#x200B;**nl6/env.sh**。

1. 以&#x200B;**root**&#x200B;身份登录，使用以下命令准备实例：

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
   >通过这些命令可创建Adobe Campaign v6内部文件系统：**conf**&#x200B;目录（带有&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;文件）、**var**&#x200B;目录。

1. 转到&#x200B;**nl5.back**&#x200B;备份文件夹，并复制（覆盖）每个实例的配置文件和子文件夹。 以&#x200B;**neolane**&#x200B;身份登录并运行以下命令：

   >[!IMPORTANT]
   >
   >对于以下第一个命令，请勿复制&#x200B;**config-default.xml**&#x200B;文件。

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. 在Adobe Campaignv7 **serverConf.xml**&#x200B;和&#x200B;**config-default.xml**&#x200B;文件中，应用您对Adobe Campaign v5的特定配置。 对于&#x200B;**serverConf.xml**&#x200B;文件，请使用&#x200B;**nl5/conf/serverConf.xml.diff**&#x200B;文件。

   >[!NOTE]
   >
   >当报告配置从Adobe Campaign v5到Adobe Campaign v7时，请确保指向物理目录的路径通向Adobe Campaign v7，而不是Adobe Campaign v5。

1. 由于迁移不是通用安装，您需要强制重新启动&#x200B;**trackinglogd**&#x200B;服务。 为此，请打开&#x200B;**nl6/conf/config-default.xml**&#x200B;文件，并确保&#x200B;**trackinglogd**&#x200B;服务已激活（仅在跟踪/重定向服务器上）：

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果未在跟踪服务器上启动&#x200B;**trackinglogd**&#x200B;服务，则不会转发任何跟踪信息。

1. 使用以下命令重新加载Adobe Campaign v7配置：

   ```
   nlserver config -reload
   ```

1. 使用以下命令开始postupgrade进程（仍为&#x200B;**neolane**）：

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >您必须指定在配置期间用作引用的时区（使用&#x200B;**-timezone**&#x200B;选项）。 在这种情况下，我们使用欧洲/巴黎时区&#x200B;**-timezone:“欧洲/巴黎”**。

   >[!NOTE]
   >
   >我们强烈建议将您的用户群升级为“多时区”。 有关时区选项的详细信息，请参阅[时区](../../migration/using/general-configurations.md#time-zones)部分。

>[!IMPORTANT]
>
>尚不开始Adobe Campaign服务：仍需在Apache中进行更改。

### 从Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}迁移

部署Adobe Campaign涉及两个阶段：

* 安装Adobe Campaign v7包：必须在每台服务器上执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaign v7包：

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >必须成功安装包，然后才能执行下一步。

   >[!NOTE]
   >
   >Adobe Campaign v7默认安装在与Adobe Campaign v6.02相同的目录中：**/usr/local/neolane/nl6/**。

1. 要使客户端控制台安装项目可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参阅[本节](../../installation/using/installing-campaign-standard-packages.md)。

1. 由于迁移不是通用安装，您需要强制重新启动&#x200B;**trackinglogd**&#x200B;服务。 为此，请打开&#x200B;**nl6/conf/config-default.xml**&#x200B;文件，并确保&#x200B;**trackinglogd**&#x200B;服务已激活（仅在跟踪/重定向服务器上）：

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果未在跟踪服务器上启动&#x200B;**trackinglogd**&#x200B;服务，则不会转发任何跟踪信息。

1. 转到&#x200B;**nl6.back**&#x200B;备份文件夹，并复制（覆盖）每个实例的配置文件和子文件夹。 以&#x200B;**neolane**&#x200B;身份登录并运行以下命令：

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

1. 使用以下命令开始postupgrade进程（仍为&#x200B;**neolane**）：

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >“多时区”模式仅在v6.02中对于PostgreSQL数据库引擎可用。 现在，无论使用哪个版本的数据库引擎，它都可用。 我们强烈建议将您的用户群升级为“多时区”。 有关时区选项的详细信息，请参阅[时区](../../migration/using/general-configurations.md#time-zones)部分。

### 从Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}迁移

部署Adobe Campaign涉及两个阶段：

* 安装Adobe Campaign v7包：必须在每台服务器上执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaign v7包：

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >必须成功安装包，然后才能执行下一步。

   >[!NOTE]
   >
   >Adobe Campaign v7默认安装在&#x200B;**/usr/local/neolane/nl6/**&#x200B;目录中。

1. 要使客户端控制台安装项目可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参阅[本节](../../installation/using/installing-campaign-standard-packages.md)。

1. 转到&#x200B;**nl6.back**&#x200B;备份文件夹，并复制（覆盖）每个实例的配置文件和子文件夹。 以&#x200B;**neolane**&#x200B;身份登录并运行以下命令：

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

1. 使用以下命令开始postupgrade进程（仍为&#x200B;**neolane**）：

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## 迁移重定向服务器(Apache){#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>此部分仅在从Adobe Campaign v5.11迁移时适用。

目前，阿帕奇需要停止。 请参阅：[服务停止](#service-stop)。

1. 以&#x200B;**root**&#x200B;身份登录。
1. 更改Apache环境变量，使其链接到&#x200B;**nl6**&#x200B;目录。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      vi /etc/apache2/envvars
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. 然后运行以下命令：

   * 在&#x200B;**Debian**&#x200B;中：

      在&#x200B;**nlsrv.load**&#x200B;文件中，将&#x200B;**nl5**&#x200B;替换为&#x200B;**nl6**。

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      删除&#x200B;**nlsrv.conf**&#x200B;文件的链接并创建新文件。

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      转到&#x200B;**/usr/local/apache2/conf**&#x200B;目录，编辑&#x200B;**http.conf**&#x200B;文件，并在以下行中将&#x200B;**nl5**&#x200B;替换为&#x200B;**nl6**。

      在&#x200B;**RHEL 7/Debian 8**&#x200B;中：

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. 转到&#x200B;**alias.conf**&#x200B;文件，将所有&#x200B;**nl5**&#x200B;替换为&#x200B;**nl6**。 要在Debian中执行此操作，请运行以下命令：

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## 安全区域{#security-zones}

如果您是从v6.02或更低版本迁移，则必须在启动服务之前配置安全区域。 有关详细信息，请参阅[Security](../../migration/using/general-configurations.md#security)。

## 重新启动服务{#re-starting-services}

该过程取决于您的Adobe Campaign先前版本。

### 从Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}迁移

在&#x200B;**config-`<instance name>`.xml**&#x200B;文件中，重新激活&#x200B;**mta**、**wfserver**、**stat**&#x200B;等的自动启动。 服务。

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

开始Apache和Adobe Campaign服务：

1. 跟踪和重定向服务器。
1. 中间源服务器.
1. 营销服务器。

在执行下一步之前，请对新安装运行完整测试，确保没有回归，并且所有操作均可遵循[常规配置](../../migration/using/general-configurations.md)部分中的所有建议。

### 从Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}迁移

在&#x200B;**config-`<instance name>`.xml**&#x200B;文件中，重新激活&#x200B;**mta**、**wfserver**、**stat**&#x200B;等的自动启动。 服务。

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

开始Apache和Adobe Campaign服务：

1. 跟踪和重定向服务器。
1. 中间源服务器.
1. 营销服务器。

请完全测试新安装，检查它是否没有重新恢复，并通过遵循[常规配置](../../migration/using/general-configurations.md)部分中的所有建议确保一切正常工作。

### 从Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}迁移

开始Apache和Adobe Campaign服务：

1. 跟踪和重定向服务器。
1. 中间源服务器.
1. 营销服务器。

请完全测试新安装，检查它是否没有重新恢复，并通过遵循[常规配置](../../migration/using/general-configurations.md)部分中的所有建议确保一切正常工作。

## 删除和清理Adobe Campaignv5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>此部分仅在从Adobe Campaign v5.11迁移时适用。

在删除和清理Adobe Campaign v5安装之前，必须应用以下建议：

* 让功能团队对新安装进行完整检查。
* 只有在确定不需要回滚时卸载Adobe Campaign v5。

删除&#x200B;**nl5.back**&#x200B;目录。 以&#x200B;**neolane**&#x200B;身份登录并运行以下命令：

```
su - neolane
rm -rf nl5.back
```

重新开始服务器。
