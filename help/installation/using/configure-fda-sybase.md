---
solution: Campaign Classic
product: campaign
title: 配置对Sybase IQ的访问
description: 了解如何在联合数据访问中配置对Sybase IQ的访问
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# 配置对Sybase IQ {#configure-access-to-sybase-iq}的访问

使用活动 **联合数据访问**(联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对Sybase IQ的访问。

1. 配置[Sybase IQ数据库](#configuring-sybase)
1. 在活动中配置Sybase IQ [外部帐户](#sybase-external)

## sybase IQ配置{#configuring-sybase}

在联合数据访问中连接到Sybase IQ外部库需要在Adobe Campaign服务器上的以下其他配置。

>[!NOTE]
>
>在启动之前，请确保&#x200B;**unixodbc**&#x200B;包位于服务器上。

1. 安装&#x200B;**iq_odbc**。 安装结束时可能会出错。 可以忽略此错误。

1. 安装&#x200B;**iq_client_common**。 安装结束时可能会出现Java错误。 可以忽略此错误。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行：/etc/odbc.ini用于常规参数，/etc/odbcinst.ini用于声明驱动程序：

   * **/etc/odbc.ini(** 将字符等值 `<server_alias>` 替换为您自己的值):

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

## sybase IQ 外部帐户 {#sybase-external}

Sybase IQ外部帐户允许您将活动实例连接到Sybase IQ外部数据库。

1. 在活动&#x200B;**[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 单击&#x200B;**[!UICONTROL New]**&#x200B;并选择&#x200B;**[!UICONTROL External database]**&#x200B;作为&#x200B;**[!UICONTROL Type]**。

1. 要配置&#x200B;**[!UICONTROL Sybase IQ]**&#x200B;外部帐户，必须指定：

   * **[!UICONTROL Type]**:ODBC(Sybase ASE、Sybase IQ)

   * **[!UICONTROL Server]**:与第5步中定义的ODBC`<server_alias>`连接()相对应。不一定是服务器本身的名称。

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

>[!NOTE]
>
>对于Windows，必须在Adobe Campaign服务器上安装Sybase IQ客户端并创建ODBC连接。 确保在Windows中作为服务运行Adobe Campaign服务器(nlserver)时创建系统数据源。

