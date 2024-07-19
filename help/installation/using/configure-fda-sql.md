---
product: campaign
title: 配置对Microsoft SQL Server的访问权限
description: 了解如何配置对Microsoft SQL Server的访问权限
feature: Installation, Federated Data Access
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 1%

---

# 配置对Microsoft SQL Server的访问权限 {#configure-fda-sql}



使用Campaign **联合数据访问** (FDA)选项处理存储在外部Microsoft SQL Server数据库中的信息。 按照以下步骤配置对[!DNL Microsoft SQL Server]的访问权限。

1. 在[CentOS](#sql-centos)上配置[!DNL Microsoft SQL Server]。
1. 在[Linux](#sql-linux)上配置[!DNL Microsoft SQL Server]。
1. 在[Windows](#sql-windows)上配置[!DNL Microsoft SQL Server]。
1. 在Campaign中配置[!DNL Microsoft SQL Server] [外部帐户](#sql-external)

## CentOS上的Microsoft SQL Server {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server]在CentOS 7和6上可用。

要在CentOS上配置[!DNL Microsoft SQL Server]，请执行以下步骤：

1. 使用以下命令下载并安装SQL ODBC驱动程序：

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. 然后，您可以在Adobe Campaign中配置[!DNL Microsoft SQL Server]外部帐户。 有关如何配置外部帐户的更多信息，请参阅[此部分](#sql-external)。

## Linux上的Microsoft SQL Server {#sql-linux}

>[!NOTE]
>
> 如果您运行的是旧版Adobe Campaign（7.2.1之前），则需要安装`unix ODBC drivers`。

1. 从[此页面](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/)下载MS ODBC驱动程序。

1. 以root用户身份运行以下命令：

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. 然后，您可以在Adobe Campaign中配置[!DNL Microsoft SQL Server]外部帐户。 有关如何配置外部帐户的更多信息，请参阅[此部分](#sql-external)。

## Windows上的Microsoft SQL Server {#sql-windows}

要在Windows上配置[!DNL Microsoft SQL Server]，请执行以下操作：

1. 在Windows中，单击&#x200B;**[!UICONTROL Control Panel]**“>”**[!UICONTROL System and Security]**“>”**[!UICONTROL Administrative Tools]**“>”**[!UICONTROL ODBC Data Sources (64-bit)]**。

1. 在&#x200B;**[!UICONTROL ODBC Data Sources (64-bit)]**&#x200B;新窗口中，单击&#x200B;**[!UICONTROL Add...]**。

1. 检查&#x200B;**[!UICONTROL Create New Data Source]**&#x200B;窗口中是否列出SQL Server Native Client v11。

1. 如果未列出SQL Server Native Client，则可以在[此页](https://www.microsoft.com/en-my/download/details.aspx?id=36434)中下载它。

1. 然后，您可以在Adobe Campaign中配置[!DNL Microsoft SQL Server]外部帐户。 有关如何配置外部帐户的更多信息，请参阅[此部分](#sql-external)。

## Microsoft SQL Server外部帐户 {#sql-external}

您需要创建一个[!DNL Microsoft SQL Server]外部帐户以将Campaign实例连接到[!DNL Microsoft SQL Server]外部数据库。

1. 在营销活动&#x200B;**[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]**“>”**[!UICONTROL Platform]**“>”**[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**。

1. 选择&#x200B;**[!UICONTROL External database]**&#x200B;作为外部帐户的&#x200B;**[!UICONTROL Type]**。

1. 在&#x200B;**[!UICONTROL Configuration]**&#x200B;下，从&#x200B;**[!UICONTROL Type]**&#x200B;下拉列表中选择[!DNL Microsoft SQL Server]。

   ![](assets/sql.png)

1. 配置&#x200B;**[!UICONTROL Microsoft SQL Server]**&#x200B;外部帐户身份验证：

   * **[!UICONTROL Server]**： [!DNL Microsoft SQL Server]服务器的URL。

   * **[!UICONTROL Account]**：用户的名称。

   * **[!UICONTROL Password]**：用户帐户密码。

   * **[!UICONTROL Database]**：数据库的名称（可选）。

   * **[!UICONTROL Timezone]**： [!DNL Microsoft SQL Server]中设置了时区。 [了解详情](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. 单击&#x200B;**[!UICONTROL Parameters]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Deploy functions]**&#x200B;按钮以创建函数。

   >[!NOTE]
   >
   >要使所有函数都可用，您需要在远程数据库中创建Adobe Campaign SQL函数。 有关详细信息，请参阅此[页面](../../configuration/using/adding-additional-sql-functions.md)。

1. 配置完成后，单击&#x200B;**[!UICONTROL Save]**。

连接器支持以下选项：

| 选项 | 说明 |
|---|---|
| 身份验证 | 连接器支持的身份验证类型。 当前支持的值： ActiveDirectoryMSI。 <br>有关更多信息，请参阅[Microsoft文档](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings)的示例8。 |
| 加密 | 指定连接是否通过网络使用TLS加密。 可能的值为&#x200B;**yes/mandatory （18.0及更高版本）**、**no/optional （18.0及更高版本）**&#x200B;和&#x200B;**strict （18.0及更高版本）**。 在版本18.0及更高版本中，默认值设置为&#x200B;**是**；在早期版本中，默认值设置为&#x200B;**否**。 <br>有关详细信息，请参阅[Microsoft文档](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt)。 |
| TrustserverCertificate | 与&#x200B;**Encrypt**&#x200B;一起使用时，启用使用自签名服务器证书的加密。 <br>接受值： **是**&#x200B;或&#x200B;**否**（默认值，表示将验证服务器证书）。 |
