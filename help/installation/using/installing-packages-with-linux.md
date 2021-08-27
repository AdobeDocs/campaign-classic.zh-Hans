---
product: campaign
title: 在 Linux 中安装包
description: 在 Linux 中安装包
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 1%

---

# 在 Linux 中安装包{#installing-packages-with-linux}

![](../../assets/v7-only.svg)

对于Linux 32位平台，请安装Adobe Campaign 32位。 对于Linux 64位平台，请安装Adobe Campaign 64位。

对于其中每个版本，Adobe Campaign都提供一个包：**nlserver**。 此包包含给定版本的二进制文件和配置文件。

使用安装命令，您可以：

* 将文件复制到&#x200B;**/usr/local/neolane**
* 创建Adobe Campaign Linux帐户（及关联的组），该帐户以&#x200B;**/usr/local/neolane**&#x200B;作为其主目录创建
* 创建自动脚本&#x200B;**/etc/init.d/nlserver6**&#x200B;以在启动时使用，或创建系统单元（从20.1开始）。

>[!NOTE]
>
>在运行命令之前，不得创建&#x200B;**neolane**&#x200B;系统用户。 在安装过程中，会自动创建&#x200B;**neolane**&#x200B;用户。
>
>**home**&#x200B;链接到&#x200B;**neolane**&#x200B;用户的目录也会在&#x200B;**[!UICONTROL /usr/local/neolane]**&#x200B;中自动创建。 请确保&#x200B;**[!UICONTROL /usr/local]**&#x200B;磁盘上有足够的空间（多GB）。

您可以运行&#x200B;**ping`hostname`**&#x200B;命令，以确保服务器可以访问自己。

## 基于RPM包的分发 {#distribution-based-on-rpm--packages}

要将Adobe Campaign安装到RPM（RHEL、CentOS和SUSE）操作系统上，请应用以下步骤：

1. 您必须先获取Adobe Campaign包。

   该文件名如下，其中&#x200B;**XXXX**&#x200B;是Adobe Campaign内部版本号：

   * **nlserver6-v7-XXXX-0.x86_64.** rpmfor v7。
   * **nlserver6-XXXX-0.x86_64.** rpmfor v6.1。

   >[!CAUTION]
   >
   >在此部分的命令示例中，确保为您的Adobe Campaign版本使用正确的文件名。

1. 要安装此程序，请作为&#x200B;**root**&#x200B;连接并执行以下命令(其中&#x200B;**XXXX**&#x200B;是Adobe Campaign内部版本号):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm文件依赖于CentOS/Red Hat分发包。 如果您不想使用其中的某些依赖项(例如，如果您想要使用OracleJDK而不是OpenJDK)，则可能必须使用rpm的“nodeps”选项：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

执行Netreport所必需的“bc”命令（有关详细信息，请参阅[此部分](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)）在所有Linux分发版上默认不可用。 要检查命令是否可用，请运行“which bc”命令。 如果没有，则必须安装它。

使用CentOS，必须安装bc.x86_64包：作为&#x200B;**root**&#x200B;连接并运行以下命令：

```
yum install bc.x86_64
```

## 基于APT(Debian)的分发 {#distribution-based-on-apt--debian-}

### Debian 64位 {#in-debian-64-bits}

要在Debian 64位操作系统上安装Adobe Campaign 64位，请执行以下步骤：

1. 您必须先获取Adobe Campaign包。

   * **nlserver6-v7-XXXX-linux-2.6-amd64.** debfor v7。
   * **nlserver6-XXXX-linux-2.6-amd64.** debfor v6.1。

   **** XXXX是Adobe Campaign内部版本号。

   >[!CAUTION]
   >
   >在此部分的命令示例中，确保为您的Adobe Campaign版本使用正确的文件名。

1. 要安装此程序，请作为&#x200B;**root**&#x200B;连接并执行以下命令(其中&#x200B;**XXXX**&#x200B;是Adobe Campaign内部版本号):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   如果缺少依赖项，请运行以下命令：

   ```
   apt-get install -f
   ```

**Debian 8/9详情**

在Debian 8/9操作系统上安装Adobe Campaign时，请考虑以下事项：

* 必须事先安装OpenSSL。
* 通过以下命令安装libicu52(Debian 8)或libicu57(Debian 9)、libprotobuf9(Debian8)和libc-ares2:

   ```
   aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 8)
   ```

