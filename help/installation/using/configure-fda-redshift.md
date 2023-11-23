---
product: campaign
title: 配置对Amazon Redshift的访问权限
description: 了解如何在FDA中配置对Amazon Redshift的访问权限
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 6939307c0b33ff662fe4ef9ae0192ae7b500a95c
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 6%

---

# 配置对Amazon Redshift的访问权限 {#configure-access-to-redshift}

使用营销活动 **联合数据访问** (FDA)用于处理存储在外部数据库中的信息的选项。 执行以下步骤以配置对Amazon Redshift的访问权限。

1. 配置 [Amazon Redshift数据库](#configuring-redshift)
1. 配置Amazon Redshift [外部帐户](#redshift-external) 在Campaign中

## Linux上的Amazon Redshift {#redshift-linux}

配置 [!DNL Amazon Redshift] 在Linux上，请执行以下步骤：

1. 在ODBC安装之前，请检查在Linux分发服务器上是否安装了以下软件包：

   * 对于Red Hat/CentOS：

     ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
     ```

   * 对于Debian：

     ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
     ```

1. 在运行脚本之前，您可以使用 `--help` 选项：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./redshift_odbc-setup.sh --help
   ```

1. 访问脚本所在的目录，并以root用户身份运行以下脚本：

   ```
     cd /usr/local/neolane/nl6/bin/fda-setup-scripts
     ./redshift_odbc-setup.sh
   ```

1. 安装ODBC驱动程序后，需要重新启动Campaign Classic。 为此，请运行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 然后，您可以在Campaign中配置 [!DNL Amazon Redshift] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [本节](#redshift-external).

## Amazon Redshift外部帐户 {#redshift-external}

此 [!DNL Amazon Redshift] 外部帐户允许您将Campaign实例连接到Amazon Redshift外部数据库。

1. 在Campaign Classic中，配置您的 [!DNL Amazon Redshift] 外部帐户。 从 **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]**。

1. 选择 **[!UICONTROL External database]** 作为外部帐户的 **[!UICONTROL Type]**.

1. 配置 **[!UICONTROL Amazon Redshift]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**: Amazon Redshift

   * **[!UICONTROL Server]**：DNS的名称

   * **[!UICONTROL Account]**：用户名称

   * **[!UICONTROL Password]**：用户帐户密码

   * **[!UICONTROL Database]**：如果未在DSN中指定数据库的名称。 如果在DSN中指定，它可以留空

   * **[!UICONTROL Working schema]**：工作模式的名称。 [了解详情](https://docs.aws.amazon.com/redshift/latest/dg/r_Schemas_and_tables.html)

   * **[!UICONTROL Time zone]**: 服务器时区

   ![](assets/amazon_redshift.png)

1. 单击 **[!UICONTROL Save]**。
