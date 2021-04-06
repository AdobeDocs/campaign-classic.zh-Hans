---
solution: Campaign Classic
product: campaign
title: 将MX服务器与活动
description: 了解MX服务器如何与Adobe Campaign Classic一起使用。
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
translation-type: tm+mt
source-git-commit: 3b5a6e6f03d9cb26ed372c3df069cbada36756a2
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 0%

---

# 使用活动{#using-mx-servers}的MX服务器

了解MX服务器如何与Adobe Campaign Classic一起使用。

## MX服务器{#mx-servers}

### 什么是MX服务器？

邮件交换器记录（MX记录）是域名系统(DNS)中的资源记录类型，指定负责代表域接受电子邮件消息的邮件服务器。

### MX服务器的工作方式？

当您发送电子邮件时，软件服务器将与收件人域服务器建立连接。 两台服务器之间的通信使用SMTP语言，并且域可以有多台MX服务器。 到此域的连接将从最高优先级（最小的图）开始，其他服务器称为“备份”服务器。 必须遵守连接协议。

### MX服务器如何与Adobe Campaign一起使用？

在连接协议中，必须遵守规则以防止垃圾邮件和垄断服务器。 最重要的是：

* **允许的最大连接数**:当此数字得到尊重时，IP不在阻止列表中，并且不会因额外连接而拒绝电子邮件。
* **最大消息数**:在连接过程中，必须定义允许发送的消息数。如果未定义此号码，服务器将发送尽可能多的数据。 这会导致被识别为垃圾邮件发送者，并被ISP阻止列表添加到该。
* **每小时消息**:为了与您的电子声誉匹配，Adobe Campaign将控制您的IP每小时能够发送的电子邮件数。此系统将保护您免受电子邮件拒绝或/和阻止列表的影响。

## 跳入电子邮件

### 什么是Inbounce电子邮件？

它是Adobe Campaign在服务器通信过程中处理错误的过程。

### Inbounce电子邮件的工作原理是什么？

错误地址将处理ISP发回的回弹。 该过程将分析不同的SMTP错误代码，并根据RegEx标准应用正确的操作。

例如，电子邮件地址有ISP发送的反馈“550用户未知”。 此错误代码由Adobe Campaign错误地址（返回路径地址）处理。 然后，将此错误与RegEx标准进行比较，并应用正确的规则。 该电子邮件被视为&#x200B;*硬弹回*（与类型匹配），然后是&#x200B;*用户未知*（与原因匹配），并在第一个循环进入系统后按隔离。

### Adobe Campaign如何管理它？

Adobe Campaign通过错误类型与原因之间的匹配来管理此进程：

* **[!UICONTROL User Unknown]**:语法正确但不存在的地址。此错误被分类为硬弹回，并在第一个错误中推入隔离。
* **[!UICONTROL Mailbox full]**:已达到最大容量的邮箱。此错误还可能指示用户不再使用此邮箱。 此错误被分类为软弹回，并在第三个错误中推入隔离，在30天后从隔离中删除。
* **[!UICONTROL Inactive User]**:由于过去6个月中用户处于非活动状态，ISP已停用该邮箱。此错误被分类为软弹回，并在第三个错误中推入隔离。
* **[!UICONTROL Invalid domain]**:电子邮件地址中的域不存在。此错误被分类为软弹回，并在第三个错误中推入隔离。
* **[!UICONTROL Refused]**:ISP拒绝将电子邮件发送给其用户。此错误被分类为软跳出，不会推入隔离，因为错误未链接到电子邮件地址，而是IP或域信誉。

>[!NOTE]
>
>要进一步了解投放故障类型和原因，请参阅此[部分](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

## 可交付性实例

MX规则和跳出规则的每日更新由客户端实例中的特定工作流管理，该工作流连接到这些规则的Deliverability实例所有者。

此每日更新针对所有希望通过透明度流程使其实例保持最新的客户。

MX规则有6个不同的吞吐量级别，它们主要在加速过程中使用：

![](assets/mx-rules-throughput.png)

“自定义”模式适用于希望设置自己MX规则的高级客户端。 激活“自定义”模式后，客户端将不会由Deliverability实例更新，因为同步将关闭。

## 跳出示例

* **用户未知** （硬跳出）：550 5.1.1 ...用户未知{mx003}
* **邮箱已满** （软跳出）：550 5.2.2超出用户配额
* **非活动邮箱** （软跳出）：550 5.7.1 :收件人地址被拒绝：不活动的MailBox，超过6个月未打开
* **域无效** （软跳出）：“ourdan.com”的DNS查询失败
* **拒绝** （软弹回）：入站电子邮件弹出（规则“Feedback_loop_Hotmail”与此弹出匹配）
* **不可到达** （软跳出）：421 4.16.55  [x.] x.x.x中的TS01消息因用户投诉过多而暂时推迟

**相关主题：**
* [MX配置](../../installation/using/email-deliverability.md#mx-configuration)
* [技术电子邮件配置](../../installation/using/email-deliverability.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic — 技术Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/acc-technical-recommendations.html)
