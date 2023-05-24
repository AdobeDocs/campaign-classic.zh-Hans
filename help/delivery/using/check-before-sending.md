---
product: campaign
title: 发送前检查
description: 消息就绪后，在发送之前执行所有检查
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 4%

---

# 发送前执行所有检查 {#perform-all-checks}



消息就绪后，请确保其内容在所有设备上均正确显示，并且不包含任何错误，例如错误的个性化或损坏的链接。

在发送消息之前，还要确保参数和配置与投放一致。

## 验证为何重要 {#validation-is-key}

在发送投放之前，您需要确保收件人将收到您确实希望他们发送的消息。 要实现此目的，您需要验证消息内容和投放参数。

通过此步骤，您可以检测可能的错误，并在将其交付到主目标之前修复它们。

介绍了验证投放的步骤 [在此部分中](steps-validating-the-delivery.md).

## 收件箱呈现 {#inbox-and-email-rendering}

通过收件箱呈现，您可以预览主要电子邮件客户端上的邮件、扫描内容和信誉、了解收件人的邮件阅读方式。

**提示**：

* 您可以在接收消息的不同上下文中查看已发送的消息：Web邮件、消息服务、移动设备等。

* 收件箱呈现功能对于确定电子邮件营销活动是否成功超越主要ISP（Internet服务提供商）和Web邮件服务的过滤器至关重要。 此类工具会将电子邮件的预检副本发送到测试收件箱网络，以便您了解消息在这些服务中的显示或呈现方式。 它们还可以包括报告和代码更正选项，帮助您快速识别并进行修复以改善可投放性。

了解详情 [在此部分中](inbox-rendering.md).

## 校对消息 {#proof-messages}

发送校样使您能够检查选择退出链接、镜像页面和任何其他链接、验证消息、验证是否显示图像、检测可能存在的错误等。 您可能还希望检查您的设计和在不同设备上的渲染。

了解详情 [在此部分中](steps-validating-the-delivery.md#sending-a-proof).

## 设置A/B测试投放 {#a-b-testing-deliveries}

如果您的电子邮件投放包含多个内容，则可以使用A/B测试找出哪个版本对目标群体影响最大。

**提示**：

* 将不同版本发送给某些收件人

* 选择成功率最高的目标并将其发送到目标的其余部分

了解详情 [在此部分中](get-started-a-b-testing.md).

## 确保您的消息已投放 {#make-sure-your-message-is-delivered}

最后，最大限度地提高您的机会，并利用Adobe Campaign Classic的强大功能确保您的消息确实会被传递到相关收件人。

### 进行验证过程

您可以定义涉及Adobe Campaign操作员和组的完整验证流程，以验证目标和消息内容。 这将确保完全监控并控制营销活动的各个流程：定位、内容、预算、提取和发送证明。 根据用户的权限，用户将收到通知、接收校样并能够验证或拒绝消息。 了解详情 [在此部分中](../../campaign/using/marketing-campaign-approval.md).

### 使用批次

您可以逐步增加使用批次发送的数量。 这样可避免您的邮件被标记为垃圾邮件，或者当您想要限制每天的邮件数时。 使用批次，您可以将投放划分为多个批次，而不是同时发送大量消息。 了解详情 [在此部分中](steps-sending-the-delivery.md#sending-using-multiple-waves).

### 排定消息优先级

您可以通过指明优先级来设置投放的发送顺序。 为实现此操作，请执行以下步骤：

1. 编辑投放属性，然后选择 **[!UICONTROL Delivery]** 选项卡。

1. 根据以下标准定义投放的优先级： **[!UICONTROL Very low]** 到 **[!UICONTROL Very high]**.

>[!NOTE]
>
>无法定义从投放中发送消息的顺序。

### 设置IP相关性

为了更好地控制出站SMTP流量，您可以通过定义每个关联可以使用的特定IP地址来管理关联。 这样，您就可以限制向计算机或输出地址进行特定投放的电子邮件数量。 例如，您可以为每个国家/地区或子域使用一个关联。 然后，您可以为每个国家/地区创建一个分类，并将每个关联链接到相应的分类。

您可以：

* 在serverConf.xml配置文件中定义IP相关性。 [了解详情](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 对于每个IPAffinity元素，声明可以使用的IP地址。 [了解详情](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在 [类型](../../campaign-opt/using/about-campaign-typologies.md) 选择时，使用 **[!UICONTROL Managing affinities with IP addresses]** 用于将投放链接到管理所述关联的投放服务器(MTA)的字段。 [了解详情](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic)。

* 发送电子邮件后，检查标头以验证发送投放的IP地址。 您的电子邮件管理员应帮助您获取标头信息。

* 对于短信投放，请确保短信渠道的专用亲和度限制为 **一** 应用程序服务器容器。 [了解详情](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>这些步骤中的大多数只能由专家用户执行。

### 使用分类

您可以使用分类规则根据特定条件排除部分目标。 这可确保在遵守公司通信政策的同时，发送最符合客户需求及期望的邮件。例如，您可以从新闻稿的目标中筛选未满年龄的收件人。 了解详情 [在此示例中](../../campaign-opt/using/filtering-rules.md).

### 避免使用附件

附件仍然是恶意软件泛滥的最常见媒介之一，尤其是大量发送附件时。 包括一个指向文档的安全链接，而不是附加文档。 这确保了额外的安全层，以防止意外的重新分发，并大大减少了因消息大小或安全原因在入站电子邮件网关上被拒绝的可能性。
