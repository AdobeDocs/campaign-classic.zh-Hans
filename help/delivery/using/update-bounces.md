---
product: campaign
title: 在 ISP 中断后更新退回限制条件
description: 了解如何在ISP中断后更新退回资格
feature: Deliverability
hide: true
hidefromtoc: true
source-git-commit: 9cdd4da153e5e5d1c7203d193067843fe832f38e
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 2%

---

# 在ISP中断后更新错误硬退回 {#update-bounces}

![](../../assets/common.svg)

## 上下文{#update-bounce-context}

如果ISP发生中断，则无法成功将通过Campaign发送的电子邮件发送给其收件人：这些电子邮件将被错误地标记为退回。

例如，Apple或Gmail的全局问题可能会导致ISP服务器将发送到有效Apple或Gmail电子邮件地址的某些电子邮件错误地硬退件为无效电子邮件地址，并出现以下退件响应：

* “550 5.1.1 &#39;电子邮件地址&#39;:用户查找成功，但未找到用户记录。”

* “550 “email address”收件人被拒绝”

请注意，如果延迟退回并显示消息“452请求的操作中止：“稍后重试” — 这些操作将自动重试，无需执行任何操作。 当ISP恢复完整容量时，应该会有所改进。

>[!NOTE]
>
>您可以在上查看Apple系统状态功能板 [本页](https://www.apple.com/support/systemstatus/){_blank}。
>
>您可以在上查看Google Workspace状态功能板 [本页](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}。

## 影响{#update-bounce-impact}

如果ISP发生中断，则无法成功将通过Campaign发送的电子邮件发送给其收件人：这些电子邮件将被错误地标记为退回。

根据标准退回处理逻辑，Adobe Campaign会通过 **[!UICONTROL Status]** 设置 **[!UICONTROL Quarantine]**. 要更正此问题，您需要通过查找和删除这些收件人，或更改其 **[!UICONTROL Status]** to **[!UICONTROL Valid]** 以便夜间清理工作流将删除它们。

要查找受此问题影响的收件人，请参阅下面的说明。

## 更新流程{#update-bounce-update}

您需要对隔离表格运行查询，以过滤掉所有受影响的收件人(例如Apple、地址(包括@icloud.com、@me.com、@mac.com)，这些收件人可能会受到中断的影响，以便从隔离列表中删除，并包含在将来的Campaign电子邮件投放中。

根据事件的时间范围和ISP，以下是此查询的建议准则。

* 对于 **[!UICONTROL Error text]** 隔离列表的字段：

   * **错误文本（隔离文本）** 包含&quot;Momen_Code10_InvalidRecipient&quot;
   * **电子邮件域(@domain)** 等于domain1.com或 **电子邮件域(@domain)** 等于domain2.com或 **电子邮件域(@domain)** 等于domain3.com
   * **更新状态(@lastModified)** YYYY/MM/DD HH或之后:MM:SS AM
   * **更新状态(@lastModified)** YYYY/MM/DD HH上或之前:MM:SS PM

* 对于 **[!UICONTROL Error text]** 隔离列表的字段：

   * **错误文本（隔离文本）** 包含“550-5.1.1”和 **错误文本（隔离文本）** 包含&quot;support.ISP.com&quot;

      其中“support.ISP.com”可以是：例如&quot;support.apple.com&quot;或&quot;support.google.com&quot;

   * **更新状态(@lastModified)** YYYY/MM/DD HH或之后:MM:SS AM
   * **更新状态(@lastModified)** YYYY/MM/DD HH上或之前:MM:SS PM


获得受影响的收件人列表后，您可以将其设置为 **[!UICONTROL Valid]** 这样它们就会被 **[!UICONTROL Database cleanup]** 工作流，或只是从表中删除它们。

**相关主题：**
* [了解投放失败](understanding-delivery-failures.md)
* [退回邮件鉴别](understanding-delivery-failures.md#bounce-mail-qualification)
