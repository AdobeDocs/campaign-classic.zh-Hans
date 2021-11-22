---
product: campaign
title: 在 Linux 中迁移到 Adobe Campaign v7
description: 在 Linux 中迁移到 Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---

# 在 Linux 中迁移到 Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

![](../../assets/v7-only.svg)

## 一般程序 {#general-procedure}

Linux中的迁移步骤如下：

1. 停止服务：请参阅 [服务停止](#service-stop).
1. 保存数据库：请参阅 [备份数据库和现有安装](#back-up-the-database-and-the-existing-installation).
1. 卸载以前的Adobe Campaign版本包：请参阅 [卸载Adobe Campaign以前的版本包](#uninstalling-adobe-campaign-previous-version-packages).
1. 迁移平台：请参阅 [部署Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. 重新启动服务：请参阅 [重新启动服务](#re-starting-services).

## 服务停止 {#service-stop}

首先，在所有相关计算机上停止所有具有数据库访问权限的进程。

1. 登录方式 **根**.
1. 使用重定向模块的所有服务器(**webmdl** 服务)。 对于Apache，运行以下命令：

   ```
   /etc/init.d/apache2 stop
   ```

1. 再次登录为 **根**.
1. 在所有服务器上停止Adobe Campaign以前的版本服务。

   ```
   /etc/init.d/nlserver6 stop
   ```

   如果从v5.11迁移，请运行以下命令：

   ```
   /etc/init.d/nlserver5 stop
   ```

1. 确保在每台服务器上停止Adobe Campaign服务。

   ```
   ps waux | grep nlserver
   ```

   活动进程的列表及其ID(PID)会显示。

1. 如果一个或多个Adobe Campaign进程在几分钟后仍处于活动状态或被阻止状态，请终止它们。

   ```
   killall nlserver
   ```

1. 如果某些进程在几分钟后仍处于活动状态，您可以使用命令强制它们关闭：

   ```
   killall -9 nlserver
   ```

## 备份数据库和现有安装 {#back-up-the-database-and-the-existing-installation}

此过程取决于您之前的Adobe Campaign版本。

### 从Adobe Campaign v5.11迁移 {#migrating-from-adobe-campaign-v5-11}

1. 备份Adobe Campaign数据库。
1. 登录方式 **奈奥兰** 并备份 **nl5** 目录中使用以下命令：

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >为防范这种情况，我们建议您将 **nl5.back** 文件夹，并将其保存到服务器以外的安全位置。

1. 编辑 **配置 — `<instance name>`.xml** (在 **nl5.back** 文件夹)，以防止 **mta**, **wfserver**, **stat** 等。 服务自动启动。 例如， **autoStart** with **_autoStart** (仍为 **奈奥兰**)。

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
1. 登录方式 **奈奥兰** 并备份 **nl6** 目录中使用以下命令：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >为防范这种情况，我们建议您将 **nl6.back** 文件夹，并将其保存到服务器以外的安全位置。

1. 编辑 **配置 — `<instance name>`.xml** (在 **nl6.back** 文件夹)来阻止 **mta**, **wfserver**, **stat**&#x200B;等。 服务自动启动。 例如， **autoStart** with **_autoStart** (仍为 **Adobe Campaign**)。

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
1. 登录方式 **奈奥兰** 并备份 **nl6** 目录中使用以下命令：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >为防范这种情况，我们建议您将 **nl6.back** 文件夹，并将其保存到服务器以外的安全位置。

## 卸载Adobe Campaign以前的版本包 {#uninstalling-adobe-campaign-previous-version-packages}

此过程取决于您之前的Adobe Campaign版本。

### 卸载Adobe Campaign v5包 {#uninstalling-adobe-campaign-v5-packages}

1. 登录方式 **根**.
1. 使用以下命令标识已安装的Adobe Campaign包。

   * 在 **德比安**:

      ```
      dpkg -l | grep nl
      ```

      将显示已安装包的列表：

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * 在 **红帽**:

      ```
      rpm -qa | grep nl
      ```

1. 卸载Adobe Campaign v5包。

   * 在 **德比安**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * 在 **红帽**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### 卸载Adobe Campaign v6包 {#uninstalling-adobe-campaign-v6-packages}

本节将介绍如何卸载Adobe Campaign v6.02或v6.1包。

1. 登录方式 **根**.
1. 使用以下命令标识已安装的Adobe Campaign包。

   * 在 **德比安**:

      ```
      dpkg -l | grep nl
      ```

      将显示已安装包的列表：

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * 在 **红帽**:

      ```
      rpm -qa | grep nl
      ```

1. 卸载Adobe Campaign v6包。

   * 在 **德比安**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * 在 **红帽**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## 部署Adobe Campaign v7 {#deploying-adobe-campaign-v7}

此过程取决于您之前的Adobe Campaign版本。

### 从Adobe Campaign v5.11迁移 {#migrating-from-adobe-campaign-v5_11-1}

部署Adobe Campaign包含两个阶段：

* 安装Adobe Campaign v7包：必须对每台服务器执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaign v7包：

   * 在 **德比安**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * 在 **红帽**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >必须先成功安装包，然后才能继续执行下一步。

   >[!NOTE]
   >
   >从v5.11迁移时，Adobe Campaign将安装在 **/usr/local/neolane/nl6/** 目录。
   >
   >安装包后，将显示以下消息： **缺少“WdbcTimeZone”选项**. 这很正常。

1. 要使客户端控制台安装程序可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参阅 [此部分](../../installation/using/installing-campaign-standard-packages.md).

1. 修改 **.bashrd** 与 **奈奥兰** 用户。 登录方式 **奈奥兰** 并运行以下命令：

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >当您以 **奈奥兰**，将显示以下消息： **nl5/env.sh :没有此类文件或目录**. 这很正常。

   在文件末尾，替换 **nl5/env.sh** with **nl6/env.sh**.

1. 登录方式 **根** 和使用以下命令准备实例：

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
   >通过这些命令，您可以创建Adobe Campaign v6内部文件系统： **conf** 目录(使用 **config-default.xml** 和 **serverConf.xml** 文件)、 **var** 目录访问Advertising Cloud的帮助。

1. 转到 **nl5.back** 备份文件夹，并复制（覆盖）每个实例的配置文件和子文件夹。 登录方式 **奈奥兰** 并运行以下命令：

   >[!IMPORTANT]
   >
   >对于下面的第一个命令，请勿复制 **config-default.xml** 文件。

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. 在Adobe Campaign v7中 **serverConf.xml** 和 **config-default.xml** 文件，请应用您对Adobe Campaign v5的特定配置。 对于 **serverConf.xml** 文件，使用 **nl5/conf/serverConf.xml.diff** 文件。

   >[!NOTE]
   >
   >在报告从Adobe Campaign v5到Adobe Campaign v7的配置时，请确保物理目录的路径指向Adobe Campaign v7，而不是Adobe Campaign v5。

1. 由于迁移不是一般安装，因此您需要强制重新启动 **trackinglogd** 服务。 为此，请打开 **nl6/conf/config-default.xml** 并确保 **trackinglogd** 服务激活（仅在跟踪/重定向服务器上）：

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果 **trackinglogd** 服务未在跟踪服务器上启动，将不会转发跟踪信息。

1. 使用以下命令重新加载Adobe Campaign v7配置：

   ```
   nlserver config -reload
   ```

1. 使用以下命令启动升级后进程(仍为 **奈奥兰**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >您必须在升级后期间指定要用作引用的时区(使用 **-timezone** 选项)。 在本例中，我们使用的是欧洲/巴黎时区 **-timezone:&quot;欧洲/巴黎&quot;**.

   >[!NOTE]
   >
   >我们强烈建议将您的用户群升级为“多时区”。 有关时区选项的更多信息，请参阅 [时区](../../migration/using/general-configurations.md#time-zones) 中。

>[!IMPORTANT]
>
>尚未启动Adobe Campaign服务：仍需在Apache中进行更改。

### 从Adobe Campaign v6.02迁移 {#migrating-from-adobe-campaign-v6_02-1}

部署Adobe Campaign包含两个阶段：

* 安装Adobe Campaign v7包：必须对每台服务器执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaign v7包：

   * 在 **德比安**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * 在 **红帽**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >必须先成功安装包，然后才能继续执行下一步。

   >[!NOTE]
   >
   >Adobe Campaign v7默认安装在与Adobe Campaign v6.02相同的目录中： **/usr/local/neolane/nl6/**.

1. 要使客户端控制台安装程序可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参阅 [此部分](../../installation/using/installing-campaign-standard-packages.md).

1. 由于迁移不是一般安装，因此您需要强制重新启动 **trackinglogd** 服务。 为此，请打开 **nl6/conf/config-default.xml** 并确保 **trackinglogd** 服务激活（仅在跟踪/重定向服务器上）：

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果 **trackinglogd** 服务未在跟踪服务器上启动，将不会转发跟踪信息。

1. 转到 **nl6.back** 备份文件夹，并复制（覆盖）每个实例的配置文件和子文件夹。 登录方式 **奈奥兰** 并运行以下命令：

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

1. 使用以下命令启动升级后进程(仍为 **奈奥兰**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >“多时区”模式仅在v6.02中适用于PostgreSQL数据库引擎。 现在，无论使用的是哪个版本的数据库引擎，它都可用。 我们强烈建议将您的用户群升级为“多时区”。 有关时区选项的更多信息，请参阅 [时区](../../migration/using/general-configurations.md#time-zones) 中。

### 从Adobe Campaign v6.1迁移 {#migrating-from-adobe-campaign-v6_1-1}

部署Adobe Campaign包含两个阶段：

* 安装Adobe Campaign v7包：必须对每台服务器执行此操作。
* 升级后：必须在每个实例上启动此命令。

要部署Adobe Campaign，请应用以下步骤：

1. 使用以下命令安装最新的Adobe Campaign v7包：

   * 在 **德比安**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * 在 **红帽**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >必须先成功安装包，然后才能继续执行下一步。

   >[!NOTE]
   >
   >Adobe Campaign v7安装在 **/usr/local/neolane/nl6/** 目录。

1. 要使客户端控制台安装程序可用，请将其复制到Adobe Campaign安装目录中：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有关如何在Linux中安装Adobe Campaign的详细信息，请参阅 [此部分](../../installation/using/installing-campaign-standard-packages.md).

1. 转到 **nl6.back** 备份文件夹，并复制（覆盖）每个实例的配置文件和子文件夹。 登录方式 **奈奥兰** 并运行以下命令：

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

1. 使用以下命令启动升级后进程(仍为 **奈奥兰**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## 迁移重定向服务器(Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>本节仅在从Adobe Campaign v5.11迁移时适用。

此时，需要停止Apache。 请参阅： [服务停止](#service-stop).

1. 登录方式 **根**.
1. 更改Apache环境变量以使其链接到 **nl6** 目录访问Advertising Cloud的帮助。

   * 在 **德比安**:

      ```
      vi /etc/apache2/envvars
      ```

   * 在 **红帽**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. 然后，运行以下命令：

   * 在 **德比安**:

      在 **nlsrv.load** 文件，替换 **nl5** with **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      删除 **nlsrv.conf** 文件，然后创建一个新文件。

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * 在 **红帽**:

      转到 **/usr/local/apache2/conf** 目录，编辑 **http.conf** 文件和替换 **nl5** with **nl6** 中。

      在 **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. 转到 **alias.conf** 文件并替换所有 **nl5** with **nl6**. 要在Debian中执行此操作，请运行以下命令：

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## 安全区 {#security-zones}

如果您是从v6.02或更低版本迁移，则必须先配置安全区，然后才能启动服务。 有关更多信息，请参阅 [安全性](../../migration/using/general-configurations.md#security).

## 重新启动服务 {#re-starting-services}

此过程取决于您之前的Adobe Campaign版本。

### 从Adobe Campaign v5.11迁移 {#migrating-from-adobe-campaign-v5_11-2}

在 **配置 — `<instance name>`.xml** 文件，重新激活 **mta**, **wfserver**, **stat**&#x200B;等。 服务。

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
1. 中间源服务器.
1. 营销服务器。

在执行下一步之前，请对新安装进行完整测试，确保没有回归，并且所有操作都可以按照 [一般配置](../../migration/using/general-configurations.md) 中。

### 从Adobe Campaign v6.02迁移 {#migrating-from-adobe-campaign-v6_02-2}

在 **配置 — `<instance name>`.xml** 文件，重新激活 **mta**, **wfserver**, **stat**&#x200B;等。 服务。

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
1. 中间源服务器.
1. 营销服务器。

完全测试新安装，检查它是否未回退，并通过遵循 [一般配置](../../migration/using/general-configurations.md) 中。

### 从Adobe Campaign v6.1迁移 {#migrating-from-adobe-campaign-v6_1-2}

在以下每台服务器上启动Apache和Adobe Campaign服务：

1. 跟踪和重定向服务器。
1. 中间源服务器.
1. 营销服务器。

完全测试新安装，检查它是否未回退，并通过遵循 [一般配置](../../migration/using/general-configurations.md) 中。

## 删除和清理Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>本节仅在从Adobe Campaign v5.11迁移时适用。

在删除和清除Adobe Campaign v5安装之前，必须应用以下建议：

* 让功能团队对新安装进行完整检查。
* 只有在您确定不需要回滚时，才卸载Adobe Campaign v5。

删除 **nl5.back** 目录访问Advertising Cloud的帮助。 登录方式 **奈奥兰** 并运行以下命令：

```
su - neolane
rm -rf nl5.back
```

重新启动服务器。
