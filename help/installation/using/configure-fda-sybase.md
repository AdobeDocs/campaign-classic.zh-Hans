---
product: campaign
title: 配置对Sybase IQ的访问权限
description: 了解如何在FDA中配置对Sybase IQ的访问权限
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 配置对Sybase IQ的访问权限 {#configure-access-to-sybase-iq}



使用Campaign **联合数据访问** (FDA)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对Sybase IQ的访问权限。

1. 配置[Sybase IQ数据库](#configuring-sybase)
1. 在Campaign中配置Sybase IQ[外部帐户](#sybase-external)

## sybase IQ配置 {#configuring-sybase}

连接到FDA中的Sybase IQ外部数据库需要在Adobe Campaign服务器上进行以下其他配置。

>[!NOTE]
>
>开始之前，请确保&#x200B;**unixodbc**&#x200B;包位于服务器上。

1. 安装&#x200B;**iq_odbc**。 安装结束时可能会出错。 可以忽略此错误。

1. 安装&#x200B;**iq_client_common**。 安装结束时，可能会出现Java错误。 可以忽略此错误。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行： /etc/odbc.ini用于常规参数，/etc/odbcinst.ini用于声明驱动程序：

   * **/etc/odbc.ini** （将诸如`<server_alias>`个字符之类的值替换为您自己的值）：

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
   * 否则，使用Unix命令。

## sybase IQ外部帐户 {#sybase-external}

利用Sybase IQ外部帐户，可将Campaign实例连接到Sybase IQ外部数据库。

1. 在营销活动&#x200B;**[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]**“>”**[!UICONTROL Platform]**“>”**[!UICONTROL External accounts]**。

1. 单击&#x200B;**[!UICONTROL New]**&#x200B;并选择&#x200B;**[!UICONTROL External database]**&#x200B;作为&#x200B;**[!UICONTROL Type]**。

1. 要配置&#x200B;**[!UICONTROL Sybase IQ]**&#x200B;外部帐户，您必须指定：

   * **[!UICONTROL Type]**： ODBC (Sybase ASE，Sybase IQ)

   * **[!UICONTROL Server]**：对应于步骤5中定义的ODBC连接(`<server_alias>`)。 不一定是服务器本身的名称。

   * **[!UICONTROL Account]**：用户的名称

   * **[!UICONTROL Password]**：用户帐户密码

   * **[!UICONTROL Database]**：数据库的名称

>[!NOTE]
>
>对于Windows，必须在Adobe Campaign服务器上安装Sybase IQ客户端并创建ODBC连接。 确保在Adobe Campaign服务器(nlserver)作为服务在Windows中运行时创建系统数据源。
