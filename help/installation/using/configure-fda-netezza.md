---
product: campaign
title: 配置对Netezza的访问
description: 了解如何在FDA中配置对Netezza的访问
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# 配置对Netezza的访问 {#configure-access-to-netezza}



使用Campaign [联合数据访问](../../installation/using/about-fda.md) (FDA)选项，用于处理存储在外部数据库中的信息。 请按照以下步骤配置对Netezza的访问。

1. 安装和配置 [Netezza驱动程序](#netezza-config)
1. 配置Netezza [外部帐户](#netezza-external) 在Campaign中

## Netezza配置 {#netezza-config}

在FDA中连接到Netezza外部数据库需要在Adobe Campaign服务器上进行以下其他配置：

1. 根据您使用的操作系统安装ODBC驱动程序进行Netezza:

   * **nz-linuxclient-v7.2.0.0.tar.gz** 的URL。 选择与您的操作系统（linux或linux64）对应的文件夹，然后启动unpack命令。 您可以保留默认建议在存储库中执行的安装：&quot;/usr/local/nz&quot;。
   * **nz-winclient-v7.2.0.0.zip** （对于Windows）。 解压缩文件，并启动与您的操作系统对应的可执行脚本：nzodbcsetup.exe或nzodbcsetup64.exe。 按照向导说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行： **/etc/odbc.ini** 对于常规参数和 **/etc/odbcinst.ini** 来宣布司机。

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

1. 指定Adobe Campaign服务器的环境变量：

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib和/usr/local/nz/lib64。 “/usr/local/nz”对应于安装驱动程序时默认提供的安装存储库。 您需要在此指定为安装选择的存储库。
   * **奥德布奇尼**:odbc.ini文件的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**:odbc.ini文件的位置。 Netezza还需要此第二个变量才能使用odbc.ini文件。

## Netezza外部帐户 {#netezza-external}

netezza外部帐户允许您将Campaign实例连接到Netezza外部数据库。

1. 从Campaign **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 选择 **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. 配置 **[!UICONTROL Netezza]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**:netezza服务器的URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

>[!NOTE]
>
>不考虑对包含自动生成的主键的架构的操作。
>
>该表将使用 **组织** 子句。 由于此子句的Netezza限制为1到4列，因此此索引不能包含4列以上。
