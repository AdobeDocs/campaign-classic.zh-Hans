---
solution: Campaign Classic
product: campaign
title: 配置对Oracle的访问
description: 了解如何在联合数据访问中配置对Oracle的访问
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# 配置对Oracle {#configure-access-to-oracle}的访问

使用活动 [联合数据访问](../../installation/using/about-fda.md)(联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对Oracle的访问。

1. 在[Linux](#oracle-linux)或[Windows](#azure-windows)上配置Oracle
1. 在活动中配置Oracle [外部帐户](#oracle-external)

## Oracle Linux {#oracle-linux}

在联合数据访问中连接到Oracle外部库需要在Adobe Campaign服务器上的以下其他配置。

1. 安装与您的Oracle版本对应的Oracle完整客户端。
1. 将您的TNS定义添加到安装中。 为此，请在/etc/oracle存储库的&#x200B;**tnsnames.ora**&#x200B;文件中指定它们。 如果此存储库不存在，请创建它。

   然后新建一个TNS_ADMIN环境变量：导出TNS_ADMIN=/etc/oracle并重新启动计算机。

1. 将Oracle集成到您的Adobe Campaign服务器(nlserver)中。 为此，请检查&#x200B;**customer.sh**&#x200B;文件是否位于Adobe Campaign服务器树结构的“nl6”文件夹中，并且它包含指向Oracle库的链接。

   例如，对于11.2中的客户端：

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >这些值(特别是ORACLE_HOME)取决于您的安装存储库。 在引用这些值之前，请确保检查树结构。

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

1. 在Campaign Classic中，您随后可以配置[!DNL Oracle]外部帐户。 有关如何配置外部帐户的详细信息，请参阅[本节](#oracle-external)。

## Oracle Windows {#oracle-windows}

在联合数据访问中连接到Oracle外部库需要在Adobe Campaign服务器上的以下其他配置。

1. 安装Oracle客户端。

1. 在C:Oracle文件夹中，创建一个包含您的TNS定义的&#x200B;**tnsnames.ora**&#x200B;文件。

1. 添加一个TNS_ADMIN环境变量，将C:Oracle作为值并重新启动计算机。

1. 在Campaign Classic中，您随后可以配置[!DNL Oracle]外部帐户。 有关如何配置外部帐户的详细信息，请参阅[本节](#oracle-external)。

## Oracle 外部帐户 {#oracle-external}

[!DNL Oracle]外部帐户允许您将活动实例连接到Oracle外部数据库。

1. 从活动&#x200B;**[!UICONTROL Explorer]**&#x200B;中，选择&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 选择&#x200B;**[!UICONTROL New]**。

1. 选择&#x200B;**[!UICONTROL External database]**&#x200B;作为外部帐户的&#x200B;**[!UICONTROL Type]**。

1. 配置&#x200B;**[!UICONTROL Oracle]**&#x200B;外部帐户，必须指定：

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**:DNS的名称

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Time zone]**:服务器时区

   ![](assets/oracle_config.png)

