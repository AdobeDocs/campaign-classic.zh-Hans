---
title: Adobe Campaign经典文档更新
description: 本页列表了每个Adobe Campaign经典版本的所有新增功能和文档更新。
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
source-git-commit: 57263746675152b472aa5df4ce94f97b77a84a6b
workflow-type: tm+mt
source-wordcount: '6726'
ht-degree: 8%

---


# 文档更新{#documentation-updates}

本页列表每月所有新增功能和文档更新以及活动版本。

您还可以查阅Adobe Campaign经 [典发行说明](../../rn/using/latest-release.md) ，以获取更多更新。

## 2020年6月 {#june-2020}

在如何使用控制面板和活动工作流 [加密](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt)[和解](../../workflow/using/importing-data.md#use-case-gpg-decrypt) 密数据方面添加了用例。

“白名单”和“黑名单”术语已从Adobe Campaign文档中删除。 这些产品UI、选项名称和内部代码中可能仍然存在这些术语的某些出现，但在即将发布的活动版本中，这些术语将替换为“blocklist”和“allowlist”。

## 20.2 - 08/06/2020{#release-20-2}

**此版本中包含的新功能**

支持表情图标- [阅读更多](../../delivery/using/customizing-emoticon-list.md)

Azure突触联合数据访问连接器- [阅读更多](../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse)

泰国和巴西隐私法——阅 [读更多](https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**随版本提供的其他文档更新**

此部分介绍了用于取消发布事务性消息模板的[新选项](../../message-center/using/template-unpublication.md)。

新选项允许在发送包含从个性化URL下载的图像和附件的电子邮件时设置限制，这些新选项已添加到Campaign Classic选项列表。 [阅读更多](../../installation/using/configuring-campaign-options.md#delivery)

本节 **介绍了新的“在投放库中准备** ”选项 [的相关内容](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis)。

验证投放部分已明确并更新。 [阅读更多](../../delivery/using/steps-validating-the-delivery.md)

与新跟踪链接签名机制相关的参数已添加到服务 [器配置文件部分](../../installation/using/the-server-configuration-file.md) 。

兼容性矩阵已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

清除工作流部分已更新。 [了解更多](../../production/using/database-cleanup-workflow.md)

活动网络端点已移动到此 [部分](../../installation/using/campaign-network-endpoints.md)。

Spam Assassin安装部分已更新为新的安装文件名。 [了解更多](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

有关复制环境的部分已更新。 [了解更多](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)


## 2020年5月 {#may-2020}

“监视可交付性”部分已移动和改进。 [阅读更多](../../delivery/using/monitoring-deliverability.md)

“可交付性”疑难解答部分已移动和改进。 [阅读更多](../../delivery/using/deliverability-faq.md)

启动新平台部分时的可交付性指南已得到增强。 [阅读更多](../../delivery/using/starting-new-platform.md)

已移动并更新“发送带有附件的交易电子邮件”部分。 [阅读更多](../../message-center/using/transactional-email-with-attachments.md)

数据包最佳实践部分已移动并更新。 [阅读更多](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## 2020 年 4 月 {#april-2020}

联合数据访问权限表已移至访问外部联合数据访问库()文档。 [阅读更多](../../platform/using/remote-database-access-rights.md)

常见问题解答已更新，其中包含有关如何清除软缓存和硬缓存的提示。 [阅读更多](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

数据模型最佳实践已得到改进，并添加了有关索引的更多信息。 [阅读更多](../../configuration/using/data-model-best-practices.md#indexes)

描述Adobe Campaign内置数据模型的部分已更新，并且每个表中都有更多详细信息。 [阅读更多](../../configuration/using/data-model-description.md)

工作流使用案例已更新并重新组织为主题部分。 [阅读更多](../../workflow/using/using-the-local-approval-activity.md)

弹回 [邮件资格](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) 和电子邮件 [管理规则部分已](../../delivery/using/understanding-delivery-failures.md#email-management-rules) 通过更新的信息进行了增强。

Adobe Campaign增强的MTA文章已更新。 现在只适用于Campaign Classic。 [阅读更多](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

## 2020 年 3 月 {#march-2020}

数据模型最佳实践已通过包括序列、性能 [和大表](../../configuration/using/data-model-best-practices.md#sequences)等新 [的部](../../configuration/using/data-model-best-practices.md#performance) 分进行更新 [](../../configuration/using/data-model-best-practices.md#large-tables)。 [阅读更多](../../configuration/using/data-model-best-practices.md)

现在提供了描述Adobe Campaign内置数据模型和表之间交互的新部分。 [阅读更多](../../configuration/using/data-model-description.md)

其他关键链接已添加到文档主页。 [阅读更多](../../campaign-classic-home.md)

已添加一个用例，说明如何将动态优惠从Adobe Target集成到Adobe Campaign的电子邮件中。 [阅读更多](../../integrations/using/inserting-a-dynamic-image.md)

现在提供了详细介绍Adobe Campaign中不同语言的新部分。 [阅读更多](../../platform/using/adobe-campaign-workspace.md#languages)

访问管理指南已更新，其中包含有关已命名权限的更多信息。 [阅读更多](../../platform/using/access-management.md#named-rights)

## 2020 年 2 月 {#february-2020}

现在提供设计Adobe Campaign数据模型时概述最佳实践和主要建议的新部分。 [阅读更多](../../configuration/using/data-model-best-practices.md)

新增了有关技术电子邮件配置的部分。 [阅读更多](../../installation/using/email-deliverability.md)

“交付性常见问题解答”已更新，其中包含有关“满足配额”错误消息的更多详细信息。 [阅读更多](https://helpx.adobe.com/campaign/kb/acc-deliverability-faq.html#FAQ)

新的电子邮件提供商现在支持电子邮件AMP: 相关文档已更新。 [阅读更多](../../delivery/using/defining-interactive-content.md)

电子邮件存档部分已得到改进。 [阅读更多](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 20.1 - 17/02/2020{#release-20-1}

**此版本中包含的新功能**

雪花联合数据访问连接器- [阅读更多](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Hadoop联合数据访问连接器增强- [阅读更多](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**随版本提供的其他文档更新**

安 [装、](../../installation/using/before-reading.md)生产和配 [置指南](../../production/using/foreword.md)[](../../configuration/using/additional-parameters.md) ，已使用nlserver服务启动使用的新系统单元进行更新。 您仍可以使用/etc/init.d/nlserver6，但Adobe建议您现在使用systemctl命令与nlserver服务进行交互。

安装指南已更新并与最新版本的兼容性矩阵同步。 新增了支持的系统。 已删除已弃用和不支持的系统的实例。 [阅读更多](../../installation/using/before-reading.md)

兼容性矩阵已使用Hadoop 3.0和Snowflake联合数据访问连接器进行更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

安装指南中添加了有关IP关联的最佳实践。 [阅读更多](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

数据库清理工作流部分已更新。 现在提供的批量数字反映了代码实现。 [阅读更多](../../production/using/database-cleanup-workflow.md)

事务消息传递指南中增加了对HTTP联合数据访问的限制。 [阅读更多](../../production/using/database-cleanup-workflow.md)

新选项中已添加信息，允许您为工作流和工作流活动定义 **[!UICONTROL JavaScript code]** 超时 **[!UICONTROL Advanced JavaScript code]** 期限。 [阅读更多](../../workflow/using/sql-code-and-javascript-code.md)

在> >节点中提供的 **[!UICONTROL Start Pending]** 新视图中已 **[!UICONTROL Administration]** 添 **[!UICONTROL Audit]** 加信 **[!UICONTROL Workflows Status]** 息。 [阅读更多](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

已移 [动、重新组织](../../delivery/using/about-mobile-app-channel.md) “发送推送通知”指南，并对其进行了清晰的信息改进。

此处记录了URL报告配置的新 [参数](../../reporting/using/properties-of-the-report.md#defining-additional-settings)。

Campaign Classic **本地和托管功能矩阵页面已使用** 新的联合数据访问连接器进行更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

“ **Campaign Classic能力** ”矩阵页已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

此处记录 **[!UICONTROL Cleanup of Nmsaddress]** 了新的工作 [流程](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress)。

在工作流中使用查询活动时已添加限制。 [阅读更多](../../workflow/using/query.md)。

新增了一个部分，以详细描述增强的电子邮件地址验证规则，以便在软错误时向隔离发送地址。 [阅读更多](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

配置文件中的参数表明实例是否正在使用增强的MTA，现在记录在案。 [阅读更多](../../installation/using/the-server-configuration-file.md#mta)

## 2020 年 1 月 {#january-2020}

“可交付性”部分已通过更新的内容进行移动、重新组织和增强。 [阅读更多](../../delivery/using/about-deliverability.md)

现在提供了新的部分，其中介绍了Adobe Campaign经典数据模型基础知识以及如何访问每个表的说明。 [阅读更多](../../configuration/using/about-data-model.md)

Adobe Campaign增强的MTA文章已更新，其中包含有关在未向每条消息添加所需增强的MTA头的实例上安装特定排版包的详细信息。 [阅读更多](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

与查询设计相关的使用案例已重新组织为单独的部分。 [阅读更多](../../workflow/using/querying-recipient-table.md)

现在提供有关管理优惠和使用Adobe Campaign经典中的交互模块的提示和技巧的新部分。 [阅读更多](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

“交互”文档中丰富了指向多个视频的链接，这些视频有助于更好地了解如何管理优惠。 [阅读更多](../../interaction/using/interaction-and-offer-management.md)

有关如何优化实例上运行的查询的最佳实践文章已集成到文档中。 [阅读更多](../../workflow/using/query.md#optimizing-queries)

报告指南已更新并重新组织。 [阅读更多](../../reporting/using/about-adobe-campaign-reporting-tools.md)

已添加一个如何在工作流中使用实例变量的示例。 [阅读更多](../../workflow/using/javascript-scripts-and-templates.md)

## 2019 年 12 月 {#december-2019}

“WdbcOptions_TempDbName”选项已添加到活动选项的列表。 [阅读更多](../../installation/using/configuring-campaign-options.md)

联合数据访问矩阵页面已移到 [此处](../../platform/using/remote-database-access-rights.md)。

“访问权限矩阵”页面已移 [到此处](https://docs.adobe.com/content/help/en/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf)。

描述如何使用AMP定义交互式内容的部分已被移动。 [阅读更多](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**此版本中包含的新功能**

加利福尼亚消费者隐私法(CCPA)-阅 [读更多](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

使用AMP的交互式内容- [阅读更多](../../delivery/using/defining-interactive-content.md)

工作流实时监视——阅 [读更多](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

安全SMS消息(TLS)-阅 [读更多](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

**随版本提供的其他文档更新**

Adobe Campaign增强MTA文档现已可用。 [阅读更多](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

新增了一节，介绍如何对工作流在开始中保持“尽快”状态进行故障诊断。 [Read more](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

新的“NmsOperation_DeliveryPreparationWindow”和“WdbcKillSessionPolicy”选项已添加到活动选项列表中。 [阅读更多](../../installation/using/configuring-campaign-options.md)

现在提供了描述Adobe Campaign经典数据模型基础知识的新文档。 [阅读更多](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)

此部分 **介绍了投放属性** 中新增的“最大个性化”运行时 [间选项](../../delivery/using/personalization-fields.md#timing-out-personalization)。

已更新使用HttpServletRequest **和logon** ()和查询()的API调用的示例。 [阅读更多](../../configuration/using/web-service-calls.md)。

添加了模式 **定义中** sqlDefault属性的建议。 [阅读更多](../../configuration/using/elements-and-attributes.md#attribute-description)。

Adobe Campaign与Adobe实时客户数据Platform之间的集成现在已在“与Adobe Experience Cloud集 **成”指南中提及** 。 [阅读更多](../../integrations/using/about-campaign-integrations.md)。

## 2019年11月 {#november-2019}

在多路复用中间源服 [务器和支持多个控制实例](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server)[部分中添加了一个警告](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) ，提到完全托管和混合客户端不支持这些部署。

新增了一节，用于说明如何强制在发送电子邮件时使用字符编码。 [阅读更多](../../delivery/using/sending-messages.md#character-encoding)

“访问管理”部分已使用“隐私数据” **权限进行更新**。 [阅读更多](../../platform/using/access-management.md#named-rights)

已添加信息，以指定个性化字段内容不能超过1024个字符。 [阅读更多](../../delivery/using/personalization-fields.md)

控制面板文档已集成到新的协作文档集中。 [阅读更多](https://docs.adobe.com/content/help/zh-Hans/control-panel/using/control-panel-home.html)

投放最佳实践快速入门指南已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

## 2019年10月 {#october-2019}

Campaign Standard和Campaign Classic的错误消息列表已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

GDPR入门指南已得到改进和丰富。 它现在是包括GDPR和CCPA在内的隐私管理文档。 [阅读更多](https://helpx.adobe.com/content/help/en/campaign/kb/campaign-privacy.html)

新增了一个疑难解答页面，用于在Campaign Classic中跟踪。 [阅读更多](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html)。

新增了AdobeAnalytics数据连接器的最佳实践页面。 [阅读有关AdobeAnalytics数据连接器的更多信息](../../platform/using/adobe-analytics-data-connector.md)

投放最佳实践快速入门指南已移动并更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

已向SMS渠道文档添加了建议，以避免在使用具有相同提供者帐户的扩展通用SMPP连接器的多个外部帐户时出现问题。 [阅读更多](../../delivery/using/sms-channel.md#automatic-reply)

在调度程序活动文档中添加了有关如何防止同时执行工作流的信息。 [阅读更多](../../workflow/using/scheduler.md)

为预置安装配置收件箱渲染的步骤已添加到文档中。 [阅读更多](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## 2019 年 9 月 {#september-2019}

添加了新页面，以提供维护Campaign Classic的一般准则。 [阅读更多](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)

与工作流监测有关的信息已集中到新的专设部分。 [阅读更多](../../workflow/using/monitoring-workflow-execution.md)。

已添加有关Adobe Campaign经典中跟踪的一般准则的新页面。 [阅读更多](https://helpx.adobe.com/campaign/kb/acc-tracking.html)。

已更新工作流和投放性能改进的最佳实践。 [阅读有关工作流的更多信](../../workflow/using/workflow-best-practices.md) 息， [以及有关投放的更多信息](../../delivery/using/monitoring-a-delivery.md#best-practices-performance)。

## 19.1 - 30/05/2019{#release-19-1}

**此版本中包含的新功能**

控制面板——阅 [读更多](https://docs.adobe.com/content/help/zh-Hans/control-panel/using/control-panel-home.html)

审核跟踪——阅 [读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Audit_trail.html)

**随版本提供的其他文档更新**

已创建新的构建升级常见问题解答。 [阅读更多](https://helpx.adobe.com/campaign/kb/build-upgrade-faq.html)

兼容 [性矩阵](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) 已更新。 支持的列表库系统的已更新，Android/iOS版本和相关SDK也已更新。 已 [存档19.0兼容性](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html) 矩阵。

“Campaign Classic中已弃用和已删除的功能”页面已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

服务器配置文件的说明已添加到《安装指南》中。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

添加了一节，介绍托管和混合型号的安装和配置步骤。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

添加了描述活动服务器卸载步骤的部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

安全 [性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)、交付 [性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 和隐 [私](https://helpx.adobe.com/campaign/kb/acc-privacy.html) 入门指南已更新。

预处理工作流选项的描述已更新，以反映产品更改。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

Marketing Cloud触发器技术说明已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

错误消息的列表已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

添加了有关事务消息传递的SOAP身份验证方法的更多信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Apache配置步骤已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

已添加新页面，包括列表Campaign Standard和经典的端点。 [阅读更多](https://helpx.adobe.com/campaign/kb/campaign-endpoints.html)

数据包最佳实践文章已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/data-package-best-practices.html)

“管理优惠”文档已更新，其中新增了列出最佳实践的部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

已创建一篇关于在Adobe Campaign经典中使用优惠目录的新知识库文章。 [阅读更多](https://helpx.adobe.com/campaign/kb/offer-best-practices.html)

子工作流活动部分已通过一个使用示例进行了增强。 [阅读更多](../../workflow/using/sub-workflow.md)

Campaign Classic [本地和托管功能矩阵知识库文章已更新](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html) ，其中包含与归档电子邮件相关的信息。

Transactional Messaging文档已更新，并带有有关模板发布的说明。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

“未处理的弹回邮件”部分已更新，其中包含有关“转发地址”和“错误地址”字段的更多详细信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

新增了有关工作流计划最佳实践的一节。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

为列表活动选项添加了两个新选项： XtkSecurity_Restrict_EditXML和NmsOperation_OperationMgtDebug。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

添加了有关Campaign Classic中可用的不同外部帐户以及如何配置这些数据的信息。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

更新了Analytics数据连接器部分以反映接口更改。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

添加了有关帐单报表的信息。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

更新了有关共享受众集成的文档。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

以下技术已更新： [SMS连接器协议、设置](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html) 和序 [列自动生成](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)。

技术工作流部分已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

活动域名设置过程已得到改进和更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)

Android应用程序从Google Cloud Messaging(GCM)到Firebase Cloud Messaging(FCM)的迁移过程已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html)

活动硬件大小调整指南已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)

添加了关于Teradata查询的外部帐户条带的信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## 2019 年 1 月{#release-doc-16-01-2019}

Marketing Cloud触发器技术说明已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

在优惠批准部分添加了注释，以指定“已批准内容”提及指示内容批准流程已完成，无论是否已启用／批准所有优惠。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

在安装指南中添加了新部分，其中列出了“管理”/“Platform”/“选项”节点中的选项。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

添加了有关使用种子地址保护邮寄列表的信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

创建和发送投放时的关键步骤已重新分组到新部分，并在需要时引用各种渠道。 [阅读更多](../../delivery/using/steps-about-delivery-creation-steps.md)

电子邮件 [归档部分](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) 已经进行了移动、重新组织和改进，其中包含了明确的信息：

* 已添加有关每个连接的电子邮件和密送发送IP参数的最佳实践。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* 如果您已经使用旧版本的电子邮件归档(在Adobe Campaign17.2 —— 内部版本8795之前)，则我们更新了升级到新电子邮件归档系统(BCC)的步骤。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

在“使用工作流实现自动化”指南中添加了一个用例： 向运营商发送个性化提醒。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

“迁移到新版本”部分已更新。 文档现在只详细介绍了从任何旧版本迁移到Adobe Campaign经典v7的步骤，因为不再可能迁移到Adobe Campaignv6.11。请阅 [读更多](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

&quot;投放临时失败后的重试&quot;一节已明确。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

指向“数字内容编辑器”部分的链接已添加到“定义电子邮件内容”部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

“事务消息架构”部分已更新，并显示一条警告，指定控件和执行实例不能安装在同一台计算机上。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

“工作流监视”部分已更新，其中包含8700到8977(18.10)之间构建的注释，其中包括有关如何为这些构建安装Workflow HeatMap包的技术说明的链接。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

添加了一个用例，说明如何使用工作流中的扩充活动发送包含自定义数据字段的电子邮件。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

功能视频已移到 [此处](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html)。

Teradata和MySQL 5.7 [中](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html)[添加了两项技术](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html)。

## 18.10 - 05/11/2018{#release-18-10}

**此版本中包含的新功能**

推送通知改进- [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

SQL数据管理活动- [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

工作流监视- [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**随版本提供的其他文档更新**

Campaign ClassicAPI现在可在专用 [页面中使用](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)。 如果您使用的是jsapi.chm文件，您现在应该参阅新的在线版本。

兼容性矩阵已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

“Campaign Classic中已弃用和已删除的功能”页面已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

在发 [行说明](https://docs.campaign.adobe.com/doc/AC/en/RN.html)[和旧版发行说明中](https://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html)，已为已召回的构建添加了警告。 还增加了17.9、18.4和18.6的累积内部版本。

安全 [性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)、可 [交付性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)[、](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 构建升级入门指南已更新。

隐私 [入门指南](https://helpx.adobe.com/campaign/kb/acc-privacy.html) 已更新，其中包含有关如何在外部调用API以及如何使用queryDef查询状态和下载GDPR文件的信息。

添加了事务性消息使用案例，以便将电子邮件附件快速添加到出站派单。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

更新了连接阈值疑难解答部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

添加了有关如何配置代理连接的部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

更新了授权外部命令限制部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

添加了与SFTP使用情况相关的疑难解答部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

“发送消息”指南的概述部分重新进行了组织。 在投放创建全局过程和不同投放类型中添加了信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

错误消息的列表已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

已将有关如何使用种子地址的部分移到“发送消息指南”概述章节。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

添加了新的工作流用例： 管理伴随的工作流执行中的更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

“收件箱呈现”部分已更新，其中包含有关Litmus的更多信息和更详细的操作过程。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

“SpamAssassin”部分已得到改进。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

“使用压力规则管理营销疲劳”部分已添加一个用例。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

现在提供了一个新的用例，用于描述如何创建跨渠道投放工作流。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

在“存档电子邮件”部分添加了一些建议。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

新增了关于最小屏幕分辨率的建议，以便Adobe Campaign最佳使用。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

Experience Manager集成指南已更新，并添加了一些说明来配置此集成。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

添加了有关组类型列表与列表类型列表之间差异的信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

已更新代码，通过电子邮件将报表提取作为附件发送。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

添加了一个示例，说明如何创建查询以过滤过去7天内未打开电子邮件的收件人。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

已使用Adobe Experience Cloud集成指南更新共享受众。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

常见问题帮助页面现在包含有关活动可用语言、Web表单翻译和多语言电子邮件的信息。 [阅读更多](../../platform/using/common-questions.md)

“美国英语”和“英国英语”实例之间的差异现在列在专用部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

“常见 [问题](../../platform/using/common-questions.md) ”帮助页面现在链接到错误消息页面。

已添加有关“打开”跟踪模式的信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

添加有关Web应用程序和Web表单的最低分辨率的信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

活动和Adobe Experience Cloud解决方案集成指南已更新并重新组织。 [阅读更多](../../integrations/using/about-campaign-integrations.md)

添加了有关Web表单中文本变量用法的部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

消息中的URL跟踪模式现已详细介绍。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

实例创建部分已重新组织。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

现在，在日本手机上发送电子邮件记录在一个新部分中。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

“优化个性化”部分已更新，并提供更多信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**此版本中包含的新功能**

兼容性矩阵已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

JSAPI文档已更新。 [阅读更多](https://support.neolane.net/webApp/extranetLogin)

已更新已弃用和已删除的功能页面。 [阅读更多](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

**随版本提供的其他文档更新**

Campaign Classic用户指南已更名为简化导航、改善用户体验、访问信息和自助。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/browseAC.html)

表达式编辑器中可用函数的列表已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

安全入门指南已更新，其中包含有关如何保护包含PI的页面的信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

错误消息的列表已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

IMS集成文档中已添加一个疑难解答部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

已更新“构建升级入门”指南。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)

IP关联配置部分已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

已添加“性能和吞吐量”疑难解答部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

内置个性化块的列表已通过示例进行更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

已更新投放故障原因的列表。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

添加了有关包定义管理的新部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

活动与Adobe Deta Connector - Data Connector部分的集成已得到改进和重新组织。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

新增了“教程”部分，其中包含指向分步指南和操作方法视频的链接。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

已创建有关SMS连接器协议和设置的新技术说明。 [阅读更多](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

投放最佳实践快速入门指南已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

已更新具有Web API部署的Microsoft Dynamics 365帐户配置。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

在Windows平台上安装Adobe Campaign经典的过程已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

受众在Adobe Experience Cloud和Campaign Classic之间的共享时间范围已详尽。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

已更新Campaign Classic列表的知识库文章完整版。 [阅读更多](https://helpx.adobe.com/campaign/kb/article-list.html)

有关性能改进和最佳实践的新技术现已发布。 [阅读更多](https://helpx.adobe.com/campaign/kb/best-practices-for-performance-improvement.html)

A/B测试范例已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Campaign Classic常见问题／常见问题解答页面已更新。 [阅读更多](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**此版本中包含的新功能**

欧盟一般数据保护规定(GDPR)-阅 [读更多](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

活动用户档案- [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Android推送连接器增强——阅 [读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**随版本提供的其他文档更新**

发行说明已得到改进，以获得更好的用户体验，现在包括所有与客户请求相关的修补程序。  [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/RN.html)

添加了一个新页面，其中包含最常见的有关Campaign Classic的问题。 [阅读更多](../../platform/using/common-questions.md)

错误消息的列表已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Marketing Cloud触发器技术说明已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

已添加有关如何在旧版Campaign Classic版上安装和部署隐私(GDPR)包的技术说明。 [阅读更多](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

新的序列自动生成机制增加了技术。 [阅读更多](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html)

JSAPI文档已更新。 [阅读更多](https://support.neolane.net/webApp/extranetLogin)

兼容性矩阵已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

现在提供一个新页面，其中列出了已弃用的功能和版本。 [阅读更多](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

已添加一些关于RDBMS的已知限制和最佳实践。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

了解有关SFTP使用的最佳实践。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

技术工作流列表已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

知识库文章的列表（以前称为“技术说明”）现已在此处提供。 [阅读更多](https://helpx.adobe.com/campaign/kb/article-list.html)

操 [作方法视频](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) 已更新。

在LINE包折旧后更新了LINE文档。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

更新了报告指示器计算文档。 [阅读更多](../../reporting/using/indicator-calculation.md)

添加了有关与Oracle时区文件对齐的信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

添加了新的“监视投放”部分，其中包含有关投放故障和隔离管理的更新信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

重新组织了“个性化块”部分，其中包含了有关现成个性化块的新信息。
[阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

重新组织了“归档电子邮件”部分，其中包含有关文件配置 ```config-<instance name>.xml``` 的新信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

更新了有关消息中心（控制）技术工作流程的信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

添加了有关设置SMTP中继时吞吐量限制的信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

Adobe Campaign [经典文档集](https://helpx.adobe.com/support/campaign/classic.html) 已重新组织，以提高可用性。

新增了一个教程部分，以便于访问核心活动功能帮助材料、操作方法、示例和视频。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

新增了一个部分，帮助您监视投放状态，但也可能出现错误并了解如何修复它们。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

错误消息的列表已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Marketing Cloud触发器技术说明已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Campaign Classic迁移指南已添加到集合中。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

活动兼容性矩阵已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

如果适用，配置和安装说明现在提及它们适用的托管模型。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

新知识库文章，重点介绍内部部署、混合部署和Managed Services部署之间的配置和功能差异。 [阅读更多](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

添加了有关如何安装标准包的说明。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

添加了有关如何配置与Audience Manager或人员核心服务集成的详细信息。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

更新了安装文档，以提及在使用PostreSQL时，活动安装现在需要pgcrypto。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**此版本中包含的新功能**

ACS连接器增强功能

SAP HANA连接器——阅 [读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

通过HiveSQL的Hadoop Connector —— 阅 [读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

行渠道: 消息传递增强- [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**随版本提供的其他文档更新**

新增了查询样本。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

投放最佳实践指南已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

A/B测试范例已更新，缺少说明。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

操作方法视频已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

更新电子邮件存档部分。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

明确工作流中的调度程序使用。 [阅读更多](../../workflow/using/scheduler.md)

添加暂停的工作流最佳实践。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

有关在工作流中导出数据时导入和后处理文件的新过程。 请 [在这里](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)。

SMS消息文档的隔离机制已更新，以反映扩展通用SMPP连接器的错误管理的特性。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)。

移动应用程序渠道文档已得到增强，并提供了在Android上发送丰富通知的详细过程。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications)。

收件箱呈现文档已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html)。

设置Web跟踪文档已通过更新的示例和说明进行了增强。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration)。

SMS渠道文档已更新，在“自动回复”部分中添加了一些说明，这些说明适用于扩展的通用SMPP连接器。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account)。

社交营销文档已更新。 [阅读更多](../../social/using/about-social-marketing.md)。

还增加了一项关于知识产权变暖的新技术。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf)。

已添加新的内部版本升级入门。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)。

## 2017年5月{#release-doc-30-05-2017}

提供了新的入门指南： 它介绍了一些最佳实践，可用于通过Adobe Campaign提供，从创建和定位到发送和监控。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

安全入门指南已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

“存 [档电子邮件”文档](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) ”已通过“电子邮件密 [件抄送”部分进行更新](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) ，并详细 [了激活该功能的步骤](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails)。

某些视频已添加和更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

了解如何将投放发送到从外部文件加载的收件人，而不更新数据库。 [阅读更多](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

多次选择加入示例已更新。 [阅读更多](../../web/using/use-cases--web-forms.md)

## 2017 年 3 月{#release-doc-31-03-2017}

可交付性： 已 [更新入门](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 指南。 交付性文档现在包含更详细 [的概述](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) ，以及实施 [过程和主要步骤的说明](../../delivery/using/deliverability-key-points.md)。

“使用批次发送”部分已通过详细示例、建议和使用案例进行移动和增强。    [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

“隔离管理”部分已添加一个表，其中描述了SMS消息特有的错误。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

工作流: 新增了多渠道工作流示例。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Marketing Cloud触发器： 添加了有关如何配置它并将其与Adobe Campaign一起使用的技术说明。 [阅读更多](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

重新组织并扩展了工作流指南。 轻松找到如何构建和执 [行工作流](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) 、如何目标和管 [理您的数据、如何导入数据、如](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow)何使用、如何使用投放更新数据或更新库或发送工作流。

现在提供了 [根据导入](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) 最佳实践 [构建的导入工作](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices) 流的示例。
此新版本的安装指南已更新。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

兼容性矩阵已更新。 [阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

收件人在电子邮件投放中加入优惠券后可获得附加价值。 [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaignv7 - 16/03/2017{#release-17-2}

**此版本中包含的新功能**

ACS连接器

Web API for Microsoft Dynamics —— 阅 [读更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

电子邮件归档密送方法- [阅读更多](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Amazon Simple存储服务(S3)连接器——阅 [读更多](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

