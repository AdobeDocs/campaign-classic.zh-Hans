---
solution: Campaign Classic
product: campaign
title: 可交付性要点
description: 改进交付能力的要点
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 2%

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

垃圾邮件发送者通常使用基于列表频繁姓名和名字的地址生成器；此外，他们很少处理邮件服务器发送的技术通知。 无效地址的高率通常被解释为垃圾邮件的标志。 多次选择加入机制和对技术弹回消息的有效处理使避免这种情况成为可能。

## 减少投诉和弹出率 {#reduce-complaint-rates}

ISP通常将收到的邮件报告为垃圾邮件。 这使得识别不可靠来源成为可能。 通过快速执行退出请求、定期使用特定列表、通过多次选择加入系统验证同意并实施反馈循环，您可以降低投诉率。

## 发送到蜜罐地址 {#honeypot-addresses}

ISP和其他组织(请参 [阅Project Honey Pot](https://www.projecthoneypot.org/) web站点)利用的邮箱与实际人群不对应，而是仅仅用于欺骗垃圾邮件发送者。 这些所谓的“蜜罐”地址发布在Web上，以便由垃圾邮件程序收集，从而捕获非法发送者。 使用多次加入机制，将这种地址添加到列表。 使用第三方列表时，您必须确定其维护器所使用的方法。

## 调整消息内容 {#message-content}

某些邮件的内容会导致某些过滤器将其检测为垃圾邮件。 使用某些单词、在主题行和邮件中使用感叹号会被视为垃圾邮件的告示符。 垃圾邮件发送者还知道用图像替换文本，以防止防垃圾邮件过滤器自动分析违规文本。 为此，图像比例较高或图像作为附件的邮件（HTML格式）可能最终被阻止。

## 善用声誉 {#reputation}

垃圾邮件发送者使程序化投放能够随着时间的流逝保持其声誉。 他们有时需要调整营销计划，以符合ISP实施的最佳实践，因此，在声誉达到高峰（加速）后，他们会配置常规投放。

## 最佳做法 {#best-practices}

了解与Adobe Campaign交付性相关的最佳实践。 使用以下链接浏览主题并查找指南。

<table>
<tr>
  <td>
    <a href="starting-new-platform.md">
      <img alt="开始" src="assets/do-not-localize/start.svg" width="60px"/>
    </a>
    <div>
      <a href="starting-new-platform.md">
    <strong>开始</strong>
    </a>
    </div>
    <p>
    <em>启动新平台</em>
    <p>
  </td>
   <td>
    <a href="control-message-content.md">
      <img alt="设计" src="assets/do-not-localize/design.svg" width="60px"/>
    </a>
    <div>
      <a href="control-message-content.md">
    <strong>设计</strong>
    </a>
    </div>
    <p>
    <em>控制消息内容</em>
    <p>
  </td>
  <td>
    <a href="improve-reputation.md">
      <img alt="设计" src="assets/do-not-localize/check.svg" width="60px"/>
    </a>
    <div>
      <a href="improve-reputation.md">
    <strong>发送</strong>
    </a>
    </div>
    <p>
    <em>提高声誉</em>
    <p>
  </td>
</tr>
<tr>
  <td>
    <a href="technical-recommendations.md">
      <img alt="优化" src="assets/do-not-localize/optimize.svg" width="60px"/>
    </a>
    <div>
      <a href="technical-recommendations.md">
    <strong>优化</strong>
    </a>
    </div>
    <p>
    <em>技术建议</em>
    <p>
  </td>
   <td>
    <a href="monitoring-deliverability.md">
      <img alt="检查" src="assets/do-not-localize/monitor.svg" width="60px"/>
    </a>
    <div>
      <a href="monitoring-deliverability.md">
    <strong>监视器</strong>
    </a>
    </div>
    <p>
    <em>监视工具</em>
    <p>
  </td>
  <td>
    <a href="deliverability-faq.md">
      <img alt="优化" src="assets/do-not-localize/troubleshoot.svg" width="60px"/>
    </a>
    <div>
      <a href="deliverability-faq.md">
    <strong>疑难解答</strong>
    </a>
    </div>
    <p>
    <em>解决问题</em>
    <p>
  </td>
</tr>
</table>
