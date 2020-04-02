---
title: 活动设置常见问题解答
seo-title: 如何配置 Campaign
description: Campaign Classic常见问题解答
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c5a9823b2feb6e2f721a2ad15dc08c1abe672054

---


# 活动设置常见问题解答 {#settings-faq}

了解根据您的需求设置 Campaign 实例的主要配置工作。

## Can I change the language of Campaign interface? {#can-i-change-the-language-of-campaign-interface-}

创建实例时可选择 Campaign 语言。之后将无法改变语言设置。如需详细信息，请参阅[此部分](../../installation/using/creating-an-instance-and-logging-on.md)。

Adobe Campaign 目前提供英语、法语、德语和日语共 4 种语言的用户界面。请注意，客户端控制台和服务器必须使用相同的语言设置。每个 Campaign 实例只能以一种语言运行。

如果是英语，在安装 Campaign 时可以选择美式英语还是英式英语：二者的日期和时间格式有所不同。如需有关这些差别的详细信息，请参阅[此部分](../../platform/using/adobe-campaign-workspace.md#date-and-time)。

## Can I use Campaign Classic with other Adobe solutions? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

您可以将 Adobe Campaign 的投放功能和高级活动管理功能与帮助您个性化用户体验的解决方案结合起来。

单击此处了解[如何使用其他 Adobe 解决方案](../../integrations/using/about-campaign-integrations.md)和[如何在 Campaign 中设置 IMS](../../integrations/using/about-adobe-id.md)。

## How can I set up tracking capabilities on my Campaign instance? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

作为专家级用户，您可以在 Campaign 实例上配置跟踪功能。

[单击此处了解更多信息](../../installation/using/deploying-an-instance.md#tracking-configuration)。

## 如何配置电子邮件可投放性? {#how-to-configure-email-deliverability-}

除了阅读[可投放性入门](https://docs.adobe.com/content/help/en/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html)，请参阅有关电子邮件可投放性配置的部分，了解如何配置您的实例，以充分利用 Campaign 的投放功能。

[单击此处了解更多信息](../../installation/using/email-deliverability.md)。

## How can I implement content approval? {#how-can-i-implement-content-approval-}

活动允许您以协作模式为营销活动的主要步骤设置审批流程。 对于每个活动，您可以批准投放目标、内容和成本。 负责批准工作的 Adobe Campaign 操作员收到电子邮件通知后，可通过控制台或 Web 连接批准或拒绝批准相关请求。

[单击此处了解更多信息](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)，并了解如何在 Campaign 中实施投放内容的批准工作。

## How can I access data stored in an external database? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign 提供了联合数据访问 (FDA) 选项，以处理存储在一个或多个外部数据库中的信息：无需改变 Adobe Campaign 数据的结构就可以访问外部数据。

[单击此处了解更多信息](../../platform/using/connecting-to-database.md)。

## Which external databases can I connect Campaign to? {#which-external-databases-can-i-connect-campaign-to-}

[兼容性表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)中列出了通过联合数据访问 (FDA) 与 Campaign 兼容的外部数据库。

## Can Adobe Campaign integrate with LDAP? {#can-adobe-campaign-integrate-with-ldap-}

作为内部部署/混合部署客户，您可以将 Campaign Classic 与 LDAP 目录相集成。

[单击此处了解如何操作](../../installation/using/connecting-through-ldap.md)。

## How can I set up CRM connectors in Campaign? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign 提供各种 CRM 连接器，可将您的 Adobe Campaign 平台链接到第三方系统。通过这些 CRM 连接器，您可以同步处理联系人、帐户、购买等。您可以使用这些 CRM 连接器轻松地将您的应用程序与各第三方和商务应用程序相集成。

通过这些连接器，可快速轻松地集成数据：Adobe Campaign 提供专用的向导，让您从 CRM 中提供的表中收集和选择数据。并且可确保双向同步处理，让整个系统中的数据随时保持最新。

请参阅[配置 CRM 连接器](../../platform/using/crm-connectors.md)，了解如何将 CRM 工具与 Adobe Campaign 同步。观看有关[Adobe Campaign 与 Microsoft Dynamics 365 集成](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html)的用例视频。

## 如何在问题特定于计算机或特定于用户时执行软缓存清除？ {#perform-soft-cache-clear}

如果您遇到了新徽标正确反映的问题，能够成功导出计算机特定／用户特定的数据，则可能需要在Windows(Windows 7、Windows XP、Windows 10)上执行软缓存清除。

登录后，转到 **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**。 之后，注销并重新登录。

![](assets/faq_soft_cache.png)

如果这仍然无效，请尝试通过执行以下步骤清除硬缓存。

## 如何在问题特定于计算机或特定于用户时执行硬缓存清除？ {#perform-hard-cache-clear}

如果您遇到了新徽标正确反映的问题，能够成功导出计算机特定／用户特定的数据，则可能需要在Windows(Windows 7、Windows XP、Windows 10)上执行硬缓存清除。

1. 在客户端控制台上，选择 **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**。

1. 注销并关闭客户端控制台（富客户端）。

1. 根据您的操作系统版本，转到以下位置：

   * Windows 7:C:\Users\&lt;用户名>\AppData\Roaming\Neolane\NL_5\
   * Windows XP:C:\Documents and Settings\&lt;用户名>\Application Data\Neolane\NL_5
   这里您将看到许多名为nlclient-config-&lt;字母数字值>.xml的xml文件。

1. 删除这些xml文件和关联的文件夹。

   >[!CAUTION]
   >
   >请勿删除nlclient_cnx.xml文件。

1. 登录到客户端控制台。