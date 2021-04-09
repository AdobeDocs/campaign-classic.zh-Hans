---
solution: Campaign Classic
product: campaign
title: 在 Linux 中安装包
description: 在 Linux 中安装包
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 1%

---

# 在 Linux 中安装包{#installing-packages-with-linux}

对于Linux 32位平台，请安装Adobe Campaign 32位。 对于Linux 64位平台，请安装Adobe Campaign 64位。

对于每个版本，Adobe Campaign都附带一个包：**nlserver**。 此包包含给定版本的二进制文件和配置文件。

使用安装命令可以：

* 将文件复制到&#x200B;**/usr/local/neolane**
* 创建一个Adobe Campaign Linux帐户（和关联组），它以&#x200B;**/usr/local/neolane**&#x200B;作为其主目录创建
* 创建供启动时使用的自动脚本&#x200B;**/etc/init.d/nlserver6**，或创建系统单元（从20.1开始）。

>[!NOTE]
>
>**neolane**&#x200B;系统用户必须在运行命令之前尚未创建。 在安装过程中会自动创建&#x200B;**neolane**&#x200B;用户。
>
>还在&#x200B;**[!UICONTROL /usr/local/neolane]**&#x200B;中自动创建链接到&#x200B;**neolane**&#x200B;用户的&#x200B;**home**&#x200B;目录。 请确保&#x200B;**[!UICONTROL /usr/local]**&#x200B;磁盘上有足够的空间（几GB）。

可以运行&#x200B;**ping`hostname`**&#x200B;命令，以确保服务器可以连接到自己。

## 基于RPM包{#distribution-based-on-rpm--packages}的分发

要将Adobe Campaign安装到RPM（RHEL、CentOS和SUSE）操作系统上，请应用以下步骤：

1. 必须首先获得Adobe Campaign包。

   文件名如下，其中&#x200B;**XXXX**&#x200B;是Adobe Campaign生成号：

   * **nlserver6-v7-XXXX-0.x86_64.** rpmfor v7。
   * **nlserver6-XXXX-0.x86_64.** rpmfor v6.1。

   >[!CAUTION]
   >
   >请确保在本节的命令示例中为您的Adobe Campaign版本使用正确的文件名。

1. 要安装它，请以&#x200B;**root**&#x200B;连接并执行以下命令(其中&#x200B;**XXXX**&#x200B;是Adobe Campaign生成号):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm文件依赖于CentOS/Red Hat分发上可找到的包。 如果您不想使用其中的某些依赖关系(例如，如果您想使用Oracle JDK而不是OpenJDK)，则可能必须使用rpm的“nodeps”选项：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

执行netreport所必需的“bc”命令（有关详细信息，请参阅[此部分](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)）并非在所有Linux分发版中都可用。 要检查该命令是否可用，请运行“which bc”命令。 否则，必须安装它。

对于CentOS，必须安装bc.x86_64包：以&#x200B;**root**&#x200B;身份连接并运行以下命令：

```
yum install bc.x86_64
```

## 基于APT(Debian){#distribution-based-on-apt--debian-}的分布

### 在Debian中，64位{#in-debian-64-bits}

要在Debian 64位操作系统上安装Adobe Campaign 64位，请应用以下步骤：

1. 必须首先获得Adobe Campaign包。

   * **nlserver6-v7-XXXX-linux-2.6-amd64.** debfor v7。
   * **nlserver6-XXXX-linux-2.6-amd64.** debfor v6.1。

   **** XXXX是Adobe Campaign生成号。

   >[!CAUTION]
   >
   >请确保在本节的命令示例中为您的Adobe Campaign版本使用正确的文件名。

1. 要安装它，请以&#x200B;**root**&#x200B;连接并执行以下命令(其中&#x200B;**XXXX**&#x200B;是Adobe Campaign生成号):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   如果缺少依赖项，请运行以下命令：

   ```
   apt-get install -f
   ```

**德比安8/9特点**

在Debian 8/9操作系统上安装Adobe Campaign时，请考虑以下事项：

