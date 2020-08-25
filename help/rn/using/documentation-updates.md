---
title: Adobe Campaign经典文档更新
description: 本页列出了每个 Adobe Campaign Classic 版本的所有新增功能和文档更新。
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 70efc8a7f1fab68d73e36b4373116c4aaaa0af5d
workflow-type: tm+mt
source-wordcount: '7164'
ht-degree: 94%

---


# 文档更新{#documentation-updates}

本页列出了每月所有新增功能和文档更新以及 Campaign 版本。

您还可以查阅 [Adobe Campaign Classic Release 发行说明](../../rn/using/latest-release.md) ，了解更多更新信息。

## 2020 年 8 月 {#aug-2020}

通过专门的章节了解与投放设计和与活动一起发送相关的最佳实践。 [阅读更多](../../delivery/using/delivery-best-practices.md)

改进了“交付能力”最佳做法登陆页，以便访问各分节。 [阅读更多](../../delivery/using/deliverability-key-points.md)

操作方法视频现在可用于以下主题：

* [如何利用类型规则和预定义过滤器建立疲劳管理](../../campaign/using/about-campaign-typologies.md)

* [如何在活动中创建电子邮件](../../campaign/using/marketing-campaign-deliveries.md)

* [如何创建包含条件内容的多语言新闻稿](../../delivery/using/conditional-content.md)

* [如何配置和部署投放模板](../../delivery/using/creating-a-delivery-template.md)

* [如何激活和使用AMP处理电子邮件](../../delivery/using/defining-interactive-content.md)

* [如何使用动态内容块个性化电子邮件](../../delivery/using/personalization-blocks.md)

* [如何使用个性化字段个性化电子邮件](../../delivery/using/personalization-fields.md)

* [如何在电子邮件中管理种子和验证](../../delivery/using/steps-defining-the-target-population.md)

* [如何设置重复投放](../../workflow/using/recurring-delivery.md)

* [如何设置连续投放](../../workflow/using/continuous-delivery.md)

在连接到FTP服务器后，收到“无法解析主机名”错误时，要执行的检查和操作中已添加信息。 [阅读更多](../../platform/using/sftp-server-usage.md)

在工作流用例的列表中引用了 [新的用例](../../workflow/using/about-workflow-use-cases.md):

* 内容创建、编辑和发布自动化
* 在发送收件人之前设置投放批准流程
* 在查询中调用实例变量
* 对人口应用分解百分比

活动 **[!UICONTROL AND-join]** 一节已丰富了关于其使用情况的更多信息，并有关于变量使用情况的说明。 [阅读更多](../../workflow/using/and-join.md)

## 2020 年 7 月 {#july-2020}

一个关于如何使用增量列表自动更新查询的用例已添加到工作流用例中。 [阅读更多](../../workflow/using/about-workflow-use-cases.md)

“发 [行说明](../../rn/using/latest-release.md) ”已重新组织：已添 [加概述页](../../rn/using/latest-release.md) ，其中包含有关构建状态、升级过程、建议和重要链接的信息。 此外，还添加了 [Gold Standard版本](../../rn/using/gold-standard.md) 的专用页面，并集 [成了兼容性](../../rn/using/compatibility-matrix.md) 矩阵。

新增了一节，其中载有与Campaign Classic监测相关的准则。 [阅读更多](../../production/using/monitoring-guidelines.md)

“隐私和同意”部分已得到增强，其中包含更详细的信息和有用的链接。 [阅读更多](../../platform/using/privacy-and-recommendations.md)。

