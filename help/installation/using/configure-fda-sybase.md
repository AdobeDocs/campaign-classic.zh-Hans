---
product: campaign
title: 配置对Sybase IQ的访问权限
description: 了解如何在FDA中配置对Sybase IQ的访问权限
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 配置对Sybase IQ的访问权限 {#configure-access-to-sybase-iq}



使用Campaign **联合数据访问** (FDA)用于处理存储在外部数据库中的信息的选项。 按照以下步骤配置对Sybase IQ的访问权限。

1. 配置 [sybase IQ数据库](#configuring-sybase)
1. 配置Sybase IQ [外部帐户](#sybase-external) 在Campaign中

## sybase IQ配置 {#configuring-sybase}

连接到FDA中的Sybase IQ外部数据库需要在Adobe Campaign服务器上进行以下其他配置。

>[!NOTE]
>
>开始之前，请确保 **unixodbc** 包位于服务器上。

1. 安装 **iq_odbc**. 安装结束时可能会出错。 可以忽略此错误。

1. 安装 **iq_client_common**. 安装结束时，可能会出现Java错误。 可以忽略此错误。

1. 配置ODBC驱动程序。 可以在标准文件中执行配置：对于常规参数，请使用/etc/odbc.ini；对于声明驱动程序，请使用/etc/odbcinst.ini：

   * **/etc/odbc.ini** (替换类似于 `<server_alias>` 个字符)：

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

   * 如果使用customer.sh文件声明路径：为LD_LIBRARY_PATH变量添加路径/opt/sybase/IQ-16_0/lib64 。
   * 否则，请使用Unix命令。

## 外部帐户Sybase IQ {#sybase-external}

使用Sybase IQ外部帐户可将Campaign实例连接到Sybase IQ外部数据库。

1. 来自营销活动 **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 并选择 **[!UICONTROL External database]** 作为 **[!UICONTROL Type]**.

1. 要配置 **[!UICONTROL Sybase IQ]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**：ODBC(Sybase ASE，Sybase IQ)

   * **[!UICONTROL Server]**：对应于ODBC连接(`<server_alias>`)。 不一定是服务器本身的名称。

   * **[!UICONTROL Account]**：用户的名称

   * **[!UICONTROL Password]**：用户帐户密码

   * **[!UICONTROL Database]**：数据库的名称

>[!NOTE]
>
>对于Windows，必须在Adobe Campaign服务器上安装Sybase IQ客户端并创建ODBC连接。 确保在Adobe Campaign服务器(nlserver)作为服务在Windows中运行时创建系统数据源。
