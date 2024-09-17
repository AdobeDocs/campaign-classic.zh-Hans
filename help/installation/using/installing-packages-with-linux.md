---
product: campaign
title: 在Linux中安装包
description: 在Linux中安装包
feature: Installation, Application Settings
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: 1ab08a89b17fca20e9497696417ecba580e26802
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 在Linux中安装包{#installing-packages-with-linux}

Adobe Campaign附带了&#x200B;**nlserver**&#x200B;包，其中包含给定版本的二进制文件和配置文件。



安装命令使您能够：

* 将文件复制到&#x200B;**/usr/local/neolane**
* 创建一个Adobe Campaign Linux帐户（以及关联的组），该帐户是使用&#x200B;**/usr/local/neolane**&#x200B;作为主目录创建的
* 创建启动时使用的自动脚本&#x200B;**/etc/init.d/nlserver6**，或者创建一个系统单元

>[!NOTE]
>
>在运行命令之前，不能创建&#x200B;**neolane**&#x200B;系统用户。 **neolane**&#x200B;用户是在安装期间自动创建的。
>
>链接到&#x200B;**neolane**&#x200B;用户的&#x200B;**home**&#x200B;目录也在&#x200B;**[!UICONTROL /usr/local/neolane]**&#x200B;中自动创建。 请确保&#x200B;**[!UICONTROL /usr/local]**&#x200B;磁盘上有足够的空间。

您可以运行&#x200B;**ping`hostname`**&#x200B;命令以确保服务器可以访问自身。

## 基于RPM软件包的分发 {#distribution-based-on-rpm--packages}

>[!AVAILABILITY]
>
>从v7.4.1开始，Campaign中不再包含用于RPM Linux软件包的库。 您必须安装这些库。
> 

要将Adobe Campaign安装到RPM (RHEL、CentOS)操作系统上，请执行以下步骤：

1. 获取Adobe Campaign包。 文件的名称为&#x200B;**nlserver6-v7-XXXX-0.x86_64.rpm**，其中&#x200B;**XXXX**&#x200B;是Adobe Campaign内部版本号。

   >[!CAUTION]
   >
   >在本节的命令示例中，确保对Adobe Campaign版本使用正确的文件名。

1. 要安装它，请以&#x200B;**root**&#x200B;身份连接并执行以下命令，其中&#x200B;**XXXX**&#x200B;是Adobe Campaign内部版本号：

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm文件依赖于可在CentOS/Red Hat分发中找到的软件包。 如果您不想使用其中的某些依赖项(例如，如果要使用OracleJDK而不是OpenJDK)，则可能需要使用rpm的“nodeps”选项：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

默认情况下，执行[netreport](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)所必需的`bc`命令在所有Linux分发版上均不可用。 要检查该命令是否可用，请运行`which bc`命令。 如果没有，则必须安装它。

对于CentOS，您必须安装bc.x86_64程序包：以&#x200B;**root**&#x200B;身份连接并运行以下命令：

```
yum install bc.x86_64
```

## 基于APT(Debian)的分配 {#distribution-based-on-apt--debian-}

要在Debian 64位操作系统上安装Adobe Campaign，请应用以下步骤：

1. 获取Adobe Campaign包。 文件的名称为&#x200B;**nlserver6-v7-XXXX-linux-2.6-amd64.deb**，其中&#x200B;**XXXX**&#x200B;是Adobe Campaign内部版本号。

   >[!CAUTION]
   >
   >在本节的命令示例中，确保对Adobe Campaign版本使用正确的文件名。

1. 要安装它，请以&#x200B;**root**&#x200B;身份连接并执行以下命令，其中&#x200B;**XXXX**&#x200B;是Adobe Campaign内部版本号：

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   如果缺少依赖项，请运行以下命令：

   ```
   apt-get install -f
   ```


1. 在Debian操作系统上安装Adobe Campaign时，请考虑以下事项：

* 必须预先安装OpenSSL。
* 使用以下命令安装libicu和libc-aresYY，其中XX是版本：

  ```
  apt install libicuXX
  ```

  ```
  apt install libc-aresXX
  ```

  ```
  apt install openjdk-XX-jdk
  ```

## 个性化参数 {#personalizing-parameters}

某些参数可以通过&#x200B;**customer.sh**&#x200B;文件进行个性化

如果您是第一次执行安装，则服务器上可能尚不存在&#x200B;**customer.sh**&#x200B;文件。

创建并确保它拥有执行权限。 如果不是这种情况，请输入以下命令：

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 服务器编码 {#server-encoding}

默认情况下，服务器在iso8859-15环境中启动。 但是，服务器可以在UTF-8环境中启动。

>[!CAUTION]
>
>此更改会影响与文件系统(通过工作流或JavaScript脚本加载的文件)的交互以及文件编码。 因此，我们建议使用默认环境。

若要创建&#x200B;**日语实例**，必须使用UTF-8环境。

要启用UTF-8环境，请使用以下命令：

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### 环境变量 {#environment-variables}

必须正确定义以下环境变量。

某些组合要求更改用于执行Adobe Campaign的环境。 可以创建和编辑特定文件(`/usr/local/neolane/nl6/customer.sh`)，以添加特定于Adobe Campaign环境的修改。

如有必要，请使用&#x200B;**vi customer.sh**&#x200B;命令编辑&#x200B;**customer.sh**&#x200B;文件并调整配置或添加缺少的行：

* 对于Oracle客户端：

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  oracle_HOME环境变量的内容与Oracle安装目录匹配。

  TNS_ADMIN变量的内容必须与&#x200B;**tnsnames.ora**&#x200B;文件的位置匹配。

* 对于LibreOffice：

  要在现有LibreOffice版本上运行Adobe Campaign，需要进行其他配置：您需要指定安装目录的访问路径。 例如：

   * Debian

     提供了OOO_INSTALL_DIR和OOO_BASIS_INSTALL_DIR的默认值。 如果LibreOffice安装的布局不同，则可以在&#x200B;**customer.sh**&#x200B;中覆盖它们：

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

* 对于Java开发工具包(JDK)：

  默认情况下，Adobe Campaign环境(`~/nl6/env.sh`)的配置脚本将搜索JDK安装目录。 但是，建议指定需要使用的JDK。 为此，您可以使用以下命令强制&#x200B;**JDK_HOME**&#x200B;环境变量：

  ```
  export JDK_HOME=/usr/java/jdkX.Y.Z
  ```

  >[!NOTE]
  >
  >确保使用的JDK版本与目录名称匹配。

  要测试JDK配置，请使用以下命令以Adobe Campaign系统用户身份登录：

  ```
  su - neolane
  ```

您必须重新启动Adobe Campaign服务才能将更改考虑在内。

命令如下：

```
systemctl stop nlserver
systemctl start nlserver
```

### Linux中的Oracle客户端 {#oracle-client-in-linux}

在将Oracle与Adobe Campaign结合使用时，需要在Linux中配置Oracle客户端层。

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

  请参阅[环境变量](#environment-variables)。

* Adobe Campaign的配置

  要完成Adobe CampaignOracle客户端的安装，您需要为Adobe Campaign使用的&#x200B;**.so**&#x200B;文件创建一个符号链接。

  为此，请使用以下命令：

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

如果出现问题，请确保已正确安装Oracle安装文档中列出的软件包。

## 安装检查 {#installation-checks}

现在可以使用以下命令执行初始安装测试：

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

```sql
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

这些命令允许您创建&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;配置文件。 **serverConf.xml**&#x200B;中的所有可用参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

按&#x200B;**Ctrl+C**&#x200B;停止该进程，然后输入以下命令：

```
nlserver start web
```

随后将显示以下信息：

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

要停止此操作，请输入：

```
nlserver stop web
```

随后将显示以下信息：

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 内部标识符的密码 {#password-for-the-internal-identifier}

Adobe Campaign服务器定义了一个名为&#x200B;**internal**&#x200B;的技术登录名，该登录名对所有实例具有所有权限。 安装之后，登录没有密码。 必须定义一个。

可在[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)中了解详情。
