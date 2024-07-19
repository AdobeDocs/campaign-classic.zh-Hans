---
product: campaign
title: Adobe Campaign Classic数据模型描述
description: 本文档介绍了Adobe Campaign数据模型
feature: Data Model
role: Data Engineer, Developer
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2399'
ht-degree: 1%

---

# Campaign数据模型说明{#data-model-description}


Adobe Campaign 提供了预定义的数据模型。本节提供了有关Adobe Campaign数据模型的内置表及其交互的一些详细信息。

要访问每个表的说明，请转到&#x200B;**[!UICONTROL Admin > Configuration > Data schemas]**，从列表中选择资源，然后单击&#x200B;**[!UICONTROL Documentation]**&#x200B;选项卡。

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>应用中所承载数据的物理和逻辑结构以 XML 格式进行描述。它遵循 Adobe Campaign 特有的语法，称为模式。有关Adobe Campaign架构的详细信息，请阅读[此部分](../../configuration/using/about-schema-reference.md)。

## 主表的说明 {#description-main-tables}

Adobe Campaign依赖于包含链接在一起的表的关系数据库。

下图显示了Adobe Campaign数据模型的主业务表与每个业务表的主字段之间的连接。

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

预定义的Adobe Campaign数据模型包括以下列出的主表。

### NmsRecipient {#NmsRecipient}

此表与&#x200B;**nms：recipient**&#x200B;架构匹配。

它是用于投放&#x200B;**的**&#x200B;收件人的默认表。 因此，它包含通过各种渠道投放所需的信息：

* sEmail：电子邮件地址。
* iEmailFormat：首选的电子邮件格式(1表示文本，2表示HTML，如果未定义，则为0)。
* 邮政地址由sAddress1、sAddress2、sAddress3、sAddress4、sZipCode和sCity生成（符合1997年5月发布的XPZ 10-011 AFNOR标准）。
* sPhone、sMobilePhone和sFax分别包含电话、手机和传真号码。
* iBlackList是用于配置文件的默认选择退出标记（1表示“已取消订阅”，0表示）。

