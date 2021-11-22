---
product: campaign
title: 配置对Sybase IQ的访问
description: 了解如何在FDA中配置对Sybase IQ的访问
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 配置对Sybase IQ的访问 {#configure-access-to-sybase-iq}

![](../../assets/v7-only.svg)

使用Campaign **联合数据访问** (FDA)选项，用于处理存储在外部数据库中的信息。 请按照以下步骤配置对Sybase IQ的访问。

1. 配置 [sybase IQ数据库](#configuring-sybase)
1. 配置Sybase IQ [外部帐户](#sybase-external) 在Campaign中

## sybase IQ配置 {#configuring-sybase}

在FDA中连接到Sybase IQ外部数据库需要在Adobe Campaign服务器上的下面进行其他配置。

>[!NOTE]
>
>在开始之前，请确保 **unixodbc** 包在服务器上。

1. 安装 **iq_odbc**. 安装结束时可能会出错。 此错误可以忽略。

1. 安装 **iq_client_common**. 安装结束时可能会出现Java错误。 此错误可以忽略。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行：/etc/odbc.ini用于常规参数，/etc/odbcinst.ini用于声明驱动程序：

   * **/etc/odbc.ini** (将值替换为 `<server_alias>` 字符数):

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

1. 在LD_LIBRARY_PATH变量中添加新libodbc16.so库的路径。 为此，请执行以下操作：

   * 如果您使用customer.sh文件来声明路径：为LD_LIBRARY_PATH变量添加路径/opt/sybase/IQ-16_0/lib64 。
   * 否则，请使用Unix命令。

## sybase IQ外部帐户 {#sybase-external}

利用Sybase IQ外部帐户，可将Campaign实例连接到Sybase IQ外部数据库。

1. 从Campaign **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 选择 **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. 配置 **[!UICONTROL Sybase IQ]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**:ODBC(Sybase ASE，Sybase IQ)

   * **[!UICONTROL Server]**:与ODBC连接(`<server_alias>`)。 不一定是服务器本身的名称。

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

>[!NOTE]
>
>对于Windows，必须在Adobe Campaign服务器上安装Sybase IQ客户端并创建ODBC连接。 确保在Adobe Campaign服务器(nlserver)在Windows中作为服务运行时创建系统数据源。