* 必须事先安装OpenSSL。
* 使用以下命令安装libicu52(Debian 8)或libicu57(Debian 9)、libprotobuf9(Debian8)和libc-ares2:

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

## 个性化参数{#personalizing-parameters}

某些参数可以通过&#x200B;**customer.sh**&#x200B;文件进行个性化

如果您是第一次执行安装，则服务器上可能尚不存在&#x200B;**customer.sh**&#x200B;文件。 创建它并确保它具有执行权限。 如果不是这样，请输入以下命令：

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 服务器编码{#server-encoding}

默认情况下，服务器在iso8859-15环境中启动。 但是，服务器可以以UTF-8环境启动。

>[!CAUTION]
>
>此更改影响与文件系统（通过工作流或JavaScript脚本加载的文件）的交互以及文件编码。 因此，我们建议使用默认环境。

但是，要创建&#x200B;**日语实例**，必须使用UTF-8环境。

要启用UTF-8环境，请使用以下命令：

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### 服务器{#default-language-for-the-server}的默认语言

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

要确保正确读取系统消息，控制台必须位于与语言对应的代码页中（法语为ISO-8859-1或–15）。

### 环境变量{#environment-variables}

必须正确定义以下环境变量。

某些组合需要更改用于执行Adobe Campaign的环境。 可以创建和编辑特定文件(`/usr/local/neolane/nl6/customer.sh`)，以添加特定于Adobe Campaign环境的修改。

如有必要，使用&#x200B;**vi customer.sh**&#x200B;命令编辑&#x200B;**customer.sh**&#x200B;文件并调整配置或添加缺少的行：

* 对于Oracle客户端：

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   oracle_HOME环境变量的内容与Oracle安装目录匹配。

   TNS_ADMIN变量的内容必须与&#x200B;**tnsnames.ora**&#x200B;文件的位置匹配。

* 对于LibreOffice:

   要在现有版本的LibreOffice上运行Adobe Campaign，需要其他配置：您需要指定到安装目录的访问路径。 例如：

   * Debian

      提供了OOO_INSTALL_DIR、OO_BASIS_INSTALL_DIR、OOO_URE_INSTALL_DIR的默认值。 如果LibreOffice安装的布局不同，则可以在&#x200B;**customer.sh**&#x200B;中覆盖它们：

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

   默认情况下，Adobe Campaign环境(`~/nl6/env.sh`)的配置脚本会搜索JDK安装目录。 由于此行为不是100%可靠，您需要指定需要使用的JDK。 为此，可以使用以下命令强制&#x200B;**JDK_HOME**&#x200B;环境变量：

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

必须重新启动Adobe Campaign服务，才能将更改考虑在内。

命令如下所示：

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

从20.1开始，我们建议改用以下命令：

```
systemctl stop nlserver
systemctl start nlserver
```

### Oracle Client in Linux {#oracle-client-in-linux}

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

   要完成Oracle客户端的Adobe Campaign安装，您需要为Adobe Campaign使用的&#x200B;**.so**&#x200B;文件创建一个符号链接。

   为此，请使用以下命令：

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

如果遇到问题，请确保[Oracle安装文档](https://www.oracle.com/pls/db112/portal.portal_db?selected=11)中列出的包已正确安装。

## 安装检查{#installation-checks}

您现在可以使用以下命令执行初始安装测试：

```
su - neolane
nlserver pdump
```

当Adobe Campaign未启动时，响应为：

```
no task
```

## 服务器{#first-start-up-of-the-server}的首次开始

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

这些命令允许您创建&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;配置文件。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

按&#x200B;**Ctrl+C**&#x200B;可停止进程，然后输入以下命令：

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

要停止，请输入：

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

## 内部标识符{#password-for-the-internal-identifier}的口令

Adobe Campaign服务器定义名为&#x200B;**internal**&#x200B;的技术登录，该登录对所有实例具有所有权限。 安装后，登录名没有密码。 必须定义一个。

请阅读[本节](../../installation/using/configuring-campaign-server.md#internal-identifier)了解更多信息。
