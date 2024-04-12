---
product: campaign
title: 配置对SAP HANA的访问权限
description: 了解如何在FDA中配置对SAP HANA的访问权限
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 配置对SAP HANA的访问权限 {#configure-access-to-sap-hana}



使用营销活动 [联合数据访问](../../installation/using/about-fda.md) (FDA)用于处理存储在外部数据库中的信息的选项。 按照以下步骤配置对SAP HANA的访问权限。

1. 配置 [SAP HANA数据库](#sap-config)
1. 配置SAP HANA [外部帐户](#sap-external) 在Campaign中

## SAP HANA驱动程序 {#sap-config}

连接到FDA中的SAP HANA外部数据库需要Adobe Campaign服务器上的某些其他配置：

1. 根据您使用的操作系统安装用于SAP HANA的ODBC驱动程序：

   * **hdb_client_linux.tgz** 用于Linux。 解压后，启动hdbinst命令并按照说明完成驱动程序的安装。
   * **hdb_client_windows.zip** 用于Windows。 解压缩文件并启动可执行文件： **hdbinst.exe**. 按照向导说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行：/etc/odbc.ini用于常规参数，/etc/odbcinst.ini用于声明驱动程序。

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     
     [HDB]
     Driver=HDBODBC
     servernode=localhost:39013 (this value depend of your server)
     User:SYSTEM
     ```

     “InstallDir”对应于 **odbcinst.ini** 文件。

   * **/etc/odbcinst.ini**

     ```
     [HDBODBC]
     Description = "SmartCloudPT HANA"
     Driver = /usr/sap/hdbclient/libodbcHDB.so
     ```

1. 指定Adobe Campaign服务器的环境变量：

   * **LD_LIBRARY_PATH**：默认情况下，它应包含指向您的SAP Hana客户端的链接(/usr/sap/hdbclient/libodbcHDB.so)。
   * **ODBCINI**：odbc.ini文件的位置(例如/etc/odbc.ini)。

## SAP HANA外部帐户{#sap-external}

SAP HANA外部帐户允许您将Campaign实例连接到SAP HANA外部数据库。

1. 来自营销活动 **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 并选择 **[!UICONTROL External database]** 作为 **[!UICONTROL Type]**.

1. 配置 **[!UICONTROL SAP Hana]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**： SAP Hana

   * **[!UICONTROL Server]**：SAP Hana服务器的URL

   * **[!UICONTROL Account]**：用户名称

   * **[!UICONTROL Password]**：用户帐户密码
