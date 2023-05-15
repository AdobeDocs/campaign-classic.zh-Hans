---
product: campaign
title: 在 Linux 中安装包
description: 在 Linux 中安装包
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 1%

---

# 在 Linux 中安装包{#installing-packages-with-linux}



对于Linux 32位平台，请安装Adobe Campaign 32位。 对于Linux 64位平台，请安装Adobe Campaign 64位。

对于其中每个版本，Adobe Campaign都提供一个包： **nlserver**. 此包包含给定版本的二进制文件和配置文件。

使用安装命令，您可以：

* 将文件复制到 **/usr/local/neolane**
* 创建Adobe Campaign Linux帐户（和关联的组），该帐户是通过 **/usr/local/neolane** 作为主目录
* 创建自动脚本 **/etc/init.d/nlserver6** 用于启动，或创建系统单元（从20.1开始）。

>[!NOTE]
>
>的 **奈奥兰** 在运行命令之前，必须尚未创建系统用户。 的 **奈奥兰** 在安装过程中会自动创建用户。
>
>的 **home** 链接到的目录 **奈奥兰** 用户也会在 **[!UICONTROL /usr/local/neolane]**. 请确保上有足够的空间 **[!UICONTROL /usr/local]** 磁盘（多GB）。

您可以运行 **ping`hostname`** 命令，以确保服务器可以访问自己。

## 基于RPM包的分发 {#distribution-based-on-rpm--packages}

要将Adobe Campaign安装到RPM（RHEL、CentOS和SUSE）操作系统上，请应用以下步骤：

1. 您必须先获取Adobe Campaign包。

   该文件名为，其中 **XXXX** 是Adobe Campaign内部版本号：

   * **nlserver6-v7-XXXX-0.x86_64.rpm** 对于v7。
   * **nlserver6-XXXX-0.x86_64.rpm** 适用于v6.1。

   >[!CAUTION]
   >
   >在此部分的命令示例中，确保为您的Adobe Campaign版本使用正确的文件名。

1. 要安装它，请连接为 **根** 并执行以下命令(其中 **XXXX** 是Adobe Campaign内部版本号):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm文件依赖于CentOS/Red Hat分发包。 如果您不想使用其中的某些依赖项(例如，如果您想要使用OracleJDK而不是OpenJDK)，则可能必须使用rpm的“nodeps”选项：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

执行Netreport所必需的“bc”命令(请参阅 [此部分](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) )，在所有Linux发行版中默认不可用。 要检查命令是否可用，请运行“which bc”命令。 如果没有，则必须安装它。

使用CentOS，必须安装bc.x86_64包：连接为 **根** 并运行以下命令：

```
yum install bc.x86_64
```

## 基于APT(Debian)的分发 {#distribution-based-on-apt--debian-}

### Debian 64位 {#in-debian-64-bits}

要在Debian 64位操作系统上安装Adobe Campaign 64位，请执行以下步骤：

1. 您必须先获取Adobe Campaign包。

   * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** 对于v7。
   * **nlserver6-XXXX-linux-2.6-amd64.deb** 适用于v6.1。

   **XXXX** 是Adobe Campaign内部版本号。

   >[!CAUTION]
   >
   >在此部分的命令示例中，确保为您的Adobe Campaign版本使用正确的文件名。

1. 要安装它，请连接为 **根** 并执行以下命令(其中 **XXXX** 是Adobe Campaign内部版本号):

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

某些参数可以通过 **customer.sh** 文件

如果您是首次执行安装，则 **customer.sh** 文件可能尚不存在于服务器上。 创建并确保具有执行权限。 如果不是这种情况，请输入以下命令：

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 服务器编码 {#server-encoding}

默认情况下，服务器在iso8859-15环境中启动。 但是，可以在UTF-8环境中启动服务器。

>[!CAUTION]
>
>此更改会影响与文件系统（通过工作流或JavaScript脚本加载的文件）的交互以及对文件编码的交互。 因此，我们建议使用默认环境。

然而，由于 **日语实例**，则必须使用UTF-8环境。

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

某些组合需要更改用于执行Adobe Campaign的环境。 特定文件(`/usr/local/neolane/nl6/customer.sh`)以添加特定于Adobe Campaign环境的修改。

如有必要，请编辑 **customer.sh** 使用 **vi customer.sh** 命令和修改配置或添加缺失行：

* 对于Oracle客户端：

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   oracle_HOME环境变量的内容与Oracle安装目录匹配。

   TNS_ADMIN变量的内容必须匹配 **tnsnames.ora** 文件。

* 对于LibreOffice:

   要在LibreOffice的现有版本上运行Adobe Campaign，需要额外配置：您需要指定安装目录的访问路径。 例如：

   * Debian

      提供了OOO_INSTALL_DIR和OOO_BASIS_INSTALL_DIR的默认值。 您可以在 **customer.sh** 如果LibreOffice安装的布局不同：

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      ```

   * CentOs

      使用以下默认值：

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      ```

* 对于Java开发工具包(JDK):

   默认情况下，Adobe Campaign环境的配置脚本(`~/nl6/env.sh`)搜索JDK安装目录。 由于此行为不是100%可靠，因此您需要指定需要使用的JDK。 为此，您可以强制 **JDK_HOME** 环境变量：

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

   请参阅 [环境变量](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Adobe Campaign配置

   要完成Adobe Campaign的Oracle客户端安装，您需要为 **.so** 文件。Adobe Campaign

   为此，请使用以下命令：

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

如果遇到问题，请确保 [Oracle安装文档](https://docs.oracle.com/) 正确安装。

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

这些命令允许您创建 **config-default.xml** 和 **serverConf.xml** 配置文件。 中所有可用的参数 **serverConf.xml** 此 [部分](../../installation/using/the-server-configuration-file.md).

按 **Ctrl+C** 要停止该进程，请输入以下命令：

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

Adobe Campaign服务器定义名为 **内部** 对所有情况均具有所有权限。 安装后，登录名没有密码。 必须定义一个。

在[此章节](../../installation/using/configuring-campaign-server.md#internal-identifier)中了解更多信息。
