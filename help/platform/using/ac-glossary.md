---
product: campaign
title: Adobe Campaign术语表
description: Adobe Campaign术语表
role: User, Data Architect
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: 9900fb627dfb310e8f34735a502997ef8e24e769
workflow-type: tm+mt
source-wordcount: '5993'
ht-degree: 3%

---

# Adobe Campaign术语表{#ac-glossary}

以下是Adobe Campaign中关键术语和概念的定义，以及相关文档的链接。 单击某个术语以显示其定义。

## A - D{#sec-1}

+++**A/B 测试**

A/B测试是一项功能，允许用户定义两到三个电子邮件变体：每个变体都会发送到群体样本，以确定哪个变体效果最佳。 确定之后，会将入选的变体发送给其余群体。

详细了解 [A/B测试](../../delivery/using/get-started-a-b-testing.md).
+++

+++**访问管理**

访问管理允许管理员为Adobe Campaign的用户分配访问权限和权限。 权限包括能够查看和/或使用Adobe Campaign功能，例如执行工作流、定义架构和管理受众。

详细了解 [访问管理](access-management.md).
+++

+++**ACS 连接器**

ACS Connector(Prime Offering)连接了Adobe Campaign v7和Adobe Campaign Standard。 它是Campaign v7中的一项集成功能，可自动将数据复制到Campaign Standard，从而将两个应用程序中的最佳功能结合起来。 Campaign v7具有用于管理主营销数据库的高级工具。 Campaign v7中的数据复制允许Campaign Standard在用户友好的环境中利用丰富的数据。

