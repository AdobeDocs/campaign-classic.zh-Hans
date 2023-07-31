---
product: campaign
title: 配置对Oracle的访问权限
description: 了解如何在FDA中配置对Oracle的访问权限
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 1%

---

# 配置对Oracle的访问权限 {#configure-access-to-oracle}



使用营销活动 [联合数据访问](../../installation/using/about-fda.md) (FDA)用于处理存储在外部数据库中的信息的选项。 按照以下步骤配置对Oracle的访问权限。

1. 配置Oracle [Linux](#oracle-linux) 或 [Windows](#azure-windows)
1. 配置Oracle [外部帐户](#oracle-external) 在Campaign中

## Linux上的Oracle {#oracle-linux}

连接到FDA中的Oracle外部数据库需要在Adobe Campaign服务器上进行以下其他配置。

1. 安装与您的Oracle版本相对应的Oracle完整客户端。
1. 将TNS定义添加到安装中。 要实现此目的，请在 **tnsnames.ora** /etc/oracle存储库中的文件。 如果此存储库不存在，请创建它。

   然后，创建一个新的TNS_ADMIN环境变量：导出TNS_ADMIN=/etc/environment并重新启动oracle。

1. 将Oracle集成到Adobe Campaign服务器(nlserver)。 要执行此操作，请检查 **customer.sh** 文件位于Adobe Campaign服务器树结构的“nl6”文件夹中，并且其中包含指向Oracle库的链接。

   例如，对于11.2中的客户端：

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >这些值(特别是ORACLE_HOME)取决于您的安装资料档案库。 在引用这些值之前，请确保检查树结构。

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

1. 然后，您可以在Campaign Classic中配置 [!DNL Oracle] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [本节](#oracle-external).

## 在Windows上Oracle {#oracle-windows}

连接到FDA中的Oracle外部数据库需要在Adobe Campaign服务器上进行以下其他配置。

1. 安装Oracle客户端。

1. 在C：Oracle文件夹中，创建 **tnsnames.ora** 包含TNS定义的文件。

1. 添加一个TNS_ADMIN环境变量，并将C：Oracle作为值，然后重新启动计算机。

1. 然后，您可以在Campaign Classic中配置 [!DNL Oracle] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [本节](#oracle-external).

## oracle外部帐户 {#oracle-external}

此 [!DNL Oracle] 外部帐户允许您将Campaign实例连接到Oracle外部数据库。

1. 来自营销活动 **[!UICONTROL Explorer]**，选择 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 选择 **[!UICONTROL New]**.

1. 选择 **[!UICONTROL External database]** 作为外部帐户的 **[!UICONTROL Type]**.

1. 配置 **[!UICONTROL Oracle]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**：DNS的名称

   * **[!UICONTROL Account]**：用户名称

   * **[!UICONTROL Password]**：用户帐户密码

   * **[!UICONTROL Time zone]**: 服务器时区

   ![](assets/oracle_config.png)
