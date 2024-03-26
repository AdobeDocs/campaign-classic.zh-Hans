---
product: campaign
title: 在 Campaign 中使用 MX 服务器
description: 了解MX服务器如何与Adobe Campaign Classic配合使用
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 2%

---

# 在 Campaign 中使用 MX 服务器 {#using-mx-servers}



了解MX服务器如何与Adobe Campaign Classic配合使用。

## MX服务器 {#mx-servers}

### 什么是MX服务器？

邮件交换器记录（MX记录）是域名系统(DNS)中的一种资源记录，它指定负责代表域接受电子邮件的邮件服务器。

### MX服务器的工作原理是什么？

当您发送电子邮件时，软件服务器将与收件人域服务器建立连接。 两台服务器之间的通信使用SMTP语言，并且一个域可以有多个MX服务器。 与此域的连接将从最高优先级（最小数字）开始，而其他服务器称为“备份”服务器。 必须遵循连接协议。

### MX服务器如何与Adobe Campaign配合使用？

在连接协议中，必须遵守规则以防止发送垃圾邮件和垄断服务器。 最重要的是：

* **允许的最大连接数**&#x200B;列入阻止列表 ：当遵守此数字时，IP不在上，并且电子邮件不会由于额外的连接而被拒绝。
* **最大消息数**：在连接期间，必须定义允许发送的消息数。 如果未定义此数字，服务器将发送尽可能多的数据。 列入阻止列表这会导致被识别为垃圾邮件发送者，并由ISP添加到中。
* **每小时消息数**：为了与您的电子信誉相匹配，Adobe Campaign将控制IP每小时可发送的电子邮件数量。 此系统将保护您免受电子邮件拒绝或/和阻止列表的侵害。

## 退回电子邮件

### 什么是“退回”电子邮件？

这是Adobe Campaign在服务器通信期间用于处理错误的进程。

### 收件箱电子邮件如何工作？

错误地址将处理ISP发回的退信。 该过程将分析不同的SMTP错误代码，并根据RegEx标准应用正确的操作。

例如，电子邮件地址具有由ISP发送的反馈“550用户未知”。 此错误代码由Adobe Campaign错误地址（returnpath地址）处理。 然后，将此错误与RegEx标准进行比较，并应用正确的规则。 该电子邮件被视为 *硬退回* （匹配类型），然后 *用户未知* （匹配原因），并在第一个循环进入系统后进入隔离状态。

### Adobe Campaign如何管理它？

Adobe Campaign通过匹配错误类型和原因来管理此过程：

* **[!UICONTROL User Unknown]**：语法正确但不存在的地址。 此错误被分类为硬退回，并在第一次错误时被隔离。
* **[!UICONTROL Mailbox full]**：已达到最大容量的邮箱。 此错误也可能表明用户不再使用此邮箱。 此错误被分类为软退回，在第三个错误中被推送至隔离区，并在30天后从隔离区中删除。
* **[!UICONTROL Inactive User]**：由于过去6个月内用户停用，ISP已停用邮箱。 此错误被分类为软退回，并在第三个错误中被推送至隔离区。
* **[!UICONTROL Invalid domain]**：电子邮件地址中的域不存在。 此错误被分类为软退回，并在第三个错误中被推送至隔离区。
* **[!UICONTROL Refused]**：ISP拒绝向其用户发送电子邮件。 此错误被分类为软退回，并且不会被推送到隔离区，因为此错误不与电子邮件地址关联，而是与IP或/域信誉关联。

>[!NOTE]
>
>要了解有关投放失败类型和原因的更多信息，请参阅此 [部分](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## 可投放性实例 {#deliveratbility-env}

MX规则和退回规则的每日更新由客户端实例中的特定工作流管理，该特定工作流与这些规则的“可交付性”实例所有者连接。

此每日更新针对所有希望通过透明度流程使其实例保持最新的客户端。

MX规则具有6个不同的吞吐量级别，主要在启动过程中使用：

![](assets/mx-rules-throughput.png)

自定义模式适用于希望设置自己的MX规则的高级客户端。 激活“自定义”模式后，客户端将不会被Deliverability实例更新，因为同步将关闭。

## 退回示例

* **用户未知** （硬退回）：550 5.1.1 ...用户未知 {mx003}
* **邮箱已满** （软退回）：超过550 5.2.2用户配额
* **非活动邮箱** （软退回）：550 5.7.1 ：收件人地址被拒绝：邮箱处于非活动状态，播出时间不超过6个月
* **域无效** （软退回）：“ourdan.com”的DNS查询失败
* **已拒绝** （软退回）：入站电子邮件退回（规则“Feedback_loop_Hotmail”与此退回匹配）
* **不可到达** （软退回）：421 4.16.55 [TS01] x.x.x.x因用户投诉过多而暂时推迟发送的邮件

**相关主题：**
* [MX配置](../../installation/using/email-deliverability.md#mx-configuration)
* [技术电子邮件配置](../../installation/using/email-deliverability.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic — 技术Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