“Campaign Classic中的隐私管理”页面已更新，其中包含有关“规定”字段的信息，现在在使用允许设置自动隐私请求流程的API时，该字段可用。 [阅读更多](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

隐私管理概述页面已更新，以包含有关泰国个人数据保护法(PDPA)和巴西Lei Geral de Proteção de Dados(LGPD)的信息。 [阅读更多](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

已在子工作流日志和行为中添加信息，以防出错。 [阅读更多](../../workflow/using/sub-workflow.md)

最佳实践已添加到“ **[!UICONTROL Scheduler]** 活动”部分。 [阅读更多](../../workflow/using/scheduler.md)

## 2020 年 6 月 {#june-2020}

更新了“删除隔离地址”部分。这包括明确了地址会自动从隔离列表中删除的情况。[阅读更多](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

在如何使用控制面板和活动工作流[加密](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt)和[解密](../../workflow/using/importing-data.md#use-case-gpg-decrypt)数据方面添加了用例。

“白名单”和“黑名单”术语已从 Adobe Campaign 文档中删除。这些术语可能还会出现在产品 UI、选项名称和内部代码中，但将在即将发布的 Campaign 版本中替换为“阻止列表”和“允许列表”。

The Experience Cloud Triggers and Adobe Campaign Classic integration page has been moved [here](../../integrations/using/about-triggers.md).

## 20.2 - 08/06/2020{#release-20-2}

**此版本中包含的新功能**

支持表情符号 - [阅读更多](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA 连接器 - [阅读更多](../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse)

泰国和巴西隐私法 - [阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**随版本提供的其他文档更新**

[此部分](../../message-center/using/template-unpublication.md)介绍了用于取消发布事务性消息模板的新选项。

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

启动新平台时的投放能力部分指南已得到改进。[阅读更多](../../delivery/using/starting-new-platform.md)

已移动并更新“发送带有附件的事务电子邮件”部分。[阅读更多](../../message-center/using/transactional-email-with-attachments.md)

数据包最佳实践部分已移动并更新。[阅读更多](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## 2020 年 4 月 {#april-2020}

联合数据访问 (FDA) 权限表已移至访问外部数据库 (FDA) 文档。[阅读更多](../../platform/using/remote-database-access-rights.md)

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

访问管理指南已更新，其中包含有关已命名权限的更多信息。[阅读更多](../../platform/using/access-management.md#named-rights)

## 2020 年 2 月 {#february-2020}

现在提供概述设计 Adobe Campaign 数据模型时最佳实践和主要建议的新部分。[阅读更多](../../configuration/using/data-model-best-practices.md)

新增了有关技术电子邮件配置的部分。[阅读更多](../../installation/using/email-deliverability.md)

“投放能力常见问题解答”已更新，其中包含有关“满足配额”错误消息的更多详细信息。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-deliverability-faq.html#FAQ)

新的电子邮件提供商现在支持 AMP for Email：相关文档已更新。[阅读更多](../../delivery/using/defining-interactive-content.md)

电子邮件存档部分已得到改进。[阅读更多](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 20.1 - 17/02/2020{#release-20-1}

**此版本中包含的新功能**

Snowflake FDA 连接器 - [阅读更多](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Hadoop FDA 连接器增强 - [阅读更多](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**随版本提供的其他文档更新**

[安装、](../../installation/using/before-reading.md) [生产](../../production/using/foreword.md)[和配置](../../configuration/using/additional-parameters.md)指南已更新，包含 nlserver 服务启动使用的新系统单元。您仍可以使用 /etc/init.d/nlserver6，但 Adobe 建议您现在使用 systemctl 命令与 nlserver 服务进行交互。

安装指南已更新并与最新版本的兼容性矩阵同步。新增了支持的系统。已删除已弃用和不支持的系统的实例。[阅读更多](../../installation/using/before-reading.md)

更新了兼容性矩阵，纳入 Hadoop 3.0 和 Snowflake FDA 连接器。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

安装指南中添加了有关 IP 关联的最佳实践。[阅读更多](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

数据库清理工作流部分已更新。现在提供的批处理数字反映代码实现。[阅读更多](../../production/using/database-cleanup-workflow.md)

事务性消息传递指南中增加了对 HTTP 联合数据访问的限制。[阅读更多](../../production/using/database-cleanup-workflow.md)

新选项中添加了信息，允许您为&#x200B;**[!UICONTROL JavaScript code]**&#x200B;和 **[!UICONTROL Advanced JavaScript code]**&#x200B;工作流活动定义超时期限。[阅读更多](../../workflow/using/sql-code-and-javascript-code.md)

在 **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** 节点的新 **[!UICONTROL Start Pending]** 视图中添加了信息。[阅读更多](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

移动、重新组织和改进了[发送推送通知](../../delivery/using/about-mobile-app-channel.md)指南，提供了澄清信息。

[此处](../../reporting/using/properties-of-the-report.md#defining-additional-settings)记录了 URL 报告配置的新参数。

**Campaign Classic 本地和托管功能矩阵**&#x200B;页面已更新新的 FDA 连接器。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-on-prem-vs-hosted.html)

**Campaign Classic 功能矩阵**&#x200B;页面已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

新的&#x200B;**[!UICONTROL Cleanup of Nmsaddress]**&#x200B;工作流记录在[此处](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress)。

添加了在工作流中使用查询活动时的限制。[阅读更多](../../workflow/using/query.md)。

新增了一个部分，以详细描述增强的电子邮件地址验证规则，以便在发生软错误时发送隔离地址。[阅读更多](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

配置文件中表明实例是否正在使用增强的 MTA 的参数现予以记录。[阅读更多](../../installation/using/the-server-configuration-file.md#mta)

## 2020 年 1 月 {#january-2020}

“投放能力”部分进行了移动、重新组织和增加了更新的内容。[阅读更多](../../delivery/using/about-deliverability.md)

现在提供了新的部分，介绍 Adobe Campaign Classic 数据模型基础知识以及如何访问每个表的说明。[阅读更多](../../configuration/using/about-data-model.md)

Adobe Campaign 增强 MTA 文章已更新，其中包含有关在未向每封邮件添加所需增强 MTA 头的实例上安装特定 Typology 包的详细信息。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

与查询设计相关的用例已重新组织为单独的部分。[阅读更多](../../workflow/using/querying-recipient-table.md)

增加了有关管理优惠和使用 Adobe Campaign Classic 中的交互模块的提示和技巧的新部分。[阅读更多](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

“交互”文档中增加了指向多个视频的链接，这些视频有助于更好地了解如何管理优惠。[阅读更多](../../interaction/using/interaction-and-offer-management.md)

有关如何优化实例上运行的查询的最佳实践文章已集成到文档中。[阅读更多](../../workflow/using/query.md#optimizing-queries)

报告指南已更新并重新组织。[阅读更多](../../reporting/using/about-adobe-campaign-reporting-tools.md)

已添加如何在工作流中使用实例变量的示例。[阅读更多](../../workflow/using/javascript-scripts-and-templates.md)

## 2019 年 12 月 {#december-2019}

“WdbcOptions_TempDbName”选项已添加到 Campaign 选项的列表。[阅读更多](../../installation/using/configuring-campaign-options.md)

FDA 矩阵页面已移到[此处](../../platform/using/remote-database-access-rights.md)。

“访问权限矩阵”页面已移到[此处](https://docs.adobe.com/content/help/zh-Hans/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf)。

描述如何使用 AMP 定义交互式内容的部分已被移动。[阅读更多](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**此版本中包含的新功能**

加利福尼亚消费者隐私法 (CCPA) - [阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)

使用 AMP 定义交互式内容 - [阅读更多](../../delivery/using/defining-interactive-content.md)

工作流实时监视 - [阅读更多](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

安全 SMS 消息 (TLS) - [阅读更多](https://helpx.adobe.com/cn/campaign/kb/sms-connector-protocol-and-settings.html)

**随版本提供的其他文档更新**

Adobe Campaign 增强 MTA 文档现已可用。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html)

增加了新的部分，介绍如何对活动中保持“尽快启动”状态的工作流进行故障排除。[阅读更多](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

新的“NmsOperation_DeliveryPreparationWindow”和“WdbcKillSessionPolicy”选项已添加到 Campaign 选项列表中。[阅读更多](../../installation/using/configuring-campaign-options.md)

现在提供了描述 Adobe Campaign Classic 数据模型基础知识的新文档。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-datamodel.html)

投放属性中新的&#x200B;**最大个性化运行时间**&#x200B;选项记录于[此部分](../../delivery/using/personalization-fields.md#timing-out-personalization)。

更新了使用 **HttpServletRequest** 与 logon() 和 query() 的示例。[阅读更多](../../configuration/using/web-service-calls.md)。

在模式定义中添加了&#x200B;**sqlDefault** 属性的建议。[阅读更多](../../configuration/using/elements-and-attributes.md#attribute-description)。

Adobe Campaign 与 Adobe 实时客户数据平台之间的集成现在在&#x200B;**“与 Adobe Experience Cloud 集成”**&#x200B;指南中提到。[阅读更多](../../integrations/using/about-campaign-integrations.md)。

## 2019 年 11 月{#november-2019}

在[多路复用中间源服务器](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server)和[和支持多个控制实例](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances)部分中添加了一个警告，提到完全托管和混合客户端不支持这些部署。

增加了新的部分，用于说明如何在发送电子邮件时强制使用字符编码。[阅读更多](../../delivery/using/sending-messages.md#character-encoding)

“访问管理”部分已更新&#x200B;**隐私数据权限**。[阅读更多](../../platform/using/access-management.md#named-rights)

添加了信息，以指定个性化字段内容不能超过 1024 个字符。[阅读更多](../../delivery/using/personalization-fields.md)

控制面板文档已集成到新的协作文档集中。[阅读更多](https://docs.adobe.com/content/help/zh-Hans/control-panel/using/control-panel-home.html)

投放最佳实践快速入门指南已更新。[阅读更多](../../delivery/using/delivery-best-practices.md)

## 2019 年 10 月 {#october-2019}

Campaign Standard 和 Campaign Classic 的错误消息列表已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

GDPR 入门指南已得到改进和丰富。它现在是包括 GDPR 和 CCPA 在内的隐私管理文档。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/campaign-privacy.html)

在 Campaign Classic 中新增了用户跟踪的故障排除页面。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/classic-tracking-troubleshooting.html)。

新增了 Adobe Analytics 数据连接器的最佳实践页面。[阅读有关 Adobe Analytics 数据连接器的更多信息](../../platform/using/adobe-analytics-data-connector.md)

投放最佳实践快速入门指南已移动并更新。[阅读更多](../../delivery/using/delivery-best-practices.md)

已向 SMS 渠道文档添加了建议，以避免在使用具有相同提供者帐户的扩展通用 SMPP 连接器的多个外部帐户时出现问题。[阅读更多](../../delivery/using/sms-channel.md#automatic-reply)

在调度程序活动文档中添加了有关如何防止同时执行工作流的信息。[阅读更多](../../workflow/using/scheduler.md)

在文档中添加了配置本地安装的收件箱呈现的步骤。[阅读更多](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## 2019 年 9 月 {#september-2019}

添加了新页面，以提供维护 Campaign Classic 的一般准则。[阅读更多](../../production/using/monitoring-guidelines.md)

与工作流监测有关的信息已集中到新的专设部分。[阅读更多](../../workflow/using/monitoring-workflow-execution.md)。

已添加有关 Adobe Campaign Classic 中跟踪的一般准则的新页面。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-tracking.html)。

已更新工作流和投放性能改进的最佳实践。[阅读有关工作流的更多信息](../../workflow/using/workflow-best-practices.md) ， [以及有关投放的更多信息](../../delivery/using/monitoring-a-delivery.md#best-practices-performance)。

## 19.1 - 30/05/2019{#release-19-1}

**此版本中包含的新功能**

控制面板 - [阅读更多](https://docs.adobe.com/content/help/zh-Hans/control-panel/using/control-panel-home.html)

审核跟踪 - [阅读更多](../../production/using/audit-trail.md)

**随版本提供的其他文档更新**

已创建新的版本升级常见问题解答。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/build-upgrade-faq.html)

[兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)已更新。更新了支持的列表库系统，以及 Android/iOS 版本和相关 SDK。已存档 [19.0 兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix-19-0.html)。

“Campaign Classic 中已弃用和已删除的功能”页面已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/deprecated-and-removed-features.html)

《安装指南》中添加了服务器配置文件的说明。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

添加了介绍托管和混合型号的安装和配置步骤的部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

添加了描述 Campaign 服务器卸载步骤的部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

[安全性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)、 [投放能力](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)和 [隐私](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)入门指南已更新。

预处理工作流选项的描述已更新，以反映产品更改。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

Marketing Cloud 触发器技术说明已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/triggers-and-campaign.html)

错误消息的列表已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

添加了有关事务消息的 SOAP 身份验证方法的更多信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Apache 配置步骤已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

添加了新页面，包括 Campaign Standard 和 Classic 的端点列表。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/campaign-endpoints.html)

数据包最佳实践文章已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/data-package-best-practices.html)

“管理优惠”文档已更新，其中新增了列出最佳实践的部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

已创建一篇关于在 Adobe Campaign Classic 中使用优惠目录的新知识库文章。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/offer-best-practices.html)

子工作流活动部分新增了使用示例。[阅读更多](../../workflow/using/sub-workflow.md)

[Campaign Classic 本地和托管功能矩阵](https://helpx.adobe.com/cn/campaign/kb/acc-on-prem-vs-hosted.html)知识库文章已更新，其中包含与归档电子邮件相关的信息。

事务性消息文档已更新，包含有关模板发布的说明。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

“未处理的弹回邮件”部分已更新，其中包含有关“转发地址”和“错误地址”字段的更多详细信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

新增了有关工作流计划最佳实践的部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

为 Campaign 选项列表增加了两个新选项：XtkSecurity_Restrict_EditXML 和 NmsOperation_OperationMgtDebug。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

添加了有关 Campaign Classic 中可用的不同外部帐户以及如何配置这些帐户的信息。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

更新了 Analytics 数据连接器部分以反映接口更改。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

添加了有关计费报告的信息。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

更新了有关共享受众集成的文档。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

以下技术已更新：[SMS 连接器协议和设置](https://helpx.adobe.com/cn/campaign/kb/sms-connector-protocol-and-settings.html)以及[序列自动生成](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)。

技术工作流部分已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

Campaign 域名设置程序已得到改进和更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/domain-name-delegation.html)

Android 应用程序从 Google Cloud Messaging (GCM) 到 Firebase Cloud Messaging (FCM) 的迁移过程已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/migrate-to-fcm.html)

Campaign 硬件大小调整指南已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html)

添加了关于 Teradata 外部帐户查询分段的信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## 2019 年 1 月{#release-doc-16-01-2019}

Marketing Cloud 触发器技术说明已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/triggers-and-campaign.html)

在优惠批准部分添加了注释，以指定“已批准内容”提及指示内容批准流程已完成，无论是否已启用/批准所有优惠。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

在《安装指南》中添加了新部分，其中列出了“管理/平台/选项”节点中的选项。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

添加了有关使用种子地址保护邮寄列表的信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

创建和发送投放时的关键步骤已重新分组到新部分，并提供了在需要时可参考的各种渠道。[阅读更多](../../delivery/using/steps-about-delivery-creation-steps.md)

[电子邮件归档](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)部分已进行了移动、重新组织并增加了阐明信息：

* 已添加有关每个连接的电子邮件和密送 IP 参数的最佳实践。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* 如果您已经在使用旧版本（Adobe Campaign 17.2 – 版本 8795 之前）的电子邮件归档，我们更新了升级到新电子邮件归档系统（密送）的步骤。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

在《使用工作流实现自动化》指南中添加了一个用例：向运营商发送个性化提醒。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

“迁移到新版本”部分已更新。文档现在只详细介绍了从任何旧版本迁移到 Adobe Campaign Classic v7 的步骤，因为现在已不再可能迁移到 Adobe Campaign v6.11。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

对“投放临时失败后的重试”部分进行了阐明。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

指向“数字内容编辑器”部分的链接已添加到“定义电子邮件内容”部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

“事务性消息架构”部分已更新，并显示一条警告，指定控件和执行实例不能安装在同一台计算机上。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

“工作流监视”部分已更新，其中包含 8700 到 8977 (18.10) 版本的说明，包括有关如何为这些版本安装 Workflow HeatMap 包的技术说明的链接。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

添加了一个用例，说明如何使用工作流中的扩充活动发送包含自定义数据字段的电子邮件。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

功能视频已移到[此处](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html)。

[Teradata](https://helpx.adobe.com/cn/campaign/kb/campaign_fda_teradata.html) 和 [MySQL 5.7](https://helpx.adobe.com/cn/campaign/kb/campaign_fda_mysql.html) 中添加了两项技术说明。

## 18.10 - 05/11/2018{#release-18-10}

**此版本中包含的新功能**

推送通知改进 - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

SQL 数据管理活动 - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

工作流监视 - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**随版本提供的其他文档更新**

Campaign Classic API 现在可在[专用页面](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)中使用。如果您使用的是 jsapi.chm 文件，您现在应该参阅新的在线版本。

兼容性矩阵已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

“Campaign Classic 中已弃用和已删除的功能”页面已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/deprecated-and-removed-features.html)

在[发行说明](https://docs.adobe.com/content/help/zh-Hans/campaign-classic/using/release-notes/latest-release.html)和[旧版发行说明中](https://docs.adobe.com/content/help/zh-Hans/campaign-classic/using/release-notes/latest-release.html)，为召回的版本添加了警告。还增加了 17.9、18.4 和 18.6 的累积版本。

[安全性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)、 [可交付性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)和[构建升级](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)入门指南已更新。

[隐私](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)入门指南已更新，其中包含有关如何在外部调用 API 以及如何使用 queryDef 查询状态和下载 GDPR 文件的信息。

添加了事务性消息使用案例，以便将电子邮件附件快速添加到出站调度。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

更新了连接阈值故障排除部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

添加了有关如何配置代理连接的部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

更新了授权外部命令限制部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

添加了与 SFTP 使用相关的故障排除部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

对《发送邮件》指南的概述部分重新进行了组织。在投放创建全局过程和不同投放类型中添加了信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

错误消息的列表已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

将“如何使用种子地址”部分移至“发送邮件”指南概述一章。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

添加了新的工作流用例：管理同时执行的工作流中的更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

“收件箱呈现”部分已更新，其中包含有关 Litmus 的更多信息和更详细的操作过程。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

“SpamAssassin”部分已得到改进。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

“使用压力规则管理营销疲劳度”部分添加了一个用例。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

提供了一个新的用例，描述如何创建跨渠道投放工作流。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

在“存档电子邮件”部分添加了一些建议。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

新增了关于最小屏幕分辨率的建议，以便实现 Adobe Campaign 的最佳使用。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

Experience Manager 集成指南已更新，并在此集成配置中添加了一些说明。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

添加了有关组类型列表与列表类型列表之间差异的信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

更新了通过电子邮件将报告提取作为附件发送的代码。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

添加了一个示例，说明如何创建查询以过滤过去 7 天内未打开电子邮件的收件人。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

更新了《使用 Adobe Experience Cloud 共享受众》的集成指南。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

常见问题帮助页面现在包含有关 Campaign 可用语言、Web 窗体翻译和多语言电子邮件的信息。[阅读更多](../../platform/using/common-questions.md)

“美式英语”和“英式英语”实例之间的差异现列于专设部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

[常见问题](../../platform/using/common-questions.md)帮助页面现在链接到错误消息页面。

添加了有关“打开”跟踪模式的信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

添加了有关 Web 应用程序和 Web 窗体的最低分辨率的信息。[阅读更多](https://docs.adobe.com/content/help/zh-Hans/campaign-classic/using/designing-content/web-forms/about-web-forms.html)

Campaign 和 Adobe Experience Cloud 解决方案集成指南已更新并重新组织。[阅读更多](../../integrations/using/about-campaign-integrations.md)

添加了有关 Web 窗体中文本变量用法的部分。[阅读更多](https://docs.adobe.com/content/help/zh-Hans/campaign-classic/using/designing-content/web-forms/static-elements-in-a-web-form.html#Using_text_variables)

详细介绍了消息中的 URL 跟踪模式。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

实例创建部分已重新组织。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

现在，在日本手机上发送电子邮件记录在一个新部分中。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

“优化个性化”部分已更新，并提供更多信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**此版本中包含的新功能**

兼容性矩阵已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

JSAPI 文档已更新。[阅读更多](https://support.neolane.net/webApp/extranetLogin)

更新了已弃用和已删除的功能页面。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/deprecated-and-removed-features.html)

**随版本提供的其他文档更新**

Campaign Classic 用户指南已更名，以简化导航和改进用户体验、访问信息和自助服务。[阅读更多](https://docs.adobe.com/content/help/zh-Hans/campaign-classic/using/campaign-classic-home.html)

表达式编辑器中可用函数的列表已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

《安全入门指南》已更新，其中包含有关如何保护包含 PI 的页面的信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

错误消息的列表已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

IMS 集成文档中添加了故障排除部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS._troubleshooting.html)

已更新《版本升级快速入门》指南。[阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)

IP 关联配置部分已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

已添加“性能和吞吐量”故障排除部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

内置个性化块的列表已更新并提供了示例。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

已更新投放故障原因的列表。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

添加了有关包定义管理的新部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

Campaign 与 Adobe Analytics 集成 - 改进并重新组织了数据连接器部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

新增了“教程”部分，其中包含指向分步指南和操作方法视频的链接。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

创建了有关 SMS 连接器协议和设置的新技术说明。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/sms-connector-protocol-and-settings.html)

投放最佳实践快速入门指南已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

已更新具有 Web API 部署的 Microsoft Dynamics 365 帐户配置。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

更新了在 Windows 平台上安装 Adobe Campaign Classic 的过程。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

详细说明了 Adobe Experience Cloud 和 Campaign Classic 之间的受众共享时间范围。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

更新了 Campaign Classic 列表的知识库文章完整版。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/article-list.html)

有关性能改进和最佳实践的新技术现已发布。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/best-practices-for-performance-improvement.html)

A/B 测试范例已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Campaign Classic 常见问题/常见问题解答页面已更新。[阅读更多](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**此版本中包含的新功能**

欧盟一般数据保护规定 (GDPR) - [阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)

活动用户档案 - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Android 推送连接器增强 - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**随版本提供的其他文档更新**

发行说明已改进，以实现更好的用户体验，现在包括所有与客户请求相关的修补程序。[阅读更多](https://docs.adobe.com/content/help/zh-Hans/campaign-classic/using/release-notes/latest-release.html)

添加了一个新页面，其中包含最常见的有关 Campaign Classic 的问题。[阅读更多](../../platform/using/common-questions.md)

错误消息的列表已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Marketing Cloud 触发器技术说明已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/triggers-and-campaign.html)

已添加有关如何在旧版 Campaign Classic 上安装和部署隐私 (GDPR) 包的技术说明。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

增加了新的序列自动生成机制的技术说明。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html)

JSAPI 文档已更新。[阅读更多](https://support.neolane.net/webApp/extranetLogin)

兼容性矩阵已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

现提供一个新页面，其中列出了已弃用的功能和版本。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/deprecated-and-removed-features.html)

添加了一些关于 RDBMS 的已知限制和最佳实践。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

了解有关 SFTP 使用的最佳实践。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

技术工作流列表已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

知识库文章的列表（以前称为“技术说明”）现在此处提供。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/article-list.html)

[操作方法视频](https://docs.adobe.com/content/help/zh-Hans/campaign-classic-learn/tutorials/overview.html)已更新。

在 LINE 包折旧后更新了 LINE 文档。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

更新了报告指示器计算文档。[阅读更多](../../reporting/using/indicator-calculation.md)

添加了有关与 Oracle 时区文件对齐的信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

添加了新的“监视投放”部分，其中包含有关投放故障和隔离管理的更新信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

重新组织了“个性化块”部分，其中包含了有关现成个性化块的新信息。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

重新组织了“归档电子邮件”部分，其中包含有关文件配置 ```config-<instance name>.xml```的新信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

更新了有关消息中心（控制）技术工作流程的信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

添加了有关设置 SMTP 中继时吞吐量限制的信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

[Adobe Campaign Classic 文档](https://helpx.adobe.com/support/campaign/classic.html)集已重新组织，以提高可用性。

新增了一个教程部分，以便于访问核心 Campaign 功能帮助材料、操作方法、示例和视频。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

新增了一个部分，以帮助您监视投放状态以及可能出现的错误，并让您了解如何修复它们。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

错误消息的列表已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Marketing Cloud 触发器技术说明已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/triggers-and-campaign.html)

Campaign Classic 迁移指南已添加到集合中。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

活动兼容性矩阵已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

如果适用，配置和安装说明现在提及它们适用的托管模型。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

新知识库文章，重点介绍内部部署、混合部署和 Managed Services 部署之间的配置和功能差异。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/acc-on-prem-vs-hosted.html)

添加了有关如何安装标准包的说明。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

添加了有关如何配置与 Audience Manager 或人员核心服务集成的详细信息。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

更新了安装文档，以提及在使用 PostreSQL 时，安装 Campaign 现在需要使用 pgcrypto 命令。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**此版本中包含的新功能**

ACS 连接器增强功能

SAP HANA连 接器 - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

Hadoop Connector via HiveSQL - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

LINE 渠道：邮件增强功能 - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**随版本提供的其他文档更新**

新增了查询样本。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

投放最佳实践指南已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

A/B 测试范例已更新，缺少说明。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

操作方法视频已更新。[阅读更多](https://docs.adobe.com/content/help/zh-Hans/campaign-classic-learn/tutorials/overview.html)

更新电子邮件存档部分。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

明确工作流中的调度程序使用。[阅读更多](../../workflow/using/scheduler.md)

添加暂停的工作流最佳实践。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

有关在工作流中导出数据时导入和后处理文件的新过程。请参阅[此处](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)。

SMS 消息文档的隔离机制已更新，以反映扩展通用 SMPP 连接器的错误管理的特性。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS._quarantines)。

移动应用程序渠道文档已改进，提供了在 Android 上发送丰富通知的详细过程。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications)。

收件箱呈现文档已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html)。

设置 Web 跟踪文档已通过更新的示例和说明进行了增强。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration)。

SMS 渠道文档已更新，在“自动回复”部分中添加了一些说明，这些说明适用于扩展的通用 SMPP 连接器。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS._channel.html#Creating_an_SMPP_external_account)。

社交营销文档已更新。[阅读更多](../../social/using/about-social-marketing.md)。

还增加了一项关于 IP warming 的新技术。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf)。

已添加版本升级的新快速入门指南。[阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)。

## 2017 年 5 月{#release-doc-30-05-2017}

提供了新的快速入门指南：它介绍了一些通过 Adobe Campaign 进行投放的最佳实践，从创建和定位到发送和监控。[阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

安全快速入门指南已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

[“存档电子邮件”文档](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)更新了[“电子邮件密送”](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_)部分，并详细介绍了[激活该功能的步骤](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails)。

添加和更新了某些视频。[阅读更多](https://docs.adobe.com/content/help/zh-Hans/campaign-classic-learn/tutorials/overview.html)

了解如何将投放发送到从外部文件加载的收件人，而不更新数据库。[阅读更多](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

多次选择启用示例已更新。[阅读更多](../../web/using/use-cases--web-forms.md)

## 2017 年 3 月{#release-doc-31-03-2017}

投放能力：已更新[快速入门指南](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)。交付性文档现在包含更详细 [的概述](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) ，以及实施 [过程和主要步骤的说明](../../delivery/using/deliverability-key-points.md)。

“使用批次发送”部分已通过详细示例、建议和使用案例进行移动和增强。   [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

“隔离管理”部分添加了一个表，其中描述了 SMS 消息特有的错误。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS._quarantines)

工作流：新增了多渠道工作流示例。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Marketing Cloud 触发器：添加了有关如何通过 Adobe Campaign 配置它的技术说明。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/triggers-and-campaign.html)

重新组织并扩展了工作流指南。轻松了解如何[构建](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html)和[执行](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)工作流，如何[定位](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html)和[管理](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management)您的数据，如何[导入](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)数据，以及如何使用工作流数据[更新数据库](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database)或[发送投放](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow)。

现提供根据[导入最佳实践](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices)构建[导入工作流](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow)的示例。
此新版本的安装指南已更新。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

兼容性矩阵已更新。[阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

在电子邮件投放中加入优惠券后可使收件人获得附加价值。[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7 - 16/03/2017{#release-17-2}

**此版本中包含的新功能**

ACS 连接器

Web API for Microsoft Dynamics - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

电子邮件归档密送方法 - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Amazon Simple 存储服务 (S3) 连接器 - [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

