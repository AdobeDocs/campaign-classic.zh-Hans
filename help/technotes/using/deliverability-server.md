---
product: campaign
title: 更新到新的可投放性服务器
description: 了解如何更新到新的Campaign可投放性服务器
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 1%

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

>[!WARNING]
>
>这些步骤只应针对混合和内部部署实施执行。

作为新的可投放性服务器集成的一部分，Campaign需要通过基于Identity Management Service (IMS)的身份验证与AdobeShared Services进行通信。 首选方式是使用基于Adobe Developer的网关令牌(也称为技术帐户令牌或AdobeIO JWT)。

>[!AVAILABILITY]
>
> Adobe已弃用服务帐户(JWT)凭据，Campaign与Adobe解决方案和应用程序的集成现在必须依赖OAuth服务器到服务器凭据。 </br>
>
> * 如果您已实施与Campaign的入站集成，则必须迁移技术帐户，如中所述 [本文档](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). 现有服务账户(JWT)凭证将继续使用至2025年1月27日。 </br>
>
> * 如果您实施了叫客集成，如Campaign-Analytics集成或Experience Cloud Triggers集成，则在2025年1月27日之前它们将继续工作。 但是，在该日期之前，您必须将Campaign环境升级到v7.4.1，并将技术帐户迁移到oAuth。

### 先决条件{#prerequisites}

在开始实施之前，请检查实例配置。

1. 打开Campaign客户端控制台，并以管理员身份登录到Adobe Campaign。
1. 浏览至 **管理>平台>选项**.
1. 检查 `DmRendering_cuid` 填充选项值。

   * 如果填写了选项，则可以开始实施。
   * 如果未填写任何值，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} 去拿你的小女友。

   必须在您的所有Campaign实例(MKT、MID、RT、EXEC)上使用正确的值填充此选项。 作为混合型客户，请联系Adobe以在MID、RT和EXEC实例上设置选项。

作为内部部署客户，您还必须检查Campaign **[!UICONTROL Product profile]** 适用于您的组织。 要执行此操作，请按照以下步骤进行：

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

要继续配置Adobe Analytics连接器，请访问Adobe Developer控制台并创建您的OAuth服务器到服务器项目。

请参阅 [此页面](../../integrations/using/oauth-technical-account.md#oauth-service) 以了解详细文档。

### 步骤2：在Adobe Campaign中添加项目凭据 {#add-credentials-campaign}

请按照中详述的步骤操作 [此页面](../../integrations/using/oauth-technical-account.md#add-credentials) 以在Adobe Campaign中添加您的OAuth项目凭据。

### 步骤3：验证配置

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
