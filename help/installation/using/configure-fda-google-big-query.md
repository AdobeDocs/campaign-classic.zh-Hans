---
product: campaign
title: 配置对Google BigQuery的访问权限
description: 了解如何在FDA中配置对Google BigQuery的访问
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 0cfe8439007b56014eba497c511904c4f11b39ce
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---

# 配置对Google BigQuery的访问权限 {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

使用Adobe Campaign Classic **联合数据访问**(FDA)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对[!DNL Google BigQuery]的访问。

1. 在[Windows](#google-windows)或[Linux](#google-linux)上配置[!DNL Google BigQuery]
1. 在Adobe Campaign Classic中配置[!DNL Google BigQuery] [外部帐户](#google-external)
1. 在[Windows](#bulk-load-windows)或[Linux](#bulk-load-linux)上设置[!DNL Google BigQuery]连接器批量加载

>[!NOTE]
>
> [!DNL Google BigQuery] 连接器可用于混合部署和内部部署。有关详细信息，请参见[此页面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## Windows上的Google BigQuery {#google-windows}

### 在Windows上设置的驱动程序 {#driver-window}

1. 下载适用于Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers)的[ODBC驱动程序。

1. 在Windows中配置ODBC驱动程序。 有关详细信息，请参见[此页面](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf)。

1. 要使[!DNL Google BigQuery]连接器正常工作，Adobe Campaign Classic需要以下参数才能连接：

   * **[!UICONTROL Project]**:创建或使用现有项目。

      有关详细信息，请参见此[页面](https://cloud.google.com/resource-manager/docs/creating-managing-projects)。

   * **[!UICONTROL Service account]**:创建服务帐户。

      有关详细信息，请参见此[页面](https://cloud.google.com/iam/docs/creating-managing-service-accounts)。

   * **[!UICONTROL Key File Path]**:需 **[!UICONTROL Service account]** 要通 **[!UICONTROL Key File]** 过ODBC [!DNL Google BigQuery] 的连接。

      有关详细信息，请参见此[页面](https://cloud.google.com/iam/docs/creating-managing-service-account-keys)。

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** 对于ODBC连接而言，它是可选项。由于每个查询都需要提供表所在的数据集，因此必须为Adobe Campaign Classic中的[!DNL Google BigQuery] FDA连接器指定&#x200B;**[!UICONTROL Dataset]**。

      有关详细信息，请参见此[页面](https://cloud.google.com/bigquery/docs/datasets)。

1. 然后，在Adobe Campaign Classic中，您可以配置[!DNL Google BigQuery]外部帐户。 有关如何配置外部帐户的更多信息，请参阅[此部分](#google-external)。

### 在Windows上设置批量加载 {#bulk-load-window}

>[!NOTE]
>
>您需要安装Python才能使Google Cloud SDK正常工作。
>
>我们建议使用Python3，请参阅此[页面](https://www.python.org/downloads/)。

批量加载实用程序允许更快地传输，这可通过Google Cloud SDK实现。

1. 从此[页面](https://cloud.google.com/sdk/docs/downloads-versioned-archives)下载Windows 64位(x86_64)存档，并将其解压缩到相应的目录中。

1. 运行`google-cloud-sdk\install.sh`脚本。 您需要接受路径变量的设置。

1. 安装后，检查路径变量`...\google-cloud-sdk\bin`是否已设置。 如果没有，请手动添加。

1. 在`..\google-cloud-sdk\bin\bq.cmd`文件中，添加`CLOUDSDK_PYTHON`本地变量，该变量将重定向到Python安装的位置。

   例如：

   ![](assets/google-big-query_1.png)

1. 重新启动Adobe Campaign Classic以考虑所做的更改。

## Linux上的Google BigQuery {#google-linux}

### 在Linux上设置的驱动程序 {#driver-linux}

1. 在安装ODBC驱动程序之前，您需要更新系统。 在Linux或CentOS上，运行以下命令：

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. 然后，您需要使用以下命令安装unixODBC驱动程序管理器：

   ```
   # switch to root user
   sudo su
   ```

   在Debian上：

   ```
   apt-get update
   apt-get upgrade
   # install unixODBC driver manager
   apt-get install unixODBC
   ```

1. 下载[Magnitude Simba Linux ODBC驱动程序(.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers)。 然后，将目标文件传输到计算机上的临时文件夹中，或使用wget命令：

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. 按如下方式提取主目标文件，其中&#x200B;**TarballName**&#x200B;是包含驱动程序的目标包的名称：

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. 访问您提取的文件夹，并提取与驱动程序版本对应的内部目标文件。 将其安装到另一个临时文件夹中，如以下示例BigQueryDriver中：

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. 访问提取主目标文件的临时位置，并将`GoogleBigQueryODBC.did`和`setup/simba.googlebigqueryodbc.ini`文件复制到在上一步骤中创建的新文件夹中：

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. 创建安装目录，如下所示：

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. 将目录的内容复制到新的安装目录中：

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. 在安装目录的`simba.googlebigqueryodbc.ini`中将`<INSTALLDIR>`替换为`/opt/simba/googlebigqueryodbc`:

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. 在`simba.googlebigqueryodbc.ini`中将`DriverManagerEncoding`更改为UTF-16和`SwapFilePath`。 如果需要，您还可以更改日志记录设置。

   以下是更新的驱动程序范围配置文件的示例：

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. 如果您使用系统驱动程序文件或任何当前的`odbcinst.ini`文件，请配置`/etc/odbcinst.ini`以指向Google BigQuery驱动程序位置`/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`。

   例如：

   ```
   # /etc/odbcinst.ini
   # Make sure to use Simba ODBC Driver for Google BigQuery as a driver name.
   
   [ODBC Drivers]
   Simba ODBC Driver for Google BigQuery=Installed
   
   [Simba ODBC Driver for Google BigQuery]
   Description=Simba ODBC Driver for Google BigQuery(64-bit)
   Driver=/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   ```

1. 找到unixODBC驱动程序管理器库的位置，并将`unixODBC`和`googlebigqueryodbc`库路径添加到`LD_LIBRARY_PATH environment`变量中。

   ```
   find / -name 'lib*odbc*.so*' -print
   #output:
   /usr/lib/x86_64-linux-gnu/libodbccr.so.2
   /usr/lib/x86_64-linux-gnu/libodbcinst.so.2.0.0
   /usr/lib/x86_64-linux-gnu/libodbccr.so.1
   .
   .
   /opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   
   #the command would look like this
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/simba/googlebigqueryodbc:/usr/lib
   ```

1. 然后，在Adobe Campaign Classic中，您可以配置[!DNL Google BigQuery]外部帐户。 有关如何配置外部帐户的更多信息，请参阅[此部分](#google-external)。

### 在Linux上设置批量加载 {#bulk-load-linux}

>[!NOTE]
>
>您需要安装Python才能使Google Cloud SDK正常工作。
>
>我们建议使用Python3，请参阅此[页面](https://www.python.org/downloads/)。

批量加载实用程序允许更快地传输，这可通过Google Cloud SDK实现。

1. 在此[页面](https://cloud.google.com/sdk/docs/downloads-versioned-archives)中下载Linux 64位(x86_64)存档，并在相应目录中提取。

1. 运行`google-cloud-sdk\install.sh`脚本。 您需要接受路径变量的设置。

1. 安装后，检查路径变量`...\google-cloud-sdk\bin`是否已设置。 如果没有，请手动添加。

1. 如果要避免使用`PATH`变量，或者要将`google-cloud-sdk`目录移动到其他位置，请在配置&#x200B;**[!UICONTROL External account]**&#x200B;时使用`bqpath`选项值指定系统上bin目录的确切路径。

1. 重新启动Adobe Campaign Classic以考虑所做的更改。

## Google BigQuery外部帐户 {#google-external}

您需要创建一个[!DNL Google BigQuery]外部帐户，以将Adobe Campaign Classic实例连接到[!DNL Google BigQuery]外部数据库。

1. 从Adobe Campaign Classic **[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**。

1. 选择&#x200B;**[!UICONTROL External database]**&#x200B;作为外部帐户的&#x200B;**[!UICONTROL Type]**。

1. 配置[!DNL Google BigQuery]外部帐户时，必须指定：

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**:您的电子邮件 **[!UICONTROL Service account]**。有关此内容的更多信息，请参阅[Google Cloud文档](https://cloud.google.com/iam/docs/creating-managing-service-accounts)。

   * **[!UICONTROL Project]**:您的名 **[!UICONTROL Project]**&#x200B;称。有关此内容的更多信息，请参阅[Google Cloud文档](https://cloud.google.com/resource-manager/docs/creating-managing-projects)。

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**:选 **[!UICONTROL Click here to upload]** 择通过Adobe Campaign Classic上传密钥。

      * **[!UICONTROL Enter manually the key file path]**:如果选择使用预先存在的键，请在此字段中复制/粘贴绝对路径。
   * **[!UICONTROL Dataset]**:您的名 **[!UICONTROL Dataset]**&#x200B;称。有关此内容的更多信息，请参阅[Google Cloud文档](https://cloud.google.com/bigquery/docs/datasets-intro)。
   ![](assets/google-big-query.png)
