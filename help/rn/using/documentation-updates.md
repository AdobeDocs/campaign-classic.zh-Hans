---
product: campaign
title: Adobe Campaign Classic v7 文档更新
description: 本页列出了 Adobe Campaign Classic 文档中的所有新增功能和更新
feature: Overview
role: User
level: Beginner
exl-id: 07c1f4a3-cf16-4a9b-b402-e13258799f91
source-git-commit: 87067a0cca1a4a7f8ea1137ece6d513d58fcdb42
workflow-type: tm+mt
source-wordcount: '4796'
ht-degree: 95%

---

# 文档更新{#documentation-updates}

![](../../assets/v7-only.svg)

本页列出了每月所有新增功能和文档更新以及 Campaign 版本。

有关与版本相关的更新，请参阅《[Adobe Campaign Classic 发行说明](../../rn/using/latest-release.md)》。

## 2022年

###  年 1 月

**随 7.2.1 版提供的文档更新**

更新了兼容性矩阵。 [了解更多信息](compatibility-matrix.md)

更新了发行说明章节。 [了解更多信息](rn-overview.md)

更新了FDA外部帐户配置以进行Snowflake。 [了解更多信息](../../installation/using/configure-fda-snowflake.md)

更新了Azure synapse分析的FDA外部帐户配置。 [了解更多信息](../../installation/using/configure-fda-synapse.md#azure-external)

更新了Google BigQuery FDA连接器。 [了解更多信息](../../installation/using/configure-fda-google-big-query.md)

弃用后，Microsoft CRM、Salesforce、OracleCRM（按需）操作活动已从文档中删除。

新选项 **出错时中止** 已添加到工作流错误管理部分。 [了解更多信息](../../workflow/using/advanced-parameters.md#in-case-of-errors)

在CRM连接器活动中添加了批量更新选项。 [了解更多信息](../../workflow/using/crm-connector.md)

## 2021年

### 2021 年 12 月{#dec-2021}

Campaign Classicv7发行说明已重新组织，以简化导航。 [了解更多信息](rn-overview.md)

更新并改进了有关Campaign表单版本的文档。 [了解更多信息](../../configuration/using/editing-forms.md)

CentOs 8已结束其生命周期，现已在Adobe Campaign Classic中弃用。 [了解更多信息](deprecated-features.md)

### 2021 年 11 月{#nov-2021}

添加了有关传入短信(MO)的限制。 [了解更多信息](../../delivery/using/sms-protocol.md#multipart)

更新了CRM连接器部署的迁移过程日志详细信息。 [了解更多信息](../../migration/using/testing-the-migration.md#verification-process)

添加了有关实施Adobe Campaign-Adobe Analytics集成的IMS权限的要求。 [了解更多信息](../../platform/using/adobe-analytics-provisioning.md)

更新了Adobe Analytics Data Connector生命周期终止日期，从2022年3月1日至2022年8月17日。 [了解更多信息](deprecated-features.md)

添加了指向Adobe Experience Platform Mobile SDK文档的链接，以了解如何在Launch中配置Campaign扩展Adobe。 [了解更多信息](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)

添加了有关如何使用JavaScript计算值、交换数据以及使用SOAP调用执行特定操作的章节。[了解更多信息](../../workflow/using/javascript-scripts-and-templates.md)

在工作流中添加了JavaScript代码实施示例。 [了解更多信息](../../workflow/using/javascript-in-workflows.md)


### 2021 年 10 月{#oct-2021}

现有技术说明已分组到新的&#x200B;**技术说明**&#x200B;部分。

更新了&#x200B;**硬件大小调整建议**&#x200B;页面并将其添加到了&#x200B;**技术说明**&#x200B;部分。[阅读更多](../../technotes/using/hardware-sizing.md)

### 2021 年 9 月{#sept-2021}

**随 21.1.4 版提供的文档更新**

**量规**&#x200B;图表类型已移除。

移除 Adobe Flash 后，报表和 Web 应用程序屏幕截图和参数已更新。

更新了[计费技术工作流](../../production/using/monitoring-processes.md#billing-report)的描述，并新增了护栏。

### 2021 年 8 月{#aug-2021}

添加了新的工作流活动：更改数据源 - [了解详情](../../workflow/using/change-data-source.md)

已在文档页面中添加了适用性徽章：对于 Campaign Classic v7 功能，**仅适用于 v7**，而对于常见功能，**适用于 v7 和 v8**。

添加了有关 Campaign 与 AEM Assets 之间集成的注释，该集成已从 Adobe Experience Manager 6.4 开始停用。 [了解详情](../../integrations/using/configuring-access-to-assets.md)


### 2021 年 7 月 {#july-2021}

[Campaign 21.1.3 版本](../../rn/using/latest-release.md#release-21-1-3-build-9330)已转为“一般可用性 (GA)”。


### 2021 年 6 月 {#june-2021}

**事务性消息传递**&#x200B;部分经过了重新组织，并通过新的“入门”部分进行了说明，包括[增强模式](../../message-center/using/about-transactional-messaging.md#transactional-messaging-operating-principle)，从而帮助更好地了解该流程。[阅读更多](../../message-center/using/about-transactional-messaging.md)

**随 21.1.3 版提供的文档更新**

与 Adobe Journey Orchestration 集成 - [了解详情](https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=zh-Hans)。[此页面](https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=zh-Hans)中介绍了分步用例

LINE 渠道增强 - [了解详情](../../delivery/using/line-channel.md)

新的 Vertica FDA 连接器 - [了解详情](../../installation/using/configure-fda-vertica.md)

新的Google BigQuery FDA连接器 —  [了解更多](../../installation/using/configure-fda-google-big-query.md)

“计费 (billing)”技术工作流描述现在包括原来由“活跃计费用户档案数 (billingActiveContactCount)”执行的任务。[阅读更多](../../workflow/using/about-technical-workflows.md)

### 2021 年 5 月 {#may-2021}

已更新和改进工作流热图报表文档。[阅读更多](../../workflow/using/heatmap.md)

兼容性矩阵中更新了 Campaign 客户端控制台要求。[阅读更多](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

已改进并阐明 Campaign 客户端控制台的安装步骤。[阅读更多](../../installation/using/installing-the-client-console.md)

已创建有关跟踪 URL 签名问题的新技术说明。[阅读更多](../../technotes/using/tracked-urls.md)

### 2021 年 4 月 {#april-2021}

新增的一个小节介绍了如何使用 Adobe Experience Platform Sources 与 Destinations 在 Campaign Classic 和 Adobe 实时客户数据平台 (RTCDP) 之间共享数据。[阅读更多](../../integrations/using/get-started-sources-destinations.md)

已创建一条新的技术说明，以说明如何在 ISP 中断后更新弹回限定条件。[阅读更多](../../delivery/using/update-bounce-qualification.md)

### 2021 年 3 月 {#march-2021}

[开始使用短信部分](../../delivery/using/sms-channel.md)已重新组织和完善。您现在可以在专门章节中学习如何[配置短信渠道](../../delivery/using/sms-set-up.md)、[创建短信](../../delivery/using/sms-create.md)、[发送和跟踪短信](../../delivery/using/sms-send.md)。

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

### 2021 年 2 月 {#release-21.1}

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

### 2021 年 1 月 {#jan-2021}

**[!UICONTROL Fork]** 活动部分已使用最佳实践进行了扩充。[阅读更多](../../workflow/using/fork.md)

**CRM 连接器**&#x200B;部分已更新、改进和重组。[阅读更多](../../platform/using/crm-connectors.md)。

现在，在专用页面中详细介绍了用于连接 **Adobe Campaign 和 Microsoft Dynamics** 的步骤。[阅读更多](../../platform/using/crm-ms-dynamics.md)。

Oracle On Demand API 现在作为与 Campaign 连接的 CRM 已弃用。[阅读更多](../../rn/using/deprecated-features.md)。

了解如何在[此处](../../production/using/locate-tomcat-version.md)查找 Adobe Campaign 实例中使用的嵌入式 Tomcat Web servlet 的当前版本。

技术工作流及其关联包的列表已增强并集中到单一页面中。[阅读更多](../../workflow/using/about-technical-workflows.md)

**监视**&#x200B;指南的疑难解答部分已重组并使用登陆页进行了增强。[阅读更多](../../production/using/troubleshooting.md)。

新增&#x200B;**导入和导出数据**&#x200B;部分，其中包含与工作流、数据压缩、加密和导入最佳实践相关的新页面。[阅读更多](../../platform/using/get-started-data-import-export.md)






## 2020年

### 2020 年 12 月 {#dec-2020}

**投放监视**&#x200B;部分已重组为专题。[阅读更多](../../delivery/using/about-delivery-monitoring.md)

添加了一个关于如何将发件人的IP地址添加到传递日志的用例。[阅读更多](../../delivery/using/delivery-dashboard.md#use-case)

隐私常见问题解答已移至[此部分](../../platform/using/privacy-faq.md)。

添加了关于如何使用 **[!UICONTROL Deduplication]** 活动的合并功能的用例。[阅读更多](../../workflow/using/deduplication-merge.md)

现在，[此处](../../delivery/using/sms-protocol.md)提供 SMS 连接器协议和设置页面的完整说明。

向&#x200B;**事务性消息传递**&#x200B;部分中添加了注释，用于警告不得将事件文件夹设置为执行实例上的视图，以避免出现访问权限问题。[阅读更多](../../message-center/using/about-event-processing.md#event-collection)

### 2020 年 11 月 {#nov-2020}

Campaign 数据模型概述已得到改进并重组。[阅读更多](../../configuration/using/about-data-model.md)。

外部帐户配置已移至[此部分](../../installation/using/external-accounts.md)。

Campaign 联合数据访问 (FDA) 文档已通过每个外部数据库配置的详细信息得到改进，并已移至[此部分](../../installation/using/about-fda.md)。

[Campaign 20.2.3 版本](../../rn/using/release--2020.md#release-20-2-3-build-9182)已转为“一般可用性 (GA)”。

“隐私”部分已移动并新增两个页面：[隐私管理](../../platform/using/privacy-management.md)和[管理隐私请求](../../platform/using/privacy-requests.md)。

在中间源服务器配置页面中添加了注释，以指定设置服务器后便不应更新外部帐户的内部名称。[阅读更多](../../installation/using/mid-sourcing-server.md)

已添加有关在指定外部 SFTP 服务器的路径时要使用的语法的信息。[阅读更多](../../platform/using/sftp-server-usage.md#external-SFTP-server)

“个人数据和角色”部分已使用用例方案进行更新，以说明不同角色在隐私方面如何进行交互。[阅读更多](../../platform/using/privacy-and-recommendations.md#use-case-scenario)

新增了一个部分，其中列出有关隐私的常见问题解答。[阅读更多](../../platform/using/privacy-faq.md)

### 2020 年 10 月 {#oct-2020}

**20.3 版本中包含的新功能**

iOS 的推送通知改进 - [阅读更多](../../delivery/using/configuring-the-mobile-application.md)

Android 的推送通知改进 - [阅读更多](../../delivery/using/configuring-the-mobile-application-android.md)

**随版本提供的其他文档更新**

兼容性矩阵已更新。[阅读更多](../../rn/using/compatibility-matrix.md)

更新了已弃用和已删除的功能页面。[阅读更多](../../rn/using/deprecated-features.md)

的发行说明和兼容性矩阵 [!DNL Gold Standard] 现在，可在专用页面中使用该版本。
[阅读更多](../../rn/using/gold-standard.md)。

最初基于 oAUTH 身份验证设置来访问管道的 Triggers 集成现已更改并移至 Adobe I/O。[阅读更多](../../integrations/using/configuring-adobe-io.md)

**其他更新**

已更新文档页面，以反映 Tomcat 8 更新。

已在“获取 Adobe Campaign 版本”部分的“关于”框说明中添加了详细信息。[阅读更多](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

已向“更新 Adobe Campaign Classic”部分中添加了执行内部版本升级的准则。阅读更多 [阅读更多](../../production/using/build-upgrade.md)

已向 Campaign 常见问题部分中添加了关于 Campaign 内部版本升级的常见问题解答。阅读更多 [阅读更多](../../platform/using/faq-build-upgrade.md)

现在，在专用部分中对 Campaign 本地、托管和混合托管模型进行说明。[阅读更多](../../installation/using/hosting-models.md)

已在《安装指南》中更新并移动每个托管模型的 Campaign 功能矩阵。[阅读更多](../../installation/using/capability-matrix.md)

“Campaign 报告高级功能”部分已得到改进，以详细说明如何在自定义报告中使用 URL 参数和变量。[阅读更多](../../reporting/using/advanced-functionalities.md)

报告属性页面已重组并进行了丰富，以促进配置。[阅读更多](../../reporting/using/properties-of-the-report.md)

已使用有关如何从旧版二进制协议迁移到基于 HTTP/2 的 APNs 提供程序 API 的详细信息来创建新的技术说明。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/migrate-to-apns-http2.html)

### 2020 年 9 月 {#september-2020}

已添加注释来指定“有效用户档案”计数仅适用于营销实例。[阅读更多](../../platform/using/about-profiles.md#active-profiles)

已添加有关模式版本的新示例来将字段链接到现有引用表。[阅读更多](../../configuration/using/examples-of-schemas-edition.md#uc-link)

已添加关于在投放中对种子地址使用额外数据的说明。[阅读更多](../../delivery/using/creating-seed-addresses.md#defining-addresses)

### 2020 年 8 月 {#aug-2020}

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

**[!UICONTROL AND-join]** 活动部分已使用有关其使用情况的更多信息以及关于变量的使用说明进行了扩充。[阅读更多](../../workflow/using/and-join.md)

### 2020 年 7 月 {#july-2020}

已向工作流用例中添加了有关如何使用增量查询自动更新列表的用例。[阅读更多](../../workflow/using/about-workflow-use-cases.md)

[发行说明](../../rn/using/latest-release.md)已重组：添加了[概述页面](../../rn/using/latest-release.md)，其中包含有关生成状态、升级过程、建议和重要链接的信息。此外，还添加了 [[!DNL Gold Standard]  版本](../../rn/using/gold-standard.md)的专门页面，并集成了[兼容性矩阵](../../rn/using/compatibility-matrix.md)。

已添加新部分，其中包含与 Campaign Classic 监控相关的准则。[阅读更多](../../production/using/monitoring-guidelines.md)

“隐私和同意”部分已得到增强，其中包含更多详细信息和有用的链接。[阅读更多](../../platform/using/privacy-and-recommendations.md)

“Campaign Classic 中的隐私管理”页面已更新，其中包含有关“规定”字段的信息，现在在使用允许设置自动隐私请求流程的 API 时，该字段可用。[阅读更多](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

“隐私管理概述”页面已更新，包含有关泰国的个人数据保护法 (PDPA) 和巴西的 Lei Geral de Proteção de Dados(LGPD) 的信息。[阅读更多](../../platform/using/privacy-and-recommendations.md)

添加了有关子工作流日志和行为的信息，以防出错。[阅读更多](../../workflow/using/sub-workflow.md)

已在 **[!UICONTROL Scheduler]** 活动部分中添加最佳实践。[阅读更多](../../workflow/using/scheduler.md)

### 2020 年 6 月 {#june-2020}

更新了“删除隔离地址”部分。这包括明确了地址会自动从隔离列表中删除的情况。[阅读更多](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

在如何使用控制面板和活动工作流[加密](../../platform/using/zip-encrypt.md)和[解密](../../platform/using/unzip-decrypt.md)数据方面添加了用例。

Experience Cloud Triggers 和 Adobe Campaign Classic 集成页面已移至[此处](../../integrations/using/about-triggers.md)。

### 2020 年 7 月 {#release-20-2}

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

### 2020 年 5 月 {#may-2020}

“监视投放能力”部分已移动和改进。[阅读更多](../../delivery/using/monitoring-deliverability.md)

“投放能力”疑难解答部分已移动和改进。[阅读更多](../../delivery/using/deliverability-faq.md)

启动新平台时的可投放性指导原则经过了改进。[阅读更多](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans#transition-process)

已移动并更新“发送带有附件的事务电子邮件”部分。[阅读更多](../../message-center/using/transactional-email-with-attachments.md)

数据包最佳实践部分已移动并更新。[阅读更多](../../platform/using/working-with-data-packages.md#data-package-best-practices)

### 2020 年 4 月 {#april-2020}

联合数据访问 (FDA) 权限表已移至访问外部数据库 (FDA) 文档。[阅读更多](../../installation/using/remote-database-access-rights.md)

常见问题解答已更新，其中包含有关如何清除软缓存和硬缓存的提示。[阅读更多](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

数据模型最佳实践已得到改进，并添加了有关索引的更多信息。[阅读更多](../../configuration/using/data-model-best-practices.md#indexes)

描述 Adobe Campaign 内置数据模型的部分已更新，每个表中都有更多详细信息。[阅读更多](../../configuration/using/data-model-description.md)

工作流用例已更新并重新组织为主题部分。[阅读更多](../../workflow/using/about-workflow-use-cases.md)

[弹回邮件资格](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) 和[电子邮件管理规则](../../delivery/using/understanding-delivery-failures.md#email-management-rules)部分已改进并增加了更新的信息。

Adobe Campaign 增强 MTA 文章已更新。现在只适用于 Campaign Classic。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html)

### 2020 年 3 月 {#march-2020}

数据模型最佳实践已更新新的部分，包括[序列](../../configuration/using/data-model-best-practices.md#sequences)性能[和](../../configuration/using/data-model-best-practices.md#performance) 大表 [](../../configuration/using/data-model-best-practices.md#large-tables)。[阅读更多](../../configuration/using/data-model-best-practices.md)

现在提供了描述 Adobe Campaign 内置数据模型和表之间交互的新部分。[阅读更多](../../configuration/using/data-model-description.md)

其他关键链接已添加到文档主页。[阅读更多](../../campaign-classic-home.md)

已添加一个用例，说明如何将动态优惠从 Adobe Target 集成到 Adobe Campaign 的电子邮件中。[阅读更多](../../integrations/using/inserting-a-dynamic-image.md)

现在提供了详细介绍 Adobe Campaign 中不同语言的新部分。[阅读更多](../../platform/using/adobe-campaign-workspace.md#languages)

访问管理指南已更新，其中包含有关已命名权限的更多信息。[阅读更多](../../platform/using/access-management-named-rights.md)

### 2020 年 2 月 {#february-2020}

现在提供概述设计 Adobe Campaign 数据模型时最佳实践和主要建议的新部分。[阅读更多](../../configuration/using/data-model-best-practices.md)

新增了有关技术电子邮件配置的部分。[阅读更多](../../installation/using/email-deliverability.md)

“投放能力常见问题解答”已更新，其中包含有关“满足配额”错误消息的更多详细信息。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-deliverability-faq.html#FAQ)

新的电子邮件提供商现在支持 AMP for Email：相关文档已更新。[阅读更多](../../delivery/using/defining-interactive-content.md)

电子邮件存档部分已得到改进。[阅读更多](../../installation/using/email-archiving.md#recommendations-and-limitations)

### 2020 年 1 月 {#release-20-1}

**20.1 版本中包含的新功能**

Snowflake FDA 连接器 - [阅读更多](../../installation/using/configure-fda-snowflake.md)

Hadoop FDA 连接器增强 - [阅读更多](../../installation/using/configure-fda-hadoop.md)

**随版本提供的其他文档更新**

[安装、](../../installation/using/general-architecture.md) [生产](../../production/using/foreword.md)[和配置](../../configuration/using/additional-parameters.md)指南已更新，包含 nlserver 服务启动使用的新系统单元。您仍可以使用 /etc/init.d/nlserver6，但 Adobe 建议您现在使用 systemctl 命令与 nlserver 服务进行交互。

安装指南已更新并与最新版本的兼容性矩阵同步。新增了支持的系统。已弃用和不支持的系统的实例已被删除。[阅读更多](../../installation/using/general-architecture.md)

更新了兼容性矩阵，纳入 Hadoop 3.0 和 Snowflake FDA 连接器。[阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

安装指南中添加了有关 IP 关联的最佳实践。[阅读更多](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

数据库清理工作流部分已更新。现在提供的批处理数字反映代码实现。[阅读更多](../../production/using/database-cleanup-workflow.md)

事务性消息传递指南中增加了对 HTTP 联合数据访问的限制。[阅读更多](../../production/using/database-cleanup-workflow.md)

新选项中添加了信息，允许您为&#x200B;**[!UICONTROL JavaScript code]**&#x200B;和 **[!UICONTROL Advanced JavaScript code]**&#x200B;工作流活动定义超时期限。[阅读更多](../../workflow/using/sql-code-and-javascript-code.md)

在 **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** 节点的新 **[!UICONTROL Start Pending]** 视图中添加了信息。[阅读更多](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

移动、重新组织和改进了[发送推送通知](../../delivery/using/about-mobile-app-channel.md)指南，提供了澄清信息。

[此处](../../reporting/using/properties-of-the-report.md#defining-additional-settings)记录了 URL 报告配置的新参数。

**Campaign Classic 本地和托管功能矩阵**&#x200B;页面已更新新的 FDA 连接器。[阅读更多](../../installation/using/capability-matrix.md)。

**Campaign Classic 功能矩阵**&#x200B;页面已更新。[阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

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

## 2019

### 2019 年 12 月 {#december-2019}

“WdbcOptions_TempDbName”选项已添加到 Campaign 选项的列表。[阅读更多](../../installation/using/configuring-campaign-options.md)

FDA 矩阵页面已移到[此处](../../installation/using/remote-database-access-rights.md)。

“访问权限矩阵”页面已移到[此处](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)。

描述如何使用 AMP 定义交互式内容的部分已被移动。[阅读更多](../../delivery/using/defining-interactive-content.md)

**19.2 版本中包含的新功能**

加利福尼亚消费者隐私法 (CCPA) - [阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)

使用 AMP 定义交互式内容 - [阅读更多](../../delivery/using/defining-interactive-content.md)

工作流实时监视 - [阅读更多](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

安全 SMS 消息 (TLS) - [阅读更多](https://helpx.adobe.com/cn/campaign/kb/sms-connector-protocol-and-settings.html)

**随版本提供的其他文档更新**

Adobe Campaign 增强 MTA 文档现已可用。[阅读更多](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

增加了新的部分，介绍如何对活动中保持“尽快启动”状态的工作流进行故障排除。[阅读更多](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

新的“NmsOperation_DeliveryPreparationWindow”和“WdbcKillSessionPolicy”选项已添加到 Campaign 选项列表中。[阅读更多](../../installation/using/configuring-campaign-options.md)

现在提供了描述 Adobe Campaign Classic 数据模型基础知识的新文档。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-datamodel.html)

投放属性中新的&#x200B;**最大个性化运行时间**&#x200B;选项记录于[此部分](../../delivery/using/personalization-fields.md#timing-out-personalization)。

更新了使用 **HttpServletRequest** 与 logon() 和 query() 的示例。[阅读更多](../../configuration/using/web-service-calls.md)。

在模式定义中添加了&#x200B;**sqlDefault** 属性的建议。[阅读更多](../../configuration/using/schema/attribute.md)).

Adobe Campaign 与 Adobe 实时客户数据平台之间的集成现在在&#x200B;**“与 Adobe Experience Cloud 集成”**&#x200B;指南中提到。[阅读更多](../../integrations/using/about-campaign-integrations.md)。

### 2019 年 11 月 {#november-2019}

在[多路复用中间源服务器](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server)和[和支持多个控制实例](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances)部分中添加了一个警告，提到完全托管和混合客户端不支持这些部署。

增加了新的部分，用于说明如何在发送电子邮件时强制使用字符编码。[阅读更多](../../delivery/using/sending-messages.md#character-encoding)

“访问管理”部分已更新&#x200B;**隐私数据权限**。[阅读更多](../../platform/using/access-management-named-rights.md)

添加了信息，以指定个性化字段内容不能超过 1024 个字符。[阅读更多](../../delivery/using/personalization-fields.md)

控制面板文档已集成到新的协作文档集中。[阅读更多](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)

投放最佳实践快速入门指南已更新。[阅读更多](../../delivery/using/delivery-best-practices.md)

### 2019 年 10 月 {#october-2019}

Campaign 的错误消息列表已更新。[阅读更多](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=zh-Hans)

GDPR 入门指南已得到改进和丰富。它现在是包括 GDPR 和 CCPA 在内的隐私管理文档。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/campaign-privacy.html)

在 Campaign Classic 中新增了用户跟踪的故障排除页面。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/classic-tracking-troubleshooting.html)。

新增了 Adobe Analytics Connector 的最佳实践页面。[阅读有关 Adobe Analytics Connector 的更多信息](../../platform/using/adobe-analytics-connector.md)

投放最佳实践快速入门指南已移动并更新。[阅读更多](../../delivery/using/delivery-best-practices.md)

已向 SMS 渠道文档添加了建议，以避免在使用具有相同提供者帐户的扩展通用 SMPP 连接器的多个外部帐户时出现问题。[阅读更多](../../delivery/using/sms-set-up.md#automatic-reply)

在调度程序活动文档中添加了有关如何防止同时执行工作流的信息。[阅读更多](../../workflow/using/scheduler.md)

在文档中添加了配置本地安装的收件箱呈现的步骤。[阅读更多](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

### 2019 年 9 月 {#september-2019}

添加了新页面，以提供维护 Campaign Classic 的一般准则。[阅读更多](../../production/using/monitoring-guidelines.md)

与工作流监测有关的信息已集中到新的专设部分。[阅读更多](../../workflow/using/monitoring-workflow-execution.md)。

已添加有关 Adobe Campaign Classic 中跟踪的一般准则的新页面。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-tracking.html)。

已更新工作流和投放性能改进的最佳实践。[阅读有关工作流的更多信息](../../workflow/using/workflow-best-practices.md) ， [以及有关投放的更多信息](../../delivery/using/delivery-performances.md#best-practices-performance)。

### 2019 年 5 月 {#release-19-1}

**19.1 版本中包含的新功能**

控制面板 - [阅读更多](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)

审核跟踪 - [阅读更多](../../production/using/audit-trail.md)

**随版本提供的其他文档更新**

已创建新的版本升级常见问题解答。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/build-upgrade-faq.html)

[兼容性矩阵](compatibility-matrix.md)已更新。更新了支持的列表库系统，以及 Android/iOS 版本和相关 SDK。已存档 19.0 兼容性矩阵。

“Campaign Classic 中已弃用和已删除的功能”页面已更新。[阅读更多](deprecated-features.md)

《安装指南》中添加了服务器配置文件的说明。[阅读更多](../../installation/using/the-server-configuration-file.md)

添加了介绍托管和混合型号的安装和配置步骤的部分。[阅读更多](../../installation/using/hosting-models.md)

添加了描述 Campaign 服务器卸载步骤的部分。[阅读更多](../../installation/using/uninstalling-campaign.md)

[安全性](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)、 [投放能力](../../delivery/using/about-deliverability.md)和 [隐私](../../platform/using/privacy-management.md)入门指南已更新。

预处理工作流选项的描述已更新，以反映产品更改。[阅读更多](../../workflow/using/data-loading--file-.md)

Marketing Cloud 触发器技术说明已更新。[阅读更多](../../integrations/using/about-triggers.md)

错误消息的列表已更新。[阅读更多](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html)

添加了有关事务消息的 SOAP 身份验证方法的更多信息。[阅读更多](../../message-center/using/event-description.md)

Apache 配置步骤已更新。[阅读更多](../../installation/using/integration-into-a-web-server-for-linux.md)

添加了包含 Classic 的端点列表的新页面。[阅读更多](../../installation/using/campaign-network-endpoints.md)

数据包最佳实践文章已更新。[阅读更多](../../configuration/using/data-model-best-practices.md)

“管理优惠”文档已更新，其中新增了列出最佳实践的部分。[阅读更多](../../interaction/using/interaction-best-practices.md)

已创建一篇关于在 Adobe Campaign Classic 中使用优惠目录的新知识库文章。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/offer-best-practices.html)

子工作流活动部分新增了使用示例。[阅读更多](../../workflow/using/sub-workflow.md)

[Campaign Classic 本地和托管功能矩阵](../../installation/using/capability-matrix.md)页面已更新，其中包含与电子邮件密件抄送相关的信息。

事务性消息文档已更新，包含有关模板发布的说明。[阅读更多](../../message-center/using/publishing-message-templates.md#template-publication)

“未处理的弹回邮件”部分已更新，其中包含有关“转发地址”和“错误地址”字段的更多详细信息。[阅读更多](../../installation/using/deploying-an-instance.md)

新增了有关工作流计划最佳实践的部分。[阅读更多](../../workflow/using/workflow-best-practices.md)

为 Campaign 选项列表增加了两个新选项：XtkSecurity_Restrict_EditXML 和 NmsOperation_OperationMgtDebug。
[阅读更多](../../installation/using/configuring-campaign-options.md)

添加了有关 Campaign Classic 中可用的不同外部帐户以及如何配置这些帐户的信息。
[阅读更多](../../installation/using/external-accounts.md)

更新了 Analytics Connector 部分以反映接口更改。
[阅读更多](../../platform/using/adobe-analytics-connector.md)

添加了有关计费报告的信息。
[阅读更多](../../production/using/monitoring-processes.md)

更新了有关共享受众集成的文档。
[阅读更多](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)

以下技术已更新：[SMS 连接器协议和设置](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)以及[序列自动生成](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)。

技术工作流部分已更新。[阅读更多](../../workflow/using/about-technical-workflows.md)

Campaign 域名设置程序已得到改进和更新。

Android 应用程序从 Google Cloud Messaging (GCM) 到 Firebase Cloud Messaging (FCM) 的迁移过程已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/migrate-to-fcm.html)

Campaign 硬件大小调整指南已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html)

添加了关于 Teradata 外部帐户查询分段的信息。[阅读更多](../../installation/using/external-accounts.md)

### 2019 年 1 月{#release-doc-16-01-2019}

Marketing Cloud 触发器技术说明已更新。[阅读更多](../../integrations/using/about-triggers.md)

在优惠批准部分添加了注释，以指定“已批准内容”提及指示内容批准流程已完成，无论是否已启用/批准所有优惠。[阅读更多](../../interaction/using/offer-catalog-overview.md)

在《安装指南》中添加了新部分，其中列出了“管理/平台/选项”节点中的选项。[阅读更多](../../installation/using/configuring-campaign-options.md)

添加了有关使用种子地址保护邮寄列表的信息。[阅读更多](../../delivery/using/creating-seed-addresses.md)

创建和发送投放时的关键步骤已重新分组到新部分，并提供了在需要时可参考的各种渠道。[阅读更多](../../delivery/using/steps-about-delivery-creation-steps.md)

[电子邮件归档](../../installation/using/email-archiving.md)部分已进行了移动、重新组织并增加了阐明信息：

* 已添加有关每个连接的电子邮件和密送 IP 参数的最佳实践。

* 如果您已经在使用旧版本（Adobe Campaign 17.2 – 版本 8795 之前）的电子邮件归档，我们更新了升级到新电子邮件归档系统（密送）的步骤。

在《使用工作流实现自动化》指南中添加了一个用例：向运营商发送个性化提醒。[阅读更多](../../workflow/using/sending-personalized-alerts-to-operators.md)

“迁移到新版本”部分已更新。文档现在只详细介绍了从任何旧版本迁移到 Adobe Campaign Classic v7 的步骤，因为现在已不再可能迁移到 Adobe Campaign v6.11。[阅读更多](../../migration/using/about-migration.md)

对“投放临时失败后的重试”部分进行了阐明。[阅读更多](../../delivery/using/understanding-delivery-failures.md)

指向“数字内容编辑器”部分的链接已添加到“定义电子邮件内容”部分。[阅读更多](../../delivery/using/defining-the-email-content.md)

“事务性消息架构”部分已更新，并显示一条警告，指定控件和执行实例不能安装在同一台计算机上。[阅读更多](../../message-center/using/transactional-messaging-architecture.md)

“工作流监视”部分已更新，其中包含 8700 到 8977 (18.10) 版本的说明，包括有关如何为这些版本安装 Workflow HeatMap 包的技术说明的链接。[阅读更多](../../workflow/using/heatmap.md)

添加了一个用例，说明如何使用工作流中的扩充活动发送包含自定义数据字段的电子邮件。[阅读更多](../../workflow/using/email-enrichment-with-custom-date-fields.md)

功能视频已移到[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)。
