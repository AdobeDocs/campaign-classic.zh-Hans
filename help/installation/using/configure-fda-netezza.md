---
product: campaign
title: 配置对Netezza的访问权限
description: 了解如何在FDA中配置对Netezza的访问权限
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# 配置对Netezza的访问权限 {#configure-access-to-netezza}



使用Campaign [联合数据访问](../../installation/using/about-fda.md) (FDA)选项处理存储在外部数据库中的信息。 按照以下步骤配置对Netezza的访问权限。

1. 安装和配置[Netezza驱动程序](#netezza-config)
1. 在Campaign中配置Netezza[外部帐户](#netezza-external)

## netezza配置 {#netezza-config}

连接到FDA中的Netezza外部数据库需要在Adobe Campaign服务器上进行以下其他配置：

1. 根据您使用的操作系统安装用于Netezza的ODBC驱动程序：

   * 用于Linux的&#x200B;**nz-linuxclient-v7.2.0.0.tar.gz**。 选择与您的操作系统（linux或linux64）对应的文件夹，然后启动unpack命令。 您可以将安装保留在存储库中执行，默认情况下建议这样做：“/usr/local/nz”。
   * 用于Windows的&#x200B;**nz-winclient-v7.2.0.0.zip**。 解压缩文件并启动与您的操作系统对应的可执行脚本： nzodbcsetup.exe或nzodbcsetup64.exe。 按照助理说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 可以在标准文件中执行配置： **/etc/odbc.ini**&#x200B;用于常规参数，**/etc/odbcinst.ini**&#x200B;用于声明驱动程序。

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
   * **ODBCINI**： odbc.ini文件的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**： odbc.ini文件的位置。 使用odbc.ini文件时，Netezza还需要此第二个变量。

## netezza外部帐户 {#netezza-external}

netezza外部帐户允许您将Campaign实例连接到Netezza外部数据库。

1. 在营销活动&#x200B;**[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]**“>”**[!UICONTROL Platform]**“>”**[!UICONTROL External accounts]**。

1. 单击&#x200B;**[!UICONTROL New]**&#x200B;并选择&#x200B;**[!UICONTROL External database]**&#x200B;作为&#x200B;**[!UICONTROL Type]**。

1. 要配置&#x200B;**[!UICONTROL Netezza]**&#x200B;外部帐户，您必须指定：

   * **[!UICONTROL Type]**：Netezza

   * **[!UICONTROL Server]**：Netezza服务器的URL

   * **[!UICONTROL Account]**：用户的名称

   * **[!UICONTROL Password]**：用户帐户密码

   * **[!UICONTROL Database]**：数据库的名称

>[!NOTE]
>
>不包含对包含自动生成主键的架构的操作。
>
>该表将在架构中定义的第一个索引上使用&#x200B;**Organize on**&#x200B;子句。 由于此子句限制为1到4列Netezza，因此此索引不能包含超过4列。
