---
title: 配置访问Oracle
description: 了解如何在联合数据访问配置访问Oracle
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
source-wordcount: '352'
ht-degree: 0%

---


# 配置访问Oracle {#configure-access-to-oracle}

使用活动 [联合数据访问](../../installation/using/about-fda.md) (联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置访问Oracle。

1. 在Linux或Windows上 [配置](#oracle-linux) Oracle [系统](#azure-windows)
1. 在Oracle中 [配置活动](#oracle-external) 外部帐户

## Oracle在Linux上 {#oracle-linux}

在联合数据访问下连接到Oracle外部数据库需要在Adobe Campaign服务器下面进行其他配置。

1. 安装与您的Oracle版本对应的Oracle完整客户端。
1. 将TNS定义添加到安装中。 为此，请在/etc/ **oracle存储库的tnsnames** .ora文件中指定它们。 如果此存储库不存在，请创建它。

   然后新建一个TNS_ADMIN环境变量：导出TNS_ADMIN=/etc/oracle并重新启动计算机。

1. 将Oracle集成到您的Adobe Campaign服务器(nlserver)中。 为此，请检查Adobe Campaign服 **务器树结构的** “nl6”文件夹中是否存在customer.sh文件，并检查该文件是否包含指向Oracle库的链接。

   例如，对于11.2中的客户端：

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >这些值(特别是ORACLE_HOME)取决于您的安装存储库。 在引用这些值之前，请务必检查树结构。

1. 安装Oracle所需的库：

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. 在Campaign Classic中，您随后可以配置 [!DNL Oracle] 外部帐户。 有关如何配置外部帐户的详细信息，请参 [阅此部分](#oracle-external)。

## OracleWindows版 {#oracle-windows}

在联合数据访问下连接到Oracle外部数据库需要在Adobe Campaign服务器下面进行其他配置。

1. 安装Oracle客户端。

1. 在C:Oracle文件夹中，创 **建包含TNS定** 义的tnsnames.ora文件。

1. 添加一个TNS_ADMIN环境变量，其值为C:Oracle，然后重新启动计算机。

1. 在Campaign Classic中，您随后可以配置 [!DNL Oracle] 外部帐户。 有关如何配置外部帐户的详细信息，请参 [阅此部分](#oracle-external)。

## Oracle外部帐户 {#oracle-external}

外部帐户 [!DNL Oracle] 允许您将活动实例连接到Oracle外部数据库。

1. 从活动 **[!UICONTROL Explorer]**&#x200B;中， **[!UICONTROL Administration]** 选择“>” **[!UICONTROL Platform]** “>” **[!UICONTROL External accounts]**。

1. 选择 **[!UICONTROL New]**。

1. 选 **[!UICONTROL External database]** 择作为外部帐户 **[!UICONTROL Type]**。

1. 配置 **[!UICONTROL Oracle]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**:Oracle

   * **[!UICONTROL Server]**:DNS的名称

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Time zone]**:服务器时区

   ![](assets/oracle_config.png)

