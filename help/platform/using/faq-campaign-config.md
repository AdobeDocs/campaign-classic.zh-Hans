---
product: campaign
title: Campaign 设置常见问题解答
description: Campaign Classic 常见问题解答
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 50bed489-2a0f-4123-a326-3d68c8295662
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 92%

---

# Campaign 设置常见问题解答 {#settings-faq}



了解根据您的需求设置 Campaign 实例的主要配置工作。

## 我能改变 Campaign 界面的语言吗？ {#can-i-change-the-language-of-campaign-interface-}

创建实例时可选择 Campaign 语言。之后将无法改变语言设置。如需详细信息，请参阅[此部分](../../installation/using/creating-an-instance-and-logging-on.md)。

Adobe Campaign 目前提供英语、法语、德语和日语共 4 种语言的用户界面。请注意，客户端控制台和服务器必须使用相同的语言设置。每个 Campaign 实例只能以一种语言运行。

如果是英语，在安装 Campaign 时可以选择美式英语还是英式英语：二者的日期和时间格式有所不同。如需有关这些差别的详细信息，请参阅[此部分](../../platform/using/adobe-campaign-workspace.md#date-and-time)。

## 我可以将 Campaign Classic 与其他 Adobe 解决方案结合使用吗？ {#can-i-use-campaign-classic-with-other-adobe-solutions-}

您可以将 Adobe Campaign 的投放功能和高级活动管理功能与帮助您个性化用户体验的解决方案结合起来。

单击此处了解[如何使用其他 Adobe 解决方案](../../integrations/using/about-campaign-integrations.md)和[如何在 Campaign 中设置 IMS](../../integrations/using/about-adobe-id.md)。

## 如何在 Campaign 实例上设置跟踪功能？ {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

作为专家级用户，您可以在 Campaign 实例上配置跟踪功能。

[单击此处了解更多信息](../../installation/using/deploying-an-instance.md#tracking-configuration)。

## 如何配置电子邮件投放能力? {#how-to-configure-email-deliverability-}

除 [Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans)，阅读可投放性技术建议，了解如何配置实例以最大限度地提升Campaign投放能力。

[单击此处了解更多信息](../../delivery/using/about-deliverability.md)。

## 如何实施内容批准？ {#how-can-i-implement-content-approval-}

借助 Campaign，您能够以协作模式为营销活动的主要步骤设置审批流程。对于每个活动，您可以批准投放目标、内容和成本。负责审批的Adobe Campaign运营商可以通过电子邮件通知，并可以通过控制台或Web连接接受或拒绝审批。

[单击此处了解更多信息](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)，并了解如何在 Campaign 中实施投放内容的批准工作。

## 如何访问存储在外部数据库中的数据？ {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign 提供了联合数据访问 (FDA) 选项，以处理存储在一个或多个外部数据库中的信息：无需改变 Adobe Campaign 数据的结构就可以访问外部数据。

[单击此处了解更多信息](../../installation/using/connecting-to-database.md)。

## 我能将 Campaign 连接到哪些外部数据库？ {#which-external-databases-can-i-connect-campaign-to-}

[兼容性表](../../rn/using/compatibility-matrix.md)中列出了通过联合数据访问 (FDA) 与 Campaign 兼容的外部数据库。

## Adobe Campaign 可与轻型目录访问协议 (LDAP) 相集成吗？ {#can-adobe-campaign-integrate-with-ldap-}

作为内部部署/混合部署客户，您可以将 Campaign Classic 与 LDAP 目录相集成。

[单击此处了解如何操作](../../installation/using/connecting-through-ldap.md)。

## 如何在 Campaign 中设置 CRM 连接器？ {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign 提供各种 CRM 连接器，可将您的 Adobe Campaign 平台链接到第三方系统。通过这些 CRM 连接器，您可以同步处理联系人、帐户、购买等。您可以使用这些 CRM 连接器轻松地将您的应用程序与各第三方和商务应用程序相集成。

通过这些连接器，可快速轻松地集成数据：Adobe Campaign 提供专用的向导，让您从 CRM 中提供的表中收集和选择数据。并且可确保双向同步处理，让整个系统中的数据随时保持最新。

请参阅[配置 CRM 连接器](../../platform/using/crm-connectors.md)，了解如何将 CRM 工具与 Adobe Campaign 同步。

![](assets/do-not-localize/how-to-video.png)观看有关[Adobe Campaign 与 Microsoft Dynamics 365 集成](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html)的用例视频。

## 对于特定于计算机或用户的问题，如何执行软缓存清除？  {#perform-soft-cache-clear}

如果您遇到无法正确反映新徽标的问题，或者不能成功导出特定于计算机/用户的数据的问题，则可能需要在 Windows（Windows 7、Windows XP、Windows 10）上执行软缓存清除。

登录后，转到 **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**。然后，注销并重新登录。

![](assets/faq_soft_cache.png)

如果仍然无效，请尝试通过执行以下步骤清除硬缓存。

## 对于特定于计算机或用户的问题，如何执行硬缓存清除？  {#perform-hard-cache-clear}

如果您遇到无法正确反映新徽标的问题，或者不能成功导出特定于计算机/用户的数据的问题，则可能需要在 Windows（Windows 7、Windows XP、Windows 10）上执行硬缓存清除。

1. 在客户端控制台上，选择 **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**。

1. 注销并关闭客户端控制台（富客户端）。

1. 根据您的操作系统版本，转到以下位置：

   * Windows 7: C:\Users\&lt; Username >\AppData\Roaming\Neolane\NL_5\
   * Windows XP: C:\Documents and Settings\&lt; Username >\Application Data\Neolane\NL_5

   在这里，您将看到许多名为 nlclient-config-&lt; alphanumerical value >.xml 的文件。

1. 删除这些 xml 文件和关联的文件夹。

   >[!IMPORTANT]
   >
   >请勿删除 nlclient_cnx.xml 文件。

1. 登录到客户端控制台。
