---
product: campaign
title: Adobe Campaign术语表
description: Adobe Campaign术语表
role: User, Data Architect
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: 5e4866281fa661de6ebd344fe68d4f23ae8e876c
workflow-type: tm+mt
source-wordcount: '4246'
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

详细了解 [活动用户档案](about-profiles.md#active-profiles).
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

+++**自动化促销活动**

按计划运行的营销活动，例如定向生日或周年纪念的收件人。 还可用于执行前瞻和回顾逻辑，例如，谁在昨天购买了产品或谁在明天有付款。

详细了解 [促销活动](../../campaign/using/designing-marketing-campaigns.md).
+++

+++**批处理模式**

*上下文：营销活动互动*

在促销活动交互的上下文中，批量模式允许选件引擎为一组联系人选择最佳选件（或选件）。 资格/优先级规则将应用于集合的所有联系人。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**营销活动**

营销活动是协调、定义和执行营销活动的界面。 营销活动可以将一个或多个工作流、投放、文档和其他相关数据点包含到一个易于使用的界面中。

详细了解 [促销活动](../../campaign/using/designing-marketing-campaigns.md).
+++

+++**转换过程**

*上下文：营销活动互动*

在营销活动互动的背景下，转换过程是已识别环境中的激活过程，负责在联系人未被明确和/或隐式识别时将呼叫定向到匿名环境。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

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

详细了解 [内容批准](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).
+++

+++**控制面板**

该控制面板允许您管理每个实例的设置并跟踪其使用情况，从而帮助您作为Adobe Campaign的产品管理员提高工作效率。 其直观的界面可让您轻松监控关键资产的使用情况，并执行管理任务，如将 IP 地址添加到允许列表、SFTP 存储监控、密钥管理等。

详细了解 [内容批准](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hans).
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

详细了解 [自定义资源](../../configuration/using/about-data-model.md).
+++

+++**数据库清理工作流**

数据库清理工作流会删除过时的数据，以避免数据库呈指数级增长。 工作流会自动触发，无需用户干预。

详细了解 [数据库清理工作流](../../production/using/database-cleanup-workflow.md).
+++

+++**专用服务器**

*上下文：事务型消息传递*

专用执行服务器来利用事务型消息传递。 服务器通常每小时最多可处理50,000个引擎调用。 “每专用服务器”指标不一定与物理服务器有1:1的关联，因为Adobe可能利用虚拟化技术来达到同等效果。

详细了解 [事务型消息传递](../../message-center/using/about-transactional-messaging.md).
+++

+++**可投放性**

*上下文：电子邮件投放能力*

一种量度，可让操作员测量营销活动在到达收件人收件箱时是否成功，而不会跳出或标记为垃圾邮件。

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

+++**交付基础知识**

*上下文：电子邮件投放能力*

Adobe Campaign可投放性基础咨询服务提供电子邮件可投放性咨询和声誉管理，以支持使用Adobe Campaign投放的客户。

详细了解 [投放能力](../../delivery/using/about-deliverability.md).
+++

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

向Campaign运营商提供的分布式营销附加组件提供了一个协作工作区，用于在中心实体（总部、营销部门等）之间实施营销活动 实施协作营销活动。此合作基于称为 **Campaign包列表**，其中向本地实体提供了集中创建的营销活动模板和实例。

详细了解 [分布式营销](../../distributed/using/about-distributed-marketing.md)
+++

+++**值分布**

值分布是一个工具，用于显示当前存在于数据库中的架构属性的值分布。 这有助于您确定哪些值可用、其计数和百分比，并避免在创建查询或表达式时出现值大小写和拼写问题。

详细了解 [分布式营销](../../platform/using/defining-filter-conditions.md#selecting-data-to-extract)
+++

+++**域委派**

子域配置允许您配置域的子区域（技术上称为“DNS区域”）以与Adobe Campaign一起使用。
通过域委派，Adobe可以控制并维护发送、渲染和跟踪电子邮件促销活动所需的DNS的所有方面。

详细了解 [域委派](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=zh-Hans)
+++

## E - H {#sec-2}

<!--
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

+++**电子邮件卷承诺**

销售订单中规定的每年发送的预期电子邮件。 这是年度电子邮件总量承诺，包括由于发送错误而发送但未发送的电子邮件，例如：未投放邮件，包括但不限于电子邮件地址错误、硬退回、软退回、邮件客户端的电子邮件过滤器和电子邮件黑名单。
+++

+++**引擎调用**

引擎调用是在服务器端启动实时处理以提取数据的服务器调用，例如与调查、WebApps、JSSP、API、移动设备应用程序注册等相关的数据。 引擎调用必须在每天5,000个引擎调用的包中获得许可。
+++

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

+++**正在过滤维度**

筛选维度是一种架构，其中包含查询用于筛选所需行的数据或属性。 筛选维度架构必须直接链接到定义的定向维度，以便Adobe Campaign能够跨数据库连接并返回响应行。

详细了解 [筛选维度](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).
+++

+++**文件夹**

文件夹是一个Explorer视图项，它保存特定数据类型的数据库记录。 “通用”文件夹类型是例外，该文件夹类型用作组织元素，并且本身不包含任何数据，仅包含其他文件夹。

详细了解 [文件夹](../../platform/using/adobe-campaign-explorer.md).
+++

+++**文件夹视图**

“文件夹视图”是一种特殊的“资源管理器”文件夹类型，用于显示选定数据类型的所有记录，无论它属于哪个文件夹。 文件夹视图用作管理多个文件夹之间分发的分区数据或数据的管理工具。

详细了解 [文件夹视图](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Forms**

Forms定义特定架构类型的界面表示形式。 Forms是轻松创建和编辑产品中数据元素（如“收件人”、“投放”和“营销活动”）的方法。 Adobe Campaign中的所有界面元素均使用Forms在产品本身中创建。 请注意，表单是可选的，并非所有架构都具有表单。

详细了解 [Forms](../../configuration/using/identifying-a-form.md).
+++

+++**生成的SQL查询**

当运算符操作模式时为基础数据库生成的SQL代码。 架构定义随后使用数据库表和列实施的数据类型。 为架构操作（例如在查询中）生成的SQL基于已安装的数据库类型。 因此，可以将数据库交换为其他类型，并且Campaign中的查询保持不变。 Adobe将此功能称为与数据库无关的功能。

详细了解 [生成的SQL查询](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++

+++**热图**

Campaign热图是一个显示24小时工作流执行信息的表。 它按小时和5分钟间隔显示整个时段的工作流分布。 热图用于评估服务器负载并确定消耗最多资源的工作流活动。

详细了解 [热图](../../workflow/using/heatmap.md).
+++

+++**混合部署**

混合部署是按需服务与部署在一起运行的内部部署软件的组合。

详细了解 [混合部署](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

+++**识别模式**

*上下文：营销活动互动*

指联系人的状态。 它可以是显式的、隐式的或匿名的。

* **显式**:联系人在登录渠道界面后即被识别。
* **隐式**:联系人已通过cookie（永久或会话）进行识别。 它可以作为匿名或已识别的联系人进行处理。
* **匿名**:无法识别联系人。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**图像服务**

向投放的收件人提供电子邮件中嵌入的图像的功能。 基于电子邮件系统的“下载图像”功能插入图像，是指在Campaign的跟踪日志中生成“打开”条目的原因。

详细了解 [图像服务](../../delivery/using/defining-the-email-content.md#adding-images).
+++

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

在操作员计算机上本地存储的信息。 控制台会使用缓存信息来减少服务器所需的流量并提高性能。 定期清除本地缓存（在“文件”菜单上）会更新存储的信息，并提高性能和稳定性。

详细了解 [本地缓存](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**营销资源管理(MRM)**

*上下文：营销资源管理(MRM)*

的 **营销资源管理(MRM)** Adobe Campaign中的模块通过提供所涉任务、预算和营销资源的完整管理和实时跟踪，使您能够以协作模式控制营销操作。 Adobe Campaign操作员可以通过完整的验证流程和适当的跟踪工具来协调其操作并批准其在所有阶段的进度：报告、审批跟踪、通知、论坛等。

详细了解 [MRM](../../mrm/using/about-marketing-resource-management.md).
+++

<!--
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**已命名权限**

用于定义操作员组访问权限和权限（角色）的粒度数据库访问权限。 在产品安装期间，通过导入定义工具特定功能的各种包来填充命名权限。 可以创建自定义命名权限以支持客户端业务要求。

详细了解 [已命名权限](../../platform/using/access-management-named-rights.md).
+++

+++**命名空间**

分区，用于将客户数据类型与数据模型中Adobe Campaign的本机数据类型分隔开。 还用于促进定义从一个实例迁移到另一个实例，例如将架构或模板从开发实例移动到生产实例。

详细了解 [命名空间](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

+++**导航栏**

在界面顶部运行的导航元素。 导航栏可重组平台的各种核心功能。 单击导航栏链接以显示与此功能相关的功能集。 可以访问的核心功能列表将取决于您所安装的软件包和附加组件以及访问权。导航栏的用途是简化屏幕管理并提高工作效率。

详细了解 [导航栏](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++

+++**导航树**

Adobe Campaign的Explorer视图中的主导航。 导航树的工作方式类似于文件浏览器（例如Windows资源管理器）。 文件夹可能包含子文件夹。 选择节点后，将显示与该节点对应的视图。 显示的视图是与架构关联的列表以及用于编辑所选行的输入表单。 您可以自定义导航树并设置文件夹的权限。

详细了解 [导航树](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarch).
+++

+++**目标**

*上下文：营销资源管理(MRM)*

在营销策划、项目策划或计划中，操作员可以声明目标列表。 这些是要达到的量化值。 在营销活动、项目或计划结束时，MRM模块允许操作员在专用报告中比较目标和结果。

详细了解 [目标](../../mrm/using/creating-and-managing-tasks.md#expenses-and-revenues).
+++

+++**优惠目录**

*上下文：营销活动互动*

在Adobe Campaign中定义的一组选件，可在交互过程中进行选择。 该目录以对应于一类别的每个节点来分层组织。

详细了解 [优惠目录](../../interaction/using/offer-catalog-overview.md).
+++

+++**选件联系人**

*上下文：营销活动互动*

集客互动的联系人。 在引擎调用处理期间，联系人与定向维度关联。 未识别的匿名联系人将归属于访客定位维度。 有两种类型的联系人：已识别和匿名：

* **已识别的联系人**:已在频道上自愿识别的联系人。 在叫客交互中，联系人会被自动识别。
* **匿名联系人**:未通过渠道自愿订阅，但可通过Cookie隐式识别的联系人。 此术语仅用于传入交互。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**选件设计环境**

*上下文：营销活动互动*

选件 **设计环境** 是运算符在其中创建选件、定义分类规则以及选择选件所定向的架构的环境。 用于存储所生成的优惠建议的表也由环境定义。 默认情况下， Interaction附加组件附带 **设计** 环境和 **实时** 链接到该环境。 这两个环境都已预配置为定向内置的收件人表。

详细了解 [设计环境](../../interaction/using/fundamental-principles.md).
+++

+++**优惠引擎套利**

*上下文：营销活动互动*

选择将在环境中显示的选件（符合条件的选件）。 套利原则根据类别和报价中定义的标准，按优先级对报价进行排序。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**优惠引擎修剪**

*上下文：营销活动互动*

删除不符合选择条件的选件的过程。 在优惠引擎套利步骤之前执行。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**选件环境**

*上下文：营销活动互动*

根文件夹，用于定义选件目录、其可用空格和环境的预定义过滤器。 操作员需要为每个定向维度创建一个环境。 选件环境有两种类型：设计和实时。

详细了解 [环境](../../interaction/using/fundamental-principles.md).
+++

+++**选件实时环境**

*上下文：营销活动互动*

链接到营销活动的环境 **设计环境**. 它包含已通过 **设计环境**. 可以选择在网站上演示或插入到出站消息中。

详细了解 [实时环境](../../interaction/using/fundamental-principles.md).
+++

+++**优惠预览**

*上下文：营销活动互动*

预览选件在其文件夹中显示时的显示效果。 可从选件预览选项卡或联系人资料访问选件。

详细了解 [选件预览](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**选件演示规则**

*上下文：营销活动互动*

选件环境中引用的分类规则，允许运算符通过考虑收件人的建议历史记录来排除特定选件。

详细了解 [选件演示规则](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**优惠建议**

*上下文：营销活动互动*

选件建议是该操作的结果，该操作包括在给定选件空间中向联系人展示选件，例如网站上的横幅、电子邮件或短信内容。 此结果存储在选件建议表中，该表定义了选件、收件人和时间戳，提供了收件人收到的所有选件的记录。

详细了解 [提供建议](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**选件演示**

*上下文：营销活动互动*

选件建议是该操作的结果，该操作包括在给定选件空间中向联系人展示选件，例如网站上的横幅、电子邮件或短信内容。 此结果存储在选件建议表中，该表定义了选件、收件人和时间戳，提供了收件人收到的所有选件的记录。

详细了解 [互动](../../interaction/using/interaction-and-offer-management.md).
+++

+++**优惠模拟**

*上下文：营销活动互动*

通过选件模拟，操作员可以测试在定义范围（投放日期、目标区段、选件数量、主题等）中的选件分发 发送选件之前。 它可用于调整选件优先级和资格规则，以最大限度地提高选件的有效性。

详细了解 [优惠模拟](../../interaction/using/about-offers-simulation.md).
+++

+++**选件空间**

*上下文：营销活动互动*

选件空间是一个文件夹，用于定义选件的显示位置。 通过定义空格，您可以指定使用的渠道、构建选件的内容，以及指定显示的选件。 选件空间是渠道与选件引擎之间的接口。

详细了解 [优惠模拟](../../interaction/using/creating-offer-spaces.md).
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

## Q - T {#sec-5}

## U - Z {#sec-6}
