---
product: campaign
title: Adobe Campaign术语表
description: Adobe Campaign术语表
feature: Overview
role: User, Data Architect
level: Beginner
exl-id: 81f207a0-bb72-450b-abe4-0b229b6b1f3a
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '5959'
ht-degree: 2%

---

# Adobe Campaign术语表{#ac-glossary}

以下是Adobe Campaign中关键术语和概念的定义，以及指向相关文档的链接。 单击术语以显示其定义。

## A - D{#sec-1}

+++**A/B 测试**

A/B测试是一项功能，可让用户定义两到三个电子邮件变体：每个变体都会发送到群体样本，以确定哪个变体效果最佳。 确定之后，会将入选的变体发送给其余群体。

了解有关 [A/B测试](../../delivery/using/get-started-a-b-testing.md).
+++

+++**访问管理**

访问管理允许管理员向Adobe Campaign用户分配访问权和权限。 权限包括查看和/或使用Adobe Campaign功能的功能，例如执行工作流、定义架构和管理受众。

了解有关 [访问管理](access-management.md).
+++

<!--
+++**ACS Connector**

ACS Connector (Prime Offering) bridges Adobe Campaign v7 and Adobe Campaign Standard. It is an integrated feature in Campaign v7 that automatically replicates data to Campaign Standard, uniting the best of both applications. Campaign v7 has advanced tools to manage the primary marketing database. The data replication from Campaign v7 allows Campaign Standard to leverage the rich data in a user-friendly environment. 

