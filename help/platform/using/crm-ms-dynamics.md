---
solution: Campaign Classic
product: campaign
title: 活动- Microsoft Dynamics CRM连接器
description: Connect 活动和Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
translation-type: tm+mt
source-git-commit: 37802e52f1d1d38d9c3d59c439f23114a594bfef
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Connect 活动和Microsoft Dynamics 365{#connect-to-msdyn}

在本页中，您将学习如何将Campaign Classic连接到&#x200B;**Microsoft Dynamics CRM 365**。

可能的部署包括：

* （建议）。 ****&#x200B;请参阅[下面的部分](#microsoft-dynamics-implementation-step)，了解设置与Microsoft Dynamics连接的步骤。
* **Office 365**。 请参阅[此视频](#microsoft-dynamics-office-365)以了解设置此集成的关键步骤。
* 对于&#x200B;**内部部署**&#x200B;部署，请应用Office 365关键步骤。

通过专用工作流活动进行数据同步。 [了解详情](../../platform/using/crm-data-sync.md)。

## 实施步骤{#microsoft-dynamics-implementation-steps}

要连接Microsoft Dynamics 365以通过&#x200B;**Web API**&#x200B;与Adobe Campaign配合使用，您需要应用以下步骤：

在Microsoft Dynamics CRM中：
1. 获取Microsoft Dynamics客户端ID
1. 生成Microsoft Dynamics客户端机密
1. 配置权限
1. 创建应用程序用户
1. 对私钥进行编码

[在本节中了解更多信息](#config-crm-microsoft)

Campaign Classic:
1. 创建新外部帐户
1. 使用Microsoft Dynamics设置配置外部帐户
1. 使用配置向导映射表和同步明细列表
1. 创建同步工作流

[在本节中了解更多信息](#configure-acc-for-microsoft)


>[!CAUTION]
> 将Adobe Campaign与Microsoft Dynamics连接时，您无法：
> * 安装可以更改CRM行为并导致与Adobe Campaign兼容的插件
> * 选择多个明细列表

>



## 配置Microsoft Dynamics CRM {#config-crm-microsoft}

要生成访问令牌和用于设置帐户的密钥，您需要使用&#x200B;**全局管理员**&#x200B;凭据登录[Microsoft Azure Directory](https://portal.azure.com)。 然后，按照以下概述的步骤操作。

### 获取Microsoft Dynamics客户端ID {#get-client-id-microsoft}

要获取客户端ID，您需要在Azure Active Directory中注册应用程序。 客户端ID与应用程序 ID相同。

1. 导航到&#x200B;**Azure Active Directory > App Registrations**，然后单击&#x200B;**New Application Registration**。
1. 请指定一个可帮助标识实例的唯一名称，如&#x200B;**adobecampaign`<instance identifier>`**。
1. 选择&#x200B;**应用程序类型**&#x200B;作为&#x200B;**Web应用程序/ API**。
1. 对&#x200B;**登录URL**&#x200B;使用`http://localhost`。

保存后，您会得到一个&#x200B;**应用程序 ID**，它是活动的客户端标识符。

请阅读[本页](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)了解更多信息。

### 生成Microsoft Dynamics客户端密码{#config-client-secret-microsoft}

客户端密钥是客户端ID唯一的密钥。 要获取证书密钥标识符，请执行以下步骤：

1. 导航到&#x200B;**Azure Active Directory > App Registrations**&#x200B;并选择之前创建的应用程序。
1. 单击&#x200B;**证书和密钥**。
1. 单击&#x200B;**上载证书**，然后浏览并上载生成的公共证书。
1. 要生成证书，您可以使用openssl。

   例如：

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. 单击&#x200B;**manifest**&#x200B;链接可获取&#x200B;**证书密钥标识符**&#x200B;和&#x200B;**密钥ID**。

### 配置权限{#config-permissions-microsoft}

您需要为已创建的应用程序配置&#x200B;**所需权限**。

1. 导航到&#x200B;**Azure Active Directory > App Registrations**&#x200B;并选择之前创建的应用程序。
1. 单击左上角的&#x200B;**设置**。
1. 在&#x200B;**所需权限**&#x200B;上，单击&#x200B;**添加**&#x200B;和&#x200B;**选择API > Dynamics CRM联机**。
1. 然后，单击&#x200B;**选择**，启用&#x200B;**作为组织用户访问Dynamics 365复选框，然后单击**&#x200B;选择&#x200B;**。**

### 创建应用程序用户{#create-app-user-microsoft}

应用程序用户是上述注册的应用程序将使用的用户。 使用上述注册的应用程序对Microsoft Dynamics所做的任何更改都将通过此用户完成。

**第1步**:在azure active directory上创建非交互式用户

1. 单击&#x200B;**Azure Active Directory > Users** ，然后单击&#x200B;**New User**。
1. 请提供要使用的正确名称，用户名应为电子邮件格式。
1. 在&#x200B;**目录角色**&#x200B;中选择&#x200B;**Dynamics 365 Administrator**。

**第2步**:为创建的用户分配适当的许可证

1. 从[Microsoft Azure](https://portal.azure.com)中，单击&#x200B;**管理应用程序**。
1. 转到&#x200B;**“用户”>“活动用户”**&#x200B;并单击新创建的用户。
1. 单击&#x200B;**编辑产品许可证**，然后选择&#x200B;**Dynamics 365客户参与计划**。
1. 单击&#x200B;**关闭**。

**第3步**:在Dynamics CRM上创建应用程序用户

1. 从[Microsoft Azure](https://portal.azure.com)，导航到&#x200B;**设置>安全>用户**。
1. 单击下拉框，选择&#x200B;**应用程序用户**，然后单击&#x200B;**新建**。
1. 使用与以上活动目录上创建的用户相同的用户名

   >[!NOTE]
   >
   >使用同一名称会引发重复键错误，因此，在获得是否需要此步骤的确认之前，请使用其他用户名并继续。

1. 为[您之前创建的](#get-client-id-microsoft)应用程序分配&#x200B;**应用程序 ID**。
1. 单击&#x200B;**管理角色**，然后为用户选择&#x200B;**系统管理员**&#x200B;角色。

## 配置活动{#configure-acc-for-microsoft}

要连接Microsoft Dynamics 365和活动，您需要在活动中创建并配置专用外部帐户。

1. 导航到&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。

1. 创建新外部帐户，选择类型&#x200B;**[!UICONTROL Microsoft Dynamics CRM]**&#x200B;和&#x200B;**[!UICONTROL Enable]**&#x200B;选项。

1. 选择&#x200B;**[!UICONTROL Web API]**&#x200B;部署类型：

   Adobe Campaign Classic支持Dynamics 365 REST接口，OAuth协议用于使用&#x200B;**[!UICONTROL Certificate]**&#x200B;或&#x200B;**[!UICONTROL Password Credentials]**&#x200B;进行身份验证。

   使用Azure目录中之前定义的设置[](#get-client-id-microsoft)配置外部帐户。

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >本节](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)中详细介绍了Microsoft Dynamics CRM外部帐户配置。[

1. 单击&#x200B;**[!UICONTROL Microsoft CRM configuration wizard...]**&#x200B;链接：Adobe Campaign会自动检测Microsoft Dynamics数据模板中的表。

   ![](assets/crm_connectors_msdynamics_02.png)

1. 选择要恢复的表。

   ![](assets/crm_connectors_msdynamics_03.png)

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;以开始创建相应的模式。

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >要批准配置，您必须断开/重新连接到Adobe Campaign控制台。

   您可以检查匹配的模式是否在Adobe Campaign中可用。

   ![](assets/crm_connectors_msdynamics_05.png)

1. 单击&#x200B;**[!UICONTROL Synchronizing enumerations...]**&#x200B;链接以开始同步Adobe Campaign和Microsoft Dynamics之间的明细列表。

   ![](assets/crm_connectors_msdynamics_06.png)

活动和Microsoft Dynamics现已连接。 可以在两个系统之间设置数据同步。 在[数据同步](../../platform/using/crm-data-sync.md)部分了解更多信息。

## 配置Microsoft Dynamics CRM Office 365集成{#microsoft-dynamics-office-365}

观看此视频，了解如何在Office 365部署环境中将Dynamics 365与Adobe Campaign Classic集成。

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)


## 支持的字段数据类型{#ms-dyn-supported-types}

对于Microsoft Dynamics 365，以下列出了支持/不支持的属性类型：


| 属性类型 | 支持 |
| --------------------------------------------------------------------------------- | --------- |
| 基本类型：boolean、datetime、decimal、float、多次、integer、bigint、string | 是 |
| 货币(作为多次) | 是 |
| memo、entityname、primarykey、uniqueidentifier（作为字符串） | 是 |
| 状态、选择列表(我们将可能的值存储在明细列表中)、状态（字符串） | 是 |
| owner（作为字符串） | 是 |
| 查找（仅单个实体引用查找） | 是 |
| 客户 | 否 |
| 关于 | 否 |
| PartyList | 否 |
| ManagedProperty | 否 |
