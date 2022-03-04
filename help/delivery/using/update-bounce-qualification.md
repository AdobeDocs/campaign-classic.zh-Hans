---
product: campaign
title: 在 ISP 中断后更新退回限制条件
description: 了解如何在ISP中断后更新退回资格
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# 在Apple中断后更新错误硬退回 {#update-bounce-qualification.md}

![](../../assets/common.svg)

## 上下文

2021年4月26日，Apple出现一个全局问题，导致发送到有效Apple电子邮件地址的某些电子邮件被错误地硬退件为由Apple服务器无效的电子邮件地址，并出现以下退件响应：“550 5.1.1 &#39;电子邮件地址&#39;:用户查找成功，但未找到用户记录。”

此问题在4/26发生，并持续到美国东部时间上午7点至下午1点。

>[!NOTE]
>
>您可以在上查看Apple系统状态功能板 [本页](https://www.apple.com/support/systemstatus/).

如果ISP发生中断，则无法成功将通过Campaign发送的电子邮件发送给其收件人：这些电子邮件将被错误地标记为退回。

根据标准退回处理逻辑，Adobe Campaign会通过 **[!UICONTROL Status]** 设置 **[!UICONTROL Quarantine]**. 要更正此问题，您需要通过查找和删除这些收件人，或更改其 **[!UICONTROL Status]** to **[!UICONTROL Valid]** 以便夜间清理工作流将删除它们。

要查找受此问题影响的收件人，或者如果在其他ISP中再次出现此问题，请参阅下面的说明。

## 更新流程

您需要对隔离表运行查询，以过滤掉所有可能受中断影响的Apple收件人(包括@icloud.com、@me.com、@mac.com)，以便将他们从隔离列表中删除，并包含在将来的Campaign电子邮件投放中。

根据事件的时间范围，以下是此查询的建议准则。

>[!IMPORTANT]
>
>这些日期/时间基于东部标准时区(EST)。 请根据实例的时区进行调整。

* 对于SMTP退回响应信息位于 **[!UICONTROL Error text]** 隔离列表的字段：

   * **错误文本（隔离文本）** 包含“用户查找成功但未找到用户记录”和 **错误文本（隔离文本）** 包含&quot;support.apple.com&quot;
   * **更新状态(@lastModified)** 4/26/2021 07或之后:00:上午00点
   * **更新状态(@lastModified)** 4/26/2021 01或之前:00:00 PM

* 对于 **[!UICONTROL Error text]** 隔离列表的字段：

   * **错误文本（隔离文本）** 包含&quot;Momen_Code10_InvalidRecipient&quot;
   * **电子邮件域(@domain)** 等于icloud.com或 **电子邮件域(@domain)** 等于me.com或 **电子邮件域(@domain)** 等于mac.com
   * **更新状态(@lastModified)** 4/26/2021 07或之后:00:上午00点
   * **更新状态(@lastModified)** 4/26/2021 01或之前:00:00 PM

获得受影响的收件人列表后，您可以将其设置为 **[!UICONTROL Valid]** 这样它们就会被 **[!UICONTROL Database cleanup]** 工作流，或只是从表中删除它们。

**相关主题：**
* [了解投放失败](understanding-delivery-failures.md)
* [退回邮件鉴别](understanding-delivery-failures.md#bounce-mail-qualification)
