---
product: campaign
title: 在 ISP 中断后更新退回限制条件
description: 了解如何在ISP中断后更新退回限定条件
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 4%

---

# ISP 中断后更新错误的硬退回 {#update-bounces}



## 上下文{#update-bounce-context}

如果ISP发生中断，通过Campaign发送的电子邮件无法成功发送给收件人：这些电子邮件将被错误标记为跳出。

例如，Apple或Gmail中的全局问题可能会导致发送到有效Apple或Gmail电子邮件地址的某些电子邮件被错误地硬退回为ISP服务器无效的电子邮件地址，并返回以下响应：

* “550 5.1.1 ‘电子邮件地址’：用户查找成功，但未找到用户记录。”

* “550‘电子邮件地址’收件人被拒绝”

请注意，如果观察到延迟跳出并显示消息“452 requested action aborted： try later”（452请求的操作已中止：请稍后重试），则将自动重试这些操作，而无需执行任何操作。 随着ISP恢复全部容量，这些功能应得到改进。

>[!NOTE]
>
>您可以检查Apple系统状态功能板，位于 [此页面](https://www.apple.com/support/systemstatus/){_blank}。
>
>您可以查看Google Workspace状态功能板，网址为 [此页面](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}。

## 影响{#update-bounce-impact}

如果ISP发生中断，通过Campaign发送的电子邮件无法成功发送给收件人：这些电子邮件将被错误标记为跳出。

根据标准退回处理逻辑，Adobe Campaign会使用自动将这些收件人添加到隔离列表 **[!UICONTROL Status]** 设置 **[!UICONTROL Quarantine]**. 要更正此问题，您需要通过查找并移除这些收件人或更改其在Campaign中的隔离表来更新隔离表 **[!UICONTROL Status]** 到 **[!UICONTROL Valid]** 以便“夜间清理”工作流会删除它们。

要查找受此问题影响的收件人，请参阅下面的说明。

## 更新流程{#update-bounce-update}

您需要对隔离表运行查询以筛选出所有受影响的收件人，例如Apple，这些地址包括、@icloud.com、@me.com、@mac.com — 可能受中断影响的收件人，以便将这些收件人从隔离列表中删除，并包含在将来的Campaign电子邮件投放中。

根据事件的时间范围和ISP，以下是此查询的建议准则。

* 对于包含入站电子邮件规则信息的Campaign环境 **[!UICONTROL Error text]** 隔离列表的字段：

   * **错误文本（隔离文本）** 包含“Momen_Code10_InvalidRecipient”
   * **电子邮件域(@domain)** 等于domain1.com或 **电子邮件域(@domain)** 等于domain2.com或 **电子邮件域(@domain)** 等于domain3.com
   * **更新状态(@lastModified)** 在YYYY/MM/DD上或之后HH:MM:SS AM
   * **更新状态(@lastModified)** 在YYYY/MM/DD或之前HH:MM:SS PM

* 对于包含SMTP退回响应信息的Campaign环境 **[!UICONTROL Error text]** 隔离列表的字段：

   * **错误文本（隔离文本）** 包含“550-5.1.1”和 **错误文本（隔离文本）** 包含“support.ISP.com”

      其中“support.ISP.com”可以是：例如“support.apple.com”或“support.google.com”

   * **更新状态(@lastModified)** 在YYYY/MM/DD上或之后HH:MM:SS AM
   * **更新状态(@lastModified)** 在YYYY/MM/DD或之前HH:MM:SS PM


获得受影响的收件人列表后，可以将他们设置为状态 **[!UICONTROL Valid]** 因此它们将被从隔离列表中删除 **[!UICONTROL Database cleanup]** 工作流，或者只是从表中删除它们。

**相关主题：**
* [了解投放失败](understanding-delivery-failures.md)
* [退回邮件鉴别](understanding-delivery-failures.md#bounce-mail-qualification)
