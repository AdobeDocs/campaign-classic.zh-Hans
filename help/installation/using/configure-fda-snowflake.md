---
solution: Campaign Classic
product: campaign
title: 配置对Snowflake的访问
description: 了解如何在联合数据访问中配置对Snowflake的访问
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 535339b5a9b39625100d630b0b831df143dbeb01
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 6%

---


# 配置对Snowflake{#configure-access-to-snowflake}的访问

使用活动&#x200B;**联合数据访问**(联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对[!DNL Snowflake]的访问。

1. 在[CentOS](#snowflake-centos)、[Windows](#snowflake-windows)或[Debian](#snowflake-debian)上配置[!DNL Snowflake]
1. 在活动中配置[!DNL Snowflake] [外部帐户](#snowflake-external)


>[!NOTE]
>
>[!DNL Snowflake] connector可用于托管和内部部署。有关详细信息，请参见[此页面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## SnowflakeCentOS {#snowflake-centos}

要在CentOS上配置[!DNL Snowflake]，请执行以下步骤：

1. 下载[!DNL Snowflake]的ODBC驱动程序。 [单击此](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) 处以下载开始。
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

1. 在活动中，您随后可以配置[!DNL Snowflake]外部帐户。 有关如何配置外部帐户的详细信息，请参阅[本节](#snowflake-external)。

## SnowflakeWindows {#snowflake-windows}

1. 下载用于Windows的[ODBC驱动程序](https://docs.snowflake.net/manuals/user-guide/odbc-download.html)。 请注意，您需要管理员级权限才能安装驱动程序。 有关详细信息，请参阅[此页](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. 配置ODBC驱动程序。 有关详细信息，请参阅[此页](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. 在活动中，您随后可以配置[!DNL Snowflake]外部帐户。 有关如何配置外部帐户的详细信息，请参阅[本节](#snowflake-external)。

## SnowflakeDebian {#snowflake-debian}

1. 下载[!DNL Snowflake]的ODBC驱动程序。 [单击此](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 处开始下载。

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

1. 在活动中，您随后可以配置[!DNL Snowflake]外部帐户。 有关如何配置外部帐户的详细信息，请参阅[本节](#snowflake-external)。

## Snowflake外部帐户{#snowflake-external}

您需要创建[!DNL Snowflake]外部帐户才能将活动实例连接到[!DNL Snowflake]外部数据库。

1. 在活动&#x200B;**[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**.

1. 选择&#x200B;**[!UICONTROL External database]**&#x200B;作为外部帐户的&#x200B;**[!UICONTROL Type]**。

1. 配置&#x200B;**[!UICONTROL Snowflake]**&#x200B;外部帐户，必须指定：

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**:服务器的 [!DNL Snowflake] URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

   ![](assets/snowflake.png)

1. 单击&#x200B;**[!UICONTROL Parameters]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Deploy functions]**&#x200B;按钮以创建函数。

   ![](assets/snowflake_2.png)

连接器支持以下选项：

| 选项 | 说明 |
|---|---|
| 工作架构 | 用于工作表的模式库 |
| 仓库 | 要使用的默认仓库的名称。 它将覆盖用户的默认设置。 |
| 时区名称 | 默认为空，这意味着使用Campaign Classic应用服务器的系统时区。 该选项可用于强制TIMEZONE会话参数。 <br>有关详细信息，请参见[此页面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)。 |
| WeekStart | WEEK_开始会话参数。 默认情况下，设置为0。 <br>有关详细信息，请参见[此页面](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start)。 |
| UseCachedResult | USE_CACHED_RESULTS会话参数。 默认设置为TRUE。 此选项可用于禁用Snowflake缓存结果。 <br>有关详细信息，请参见[此页面](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)。 |
