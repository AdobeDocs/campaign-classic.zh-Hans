---
solution: Campaign Classic
product: campaign
title: 配置对SAP HANA的访问
description: 了解如何在联合数据访问中配置对SAP HANA的访问
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# 配置对SAP HANA {#configure-access-to-sap-hana}的访问

使用活动 [联合数据访问](../../installation/using/about-fda.md)(联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对SAP HANA的访问。

1. 配置[SAP HANA数据库](#sap-config)
1. 在活动中配置SAP HANA [外部帐户](#sap-external)

## SAP HANA驱动程序{#sap-config}

在联合数据访问中连接到SAP HANA外部库需要在Adobe Campaign服务器上进行某些附加配置：

1. 根据您使用的操作系统，为SAP HANA安装ODBC驱动程序：

   * **适用于Linux的hdb_client_linux** .tgz。解压后，启动hdbinst命令并按照说明完成驱动程序的安装。
   * **hdb_client_windows.** zipfor Windows。解压缩文件并开始可执行文件：**hdbinst.exe**。 按照向导说明完成驱动程序的安装。

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

      &quot;InstallDir&quot;对应于&#x200B;**odbcinst.ini**&#x200B;文件的位置。

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. 指定环境服务器的Adobe Campaign变量：

   * **LD_LIBRARY_PATH**:默认情况下，它应包含指向SAP Hana客户端(/usr/sap/hdbclient/libodbcHDB.so)的链接。
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。

## SAP HANA 外部帐户{#sap-external}

SAP HANA外部帐户允许您将活动实例连接到SAP HANA外部数据库。

1. 在活动&#x200B;**[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 单击&#x200B;**[!UICONTROL New]**&#x200B;并选择&#x200B;**[!UICONTROL External database]**&#x200B;作为&#x200B;**[!UICONTROL Type]**。

1. 要配置&#x200B;**[!UICONTROL SAP Hana]**&#x200B;外部帐户，必须指定：

   * **[!UICONTROL Type]**:SAP Hana

   * **[!UICONTROL Server]**:SAP Hana服务器的URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码
