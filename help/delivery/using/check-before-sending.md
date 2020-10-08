---
title: 发送前检查
seo-title: 发送前检查
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 3%

---


# 发送前执行所有检查 {#perform-all-checks}

消息准备就绪后，请确保其内容在所有设备上均正确显示，且不包含任何错误，如错误的个性化或中断的链接。

在发送消息之前，还应确保参数和配置与投放一致。

## 验证为何重要 {#validation-is-key}

在发送投放之前，您需要确保收件人将收到您真正希望发送的消息。 为此，您需要验证消息内容和投放参数。

通过此步骤，您可以检测可能的错误并修复它们，然后再将其传送到主目标。

本节介绍验证投放 [的步骤](../../delivery/using/steps-validating-the-delivery.md)。

## 收件箱呈现 {#inbox-and-email-rendering}

收件箱呈现使您能够在主要电子邮件客户端预览邮件、扫描内容和声誉、发现收件人阅读邮件的方式。

**提示**:

* 您可以在收到邮件的不同视图中上下文发送的邮件：Web邮件、邮件服务、移动等。

* 收件箱呈现功能对于确定您的电子邮件活动是否成功地使其超过主要ISP(Internet服务提供商)和Web邮件服务的过滤器至关重要。 此类工具会将电子邮件的预检副本发送到测试收件箱网络，以便您能够查看消息在这些服务中的显示或呈现方式。 它们还可能包括报告和代码更正选项，可帮助您快速识别并进行可改进交付性的修复。

在本节 [中了解更多](../../delivery/using/inbox-rendering.md)。

## 验证消息 {#proof-messages}

发送验证使您能够检查退出链接、镜像页面和任何其他链接、验证消息、验证图像是否显示、检测可能的错误等。 您可能还希望检查在不同设备上的设计和渲染。

在本节 [中了解更多](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

## 设置A/B测试投放 {#a-b-testing-deliveries}

如果电子邮件投放有多个内容，则可以使用A/B测试找出哪个版本对目标人群的影响最大。

**提示**:

* 将不同版本发送给您的某些收件人

* 选择成功率最高的目标，并将其发送至其他

在本节 [中了解更多](../../workflow/using/a-b-testing.md)。

## 确保您的消息已送达 {#make-sure-your-message-is-delivered}

最后一步，充分利用你的机会，利用Adobe Campaign Classic的力量，确保你的信息真正传递给相关收件人。

### 完成验证过程

您可以定义一个包含Adobe Campaign运算符和组的完整验证流程，以验证目标和消息内容。 这将确保全面监测和控制该活动的各种进程：定位、内容、预算、提取和发送验证。 根据用户的权限，用户将收到通知、接收验证并能够验证或拒绝消息。 在本节 [中了解更多](../../campaign/using/marketing-campaign-approval.md#approval-process)。

### 使用批次

您可以使用批次逐步增加发送的音量。 这将避免您的邮件被标记为垃圾邮件，或者您希望限制每天的邮件数。 使用批次，您可以将投放分为几批，而不是同时发送大量消息。 在本节 [中了解更多](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。

### 确定消息的优先级

您可以通过声明优先级来设置投放的发送顺序。 为实现此操作，请执行以下步骤：

1. 编辑投放属性，然后选择选 **[!UICONTROL Delivery]** 项卡。

1. 定义投放从到的比例的优先级 **[!UICONTROL Very low]** 别 **[!UICONTROL Very high]**。

>[!NOTE]
>
>无法从投放中定义发送消息的顺序。

### 设置IP关联

为了更好地控制出站SMTP通信，您可以通过定义每个关联可以使用哪些特定IP地址来管理关联。 这样，您就可以将特定投放的电子邮件数量限制到计算机或输出地址。 例如，您可以在每个国家／地区或子域使用一个关联。 然后，您可以为每个国家／地区创建一种类型学，并将每种关联关联到相应的类型学。

您可以：

* 在serverConf.xml配置文件中定义IP关联。 [了解详情](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 对于每个IPAfinity元素，声明可使用的IP地址。 [了解详情](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在您 [选择](../../campaign/using/about-campaign-typologies.md) 的排版中，使用 **[!UICONTROL Managing affinities with IP addresses]** 该字段将投放链接到投放服务器(MTA)，该服务器管理所述关联。 [了解详情](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic)。

* 发送电子邮件后，检查标题以验证投放从哪个IP地址发送。 电子邮件管理员应帮助您获取标题信息。

>[!NOTE]
>
>这些步骤大多只能由专家用户执行。

### 使用类型

您可以使用类型规则根据特定条件排除部分目标。 这可确保在遵守公司通信政策的同时，发送最符合客户需求及期望的邮件。例如，您可以从新闻稿的目标中过滤未达到规定的收件人。 通过此示 [例了解更多信息](../../campaign/using/filtering-rules.md)。

### 避免附件

附件仍然是防止恶意软件激增的最常见的矢量之一，尤其是当它们被批量发送时。 包括指向文档的安全链接，而不是附加它。 这确保了额外的安全层以防止意外的重新分发，并且极大地降低了由于邮件大小或安全原因在入站电子邮件网关处拒绝邮件的可能性。
