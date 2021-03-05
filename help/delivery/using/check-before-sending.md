---
solution: Campaign Classic
product: campaign
title: 发送前检查
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 4%

---


# 在发送{#perform-all-checks}之前执行所有检查

在您的消息准备就绪后，请确保其内容在所有设备上正确显示，并且不包含任何错误，如错误的个性化或中断的链接。

在发送消息之前，还要确保参数和配置与投放一致。

## 为什么验证是键{#validation-is-key}

在发送投放之前，您需要确保收件人将收到您真正希望发送的消息。 为此，您需要验证消息内容和投放参数。

通过此步骤，您可以检测可能的错误并修复它们，然后再将其提交到主目标。

本节](../../delivery/using/steps-validating-the-delivery.md)介绍了验证投放的步骤[。

## 收件箱呈现 {#inbox-and-email-rendering}

收件箱渲染使您能够在主要电子邮件客户端上预览您的邮件，扫描内容和声誉，发现收件人阅读邮件的方式。

**提示**:

* 您可以在收到邮件的不同上下文视图已发送的邮件：Web邮件、消息服务、移动等。

* 收件箱渲染功能对于确定您的电子邮件活动是否成功使其超过主要ISP(Internet服务提供商)和Web邮件服务的过滤器至关重要。 此类工具会向测试收件箱网络发送电子邮件的预检副本，以便您能够查看邮件在这些服务中的显示或呈现方式。 它们还可能包括报告和代码更正选项，可帮助您快速识别和进行可改进交付性的修复。

请阅读本节](../../delivery/using/inbox-rendering.md)了解更多信息。[

## 验证消息{#proof-messages}

发送验证使您能够检查退出链接、镜像页面和任何其他链接、验证消息、验证图像是否显示、检测可能的错误等。 您可能还希望在不同设备上检查您的设计和渲染。

请阅读本节](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)了解更多信息。[

## 设置A/B测试投放{#a-b-testing-deliveries}

如果您对电子邮件投放有多个内容，则可以使用A/B测试来确定哪个版本对目标人群的影响最大。

**提示**:

* 将不同版本发送到您的某些收件人

* 选择成功率最高的，并将其发送给您的其他目标

请阅读本节](../../delivery/using/get-started-a-b-testing.md)了解更多信息。[

## 确保已传递{#make-sure-your-message-is-delivered}

最后一步，最大化您的机会并利用Adobe Campaign Classic的力量，确保您的信息将真正传递给相关收件人。

### 执行验证过程

您可以定义一个包含Adobe Campaign运算符和组的完整验证过程，以验证目标和消息内容。 这将确保全面监测和控制该活动的各种进程：定位、内容、预算、提取和发送验证。 根据用户的权限，用户将收到通知、接收验证并能够验证或拒绝消息。 请阅读本节](../../campaign/using/marketing-campaign-approval.md)了解更多信息。[

### 使用批次

您可以逐步增加使用批次发送的音量。 这将避免您的邮件被标记为垃圾邮件或您希望限制每天的邮件数。 使用批次，您可以将投放分为几批，而不是同时发送大量消息。 请阅读本节](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)了解更多信息。[

### 确定消息优先级

您可以通过声明优先级来设置投放的发送顺序。 为实现此操作，请执行以下步骤：

1. 编辑投放属性，然后选择&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡。

1. 定义从&#x200B;**[!UICONTROL Very low]**&#x200B;到&#x200B;**[!UICONTROL Very high]**&#x200B;的投放的优先级。

>[!NOTE]
>
>无法定义从投放中发送消息的顺序。

### 设置IP关联

为了更好地控制出站SMTP通信，您可以通过定义每个关联可以使用哪些特定IP地址来管理关联。 这样，您就可以将特定投放的电子邮件数量限制到计算机或输出地址。 例如，您可以在每个国家/地区或子域使用一个关联。 然后，您可以为每个国家/地区创建一种类型学，并将每种关联与相应的类型学关联起来。

您可以：

* 在serverConf.xml配置文件中定义IP关联。 [了解详情](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 对于每个IPAfinity元素，声明可使用的IP地址。 [了解详情](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在您选择的[类型](../../campaign/using/about-campaign-typologies.md)中，使用&#x200B;**[!UICONTROL Managing affinities with IP addresses]**&#x200B;字段将投放链接到管理所述关联的投放服务器(MTA)。 [了解详情](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic)。

* 发送电子邮件后，检查标题以验证投放从哪个IP地址发送。 电子邮件管理员应帮助您获取标题信息。

>[!NOTE]
>
>大多数这些步骤只能由专家用户执行。

### 使用类型

您可以使用类型规则根据特定条件排除部分目标。 这可确保在遵守公司通信政策的同时，发送最符合客户需求及期望的邮件。例如，您可以从新闻稿的目标中筛选未达到规定的收件人。 请阅读本示例](../../campaign/using/filtering-rules.md)了解更多信息。[

### 避免附件

附件仍然是导致恶意软件激增的最常见矢量之一，尤其是当它们批量发送时。 包括指向文档的安全链接，而不是附加它。 这确保了额外的安全层以防止意外的重新分发，并极大地降低了由于消息大小或安全原因而在入站电子邮件网关处拒绝消息的可能性。
