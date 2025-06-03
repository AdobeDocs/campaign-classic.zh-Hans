---
product: campaign
title: Campaign - Microsoft Dynamics CRM连接器
description: 了解如何连接Campaign和Microsoft Dynamics
feature: Microsoft CRM Integration
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
hide: true
hidefromtoc: true
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '1104'
ht-degree: 2%

---

# 连接Campaign和Microsoft Dynamics 365{#connect-to-msdyn}



在本页中，您将了解如何将Campaign Classic连接到&#x200B;**Microsoft Dynamics CRM 365**。

可能的部署是通过&#x200B;**Web API**（推荐）。 请参阅下面的[部分](#microsoft-dynamics-implementation-step)，了解与Microsoft Dynamics建立连接的步骤。

数据同步通过专用工作流活动执行。 [了解详情](../../platform/using/crm-data-sync.md)。

## 实施步骤{#microsoft-dynamics-implementation-steps}

要通过&#x200B;**Web API**&#x200B;连接Microsoft Dynamics 365以使用Adobe Campaign，您需要应用以下步骤：

在Microsoft Dynamics CRM中：
1. 获取Microsoft Dynamics客户端ID
1. 生成Microsoft Dynamics证书密钥标识符和密钥ID
1. 配置权限
1. 创建应用程序用户
1. 编码私钥

