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


# 可交付性关键点{#deliverability-key-points}

为优化Adobe Campaign电子邮件的发送能力，我们建议使用下面列出的最佳实践。 传送能力问题通常与互联网服务提供商和邮件服务器管理员实施的防垃圾邮件措施有关。

**电子** 邮件传送能力是指一系列特征，这些特征决定了邮件在短时间内通过个人电子邮件地址到达其目的地的能力，并在内容和格式方面达到了预期的质量。

这些特征分为四个主要类别:
* 数据质量
* 消息和内容
* 发送基础结构
* 声誉

它们共同构成了成功的电子邮件交付项目的基础。

**可传送性率**&#x200B;是已成功传送至其收件人的已发送电子邮件数。

交付率取决于诸多因素，特别是：
* 实例的正确配置
* 您的IP地址信誉
* 目标地址的质量
* 低投诉和高反弹率
* 您的消息内容
* 邮件身份验证(SPF、DKIM、DMARC)
* 发件人声誉

以下是要检查的要点列表，以确保良好的交付能力。

## 检查网络配置{#network-configuration}

垃圾邮件发送者试图隐藏他们的真实身份，结果导致他们的服务器难以识别。 不尝试隐藏服务器标识的合法网络配置对于以大容量发送电子邮件至关重要。

## 发送到有效地址{#valid-addresses}

垃圾邮件发送者经常使用基于频繁姓名和名字列表的地址生成器；此外，他们很少处理邮件服务器发送的技术通知。 无效地址的高率通常被解释为垃圾邮件的标志。 多次选择加入机制和对技术弹回消息的有效处理使避免这种情况成为可能。

## 减少投诉和跳出率{#reduce-complaint-rates}

ISP通常将收到的消息报告为垃圾邮件。 这使得能够识别不可靠的来源。 通过快速满足选择退出请求、定期使用给定列表、通过多次选择加入系统验证同意并实施反馈循环，您可以降低投诉率。

## 发送到蜜罐地址{#honeypot-addresses}

ISP和其他组织（请参阅[Project Honey Pot](https://www.projecthoneypot.org/)网站）使用的邮箱与物理人员不对应，而是仅仅为了欺骗垃圾邮件发送者而创建的。 这些所谓的“蜜罐”地址发布在Web上，以便由垃圾邮件程序收集，从而捕获非法发送者。 使用多次选择加入机制可阻止此类地址添加到列表。 使用第三方列表时，必须确定其维护器使用的方法。

## 调整消息内容{#message-content}

某些邮件的内容会导致某些过滤器将其检测为垃圾邮件。 使用某些单词，在主题行和邮件中使用感叹号被解读为垃圾邮件的告诉信号。 众所周知，垃圾邮件发送者会用图像替换文本，以阻止防垃圾邮件过滤器自动分析违规文本。 为此，具有高比例图像或图像作为附件的消息（HTML格式）最终可能被阻止。

## 处理您的声誉{#reputation}

垃圾邮件发送者会通过编程投放来保持自己的声誉。 他们有时需要调整营销计划以符合ISP强加的最佳实践，因此，在声誉达到高峰（加速）后，他们会配置常规投放。

## 最佳做法 {#best-practices}

了解与通过Adobe Campaign交付相关的最佳实践。 使用以下链接浏览主题并查找指导。

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
