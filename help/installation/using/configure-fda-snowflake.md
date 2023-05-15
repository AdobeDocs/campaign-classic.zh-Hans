---
product: campaign
title: 配置对Snowflake的访问
description: 了解如何在FDA中配置对Snowflake的访问
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 6%

---

# 配置对Snowflake的访问 {#configure-access-to-snowflake}



使用Campaign **联合数据访问** (FDA)选项，用于处理存储在外部数据库中的信息。 请按照以下步骤配置对 [!DNL Snowflake].

1. 配置 [!DNL Snowflake] on [Linux](#snowflake-linux).
1. 配置 [!DNL Snowflake] [外部帐户](#snowflake-external) 在Campaign中

>[!NOTE]
>
>[!DNL Snowflake] 连接器可用于托管部署和内部部署。 有关详细信息，请参见[此页面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## SnowflakeLinux {#snowflake-linux}

配置 [!DNL Snowflake] 在Linux上，请执行以下步骤：

1. 在ODBC安装之前，请检查以下软件包是否安装在Linux分发版上：

   * 对于Red Hat/CentOS:

      ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
      ```

   * 对于Debian:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
      ```

1. 在运行脚本之前，您可以使用 `--help` 选项：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./snowflake_odbc-setup.sh --help
   ```

1. 访问脚本所在的目录，并以根用户身份运行以下脚本：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./snowflake_odbc-setup.sh
   ```

1. 安装ODBC驱动程序后，需要重新启动Campaign Classic。 为此，请运行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 然后，在Campaign中，您可以配置 [!DNL Snowflake] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#snowflake-external).

## Snowflake外部帐户 {#snowflake-external}

您需要创建 [!DNL Snowflake] 外部帐户将Campaign实例连接到 [!DNL Snowflake] 外部数据库。

1. 从Campaign **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]**。

1. 选择 **[!UICONTROL External database]** 作为外部帐户的 **[!UICONTROL Type]**.

1. 在 **[!UICONTROL Configuration]**，选择 [!DNL Snowflake] 从 **[!UICONTROL Type]** 下拉菜单。

   ![](assets/snowflake_5.png)

1. 添加 **[!UICONTROL Server]** URL和 **[!UICONTROL Database]**.

1. 配置 **[!UICONTROL Snowflake]** 外部帐户身份验证：

   * 对于帐户/密码身份验证，您必须指定：

      * **[!UICONTROL Account]**:用户的名称

      * **[!UICONTROL Password]**:用户帐户密码。

      ![](assets/snowflake.png)

   * 对于密钥对身份验证，请单击 **[!UICONTROL Keypair Auth]** 选项卡 **[!UICONTROL Private key]** 验证并复制粘贴 **[!UICONTROL Private key]**.

      ![](assets/snowflake_4.png)


1. 单击 **[!UICONTROL Parameters]** 选项卡 **[!UICONTROL Deploy functions]** 按钮以创建函数。

   >[!NOTE]
   >
   >要使所有函数都可用，您需要在远程数据库中创建Adobe Campaign SQL函数。 有关更多信息，请参阅 [页面](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. 单击 **[!UICONTROL Save]** 配置完成后。

连接器支持以下选项：

| Option | 说明 |
|---|---|
| 工作模式 | 用于工作表的数据库模式 |
| 仓库 | 要使用的默认仓库的名称。 它将覆盖用户的默认设置。 |
| 时区名称 | 默认为空，这表示使用Campaign Classic应用程序服务器的系统时区。 可以使用选项强制使用TIMEZONE会话参数。 <br>[有关更多信息，请参阅此页面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | WEEK_START会话参数。 默认情况下，设置为0。 <br>[有关更多信息，请参阅此页面](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | USE_CACHED_RESULTS会话参数。 默认情况下，设置为TRUE。 此选项可用于禁用Snowflake缓存结果。 <br>[有关更多信息，请参阅此页面](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
| bulkThreads | 用于Snowflake批量加载器的线程数量越多，线程数越多，对于较大的批量加载而言，性能越好。 默认情况下，设置为1。 数字可根据计算机线程计数进行调整。 |
| chunkSize | 确定批量加载器块的文件大小。 默认情况下，设置为128MB。 当与bulkThreads一起使用时，可以修改以获得更佳性能。 同时活动线程越多，性能越好。 <br>有关更多信息，请参阅 [Snowflake文档](https://docs.snowflake.net/manuals/sql-reference/sql/put.html). |
| StageName | 预配置的内部阶段的名称。 它将用于批量加载，而不是创建新的临时阶段。 |
