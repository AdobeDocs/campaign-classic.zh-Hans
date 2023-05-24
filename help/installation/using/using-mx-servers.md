---
product: campaign
title: 在 Campaign 中使用 MX 服务器
description: 了解MX服务器如何与Adobe Campaign Classic配合使用
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 1%

---

# 在 Campaign 中使用 MX 服务器 {#using-mx-servers}



了解MX服务器如何与Adobe Campaign Classic配合使用。

## MX服务器 {#mx-servers}

### 什么是MX服务器？

邮件交换器记录（MX记录）是域名系统(DNS)中的一种资源记录，指定负责代表域接受电子邮件的邮件服务器。

### MX服务器如何工作？

当您发送电子邮件时，软件服务器将与收件人域服务器建立连接。 两台服务器之间的通信使用SMTP语言，并且一个域可以有多个MX服务器。 与此域的连接将从最高优先级（最小数字）开始，而其他服务器称为“备份”服务器。 必须遵循连接协议。

### MX服务器如何与Adobe Campaign配合使用？

在连接协议中，必须遵守规则以防止发送垃圾信息和垄断服务器。 最重要的是：

* **允许的最大连接数**&#x200B;阻止列表 ：当遵守此数字时，IP不在上，并且电子邮件不会由于额外的连接而被拒绝。
* **最大消息数**：在连接期间，必须定义允许发送的消息数。 如果未定义此数字，服务器将发送尽可能多的数据。 阻止列表这会导致被识别为垃圾邮件发送者，并由ISP添加到。
* **每小时消息数**：为了与您的电子信誉相匹配，Adobe Campaign将控制您的IP每小时能够发送的电子邮件数量。 此系统将保护您免受电子邮件拒绝或/和阻止列表的侵扰。

## 退回电子邮件

### 什么是退回电子邮件？

Adobe Campaign在服务器通信期间用于处理错误的进程。

### Inbounce电子邮件如何工作？

错误地址将处理ISP发回的退信。 该过程将分析不同的SMTP错误代码，并根据RegEx标准应用正确的操作。

例如，电子邮件地址包含ISP发送的反馈“550用户未知”。 此错误代码由Adobe Campaign错误地址（returnpath地址）处理。 然后，将此错误与RegEx标准进行比较，并应用正确的规则。 该电子邮件被视为 *硬退回* （匹配类型），然后 *用户未知* （匹配原因），并在第一个循环进入系统后进入隔离区。

### Adobe Campaign如何管理它？

Adobe Campaign通过匹配错误类型和原因来管理此过程：

* **[!UICONTROL User Unknown]**：语法正确但不存在的地址。 此错误被归类为硬退回，并在第一次出错时被添加到隔离区。
* **[!UICONTROL Mailbox full]**：已达到最大容量的邮箱。 此错误也可能表示用户不再使用此邮箱。 此错误被归类为软退回，在第三个错误中被推送至隔离，并在30天后从隔离中删除。
* **[!UICONTROL Inactive User]**：由于过去6个月内用户停用，ISP已停用邮箱。 此错误被分类为软退回，并在第三个错误中被隔离。
* **[!UICONTROL Invalid domain]**：电子邮件地址中的域不存在。 此错误被分类为软退回，并在第三个错误中被隔离。
* **[!UICONTROL Refused]**：ISP拒绝向其用户投放电子邮件。 此错误被分类为软退回，不会推送到隔离区，因为错误未链接到电子邮件地址，而是与IP或/域信誉关联。

>[!NOTE]
>
>要了解有关投放失败类型和原因的更多信息，请参阅此 [部分](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## 可投放性实例 {#deliveratbility-env}

MX规则和退回规则的每日更新由客户端实例中的特定工作流管理，该工作流与这些规则的Deliverability实例所有者连接。

此每日更新针对所有希望通过透明流程使其实例保持最新的客户端。

MX规则具有6个不同的吞吐量级别，主要用于提升过程：

![](assets/mx-rules-throughput.png)

自定义模式适用于希望设置自己的MX规则的高级客户端。 激活自定义模式后，客户端将不会被可投放性实例更新，因为同步将关闭。

## 退回示例

* **用户未知** （硬退回）：550 5.1.1 ...用户未知{mx003}
* **邮箱已满** （软退回）：超过550 5.2.2用户配额
* **非活动邮箱** （软退回）：550 5.7.1 ：收件人地址被拒绝：邮箱处于非活动状态，弹出时间不超过6个月
* **域无效** （软退回）：“ourdan.com”的DNS查询失败
* **已拒绝** （软退回）：入站电子邮件退回（规则“Feedback_loop_Hotmail”与此退回匹配）
* **不可到达** （软退回）：421 4.16.55 [TS01] 由于用户投诉过多，来自x.x.x.x的邮件暂时延期

**相关主题：**
* [MX配置](../../installation/using/email-deliverability.md#mx-configuration)
* [技术电子邮件配置](../../installation/using/email-deliverability.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic — 技术Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
