---
title: 配置对Sybase IQ的访问
description: 了解如何在联合数据访问中配置对Sybase IQ的访问
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
source-wordcount: '319'
ht-degree: 0%

---


# 配置对Sybase IQ的访问 {#configure-access-to-sybase-iq}

使用活动 **联合数据访问** (联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对Sybase IQ的访问。

1. 配置 [Sybase IQ数据库](#configuring-sybase)
1. 在活动中配 [置Sybase](#sybase-external) IQ外部帐户

## Sybase IQ配置 {#configuring-sybase}

在联合数据访问下连接到Sybase IQ外部数据库需要在Adobe Campaign服务器上进行下面的其他配置。

>[!NOTE]
>
>在启动之前，请确 **保unixodbc** 包在服务器上。

1. 安 **装iq_odbc**。 安装结束时可能会出错。 可以忽略此错误。

1. 安 **装iq_client_common**。 安装结束时可能会发生Java错误。 可以忽略此错误。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行：/etc/odbc.ini用于常规参数，/etc/odbcinst.ini用于声明驱动程序：

   * **/etc/odbc.ini** (将字符等 `<server_alias>` 值替换为您自己的值):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. 在LD_LIBRARY_PATH变量中为新libodbc16.so库添加路径。 为此：

   * 如果您使用customer.sh文件声明您的路径：为LD_LIBRARY_PATH变量添加路径/opt/sybase/IQ-16_0/lib64。
   * 否则，请使用Unix命令。

## Sybase IQ外部帐户 {#sybase-external}

Sybase IQ外部帐户允许您将活动实例连接到Sybase IQ外部数据库。

1. 在活动 **[!UICONTROL Explorer]**&#x200B;中， **[!UICONTROL Administration]** 单击“>” **[!UICONTROL Platform]** “>” **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]** 并选 **[!UICONTROL External database]** 择为 **[!UICONTROL Type]**。

1. 要配置 **[!UICONTROL Sybase IQ]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**:ODBC(Sybase ASE、Sybase IQ)

   * **[!UICONTROL Server]**:与第5步中定义的ODBC`<server_alias>`连接()相对应。 不一定是服务器本身的名称。

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

>[!NOTE]
>
>对于Windows，必须在Adobe Campaign服务器上安装Sybase IQ客户端并创建ODBC连接。 确保在Windows中Adobe Campaign服务器(nlserver)作为服务运行时创建系统数据源。

