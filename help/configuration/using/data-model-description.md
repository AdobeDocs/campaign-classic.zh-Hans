---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic数据模型描述
description: 本文档描述了Adobe Campaign数据模型。
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '2374'
ht-degree: 1%

---


# 活动数据模型描述{#data-model-description}

Adobe Campaign 提供了预定义的数据模型。本节提供一些关于Adobe Campaign数据模型的内置表及其交互的详细信息。

要访问每个表的说明，请转到&#x200B;**[!UICONTROL Admin > Configuration > Data schemas]**，从列表中选择一个资源并单击&#x200B;**[!UICONTROL Documentation]**&#x200B;选项卡。

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>应用中所承载数据的物理和逻辑结构以 XML 格式进行描述。它遵循 Adobe Campaign 特有的语法，称为模式。有关Adobe Campaign模式的详细信息，请阅读[本节](../../configuration/using/about-schema-reference.md)。

## 主表{#description-main-tables}的说明

Adobe Campaign依赖于包含链接在一起的表的关系数据库。

下图显示了Adobe Campaign数据模型的主要业务表与每个主字段之间的联接。

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

预定义的Adobe Campaign数据模型包括下面列出的主表。

### NmsRecipient {#NmsRecipient}

此表与&#x200B;**nms:收件人**&#x200B;模式匹配。

它是用于&#x200B;**收件人投放**&#x200B;的默认表。 因此，它包含通过各种渠道进行投放所需的信息：

