---
product: campaign
title: Adobe Campaign Classic v7 文档更新
description: 本页列出了 Adobe Campaign Classic 文档中的所有新增功能和更新
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
role: User
level: Beginner
exl-id: 07c1f4a3-cf16-4a9b-b402-e13258799f91
source-git-commit: cc6d85bcf822ba9be99e39cf459a5aa20cc2d4fe
workflow-type: ht
source-wordcount: '3648'
ht-degree: 100%

---

# 文档更新{#documentation-updates}

本页列出了每月所有新增功能和文档更新以及 Campaign 版本。

有关与版本相关的更新，请参阅《[Adobe Campaign Classic 发行说明](../../rn/using/latest-release.md)》。

## 2023

### 2023 年 12 月 {#dec-2023}

JWT（JSON Web 令牌）目前正在被逐步停用，它将被 OAuth 取代。此项转换工作将在 Campaign 的后续版本中逐步执行，会对文档进行更新以反映这些变化。

添加了适用于 Amazon Redshift 的 FDA 外部帐户配置。[了解更多信息](../../installation/using/configure-fda-redshift.md)

### 2023 年 8 月 {#aug-2023}

添加了一条限制说明，以指明无法使用 Adobe Campaign 解压缩大于 4GB 的压缩文件。 [了解更多信息](../../platform/using/unzip-decrypt.md)

### 2023 年 4 月 {#apr-2023}

添加了有关如何在内部部署/混合环境中启用 Microsoft Edge Chromium 的技术说明。[了解更多信息](../../technotes/using/edge-chromium.md)

### 2023 年 3 月 {#mar-2023}

更新了“发行说明”部分，更新内容是 7.3.3 版本的改进和修补程序。[了解更多信息](latest-release.md)


+++ 2022


## 2022 年 11 月 {#nov-2022}

更新了“发行说明”部分，更新内容是 7.3.2 版本的改进和修补程序。[了解更多信息](latest-release.md)

更新了兼容性矩阵，更新内容是有关 Teradata 17 的支持情况。[了解更多信息](compatibility-matrix.md)

更新了文件和资源管理部分，更新内容是有关 **uploadWhiteList** 属性的更多信息。[了解更多信息](../../installation/using/file-res-management.md)

