---
product: campaign
title: 配置对Oracle的访问
description: 了解如何在FDA中配置对Oracle的访问
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 1%

---

# 配置对Oracle的访问 {#configure-access-to-oracle}



使用Campaign [联合数据访问](../../installation/using/about-fda.md) (FDA)选项，用于处理存储在外部数据库中的信息。 请按照以下步骤配置对Oracle的访问。

1. 配置Oracle [Linux](#oracle-linux) 或 [Windows](#azure-windows)
1. 配置Oracle [外部帐户](#oracle-external) 在Campaign中

## OracleLinux {#oracle-linux}

在FDA中连接到Oracle外部数据库需要在Adobe Campaign服务器上的下面添加其他配置。

1. 安装与您的Oracle版本对应的Oracle完整客户端。
1. 将TNS定义添加到安装中。 为此，请在 **tnsnames.ora** 文件。 如果此存储库不存在，请创建它。

   然后，创建新的TNS_ADMIN环境变量：导出TNS_ADMIN=/etc/oracle并重新启动计算机。

1. 将Oracle集成到Adobe Campaign服务器(nlserver)中。 为此，请检查 **customer.sh** 文件位于Adobe Campaign服务器树结构的“nl6”文件夹中，且包含指向Oracle库的链接。

   例如，对于11.2中的客户：

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

1. 在Campaign Classic中，您可以配置 [!DNL Oracle] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#oracle-external).

## OracleWindows {#oracle-windows}

在FDA中连接到Oracle外部数据库需要在Adobe Campaign服务器上的下面添加其他配置。

1. 安装Oracle客户端。

1. 在C:Oracle文件夹中，创建 **tnsnames.ora** 包含TNS定义的文件。

1. 添加一个以C:Oracle为值的TNS_ADMIN环境变量，然后重新启动计算机。

1. 在Campaign Classic中，您可以配置 [!DNL Oracle] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#oracle-external).

## Oracle外部帐户 {#oracle-external}

的 [!DNL Oracle] 外部帐户允许您将Campaign实例连接到Oracle外部数据库。

1. 从Campaign **[!UICONTROL Explorer]**，选择 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 选择 **[!UICONTROL New]**.

1. 选择 **[!UICONTROL External database]** 作为外部帐户的 **[!UICONTROL Type]**.

1. 配置 **[!UICONTROL Oracle]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**:DNS的名称

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Time zone]**: 服务器时区
   ![](assets/oracle_config.png)
