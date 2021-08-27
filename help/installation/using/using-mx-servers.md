---
product: campaign
title: 在 Campaign 中使用 MX 服务器
description: 了解MX服务器如何与Adobe Campaign Classic配合使用。
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 1%

---

# 在 Campaign 中使用 MX 服务器 {#using-mx-servers}

![](../../assets/v7-only.svg)

了解MX服务器如何与Adobe Campaign Classic配合使用。

## MX服务器 {#mx-servers}

### 什么是MX服务器？

邮件交换器记录（MX记录）是域名系统(DNS)中的一种资源记录类型，它指定负责代表域接受电子邮件的邮件服务器。

### MX服务器的工作原理是什么？

当您发送电子邮件时，软件服务器将与收件人域服务器建立连接。 两台服务器之间的通信使用SMTP语言，并且域可以有多台MX服务器。 与此域的连接将从最高优先级（最小数字）开始，而其他服务器则称为“备份”服务器。 必须遵守连接协议。

### MX服务器如何与Adobe Campaign一起使用？

在连接协议中，必须遵守规则，以防止垃圾邮件和垄断服务器。 最重要的是：

* **允许的最大连接数**:遵守此数字后，IP不在阻止列表中，电子邮件也不会因额外连接而被拒绝。
* **最大消息数**:在连接期间，必须定义允许发送的消息数。如果未定义此号码，服务器将发送尽可能多的数据。 这会导致被识别为垃圾邮件发送者，并被ISP添阻止列表加到中。
* **每小时消息数**:为了与您的电子信誉相匹配，Adobe Campaign将控制您的IP每小时能够发送的电子邮件数量。此系统将保护您免受电子邮件拒绝或/和阻止列表的影响。

## 退回电子邮件

### 什么是Inbounce电子邮件？

这是Adobe Campaign在服务器通信期间用于处理错误的过程。

### “退回”电子邮件的工作原理

错误地址将处理ISP发回的退回。 该过程将分析不同的SMTP错误代码，并根据RegEx标准应用正确的操作。

例如，电子邮件地址由ISP发送反馈“550用户未知”。 此错误代码由Adobe Campaign错误地址(returnpath address)处理。 然后，将该错误与RegEx标准进行比较，并应用正确的规则。 该电子邮件被视为&#x200B;*硬退回*（与类型匹配），然后是&#x200B;*用户未知*（与原因匹配），并在第一个循环进入系统后被隔离。

### Adobe Campaign是如何管理的？

Adobe Campaign通过错误类型与原因之间的匹配来管理此流程：

* **[!UICONTROL User Unknown]**:语法正确但不存在的地址。此错误会被分类为硬退回，并在第一个错误内推送到隔离。
* **[!UICONTROL Mailbox full]**:已达到最大容量的邮箱。此错误还可能表示用户不再使用此邮箱。 此错误会被分类为软退件，并在第三个错误内推入隔离，并在30天后从隔离中删除。
* **[!UICONTROL Inactive User]**:由于用户在过去6个月中处于非活动状态，ISP已停用该邮箱。此错误会被分类为软退件，并在第三个错误内推送到隔离。
* **[!UICONTROL Invalid domain]**:电子邮件地址中的域不存在。此错误会被分类为软退件，并在第三个错误内推送到隔离。
* **[!UICONTROL Refused]**:ISP拒绝向其用户发送电子邮件。此错误会被分类为软退件，并且不会被推送到隔离，因为错误未链接到电子邮件地址，而是IP或/域名声誉。

>[!NOTE]
>
>要了解有关投放失败类型和原因的更多信息，请参阅此[部分](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

## 投放能力实例

MX规则和跳出规则的每日更新由客户端实例中的特定工作流管理，该工作流已连接到这些规则的可交付性实例所有者。

此每日更新针对所有希望通过透明度流程使其实例保持最新的客户。

MX规则具有6个不同的吞吐量级别，这些级别主要用于启动过程：

![](assets/mx-rules-throughput.png)

自定义模式适用于希望设置自己MX规则的高级客户端。 激活自定义模式后，可交付性实例不会更新客户端，因为同步将关闭。

## 跳出示例

* **用户未知** （硬退件）：550 5.1.1 ...用户未知{mx003}
* **邮箱已满** （软退回）：550 5.2.2超出用户配额
* **非活动邮箱** （软退回）：550 5.7.1 :收件人地址被拒绝：不活动的MailBox，不超过6个月
* **域无效** （软退回）：“ourdan.com”的DNS查询失败
* **拒绝** （软退回）：入站电子邮件退回（规则“Feedback_loop_Hotmail”与此退回相匹配）
* **无法访问** （软退回）：421 4.16.55  [TS01] 由于用户投诉过多，x.x.x.x中的消息暂时推迟

**相关主题：**
* [MX配置](../../installation/using/email-deliverability.md#mx-configuration)
* [技术电子邮件配置](../../installation/using/email-deliverability.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic — 技术Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/acc-technical-recommendations.html)
