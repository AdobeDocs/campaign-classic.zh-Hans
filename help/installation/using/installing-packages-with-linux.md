---
title: 使用Linux安装包
seo-title: 使用Linux安装包
description: 使用Linux安装包
seo-description: null
page-status-flag: never-activated
uuid: d83f00b5-500b-406a-a3d6-ea5639f244f0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 04faa9f3-d160-4060-b26e-44333f2faf71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8ad1a83d40f5a841b01aaeb17fe271b44f2480dd

---


# 使用Linux安装包{#installing-packages-with-linux}

对于Linux 32位平台，请安装Adobe Campaign 32位。 对于Linux 64位平台，请安装Adobe Campaign 64位。

对于这些版本，Adobe Campaign都提供一个包： **nlserver**。 此包包含给定版本的二进制文件和配置文件。

安装命令允许您：

* 将文件复制到 **/usr/local/neolane**
* 创建一个Adobe Campaign linux帐户（和关联的组），该帐户以 **/usr/local/neolane** 作为其主目录创建
* 创建自动脚本 **/etc/init.d/nlserver6** ，以在启动时使用

此包是使用GCC 4编译的，这意味着与特定版本的库存在依赖关系，这些库并不总是在安装平台上可用。

>[!NOTE]
>
>运行 **命令之前** ，必须尚未创建Neolane系统用户。 在安 **装过程中** ，会自动创建Neolane用户。
>
>链 **接到Neolane** 用户的主目 **录也会在中自动创建****[!UICONTROL /usr/local/neolane]**。 请确保磁盘上有足够的空 **[!UICONTROL /usr/local]** 间（数GB）。

您可以运行 **ping命`hostname`**令，以确保服务器可以连接到自己。

## 基于RPM包的分发 {#distribution-based-on-rpm--packages}

要将Adobe Campaign安装到RPM（RHEL、CentOS和SUSE）操作系统上，请应用以下步骤：

1. 您必须首先获得Adobe Campaign包。

   该文件命名如下，其中 **XXXX** 是Adobe Campaign内部版本号：

   * **对于v7,NLSERVER6-v7-XXXX-0.x86_64.rpm** 。
   * **适用于v6.1的nlserver6-XXXX-0.x86_64.rpm** 。
   >[!CAUTION]
   >
   >确保在本节的命令范例中为您的Adobe Campaign版本使用正确的文件名。

1. 要安装它，请以 **root身份连接** ，并执行以下命令(其中 **XXXX** 是Adobe Campaign内部版本号):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm文件依赖于CentOS/Red Hat分发上的包。 如果不想使用这些依赖关系中的某些内容（例如，如果要使用Oracle JDK而不是OpenJDK），则可能必须使用rpm的“nodeps”选项：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

执行Netreport所必需的“bc”命令(有关详细信 [息](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) ，请参阅本节)并非在所有Linux分发版中都可用。 要检查该命令是否可用，请运行“which bc”命令。 否则，您必须安装它。

对于CentOS，必须安装bc.x86_64包：以root身 **份连接** ，并运行以下命令：

```
yum install bc.x86_64
```

**在SLES 11 SP2上安装的示例：**

* 禁用 **[!UICONTROL libboost_regex]** :

   ```
   zypper remove libboost_regex1_36_0
   ```

