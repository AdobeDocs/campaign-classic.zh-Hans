---
product: campaign
title: 了解投放失败
description: 了解如何了解投放失败
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 2%

---

# 了解投放失败{#understanding-delivery-failures}

>[!NOTE]
>
>有关了解投放失败的全面指南记录在[Campaign v8了解投放失败](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures)页面中。 此内容适用于Campaign Classic v7和Campaign v8用户，内容包括：
>
>* 投放失败类型和原因（硬、软、已忽略）
>* 同步和异步错误
>* 退回邮件鉴别
>* 电子邮件、推送通知和短信错误类型
>* 重试管理和有效期
>* 常见投放失败疑难解答
>
>此页面记录了在混合部署和内部部署中用于退回邮件管理的&#x200B;**Campaign Classic v7特定配置**。

有关常见的投放失败概念、错误类型和疑难解答指南，请参阅[Campaign v8了解投放失败文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}。

## 退回邮件配置 {#v7-bounce-mail-config}

以下配置选项可用于&#x200B;**Campaign Classic v7混合/内部部署**&#x200B;以管理退回邮件处理。

### 退回邮箱配置 {#bounce-mailbox-configuration}

对于内部部署安装，退回邮箱的配置在[此部分](../../installation/using/deploying-an-instance.md#managing-bounced-emails)中有详细说明。

异步错误消息由Adobe Campaign平台通过退回邮箱收集，并由inMail流程进行鉴别，以扩充电子邮件管理规则的列表。

>[!NOTE]
>
>对于Campaign v8托管云服务用户，退回邮箱配置由Adobe执行和管理。 无需配置。

### 退回邮件鉴别管理 {#bounce-mail-qualification-management}

对于使用旧版Campaign MTA的内部部署和托管/混合安装，当电子邮件投放失败时，Adobe Campaign投放服务器会收到来自消息传送服务器或远程DNS服务器的错误消息。 错误列表由远程服务器返回的消息中包含的字符串组成。 为每个错误消息指定失败类型和原因。

此列表可通过&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;节点使用。 它包含Adobe Campaign用于限定投放失败的所有规则。 此文档并非详尽无遗，由Adobe Campaign定期更新，用户也可以对其进行管理。

![](assets/tech_quarant_rules_qualif.png)

远程服务器第一次出现此错误类型时返回的消息显示在&#x200B;**[!UICONTROL First text]**&#x200B;表的&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;列中。 如果未显示此列，请单击列表右下方的&#x200B;**[!UICONTROL Configure list]**&#x200B;按钮将其选定。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign过滤此消息以删除变量内容（如ID、日期、电子邮件地址、电话号码等），并在&#x200B;**[!UICONTROL Text]**&#x200B;列中显示过滤的结果。 变量已替换为&#x200B;**`#xxx#`**，但地址已替换为&#x200B;**`*`**。

此流程允许汇总相同类型的所有故障，并避免投放日志鉴别表中出现多个类似错误条目。

>[!NOTE]
>
>**[!UICONTROL Number of occurrences]**&#x200B;字段显示消息在列表中的出现次数。 限制为100 000次。 例如，如果您希望重置该字段，则可以对其进行编辑。

退回邮件可以具有以下资格状态：

* **[!UICONTROL To qualify]**：无法限定退回邮件。 必须向可交付性团队分配资格以确保高效的平台可交付性。 只要不满足条件，就不会使用退回邮件来丰富电子邮件管理规则的列表。
* **[!UICONTROL Keep]**：退回邮件已限定，将由&#x200B;**刷新以进行可投放性**&#x200B;工作流使用，以与现有电子邮件管理规则进行比较并扩充列表。
* **[!UICONTROL Ignore]**：退回邮件被Campaign MTA忽略，这意味着此退回不会导致隔离收件人的地址。 **刷新可投放性**&#x200B;工作流不会使用此项，并且不会将其发送到客户端实例。

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>如果ISP发生中断，通过Campaign发送的电子邮件将被错误地标记为退回。 要更正此问题，您需要更新退回鉴别。 有关更多信息，请参阅[此页面](update-bounce-qualification.md)。

### 电子邮件管理规则配置 {#email-management-rules}

通过&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;节点访问邮件规则。 电子邮件管理规则显示在窗口的下部。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的默认参数是在部署向导中配置的。 有关详细信息，请参阅[此部分](../../installation/using/deploying-an-instance.md)。

默认规则如下：

>[!IMPORTANT]
>
>* 如果更改了参数，则必须重新启动投放服务器(MTA)。
>* 管理规则的修改或创建仅供专家用户使用。

#### 入站电子邮件 {#inbound-email}

这些规则包含可由远程服务器返回的字符串，并可让您限定错误（**Hard**、**Soft**&#x200B;或&#x200B;**Ignored**）。

当电子邮件失败时，远程服务器会向平台参数中指定的地址返回退回消息。 Adobe Campaign会将每个退回消息的内容与规则列表中的字符串进行比较，然后为其分配三种错误类型之一。

>[!NOTE]
>
>用户可以创建自己的规则。 在导入包和通过&#x200B;**刷新可投放性**&#x200B;工作流更新数据时，用户创建的规则将被覆盖。

有关退回邮件鉴别的更多信息，请参阅[此章节](#bounce-mail-qualification-management)。

#### 域管理 {#domain-management}

对于内部部署，MTA将单个&#x200B;**域管理**&#x200B;规则应用于所有域。

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* 您可以选择是否激活某些标识标准和加密密钥以检查域名，如&#x200B;**发件人ID**、**DomainKeys**、**DKIM**&#x200B;和&#x200B;**S/MIME**。
* **SMTP中继**&#x200B;参数允许您为特定域配置中继服务器的IP地址和端口。 如需详细信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#smtp-relay)。

如果您的邮件在发件人地址中显示&#x200B;**[!UICONTROL on behalf of]**，请确保不要使用&#x200B;**发件人ID**&#x200B;签署电子邮件，这是Microsoft中过时的专有电子邮件身份验证标准。 如果已启用&#x200B;**[!UICONTROL Sender ID]**&#x200B;选项，请取消选中相应的框并联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 您的可投放性不会受到影响。

#### MX 管理 {#mx-management}

对于内部部署，使用MX管理规则来规范特定域的传出电子邮件流程。

<!--![](assets/tech_quarant_domain_rules_01.png)-->

这些规则在部署向导中可用，并且可以自定义：

* **[!UICONTROL MX Management]**：此规则用于控制域的传出电子邮件流量。 它会在适当的时候对退回消息和发送块进行采样。

* **[!UICONTROL Period]**：调整或阻止消息的时间范围。

* **[!UICONTROL Limit]**：每个时段允许的最大消息数。

* **[!UICONTROL Type]**：用于确定发送行为的错误类型（hard、soft或ignored）。 有关错误类型定义，请参阅[Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}。

有关MX管理的详细信息，请参阅[此部分](../../installation/using/email-deliverability.md#about-mx-rules)。

>[!NOTE]
>
>对于Campaign v8托管云服务用户，MX规则和电子邮件流管理作为托管基础架构的一部分由Adobe管理。 如果您需要针对特定用例调整MX设置，请联系Adobe客户关怀。

## 相关主题

* [了解投放失败](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}（Campaign v8文档）
* [投放状态](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"}（Campaign v8文档）
* [隔离管理](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}（Campaign v8文档）
* [隔离配置](understanding-quarantine-management.md)（v7混合/内部部署）
* [更新退回资格](update-bounce-qualification.md)（v7混合/内部部署）
* [电子邮件可投放性配置](../../installation/using/email-deliverability.md)（v7混合/内部部署）
* [正在部署实例](../../installation/using/deploying-an-instance.md#managing-bounced-emails)（v7混合/内部部署）