更新了有关安全区域的文档，更新内容是有关 **allowDebug** 属性的更多信息。[了解更多信息](../../installation/using/security-zones.md#recommendations)

迁移指南已更新。已移除对不支持的 Adobe Campaign 版本的引用。[了解更多信息](../../migration/using/about-migration.md)


## 2022 年 7 月 {#july-2022}

有关过渡到新的可交付性服务器的详情，请参阅新技术说明。[了解更多信息](../../technotes/using/deliverability-server.md)

**随 7.3.1 版提供的文档更新**

更新了兼容性矩阵。[了解更多信息](compatibility-matrix.md)

更新了发行说明章节。[了解更多信息](rn-overview.md)

iOS 15 的时效性通知。[了解更多信息](../../delivery/using/create-notifications-ios.md)


## 2022 年 3 月 {#mar-2022}

添加了对 **[!UICONTROL Test SMTP delivery]** 选项的详细说明。[了解更多信息](../../delivery/using/steps-sending-the-delivery.md#delivery-additiona-parameters)

更新了升级入门页面，以阐明 Campaign 控制台升级准则。[了解更多信息](../../rn/using/rn-overview.md)

现已推出新的 Campaign v7.2.2 内部版本。[了解更多信息](../../rn/using/latest-release.md)

<!--Added troubleshooting information related to the ACS connector. [Read more](../../integrations/using/troubleshooting-the-acs-connector.md)-->

生命周期已终止的旧版 PostgreSQL 已添加至[已弃用和删除的功能](../../rn/using/deprecated-features.md#dbe-eol)页面。

## 2022 年 2 月 {#february-2022}

更新了&#x200B;**文件传输**&#x200B;活动一节，提醒用户手动监测 SFTP 目录中已存档内容的大小，以防未选择 **Delete the source files after transfer** 选项。[了解更多信息](../../workflow/using/file-transfer.md#properties)

隔离与阻止列表一节经过了修订。[了解更多信息](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

更新了有关如何将地址发送到隔离列表以及如何从隔离列表中移除地址的章节。[了解更多信息](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

添加了工作流最佳实践，建议不要在同一工作流上执行多个停止请求。[了解更多信息](../../workflow/using/workflow-best-practices.md)

添加了有关如何阻止循环投放在营销活动中运行的信息。[了解更多信息](../../workflow/using/recurring-delivery.md)

## 2022 年 1 月 {#january-2022}

**随 7.2.1 版提供的文档更新**

更新了兼容性矩阵。[了解更多信息](compatibility-matrix.md)

更新了发行说明章节。[了解更多信息](rn-overview.md)

更新了适用于 Snowflake 的 FDA 外部帐户配置。[了解更多信息](../../installation/using/configure-fda-snowflake.md)

更新了适用于 Azure Synapse Analytics 的 FDA 外部帐户配置。[了解更多信息](../../installation/using/configure-fda-synapse.md#azure-external)

更新了 Google BigQuery FDA 连接器。[了解更多信息](../../installation/using/configure-fda-google-big-query.md)

弃用后，Microsoft CRM、Salesforce、Oracle CRM On Demand 操作活动已从文档中删除。

新选项 **Abort on error** 已添加到工作流错误管理部分。[了解更多信息](../../workflow/using/advanced-parameters.md#in-case-of-errors)

在 CRM 连接器活动中增加了批量更新选项。[了解更多信息](../../workflow/using/crm-connector.md)

+++

+++ 2021

## 2021 年 12 月{#dec-2021}

Campaign Classic v7 发行说明已重新组织以简化导航。[了解更多信息](rn-overview.md)

更新并改进了有关 Campaign 表单版本的文档。[了解更多信息](../../configuration/using/editing-forms.md)

CentOs 8 的生命周期已终止，现已在 Adobe Campaign Classic 中弃用。[了解更多信息](deprecated-features.md)

## 2021 年 11 月{#nov-2021}

添加了有关传入短信 (MO) 的限制。[了解更多信息](../../delivery/using/sms-protocol.md#multipart)

更新了 CRM 连接器部署的迁移过程日志详细信息。[了解更多信息](../../migration/using/testing-the-migration.md#verification-process)

添加了有关实施 Adobe Campaign-Adobe Analytics 集成的 IMS 权限的要求。[了解更多信息](../../platform/using/adobe-analytics-provisioning.md)

将 Adobe Analytics 数据连接器的生命周期终止日期从 2022 年 3 月 1 日更新为 2022 年 8 月 17 日。[了解更多信息](deprecated-features.md)

添加了 Adobe Experience Platform 移动 SDK 文档的链接，以了解如何在 Adobe Launch 中配置 Campaign 扩展程序。[了解更多信息](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)

添加了有关如何使用 JavaScript 计算值、交换数据以及使用 SOAP 调用执行特定操作的部分。[了解更多信息](../../workflow/using/javascript-scripts-and-templates.md)

添加了在工作流中实施 JavaScript 代码的示例。[了解更多信息](../../workflow/using/javascript-in-workflows.md)


## 2021 年 10 月{#oct-2021}

现有技术说明已分组到新的&#x200B;**技术说明**&#x200B;部分。

更新了&#x200B;**硬件大小调整建议**&#x200B;页面并将其添加到了&#x200B;**技术说明**&#x200B;部分。[阅读更多](../../technotes/using/hardware-sizing.md)

## 2021 年 9 月{#sept-2021}

**随 21.1.4 版提供的文档更新**

**量规**&#x200B;图表类型已移除。

移除 Adobe Flash 后，报表和 Web 应用程序屏幕截图和参数已更新。

更新了[计费技术工作流](../../production/using/monitoring-processes.md#billing-report)的描述，并新增了护栏。

## 2021 年 8 月{#aug-2021}

添加了新的工作流活动：更改数据源 - [了解详情](../../workflow/using/change-data-source.md)

已在文档页面中添加了适用性徽章：对于 Campaign Classic v7 功能，**仅适用于 v7**，而对于常见功能，**适用于 v7 和 v8**。

添加了有关 Campaign 与 AEM Assets 之间集成的注释，该集成已从 Adobe Experience Manager 6.4 开始停用。 [了解详情](../../integrations/using/configuring-access-to-assets.md)


## 2021 年 7 月 {#july-2021}

[Campaign 21.1.3 版本](../../rn/using/latest-release.md#release-21-1-3-build-9330)已转为“一般可用性 (GA)”。


## 2021 年 6 月 {#june-2021}

**事务性消息传递**&#x200B;部分经过了重新组织，并通过新的“入门”部分进行了说明，包括[增强模式](../../message-center/using/about-transactional-messaging.md#transactional-messaging-operating-principle)，从而帮助更好地了解该流程。[阅读更多](../../message-center/using/about-transactional-messaging.md)

**随 21.1.3 版提供的文档更新**

与 Adobe Journey Orchestration 集成 - [了解详情](https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=zh-Hans)。[此页面](https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=zh-Hans)中介绍了分步用例

LINE 渠道增强 - [了解详情](../../delivery/using/line-channel.md)

新的 Vertica Analytics FDA 连接器 - [了解详情](../../installation/using/configure-fda-vertica.md)

新的 Google BigQuery FDA 连接器 - [了解详情](../../installation/using/configure-fda-google-big-query.md)

“计费 (billing)”技术工作流描述现在包括原来由“活跃计费用户档案数 (billingActiveContactCount)”执行的任务。[了解更多信息](../../workflow/using/about-technical-workflows.md)

## 2021 年 5 月 {#may-2021}

已更新和改进工作流热图报表文档。[阅读更多](../../workflow/using/heatmap.md)

兼容性矩阵中更新了 Campaign 客户端控制台要求。[阅读更多](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

已改进并阐明 Campaign 客户端控制台的安装步骤。[阅读更多](../../installation/using/installing-the-client-console.md)

已创建有关跟踪 URL 签名问题的新技术说明。[阅读更多](../../technotes/using/tracked-urls.md)

## 2021 年 4 月 {#april-2021}

新增的一个小节介绍了如何使用 Adobe Experience Platform Sources 与 Destinations 在 Campaign Classic 和 Adobe 实时客户数据平台 (RTCDP) 之间共享数据。[阅读更多](../../integrations/using/get-started-sources-destinations.md)

已创建一条新的技术说明，以说明如何在 ISP 中断后更新弹回限定条件。[阅读更多](../../delivery/using/update-bounce-qualification.md)

## 2021 年 3 月 {#march-2021}

[短信入门部分](../../delivery/using/sms-channel.md)已重新组织和完善。您现在可以在专门章节中学习如何[配置短信渠道](../../delivery/using/sms-set-up.md)、[创建短信](../../delivery/using/sms-create.md)、[发送和跟踪短信](../../delivery/using/sms-send.md)。

Campaign Classic 的“帮助和支持选项”页面已集成到核心文档中。[阅读更多](../../support.md)

已新增一个章节，介绍了有关安全性和隐私的最佳实践和检查。[阅读更多](../../installation/using/get-started-security-privacy.md)

[有关许可管理的一章](../../platform/using/access-management.md)已经过了改进并分为数节，包括有关[操作员](../../platform/using/access-management-operators.md)、[操作员组](../../platform/using/access-management-groups.md)、[已命名权限](../../platform/using/access-management-named-rights.md)和[文件夹管理](../../platform/using/access-management-folders.md)的详细信息。

通过以下新页面了解如何创建和管理活动：
* [创建和配置营销活动模板](../../campaign/using/marketing-campaign-templates.md)
* [营销活动投放](../../campaign/using/marketing-campaign-deliveries.md)
* [选择营销活动受众](../../campaign/using/marketing-campaign-target.md)
* [管理关联文档](../../campaign/using/marketing-campaign-assets.md)
* [建立和管理审批流程](../../campaign/using/marketing-campaign-approval.md)

在&#x200B;**[!UICONTROL Advanced JavaScript]**&#x200B;活动部分中添加了有关如何使用 task.setCompleted() 方法终止任务和防止将来出现撤回的信息。[阅读更多](../../workflow/using/sql-code-and-javascript-code.md#adv-js-code-desc)

[可投放性](../../delivery/using/about-deliverability.md)部分已更新，现包括指向新的 [Adobe 可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans)的链接。所有与适用于各种 Adobe 解决方案的可投放性相关的一般信息均已移至[最佳实践指南附录](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html?lang=zh-Hans#additional-resources)。

## 2021 年 2 月 {#release-21.1}

**随 21.1 版提供的文档更新**

新的&#x200B;**电子邮件反馈服务**&#x200B;功能（私人测试版）在[此处](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service)有文档说明。

**服务器配置文件**&#x200B;部分已更新了 Campaign 使用 IMS 连接到其他服务所需的配置参数。 [阅读更多](../../installation/using/the-server-configuration-file.md#ims)

在投放状态列表中，**Taken into account by the service provider（服务提供商已考虑）**&#x200B;的说明已更新：此状态现在也用于使用[电子邮件反馈服务](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service)发送的电子邮件投放。[阅读更多](../../delivery/using/delivery-statuses.md#list-delivery-statuses)

新登录屏幕上可用于连接到 Adobe Campaign 的键盘快捷键现在有文档说明。 [阅读更多](../../platform/using/launching-adobe-campaign.md#connecting-to-adobe-campaign)

**其他更新**

新增了一个章节，详细介绍了如何使用工作流执行 A/B 测试。[阅读更多](../../delivery/using/get-started-a-b-testing.md)

“Adobe Campaign 增强 MTA”部分已移动至[此处](../../delivery/using/sending-with-enhanced-mta.md)。

新增了一个页面，概述了 [!DNL Campaign Classic] 中的跟踪功能。[阅读更多](../../delivery/using/about-message-tracking.md)

新增了疑难解答部分，以帮助您解决与跟踪相关的常见问题。[阅读更多](../../delivery/using/tracking-troubleshooting.md)

**发送电子邮件**&#x200B;部分已重新组织，并增加了新的小节以提供进一步的说明。[阅读更多](../../delivery/using/sending-messages.md)

新增了有关如何在电子邮件中添加可个性化并支持跟踪的链接的信息。[阅读更多](../../delivery/using/tracking-personalized-links.md)。

## 2021 年 1 月 {#jan-2021}

**[!UICONTROL Fork]** 活动部分已使用最佳实践进行了扩充。[阅读更多](../../workflow/using/fork.md)

**CRM 连接器**&#x200B;部分已更新、改进和重组。[阅读更多](../../platform/using/crm-connectors.md)。

现在，在专用页面中详细介绍了用于连接 **Adobe Campaign 和 Microsoft Dynamics** 的步骤。[阅读更多](../../platform/using/crm-ms-dynamics.md)。

Oracle On Demand API 现在作为与 Campaign 连接的 CRM 已弃用。[阅读更多](../../rn/using/deprecated-features.md)。

了解如何在[此处](../../production/using/locate-tomcat-version.md)查找 Adobe Campaign 实例中使用的嵌入式 Tomcat Web servlet 的当前版本。

技术工作流及其关联包的列表已增强并集中到单一页面中。[阅读更多](../../workflow/using/about-technical-workflows.md)

**监视**&#x200B;指南的疑难解答部分已重组并使用登陆页进行了增强。[阅读更多](../../production/using/troubleshooting.md)。

新增&#x200B;**导入和导出数据**&#x200B;部分，其中包含与工作流、数据压缩、加密和导入最佳实践相关的新页面。[阅读更多](../../platform/using/get-started-data-import-export.md)

+++


+++ 2020


## 2020 年 12 月 {#dec-2020}

**投放监视**&#x200B;部分已重组为专题。[阅读更多](../../delivery/using/about-delivery-monitoring.md)

添加了一个关于如何将发件人的IP地址添加到传递日志的用例。[阅读更多](../../delivery/using/delivery-dashboard.md#use-case)

隐私常见问题解答已移至[此部分](../../platform/using/privacy-faq.md)。

添加了关于如何使用 **[!UICONTROL Deduplication]** 活动的合并功能的用例。[阅读更多](../../workflow/using/deduplication-merge.md)

现在，[此处](../../delivery/using/sms-protocol.md)提供短信连接器协议和设置页面的完整说明。

向&#x200B;**事务性消息传递**&#x200B;部分中添加了注释，用于警告不得将事件文件夹设置为执行实例上的视图，以避免出现访问权限问题。[阅读更多](../../message-center/using/about-event-processing.md#event-collection)

## 2020 年 11 月 {#nov-2020}

Campaign 数据模型概述已得到改进并重组。[阅读更多](../../configuration/using/about-data-model.md)。

外部帐户配置已移至[此部分](../../installation/using/external-accounts.md)。

Campaign 联合数据访问 (FDA) 文档已通过每个外部数据库配置的详细信息得到改进，并已移至[此部分](../../installation/using/about-fda.md)。

Campaign 20.2.3 版本已转为“正式发布版 (GA)”。

“隐私”部分已移动并新增两个页面：[隐私管理](../../platform/using/privacy-management.md)和[管理隐私请求](../../platform/using/privacy-requests.md)。

在中间源服务器配置页面中添加了注释，以指定设置服务器后便不应更新外部帐户的内部名称。[阅读更多](../../installation/using/mid-sourcing-server.md)

已添加有关在指定外部 SFTP 服务器的路径时要使用的语法的信息。[阅读更多](../../platform/using/sftp-server-usage.md#external-SFTP-server)

“个人数据和角色”部分已使用用例方案进行更新，以说明不同角色在隐私方面如何进行交互。[阅读更多](../../platform/using/privacy-and-recommendations.md#use-case-scenario)

新增了一个部分，其中列出有关隐私的常见问题解答。[阅读更多](../../platform/using/privacy-faq.md)

## 2020 年 10 月 {#oct-2020}

**20.3 版本中包含的新功能**

iOS 的推送通知改进 - [阅读更多](../../delivery/using/configuring-the-mobile-application.md)

Android 的推送通知改进 - [阅读更多](../../delivery/using/configuring-the-mobile-application-android.md)

**随版本提供的其他文档更新**

兼容性矩阵已更新。[阅读更多](../../rn/using/compatibility-matrix.md)

更新了已弃用和已删除的功能页面。[阅读更多](../../rn/using/deprecated-features.md)

[!DNL Gold Standard] 版本的发行说明和兼容性矩阵现在可在专门页面中获取。
[阅读更多](../../rn/using/gold-standard.md)。

最初基于 oAUTH 身份验证设置来访问管道的 Triggers 集成现已更改并移至 Adobe I/O。[阅读更多](../../integrations/using/configuring-adobe-io.md)

**其他更新**

已更新文档页面，以反映 Tomcat 8 更新。

已在“获取 Adobe Campaign 版本”部分的“关于”框说明中添加了详细信息。[阅读更多](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

已向“更新 Adobe Campaign Classic”部分中添加了执行内部版本升级的准则。[了解更多信息](../../production/using/build-upgrade.md)

已向 Campaign 常见问题部分中添加了关于 Campaign 内部版本升级的常见问题解答。阅读更多 [阅读更多](../../platform/using/faq-build-upgrade.md)

现在，在专用部分中对 Campaign 本地、托管和混合托管模型进行说明。[阅读更多](../../installation/using/hosting-models.md)

已在《安装指南》中更新并移动每个托管模型的 Campaign 功能矩阵。[阅读更多](../../installation/using/capability-matrix.md)

“Campaign 报告高级功能”部分已得到改进，以详细说明如何在自定义报告中使用 URL 参数和变量。[阅读更多](../../reporting/using/advanced-functionalities.md)

报告属性页面已重组并进行了丰富，以促进配置。[阅读更多](../../reporting/using/properties-of-the-report.md)

## 2020 年 9 月 {#september-2020}

已添加注释来指定“有效用户档案”计数仅适用于营销实例。[阅读更多](../../platform/using/about-profiles.md#active-profiles)

已添加有关模式版本的新示例来将字段链接到现有引用表。[阅读更多](../../configuration/using/examples-of-schemas-edition.md#uc-link)

已添加关于在投放中对种子地址使用额外数据的说明。[阅读更多](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## 2020 年 8 月 {#aug-2020}

通过专用部分了解与使用 Campaign 进行投放设计和发送相关的最佳实践。[阅读更多](../../delivery/using/delivery-best-practices.md)

改进了“投放能力”最佳实践登陆页，以促进访问各个子部分。[阅读更多](../../delivery/using/about-deliverability.md)

现在，可在以下主题中获取操作方法视频：

* [如何使用类型规则和预定义过滤器建立疲劳管理](../../campaign-opt/using/about-campaign-typologies.md)

* [如何在营销活动中创建电子邮件](../../campaign/using/marketing-campaign-deliveries.md)

* [如何创建包含条件内容的多语言新闻稿](../../delivery/using/conditional-content.md)

* [如何配置和部署投放模板](../../delivery/using/creating-a-delivery-template.md)

* [如何激活和使用 AMP 处理电子邮件](../../delivery/using/defining-interactive-content.md)

* [如何使用动态内容块个性化电子邮件](../../delivery/using/personalization-blocks.md)

* [如何使用个性化字段个性化电子邮件](../../delivery/using/personalization-fields.md)

* [如何在电子邮件中管理种子和验证](../../delivery/using/steps-defining-the-target-population.md)

* [如何设置循环投放](../../workflow/using/recurring-delivery.md)

* [如何设置连续投放](../../workflow/using/continuous-delivery.md)

已添加有关在连接到 FTP 服务器后收到“无法解析主机名”错误时要执行的检查和操作的信息。[阅读更多](../../platform/using/sftp-server-usage.md)

已在[工作流用例](../../workflow/using/about-workflow-use-cases.md)列表中引用新用例：

* 自动完成内容创建、编辑和发布
* 在发送投放之前设置收件人审批流程
* 在查询中调用实例变量
* 对总体应用分割百分比

**[!UICONTROL AND-join]** 活动部分的内容中增加了有关其使用情况的更多信息和关于变量的使用说明。[了解更多信息](../../workflow/using/and-join.md)

## 2020 年 7 月 {#july-2020}

已向工作流用例中添加了有关如何使用增量查询自动更新列表的用例。[阅读更多](../../workflow/using/about-workflow-use-cases.md)

[发行说明](../../rn/using/latest-release.md)已重组：添加了[概述页面](../../rn/using/latest-release.md)，其中包含有关生成状态、升级过程、建议和重要链接的信息。此外，还添加了 [[!DNL Gold Standard]  版本](../../rn/using/gold-standard.md)的专门页面，并集成了[兼容性矩阵](../../rn/using/compatibility-matrix.md)。

已添加新部分，其中包含与 Campaign Classic 监控相关的准则。[阅读更多](../../production/using/monitoring-guidelines.md)

“隐私和同意”部分已得到增强，其中包含更多详细信息和有用的链接。[阅读更多](../../platform/using/privacy-and-recommendations.md)

“Campaign Classic 中的隐私管理”页面已更新，其中包含有关“规定”字段的信息，现在在使用允许设置自动隐私请求流程的 API 时，该字段可用。[了解更多信息](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

“隐私管理概述”页面已更新，包含有关泰国的个人数据保护法 (PDPA) 和巴西的 Lei Geral de Proteção de Dados (LGPD) 的信息。[了解更多信息](../../platform/using/privacy-and-recommendations.md)

添加了有关子工作流日志和行为的信息，以防出错。[阅读更多](../../workflow/using/sub-workflow.md)

已在 **[!UICONTROL Scheduler]** 活动部分中添加最佳实践。[阅读更多](../../workflow/using/scheduler.md)

## 2020 年 6 月 {#june-2020}

更新了“删除隔离地址”部分。这包括明确了地址会自动从隔离列表中删除的情况。[阅读更多](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

在如何使用控制面板和活动工作流[加密](../../platform/using/zip-encrypt.md)和[解密](../../platform/using/unzip-decrypt.md)数据方面添加了用例。

Experience Cloud Triggers 和 Adobe Campaign Classic 集成页面已移至[此处](../../integrations/using/about-triggers.md)。

## 2020 年 7 月 {#release-20-2}

**20.2 版本中包含的新功能**

支持表情符号 - [阅读更多](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA 连接器 - [阅读更多](../../installation/using/configure-fda-synapse.md)

泰国和巴西隐私法 - [阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**随版本提供的其他文档更新**

[此部分](../../message-center/using/publishing-message-templates.md#template-unpublication)介绍了用于取消发布事务性消息模板的新选项。

在 Campaign Classic 选项列表中添加了新选项，允许在发送包含从个性化 URL 下载的图像和附件的电子邮件时设置限制。[阅读更多](../../installation/using/configuring-campaign-options.md#delivery)

[此部分](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis)介绍了新的&#x200B;**在数据库中准备投放部分**&#x200B;选项。

对“验证投放”部分做了明确说明和更新。[阅读更多](../../delivery/using/steps-validating-the-delivery.md)

与新跟踪链接签名机制相关的参数已添加到 [服务器配置文件](../../installation/using/the-server-configuration-file.md)部分。

兼容性矩阵已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

清除工作流部分已更新。[了解详情](../../production/using/database-cleanup-workflow.md)

Campaign 网络端点已移至此[部分](../../installation/using/campaign-network-endpoints.md)。

Spam Assassin 安装部分已更新为新的安装文件名。[了解详情](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

有关复制环境的部分已更新。[了解详情](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## 2020 年 5 月 {#may-2020}

“监视投放能力”部分已移动和改进。[阅读更多](../../delivery/using/monitoring-deliverability.md)

“投放能力”疑难解答部分已移动和改进。[阅读更多](../../delivery/using/deliverability-faq.md)

启动新平台时的可投放性指导原则经过了改进。[阅读更多](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans#transition-process)

已移动并更新“发送带有附件的事务电子邮件”部分。[阅读更多](../../message-center/using/transactional-email-with-attachments.md)

数据包最佳实践部分已移动并更新。[阅读更多](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## 2020 年 4 月 {#april-2020}

联合数据访问 (FDA) 权限表已移至访问外部数据库 (FDA) 文档。[阅读更多](../../installation/using/remote-database-access-rights.md)

常见问题解答已更新，其中包含有关如何清除软缓存和硬缓存的提示。[阅读更多](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

数据模型最佳实践已得到改进，并添加了有关索引的更多信息。[阅读更多](../../configuration/using/data-model-best-practices.md#indexes)

描述 Adobe Campaign 内置数据模型的部分已更新，每个表中都有更多详细信息。[阅读更多](../../configuration/using/data-model-description.md)

工作流用例已更新并重新组织为主题部分。[阅读更多](../../workflow/using/about-workflow-use-cases.md)

[弹回邮件资格](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) 和[电子邮件管理规则](../../delivery/using/understanding-delivery-failures.md#email-management-rules)部分已改进并增加了更新的信息。

Adobe Campaign 增强 MTA 文章已更新。现在只适用于 Campaign Classic。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html)

## 2020 年 3 月 {#march-2020}

数据模型最佳实践已更新新的部分，包括[序列](../../configuration/using/data-model-best-practices.md#sequences)性能[和](../../configuration/using/data-model-best-practices.md#performance) 大表 [](../../configuration/using/data-model-best-practices.md#large-tables)。[阅读更多](../../configuration/using/data-model-best-practices.md)

现在提供了描述 Adobe Campaign 内置数据模型和表之间交互的新部分。[阅读更多](../../configuration/using/data-model-description.md)

其他关键链接已添加到文档主页。[阅读更多](../../campaign-classic-home.md)

已添加一个用例，说明如何将动态优惠从 Adobe Target 集成到 Adobe Campaign 的电子邮件中。[阅读更多](../../integrations/using/inserting-a-dynamic-image.md)

现在提供了详细介绍 Adobe Campaign 中不同语言的新部分。[阅读更多](../../platform/using/adobe-campaign-workspace.md#languages)

访问管理指南已更新，其中包含有关已命名权限的更多信息。[阅读更多](../../platform/using/access-management-named-rights.md)

## 2020 年 2 月 {#february-2020}

现在提供概述设计 Adobe Campaign 数据模型时最佳实践和主要建议的新部分。[阅读更多](../../configuration/using/data-model-best-practices.md)

新增了有关技术电子邮件配置的部分。[阅读更多](../../installation/using/email-deliverability.md)

“投放能力常见问题解答”已更新，其中包含有关“满足配额”错误消息的更多详细信息。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-deliverability-faq.html#FAQ)

新的电子邮件提供商现在支持 AMP for Email：相关文档已更新。[阅读更多](../../delivery/using/defining-interactive-content.md)

电子邮件存档部分已得到改进。[阅读更多](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 2020 年 1 月 {#release-20-1}

**20.1 版本中包含的新功能**

Snowflake FDA 连接器 - [阅读更多](../../installation/using/configure-fda-snowflake.md)

Hadoop FDA 连接器增强 - [阅读更多](../../installation/using/configure-fda-hadoop.md)

**随版本提供的其他文档更新**

[安装、](../../installation/using/general-architecture.md) [生产](../../production/using/foreword.md)[和配置](../../configuration/using/additional-parameters.md)指南已更新，包含 nlserver 服务启动使用的新系统单元。您仍可以使用 /etc/init.d/nlserver6，但 Adobe 建议您现在使用 systemctl 命令与 nlserver 服务进行交互。

安装指南已更新并与最新版本的兼容性矩阵同步。新增了支持的系统。已弃用和不支持的系统的实例已被删除。[阅读更多](../../installation/using/general-architecture.md)

更新了兼容性矩阵，纳入 Hadoop 3.0 和 Snowflake FDA 连接器。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

安装指南中添加了有关 IP 关联的最佳实践。[阅读更多](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

数据库清理工作流部分已更新。现在提供的批处理数字反映代码实现。[阅读更多](../../production/using/database-cleanup-workflow.md)

事务性消息传递指南中增加了对 HTTP 联合数据访问的限制。[阅读更多](../../production/using/database-cleanup-workflow.md)

新选项中添加了信息，允许您为&#x200B;**[!UICONTROL JavaScript code]**&#x200B;和 **[!UICONTROL Advanced JavaScript code]**&#x200B;工作流活动定义超时期限。[阅读更多](../../workflow/using/sql-code-and-javascript-code.md)

在 **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** 节点的新 **[!UICONTROL Start Pending]** 视图中添加了信息。[阅读更多](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

移动、重新组织和改进了[发送推送通知](../../delivery/using/about-mobile-app-channel.md)指南，提供了澄清信息。

[此处](../../reporting/using/properties-of-the-report.md#defining-additional-settings)记录了 URL 报告配置的新参数。

**Campaign Classic 本地和托管功能矩阵**&#x200B;页面已更新新的 FDA 连接器。[阅读更多](../../installation/using/capability-matrix.md)。

**Campaign Classic 功能矩阵**&#x200B;页面已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

新的&#x200B;**[!UICONTROL Cleanup of Nmsaddress]**&#x200B;工作流记录在[此处](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress)。

添加了在工作流中使用查询活动时的限制。[阅读更多](../../workflow/using/query.md)。

新增了一个部分，以详细描述增强的电子邮件地址验证规则，以便在发生软错误时发送隔离地址。[阅读更多](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

配置文件中表明实例是否正在使用增强的 MTA 的参数现予以记录。[阅读更多](../../installation/using/the-server-configuration-file.md#mta)

“投放能力”部分进行了移动、重新组织和增加了更新的内容。[阅读更多](../../delivery/using/about-deliverability.md)

现在提供了新的部分，介绍 Adobe Campaign Classic 数据模型基础知识以及如何访问每个表的说明。[阅读更多](../../configuration/using/about-data-model.md)

Adobe Campaign 增强 MTA 文章已更新，其中包含有关在未向每封邮件添加所需增强 MTA 头的实例上安装特定 Typology 包的详细信息。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

与查询设计相关的用例已重新组织为单独的部分。[阅读更多](../../workflow/using/querying-recipient-table.md)

增加了有关管理优惠和使用 Adobe Campaign Classic 中的交互模块的提示和技巧的新部分。[阅读更多](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

“交互”文档中增加了指向多个视频的链接，这些视频有助于更好地了解如何管理优惠。[阅读更多](../../interaction/using/interaction-and-offer-management.md)

有关如何优化实例上运行的查询的最佳实践文章已集成到文档中。[阅读更多](../../workflow/using/query.md#optimizing-queries)

报告指南已更新并重新组织。[阅读更多](../../reporting/using/about-adobe-campaign-reporting-tools.md)

已添加如何在工作流中使用实例变量的示例。[阅读更多](../../workflow/using/javascript-scripts-and-templates.md)

+++

<!--

### December 2019 {#december-2019}

The "WdbcOptions_TempDbName" option has been added to the list of Campaign options. [Read more](../../installation/using/configuring-campaign-options.md)

The FDA matrix page has been moved [here](../../installation/using/remote-database-access-rights.md).

The Access Rights Matrix page has been moved [here](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf).

The section describing how to define interactive content with AMP has been moved. [Read more](../../delivery/using/defining-interactive-content.md)

**New capabilities included in 19.2 release**

California Consumer Privacy Act (CCPA) - [Read more](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

Interactive content with AMP - [Read more](../../delivery/using/defining-interactive-content.md)

Workflow live monitoring - [Read more](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Secure SMS Messaging (TLS) - [Read more](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

**Other documentation updates coming with the release**

The Adobe Campaign Enhanced MTA documentation is now available. [Read more](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

A new section has been added on how to troubleshoot a workflow staying in the "Start as soon as possible" state within a campaign. [Read more](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

The new "NmsOperation_DeliveryPreparationWindow" and "WdbcKillSessionPolicy" options have been added to the list of Campaign options. [Read more](../../installation/using/configuring-campaign-options.md)

A new document describing the Adobe Campaign Classic data model basics is now available. [Read more](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)

The new **Maximum personalization run time** option in the delivery properties is documented in this [section](../../delivery/using/personalization-fields.md#timing-out-personalization).

The examples for API calls using an **HttpServletRequest** with logon() and query() have been updated. [Read more](../../configuration/using/web-service-calls.md).

A recommendation for **sqlDefault** attribute in schema definition has been added. [Read more](../../configuration/using/schema/attribute.md)).

The integration between Adobe Campaign and Adobe Real-time Customer Data Platform is now referenced in the **Integrating with Adobe Experience Cloud** guide. [Read more](../../integrations/using/about-campaign-integrations.md).

### November 2019 {#november-2019}

A warning has been added to the [Multiplexing the mid-sourcing server](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) and [Supporting several control instances](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) sections mentioning that these deployments are not supported for fully hosted and hybrid clients.

A new section has been added to describe how to force the character encoding used when sending an email. [Read more](../../delivery/using/sending-messages.md#character-encoding)

The Access management section has been updated with the **Privacy Data right**. [Read more](../../platform/using/access-management-named-rights.md)

Information was added to specify that personalization fields content cannot exceed 1024 characters. [Read more](../../delivery/using/personalization-fields.md)

The Control Panel documentation has been integrated into the new collaborative documentation set. [Read more](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)

The Delivery Best Practices getting started guide has been updated. [Read more](../../delivery/using/delivery-best-practices.md)

### October 2019 {#october-2019}

The list of error messages for Campaign has been updated. [Read more](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html)

The GDPR getting started guide has been improved and enriched. It is now a privacy management documentation including GDPR and CCPA. [Read more](https://helpx.adobe.com/content/help/en/campaign/kb/campaign-privacy.html)

A new troubleshooting page has been added for tracking in Campaign Classic. [Read more](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html).

A new page of best practices for Adobe Analytics Connector has been added. [Read more on Adobe Analytics Connector](../../platform/using/adobe-analytics-connector.md)

The Delivery Best Practices getting started guide has been moved and updated. [Read more](../../delivery/using/delivery-best-practices.md)

A recommendation has been added to the SMS channel documentation to avoid issues when using multiple external accounts leveraging the Extended generic SMPP connector with the same provider account. [Read more](../../delivery/using/sms-set-up.md#automatic-reply)

Information was added in the Scheduler activity documentation on how to prevent simultaneous executions of a workflow. [Read more](../../workflow/using/scheduler.md)

The steps to configure Inbox rendering for on-premise installations have been added to documentation. [Read more](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

### September 2019 {#september-2019}

A new page has been added to provide general guidelines for maintaining Campaign Classic. [Read more](../../production/using/monitoring-guidelines.md)

Information related to workflows monitoring has been centralized into a new dedicated section. [Read more](../../workflow/using/monitoring-workflow-execution.md).

A new page about general guidelines for tracking in Adobe Campaign Classic has been added. [Read more](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

The best practices for performance improvements of workflows and deliveries have been updated. [Read more on workflows](../../workflow/using/workflow-best-practices.md) and [more on deliveries](../../delivery/using/delivery-performances.md#best-practices-performance).

### May 2019 {#release-19-1}

**New capabilities included in 19.1 release**

Control Panel - [Read more](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)

Audit trail - [Read more](../../production/using/audit-trail.md)

**Other documentation updates coming with the release**

A new Build upgrade FAQ has been created. [Read more](https://helpx.adobe.com/campaign/kb/build-upgrade-faq.html)

The [Compatibility matrix](compatibility-matrix.md) has been updated. The list of supported database systems has been updated, Android/iOS versions and related SDKs. The 19.0 Compatibility matrix has been archived.

The 'Deprecated and Removed Features in Campaign Classic' page has been updated. [Read more](deprecated-features.md)

The description of the server configuration file has been added to the Installation guide. [Read more](../../installation/using/the-server-configuration-file.md)

A section has been added describing the installation and configuration steps for hosted and hybrid models. [Read more](../../installation/using/hosting-models.md)

A section has been added describing the Campaign server uninstallation steps. [Read more](../../installation/using/uninstalling-campaign.md)

The [security](https://helpx.adobe.com/campaign/kb/acc-security.html), [deliverability](../../delivery/using/about-deliverability.md) and [privacy](../../platform/using/privacy-management.md) getting started guides have been updated.

The description of the pre-process workflow option has been updated to reflect product changes. [Read more](../../workflow/using/data-loading--file-.md)

The Experience Cloud Triggers technote has been updated. [Read more](../../integrations/using/about-triggers.md)

The list of error messages has been updated. [Read more](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html)

Added more information on SOAP authentication methods for transactional messaging. [Read more](../../message-center/using/event-description.md)

The Apache configuration steps have been updated. [Read more](../../installation/using/integration-into-a-web-server-for-linux.md)

A new page has been added including the list of endpoints for Classic. [Read more](../../installation/using/campaign-network-endpoints.md)

The Data package best practices article has been updated. [Read more](../../configuration/using/data-model-best-practices.md)

The Managing Offers documentation has been updated with a new section listing best practices. [Read more](../../interaction/using/interaction-best-practices.md)

A new Knowledge base article on using the offer catalog in Adobe Campaign Classic has been created. [Read more](https://helpx.adobe.com/campaign/kb/offer-best-practices.html)

The Sub-workflow activity section has been enhanced with an example of usage. [Read more](../../workflow/using/sub-workflow.md)

The [Campaign Classic On-premise & Hosted capability matrix](../../installation/using/capability-matrix.md) page has been updated with information relating to Email BCC.

The Transactional Messaging documentation has been updated with a note regarding template publication. [Read more](../../message-center/using/publishing-message-templates.md#template-publication)

The Unprocessed bounce mails section has been updated with more details on the Forwarding address and Address for errors fields. [Read more](../../installation/using/deploying-an-instance.md)

A new section on workflow planning best practices has been added. [Read more](../../workflow/using/workflow-best-practices.md)

Added two new options to the list of Campaign options: XtkSecurity_Restrict_EditXML and NmsOperation_OperationMgtDebug.
 [Read more](../../installation/using/configuring-campaign-options.md)

Added information on the different external accounts available in Campaign Classic and how to configure them.
 [Read more](../../installation/using/external-accounts.md)

Updated Analytics Connector section to reflect interface changes.
 [Read more](../../platform/using/adobe-analytics-connector.md)

Added information on the Billing report.
 [Read more](../../production/using/monitoring-processes.md)

Updated documentation on the Shared audiences integration.
 [Read more](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)

The following technote has been updated: [SMS connector protocol and settings](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html).

The Technical workflows section has been updated. [Read more](../../workflow/using/about-technical-workflows.md)

The Campaign Domain Name Setup procedure has been improved and updated.

The Campaign Hardware Sizing Guide has been updated. [Read more](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)

Information was added on Query Banding for the Teradata external account. [Read more](../../installation/using/external-accounts.md)

### January 2019{#release-doc-16-01-2019}

The Experience Cloud Triggers technote has been updated. [Read more](../../integrations/using/about-triggers.md)

A note was added in the offer approval section to specify  that the "Content approved" mention indicates that the content approval process has been achieved, whether all offers have been enabled/approved or not. [Read more](../../interaction/using/offer-catalog-overview.md)

A new section was added in the Installation guide, listing options from the Administration / Platform / Options node. [Read more](../../installation/using/configuring-campaign-options.md)

Information was added about the use of seed addresses to protect your mailing list. [Read more](../../delivery/using/creating-seed-addresses.md)

Key steps when creating and sending a delivery have been regrouped into a new section, with references to the various channels when needed. [Read more](../../delivery/using/steps-about-delivery-creation-steps.md)

The [Email archiving](../../installation/using/email-archiving.md) section has been moved, reorganized and improved with clarified information:

* Best practices have been added regarding emails per connection and BCC sending IPs parameters.

* We've updated the steps to upgrade to the new email archiving system (BCC) if you were already using email archiving with an older build (prior to Adobe Campaign 17.2 – build 8795).

A use case has been added to the Automating with Workflows guide: Sending personalized alerts to operators. [Read more](../../workflow/using/sending-personalized-alerts-to-operators.md)

The "Migrating to a new version" section has been updated. The documentation now only details the steps for a migration to Adobe Campaign Classic v7 from any older version, as it is no longer possible to migrate to Adobe Campaign v6.11. [Read more](../../migration/using/about-migration.md)

The "Retries after a delivery temporary failure" section has been clarified. [Read more](../../delivery/using/understanding-delivery-failures.md)

Links to the "Digital Content Editor" section have been added to the "Defining the email content" section. [Read more](../../delivery/using/defining-the-email-content.md)

The "Transactional messaging architecture" section has been updated with a warning specifying that the control and the execution instances cannot be installed on the same machine. [Read more](../../message-center/using/transactional-messaging-architecture.md)

The "Workflow monitoring" section has been updated with a note for builds between 8700 and 8977 (18.10), including a link to the technote on how to install the Workflow HeatMap package for these builds. [Read more](../../workflow/using/heatmap.md)

Added a use case on how to send an email with custom data fields using the Enrichment activity in a workflow. [Read more](../../workflow/using/email-enrichment-with-custom-date-fields.md)

Feature videos have been moved [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).
-->
