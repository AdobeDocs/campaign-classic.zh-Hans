---
title: 配置对Snowflake的访问
description: 了解如何在联合数据访问中配置对Snowflake的访问
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 6%

---


# 配置对Snowflake的访问 {#configure-access-to-snowflake}

使用活动 **联合数据访问** (联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置访问 [!DNL Snowflake]权。

1. 在CentOS [!DNL Snowflake] 、 [Windows或](#snowflake-centos)Debian [上配](#snowflake-windows)[置](#snowflake-debian)
1. 在外部帐户 [!DNL Snowflake] 中 [配置](#snowflake-external) 活动


>[!NOTE]
>
>[!DNL Snowflake] connector可用于托管和内部部署。 有关详细信息，请参见[此页面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## SnowflakeCentOS {#snowflake-centos}

要在CentOS [!DNL Snowflake] 上进行配置，请执行以下步骤：

1. 下载ODBC驱动程序 [!DNL Snowflake]。 [单击此处](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) ,开始下载。
1. 然后，您需要使用以下命令在CentOs上安装ODBC驱动程序：

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. 下载和安装ODBC驱动程序后，需要重新启动Campaign Classic。 要执行此操作，请运行以下命令：

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. 在活动中，您随后可以配置 [!DNL Snowflake] 外部帐户。 有关如何配置外部帐户的详细信息，请参 [阅此部分](#snowflake-external)。

## SnowflakeWindows {#snowflake-windows}

1. 下载适 [用于Windows的ODBC驱动程序](https://docs.snowflake.net/manuals/user-guide/odbc-download.html)。 请注意，您需要管理员级权限才能安装驱动程序。 For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. 配置ODBC驱动程序。 For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. 在活动中，您随后可以配置 [!DNL Snowflake] 外部帐户。 有关如何配置外部帐户的详细信息，请参 [阅此部分](#snowflake-external)。

## Snowflake德比 {#snowflake-debian}

1. 下载ODBC驱动程序 [!DNL Snowflake]。 [单击此处](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) ,开始下载。

1. 然后，您需要使用以下命令在Debian上安装ODBC驱动程序：

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. 下载和安装ODBC驱动程序后，需要重新启动Campaign Classic。 要执行此操作，请运行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在活动中，您随后可以配置 [!DNL Snowflake] 外部帐户。 有关如何配置外部帐户的详细信息，请参 [阅此部分](#snowflake-external)。

## Snowflake外部帐户 {#snowflake-external}

您需要创建一个外部帐户 [!DNL Snowflake] 来将活动实例连接到外部 [!DNL Snowflake] 数据库。

1. 在活动 **[!UICONTROL Explorer]**&#x200B;中， **[!UICONTROL Administration]** 单击“>” **[!UICONTROL Platform]** “>” **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**.

1. 选 **[!UICONTROL External database]** 择作为外部帐户 **[!UICONTROL Type]**。

1. 配置 **[!UICONTROL Snowflake]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**:服务器的 [!DNL Snowflake] URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

   ![](assets/snowflake.png)

1. 单击选 **[!UICONTROL Parameters]** 项卡，然 **[!UICONTROL Deploy functions]** 后单击按钮以创建函数。

   ![](assets/snowflake_2.png)

连接器支持以下选项：

| 选项 | 说明 |
|---|---|
| 工作架构 | 用于工作表的模式库 |
| 仓库 | 要使用的默认仓库的名称。 它将覆盖用户的默认设置。 |
| 时区名称 | 默认为空，这意味着使用Campaign Classic应用服务器的系统时区。 该选项可用于强制TIMEZONE会话参数。 <br>有关详细信息，请参见[此页面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)。 |
| WeekStart | WEEK_开始会话参数。 默认情况下，设置为0。 <br>有关详细信息，请参见[此页面](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start)。 |
| UseCachedResult | USE_CACHED_RESULTS会话参数。 默认设置为TRUE。 此选项可用于禁用Snowflake缓存结果。 <br>有关详细信息，请参见[此页面](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)。 |
