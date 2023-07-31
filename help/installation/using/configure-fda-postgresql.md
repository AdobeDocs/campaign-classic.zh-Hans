---
product: campaign
title: 配置对PostgreSQL的访问权限
description: 了解如何配置对PostgreSQL的访问权限
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 2%

---

# 配置对PostgreSQL的访问权限 {#configure-fda-postgresql}



使用营销活动 **联合数据访问** (FDA)选项，用于处理存储在外部PostgreSQL数据库中的信息。

## PostgreSQL配置 {#postgresql-configuration}

您首先需要安装Libpq。 Libpq允许客户端程序向PostgreSQL后端服务器发送查询并接收这些查询的结果。

按照以下步骤配置对的访问权限 [!DNL PostgreSQL]：

* 对于CentOS，执行以下命令 `sudo apt-get -y install libpq-dev`.

* 对于Linux，执行以下命令 `yum install postgresql-devel`.

* 对于Windows，Libpq通过以下方式实现 `libpq.dll` ，包含在Adobe Campaign安装中。

然后，您可以在Adobe Campaign中配置 [!DNL PostgreSQL] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [本节](#postgresql-external).

## PostgreSQL外部帐户 {#postgresql-external}

>[!NOTE]
>
> PostgreSQL在CentOS 7和6上可用。

您需要创建 [!DNL PostgreSQL] 用于将Campaign实例连接到 [!DNL PostgreSQL] 外部数据库。

1. 来自营销活动 **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]**。

1. 选择 **[!UICONTROL External database]** 作为外部帐户的 **[!UICONTROL Type]**.

1. 下 **[!UICONTROL Configuration]**，选择 [!DNL PostgreSQL, Greenplum] 从 **[!UICONTROL Type]** 下拉菜单。

   ![](assets/postgresql_1.png)

1. 配置 **[!UICONTROL PostgreSQL]** 外部帐户身份验证：

   * **[!UICONTROL Server]**：的URL [!DNL PostgreSQL] 服务器。

   * **[!UICONTROL Account]**：用户的名称。

   * **[!UICONTROL Password]**：用户帐户密码。

   * **[!UICONTROL Database]**：数据库的名称（可选）。

   * **[!UICONTROL Working schema]**：工作模式的名称。 [了解详情](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**：时区设置于 [!DNL PostgreSQL]. [了解详情](https://www.postgresql.org/docs/7.2/timezones.html)

1. 单击 **[!UICONTROL Parameters]** 选项卡，然后 **[!UICONTROL Deploy functions]** 按钮创建函数。

   >[!NOTE]
   >
   >要使所有函数都可用，您需要在远程数据库中创建Adobe Campaign SQL函数。 有关更多信息，请参阅此 [页面](../../configuration/using/adding-additional-sql-functions.md).

1. 单击 **[!UICONTROL Save]** 配置完成后。

连接器支持以下选项：

| Option | 说明 |
|:-:|:-:|
| PGSQL_CONNECT_超时 | 最长等待连接时间（以秒为单位）。 <br>有关详细信息，请参见 [PostgreSQL文档](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | TCP应该向服务器发送keepalive消息之后处于非活动状态的秒数。 <br>有关详细信息，请参见 [PostgreSQL文档](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | 服务器未确认的TCP keepalive消息应重新传输的秒数。  <br>有关详细信息，请参见 [PostgreSQL文档](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | 在客户端与服务器的连接被视为失效之前可以丢失的TCP keepalive数。 <br>有关详细信息，请参见 [PostgreSQL文档](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
