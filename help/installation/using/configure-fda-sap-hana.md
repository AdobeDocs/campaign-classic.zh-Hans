---
title: 配置访问SAP HANA
description: 了解如何在联合数据访问配置访问SAP HANA
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
source-wordcount: '263'
ht-degree: 0%

---


# 配置访问SAP HANA {#configure-access-to-sap-hana}

使用活动 [联合数据访问](../../installation/using/about-fda.md) (联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置访问SAP HANA。

1. 配置 [SAP HANA数据库](#sap-config)
1. 在SAP HANA中 [配置活动](#sap-external) 外部帐户

## SAP HANA司机 {#sap-config}

在联合数据访问下连接到SAP HANA外部数据库需要在Adobe Campaign服务器上进行某些附加配置：

1. 根据您使用的操作系统，为SAP HANA安装ODBC驱动程序：

   * **适用于Linux的hdb_client_linux** .tgz。 解压后，启动hdbinst命令并按照说明完成驱动程序安装。
   * **适用于Windows的hdb_client_windows** .zip。 解压缩文件并开始可执行文件： **hdbinst.exe**。 按照向导说明完成驱动程序的安装。

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

      &quot;InstallDir&quot;与odbcinst.ini文件的 **位置相对应** 。

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. 指定环境服务器的Adobe Campaign变量：

   * **LD_LIBRARY_PATH**:默认情况下，它应包含指向SAP Hana客户端(/usr/sap/hdbclient/libodbcHDB.so)的链接。
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。

## SAP HANA外部帐户{#sap-external}

SAP HANA外部帐户允许您将活动实例连接到SAP HANA外部数据库。

1. 在活动 **[!UICONTROL Explorer]**&#x200B;中， **[!UICONTROL Administration]** 单击“>” **[!UICONTROL Platform]** “>” **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]** 并选 **[!UICONTROL External database]** 择为 **[!UICONTROL Type]**。

1. 要配置 **[!UICONTROL SAP Hana]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**:SAP Hana

   * **[!UICONTROL Server]**:SAP Hana服务器的URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码
