---
product: campaign
title: 更新到新的可投放性服务器
description: 了解如何更新到新的Campaign可投放性服务器
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: c42d4022587846081442a39d03546c0ef335c7a0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 更新到新的可投放性服务器 {#acc-deliverability}

从[v7.2.2版本](../../rn/using/latest-release.md#release-7-2-2)开始，Adobe Campaign依赖新的可投放性服务器，该服务器可提供高可用性并解决安全性合规性问题。 Campaign Classic现在会将与之间的可投放性规则、broadlog和禁止地址同步到新的可投放性服务器。 旧的可交付性服务器将于2022年8月31日停用。

作为Campaign Classic客户，您必须在2022年8月31日之前实施新的可投放性服务器&#x200B;**&#x200B;**。

>[!NOTE]
>
>有关这些更改的更多问题，请参阅[常见问题解答](#faq)，或联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}。
>

## 更改了哪些内容？{#acc-deliverability-changes}

出于安全合规性的原因，Adobe正在停用旧的数据中心。 Adobe Campaign Classic客户端需要迁移到新的可投放性服务，该服务托管在Amazon Web服务(AWS)上。

此新服务器可确保高可用性(99.9)&#x200B;，并提供安全且经过身份验证的端点，以使Campaign服务器能够提取所需的数据：新的可投放性服务器不会为每个请求连接到数据库，而是会缓存数据以尽可能为请求提供服务。 此机制提高了响应时间&#x200B;。

## 您是否受影响？{#acc-deliverability-impacts}

所有客户都受到影响，必须升级到[Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2)（或更高版本），并实施其环境以从新的可投放性服务器中获益。

## 如何更新？{#acc-deliverability-update}

作为&#x200B;**托管客户**，Adobe将与您合作，将您的实例升级到新版本，并在Adobe Developer Console中创建项目。

作为&#x200B;**内部部署/混合部署客户**，您需要升级到[Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2)（或更多）以从新的可投放性服务器中获益。 升级所有实例后，您必须[实施新的集成](#implementation-steps)以Adobe可投放性服务器，并确保无缝过渡。

## 实施步骤 {#implementation-steps}

>[!WARNING]
>
>这些步骤只应针对混合和内部部署实施执行。

作为新的可投放性服务器集成的一部分，Campaign需要通过基于Identity Management Service (IMS)的身份验证与AdobeShared Services进行通信。 首选方式是使用基于Adobe Developer的网关令牌(也称为技术帐户令牌或AdobeIO JWT)。

>[!AVAILABILITY]
>
> Adobe已弃用服务帐户(JWT)凭据，Campaign与Adobe解决方案和应用程序的集成现在必须依赖OAuth服务器到服务器凭据。 </br>
>
> * 如果您已实施与Campaign的入站集成，则必须迁移技术帐户，如[本文档](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank)中所述。 现有的[服务帐户(JWT)凭据](../../integrations/using/oauth-technical-account.md)将继续工作到2025年1月27日。</br>
>
> * 如果您实施了叫客集成，如Campaign-Analytics集成或Experience Cloud Triggers集成，则在2025年1月27日之前它们将继续工作。 但是，在该日期之前，您必须将Campaign环境升级到v7.4.1，并将技术帐户迁移到oAuth。

### 先决条件{#prerequisites}

在开始实施之前，请检查实例配置。

1. 打开Campaign客户端控制台，并以管理员身份登录到Adobe Campaign。
1. 浏览到&#x200B;**管理>平台>选项**。
1. 检查是否已填写`DmRendering_cuid`选项值。

   * 如果填写了选项，则可以开始实施。
   * 如果未填写任何值，请联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}以获取您的CUID。

   必须在您的所有Campaign实例(MKT、MID、RT、EXEC)上使用正确的值填充此选项。 作为混合型客户，请联系Adobe以在MID、RT和EXEC实例上设置选项。

作为内部部署客户，您还必须检查营销活动&#x200B;**[!UICONTROL Product profile]**&#x200B;是否可用于您的组织。 要执行此操作，请按照以下步骤进行：

1. 作为管理员，连接到[Adobe Admin Console](https://adminconsole.adobe.com/){_blank}。
1. 访问&#x200B;**产品和服务**&#x200B;部分，并检查&#x200B;**Adobe Campaign**&#x200B;是否已列出。
如果您看不到&#x200B;**Adobe Campaign**，请联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}添加该产品。
1. 单击&#x200B;**Adobe Campaign**&#x200B;并选择您的组织。
   **警告**：如果您有多个组织，请确保选择正确的组织。 在此页面[&#128279;](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}中了解有关组织的更多信息。

1. 检查&#x200B;**[!UICONTROL Product profile]**&#x200B;是否存在。 如果没有，请创建它。 此&#x200B;**[!UICONTROL Product profile]**&#x200B;不需要权限。


>[!CAUTION]
>
>列入允许列表作为内部部署客户，如果在您的一侧实施了防火墙，则必须将此url `https://deliverability-service.adobe.io`添加到您的。 [了解详情](../../installation/using/url-permissions.md)。


### 步骤1：创建/更新您的Adobe Developer项目 {#adobe-io-project}

要继续配置Adobe Analytics连接器，请访问Adobe Developer控制台并创建您的OAuth服务器到服务器项目。

有关详细信息，请参阅[此页面](../../integrations/using/oauth-technical-account.md#oauth-service)。

### 步骤2：在Adobe Campaign中添加项目凭据 {#add-credentials-campaign}

按照[此页面](../../integrations/using/oauth-technical-account.md#add-credentials)中详述的步骤进行操作，以在Adobe Campaign中添加您的OAuth项目凭据。

### 步骤3：验证配置

要检查集成是否成功，请执行以下步骤：

1. 打开客户端控制台并登录到Adobe Campaign。
1. 浏览到&#x200B;**管理>生产>技术工作流**。
1. 重新启动&#x200B;**可投放性刷新** (deliverabilityUpdate)工作流。 这应在您的所有Campaign实例(MKT、MID、RT、EXEC)上执行。 作为混合型客户，请联系Adobe以在MID、RT和EXEC实例上重新启动工作流。
1. 检查日志：工作流应在没有错误的情况下执行。

>[!CAUTION]
>
>更新后，必须停止收件箱呈现(updateRenderingSeeds)**的**&#x200B;更新种子网络，因为它将不再应用，并将失败。

## 常见问题解答 {#faq}

### 更新的时间线是什么？

从2022年7月起，托管客户将开始过渡到新的可投放性服务器(Campaign Managed Services)，届时将添加这些改进的功能并增强安全性。 所有托管客户都将在8月底之前更新。

内部部署和混合型客户必须在相同的时间范围内进行过渡。

### 如果不升级环境会发生什么情况？

任何未在8月31日之前升级的Campaign实例都将无法再连接到Campaign可投放性服务器。 因此，**可投放性刷新** (deliverabilityUpdate)工作流将失败，这将影响您的可投放性。

如果不升级环境，则将停止同步电子邮件设置（ MX管理规则、入站电子邮件规则、域管理规则和退回鉴别规则）。 这可能会随着时间的推移影响您的可投放性。 如果对这些规则进行了重大更改，则必须从此刻手动应用这些规则。

对于MKT实例，只有[全局禁止显示列表](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules)受到影响。
