---
product: campaign
title: 配置对Google BigQuery的访问权限
description: 了解如何在FDA中配置对Google BigQuery的访问权限
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 2%

---

# 配置对Google BigQuery的访问权限 {#configure-fda-google-big-query}



使用Adobe Campaign Classic **联合数据访问** (FDA)用于处理存储在外部数据库中的信息的选项。 按照以下步骤配置对的访问权限 [!DNL Google BigQuery].

1. 配置 [!DNL Google BigQuery] 日期 [Windows](#google-windows) 或 [Linux](#google-linux)
1. 配置 [!DNL Google BigQuery] [外部帐户](#google-external) 在Adobe Campaign Classic中
1. 设置 [!DNL Google BigQuery] 连接器批量加载 [Windows](#bulk-load-windows) 或 [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] 连接器可用于托管、混合和内部部署。 有关详细信息，请参见[此页面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## Windows上的Google BigQuery {#google-windows}

### 在Windows上设置的驱动程序 {#driver-window}

1. 下载 [适用于Windows的ODBC驱动程序](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. 在Windows中配置ODBC驱动程序。 有关详细信息，请参见[此页面](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf)。

1. 对于 [!DNL Google BigQuery] 连接器正常工作之前，Adobe Campaign Classic需要以下参数才能连接：

   * **[!UICONTROL Project]**：创建或使用现有项目。

      有关更多信息，请参阅此 [页面](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**：创建服务帐户。

      有关更多信息，请参阅此 [页面](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**：和 **[!UICONTROL Service account]** 需要 **[!UICONTROL Key File]** 对于 [!DNL Google BigQuery] 通过ODBC连接。

      有关更多信息，请参阅此 [页面](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**： **[!UICONTROL Dataset]** 对于ODBC连接是可选的。 由于每个查询都需要提供表所在的数据集，请指定 **[!UICONTROL Dataset]** 对于 [!DNL Google BigQuery] Adobe Campaign Classic中的FDA连接器。

      有关更多信息，请参阅此 [页面](https://cloud.google.com/bigquery/docs/datasets).

1. 然后，您可以在Adobe Campaign Classic中配置 [!DNL Google BigQuery] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [本节](#google-external).

### 在Windows上批量设置 {#bulk-load-window}

>[!NOTE]
>
>您需要安装Python才能使Google Cloud SDK正常工作。
>
>我们建议使用Python3，请参阅此 [页面](https://www.python.org/downloads/).

批量加载实用程序允许通过Google Cloud SDK实现更快的传输。

1. 从此下载Windows 64位(x86_64)存档 [页面](https://cloud.google.com/sdk/docs/downloads-versioned-archives) 并将其提取到相应的目录中。

1. 运行 `google-cloud-sdk\install.sh` 脚本。 您需要接受路径变量的设置。

1. 安装后，检查路径变量 `...\google-cloud-sdk\bin` 设置。 如果不能，请手动添加。

1. 在  `..\google-cloud-sdk\bin\bq.cmd` 文件，添加 `CLOUDSDK_PYTHON` 局部变量，该变量将重定向到Python安装的位置。

   例如：

   ![](assets/google-big-query_1.png)

1. 重新启动Adobe Campaign Classic以考虑所做的更改。

## Linux上的Google BigQuery {#google-linux}

### 在Linux上设置的驱动程序 {#driver-linux}

在设置驱动程序之前，请注意，脚本和命令必须由root用户运行。 此外，还建议在运行脚本时使用Google DNS 8.8.8.8。

配置 [!DNL Google BigQuery] 在Linux上，请执行以下步骤：

1. 在ODBC安装之前，请检查您的Linux分发服务器上是否安装了以下软件包：

   * 对于Red Hat/CentOS：

      ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
      ```

   * 对于Debian：

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
      ```

1. 安装前更新系统：

   * 对于Red Hat/CentOS：

      ```
      # install unixODBC driver manager
      yum install -y unixODBC
      ```

   * 对于Debian：

      ```
      # install unixODBC driver manager
      apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
      ```

1. 在运行脚本之前，可以通过指定 — help参数获取更多信息：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. 访问脚本所在的目录，并以root用户身份运行以下脚本：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### 在Linux上批量设置 {#bulk-load-linux}

>[!NOTE]
>
>您需要安装Python才能使Google Cloud SDK正常工作。
>
>我们建议使用Python3，请参阅此 [页面](https://www.python.org/downloads/).

批量加载实用程序允许通过Google Cloud SDK实现更快的传输。

1. 在ODBC安装之前，请检查您的Linux分发服务器上是否安装了以下软件包：

   * 对于Red Hat/CentOS：

      ```
      yum update
      yum upgrade
      yum install -y python3
      ```

   * 对于Debian：

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y python3
      ```

1. 访问脚本所在的目录并运行以下脚本：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

## Google BigQuery外部帐户 {#google-external}

您需要创建 [!DNL Google BigQuery] 用于将Adobe Campaign Classic实例连接到 [!DNL Google BigQuery] 外部数据库。

1. 来自Adobe Campaign Classic **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]**。

1. 选择 **[!UICONTROL External database]** 作为外部帐户的 **[!UICONTROL Type]**.

1. 配置 [!DNL Google BigQuery] 外部帐户，您必须指定：

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**：您的电子邮件 **[!UICONTROL Service account]**. 欲知更多信息，请参见 [Google Cloud文档](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**：您的名称 **[!UICONTROL Project]**. 欲知更多信息，请参见 [Google Cloud文档](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**：
      * **[!UICONTROL Upload key file to the server]**：选择 **[!UICONTROL Click here to upload]** 如果您选择通过Adobe Campaign Classic上传密钥。

      * **[!UICONTROL Enter manually the key file path]**：如果您选择使用预先存在的密钥，请在此字段中复制/粘贴您的绝对路径。
   * **[!UICONTROL Dataset]**：您的名称 **[!UICONTROL Dataset]**. 欲知更多信息，请参见 [Google Cloud文档](https://cloud.google.com/bigquery/docs/datasets-intro).

   ![](assets/google-big-query.png)

连接器支持以下选项：

| Option | 说明 |
|:-:|:-:|
| 代理类型 | 用于通过ODBC和SDK连接器连接到BigQuery的代理类型。 </br>当前支持HTTP（默认）、http_no_tunnel、socks4和socks5。 |
| 代理主机 | 可访问代理的主机名或IP地址。 |
| 代理端口 | 代理正在运行的端口号，例如8080 |
| ProxyUid | 用于经过身份验证的代理的用户名 |
| ProxyPdw | ProxyUid密码 |
| bqpath | 请注意，这仅适用于批量加载工具(Cloud SDK)。 </br> 要避免使用PATH变量或必须将google-cloud-sdk目录移动到其他位置，您可以使用此选项指定服务器上云sdk bin目录的确切路径。 |