Learn more about [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++
-->

+++**活动**

活动是添加到工作流中以定义执行功能的面板项目。 活动是一个执行任务的容器。 在工作流中，给定活动可以生成多个任务，尤其是当存在循环或循环（定期）操作时。

了解有关 [工作流活动](../../workflow/using/about-activities.md).
+++

+++**活动配置文件**

如果用户档案在过去12个月中通过任何渠道被定向或与其联系，则视为处于活动状态。 根据您的合同，您的每个Campaign实例都会配置特定数量的活动用户档案，并对这些活动用户档案进行计数以计费。

了解有关 [活动用户档案](../../platform/using/about-profiles.md#active-profiles).
+++

+++**审批工作流活动**

*上下文： Campaign分布式营销*

本地审批活动是一种工作流活动，用于在发送消息之前设置投放审批流程。

了解关于 [本地审批活动](../../workflow/using/local-approval.md).
+++

+++**受众**

受众是生成的一组符合过滤器定义标准、基于规则和属性的用户档案。

了解有关 [受众](../../campaign/using/marketing-campaign-target.md).
+++

+++**审核跟踪**

审核记录可实时捕获在Adobe Campaign实例中发生的操作和事件的全面列表。 它提供了一种访问数据历史的自助方式，可帮助回答以下问题：您的工作流发生了什么情况、上次更新这些工作流的人员或者您的用户在实例中做了什么。

了解有关 [审核记录](../../production/using/audit-trail.md).
+++

<!--
----DUPLICATE WITH THE "CAMPAIGN" ENTRY?---
+++**Automated campaigns**

Campaigns that run on a schedule, such as for targeting recipients who have a birthday or an anniversary. Can also be used to execute look-ahead and look-back logic, such as who purchased yesterday or who has a payment due tomorrow.

Learn more about [Campaigns](../../campaign/using/designing-marketing-campaigns.md).
+++
-->

+++**批处理模式**

*上下文：Campaign交互*

在促销活动交互的上下文中，批量模式允许优惠引擎为一组联系人选择最佳优惠（或多个优惠）。 资格/优先级规则应用于集的所有联系人。

了解有关 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**营销活动**

Campaign是一个界面，用于协调、定义和执行营销活动。 营销策划可以将一个或多个工作流、投放、文档和其他相关数据点包含到一个简单易用的界面中。

了解有关 [营销活动](../../campaign/using/designing-marketing-campaigns.md).
+++

<!--
-----NOT USEFUL HERE?-----
+++**Changeover process**

*Context: Campaign Interaction*

In the context of Campaign Interaction, the changeover process is an activated process in an identified environment, responsible for directing the call to an anonymous environment if the contact has not been explicitly and/or implicitly identified.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++
-->

+++**渠道**

信道是用来发送通信的介质。 Adobe Campaign中的内置渠道包括电子邮件、短信、直邮、推送通知、LINE和X(以前称为Twitter)。 可以针对非标准渠道要求实施自定义渠道。

了解有关 [渠道](../../delivery/using/communication-channels.md).
+++

+++**客户端控制台**

Campaign客户端控制台是一个富客户端，可让您连接到Campaign应用程序服务器。 客户端控制台可执行文件(.exe)应用程序安装在具有Microsoft Windows操作系统的计算机上。 Campaign客户端控制台集中了所有功能和设置。

了解有关 [客户端控制台](../../platform/using/adobe-campaign-workspace.md).
+++

+++**内容审批**

内容审批是指在发送投放内容之前，由一个单独的操作员或一组操作员审批投放内容的过程。

了解有关 [内容审批](../../campaign/using/marketing-campaign-approval.md).
+++

+++**对照组**

使用控制组通过排除部分控制组受众来衡量活动的影响。 操作员可以将收到消息的目标群体的行为与未作为目标的联系人的行为进行比较。 根据发送日志，操作员还可以在未来的活动中以控制组为目标。

了解有关 [对照组](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).
+++

+++**控制面板**

该控制面板允许Adobe Campaign产品管理员管理每个实例的设置并跟踪使用情况，从而帮助他们提高工作效率。 其直观的界面可让他们轻松监控关键资产的使用情况，并执行管理任务，如IP地址允许列表添加、 SFTP存储监控、密钥管理等。

了解有关 [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hans).
+++

+++**多维数据集**

*上下文：Marketing Analytics*

多维数据集是一种Adobe Campaign直观的数据探索工具，可帮助用户创建和共享动态报告。

了解有关 [多维数据集](../../reporting/using/ac-cubes.md).
+++

+++**自定义资源**

Adobe Campaign附带预定义数据模型，其中数据类型通过安装各种包来定义。 运算符可以通过扩展资源以添加自定义字段或自定义表（如交易表或产品表）来扩充提供的数据模型。

了解有关 [自定义资源](../../configuration/using/about-schema-edition.md).
+++

+++**数据模型**

Campaign数据模型是一组架构，用于定义数据类型及其关系（链接）。 数据模型是一个抽象定义，使用包含实际数据的数据库进行物理实现。

了解有关 [数据模型](../../configuration/using/about-data-model.md).
+++

+++**数据库清理工作流**

数据库清理工作流会删除过时的数据，以避免数据库呈指数增长。 工作流将自动触发，无需用户干预。

了解有关 [数据库清理工作流](../../production/using/database-cleanup-workflow.md).
+++

<!--
----UNCLEAR----
+++**Dedicated server**

*Context: Transactional Messaging*

Dedicated execution server(s) to leverage Transactional Messaging. A server can typically process up to 50,000 Engine Calls per hour. The “Per-Dedicated Server” designation does not necessarily have a 1:1 correlation with a physical server as Adobe may utilize virtualization technologies to achieve the equivalent effect.

Learn more about [Transactional Messaging](../../message-center/using/about-transactional-messaging.md).
+++
-->

+++**可投放性**

*上下文：电子邮件可投放性*

通过可投放性，您可以衡量营销活动在到达收件人的收件箱时成功与否，而不会出现退回或标记为垃圾邮件的情况。 更准确地说，电子邮件可投放性指一组特征，这些特征决定消息在短时间内通过个人电子邮件地址到达其目的地的能力，以及在内容和格式方面达到预期质量。

了解有关 [可投放性](../../delivery/using/about-deliverability.md).
+++

+++**投放**

投放是一种通过特定渠道（电子邮件、短信、推送通知等）发送给受众的特定营销通信项目。 在营销术语中又称为“触摸”。

了解有关 [投放](../../delivery/using/communication-channels.md).
+++

+++**投放分析**

投放分析是投放的准备工作。 此过程会将内容与收件人用户档案数据相结合，生成收件人将收到的个性化电子邮件。 投放分析逻辑可以根据定义的逻辑，从目标中排除收件人或完全停止投放。 此过程还包括评估动态内容逻辑以及插入特定于单个收件人配置文件的选件。

了解有关 [投放分析](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
+++

+++**投放日志**

投放日志包含发送消息时生成的信息。 这些日志显示发送的详细信息，其中消息已准备、忽略、发送或失败。 可直接从投放仪表板访问它们。

了解有关 [投放日志](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).
+++

<!--
----STRANGE IN DOCS?----
+++**Delivery fundamentals**

*Context: Email Deliverability*

Adobe Campaign Deliverability Fundamentals Consulting Service provides email deliverability consultation and reputation management to support customers using Adobe Campaign deliveries.

Learn more about [Deliverability](../../delivery/using/about-deliverability.md).
+++
-->

+++**投放概要**

*上下文：直邮*

投放概要是一组结构化的元素（文档、商店、促销优惠券等） 由公司创建，并用于特定营销活动。 它在直邮投放的上下文中使用。

了解有关 [直邮](../../delivery/using/about-direct-mail-channel.md).
+++

+++**部署向导**

部署向导定义Campaign实例的参数，如默认命名空间、数据库清理计划、数据保留期和其他技术设置。

了解有关 [部署向导](../../installation/using/deploying-an-instance.md#deployment-wizard).
+++

+++**描述性分析**

描述性分析是一个上下文相关的报表工具，可用于检查工作流工作表中的数据、文件夹中的选定数据，或者深入了解选定投放的目标和排除项。

了解有关 [描述性分析](../../reporting/using/about-descriptive-analysis.md)
+++

+++**分布式营销**

*上下文：分布式营销*

分布式营销附加组件为Campaign操作员提供了一个协作工作区，用于在中央实体（总部、营销部门等）和本地实体（商店、区域代理等）之间 和地方实体（销售点、区域机构等）之间实施协作营销活动。此合作基于共享工作区，称为 **Campaign包列表**，向本地实体提供集中创建的活动模板和实例。

了解有关 [分布式营销](../../distributed/using/about-distributed-marketing.md)
+++

+++**值分布**

值分布是一种工具，它显示当前存在于数据库中的方案属性的值分布。 这有助于您确定哪些值可用、其计数和百分比，并在创建查询或表达式时避免出现大写和拼写值问题。

了解有关 [值分布](../../platform/using/defining-filter-conditions.md#selecting-data-to-extract)
+++

+++**域委派**

子域配置允许您配置域的子部分（技术上称为“DNS区域”）以与Adobe Campaign一起使用。
域委派允许Adobe控制和维护DNS的所有方面，这些方面是传递、渲染和跟踪电子邮件营销活动所必需的。

了解有关 [域委派](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=zh-Hans)
+++

## E - H {#sec-2}

<!--
----DEPRECATED------>
+++**E4X**

E4X是Adobe Campaign Classic中使用的Javascript版本。 它有时称为ECMAScript，是Javascript的扩展，允许在同一代码中混合Javascript和XML基元。 请注意，E4X被分类为已弃用的语言。
+++


+++**资格规则**

*上下文：Campaign交互*

资格规则是应用于环境、类别或选件的约束，涉及有效期、目标和权重。 它们允许操作员确保选件符合定向联系人。 在选件环境中，资格规则包括应用于选件和要定位的收件人的呈现规则。 在类别中，资格规则允许操作员及时限制类别的有效性，定义应用程序主题并确定目标收件人。 它们还可以为给定时间段定义乘数权重。 这允许操作员共享其他类别中选件的规则，从而简化其管理。 在选件中，资格规则允许操作员及时限制选件的有效性并确定要定位的收件人。

了解有关 [资格规则](../../interaction/using/interaction-and-offer-management.md).
+++

+++**合格优惠**

*上下文：Campaign交互*

合格选件是指满足上游定义的约束，并且始终能够提供给目标的选件。

了解有关 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**电子邮件密送**

电子邮件密件抄送功能会以EML格式发送相应已投放电子邮件的精确副本，该副本将保存到专用的密件抄送电子邮件地址，发件人可以在外部系统中处理和存档电子邮件。

了解有关 [电子邮件密送](../../delivery/using/email-parameters.md#email-bcc).
+++

<!--
-----STRANGE FOR DOCS?----
+++**Email volume commitment**

The anticipated emails sent per year as set forth in the Sales Order. This is the total annual email volume commitment, including emails sent but not delivered due to delivery errors such as: non-delivery of a message including but not limited to email address errors, hard bounces, soft bounces, email filters of mail clients, and email blacklists. 
+++
-->

<!--
-----USEFUL FOR DOCS?----
+++**Engine call**

An engine call is a server call that starts real-time processing on server side for the extraction of data, such as data relating to surveys, WebApps, JSSP, APIs, mobile app registrations, etc. Engine calls must be licensed in packs of 5,000 Engine Calls per day.
+++
-->

+++**扩充活动**

扩充活动是一种高级工作流活动，它允许操作员扩充将在工作流中处理的已生成的工作表数据。 此活动通常用在定向活动或导入文件之后，以及使用定向数据的活动之前。 “增强”功能可以转换集客过渡数据并配置活动，以使用增强的数据完成输出过渡。 它允许运算符组合来自多个数据集的数据，或创建指向临时资源的链接。

了解有关 [扩充活动](../../workflow/using/enrichment.md).
+++

+++**明细列表**

枚举是在架构中或在Platform级别定义的数据类型，用于定义字段的有效输入值。 枚举作为选取列表显示在用户界面和查询构建器中。

了解有关 [明细列表](../../platform/using/managing-enumerations.md).
+++

+++**资源管理器视图**

资源管理器视图是包含Adobe Campaign工件和数据的文件夹的分层显示。 请注意，Adobe Campaign中的文件夹系统的功能与典型的树状视图不同，因为每个文件夹都包含特定类型的数据，例如投放、工作流或选件。

了解有关 [资源管理器视图](../../platform/using/adobe-campaign-explorer.md).
+++

+++**外部帐户**

外部帐户是产品连接到其他环境和技术的入口和出口点。 外部帐户定义产品用于向其他源发送数据或从其他源接收数据的连接参数。 典型的外部帐户类型包括SFTP站点的连接、支持发送短信的电信、用于处理退回的邮箱或外部数据库的连接。

了解有关 [外部帐户](../../installation/using/external-accounts.md).
+++

+++**疲劳管理**

*上下文：活动优化*

疲劳管理可帮助您控制消息的频率和数量，以避免过度招徕收件人，通常使用类型规则来应用疲劳管理功能。

了解有关 [疲劳管理](../../campaign-opt/using/pressure-rules.md).
+++

+++**联合数据访问(FDA)**

联合数据访问支持扩展客户端数据模型以包括第三方数据库。 它将自动检测目标表的结构，并使用来自SQL源的数据。 您可以访问外部数据，而无需更改Adobe Campaign数据的结构。

了解有关 [联合数据访问](../../installation/using/about-fda.md).
+++

+++**文件提取审批**

*上下文：直邮*

文件提取审批是一个过程，在提取文件发送给外部供应商（如直邮投放）之前，由单独的操作员或操作员组审批提取文件的内容和配置。

了解有关 [文件提取审批](../../delivery/using/validating.md).
+++

+++**过滤维度**

筛选维度是包含数据或属性的架构，查询使用这些数据或属性来筛选所需的行。 筛选维度架构必须直接链接到定义的定向维度，以便Adobe Campaign能够跨数据库联接并返回响应行。

了解有关 [过滤维度](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).
+++

+++**文件夹**

文件夹是一个Explorer视图项，它保存特定数据类型的数据库记录。 用作组织元素的Generic文件夹类型例外，它本身不包含任何数据，仅包含其他文件夹。

了解有关 [文件夹](../../platform/using/adobe-campaign-explorer.md).
+++

+++**文件夹视图**

“文件夹”视图是一种特殊的“资源管理器”文件夹类型，用于显示选定数据类型的所有记录，无论它属于哪个文件夹。 文件夹视图用作管理工具，以管理分布在多个文件夹中的分区数据或数据。

了解有关 [文件夹视图](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Forms**

Forms为特定架构类型定义界面表示。 Forms是一种用于在产品中轻松创建和编辑数据元素的方法，例如收件人、投放和营销活动。 Adobe Campaign中的所有界面元素都是使用Forms在产品本身中创建的。 请注意，表单是可选的，并非所有架构都有表单。

了解有关 [Forms](../../configuration/using/identifying-a-form.md).
+++

<!--
-----USEFUL HERE?-----
+++**Generated SQL query**

The SQL code generated for the underlying database when an operator manipulates a schema. Schemas define the data types that are then implemented using database tables and columns. The SQL generated for schema manipulation (such as in a query) is based on the installed database type. Thus, the database can be swapped to a different type and the queries in Campaign remain unchanged. Adobe refers to this functionality as being database-agnostic.

Learn more about [Generated SQL queries](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++
-->

+++**热图**

Campaign热图是一个显示24小时期间的工作流执行信息的表。 它以小时和5分钟为间隔显示期间内的工作流分布。 热图用于评估服务器负载并确定占用资源最多的工作流活动。

了解有关 [热图](../../workflow/using/heatmap.md).
+++

+++**混合部署**

混合部署是按需服务和部署以一起工作的内部部署软件的组合。

了解有关 [混合部署](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

<!-- added more details but maybe still not clear/useful here? -->
+++**识别模式**

*上下文：Campaign交互*

识别模式是指联系人的状态。 它可以是显式的、隐式的，也可以是匿名的。

* **显式**：联系人登录渠道界面后进行标识。
* **隐含**：联系人已由Cookie（永久或会话）识别。 它可以作为匿名联系人或识别联系人处理。
* **匿名**：无法识别联系人。

了解有关 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

<!--
----NOT USEFUL HERE?----
+++**Image serving**

The functionality that supplies the images embedded in emails to the delivery’s recipients. The insertion of the images based on an emails system’s “download images” functionality is what generates an “open” entry in Campaign’s tracking logs.

Learn more about [Image serving](../../delivery/using/defining-the-email-content.md#adding-images).
+++
-->

+++**入站互动**

*上下文：Campaign交互*

入站交互是指在渠道（例如网络、呼叫中心或移动设备）中联系人操作生成的来话呼叫之后进行的交互。 此类交互通常以单一模式（即每个收件人）处理。

了解有关 [入站互动](../../interaction/using/about-inbound-channels.md).
+++

+++**收件箱呈现**

收件箱呈现是生成电子邮件预览，可确保以最佳方式在各种Web客户端、Web邮件和设备上向收件人显示消息。 Adobe Campaign利用Litmus，允许电子邮件内容创建者在70多个电子邮件渲染程序(如Gmail收件箱或Apple Mail客户端)中预览其消息内容。

了解有关 [收件箱呈现](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**实例设置**

实例设置是Adobe Campaign实例的配置详细信息。 这些设置是在“部署向导”（“工具”>“高级”>“部署向导”）中或在服务器和/或实例配置文件中定义的。

了解有关 [实例设置](../../installation/using/about-initial-configuration.md).

+++

+++**作业（导入和导出）**

作业由向导系统管理，该向导系统简化了数据在产品中的导入和导出。 作业使用模板系统以简化和保持一致性，并且可以定义为按计划执行。

了解有关 [导入和导出作业](../../platform/using/get-started-data-import-export.md).
+++

+++**列表**

列表是一个静态数据集。 列表是从其他来源(Audience Manager、Experience Platform、数据库等)导入Campaign的受众或区段，在界面中将其视为导入的列表。

了解有关 [列表](../../platform/using/creating-and-managing-lists.md).
+++

+++**本地缓存**

本地缓存是存储在操作员计算机上的本地信息。 控制台使用缓存的信息来减少服务器所需的流量并提高性能。 定期清除本地缓存（在“文件”菜单上）可更新所存储的信息，并提高性能和稳定性。

了解有关 [本地缓存](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**营销资源管理(MRM)**

*上下文：营销资源管理(MRM)*

此 **营销资源管理(MRM)** 通过Adobe Campaign中的模块，您可以对涉及的任务、预算和营销资源进行完整管理和实时跟踪，从而在协作模式下控制营销行动。 Adobe Campaign操作员可以通过完整的验证流程和适当的跟踪工具（报告、跟踪批准、通知、论坛等）协调其行动并批准其所有阶段的进度。

了解有关 [MRM](../../mrm/using/about-marketing-resource-management.md).
+++

<!--
----ACS?----
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**已命名权限**

用于定义操作员组访问权限和权限（角色）的粒度数据库访问权限。 命名权限会在产品安装期间通过导入定义工具特定功能的各种包来填充。 可以创建自定义命名权限来支持客户端业务要求。

了解有关 [已命名权限](../../platform/using/access-management-named-rights.md).
+++

+++**命名空间**

命名空间是一个分区，可将客户数据类型与Adobe Campaign在数据模型中的本机数据类型分隔开。 还用于促进定义从一个实例迁移到另一个实例，例如将架构或模板从开发实例移动到生产实例。

了解有关 [命名空间](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

<!--
----generic, not specific to campaign----
+++**Navigation bar**

The navigation bar is the navigation element running across the top of the interface. The navigation bar regroups the various core capabilities of the platform. Click a navigation bar link to display the set of functionalities related to this capability. The list of core capabilities you can access depends on the packages and add-ons you have installed and on your access rights. The purpose of the Navigation bar is to simplify screen management and increase productivity.

Learn more about [Navigation Bar](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++
-->

+++**导航树**

导航树是Adobe Campaign资源管理器视图中的主导航。 导航树的工作方式与文件浏览器类似（例如Windows资源管理器）。 文件夹可能包含子文件夹。 选择某个节点将显示与该节点对应的视图。 显示的视图是与架构关联的列表和用于编辑所选行的输入表单。 您可以自定义导航树并设置文件夹权限。

了解有关 [导航树](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarch).
+++

+++**目标**

*上下文：营销资源管理(MRM)*

在营销活动、项目或计划内，操作员可以声明目标列表。 这些是可达到的量化值。 在营销活动、项目或计划结束时， MRM模块允许操作员在专用报告中比较目标和结果。

了解有关 [目标](../../mrm/using/creating-and-managing-tasks.md#expenses-and-revenues).
+++

+++**优惠目录**

*上下文：Campaign交互*

优惠目录是在Adobe Campaign中定义的一组优惠，可在交互期间选择。 目录按层级进行组织，每个节点对应于一个类别。

了解有关 [优惠目录](../../interaction/using/offer-catalog-overview.md).
+++

+++**优惠联系人**

*上下文：Campaign交互*

优惠联系人是指来自入站交互的联系人。 在引擎调用处理期间，联系人与定位维度相关联。 未识别的匿名联系人将归因于访客定向维度。 有两种类型的联系人，即已识别和匿名：

* **已识别的联系人**：渠道中主动确认的联系人。 在叫客交互中，会自动识别联系人。
* **匿名联系人**：未通过渠道自愿订阅，但可通过Cookie隐式识别的联系人。 此术语仅用于传入交互。

了解有关 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**优惠设计环境**

*上下文：Campaign交互*

选件 **设计环境** 是操作员可在其中创建选件、定义类型规则并选择选件定位的架构的环境。 用于存储所生成的选件建议的表也由环境定义。 默认情况下，交互加载项附带 **设计** 环境和 **实时** 链接到它的环境。 这两个环境都已预配置为定位内置的收件人表。

了解有关 [优惠设计环境](../../interaction/using/fundamental-principles.md).
+++

+++**优惠引擎套利**

*上下文：Campaign交互*

优惠引擎选择将在环境中显示的优惠（符合条件的优惠）。 套利原则根据类别和优惠中定义的标准按优先级对优惠进行排名。

了解有关 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**优惠引擎修剪**

*上下文：Campaign交互*

优惠引擎修剪是删除不符合选择条件的优惠的过程。 在优惠引擎套利步骤之前执行。

了解有关 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**优惠环境**

*上下文：Campaign交互*

优惠环境是根文件夹，用于定义优惠目录、其可用空间和环境的预定义过滤器。 操作员需要为每个定向维度创建一个环境。 有两种类型的选件环境：“设计”和“实时”。

了解有关 [优惠环境](../../interaction/using/fundamental-principles.md).
+++

+++**提供实时环境**

*上下文：Campaign交互*

选件实时环境已链接到活动 **设计环境**. 它包含只读选件，其内容和资格已通过 **设计环境**. 可以选择将它们显示在网站上，或将其插入到出站消息中。

了解有关 [提供实时环境](../../interaction/using/fundamental-principles.md).
+++

+++**优惠呈现规则**

*上下文：Campaign交互*

优惠呈现规则是优惠环境中引用的类型规则，允许操作员通过考虑收件人的建议历史记录排除特定优惠。

了解有关 [优惠呈现规则](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**优惠预览**

*上下文：Campaign交互*

这是选件在其文件夹中显示的预览。 可从优惠预览选项卡或联系人配置文件访问。

了解有关 [优惠预览](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**优惠建议**

*上下文：Campaign交互*

优惠建议是操作的结果，该操作包括在给定优惠空间中向联系人展示优惠，例如网站上的横幅、电子邮件或短信内容。 此结果存储在优惠建议表中，该表定义了优惠、收件人和时间戳，提供了收件人已收到的所有优惠的记录。

了解有关 [优惠建议](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**优惠呈现**

*上下文：Campaign交互*

优惠呈现是渠道用于显示优惠的信息。 优惠表示可以从其上表示优惠的空间或直接输入到界面(例如，在HTML块中)的呈现函数来构建。 优惠可以用空格表示。

了解有关 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**优惠模拟**

*上下文：Campaign交互*

通过优惠模拟，操作员可以测试定义范围（投放日期、目标区段、优惠数量、主题等）内的优惠分发 才实际发送选件。 它可用于调整优惠优先级和资格规则，以最大限度地提高优惠有效性。

了解有关 [优惠模拟](../../interaction/using/about-offers-simulation.md).
+++

+++**优惠空间**

*上下文：Campaign交互*

优惠空间是一个文件夹，用于定义优惠的公开位置。 通过定义空间，您可以指定使用的渠道、构建选件的内容以及指定显示的选件。 优惠空间是渠道和优惠引擎之间的界面。

了解有关 [优惠空间](../../interaction/using/creating-offer-spaces.md).
+++

+++**优惠主题**

*上下文：Campaign交互*

选件主题是在类别中定义的关键字，它允许操作员在显示选件时筛选选件。 主题允许从目录结构中对优惠进行非分层选择。

了解有关 [优惠主题](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**优惠权重**

*上下文：Campaign交互*

优惠权重基于公式，这些公式精确定义了优惠的相关性，以允许引擎选择最相关的优惠。 权重在优惠中定义，乘数在类别中定义。 符合条件的优惠会在降低权重顺序时考虑在内。

了解有关 [优惠权重](../../interaction/using/creating-an-offer.md#offer-weight).
+++

+++**运算符**

操作员是具有登录和执行操作权限的Adobe Campaign用户。 操作员与操作员组相关联，并继承这些组的权限。 您还可以将命名权限直接归因于运算符。

了解有关 [运算符](../../platform/using/access-management-operators.md).
+++

+++**操作员组**

操作员组允许您管理Campaign操作员的角色。 您可以定义赋予权限的运算符组，然后将运算符与一个或多个组相关联。 这使您可以重复使用权限并使操作员配置文件更加一致。 它还便于用户档案的管理和维护。

了解有关 [操作员组](../../platform/using/access-management-groups.md).
+++

+++**选项**

选项是用于定义Campaign实例设置的平台级别变量。 选项可以在平台级别定义时间范围（如数据库清理工作流）或其他全局定义。

了解有关 [选项](../../installation/using/configuring-campaign-options.md).
+++

+++**出站交互**

*上下文：Campaign交互*

出站交互是指从联系人列表（用于投放电子邮件、直邮等）对交互引擎的调用。 相同的规则和流程将应用于每个联系人。 此类交互通常以批处理模式处理。

了解有关 [出站交互](../../interaction/using/about-outbound-channels.md).
+++

+++**资源包导出/导入**

资源包导出是一个操作，它包含生成包含对象定义的XML文件。 包用于将功能和定义从一个实例迁移到另一个实例。 它们还用于向备份和源代码控制系统添加关键产品定义。

了解有关 [资源包导出/导入](../../platform/using/working-with-data-packages.md).
+++

+++**调色板**

工作流面板显示了可添加到工作流的可用活动。 此组件以选项卡形式显示，其中工作流活动按其使用进行逻辑分组。 面板上可用的活动由已安装在Campaign实例中的加载项以及显示工作流的上下文决定。

了解有关 [调色板](../../workflow/using/building-a-workflow.md#adding-and-linking-activities).
+++

+++**性能监控**

性能监视信息显示在“监视”选项卡上。 它显示底层系统的度量，如内存和CPU使用率、SMTP服务器统计信息、服务器进程及其他相关信息。

了解有关 [性能监控](../../production/using/monitoring-processes.md).
+++

+++**个性化块**

Adobe Campaign提供了可在投放中插入的内置个性化块。 它们是动态的、个性化的，并包含特定渲染。 例如，您可以添加徽标、问候语消息或指向镜像页面的链接。 默认情况下，可以使用多个个性化块。 您还可以定义自定义个性化块，以便优化投放个性化。 在投放的分析阶段，实际数据会插入到每个生成的消息中。

了解有关 [个性化块](../../delivery/using/personalization-blocks.md).
+++

+++**个性化字段**

个性化字段是对特定收件人的投放进行个性化时使用的单个数据字段引用。 实际数据值在投放分析阶段插入。

了解有关 [个性化字段](../../delivery/using/personalization-fields.md).
+++

+++**个性化变量**

个性化变量是投放中的代码段，可根据收件人信息向不同收件人显示不同的文本。 这些字段可以作为个性化字段或块实施。

了解有关 [个性化变量](../../delivery/using/about-personalization.md).
+++

+++**计划**

计划是一种文件夹类型，用于按日历组织营销活动。 资源管理器视图中的计划文件夹定义基于时间的单位，如年、季度或月。 计划文件夹可以嵌套，并可以包含其他Plan文件夹、项目文件夹或营销活动。

了解有关 [计划](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**预定义过滤器**

预定义过滤器是已保存以供重复使用的查询。 使用预定义过滤器可以提高生产效率（因为它们只创建一次），有助于建立一致性（因为所有营销人员都可以使用它们）并降低营销人员所需的技能，因为他们可以使用他们自己可能无法创建的代码或逻辑。

了解有关 [预定义过滤器](../../platform/using/creating-filters.md#filtering-recipients).
+++

<!--
----DEPRECATED----
+++**Predictive Engagement Scoring**

Predictive engagement scoring predicts the probability of a recipient engaging with a message and the probability of opting out (unsubscribing) within the next seven days after the next email send. The probabilities are further divided into buckets according to the specific risk of disengagement, medium, or low. The model also provides the risk percentile rank for the customers to understand where the rank of a certain customer in relation to others. 

Learn more about [Predictive Engagement Scoring](../../platform/using/creating-filters.md).
+++
-->

+++**主键**

主键是数据库表中每个记录的唯一标识符。 表必须至少有一个键。 通常，键在架构的主元素和索引之后声明。 主键不能是复合键（包括多个字段）。

了解有关 [主键](../../configuration/using/schema/key.md).
+++

+++**用户档案**

用户档案是代表最终客户、潜在客户或潜在客户的信息记录。 每个配置文件对应于nmsRecipient表或外部表中的记录，该记录包含cookie ID、客户ID、移动标识符或与特定渠道相关的其他信息。

了解有关 [配置文件](../../platform/using/about-profiles.md).
+++

+++**项目**

项目和子项目群文件夹围绕业务目标（如忠诚度、客户获取或交叉销售）组织营销活动。 它们还可以代表财政周期或竞选策略，如事件或新闻稿。 每个项目都包含链接到日历的活动，日历提供了概览。

了解有关 [程序](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**公共资源**

Adobe Campaign中的公共资源文件夹包含由应用程序服务器托管的图像。 投放中的图像必须发布到应用程序服务器（或者，如果配置了Campaign，则发布到图像托管服务器），才能显示在投放中，例如电子邮件。

了解有关 [公共资源](../../installation/using/deploying-an-instance.md#managing-public-resources).
+++

+++**推送**

*上下文：移动设备应用程序渠道*

推送通知是移动应用程序收到的消息。 通过在移动应用程序中包含Experience PlatformSDK代码，将推送通知配置为与Adobe Campaign配合使用。 对于推送，提供了两个投放渠道：iOS和Android。

了解有关 [推送](../../delivery/using/about-mobile-app-channel.md).
+++

## Q - T {#sec-5}

+++**收件人**

在Adobe Campaign中，收件人是发送投放内容（电子邮件、短信等）所定位的默认用户档案 给您的客户。 通过存储在数据库中的收件人数据，可筛选目标并添加个性化数据。 通常，这些信息包括个人、联系人、人口统计和事务性信息，但也可以是支持营销和分析的任何类型的信息。

了解有关 [收件人](../../configuration/using/about-data-model.md).
+++

+++**渲染函数**

*上下文：Campaign交互*

渲染函数在选件空间中定义。 它用于根据优惠中定义的属性构建其优惠表示形式。 呈现功能模式有三种：HTML、XML和文本。

了解有关 [渲染函数](../../interaction/using/creating-offer-spaces.md).
+++

<!--
-----DID NOT FIND IN ACC DOCS, ACS?----
+++**Retargeting campaigns**

Campaigns that re-target the recipients of a previous delivery or deliveries.
+++
-->

+++**架构**

架构是与数据库表关联的XML文档。 它定义数据结构并描述表的SQL定义。 操作员在Campaign中操作架构，产品将其操作转换为所需的SQL，然后针对数据库执行。

了解有关 [架构](../../configuration/using/about-schema-reference.md).
+++

+++**架构扩展**

架构扩展允许您自定义开箱即用的架构，以最符合您的业务用例。 例如，您可以将“忠诚度”字段添加到收件人表。

了解有关 [架构扩展](../../configuration/using/extending-a-schema.md).
+++

+++**种子地址**

种子地址用于定位不符合既定目标标准的收件人。这样，超出投放范围的收件人可以像任何其他目标收件人一样接收投放。 可以将测试用户档案添加到消息的受众，以检测收件人数据库是否用于任何欺诈行为，或确保投放。

了解有关 [种子地址](../../delivery/using/about-seed-addresses.md).
+++

<!--
-------ACS?-----
+++**Send-time optimization**

To improve the open rate of your messages, you can manually define a sending time per recipient. Each profile will receive the message at the specified date and time, whenever possible. Defining a sending time can be done at the delivery level or using a workflow.

Learn more about [Send-time optimization](../../delivery/using/about-seed-addresses.md:).
+++
-->

+++**服务**

Adobe Campaign允许您创建和管理新闻稿或产品更新等信息服务，并管理这些服务的订阅。 多个服务可以并行定义。

了解有关 [服务](../../delivery/using/about-services-and-subscriptions.md).
+++

+++**SFTP管理**

在控制面板中，您可以与连接到您有权访问的 Campaign 实例的所有 SFTP 服务器进行交互。控制面板允许您对SFTP服务器执行各种操作，如监视存储容量、管理IP地址允许列表和管理公共SSH密钥。

了解有关 [SFTP管理](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/about-sftp-management.html).
+++

+++**订阅服务活动**

利用订阅服务工作流活动，可以为过渡中指定的群体创建或删除对信息服务的订阅。

了解有关 [订阅服务活动](../../workflow/using/subscription-services.md).
+++

+++**目标审批**

*上下文： Campaign分布式营销*

目标批准是指在发送投放之前，由一个单独的操作员或一组操作员批准投放的最终目标（在分析阶段生成目标后）的过程。

了解有关 [目标审批](../../workflow/using/local-approval.md).
+++

+++**目标数据**

目标数据是存储在工作流的工作台（过渡）中的数据。 此数据可在投放内部使用，用于个性化投放内容或定义投放动态元素的逻辑。

了解有关 [目标数据](../../workflow/using/data-life-cycle.md#target-data).
+++

+++**目标映射**

目标映射是投放渠道到特定数据类型的映射。 目标映射定义不同投放渠道如何链接到架构的数据字段。 它定义Campaign如何使用特定字段或表达式发送到该数据类型。

了解有关 [目标映射](../../delivery/using/selecting-a-target-mapping.md).
+++

+++**定位活动**

定位活动是特定于定位、处理群体数据和过滤活动的工作流活动。 它们允许操作员通过定义集并使用交集、并集或排除操作拆分或组合这些集来构建一个或多个目标。

了解有关 [定位活动](../../workflow/using/about-targeting-activities.md).
+++

+++**定位维度**

定位维度是由查询或其他工作流活动生成（返回）的数据类型。 请注意，无论使用什么查询获取响应数据库行，Adobe Campaign都只返回这些行的主键。

了解有关 [定位维度](../../workflow/using/targeting-data.md).
+++

+++**任务活动**

*上下文：营销资源管理(MRM)*

“任务”工作流活动将人工操作并入工作流的逻辑中。 您可以指定两种方案：第一种是已完成任务的情况，第二种是未完成任务的情况。 典型用例用于将离线操作并入营销策划或自定义操作，例如批准。

了解有关 [任务活动](../../workflow/using/task.md).
+++

<!--
-----NOT USEFUL, detail-----
+++**Task**

One iteration of the defined functionality of a workflow activity. Each execution of a task has a unique task identifier.   

Learn more about [Tasks](../../workflow/using/about-workflows.md).
+++
-->

+++**模板**

模板是用于创建对象的设计元素。 它包含对象设置以及可选的对象内容。 模板系统用于创建Adobe Campaign的投放、营销策划、工作流和许多其他元素。 可用的工厂模板由安装的软件包定义。 之后，可根据Campaign操作员的需要复制和自定义模板。
+++

<!--
-----ACS -> SEEDS IN ACC-----
+++**Test profiles**

Allows targeting of additional recipients who do not match the defined targeting criteria. They are added to a message’s audience to detect any fraudulent use of your recipient database or to ensure delivery. Seen as the Seed type in the Campaign interface.

Learn more about [Test profiles](../../workflow/using/about-workflows.md).
+++
-->

<!--
-----NOT FOR DOCS?-----
+++**Total database storage**

The aggregate size of the production and non-production instance(s) database storage managed by Adobe. 

Learn more about [Total database storage](../../workflow/using/about-workflows.md).
+++
-->

+++**跟踪日志**

在发送投放并激活跟踪后，跟踪技术工作流会检索跟踪数据。 此数据可在投放的“跟踪”选项卡中找到。 您可以查找有关打开数的信息，以及电子邮件或其他与收件人所收到邮件交互的点击数。

了解有关 [跟踪日志](../../delivery/using/accessing-the-tracking-logs.md).
+++

+++**交易型消息传递**

事务性消息传递是一个Campaign模块，旨在管理从外部信息系统发送的事件生成的自定义触发器通知。 事务型消息是由提供程序（如网站）实时发送的单个且唯一的通信。 由于它包含收件人要检查或确认的重要信息，因此尤其需要使用。

了解有关 [事务性消息传递](../../message-center/using/about-transactional-messaging.md).
+++

&lt;!-------在这里很有用??----->
+++**触发的营销活动**

触发的活动是在工作流中收到API请求时执行的活动。 API调用由启动工作流执行的工作流中的信号活动使用。

了解有关 [已触发的营销活动](../../workflow/using/external-signal.md).
+++

<!--
-----NOT USEFUL-----
+++**Triggers**

Signals that initiate execution of a workflow, delivery or other action. Typically an API call. 

Learn more about [Triggers](../../workflow/using/about-workflows.md).
+++
-->

+++**类型**

*上下文：活动优化*

分类是应用于投放分析阶段的一组分类规则。 活动分类可以包含多个分类规则，但投放只能引用一个分类。

了解有关 [类型](../../campaign-opt/using/about-campaign-typologies.md#typologies).
+++

+++**类型规则**

*上下文：活动优化*

分类规则是在投放的分析阶段中实施的业务规则。 分类规则是对投放内容（控制规则）或投放目标（筛选规则）或强制执行业务要求的其他逻辑（压力规则）的检查。 规则是可包含在一个或多个分类中的粒度元素。

了解有关 [类型规则](../../campaign-opt/using/about-campaign-typologies.md#typology-rules).
+++

## U - Z {#sec-6}

+++**单一模式**

*上下文：Campaign交互、事务性消息传递*

在单一模式下，选件引擎会在运行时处理单个联系人。 此模式通常用于入站交互和事务性消息。

了解有关 [单一模式](../../interaction/using/about-inbound-channels.md).
+++

+++**Web应用程序**

Web应用程序是由Campaign实例托管的动态和交互式应用程序页面。 它们包含来自数据库的数据和适应所连接用户的权限的内容。 例如，可在外联网上创建编辑表单，或创建通知表单，包括来自具有表、图表、输入表单等内容的数据库的数据。 此功能允许您设计和发布网页，用户可以在其中查找或输入信息。

了解有关 [Web应用程序](../../web/using/about-web-applications.md).
+++

+++**工作流**

工作流是营销活动执行流的可视表示形式。 它允许您在应用程序服务器的不同模块之间编排所有流程和任务。 您可以利用这个全面的图形环境设计各式流程，包括部分划分、活动执行、文件处理、人员参与等。工作流引擎会执行并跟踪这些流程。

了解有关 [工作流](../../workflow/using/about-workflows.md).
+++

+++**工作流日志**

工作流日志是工作流的逐步执行日志。 它包含工作流的所有历史记录或审核跟踪。 它用于开发、故障诊断或调试。

了解有关 [工作流日志](../../workflow/using/monitoring-workflow-execution.md).
+++

+++**工作台**

工作台包含工作流过渡所携带的所有信息。 每个工作流均使用多个工作表。工作表保存了其原始活动的结果，其内容用作工作流中下一个（已连接）活动的输入。  操作（扩展、自定义）工作表是Adobe Campaign运算符的主要技能之一。

了解有关 [工作台](../../workflow/using/about-workflows.md).
+++
