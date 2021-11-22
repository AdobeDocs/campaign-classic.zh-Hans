---
product: campaign
title: 配置对Snowflake的访问
description: 了解如何在FDA中配置对Snowflake的访问
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 7%

---

# 配置对Snowflake的访问 {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

使用Campaign **联合数据访问** (FDA)选项，用于处理存储在外部数据库中的信息。 请按照以下步骤配置对 [!DNL Snowflake].

1. 配置 [!DNL Snowflake] on [CentOS](#snowflake-centos), [Windows](#snowflake-windows) 或 [德比安](#snowflake-debian)
1. 配置 [!DNL Snowflake] [外部帐户](#snowflake-external) 在Campaign中


>[!NOTE]
>
>[!DNL Snowflake] 连接器可用于托管部署和内部部署。 有关详细信息，请参见[此页面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## SnowflakeCentOS {#snowflake-centos}

配置 [!DNL Snowflake] 在CentOS上，执行以下步骤：

1. 下载用于 [!DNL Snowflake]. [单击此处](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) 开始下载。
1. 然后，您需要使用以下命令在CentOs上安装ODBC驱动程序：

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. 下载并安装ODBC驱动程序后，需要重新启动Campaign Classic。 为此，请运行以下命令：

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. 然后，在Campaign中，您可以配置 [!DNL Snowflake] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#snowflake-external).

## SnowflakeWindows {#snowflake-windows}

1. 下载 [用于Windows的ODBC驱动程序](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). 请注意，您需要管理员级别的权限才能安装驱动程序。 有关更多信息，请参阅 [本页](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. 配置ODBC驱动程序。 有关更多信息，请参阅 [本页](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. 然后，在Campaign中，您可以配置 [!DNL Snowflake] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#snowflake-external).

## SnowflakeDebian {#snowflake-debian}

1. 下载用于 [!DNL Snowflake]. [单击此处](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 开始下载。

1. 然后，您需要使用以下命令在Debian上安装ODBC驱动程序：

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. 下载并安装ODBC驱动程序后，需要重新启动Campaign Classic。 为此，请运行以下命令：

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

1. 配置 **[!UICONTROL Snowflake]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**:的URL [!DNL Snowflake] 服务器

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

   ![](assets/snowflake.png)

1. 单击 **[!UICONTROL Parameters]** 选项卡 **[!UICONTROL Deploy functions]** 按钮以创建函数。

   ![](assets/snowflake_2.png)

连接器支持以下选项：

| Option | 说明 |
|---|---|
| 工作模式 | 用于工作表的数据库模式 |
| 仓库 | 要使用的默认仓库的名称。 它将覆盖用户的默认设置。 |
| 时区名称 | 默认为空，这表示使用Campaign Classic应用程序服务器的系统时区。 可以使用选项强制使用TIMEZONE会话参数。 <br>[有关更多信息，请参阅此页面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | WEEK_START会话参数。 默认情况下，设置为0。 <br>[有关更多信息，请参阅此页面](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | USE_CACHED_RESULTS会话参数。 默认情况下，设置为TRUE。 此选项可用于禁用Snowflake缓存结果。 <br>[有关更多信息，请参阅此页面](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