[在本节中了解详情](#config-crm-microsoft)

在Campaign Classic中：
1. 创建新的外部帐户
1. 使用Microsoft Dynamics设置配置外部帐户
1. 使用Configuration Assistant映射表和同步枚举
1. 创建同步工作流

[在本节中了解详情](#configure-acc-for-microsoft)


>[!CAUTION]
> 将Adobe Campaign与Microsoft Dynamics连接时，您无法：
> * 安装可更改CRM行为并导致与Adobe Campaign兼容问题的插件
> * 选择多个枚举

## 配置Microsoft Dynamics CRM {#config-crm-microsoft}

若要生成访问令牌和密钥以设置帐户，您需要使用&#x200B;**全局管理员**&#x200B;凭据登录到[Microsoft Azure目录](https://portal.azure.com)。 然后按照下面列出的步骤操作。

### 获取Microsoft Dynamics客户端ID {#get-client-id-microsoft}

要获取客户端ID，您需要在Azure Active Directory中注册应用程序。 客户端ID与应用程序ID相同。

1. 导航到&#x200B;**Azure Active Directory >应用程序注册**，然后单击&#x200B;**新建应用程序注册**。
1. 提供一个唯一的名称，以帮助识别实例，如&#x200B;**adobecampaign`<instance identifier>`**。
1. 选择&#x200B;**应用程序类型**&#x200B;作为&#x200B;**Web应用程序/API**。
1. 将`http://localhost`用于&#x200B;**登录URL**。

保存后，您会获得一个&#x200B;**应用程序ID**，它是Campaign的客户标识符。

请参阅[此页面](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)以了解详情。

### 生成Microsoft Dynamics证书密钥标识符和密钥ID {#config-certificate-key-id}

要获取&#x200B;**证书密钥标识符(customKeyIdentifier)**&#x200B;和&#x200B;**密钥ID (keyId)**，请执行以下步骤：

1. 导航到&#x200B;**Azure Active Directory >应用程序注册**，然后选择之前创建的应用程序。
1. 单击&#x200B;**证书和密码**。
1. 单击&#x200B;**上载证书**，然后浏览并上载生成的公共证书。
1. 要生成证书，您可以使用openssl。

   例如：

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >您可以更改代码示例中的天数（此处`-days 365`），以获得更长的证书有效期。

1. 然后，您需要在base64中进行编码。 为此，您可以使用Base64编码器帮助或使用适用于Linux的命令行`base64 -w0 private.key`。

1. 单击&#x200B;**清单**&#x200B;链接以获取&#x200B;**证书密钥标识符(customKeyIdentifier)**&#x200B;和&#x200B;**密钥ID (keyId)**。

稍后需要使用&#x200B;**证书密钥标识符(customKeyIdentifier)**&#x200B;和&#x200B;**密钥ID (keyId)**&#x200B;来使用证书&#x200B;**[!UICONTROL CRM O-Auth type]**&#x200B;配置您的Microsoft Dynamics CRM外部帐户。

### 配置权限 {#config-permissions-microsoft}

**步骤1**：为创建的应用程序配置&#x200B;**所需权限**。

1. 导航到&#x200B;**Azure Active Directory >应用程序注册**，然后选择之前创建的应用程序。
1. 单击左上方的&#x200B;**设置**。
1. 在&#x200B;**所需权限**&#x200B;上，单击&#x200B;**添加**&#x200B;和&#x200B;**选择API > Dynamics CRM Online**。
1. 单击&#x200B;**选择**，启用&#x200B;**以组织用户身份访问Dynamics 365**&#x200B;复选框，然后单击&#x200B;**选择**。
1. 然后，从应用程序的&#x200B;**管理**&#x200B;菜单下选择&#x200B;**清单**。

1. 在&#x200B;**清单**&#x200B;编辑器中，将`allowPublicClient`属性从`null`设置为`true`，然后单击&#x200B;**保存**。

**步骤2**：授予管理员同意

1. 导航到&#x200B;**Azure Active Directory >企业应用程序**。

1. 选择要向其授予租户范围管理员同意的应用程序。

1. 从左窗格菜单中选择&#x200B;**安全性**&#x200B;下的&#x200B;**权限**。

1. 单击&#x200B;**授予管理员同意**。

有关此内容的详细信息，请参阅[Azure文档](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal)。

### 创建应用程序用户 {#create-app-user-microsoft}

>[!NOTE]
>
> 此步骤对于&#x200B;**[!UICONTROL Password credentials]**&#x200B;身份验证是可选的。

应用程序用户是上面注册的应用程序将使用的用户。 使用上面注册的应用程序对Microsoft Dynamics所做的任何更改都将通过此用户完成。

**步骤1**：在azure active directory上创建非交互式用户

1. 单击&#x200B;**Azure Active Directory >用户**，然后单击&#x200B;**新建用户**。
1. 提供您想要使用的正确名称，用户名应为电子邮件格式。
1. 在&#x200B;**目录角色**&#x200B;中选择&#x200B;**Dynamics 365管理员**。

**步骤2**：为创建的用户分配适当的许可证

1. 从[Microsoft Azure](https://portal.azure.com)，单击&#x200B;**管理员应用**。
1. 转到&#x200B;**用户>活动用户**，然后单击新创建的用户。
1. 单击&#x200B;**编辑产品许可证**&#x200B;并选择&#x200B;**Dynamics 365客户参与计划**。
1. 单击&#x200B;**关闭**。

**步骤3**：在Dynamics CRM上创建应用程序用户

1. 从[Microsoft Azure](https://portal.azure.com)，导航到&#x200B;**设置>安全>用户**。
1. 单击下拉列表，选择&#x200B;**应用程序用户**，然后单击&#x200B;**新建**。
1. 使用与上述在Active Directory上创建的用户相同的用户名

   >[!NOTE]
   >
   >使用相同名称会引发重复键错误，因此在我们获得是否需要此步骤的确认之前，请使用其他用户名并继续。
   >

1. 为您之前创建的[应用程序](#get-client-id-microsoft)分配&#x200B;**应用程序ID**。
1. 单击&#x200B;**管理角色**&#x200B;并为用户选择&#x200B;**系统管理员**&#x200B;角色。

## 配置营销活动 {#configure-acc-for-microsoft}

>[!NOTE]
>
> 从Microsoft[&#128279;](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint)停用RDS后，内部部署和Office 365类型的CRM部署不再与Campaign兼容。 Adobe Campaign现在仅支持CRM版本&#x200B;**Dynamic CRM 365**&#x200B;的Web API部署。 [了解详情](../../rn/using/deprecated-features.md#crm-connectors)。

要连接Microsoft Dynamics 365和Campaign，您需要在Campaign中创建并配置专用的&#x200B;**[!UICONTROL External Account]**。

1. 导航到&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。

1. 选择&#x200B;**[!UICONTROL Microsoft Dynamics CRM]**&#x200B;外部帐户。 勾选 **[!UICONTROL Enabled]** 选项。

1. 填写连接Microsoft Dynamics 365和Campaign所需的信息。

   >[!NOTE]
   >
   >在此部分[&#128279;](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)中详细介绍了中每个&#x200B;**[!UICONTROL CRM O-Auth type]**&#x200B;的Microsoft Dynamics CRM外部帐户配置。

   ![](assets/crm-ms-dynamics-ext-account.png)

1. 单击&#x200B;**[!UICONTROL Microsoft CRM configuration assistant...]**&#x200B;链接。 Adobe Campaign会自动从Microsoft Dynamics数据模板中检测表。

   ![](assets/crm_connectors_msdynamics_02.png)

1. 选择要恢复的表。

   ![](assets/crm_connectors_msdynamics_03.png)

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;开始创建相应的架构。

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >要批准配置，必须断开/重新连接到Adobe Campaign控制台。

   您可以检查匹配的数据架构是否在Adobe Campaign中变得可用。

   ![](assets/crm_connectors_msdynamics_05.png)

1. 单击&#x200B;**[!UICONTROL Synchronizing enumerations...]**&#x200B;链接以开始在Adobe Campaign和Microsoft Dynamics之间同步枚举。

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign和Microsoft Dynamics现已连接。 您可以设置两个系统之间的数据同步。 在[数据同步](../../platform/using/crm-data-sync.md)部分了解详情。

>[!NOTE]
>
> 您需要确保将两个URL（服务器URL和服务器配置中的`login.microsoftonline.com`）添加到允许列表中。 有关如何配置URL权限的详细信息，请参阅此[页面](../../installation/using/url-permissions.md)。

## 支持的字段数据类型 {#ms-dyn-supported-types}

对于Microsoft Dynamics 365，下面列出了支持/不支持的属性类型：


| 属性类型 | 支持 |
| --------------------------------------------------------------------------------- | --------- |
| 基本类型：boolean、datetime、decimal、float、double、integer、bigint、string | 是 |
| 货币（双精度浮点数） | 是 |
| memo， entityname， primarykey， uniqueidentifier（作为字符串） | 是 |
| 状态、选取列表（我们以枚举形式存储可能的值）、状态（字符串） | 是 |
| 所有者（字符串） | 是 |
| 查找（仅单个实体引用查找） | 是 |
| 客户 | 否 |
| 相关 | 否 |
| PartyList | 否 |
| 托管属性 | 否 |
| 多选选项集 | 否 |