* 安装Oracle Java或OpenJDK(有关详细信息，请参阅 [Java开发工具包- JDK](../../installation/using/application-server.md#java-development-kit---jdk)):

   ```
   ./jdk-6uxx-linux-x64-rpm.bin
   ```

* 安装OpenSSL 1.0(有关详细信息，请参阅 [库](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#libraries)):

   ```
   yast -i libopenssl1_0_0-1.0.0c-18.42.1.x86_64.rpm
   ```

   您需要创建指向OpenSSL库文件的别名：

   ```
   ln -s /lib64/libssl.so.1.0.0 /lib64/libssl.so.10
   ln -s /lib64/libcrypto.so.1.0.0 /lib64/libcrypto.so.10
   ```

* 安装libicu 4.2(有关详细信息，请参阅 [库](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#libraries)):

   ```
   yast -i libicu-4.2-7.3.1.x86_64.rpm
   ```

* 安装Adobe Campaign服务器的包：

   ```
   yast -i nlserver6-v7-xxx-x.x86_64.rpm
   ```

## 基于APT(Debian)的分发 {#distribution-based-on-apt--debian-}

### 在德比亚32位中 {#in-debian-32-bits}

要在Debian 32位操作系统上安装Adobe Campaign 32位，请应用以下步骤：

1. 您必须首先获得两个Adobe Campaign包。

   * **nlserver6-v7-XXXX-linux-2.6-intel.deb** for v7.
   * **用于v6.1的nlserver6-XXXX-linux-2.6-intel.deb** 。
   **XXXX** 是Adobe Campaign内部版本号。

   >[!CAUTION]
   >
   >确保在本节的命令范例中为您的Adobe Campaign版本使用正确的文件名。

1. 要安装它，请以 **root身份连接** ，并执行以下命令(其中 **XXXX** 是Adobe Campaign内部版本号):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-intel.deb
   ```

   如果缺少相关性，请运行以下命令：

   ```
   apt-get install -f
   ```

### 在德比亚64位中 {#in-debian-64-bits}

要在Debian 64位操作系统上安装Adobe Campaign 64位，请应用以下步骤：

1. 您必须首先获得Adobe Campaign包。

   * **适用于v7的NLSERVER6-v7-XXXX-linux-2.6-amd64.deb** 。
   * **适用于v6.1的nlserver6-XXXX-linux-2.6-amd64.deb** 。
   **XXXX** 是Adobe Campaign内部版本号。

   >[!CAUTION]
   >
   >确保在本节的命令范例中为您的Adobe Campaign版本使用正确的文件名。

1. 要安装它，请以 **root身份连接** ，并执行以下命令(其中 **XXXX** 是Adobe Campaign内部版本号):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

**德比安“7·8”特点**

在Debian 7操作系统上安装Adobe Campaign时，请考虑以下事项：

* 必须事先安装OpenSSL。
* 使用以下命令安装libicu48(Debian 7)、libicu52(Debian 8)或libicu57(Debian 9)、libprotobuf9(Debian8)和libc-ares2:

   ```
   aptitude install libicu48 (Debian 7) libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 7/8)
   ```

* 使用以下命令安装JDK7:

   ```
   aptitude install openjdk-7-jdk (Debian 7/8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## 个性化参数 {#personalizing-parameters}

某些参数可以通过 **customer.sh文件个性化** 。

如果您是第一次执行安装，则 **customer.sh** 文件可能尚不在服务器上。 创建它并确保它具有执行权限。 如果不是这样，请输入以下命令：

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 服务器编码 {#server-encoding}

默认情况下，服务器在iso8859-15环境中启动。 但是，可以在UTF-8环境中启动服务器。

>[!CAUTION]
>
>此更改影响与文件系统（通过工作流或JavaScript脚本加载的文件）的交互以及对文件编码的交互。 因此，我们建议使用默认环境。

但是，要创建日 **语实例**，您必须使用UTF-8环境。

要启用UTF-8环境，请使用以下命令：

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### 服务器的默认语言 {#default-language-for-the-server}

安装支持英语和法语。 默认情况下使用英语。

要切换到法语，请输入以下命令：

```
su - neolane
vi nl6/customer.sh
```

并添加以下行：

```
export neolane_LANG=fra
```

要确保正确读取系统消息，控制台必须位于与语言对应的代码页面中(ISO-8859-1或-15（对于法语）。

### 环境变量 {#environment-variables}

必须正确定义以下环境变量。

某些组合需要更改用于执行Adobe Campaign的环境。 可以创建和编`/usr/local/neolane/nl6/customer.sh`辑特定文件()，以添加特定于Adobe Campaign环境的修改。

如有必要，请 **使用vi customer.sh命令编辑****** customer.sh文件，并调整配置或添加缺少的行：

* 对于Oracle客户端：

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   ORACLE_HOME环境变量的内容与Oracle安装目录匹配。

   TNS_ADMIN变量的内容必须与 **tnsnames.ora文件的位置匹配** 。

* 对于LibreOffice:

   要在LibreOffice的现有版本上运行Adobe Campaign，需要其他配置：您需要指定到安装目录的访问路径。 例如：

   * 德比安

      提供了OOO_INSTALL_DIR、OOO_BASIS_INSTALL_DIR、OOO_URE_INSTALL_DIR的默认值。 如果LibreOffice安装的布 **局不同** ，则可以在customer.sh中覆盖这些设置：

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib/ure/share/
      ```

   * CentOs

      请使用以下默认值：

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib64/libreoffice/ure/share/
      ```

* 对于Java开发工具包(JDK):

   默认情况下，Adobe Campaign环境()的配置脚本会`~/nl6/env.sh`搜索JDK安装目录。 由于此行为不是100%可靠，您需要指定需要使用的JDK。 为此，可以使用以下命令强制 **使用JDK_HOME** 环境变量：

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >这是一个例子。 确保使用的JDK版本与目录名称匹配。

   要测试JDK配置，请使用以下命令以Adobe Campaign系统用户身份登录：

   ```
   su - neolane
   ```

您必须重新启动Adobe Campaign服务，才能将更改考虑在内。

这些命令如下所示：

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

### Linux中的Oracle客户端 {#oracle-client-in-linux}

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

   请参阅环 [境变量](../../installation/using/installing-packages-with-linux.md#environment-variables)。

* Adobe Campaign的配置

   要最终确定Adobe Campaign的Oracle客户端安装，您需要为Adobe Campaign使用的 **.so** 文件创建符号链接。

   为此，请使用以下命令：

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

如果您遇到问题，请确保 [Oracle安装文档中列出的包已正确安装](http://www.oracle.com/pls/db112/portal.portal_db?selected=11) 。

## 安装检查 {#installation-checks}

您现在可以使用以下命令执行初始安装测试：

```
su - neolane
nlserver pdump
```

当Adobe Campaign未启动时，响应是：

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

这些命令允许您 **创建config-default.xml****和serverConf.xml配置文件** 。 serverConf.xml中可用的所 **有参数都列在本节** 中 [](../../installation/using/the-server-configuration-file.md)。

按 **Ctrl+C** 可停止该进程，然后输入以下命令：

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

要停止它，请输入：

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

## 内部标识符的口令 {#password-for-the-internal-identifier}

Adobe Campaign服务器定义一个名为internal的技术登录名 **** ，该登录名对所有实例具有所有权限。 安装后，登录名没有密码。 必须定义一个。

请参阅部 [分内部标识符](../../installation/using/campaign-server-configuration.md#internal-identifier)。
