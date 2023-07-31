---
product: campaign
title: 配置对Netezza的访问权限
description: 了解如何在FDA中配置对Netezza的访问权限
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 配置对Netezza的访问权限 {#configure-access-to-netezza}



使用营销活动 [联合数据访问](../../installation/using/about-fda.md) (FDA)用于处理存储在外部数据库中的信息的选项。 按照以下步骤配置对Netezza的访问权限。

1. 安装和配置 [netezza驱动程序](#netezza-config)
1. 配置Netezza [外部帐户](#netezza-external) 在Campaign中

## netezza配置 {#netezza-config}

连接到FDA中的Netezza外部数据库需要在Adobe Campaign服务器上进行以下其他配置：

1. 根据您使用的操作系统安装用于Netezza的ODBC驱动程序：

   * **nz-linuxclient-v7.2.0.0.tar.gz** 用于Linux。 选择与您的操作系统（linux或linux64）对应的文件夹，然后启动unpack命令。 您可以将安装保留在存储库中执行，默认情况下建议这样做：“/usr/local/nz”。
   * **nz-winclient-v7.2.0.0.zip** 用于Windows。 解压缩文件并启动与您的操作系统对应的可执行脚本： nzodbcsetup.exe或nzodbcsetup64.exe。 按照向导说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 可在标准文件中进行配置： **/etc/odbc.ini** 用于常规参数和 **/etc/odbcinst.ini** 用于声明驱动程序。

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     ```

     “InstallDir”对应于odbcinst.ini文件的位置。

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

   * **LD_LIBRARY_PATH**： /usr/local/nz/lib和/usr/local/nz/lib64。 “/usr/local/nz”对应于安装驱动程序时默认提供的安装存储库。 在此，您需要指定为安装选择的存储库。
   * **ODBCINI**：odbc.ini文件的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI路径**：odbc.ini文件的位置。 使用odbc.ini文件时，Netezza还需要此第二个变量。

## netezza外部帐户 {#netezza-external}

netezza外部帐户允许您将Campaign实例连接到Netezza外部数据库。

1. 来自营销活动 **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 并选择 **[!UICONTROL External database]** 作为 **[!UICONTROL Type]**.

1. 配置 **[!UICONTROL Netezza]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**：Netezza服务器的URL

   * **[!UICONTROL Account]**：用户名称

   * **[!UICONTROL Password]**：用户帐户密码

   * **[!UICONTROL Database]**：数据库的名称

>[!NOTE]
>
>不包含对包含自动生成主键的架构的操作。
>
>该表将使用 **组织日期** 在架构中定义的第一个索引上的子句。 由于此子句限制为1到4列Netezza，因此此索引不能包含超过4列。
