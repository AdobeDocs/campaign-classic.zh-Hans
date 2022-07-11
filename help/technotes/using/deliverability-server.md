---
product: campaign
title: 迁移到新的可投放性服务器
description: 了解如何实施Campaign可投放性服务器
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: c3b1ffcb580c7510a64115e0abbf16cb766146c5
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 3%

---

# Campaign可投放性服务器 {#acc-deliverability}

从Campaign Classicv7 21.1版本开始，Adobe Campaign提出了新的可交付性服务器，该服务器可提供高可用性并解决安全合规性问题。 Campaign Classic现在可将投放能力规则、广播和禁止地址从和同步到新的投放能力服务器。

作为Campaign Classic客户，您必须实施新的可投放性服务器 **2022年8月31日之前**.

>[!NOTE]
>
>如果对这些更改有任何疑问，请参阅 [常见问题解答](#faq)，或联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 更改了哪些内容？{#acc-deliverability-changes}

Adobe正在停用较旧的数据中心，这是出于安全合规性的原因。 Adobe Campaign Classic客户需要迁移到托管在Amazon Web Service(AWS)上的新可交付性服务。

此新服务器可保证高可用性(99.9)，并&#x200B;提供安全且经过验证的端点，以使Campaign服务器能够获取所需数据：新的可交付性服务器不会针对每个请求连接到数据库，而是缓存数据以尽可能提供请求。 此机制可缩短响应时间&#x200B;。

## 您是否受影响？{#acc-deliverability-impacts}

如果您的环境是在低于 [Campaign v7.2.1](../../rn/using/latest-release.md#release-7-2-2)，则会受到影响。 您需要升级到Campaign v7.2.1（或更高版本）。

了解如何检查您的版本 [在此部分中](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## 如何更新？{#acc-deliverability-update}

As a **托管客户**,Adobe将与您合作，将您的实例升级到较新版本，并在Adobe Developer控制台中创建项目。

作为 **内部部署/混合客户**，您需要升级到其中一个较新版本，才能从新的可投放性服务器中受益。 升级所有实例后，您将能够 [实施新集成](#implementation-steps) Adobe投放能力服务器，并确保无缝过渡。

## 实施步骤 {#implementation-steps}

作为新可投放性服务器集成的一部分，Campaign需要通过基于Identity Management服务(IMS)的身份验证与Adobe共享服务进行通信。 首选方法是使用基于Adobe Developer的网关令牌(也称为技术帐户令牌或AdobeIO JWT)。


>[!WARNING]
>
>这些步骤只应由混合实施和内部部署实施执行。

### 先决条件{#prerequisites}

在开始实施之前，请检查您的实例配置。

1. 打开Campaign客户端控制台，以管理员身份登录Adobe Campaign。
1. 浏览到 **管理>平台>选项**.
1. 检查 `DmRendering_cuid` 选项值。

   * 如果填充了选项，则可以开始实施。
   * 如果未填写值，请联系 [Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 来获取你的CUID。

      必须在具有相同值的所有Campaign实例(MKT、MID、RT、EXEC)上填充此选项。

### 步骤1:创建/更新Adobe Developer项目 {#adobe-io-project}

1. 访问 [Adobe Developer控制台](https://developer.adobe.com/console/home) 并使用贵组织的开发人员访问权限登录。

   >[!NOTE]
   >
   > 确保您已登录到正确的组织门户。

1. 选择 **[!UICONTROL Create new project]**。
   ![](assets/New-Project.png)


   >[!CAUTION]
   >
   >如果您已经为其他集成(如Analytics连接器或Adobe触发器)使用AdobeIO JWT身份验证功能，则必须通过添加 **Campaign API** 到那个项目。

1. 选择 **[!UICONTROL Add API]**.
   ![](assets/Add-API.png)
1. 在 **[!UICONTROL Add an API]** 窗口，选择 **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. 如果您的客户端ID为空，请选择 **[!UICONTROL Generate a key pair]** 创建公钥和私钥对。
   ![](assets/Generate-a-key-pair.png)

   然后，将自动下载密钥，默认到期日期为365天。 过期后，您将需要创建新密钥对并更新配置文件中的集成。 使用选项2，您可以选择手动创建和上传 **[!UICONTROL Public key]** 的期限。
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >您应该保存 `config.zip` 文件，因为您将无法再次下载它。

1. 单击 **[!UICONTROL Next]**。
1. 选择任何现有 **[!UICONTROL Product profile]** 或根据需要创建新受众。 无需权限 **[!UICONTROL Product profile]**. 有关 **[!UICONTROL Product Profiles]**，请参阅 [本页](https://helpx.adobe.com/enterprise/using/manage-developers.html).
   ![](assets/Product-Profile-API.png)

   然后，单击 **[!UICONTROL Save configured API]**.

1. 在您的项目中，选择 **[!UICONTROL Adobe Campaign]** 并在 **[!UICONTROL Service Account (JWT)]**

   ![](assets/Config-API.png)

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>Adobe Developer证书将在12个月后过期。 您每年需要生成一个新的密钥对。

### 步骤2:在Adobe Campaign中添加项目凭据 {#add-credentials-campaign}

私钥应以base64 UTF-8格式进行编码。

为实现此操作，请执行以下步骤：

1. 使用在上述步骤中生成的私钥。
1. 使用以下命令对私钥进行编码： `base64 ./private.key > private.key.base64`. 这会将base64内容保存到新文件 `private.key.base64`.

   >[!NOTE]
   >
   >有时，在复制/粘贴私钥时，会自动添加额外的行。 在对私钥进行编码之前，请记得将其删除。

1. 从文件复制内容 `private.key.base64`.
1. 通过SSH登录到安装了Adobe Campaign实例的每个容器，并通过以下命令(如 `neolane` 用户。 这将插入 **[!UICONTROL Technical Account]** 实例配置文件中的凭据。

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. 您必须停止并重新启动服务器才能考虑修改。 您还可以运行 `config -reload` 命令。

### 步骤3:启用新的可投放性服务器

您现在可以启用新的可投放性服务器。 要执行此操作，请执行以下操作：

1. 打开客户端控制台，以管理员身份登录Adobe Campaign。
1. 浏览到 **管理>平台>选项**.
1. 访问 `NewDeliverabilityServer_FeatureFlag` 选项，并将值设置为 `1`. 此配置应在您的所有Campaign实例(MKT、MID、RT、EXEC)上执行。

### 步骤4:验证配置

要检查集成是否成功，请执行以下步骤：


1. 打开客户端控制台并登录到Adobe Campaign。
1. 浏览到 **管理>生产>技术工作流**.
1. 重新启动 **可投放性更新** (deliverabilityUpdate)工作流。 此操作应在您的所有Campaign实例(MKT、MID、RT、EXEC)上执行。
1. 检查日志：工作流应在执行时不出错。


## 常见问题解答 {#faq}

### 如果我不升级环境，会发生什么情况？

任何在8月31日之前未升级的Campaign实例将无法再连接Campaign可投放性服务器。 因此， **可投放性更新** (deliverabilityUpdate)工作流将失败。 此工作流管理MX规则和跳出规则的每日更新。

如果您不升级环境，电子邮件设置将停止同步（MX管理规则、入站电子邮件规则、域管理规则和退回鉴别规则）。 这可能会随着时间的推移而影响您的投放能力。 如果对这些规则进行了重大更改，则必须从此时起手动应用这些规则。

仅对于MKT实例 [全局抑制列表](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) 会受到影响。

### 我现在无法升级。 指导是什么？

如果您在8月31日之前无法升级实例，则必须临时禁用 **可投放性更新** （可交付性更新）工作流程，直到升级完成，以便它不会尝试与旧可交付性服务器同步。



如需更多指导，请联系 [Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
