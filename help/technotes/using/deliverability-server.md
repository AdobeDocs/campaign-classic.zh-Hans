---
product: campaign
title: 更新到新的可投放性服务器
description: 了解如何更新到新的Campaign可投放性服务器
feature: Technote, Deliverability
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 3%

---

# 更新到新的可投放性服务器 {#acc-deliverability}

正在启动 [v7.2.2发布](../../rn/using/latest-release.md#release-7-2-2)， Adobe Campaign依赖于新的可投放性服务器，该服务器可提供高可用性并解决安全合规性问题。 Campaign Classic现在会将与之间的可投放性规则、broadlog和禁止地址同步到新的可投放性服务器。 旧的可交付性服务器将于2022年8月31日停用。

作为Campaign Classic客户，您必须实施新的可投放性服务器 **2022年8月31日之前**.

>[!NOTE]
>
>有关这些更改的更多问题，请参阅 [常见问题解答](#faq)，或联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.
>

## 更改了哪些内容？{#acc-deliverability-changes}

出于安全合规性的原因，Adobe正在停用旧的数据中心。 Adobe Campaign Classic客户端需要迁移到新的可投放性服务，该服务托管在Amazon Web服务(AWS)上。

此新服务器可确保高可用性(99.9)&#x200B;，并提供安全且经过身份验证的端点，以使Campaign服务器能够提取所需的数据：新的可投放性服务器不会为每个请求连接到数据库，而是会缓存数据以尽可能为请求提供服务。 此机制提高了响应时间&#x200B;。

## 您是否受影响？{#acc-deliverability-impacts}

所有客户都受到影响，必须升级到 [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) 并实施其环境以从新的可投放性服务器中受益。

## 如何更新？{#acc-deliverability-update}

作为 **托管客户**，Adobe将帮助您将实例升级到新版本，并在Adobe Developer控制台中创建项目。

作为 **内部部署/混合部署客户**，您需要升级到 [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) （或更多）以从新的可投放性服务器中受益。 升级所有实例后，您必须 [实施新的集成](#implementation-steps) Adobe可投放性服务器，并确保无缝过渡。

## 实施步骤 {#implementation-steps}

作为新的可投放性服务器集成的一部分，Campaign需要通过基于Identity Management Service (IMS)的身份验证与AdobeShared Services进行通信。 首选方式是使用基于Adobe Developer的网关令牌(也称为技术帐户令牌或AdobeIO JWT)。

>[!WARNING]
>
>这些步骤只应针对混合和内部部署实施执行。
>

### 先决条件{#prerequisites}

在开始实施之前，请检查实例配置。

1. 打开Campaign客户端控制台，并以管理员身份登录到Adobe Campaign。
1. 浏览至 **管理>平台>选项**.
1. 检查 `DmRendering_cuid` 填充选项值。

   * 如果填写了选项，则可以开始实施。
   * 如果未填写任何值，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} 去拿你的小女友。

   必须在您的所有Campaign实例(MKT、MID、RT、EXEC)上使用正确的值填充此选项。 作为混合型客户，请联系Adobe以在MID、RT和EXEC实例上设置选项。

作为内部部署客户，您还必须检查Campaign **[!UICONTROL Product profile]** 适用于您的组织。 要执行此操作，请执行以下步骤：

1. 作为管理员，连接到 [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. 访问 **产品和服务** 部分和检查 **Adobe Campaign** 列出。
如果您看不到 **Adobe Campaign** 联系人 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} 才能添加它。
1. 单击 **Adobe Campaign** 并选择您的组织。
   **注意**：如果您有多个组织，请确保选择正确的组织。 了解有关组织的更多信息 [本页内容](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.

1. 检查 **[!UICONTROL Product profile]** 已存在。 如果没有，请创建它。 无需权限 **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>作为内部部署客户，如果在您这边实施了防火墙，则必须添加此URL `https://deliverability-service.adobe.io` 敬你的允许列表。 [了解详情](../../installation/using/url-permissions.md)。


### 步骤1：创建/更新您的Adobe Developer项目 {#adobe-io-project}

1. 访问 [Adobe Developer控制台](https://developer.adobe.com/console/home) 并使用贵组织的开发人员访问权限登录。 确保您已登录到正确的组织门户。
   **注意**：如果您有多个组织，请确保选择正确的组织。 了解有关组织的更多信息 [本页内容](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.
1. 选择 **[!UICONTROL Create new project]**。
   ![](assets/New-Project.png)

   >[!CAUTION]
   >
   >如果您已在将AdobeIO JWT身份验证功能用于其他集成，例如Analytics连接器或Adobe触发器，则必须通过添加以下内容来更新项目 **Campaign API** 加入那个项目。

1. 选择 **[!UICONTROL Add API]**.
   ![](assets/Add-API.png)
1. 在 **[!UICONTROL Add an API]** 窗口，选择 **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. 如果您的客户端ID为空，请选择 **[!UICONTROL Generate a key pair]** 创建公钥和私钥对。
   ![](assets/Generate-a-key-pair.png)

   随后，这些密钥将自动下载，默认到期日期为365天。 过期后，您将需要创建新密钥对并在配置文件中更新集成。 利用选项2，您可以选择手动创建和上传 **[!UICONTROL Public key]** 到期日期更长的。
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >您应该保存 `config.zip` 文件下载提示出现，因为您将无法再次下载。

1. 单击 **[!UICONTROL Next]**。
1. 选择任何现有的 **[!UICONTROL Product profile]** 或根据需要创建一个新版本。 无需权限 **[!UICONTROL Product profile]**. 有关的详细信息 **[!UICONTROL Product Profiles]**，请参阅 [此页面](https://helpx.adobe.com/enterprise/using/manage-developers.html){_blank}.
   ![](assets/Product-Profile-API.png)

   然后，单击 **[!UICONTROL Save configured API]**.

1. 从项目中，选择 **[!UICONTROL Adobe Campaign]** 并将以下信息复制到 **[!UICONTROL Service Account (JWT)]**

   ![](assets/Config-API.png)

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>Adobe Developer证书将在12个月后过期。 您需要每年生成一个新的密钥对。

### 步骤2：在Adobe Campaign中添加项目凭据 {#add-credentials-campaign}

私钥应采用base64 UTF-8格式编码。

为实现此操作，请执行以下步骤：

1. 使用上述步骤中生成的私钥。
1. 使用以下命令对私钥进行编码： `base64 ./private.key > private.key.base64`. 这会将base64内容保存到新文件中 `private.key.base64`.

   >[!NOTE]
   >
   >复制/粘贴私钥时，有时可以自动添加额外的行。 在编码私钥之前，请记得删除它。

1. 复制文件中的内容 `private.key.base64`.
1. 通过SSH登录到安装了Adobe Campaign实例的每个容器，并通过运行以下命令（如下所示）在Adobe Campaign中添加项目凭据 `neolane` 用户。 这将插入 **[!UICONTROL Technical Account]** 实例配置文件中的凭据。

   ```sql
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. 您必须停止然后重新启动服务器，以便考虑修改。 您还可以运行 `config -reload` 命令。

### 步骤3：启用新的可投放性服务器

您现在可以启用新的可投放性服务器。 要执行此操作，请执行以下操作：

1. 打开客户端控制台，并以管理员身份登录到Adobe Campaign。
1. 浏览至 **管理>平台>选项**.
1. 访问 `NewDeliverabilityServer_FeatureFlag` 选项并将值设置为 `1`. 此配置应在您的所有Campaign实例(MKT、MID、RT、EXEC)上执行。 作为混合型客户，请联系Adobe以在MID、RT和EXEC实例上设置选项。

### 步骤4：验证配置

要检查集成是否成功，请执行以下步骤：

1. 打开客户端控制台并登录到Adobe Campaign。
1. 浏览至 **管理>生产>技术工作流**.
1. 重新启动 **刷新可投放性** (deliverabilityUpdate)工作流。 这应在您的所有Campaign实例(MKT、MID、RT、EXEC)上执行。 作为混合型客户，请联系Adobe以在MID、RT和EXEC实例上重新启动工作流。
1. 检查日志：工作流应在没有错误的情况下执行。

>[!CAUTION]
>
>更新后， **更新收件箱渲染的种子网络(updateRenderingSeeds)** 工作流必须停止，因为它将不再应用并将失败。

## 常见问题解答 {#faq}

### 更新的时间线是什么？

从2022年7月起，托管客户将开始过渡到新的可投放性服务器(Campaign Managed Services)，届时将添加这些改进的功能并增强安全性。 所有托管客户都将在8月底之前更新。

内部部署和混合型客户必须在相同的时间范围内进行过渡。

### 如果不升级环境会发生什么情况？

任何未在8月31日之前升级的Campaign实例都将无法再连接到Campaign可投放性服务器。 因此， **刷新可投放性** (deliverabilityUpdate)工作流将失败，这将影响您的可投放性。

如果不升级环境，则将停止同步电子邮件设置（ MX管理规则、入站电子邮件规则、域管理规则和退回鉴别规则）。 这可能会随着时间的推移影响您的可投放性。 如果对这些规则进行了重大更改，则必须从此刻手动应用这些规则。

仅对于MKT实例 [全局禁止显示列表](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) 受影响。
