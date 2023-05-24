---
product: campaign
title: 配置对Microsoft SQL Server的访问权限
description: 了解如何配置对Microsoft SQL Server的访问权限
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 1%

---

# 配置对Microsoft SQL Server的访问权限 {#configure-fda-sql}



使用Campaign **联合数据访问** (FDA)选项，用于处理存储在外部Microsoft SQL Server数据库中的信息。 按照以下步骤配置对的访问权限 [!DNL Microsoft SQL Server].

1. 配置 [!DNL Microsoft SQL Server] 日期 [CentOS](#sql-centos).
1. 配置 [!DNL Microsoft SQL Server] 日期 [Linux](#sql-linux).
1. 配置 [!DNL Microsoft SQL Server] 日期 [Windows](#sql-windows).
1. 配置 [!DNL Microsoft SQL Server] [外部帐户](#sql-external) 在Campaign中

## CentOS上的Microsoft SQL Server {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] 在CentOS 7和6上提供。

配置 [!DNL Microsoft SQL Server] 在CentOS上，请执行以下步骤：

1. 使用以下命令下载并安装SQL ODBC驱动程序：

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. 然后，您可以在Adobe Campaign中配置 [!DNL Microsoft SQL Server] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [本节](#sql-external).

## Linux上的Microsoft SQL Server {#sql-linux}

>[!NOTE]
>
> 如果您运行的Adobe Campaign版本较低（7.2.1之前的版本），则需要安装 `unix ODBC drivers`.

1. 从下载MS ODBC驱动程序 [此页面](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/).

1. 以root用户身份运行以下命令：

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. 然后，您可以在Adobe Campaign中配置 [!DNL Microsoft SQL Server] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [本节](#sql-external).

## Windows上的Microsoft SQL Server {#sql-windows}

配置 [!DNL Microsoft SQL Server] 在Windows上：

1. 在Windows中，单击 **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. 从 **[!UICONTROL ODBC Data Sources (64-bit)]** 新窗口，单击 **[!UICONTROL Add...]**.

1. 检查SQL Server Native Client v11是否列在 **[!UICONTROL Create New Data Source]** 窗口。

1. 如果未列出SQL Server Native Client，则可以将其下载到 [此页面](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. 然后，您可以在Adobe Campaign中配置 [!DNL Microsoft SQL Server] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [本节](#sql-external).

## Microsoft SQL Server外部帐户 {#sql-external}

您需要创建 [!DNL Microsoft SQL Server] 用于将Campaign实例连接到 [!DNL Microsoft SQL Server] 外部数据库。

1. 来自营销活动 **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]**。

1. 选择 **[!UICONTROL External database]** 作为外部帐户的 **[!UICONTROL Type]**.

1. 下 **[!UICONTROL Configuration]**，选择 [!DNL Microsoft SQL Server] 从 **[!UICONTROL Type]** 下拉菜单。

   ![](assets/sql.png)

1. 配置 **[!UICONTROL Microsoft SQL Server]** 外部帐户身份验证：

   * **[!UICONTROL Server]**：的URL [!DNL Microsoft SQL Server] 服务器。

   * **[!UICONTROL Account]**：用户的名称。

   * **[!UICONTROL Password]**：用户帐户密码。

   * **[!UICONTROL Database]**：数据库的名称（可选）。

   * **[!UICONTROL Timezone]**：时区设置于 [!DNL Microsoft SQL Server]. [了解详情](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. 单击 **[!UICONTROL Parameters]** 按Tab键，然后 **[!UICONTROL Deploy functions]** 按钮创建函数。

   >[!NOTE]
   >
   >要使所有函数都可用，您需要在远程数据库中创建Adobe Campaign SQL函数。 有关更多信息，请参阅此 [页面](../../configuration/using/adding-additional-sql-functions.md).

1. 单击 **[!UICONTROL Save]** 配置完成后。

连接器支持以下选项：

| Option | 说明 |
|---|---|
| 身份验证 | 连接器支持的身份验证类型。 当前支持的值： ActiveDirectoryMSI。 <br> 有关更多信息，请参阅示例8 [Microsoft文档](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| 加密 | 指定连接是否通过网络使用TLS加密。 可能的值包括 **是/必需（18.0及更高版本）**， **no/optional（18.0及更高版本）**、和 **strict（18.0及更高版本）**. 默认值设置为 **是** 版本18.0及更高版本中的 **否** 在以前的版本中。 <br>有关更多信息，请参阅 [Microsoft文档](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustserverCertificate | 使用自签名服务器证书启用加密（与配合使用时） **加密**. <br>接受的值： **是** 或 **否** （默认值，表示将验证服务器证书）。 |