详细了解 [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++

+++**活动**

活动是添加到工作流中以定义执行功能的面板项目。 活动是用于执行任务的容器。 在工作流中，给定的活动可以生成多个任务，尤其是当存在循环或重复（定期）操作时。

详细了解 [工作流活动](../../workflow/using/about-activities.md).
+++

+++**活动用户档案**

如果用户档案在过去 12 个月中通过任何渠道被定向或与其联系，则视为处于活动状态。根据您的合同，您的每个Campaign实例都会配置特定数量的活动用户档案，这些活动用户档案会被计为计费用。

详细了解 [活动用户档案](../../platform/using/about-profiles.md#active-profiles).
+++

+++**审批工作流活动**

*上下文：Campaign分布式营销*

本地批准活动是一个工作流活动，用于在发送消息之前设置投放批准流程。

进一步了解 [本地批准活动](../../workflow/using/local-approval.md).
+++

+++**受众**

受众是根据规则和属性生成的一组符合过滤器定义标准的用户档案。

详细了解 [受众](../../campaign/using/marketing-campaign-target.md).
+++

+++**审核跟踪**

审核跟踪可实时捕获在您的Adobe Campaign实例内发生的操作和事件的完整列表。 它包括一种访问数据历史的自助方式，可帮助回答以下问题：工作流发生的事件、上次更新这些事件的人员或用户在实例中执行的操作。

详细了解 [审核跟踪](../../production/using/audit-trail.md).
+++

<!--
----DUPLICATE WITH THE "CAMPAIGN" ENTRY?---
+++**Automated campaigns**

Campaigns that run on a schedule, such as for targeting recipients who have a birthday or an anniversary. Can also be used to execute look-ahead and look-back logic, such as who purchased yesterday or who has a payment due tomorrow.

Learn more about [Campaigns](../../campaign/using/designing-marketing-campaigns.md).
+++
-->

+++**批处理模式**

*上下文：营销活动互动*

在促销活动交互的上下文中，批量模式允许选件引擎为一组联系人选择最佳选件（或选件）。 资格/优先级规则将应用于集合的所有联系人。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**营销活动**

营销活动是协调、定义和执行营销活动的界面。 营销活动可以将一个或多个工作流、投放、文档和其他相关数据点包含到一个易于使用的界面中。

详细了解 [促销活动](../../campaign/using/designing-marketing-campaigns.md).
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

信道是发送通信的媒介。 Adobe Campaign中的内置渠道包括电子邮件、短信、直邮、推送通知、LINE和Twitter。 可以根据非标准渠道要求实施自定义渠道。

详细了解 [渠道](../../delivery/using/communication-channels.md).
+++

+++**客户端控制台**

Campaign客户端控制台是一个富客户端，可让您连接到Campaign应用程序服务器。 客户端控制台可执行文件(.exe)应用程序安装在具有Microsoft Windows操作系统的计算机上。 Campaign客户端控制台集中化了所有功能和设置。

详细了解 [客户端控制台](../../platform/using/adobe-campaign-workspace.md).
+++

+++**内容审批**

内容批准是指在发送投放内容之前，由单独的操作员或操作员组批准该投放的内容。

详细了解 [内容批准](../../campaign/using/marketing-campaign-approval.md).
+++

+++**控制组**

使用控制组通过排除部分控制组受众来衡量活动的影响。 操作员可以比较收到消息的目标群体的行为与非目标联系人的行为。 根据发送日志，操作员还可以在将来的营销活动中定位控制组。

详细了解 [内容组](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).
+++

+++**控制面板**

该控制面板允许Adobe Campaign的产品管理员管理其每个实例的设置和跟踪使用情况，从而帮助他们提高工作效率。 其直观的界面让用户能够轻松监控关键资产的使用情况，并执行管理任务，如IP地址允许列表添加、SFTP存储监控、密钥管理等。

详细了解 [内容面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hans).
+++

+++**多维数据集**

*上下文：营销分析*

多维数据集是一种Adobe Campaign直观的数据探索工具，可帮助用户创建和共享动态报告。

详细了解 [多维数据集](../../reporting/using/about-cubes.md).
+++

+++**自定义资源**

Adobe Campaign提供了预定义的数据模型，其中数据类型通过安装各种包来定义。 操作员可以通过扩展资源以添加自定义字段或自定义表（如事务表或产品表）来扩充提供的数据模型。

详细了解 [自定义资源](../../configuration/using/about-schema-edition.md).
+++

+++**数据模型**

Campaign数据模型是一组架构，用于定义数据类型及其关系（链接）。 数据模型是抽象定义，物理上使用包含实际数据的数据库来实现。

详细了解 [数据模型](../../configuration/using/about-data-model.md).
+++

+++**数据库清理工作流**

数据库清理工作流会删除过时的数据，以避免数据库呈指数级增长。 工作流会自动触发，无需用户干预。

详细了解 [数据库清理工作流](../../production/using/database-cleanup-workflow.md).
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

*上下文：电子邮件投放能力*

投放能力允许您衡量活动是否成功到达收件人的收件箱，而不会出现弹回或标记为垃圾邮件。 更准确地说，电子邮件投放能力是指一组特征，这些特征决定了消息在短时间内通过个人电子邮件地址到达其目标的能力，并在内容和格式方面具有预期质量。

详细了解 [投放能力](../../delivery/using/about-deliverability.md).
+++

+++**投放**

投放是指在特定渠道（电子邮件、短信、推送通知等）上发送给受众的特定营销通信项目。 在营销术语中也称为“接触”。

详细了解 [投放](../../delivery/using/communication-channels.md).
+++

+++**投放分析**

投放分析是投放的准备。 此过程将内容与收件人用户档案数据组合在一起，生成收件人收到的个性化电子邮件。 投放分析逻辑可以根据定义的逻辑将收件人从目标中排除或完全停止投放。 此过程还包括评估动态内容逻辑和插入特定于单个收件人用户档案的选件。

详细了解 [投放分析](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
+++

+++**投放日志**

投放日志包含发送消息时生成的信息。 这些日志显示发送的详细信息，即已准备、忽略、发送或失败的消息。 可直接从投放仪表板访问它们。

详细了解 [投放日志](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).
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

投放大纲是一组结构化元素（文档、商店、促销优惠券等） 由公司创建，用于特定营销活动。 它用于直邮投放的上下文。

详细了解 [直邮](../../delivery/using/about-direct-mail-channel.md).
+++

+++**部署向导**

部署向导定义Campaign实例的参数，如默认命名空间、数据库清理计划、数据保留期和其他技术设置。

详细了解 [部署向导](../../installation/using/deploying-an-instance.md#deployment-wizard).
+++

+++**描述性分析**

描述性分析是一种上下文相关的报告工具，可用于检查工作流工作台中的数据、在文件夹中选择的数据，或对选定投放的目标和排除项进行深入挖掘。

详细了解 [描述性分析](../../reporting/using/about-descriptive-analysis.md)
+++

+++**分布式营销**

*上下文：分布式营销*

向Campaign运营商提供的分布式营销附加组件是一个协作工作区，用于在中心实体（总部、营销部门等）之间实施营销活动 实施协作营销活动。此合作基于称为 **Campaign包列表**，其中向本地实体提供了集中创建的营销活动模板和实例。

详细了解 [分布式营销](../../distributed/using/about-distributed-marketing.md)
+++

+++**值分布**

值分布是一个工具，用于显示当前存在于数据库中的架构属性的值分布。 这有助于您确定哪些值可用、其计数和百分比，并避免在创建查询或表达式时出现值大小写和拼写问题。

详细了解 [值分布](../../platform/using/defining-filter-conditions.md#selecting-data-to-extract)
+++

+++**域委派**

子域配置允许您配置域的子区域（技术上称为“DNS区域”）以与Adobe Campaign一起使用。
通过域委派，Adobe可以控制并维护发送、渲染和跟踪电子邮件促销活动所需的DNS的所有方面。

详细了解 [域委派](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=zh-Hans)
+++

## E - H {#sec-2}

<!--
----DEPREACTED----
+++**E4X**

The version of Javascript that is used in Adobe Campaign Classic. Sometimes called ECMAScript, it is an extension of Javascript that allows the mixing of Javascript and XML primitives in the same code. Note that E4X is classified as a deprecated language. 
+++
-->

+++**资格规则**

*上下文：营销活动互动*

资格规则是对与有效期、目标和权重有关的环境、类别或选件应用的限制。 它们允许操作员确保选件与目标联系人保持一致。 在选件环境中，资格规则包括应用于选件和目标收件人的演示规则。 在类别中，资格规则允许操作员及时限制类别的有效性、定义应用程序主题并确定要定向的收件人。 它们还可以定义给定时间段的乘数权重。 这样，运算符就可以共享其他类别中选件的规则，从而简化其管理。 在选件中，资格规则允许操作员及时限制选件的有效性并确定要定向的收件人。

详细了解 [资格规则](../../interaction/using/interaction-and-offer-management.md).
+++

+++**合格选件**

*上下文：营销活动互动*

符合条件的选件是指满足上游定义的限制且始终能够提供给目标的选件。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**电子邮件密件抄送**

电子邮件密件抄送功能会以EML格式发送一封对应已送达电子邮件的确切副本，该副本将保存到专用的密件抄送电子邮件地址，发件人可在外部系统中处理和存档这些电子邮件。

详细了解 [电子邮件密送](../../delivery/using/email-parameters.md#email-bcc).
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

扩充活动是一种高级工作流活动，允许操作员扩充将在工作流中处理的生成的工作表数据。 此活动通常用于定向活动或导入文件后以及使用定向数据的活动之前。 增强功能可以转换集客过渡数据并配置活动以使用增强的数据完成输出过渡。 它允许操作员合并多个数据集中的数据，或创建指向临时资源的链接。

详细了解 [扩充活动](../../workflow/using/enrichment.md).
+++

+++**明细列表**

枚举是在架构中或在平台级别定义的数据类型，用于定义字段的有效输入值。 枚举在用户界面和查询生成器中显示为选取列表。

详细了解 [枚举](../../platform/using/managing-enumerations.md).
+++

+++**浏览器视图**

Explorer视图是包含Adobe Campaign工件和数据的文件夹的分层显示。 请注意，Adobe Campaign中的文件夹系统与典型树状视图的功能不同，因为每个文件夹都包含特定类型的数据，如“投放”、“工作流”或“选件”。

详细了解 [浏览器视图](../../platform/using/adobe-campaign-explorer.md).
+++

+++**外部帐户**

外部帐户是产品连接到其他环境和技术的入口和出口点。 外部帐户定义产品用于向其他来源发送数据或从其他来源接收数据的连接参数。 典型的外部帐户类型包括SFTP站点的连接、用于支持发送短信的电信、用于处理退回的邮箱，或与外部数据库的连接。

详细了解 [外部帐户](../../installation/using/external-accounts.md).
+++

+++**疲劳管理**

*上下文：促销活动优化*

疲劳管理可帮助您控制消息的频率和数量，以避免收件人过度通信，通常使用分类规则来应用。

详细了解 [疲劳管理](../../campaign-opt/using/pressure-rules.md).
+++

+++**联合数据访问 (FDA)**

联合数据访问支持扩展客户端数据模型以包含第三方数据库。 它将自动检测目标表的结构并使用SQL源中的数据。 您无需更改Adobe Campaign数据的结构即可访问外部数据。

详细了解 [联合数据访问](../../installation/using/about-fda.md).
+++

+++**文件提取批准**

*上下文：直邮*

文件提取批准是指在将提取的文件发送到外部供应商（如直邮投放）之前，由单独的操作员或操作员组批准其内容和配置的过程。

详细了解 [文件提取批准](../../delivery/using/validating.md).
+++

+++**过滤维度**

筛选维度是一种架构，其中包含查询用于筛选所需行的数据或属性。 筛选维度架构必须直接链接到定义的定向维度，以便Adobe Campaign能够跨数据库连接并返回响应行。

详细了解 [筛选维度](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).
+++

+++**文件夹**

文件夹是一个Explorer视图项，它保存特定数据类型的数据库记录。 “通用”文件夹类型是例外，该文件夹类型用作组织元素，并且本身不包含任何数据，仅包含其他文件夹。

详细了解 [文件夹](../../platform/using/adobe-campaign-explorer.md).
+++

+++**文件夹视图**

“文件夹”视图是一种特殊的资源管理器文件夹类型，用于显示选定数据类型的所有记录，无论它属于哪个文件夹。 文件夹视图用作管理多个文件夹之间分发的分区数据或数据的管理工具。

详细了解 [文件夹视图](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Forms**

Forms定义特定架构类型的界面表示形式。 Forms是轻松创建和编辑产品中数据元素（如“收件人”、“投放”和“营销活动”）的方法。 Adobe Campaign中的所有界面元素均使用Forms在产品本身中创建。 请注意，表单是可选的，并非所有架构都具有表单。

详细了解 [Forms](../../configuration/using/identifying-a-form.md).
+++

<!--
-----USEFUL HERE?-----
+++**Generated SQL query**

The SQL code generated for the underlying database when an operator manipulates a schema. Schemas define the data types that are then implemented using database tables and columns. The SQL generated for schema manipulation (such as in a query) is based on the installed database type. Thus, the database can be swapped to a different type and the queries in Campaign remain unchanged. Adobe refers to this functionality as being database-agnostic.

Learn more about [Generated SQL queries](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++
-->

+++**热图**

Campaign热图是一个显示24小时工作流执行信息的表。 它按小时和5分钟间隔显示整个时段的工作流分布。 热图用于评估服务器负载并确定消耗最多资源的工作流活动。

详细了解 [热图](../../workflow/using/heatmap.md).
+++

+++**混合部署**

混合部署是按需服务与部署在一起运行的内部部署软件的组合。

详细了解 [混合部署](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

<!-- added more details but maybe still not clear/useful here? -->
+++**识别模式**

*上下文：营销活动互动*

识别模式是指联系人的状态。 它可以是显式的、隐式的或匿名的。

* **显式**:联系人在登录渠道界面后即被识别。
* **隐式**:联系人已通过cookie（永久或会话）进行识别。 它可以作为匿名或已识别的联系人进行处理。
* **匿名**:无法识别联系人。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

<!--
----NOT USEFUL HERE?----
+++**Image serving**

The functionality that supplies the images embedded in emails to the delivery’s recipients. The insertion of the images based on an emails system’s “download images” functionality is what generates an “open” entry in Campaign’s tracking logs.

Learn more about [Image serving](../../delivery/using/defining-the-email-content.md#adding-images).
+++
-->

+++**入站互动**

*上下文：营销活动互动*

集客互动是指在通过渠道中联系人的操作（如Web、呼叫中心或移动设备）生成的来话呼叫之后进行的交互。 此类交互通常以单一模式（即每个收件人）进行处理。

详细了解 [入站互动](../../interaction/using/about-inbound-channels.md).
+++

+++**收件箱呈现**

收件箱呈现是生成电子邮件预览，确保以最佳方式在各种Web客户端、Web邮件和设备上向收件人显示消息。 Adobe Campaign利用Litmus，该工具允许电子邮件内容创建者在70多个电子邮件渲染器(如Gmail收件箱或Apple Mail客户端)中预览其邮件内容。

详细了解 [收件箱呈现](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**实例设置**

实例设置是Adobe Campaign实例的配置详细信息。 这些设置在部署向导（“工具”>“高级”>“部署向导”）或服务器和/或实例配置文件中定义。

详细了解 [实例设置](../../installation/using/about-initial-configuration.md).

+++

+++**作业（导入和导出）**

作业由向导系统管理，该系统可简化数据导入和导出产品的过程。 作业使用模板系统以实现简单性和一致性，并且可以定义为按计划执行。

详细了解 [导入和导出作业](../../platform/using/get-started-data-import-export.md).
+++

+++**列表**

列表是静态数据集。 列表是从其他源(Audience Manager、Experience Platform、数据库等)导入Campaign的受众或区段，在界面中显示为“导入的列表”。

详细了解 [列表](../../platform/using/creating-and-managing-lists.md).
+++

+++**本地缓存**

本地缓存是在操作员计算机上本地存储的信息。 控制台会使用缓存信息来减少服务器所需的流量并提高性能。 定期清除本地缓存（在“文件”菜单上）会更新存储的信息，并提高性能和稳定性。

详细了解 [本地缓存](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**营销资源管理(MRM)**

*上下文：营销资源管理(MRM)*

的 **营销资源管理(MRM)** Adobe Campaign中的模块通过提供所涉任务、预算和营销资源的完整管理和实时跟踪，使您能够以协作模式控制营销操作。 Adobe Campaign操作员可以通过完整的验证流程和适当的跟踪工具来协调其操作并批准其在所有阶段的进度：报告、审批跟踪、通知、论坛等。

详细了解 [MRM](../../mrm/using/about-marketing-resource-management.md).
+++

<!--
----ACS?----
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**已命名权限**

用于定义操作员组访问权限和权限（角色）的粒度数据库访问权限。 在产品安装期间，通过导入定义工具特定功能的各种包来填充命名权限。 可以创建自定义命名权限以支持客户端业务要求。

详细了解 [已命名权限](../../platform/using/access-management-named-rights.md).
+++

+++**命名空间**

命名空间是一个分区，用于将客户数据类型与数据模型中Adobe Campaign的本机数据类型分隔开。 还用于促进定义从一个实例迁移到另一个实例，例如将架构或模板从开发实例移动到生产实例。

详细了解 [命名空间](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

<!--
----generic, not specific to campaign----
+++**Navigation bar**

The navigation bar is the navigation element running across the top of the interface. The navigation bar regroups the various core capabilities of the platform. Click a navigation bar link to display the set of functionalities related to this capability. The list of core capabilities you can access depends on the packages and add-ons you have installed and on your access rights. The purpose of the Navigation bar is to simplify screen management and increase productivity.

Learn more about [Navigation Bar](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++
-->

+++**导航树**

导航树是Adobe Campaign的Explorer视图中的主导航。 导航树的工作方式类似于文件浏览器（例如Windows资源管理器）。 文件夹可能包含子文件夹。 选择节点后，将显示与该节点对应的视图。 显示的视图是与架构关联的列表以及用于编辑所选行的输入表单。 您可以自定义导航树并设置文件夹的权限。

详细了解 [导航树](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarch).
+++

+++**目标**

*上下文：营销资源管理(MRM)*

在营销策划、项目策划或计划中，操作员可以声明目标列表。 这些是要达到的量化值。 在营销活动、项目或计划结束时，MRM模块允许操作员在专用报告中比较目标和结果。

详细了解 [目标](../../mrm/using/creating-and-managing-tasks.md#expenses-and-revenues).
+++

+++**优惠目录**

*上下文：营销活动互动*

选件目录是在Adobe Campaign中定义的一组选件，可在交互过程中进行选择。 该目录以对应于一类别的每个节点来分层组织。

详细了解 [优惠目录](../../interaction/using/offer-catalog-overview.md).
+++

+++**选件联系人**

*上下文：营销活动互动*

选件联系人是来自集客互动的联系人。 在引擎调用处理期间，联系人与定向维度关联。 未识别的匿名联系人将归属于访客定位维度。 有两种类型的联系人：已识别和匿名：

* **已识别的联系人**:已在频道上自愿识别的联系人。 在叫客交互中，联系人会被自动识别。
* **匿名联系人**:未通过渠道自愿订阅，但可通过Cookie隐式识别的联系人。 此术语仅用于传入交互。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**选件设计环境**

*上下文：营销活动互动*

选件 **设计环境** 是运算符在其中创建选件、定义分类规则以及选择选件所定向的架构的环境。 用于存储所生成的优惠建议的表也由环境定义。 默认情况下， Interaction附加组件附带 **设计** 环境和 **实时** 链接到该环境。 这两个环境都已预配置为定向内置的收件人表。

详细了解 [选件设计环境](../../interaction/using/fundamental-principles.md).
+++

+++**优惠引擎套利**

*上下文：营销活动互动*

选件引擎会选择将在环境中显示的选件（符合条件的选件）。 套利原则根据类别和报价中定义的标准，按优先级对报价进行排序。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**优惠引擎修剪**

*上下文：营销活动互动*

选件引擎修剪是删除不符合选择条件的选件的过程。 在优惠引擎套利步骤之前执行。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**选件环境**

*上下文：营销活动互动*

选件环境是根文件夹，用于定义选件目录、其可用空格和环境的预定义过滤器。 操作员需要为每个定向维度创建一个环境。 选件环境有两种类型：设计和实时。

详细了解 [选件环境](../../interaction/using/fundamental-principles.md).
+++

+++**选件实时环境**

*上下文：营销活动互动*

选件实时环境已链接到营销活动 **设计环境**. 它包含已通过 **设计环境**. 可以选择在网站上演示或插入到出站消息中。

详细了解 [选件实时环境](../../interaction/using/fundamental-principles.md).
+++

+++**选件演示规则**

*上下文：营销活动互动*

选件演示规则是选件环境中引用的分类规则，允许运算符通过考虑收件人的建议历史来排除特定选件。

详细了解 [选件演示规则](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**优惠预览**

*上下文：营销活动互动*

这是选件在其文件夹中显示的预览。 可从选件预览选项卡或联系人资料访问选件。

详细了解 [选件预览](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**优惠建议**

*上下文：营销活动互动*

选件建议是该操作的结果，该操作包括在给定选件空间中向联系人展示选件，例如网站上的横幅、电子邮件或短信内容。 此结果存储在选件建议表中，该表定义了选件、收件人和时间戳，提供了收件人收到的所有选件的记录。

详细了解 [提供建议](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**选件演示**

*上下文：营销活动互动*

选件表示是渠道用于显示选件的信息。 选件表示可以由表示选件的空间的呈现函数构建，或直接输入到界面(例如，在HTML块中)中。 选件可以由空格表示。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**优惠模拟**

*上下文：营销活动互动*

通过选件模拟，操作员可以测试在定义范围（投放日期、目标区段、选件数量、主题等）中的选件分发 发送选件之前。 它可用于调整选件优先级和资格规则，以最大限度地提高选件的有效性。

详细了解 [优惠模拟](../../interaction/using/about-offers-simulation.md).
+++

+++**优惠空间**

*上下文：营销活动互动*

选件空间是一个文件夹，用于定义选件的显示位置。 通过定义空格，您可以指定使用的渠道、构建选件的内容，以及指定显示的选件。 选件空间是渠道与选件引擎之间的接口。

详细了解 [选件空间](../../interaction/using/creating-offer-spaces.md).
+++

+++**选件主题**

*上下文：营销活动互动*

选件主题是类别中定义的关键词，允许操作员在显示选件时对其进行过滤。 主题允许从目录结构中非分层选择选件。

详细了解 [选件主题](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**选件权重**

*上下文：营销活动互动*

选件权重基于精确定义选件相关性的公式，以便引擎选择最相关的选件。 权重在选件中定义，乘数在类别中定义。 在减轻重量顺序时，将考虑符合条件的选件。

详细了解 [选件权重](../../interaction/using/creating-an-offer.md#offer-weight).
+++

+++**操作员**

操作员是具有登录和执行操作权限的Adobe Campaign用户。 操作员与操作员组关联，并继承这些组的权限。 您还可以将命名权限直接归因到运算符。

详细了解 [运算符](../../platform/using/access-management-operators.md).
+++

+++**运算符组**

操作员组允许您管理Campaign操作员的角色。 您可定义属于权限的运算符组，然后将运算符与一个或多个组关联。 这样，您就可以重复使用权限，并使操作员配置文件更加一致。 它还有助于用户档案的管理和维护。

详细了解 [运算符组](../../platform/using/access-management-groups.md).
+++

+++**选项**

选项是平台级别变量，用于定义Campaign实例的设置。 选项可以在平台级别定义时间范围（如用于数据库清理工作流）或其他全局定义。

详细了解 [选项](../../installation/using/configuring-campaign-options.md).
+++

+++**叫客互动**

*上下文：营销活动互动*

叫客互动是指从联系人列表（用于投放电子邮件、直邮等）向互动引擎发出的调用。 每个联系人都应用相同的规则和流程。 此类交互通常在批处理模式下处理。

详细了解 [叫客互动](../../interaction/using/about-outbound-channels.md).
+++

+++**包导出/导入**

资源包导出是一种操作，包括生成包含对象定义的XML文件。 包用于将功能和定义从一个实例迁移到另一个实例。 它们还用于向备份和源控制系统添加关键产品定义。

详细了解 [包导出/导入](../../platform/using/working-with-data-packages.md).
+++

+++**面板**

工作流面板会显示可添加到工作流的可用活动。 此组件以选项卡式格式显示，工作流活动按其用途进行逻辑分组。 面板上可用的活动取决于已安装到Campaign实例中的加载项以及显示工作流的上下文。

详细了解 [调色板](../../workflow/using/building-a-workflow.md#adding-and-linking-activities).
+++

+++**性能监测**

性能监控信息显示在“监控”选项卡上。 它显示基础系统的量度，如内存和CPU使用率、SMTP服务器统计信息、服务器进程和其他相关信息。

详细了解 [性能监控](../../production/using/monitoring-processes.md).
+++

+++**个性化块**

Adobe Campaign提供了可插入投放的内置个性化块。 它们是动态的、个性化的，并包含特定渲染。 例如，您可以添加徽标、问候语消息或指向镜像页面的链接。 默认情况下，可以使用多个个性化块。 您还可以定义自定义个性化块，以便优化投放个性化。 在投放的分析阶段期间，实际数据被插入到每个生成的消息中。

详细了解 [个性化块](../../delivery/using/personalization-blocks.md).
+++

+++**个性化字段**

个性化字段是在为特定收件人个性化投放时使用的单个数据字段引用。 在投放分析阶段期间插入实际数据值。

详细了解 [个性化字段](../../delivery/using/personalization-fields.md).
+++

+++**个性化变量**

个性化变量是投放中的一段代码，可根据收件人的信息向不同的收件人显示不同的文本。 这些字段可以作为个性化字段或块实施。

详细了解 [个性化变量](../../delivery/using/about-personalization.md).
+++

+++**计划**

计划是一种文件夹类型，用于按日历组织营销活动。 浏览器视图中的计划文件夹定义基于时间的单位，如年、季度或月。 可以嵌套计划文件夹，并可以包含其他计划文件夹、项目群文件夹或营销活动。

详细了解 [计划](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**预定义过滤器**

预定义过滤器是指已保存以供重复使用的查询。 使用预定义过滤器可提高工作效率（因为只创建一次），帮助构建一致性（因为所有营销人员都可以使用这些过滤器），并降低营销人员所需的技能，因为他们可以使用可能无法自行创建的代码或逻辑。

详细了解 [预定义过滤器](../../platform/using/creating-filters.md#filtering-recipients).
+++

<!--
----DEPRECATED----
+++**Predictive Engagement Scoring**

Predictive engagement scoring predicts the probability of a recipient engaging with a message and the probability of opting out (unsubscribing) within the next seven days after the next email send. The probabilities are further divided into buckets according to the specific risk of disengagement, medium, or low. The model also provides the risk percentile rank for the customers to understand where the rank of a certain customer in relation to others. 

Learn more about [Predictive Engagement Scoring](../../platform/using/creating-filters.md).
+++
-->

+++**主键**

主键是数据库表中每个记录的唯一标识符。 表必须至少具有一个键。 通常，键值会在架构的主元素和索引之后声明。 主键不能是复合键（包括多个字段）。

详细了解 [主键](../../configuration/using/schema/key.md).
+++

+++**用户档案**

用户档案是代表最终客户、潜在客户或潜在客户的信息记录。 每个用户档案都对应于nmsRecipient表中的记录或外部表，其中包含Cookie ID、客户ID、移动标识符或与特定渠道相关的其他信息。

详细了解 [用户档案](../../platform/using/about-profiles.md).
+++

+++**项目**

项目和子项目文件夹围绕业务目标组织营销活动，例如忠诚度、客户获取或交叉销售。 它们还可以表示会计期或营销策划策略，如事件或新闻稿。 每个项目都包含链接到日历的活动，日历提供了概览。

详细了解 [程序](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**公共资源**

Adobe Campaign中的“公共资源”文件夹包含由应用程序服务器托管的图像。 投放中的图像必须发布到应用程序服务器（如果已配置Campaign，则发布到图像托管服务器）才能显示在投放中，如电子邮件。

详细了解 [公共资源](../../installation/using/deploying-an-instance.md#managing-public-resources).
+++

+++**推送**

*上下文：移动设备应用程序渠道*

推送通知是移动应用程序收到的消息。 推送通知配置为通过在移动应用程序中包含Experience PlatformSDK代码来与Adobe Campaign一起使用。 对于推送，提供了两个投放渠道：iOS和Android。

详细了解 [推送](../../delivery/using/about-mobile-app-channel.md).
+++

## Q - T {#sec-5}

+++**收件人**

在Adobe Campaign中，收件人是用于发送投放内容（电子邮件、短信等）的默认用户档案 客户。 通过数据库中存储的收件人数据，您可以过滤目标并添加个性化数据。 通常，这是个人、联系人、人口统计和事务型信息，但它可以是支持营销和分析的任何类型的信息。

详细了解 [收件人](../../configuration/using/about-data-model.md).
+++

+++**呈现函数**

*上下文：营销活动互动*

渲染函数在选件空间中定义。 该选件用于根据选件中定义的属性构建其选件表示形式。 有三种不同的渲染功能模式：HTML、XML和文本。

详细了解 [呈现函数](../../interaction/using/creating-offer-spaces.md).
+++

<!--
-----DID NOT FIND IN ACC DOCS, ACS?----
+++**Retargeting campaigns**

Campaigns that re-target the recipients of a previous delivery or deliveries.
+++
-->

+++**架构**

模式是与数据库表关联的XML文档。 它定义了数据结构并描述了表的SQL定义。 操作员在Campaign中处理模式，产品将其操作转换为所需的SQL，然后针对数据库执行该SQL。

详细了解 [模式](../../configuration/using/about-schema-reference.md).
+++

+++**模式扩展**

架构扩展允许您自定义现成的架构，以最适合您的业务用例。 例如，您可以将“忠诚度”字段添加到收件人表。

详细了解 [模式扩展](../../configuration/using/extending-a-schema.md).
+++

+++**种子地址**

种子地址用于定位不符合既定目标标准的收件人。这样，超出投放范围的收件人就可以像任何其他目标收件人一样接收投放。 消息的受众中会添加这些参数，以检测收件人数据库是否用于任何欺诈行为或确保投放。

详细了解 [种子地址](../../delivery/using/about-seed-addresses.md).
+++

<!--
-------ACS?-----
+++**Send-time optimization**

To improve the open rate of your messages, you can manually define a sending time per recipient. Each profile will receive the message at the specified date and time, whenever possible. Defining a sending time can be done at the delivery level or using a workflow.

Learn more about [Send-time optimization](../../delivery/using/about-seed-addresses.md:).
+++
-->

+++**服务**

利用Adobe Campaign，可创建和管理信息服务（如新闻稿或产品更新）以及管理这些服务的订阅。 可以并行定义多个服务。

详细了解 [服务](../../delivery/using/about-services-and-subscriptions.md).
+++

+++**SFTP管理**

在控制面板中，您可以与连接到您有权访问的 Campaign 实例的所有 SFTP 服务器进行交互。利用控制面板，可对SFTP服务器执行各种操作，如监控存储容量、管理IP地址允许列表和管理公共SSH密钥。

详细了解 [SFTP管理](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/about-sftp-management.html).
+++

+++**订阅服务活动**

利用订阅服务工作流活动，可为过渡中指定的群体创建或删除信息服务订阅。

详细了解 [订阅服务活动](../../workflow/using/subscription-services.md).
+++

+++**Target批准**

*上下文：Campaign分布式营销*

目标批准是指在发送投放之前，由单独的操作员或操作员组批准投放的最终目标（在分析阶段生成目标后）的过程。

详细了解 [Target批准](../../workflow/using/local-approval.md).
+++

+++**目标数据**

目标数据是存储在工作流工作台（过渡）中的数据。 此数据可在投放内部用于个性化投放内容，或定义投放动态元素的逻辑。

详细了解 [目标数据](../../workflow/using/data-life-cycle.md#target-data).
+++

+++**目标映射**

目标映射是将投放渠道映射到特定数据类型。 目标映射定义不同投放渠道如何链接到架构的数据字段。 它使用特定字段或表达式定义Campaign如何发送到该数据类型。

详细了解 [目标映射](../../delivery/using/selecting-a-target-mapping.md).
+++

+++**定位活动**

定位活动是指特定于定位、处理群体数据和筛选活动的工作流活动。 它们允许运算符通过定义集并使用交集、并集或排除运算拆分或组合这些集来构建一个或多个目标。

详细了解 [定位活动](../../workflow/using/about-targeting-activities.md).
+++

+++**定位维度**

定向维度是查询或其他工作流活动生成（返回）的数据类型。 请注意，无论使用什么查询来获取响应数据库行，Adobe Campaign都只返回响应数据库行的主键。

详细了解 [定向维度](../../workflow/using/targeting-data.md).
+++

+++**任务活动**

*上下文：营销资源管理(MRM)*

任务工作流活动将人为操作纳入工作流的逻辑。 您可以指定两种方案：第一个是任务完成时的，第二个是任务未完成时的。 典型用例用于将离线操作合并到营销活动中，或用于自定义操作（如批准）。

详细了解 [任务活动](../../workflow/using/task.md).
+++

<!--
-----NOT USEFUL, detail-----
+++**Task**

One iteration of the defined functionality of a workflow activity. Each execution of a task has a unique task identifier.   

Learn more about [Tasks](../../workflow/using/about-workflows.md).
+++
-->

+++**模板**

模板是用于创建对象的设计元素。 它包含对象设置和对象的内容（可选）。 模板系统用于创建投放、营销策划、工作流和Adobe Campaign的许多其他元素。 可用的工厂模板由安装的包定义。 然后，可根据营销活动操作员的需要复制和自定义模板。
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

发送投放并激活跟踪后，跟踪技术工作流会检索跟踪数据。 此数据可在投放的跟踪选项卡中找到。 您可以找到电子邮件打开次数和点击次数的信息，或与收件人收到的消息进行的其他交互信息。

详细了解 [跟踪日志](../../delivery/using/accessing-the-tracking-logs.md).
+++

+++**事务性消息传递**

事务型消息传递是Campaign模块，用于管理从外部信息系统发送的事件生成的自定义触发器通知。 事务型消息是由提供商（如网站）实时发送的个人通信和唯一通信。 特别需要，因为它包含收件人要检查或确认的重要信息。

详细了解 [事务型消息传递](../../message-center/using/about-transactional-messaging.md).
+++

<!------- USEFUL HERE??----->
+++**已触发营销活动**

触发的营销活动是指在工作流中收到API请求时执行的营销活动。 工作流中的信号活动会使用API调用，该活动会启动工作流的执行。

详细了解 [触发的营销活动](../../workflow/using/external-signal.md).
+++

<!--
-----NOT USEFUL-----
+++**Triggers**

Signals that initiate execution of a workflow, delivery or other action. Typically an API call. 

Learn more about [Triggers](../../workflow/using/about-workflows.md).
+++
-->

+++**类型**

*上下文：促销活动优化*

分类是应用于投放分析阶段的分类规则组。 营销活动分类可以包含多个分类规则，但投放只能引用一个分类。

详细了解 [分类](../../campaign-opt/using/about-campaign-typologies.md#typologies).
+++

+++**类型规则**

*上下文：促销活动优化*

分类规则是作为投放分析阶段一部分实施的业务规则。 分类规则是对投放内容（控制规则）、投放目标（筛选规则）或执行业务要求的其他逻辑（压力规则）的检查。 规则是可包含在一个或多个分类中的粒度元素。

详细了解 [分类规则](../../campaign-opt/using/about-campaign-typologies.md#typology-rules).
+++

## U - Z {#sec-6}

+++**酉模式**

*上下文：促销活动互动，事务型消息传递*

在统一模式下，优惠引擎在运行时处理单个联系人。 此模式通常用于集客交互和事务型消息。

详细了解 [酉模式](../../interaction/using/about-inbound-channels.md).
+++

<!--
-----NO OCCURRENCE IN ACC, OLD v6 CONCEPT?----
+++**Universes**

Application pages hosted by the Campaign instance. Used for approval forms, landing pages, opt-out forms, preference pages or to implement other business requirements.  

Learn more about [Universes](../../workflow/using/about-workflows.md).
+++
-->

+++**Web 应用程序**

Web应用程序是由Campaign实例托管的动态交互式应用程序页面。 它们包含来自数据库的数据以及与连接用户权限相适应的内容。 例如，您可以在外联网上创建编辑表单，或在通知表单中创建包含来自数据库的数据的表、图表、输入表单等。 利用此功能，可设计和发布网页，供用户查找或输入信息。

详细了解 [Web应用程序](../../web/using/about-web-applications.md).
+++

+++**工作流**

工作流是营销活动执行流程的直观表示形式。 它允许您跨应用程序服务器的不同模块编排各种流程和任务。 您可以利用这个全面的图形环境设计各式流程，包括部分划分、活动执行、文件处理、人员参与等。工作流引擎会执行并跟踪这些流程。

详细了解 [工作流](../../workflow/using/about-workflows.md).
+++

+++**工作流日记帐**

工作流日志是工作流的分步执行日志。 它包含工作流的所有历史记录或审核跟踪。 它用于开发、疑难解答或调试目的。

详细了解 [工作流日记帐](../../workflow/using/monitoring-workflow-execution.md).
+++

+++**工作台**

工作台包含工作流转换所携带的所有信息。 每个工作流都使用多个工作表。 工作台保存其原始活动的结果，并且其内容用作工作流中下一个（已连接）活动的输入。  工作台的操作（扩展、定制）是Adobe Campaign操作员的主要技能之一。

详细了解 [工作表](../../workflow/using/about-workflows.md).
+++