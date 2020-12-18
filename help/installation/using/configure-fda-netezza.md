---
solution: Campaign Classic
product: campaign
title: 配置访问Netezza
description: 了解如何在联合数据访问配置访问Netezza
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# 配置对Netezza{#configure-access-to-netezza}的访问

使用活动[联合数据访问](../../installation/using/about-fda.md)(联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置访问Netezza。

1. 安装和配置[Netezza驱动程序](#netezza-config)
1. 将Netezza[外部帐户](#netezza-external)配置为活动

## Netezza配置{#netezza-config}

在联合数据访问下连接到Netezza外部数据库需要在Adobe Campaign服务器下面进行其他配置：

1. 根据您使用的操作系统，为Netezza安装ODBC驱动程序：

   * **nz-linuxclient-v7.2.0.0.tar.** gzfor Linux。选择与您的操作系统（linux或linux64）对应的文件夹，并开始unpack命令。 您可以保留默认建议在存储库中执行的安装：&quot;/usr/local/nz&quot;。
   * **nz-winclient-v7.2.0.0.** zippfor Windows解压缩文件并开始与操作系统对应的可执行脚本：nzodbcsetup.exe或nzodbcsetup64.exe。 按照向导说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行：**/etc/odbc.ini**&#x200B;用于常规参数，**/etc/odbcinst.ini**&#x200B;用于声明驱动程序。

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

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib和/usr/local/nz/lib64。“/usr/local/nz”与安装驱动程序时默认提供的安装存储库相对应。 您需要在此指定已为安装选择的存储库。
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**:odbc.ini文件的位置。Netezza还要求使用odbc.ini文件的第二个变量。

## Netezza外部帐户{#netezza-external}

netezza外部帐户允许您将活动实例连接到Netezza外部数据库。

1. 在活动&#x200B;**[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 单击&#x200B;**[!UICONTROL New]**&#x200B;并选择&#x200B;**[!UICONTROL External database]**&#x200B;作为&#x200B;**[!UICONTROL Type]**。

1. 要配置&#x200B;**[!UICONTROL Netezza]**&#x200B;外部帐户，必须指定：

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**:netezza服务器的URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

>[!NOTE]
>
>不考虑对包含自动生成的主键的模式执行的操作。
>
>该表将在模式中定义的第一个索引上使用&#x200B;**Organize on**&#x200B;子句。 由于此子句限制为带有Netezza的1到4列，因此此索引不能包含4列以上。
