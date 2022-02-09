---
product: campaign
title: 发送前检查
description: 消息准备就绪后，在发送之前执行所有检查
feature: Deliverability
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: 808f459a0b77b1787fc017c031247ab268b5aafa
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 4%

---

# 发送前执行所有检查 {#perform-all-checks}

![](../../assets/common.svg)

消息准备就绪后，请确保其内容在所有设备上均正确显示，并且不包含任何错误，如错误的个性化或链接损坏。

在发送消息之前，还应确保参数和配置与投放一致。

## 验证为何是关键 {#validation-is-key}

在发送投放之前，您需要确保收件人将收到您确实希望发送的消息。 为此，您需要验证消息内容和投放参数。

通过此步骤，您可以在将错误传送到主目标之前，检测并修复可能的错误。

将介绍验证投放的步骤 [在此部分中](steps-validating-the-delivery.md).

## 收件箱呈现 {#inbox-and-email-rendering}

收件箱呈现功能允许您在主要电子邮件客户端上预览邮件，扫描内容和声誉，了解收件人阅读邮件的方式。

**提示**:

* 您可以在收到消息的不同上下文中查看已发送的消息：Web邮件、消息服务、移动设备等。

* 收件箱呈现功能对于确定您的电子邮件促销活动是否成功超过主要ISP（互联网服务提供商）和Web邮件服务的过滤器至关重要。 此类工具会向测试收件箱网络发送电子邮件的预检副本，以便您能够查看这些服务中消息的显示或呈现方式。 它们还可能包括报表和代码更正选项，可帮助您快速识别并进行可改进投放能力的修复。

了解更多 [在此部分中](inbox-rendering.md).

## 校样消息 {#proof-messages}

通过发送校样，您可以检查选择退订链接、镜像页面和任何其他链接、验证消息、验证图像是否显示、检测可能的错误等。 您可能还希望检查在不同设备上的设计和渲染。

了解更多 [在此部分中](steps-validating-the-delivery.md#sending-a-proof).

## 设置A/B测试投放 {#a-b-testing-deliveries}

如果您有多个用于电子邮件投放的内容，则可以使用A/B测试来确定哪个版本对目标群体的影响最大。

**提示**:

* 将不同版本发送给您的部分收件人

* 选择成功率最高的，并将其发送到目标的其余部分

了解更多 [在此部分中](get-started-a-b-testing.md).

## 确保消息已送达 {#make-sure-your-message-is-delivered}

最后一步是，最大可能地利用Adobe Campaign Classic的力量，确保您的信息确实会传递给相关收件人。

### 完成验证过程

您可以定义包含Adobe Campaign运算符和组的完整验证流程，以验证目标和消息内容。 这将确保对营销活动的各种过程进行全面监控和控制：定位、内容、预算、提取和发送校样。 根据用户的权限，系统会通知用户并接收校样，并能够验证或拒绝消息。 了解更多 [在此部分中](../../campaign/using/marketing-campaign-approval.md).

### 使用批次

您可以使用批次逐步增加发送的音量。 这样可避免将消息标记为垃圾邮件，或者希望限制每天的消息数。 使用批次，您可以将投放分为多个批次，而不是同时发送大量消息。 了解更多 [在此部分中](steps-sending-the-delivery.md#sending-using-multiple-waves).

### 优先处理消息

您可以通过声明优先级来设置投放的发送顺序。 为实现此操作，请执行以下步骤：

1. 编辑投放属性，然后选择 **[!UICONTROL Delivery]** 选项卡。

1. 从 **[!UICONTROL Very low]** to **[!UICONTROL Very high]**.

>[!NOTE]
>
>无法定义从投放内发送消息的顺序。

### 设置IP相关性

为更好地控制出站SMTP流量，您可以通过定义可用于每个关联的特定IP地址来管理关联。 这样，您就可以将特定投放的电子邮件数量限制到计算机或输出地址。 例如，您可以为每个国家/地区或子域使用一个亲和度。 然后，您可以为每个国家/地区创建一个分类，并将每个亲和度关联到相应的分类。

您可以：

* 在serverConf.xml配置文件中定义IP相关性。 [了解详情](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 对于每个IPAfinity元素，声明可使用的IP地址。 [了解详情](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在 [类型](../../campaign-opt/using/about-campaign-typologies.md) 使用 **[!UICONTROL Managing affinities with IP addresses]** 用于将投放链接到管理所述亲和度的投放服务器(MTA)的字段。 [了解详情](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic)。

* 发送电子邮件后，检查标题以验证发送投放的IP地址。 电子邮件管理员应帮助您获取标题信息。

* 对于短信投放，请确保短信渠道具有专用亲和度，该亲和度限于 **one** 应用程序服务器容器。 [了解详情](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>大多数这些步骤只能由专家用户执行。

### 使用分类

您可以使用分类规则根据特定条件排除部分目标。 这可确保在遵守公司通信政策的同时，发送最符合客户需求及期望的邮件。例如，您可以过滤未达到新闻稿目标的收件人。 了解更多 [在本例中](../../campaign-opt/using/filtering-rules.md).

### 避免附件

附件仍然是导致恶意软件激增的最常见媒介之一，尤其是在批量发送时。 包括指向文档的安全链接，而不是附加文档。 这可确保额外的安全层以防止意外的重新分发，并且会因消息大小或安全原因而大大降低在入站电子邮件网关拒绝消息的可能性。