* 电子邮件：电子邮件地址。
* iEmailFormat:首选电子邮件格式(1表示文本，2表示HTML，0（如果未定义）。
* sAddress1、sAddress2、sAddress3、sAddress4、sZipCode、sCity用于构建邮政地址（与1997年5月起的XPZ 10-011 AFNOR标准一致）。
* sPhone、sMobilePhone、sFax分别包含电话、移动电话和传真号码。
* iBlackList是用于用户档案的默认退出标志（1表示“未订阅”，0表示其他情况）。

iFolderId字段是将收件人链接到其执行文件夹的外键。 有关此的详细信息，请参阅[XtkFolder](#XtkFolder)。

sCountryCode字段是与该收件人关联的国家/地区的3166-1 Alpha 2 ISO代码（2个字符）。 此字段实际上是国家/地区参考表(NmsCountry)上的外键，它包含国家/地区标签和其他国家/地区代码数据。 如果未填充国家/地区，则存储值“XX”（并用于代替零ID记录）。

有关收件人表的详细信息，请参阅[此部分](../../configuration/using/about-data-model.md#default-recipient-table)。

### NmsGroup {#NmsGroup}

此表与&#x200B;**nms:group**&#x200B;模式匹配。

它允许您创建&#x200B;**收件人**&#x200B;的静态组。 收件人和群之间有多对多的关系。 例如，一个收件人可以属于多个组，而一个组可以包含多个收件人。 可通过导入或投放定位手动创建组。 组通常用作投放目标。 字段上有一个唯一索引，它表示sName组的内部名称。 该组链接到一个文件夹(键为iFolderId。 有关详细信息，请参阅[XtkFolder](#XtkFolder))。

### NmsRcpGrpRel {#NmsRcpGrpRel}

NmsRcpGrpRel关系表只包含与iRecipientId和iGroupId链接表的标识符对应的两个字段。

### NmsService {#NmsService}

此表与&#x200B;**nms:service**&#x200B;模式匹配。

在Adobe Campaign中，您可以创建和管理信息服务（主题）的订阅。 NmsService表存储您优惠收件人订阅的信息服务（主题）的定义（例如新闻稿）。

服务是与组(静态收件人组)类似的实体，只是它们传递更多信息并通过表单轻松管理订阅和退订。

字段上有一个唯一索引，它表示sName服务的内部名称。 该服务链接到一个文件夹(键为iFolderId。 有关详细信息，请参阅[XtkFolder](#XtkFolder))。 最后，iType字段指定此服务的投放渠道（0表示电子邮件，1表示SMS，2表示电话，3表示直邮，4表示传真）。

### NmsSubscription {#NmsSubscription}

此表与&#x200B;**nms:订阅**&#x200B;模式匹配。

它使您能够管理收件人订阅到信息服务。

### NmsSubHisto {#NmsSubHisto}

此表与&#x200B;**nms:subHisto**&#x200B;模式匹配。

如果订阅是使用Web表单或应用程序的接口进行管理，则所有订阅和退订都会在NmsSubHisto表中历史记录。 iAction字段指定在tsDate字段中存储的日期执行的操作(0表示退订,1表示订阅)。

### NmsDelivery {#NmsDelivery}

此表与&#x200B;**nms:投放**&#x200B;模式匹配。

此表中的每条记录表示&#x200B;**投放操作**&#x200B;或&#x200B;**投放模板**。 它包含执行投放(目标、内容等)所需的所有参数。 投放（广播）日志(NmsBroadLog)和关联的跟踪URL(NmsTrackingUrl)是在分析阶段创建的（有关这两个表的更多详细信息，请参见下文）。

字段上有一个唯一索引，它表示sInternalName投放或方案的内部名称。 该投放链接到一个执行文件夹(外键是iFolderProcessId。 有关详细信息，请参阅[XtkFolder](#XtkFolder))。

### XtkFolder {#XtkFolder}

它包含&#x200B;**控制台的**&#x200B;导航&#x200B;**选项卡中可见的树**&#x200B;中的所有文件夹。

键入文件夹：sModel字段的值指定可包含在文件夹中的数据类型。 此字段还使客户端控制台能够使用相应的表单正确显示数据。 此字段的可能值在navTree中定义。

树由iParentId和iChildCount字段管理。 sFullName字段提供树中文件夹的完整路径。 最后，在表示sName文件夹内部名称的字段上有一个唯一的索引。

## 投放和跟踪{#delivery-and-tracking}

这组表链接到&#x200B;**投放**&#x200B;模块，该模块允许监视发送消息时遇到的投放和最终问题。 有关详细信息，请参阅[监视投放](../../delivery/using/about-delivery-monitoring.md)。 有关跟踪的详细信息，请参阅[跟踪消息](../../delivery/using/about-message-tracking.md)。

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**:此表与nms: **broadLogMsgschema** 匹配。它是投放日志表的扩展。

## 活动管理{#campaign-management}

这组表链接到&#x200B;**营销活动**&#x200B;模块，该模块允许定义、优化、执行和分析通信和营销活动。 有关详细信息，请参阅[关于营销活动](../../campaign/using/designing-marketing-campaigns.md)。

![](assets/data-model_campaign.png)

* **NmsOperation**:此表与nms: **operationschema** 匹配。它包含营销活动数据。
* **NmsDeliveryOutline**:此表与nms: **deliveryOutlineschema** 匹配。它包含投放(投放概要)的扩展属性。
* **NmsDlvOutlineItem**:此表与nms: **dlvOutlineItemschema** 匹配。它包含投放概要的文章。
* **NmsDeliveryCustomization**:此表与nms: **deliveryCustomization** 架构匹配。它包含个性化字段的投放。
* **NmsBudget**:此表与nms: **budgetschema** 匹配。它包含活动、计划、项目、任务和/或投放的预算数据。
* **NmsDocument**:此表与nms: **documentschema** 匹配。它包含以文件（图像、excel或word文件等）形式的活动营销文档
* **XtkWorkflow**:此表与xtk: **workflowschema** 匹配。它包含活动定位。
* **NmsTask**:此表与nms: **taskschema** 匹配。它包含营销任务的定义。
* **NmsAsset**:此表与nms: **assetschema** 匹配。它包含营销资源的定义。

## 通信一致性{#communication-consistency}

这组表链接到&#x200B;**活动优化**&#x200B;模块，该模块允许控制、过滤和监视投放的发送。 有关此的详细信息，请参阅[关于活动类型](../../campaign/using/about-campaign-typologies.md)。

![](assets/data-model_typology.png)

* **NmsTypology规则**:此表与nms: **typologyRuleschema** 匹配。它包含根据类型应用于投放的规则。
* **NmsTypology**:此表与nms: **typologyschema** 匹配。它包含要应用于与类型学匹配的投放的规则集。
* **NmsTypologyRuleRel**:此表与nms: **typologyRuleRelschema** 匹配。它包含字体与规则之间的关系。
* **NmsVolumeLine**:此表与nms: **volumeLineschema** 匹配。它包含容量规则的可用行集。
* **NmsVolumeUsceved**:此表与nms: **volumeConsumedschema** 匹配。它包含能力规则的所有消耗行。

## 响应管理{#response-management}

这组表链接到&#x200B;**响应管理器**&#x200B;模块，该模块允许衡量所有通信渠道的营销活动或优惠建议的成功和盈利能力。 有关此的详细信息，请参阅[关于响应管理器](../../campaign/using/about-response-manager.md)。

![](assets/data-model_response.png)

### NmsRemaHexposition {#NmsRemaHypothesis}

此表与&#x200B;**nms:remaHexposition**&#x200B;模式一致。 它包含测量假设验证的定义。

此表包含存储在XML中的重要信息，包括：

**执行上下文（存储在XML中的信息）**

执行上下文填充了要考虑到度量计算的表和字段，即：
* nms:remaMatchRcp反应日志存储模式。
* 事务处理表模式（例如购买）。
* 查询模式，用于定义假设验证条件的开始表。
* 指向个人的链接，使您能够根据查询模式识别个人。
* 交易日期。 此字段不是必填字段，但建议您使用它来限制计算周长。
* 事务处理金额：它是用于自动计算收入指标的可选字段。

**假设验证周长（XML中存储的信息）**

假设验证周界包括基于查询模式表的假设验证过滤。

**假设验证过载脚本（存储在XML中的信息）**

假设验证过载脚本是一个JavaScript代码，它使您能够在执行过程中使假设验证的内容过载。

**测量指标**

以下指示器在执行假设验证时自动更新：

* 反应数：**iTransaction**。 反应日志表中的行数。
* 联系人数：**iContactRenacted**。 假设验证中目标联系人的不同数量。
* 对照组计数：**iProofRenated**。 假设验证中目标对照组联系人的不同数量。
* 联系的响应率：**dContactRenatedRate**。 假设验证中目标联系人的响应率。
* 对照组的响应率：**dProofRenatedRate**。 假设验证对照组的响应率。
* 联系人口总收入：**dContactRenatedTotalAmount**。 假设验证中目标联系人的总收入。
* 平均对照组收入：**dContactRenatedAvgAmount**。 假设验证中目标对照组联系人的平均收入。
* 对照组总收入：**dProofRenatedTotalAmount**。 假设验证对照组的总收入。
* 平均对照组收入：**dProofRenatedAvgAmount**。 假设验证对照组的平均收入。
* 每个联系人的总利润：**dContactRenatedTotalMargin**。 假设验证中目标的每个联系人的总毛利。
* 每个联系人的平均边距：**dContactRenatedAvgMargin**。 假设验证中目标的每个联系人的平均边距。
* 对照组总利润：**dProofRenatedTotalMargin**。 目标对照组在假设验证中的总边距。
* 平均对照组率：**dProofRenatedAvgMargin**。 目标对照组在假设验证中的平均边距。
* 额外收入：**dAdditionalAmount**。 (联系的平均收入 — 对照组的平均收入)*联系的人数。
* 附加利润：**dAdditionalMargin**。 (平均联系边距 — 平均对照组边距)/联系人数。
* 每个联系人的平均成本(SQL表达式)。 计算的投放成本/联系人数。
* ROI(SQL表达式)。 计算的投放成本/联系的总利润。
* 有效ROI(SQL表达式)。 计算投放成本/附加利润。
* 重要性：**iAvility**(SQL表达式)。 包含0到3之间的值，具体取决于活动的重要性。

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

此表与&#x200B;**nms:remaMatchRcp**&#x200B;模式匹配。

它包含表示个人对给定假设验证的反应的记录。 这些记录是在执行假设验证时创建的。

## 模拟和投放{#simulation-and-delivery}

这组表链接到&#x200B;**模拟**&#x200B;模块，该模块允许在将您的主张发送到收件人之前，测试属于类别或环境的优惠的分布。 有关详细信息，请参阅[关于优惠模拟](../../interaction/using/about-offers-simulation.md)。

![](assets/data-model_simulation.png)

* **NmsSimulation**:此表与nms: **simulationschema** 匹配。它表示对给定人口的一组投放或优惠的模拟。
* **NmsDlvSimulationRel**:此表与nms: **dlvSimulationRelschema** 匹配。它包含列表模拟中考虑的投放。 模拟的范围以XML存储。
* **NmsOfferSimulationRel**:此表与nms: **offerSimulationRelschema** 匹配。它允许您将模拟与优惠关联。

## 交互模块{#interaction-module}

这组表链接到&#x200B;**Interaction**&#x200B;模块，该模块允许通过使它们成为单个或多个适应的优惠，在与给定联系人的交互期间实时响应。 有关此的详细信息，请参阅[交互和优惠管理](../../interaction/using/interaction-and-offer-management.md)。

* **NmsOffer**:此表与nms: **offerschema** 匹配。它包含每个营销优惠的定义。
* **NmsCompationRcp**:此表与nms: **compationRcpschema** 匹配。它包含发送给每位客户的跨渠道营销建议日志。 记录是在准备或有效地向个人提出建议时创建的。
* **NmsOfferSpace**:此表与nms: **offerSpaceschema** 匹配。它包含提出建议的位置的定义。
* **NmsOfferContext**:此表与nms: **offerContextschema** 匹配。它包含关于该命题适用性的附加标准以及权重计算公式的定义。
* **NmsOfferView**:此表与nms: **offerView匹配**。它包含优惠呈现。
* **NmsOfferCategory**:此表与nms: **offerCategory匹配**。它包含优惠类别。
* **NmsOfferEnv**:此表与nms: **offerEnv匹配**。它包含优惠环境。

## 消息中心模块{#message-center-module}

以下一组表链接到&#x200B;**事务消息**（消息中心）模块，该模块允许管理发送给用户并从信息系统触发的事件生成的个别和唯一通信。 有关此的详细信息，请参阅[关于事务消息](../../message-center/using/about-transactional-messaging.md)。

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

此表与&#x200B;**nms:rtEvent**&#x200B;模式匹配。 它包含实时事件的定义。

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

此表与&#x200B;**nms:batchEvent**&#x200B;模式匹配。 它包含按批量定义的事件。

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## NMAC模块{#nmac-module}

这组表链接到&#x200B;**移动应用渠道**，该应用程序允许通过应用程序向iOS和Android终端发送个性化通知。 有关详细信息，请参阅[关于移动应用渠道](../../delivery/using/about-mobile-app-channel.md)。

* **NmsMobileApp**:此表与nms: **mobileAppschema** 匹配。它包含Adobe Campaign中定义的移动应用程序。
* **NmsAppSubscription**:此表与nms:appSubscription **架构** 匹配。它包含关于一个或多个应用程序的用户信息。
* **NmsAppSubscriptionRcp**:此表与nms: **appSubscriptionRcpschema** 匹配。它使您能够将订阅应用程序的访客与收件人表链接起来。
* **NmsExcludeLogAppSubRcp**:此表与nms: **excludeLogAppSubRcpschema** 匹配。
* **NmsTrackingLogAppSubRcp**:此表与nms: **trackingLogAppSubRcpschema** 匹配。
* **NmsBroadLogAppSubRcp**:此表与nms: **broadLogAppSubRcpschema** 匹配。

## 社交营销模块{#social-marketing-module}

这组表链接到&#x200B;**管理社交网络**&#x200B;模块，该模块允许通过Facebook和Twitter与客户和潜在客户进行交互。 有关此的详细信息，请参阅[关于社交营销](../../social/using/about-social-marketing.md)。

![](assets/data-model_social.png)

* **NmsVisitor**:此表与nms: **visitorschema** 匹配。它包含有关访客的信息。
* **NmsVisitorSub**:此表与nms: **visitorSubschema** 匹配。它允许您将访客链接到他们订阅的服务（Twitter或Facebook）。
* **NmsFriendShipRel**:此表与nms: **friendshipRelschema** 匹配。它使您能够在Facebook服务的上下文中将访客与其朋友关联。
* **NmsVisitorInterestRel**:此表与nms: **visitorInterestRelschema** 匹配。它使您能够将访客及其兴趣关联起来。
* **NmsInterest**:此表与nms: **interest** 架构匹配。它包含每个访客的兴趣列表。