iFolderId字段是将收件人链接到其执行文件夹的外键。 有关此内容的详细信息，请参阅[XtkFolder](#XtkFolder)。

sCountryCode字段是与收件人关联的国家/地区的3166-1Alpha2 ISO代码（2个字符）。 此字段实际上是国家/地区参考表(NmsCountry)上的外键，包含国家/地区标签和其他国家/地区代码数据。 如果未填充国家/地区，则存储“XX”值（并用它来代替零ID记录）。

有关收件人表的详细信息，请参阅[此部分](../../configuration/using/about-data-model.md#default-recipient-table)。

### NmsGroup {#NmsGroup}

此表与&#x200B;**nms：group**&#x200B;架构匹配。

它使您能够创建&#x200B;**静态收件人组**。 收件人和组之间存在多对多关系。 例如，一个收件人可以属于多个组，而一个组可以包含多个收件人。 组可以通过手动、导入或投放定位创建。 组通常用作投放目标。 字段上有一个唯一索引，表示sName组的内部名称。 该组链接到文件夹（键为iFolderId）。 有关此内容的详细信息，请参阅[XtkFolder](#XtkFolder)。

### NmsRcpGrpRel {#NmsRcpGrpRel}

NmsRcpGrpRel关系表仅包含与iRecipientId和iGroupId链接表的标识符对应的两个字段。

### NmsService {#NmsService}

此表与&#x200B;**nms：service**&#x200B;架构匹配。

在Adobe Campaign中，您可以创建和管理信息服务的订阅（主题）。 NmsService表存储您为收件人提供订阅的信息服务（主题）（例如新闻稿）的定义。

服务是类似于组（静态收件人分组）的实体，不同之处在于它们会分发更多信息并允许通过表单轻松管理订阅和退订。

字段上有一个唯一索引，表示sName服务的内部名称。 服务已链接到文件夹（键为iFolderId）。 有关此内容的详细信息，请参阅[XtkFolder](#XtkFolder)。 最后，iType字段指定此服务的投放渠道（0表示电子邮件，1表示短信，2表示电话，3表示直邮，4表示传真）。

### NmsSubscription {#NmsSubscription}

此表与&#x200B;**nms：subscription**&#x200B;架构匹配。

它使您能够管理收件人对信息服务的订阅。

### NmsSubHisto {#NmsSubHisto}

此表与&#x200B;**nms：subHisto**&#x200B;架构匹配。

如果使用Web窗体或应用程序的界面管理订阅，则所有订阅和退订都将在NmsSubHisto表中历史化。 iAction字段指定在存储在tsDate字段中的日期执行的操作（0表示退订，1表示订阅）。

### NmsDelivery {#NmsDelivery}

此表与&#x200B;**nms：delivery**&#x200B;架构匹配。

此表中的每个记录表示一个&#x200B;**投放操作**&#x200B;或一个&#x200B;**投放模板**。 它包含执行投放所需的所有参数（目标、内容等）。 投放（广播）日志(NmsBroadLog)和关联的跟踪URL (NmsTrackingUrl)在分析阶段创建（有关这两个表的更多详细信息，请参见下文）。

字段上有一个唯一索引，表示sInternalName投放或方案的内部名称。 投放链接到执行文件夹（外键为iFolderProcessId）。 有关此内容的详细信息，请参阅[XtkFolder](#XtkFolder)。

### XtkFolder {#XtkFolder}

它包含&#x200B;**在控制台的**&#x200B;导航&#x200B;**选项卡中可见的树**&#x200B;中的所有文件夹。

键入文件夹： sModel字段的值指定文件夹中可以包含的数据类型。 利用此字段，客户端控制台还可以正确显示相应表单中的数据。 此字段的可能值在navTree中定义。

该树由iParentId和iChildCount字段管理。 sFullName字段提供树中文件夹的完整路径。 最后，字段上有一个唯一索引，表示sName文件夹的内部名称。

## 投放和跟踪 {#delivery-and-tracking}

这组表链接到&#x200B;**投放**&#x200B;模块，该模块允许监视投放以及发送消息时遇到的最终问题。 有关此内容的详细信息，请参阅[监视投放](../../delivery/using/about-delivery-monitoring.md)。 有关跟踪的详细信息，请参阅[跟踪邮件](../../delivery/using/about-message-tracking.md)。

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**：此表与&#x200B;**nms：broadLogMsg**&#x200B;架构匹配。 它是投放日志表的扩展。

## 营销活动管理 {#campaign-management}

这组表链接到&#x200B;**营销活动**&#x200B;模块，该模块允许定义、优化、执行和分析通信和营销活动。 有关此内容的详细信息，请参阅[关于营销活动](../../campaign/using/designing-marketing-campaigns.md)。

![](assets/data-model_campaign.png)

* **NmsOperation**：此表与&#x200B;**nms：operation**&#x200B;架构匹配。 它包含营销活动的数据。
* **NmsDeliveryOutline**：此表与&#x200B;**nms：deliveryOutline**&#x200B;架构匹配。 它包含投放的扩展属性（投放概要）。
* **NmsDlvOutlineItem**：此表与&#x200B;**nms：dlvOutlineItem**&#x200B;架构匹配。 它包含投放概要的文章。
* **NmsDeliveryCustomization**：此表与&#x200B;**nms：deliveryCustomization**&#x200B;架构匹配。 它包含投放的个性化字段。
* **NmsBudget**：此表与&#x200B;**nms：budget**&#x200B;架构匹配。 它包含有关活动、计划、项目、任务和/或投放的预算数据。
* **NmsDocument**：此表与&#x200B;**nms：document**&#x200B;架构匹配。 它以文件（图像、Excel或Word文件等）的形式包含营销活动的营销文档
* **XtkWorkflow**：此表与&#x200B;**xtk：workflow**&#x200B;架构匹配。 它包含营销活动定位。
* **NmsTask**：此表与&#x200B;**nms：task**&#x200B;架构匹配。 它包含营销任务的定义。
* **NmsAsset**：此表与&#x200B;**nms：asset**&#x200B;架构匹配。 它包含营销资源的定义。

## 通信一致性 {#communication-consistency}

这组表链接到&#x200B;**Campaign优化**&#x200B;模块，该模块允许控制、筛选和监视投放的发送。 有关此内容的详细信息，请参阅[关于营销活动类型](../../campaign-opt/using/about-campaign-typologies.md)。

![](assets/data-model_typology.png)

* **NmsTypologyRule**：此表与&#x200B;**nms：typologyRule**&#x200B;架构匹配。 该规则包含根据类型应用于投放的规则。
* **NmsTypology**：此表与&#x200B;**nms：typology**&#x200B;架构匹配。 它包含一组应用于与类型匹配的投放的规则。
* **NmsTypologyRuleRel**：此表与&#x200B;**nms：typologyRuleRel**&#x200B;架构匹配。 它包含类型与其规则之间的关系。
* **NmsVolumeLine**：此表与&#x200B;**nms：volumeLine**&#x200B;架构匹配。 它包含容量规则的一组可用性行。
* **NmsVolumeConsumed**：此表与&#x200B;**nms：volumeConsumed**&#x200B;架构匹配。 它包含能力规则的所有消耗行。

## 响应管理 {#response-management}

这组表链接到&#x200B;**响应管理器**&#x200B;模块，该模块允许衡量营销活动的成功性和盈利能力，或为所有通信渠道提供建议。 有关此内容的详细信息，请参阅[关于响应管理器](../../response/using/about-response-manager.md)。

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

此表与&#x200B;**nms：remaSupposision**&#x200B;架构一致。 它包含测量假设的定义。

此表包含以XML存储的重要信息，包括：

**执行上下文（信息存储在XML中）**

执行上下文填充要考虑用于度量计算的表和字段，即：
* nms：remaMatchRcp反应日志存储模式。
* 事务表模式（例如，购买）。
* 查询模式，用于定义假设验证条件的起始表。
* 指向个人的链接，这使您能够基于查询模式识别个人。
* 交易记录日期。 此字段不是必填字段，但我们建议您使用它来限制计算边界。
* 事务处理金额：它是用于自动计算收入指示器的可选字段。

**假设验证周长（存储在XML中的信息）**

假设周界包括基于查询模式表的假设筛选。

**假设验证重载脚本（存储在XML中的信息）**

假设验证过载脚本是一个JavaScript代码，它允许您在执行期间过载假设验证的内容。

**度量指标**

以下指标在假设验证执行期间自动更新：

* 反应数： **iTransaction**。 反应日志表中的行数。
* 联系数： **iContactReacted**。 假设验证中不同数量的目标联系人。
* 对照组计数： **iProofReacted**。 假设验证中目标对照组联系人的不同数量。
* 联系响应率： **dContactReactedRate**。 假设验证中目标联系人的响应率。
* 控制组的响应率： **dProofReactedRate**。 假设验证对照组的响应率。
* 已联系群体的总收入：**dContactReactedTotalAmount**。 假设验证中目标联系人的总收入。
* 对照组的平均收入： **dContactReactedAvgAmount**。 假设验证中目标对照组联系人的平均收入。
* 对照组的总收入： **dProofReactedTotalAmount**。 假设验证对照组的总收入。
* 对照组的平均收入： **dProofReactedAvgAmount**。 假设验证对照组的平均收入。
* 每个联系人的总利润： **dContactReactedTotalMargin**。 假设验证中针对的每次联系的总利润。
* 每个联系人的平均利润： **dContactReactedAvgMargin**。 假设验证中针对的每次联系的平均利润。
* 控制组的总利润： **dProofReactedTotalMargin**。 假设验证中针对的对照组的总利润。
* 控制组的平均利润： **dProofReactedAvgMargin**。 假设验证中针对的对照组的平均利润。
* 其他收入： **dAdditionalAmount**。 （被联系人的平均收入 — 对照组的平均收入）*被联系的人数。
* 附加边距： **dAdditionalMargin**。 （联系的平均利润 — 对照组的平均利润）/联系的数量。
* 每次联系的平均成本（SQL表达式）。 计算的投放成本/联系次数。
* ROI（SQL表达式）。 计算的交货成本/联系的总利润。
* 有效ROI（SQL表达式）。 计算的交货成本/附加利润。
* 重要性： **iSignificativy** （SQL表达式）。 包含从0到3的值，具体取决于营销活动的重要性。

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

此表与&#x200B;**nms：remaMatchRcp**&#x200B;架构匹配。

它包含一条记录，表示个人对给定假设的反应。 这些记录是在假设验证执行期间创建的。

## 模拟和投放 {#simulation-and-delivery}

这组表链接到&#x200B;**Simulation**&#x200B;模块，该模块允许在将您的建议发送给收件人之前测试属于某个类别或环境的选件分发。 有关此内容的详细信息，请参阅[关于优惠模拟](../../interaction/using/about-offers-simulation.md)。

![](assets/data-model_simulation.png)

* **NmsSimulation**：此表与&#x200B;**nms：simulation**&#x200B;架构匹配。 它表示对给定群体中一组投放或优惠的模拟。
* **NmsDlvSimulationRel**：此表与&#x200B;**nms：dlvSimulationRel**&#x200B;架构匹配。 其中包含模拟中考虑的投放列表。 模拟的范围以XML格式存储。
* **NmsOfferSimulationRel**：此表与&#x200B;**nms：offerSimulationRel**&#x200B;架构匹配。 它可让您将模拟与选件链接到一起。

## 交互模块 {#interaction-module}

这组表链接到&#x200B;**交互**&#x200B;模块，该模块允许在与给定联系人的交互期间实时响应，方法是使其成为单个或多个自适应优惠。 有关此内容的详细信息，请参阅[交互和选件管理](../../interaction/using/interaction-and-offer-management.md)。

* **NmsOffer**：此表与&#x200B;**nms：offer**&#x200B;架构匹配。 它包含每个营销优惠的定义。
* **NmsPropositionRcp**：此表与&#x200B;**nms：propositionRcp**&#x200B;架构匹配。 它包含发送给每个人的营销建议的跨渠道日志。 记录是在准备建议或有效地向个人提出建议时创建的。
* **NmsOfferSpace**：此表与&#x200B;**nms：offerSpace**&#x200B;架构匹配。 它包含建立建议位置的定义。
* **NmsOfferContext**：此表与&#x200B;**nms：offerContext**&#x200B;架构匹配。 它包含附加的命题适用性准则以及权重计算公式的定义。
* **NmsOfferView**：此表与&#x200B;**nms：offerView**&#x200B;匹配。 它包含优惠呈现。
* **NmsOfferCategory**：此表与&#x200B;**nms：offerCategory**&#x200B;匹配。 它包含优惠类别。
* **NmsOfferEnv**：此表与&#x200B;**nms：offerEnv**&#x200B;匹配。 它包含选件环境。

## 消息中心模块 {#message-center-module}

以下一组表链接到&#x200B;**事务性消息传递** （消息中心）模块，该模块允许管理发送给用户以及从信息系统触发的事件生成的单独和唯一通信。 有关此内容的详细信息，请参阅[关于事务型消息传递](../../message-center/using/about-transactional-messaging.md)。

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

此表与&#x200B;**nms：rtEvent**&#x200B;架构匹配。 它包含实时事件的定义。

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

此表与&#x200B;**nms：batchEvent**&#x200B;架构匹配。 它包含批量事件的定义。

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## NMAC模块 {#nmac-module}

这组表链接到&#x200B;**移动设备应用程序渠道**，该渠道允许通过应用程序向iOS和Android终端发送个性化通知。 有关此内容的详细信息，请参阅[关于移动应用频道](../../delivery/using/about-mobile-app-channel.md)。

* **NmsMobileApp**：此表与&#x200B;**nms：mobileApp**&#x200B;架构匹配。 它包含Adobe Campaign中定义的移动设备应用程序。
* **NmsAppSubscription**：此表与&#x200B;**nms：appSubscription**&#x200B;架构匹配。 它包含有关一个或多个应用程序的订阅者信息。
* **NmsAppSubscriptionRcp**：此表与&#x200B;**nms：appSubscriptionRcp**&#x200B;架构匹配。 它使您能够将订阅应用程序的访客与收件人表关联起来。
* **NmsExcludeLogAppSubRcp**：此表与&#x200B;**nms：excludeLogAppSubRcp**&#x200B;架构匹配。
* **NmsTrackingLogAppSubRcp**：此表与&#x200B;**nms：trackingLogAppSubRcp**&#x200B;架构匹配。
* **NmsBroadLogAppSubRcp**：此表与&#x200B;**nms：broadLogAppSubRcp**&#x200B;架构匹配。

## 社交营销模块 {#social-marketing-module}

这组表链接到&#x200B;**管理社交网络**&#x200B;模块，该模块允许通过Facebook和X(以前称为Twitter)与客户和潜在客户进行交互。 有关此内容的详细信息，请参阅[关于社交营销](../../social/using/about-social-marketing.md)。

![](assets/data-model_social.png)

* **NmsVisitor**：此表与&#x200B;**nms：visitor**&#x200B;架构匹配。 它包含有关访客的信息。
* **NmsVisitorSub**：此表与&#x200B;**nms：visitorSub**&#x200B;架构匹配。 它允许您将访客关联到他们订阅的服务(X或Facebook)。
* **NmsFriendShipRel**：此表与&#x200B;**nms：friendshipRel**&#x200B;架构匹配。 它使您能够在Facebook服务的上下文中将访客与其朋友链接到一起。
* **NmsVisitorInterestRel**：此表与&#x200B;**nms：visitorInterestRel**&#x200B;架构匹配。 它使您能够链接访客及其兴趣。
* **NmsInterest**：此表与&#x200B;**nms：interest**&#x200B;架构匹配。 它包含每个访客的兴趣列表。