* 使用以下命令安装JDK7:

   ```
   aptitude install openjdk-7-jdk (Debian 8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## 个性化参数 {#personalizing-parameters}

某些参数可以通过&#x200B;**customer.sh**&#x200B;文件进行个性化

如果您是首次执行安装，则服务器上可能尚不存在&#x200B;**customer.sh**&#x200B;文件。 创建并确保具有执行权限。 如果不是这种情况，请输入以下命令：

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 服务器编码 {#server-encoding}

默认情况下，服务器在iso8859-15环境中启动。 但是，可以在UTF-8环境中启动服务器。

>[!CAUTION]
>
>此更改会影响与文件系统（通过工作流或JavaScript脚本加载的文件）的交互以及对文件编码的交互。 因此，我们建议使用默认环境。

但是，要创建&#x200B;**日语实例**，必须使用UTF-8环境。

要启用UTF-8环境，请使用以下命令：

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### 服务器的默认语言 {#default-language-for-the-server}

安装支持英语和法语。 默认使用英语。

要切换到法语，请输入以下命令：

```
su - neolane
vi nl6/customer.sh
```

并添加以下行：

```
export neolane_LANG=fra
```

为确保系统消息能够正确读取，控制台必须位于与语言对应的代码页中（法语为ISO-8859-1或–15）。

### 环境变量 {#environment-variables}

必须正确定义以下环境变量。

某些组合需要更改用于执行Adobe Campaign的环境。 可以创建和编辑特定文件(`/usr/local/neolane/nl6/customer.sh`)，以添加特定于Adobe Campaign环境的修改。

如有必要，请使用&#x200B;**vi customer.sh**&#x200B;命令编辑&#x200B;**customer.sh**&#x200B;文件，并调整配置或添加缺少的行：

* 对于Oracle客户端：

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   oracle_HOME环境变量的内容与Oracle安装目录匹配。

   TNS_ADMIN变量的内容必须匹配&#x200B;**tnsnames.ora**&#x200B;文件的位置。

* 对于LibreOffice:

   要在LibreOffice的现有版本上运行Adobe Campaign，需要额外配置：您需要指定安装目录的访问路径。 例如：

   * Debian

      提供了OOO_INSTALL_DIR、OOO_BASIS_INSTALL_DIR、OOO_URE_INSTALL_DIR的默认值。 如果LibreOffice安装的布局不同，您可以在&#x200B;**customer.sh**&#x200B;中覆盖它们：

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib/ure/share/
      ```

   * CentOs

      使用以下默认值：

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib64/libreoffice/ure/share/
      ```

* 对于Java开发工具包(JDK):

   默认情况下，Adobe Campaign环境的配置脚本(`~/nl6/env.sh`)会搜索JDK安装目录。 由于此行为不是100%可靠，因此您需要指定需要使用的JDK。 要实现此目的，可以使用以下命令强制&#x200B;**JDK_HOME**&#x200B;环境变量：

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >这是一个示例。 确保使用的JDK版本与目录名称匹配。

   要测试JDK配置，请使用以下命令以Adobe Campaign系统用户身份登录：

   ```
   su - neolane
   ```

必须重新启动Adobe Campaign服务，才能将更改考虑在内。

这些命令如下所示：

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

从20.1开始，我们建议改用以下命令：

```
systemctl stop nlserver
systemctl start nlserver
```

### OracleLinux中的客户端 {#oracle-client-in-linux}

将Oracle与Adobe Campaign结合使用时，您需要在Linux中配置Oracle客户端层。

* 使用完整客户端
* TNS定义

   必须在安装阶段添加TNS定义。 为此，请使用以下命令：

   ```
   cd /etc
   mkdir oracle
   cd oracle
   vi tnsnames.ora
   ```

* 环境变量

   请参阅[环境变量](../../installation/using/installing-packages-with-linux.md#environment-variables)。

* Adobe Campaign配置

   要完成Adobe CampaignOracle客户端的安装，您需要为Adobe Campaign使用的&#x200B;**.so**&#x200B;文件创建一个符号链接。

   为此，请使用以下命令：

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

如果遇到问题，请确保[Oracle安装文档](https://www.oracle.com/pls/db112/portal.portal_db?selected=11)中列出的包已正确安装。

## 安装检查 {#installation-checks}

您现在可以使用以下命令执行初始安装测试：

```
su - neolane
nlserver pdump
```

当Adobe Campaign未启动时，响应为：

```
no task
```

## 服务器的首次启动 {#first-start-up-of-the-server}

安装测试完成后，输入以下命令：

```
nlserver web
```

随后将显示以下信息：

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

通过这些命令，可以创建&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;配置文件。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

按&#x200B;**Ctrl+C**&#x200B;以停止进程，然后输入以下命令：

```
nlserver start web
```

随后将显示以下信息：

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

要停止该活动，请输入：

```
nlserver stop web
```

随后将显示以下信息：

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 内部标识符的密码 {#password-for-the-internal-identifier}

Adobe Campaign服务器定义名为&#x200B;**internal**&#x200B;的技术登录，该登录对所有实例具有所有权限。 安装后，登录名没有密码。 必须定义一个。

在[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)中了解详情。
