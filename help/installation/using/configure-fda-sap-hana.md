---
product: campaign
title: 配置对SAP HANA的访问
description: 了解如何在FDA中配置对SAP HANA的访问
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# 配置对SAP HANA的访问 {#configure-access-to-sap-hana}



使用Campaign [联合数据访问](../../installation/using/about-fda.md) (FDA)选项，用于处理存储在外部数据库中的信息。 请按照以下步骤配置对SAP HANA的访问。

1. 配置 [SAP HANA数据库](#sap-config)
1. 配置SAP HANA [外部帐户](#sap-external) 在Campaign中

## SAP HANA驱动程序 {#sap-config}

在FDA中连接到SAP HANA外部数据库需要在Adobe Campaign服务器上进行某些其他配置：

1. 根据您使用的操作系统安装ODBC驱动程序进行SAP HANA:

   * **hdb_client_linux.tgz** 的URL。 解压后，启动hdbinst命令并按照说明完成驱动程序的安装。
   * **hdb_client_windows_zip** （对于Windows）。 解压缩文件并启动可执行文件： **hdbinst.exe**. 按照向导说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行：/etc/odbc.ini（用于常规参数）和/etc/odbcinst.ini（用于声明驱动程序）。

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

   * **LD_LIBRARY_PATH**:默认情况下，它应包含指向SAP Hana客户端(/usr/sap/hdbclient/libodbcHDB.so)的链接。
   * **奥德布奇尼**:odbc.ini文件的位置(例如/etc/odbc.ini)。

## SAP HANA外部帐户{#sap-external}

SAP HANA外部帐户允许您将Campaign实例连接到SAP HANA外部数据库。

1. 从Campaign **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 选择 **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. 配置 **[!UICONTROL SAP Hana]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**:SAP Hana

   * **[!UICONTROL Server]**:SAP Hana服务器的URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码
