---
title: 配置对Netezza的访问
description: 了解如何在联合数据访问中配置对Netezza的访问
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
source-wordcount: '374'
ht-degree: 0%

---


# 配置对Netezza的访问 {#configure-access-to-netezza}

使用活动 [联合数据访问](../../installation/using/about-fda.md) (联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对Netezza的访问。

1. 安装和配置Netezza [驱动程序](#netezza-config)
1. 在活动中配 [置Netezza](#netezza-external) 外部帐户

## Netezza配置 {#netezza-config}

在联合数据访问下连接到Netezza外部数据库需要在Adobe Campaign服务器上进行以下其他配置：

1. 根据您使用的操作系统，安装Netezza的ODBC驱动程序：

   * **nz-linuxclient-v7.2.0.0.tar.gz** for Linux。 选择与您的操作系统（linux或linux64）对应的文件夹，并开始unpack命令。 您可以保留默认建议在存储库中执行的安装：&quot;/usr/local/nz&quot;。
   * **nz-winclient-v7.2.0.0.zip** for Windows 解压缩文件并开始与操作系统对应的可执行脚本：nzodbcsetup.exe或nzodbcsetup64.exe。 按照向导说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行： **/etc/odbc.ini** ，用于常规参数， **/etc/odbcinst.ini** ，用于声明驱动程序。

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;对应于odbcinst.ini文件的位置。

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. 指定环境服务器的Adobe Campaign变量：

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib和/usr/local/nz/lib64。 “/usr/local/nz”与安装驱动程序时默认提供的安装存储库相对应。 您需要在此指定已为安装选择的存储库。
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**:odbc.ini文件的位置。 Netezza还要求使用odbc.ini文件的第二个变量。

## 内泰扎外部帐户 {#netezza-external}

Netezza外部帐户允许您将活动实例连接到Netezza外部数据库。

1. 在活动 **[!UICONTROL Explorer]**&#x200B;中， **[!UICONTROL Administration]** 单击“>” **[!UICONTROL Platform]** “>” **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]** 并选 **[!UICONTROL External database]** 择为 **[!UICONTROL Type]**。

1. 要配置 **[!UICONTROL Netezza]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**:内泰扎

   * **[!UICONTROL Server]**:Netezza服务器的URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

>[!NOTE]
>
>不考虑对包含自动生成的主键的模式执行的操作。
>
>该表将在模式中定 **义的第** 一个索引上使用Organize on子句。 由于此子句限制为Netezza的1到4列，因此此索引不能包含4列以上。
