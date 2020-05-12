---
title: 在Adobe Campaign经典中管理交付性时的要点
description: 在Adobe Campaign经典中管理交付性时，需要检查哪些要点？
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4582ea496fff35c5b586049b8daa379464bd78fc
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---


# 可交付性要点{#deliverability-key-points}

为了优化Adobe Campaign电子邮件的可投递性，我们建议使用下面列出的最佳实践。 传送能力问题通常与互联网服务提供商和邮件服务器管理员实施的防垃圾邮件措施有关。

**电子邮件发送** ，是指一系列特征，这些特征决定了邮件在短时间内通过个人电子邮件地址到达其目的地的能力，并且在内容和格式方面具有预期的质量。

这些特征分为四个主要类别:
* 数据质量
* 消息和内容
* 发送基础结构
* 声誉

它们共同构成了成功电子邮件交付项目的基础。

交 **付率是** 已发送电子邮件的数量，已成功交付给收件人。

交付率取决于诸多因素，特别是：
* 正确配置实例
* 您的IP地址信誉
* 目标地址的质量
* 低投诉和高反弹率
* 您的消息内容
* 邮件身份验证(SPF、DKIM、DMARC)
* 发件人声誉

以下是要检查的关键点的列表，以确保良好的交付能力。

## 检查网络配置 {#network-configuration}

垃圾邮件发送者试图隐藏其真实身份，结果导致其服务器难以识别。 不试图隐藏服务器标识的合法网络配置对于以大量方式发送电子邮件至关重要。

## 发送到有效地址 {#valid-addresses}

垃圾邮件发送者通常使用基于列表频繁姓名和名字的地址生成器； 此外，他们很少处理邮件服务器发送的技术通知。 无效地址的高率通常被解释为垃圾邮件的标志。 多次选择加入机制和对技术弹回消息的有效处理使避免这种情况成为可能。

## 减少投诉和弹出率 {#reduce-complaint-rates}

ISP通常将收到的邮件报告为垃圾邮件。 这使得识别不可靠来源成为可能。 通过快速执行退出请求、定期使用特定列表、通过多次选择加入系统验证同意并实施反馈循环，您可以降低投诉率。

## 发送到蜜罐地址 {#honeypot-addresses}

ISP和其他组织(请参 [阅Project Honey Pot](https://www.projecthoneypot.org/) web站点)利用的邮箱与实际人群不对应，而是仅仅用于欺骗垃圾邮件发送者。 这些所谓的“蜜罐”地址发布在Web上，以便由垃圾邮件程序收集，从而捕获非法发送者。 使用多次加入机制，将这种地址添加到列表。 使用第三方列表时，您必须确定其维护器所使用的方法。

## 调整消息内容 {#message-content}

某些邮件的内容会导致某些过滤器将其检测为垃圾邮件。 使用某些单词、在主题行和邮件中使用感叹号会被视为垃圾邮件的告示符。 垃圾邮件发送者还知道用图像替换文本，以防止防垃圾邮件过滤器自动分析违规文本。 为此，图像比例较高或图像作为附件的邮件（HTML格式）可能最终被阻止。

## 善用声誉 {#reputation}

垃圾邮件发送者使程序化投放能够随着时间的流逝保持其声誉。 他们有时需要调整营销计划，以符合ISP实施的最佳实践，因此，在声誉达到高峰（加速）后，他们会配置常规投放。