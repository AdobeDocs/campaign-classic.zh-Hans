---
solution: Campaign Classic
product: campaign
title: 在 ISP 中断后更新退回限制条件
description: 了解如何在ISP中断后更新跳出资格。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
translation-type: tm+mt
source-git-commit: 7c161862a4ce2e86e7968fd61af6b8ca28d6623f
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 3%

---

# 在Apple中断{#update-bounce-qualification.md}后更新错误的硬弹回

## 上下文

2021年4月26日，Apple的一个全局问题导致发送给有效Apple电子邮件地址的一些电子邮件被错误地硬弹回为无效电子邮件地址，Apple服务器会弹出以下响应： 《550 5.1.1》 <email address>:用户查找成功，但未找到用户记录。”

此问题在2016年4月26日发生，持续时间为美国东部时间早7点至晚1点。

如果ISP中断，则无法将通过活动发送的电子邮件成功发送给其收件人:这些电子邮件会被错误地标为弹回。

>[!NOTE]
>
>可以在[此页](https://www.apple.com/support/systemstatus/)上检查Apple系统状态仪表板。

根据标准弹出处理逻辑，Adobe Campaign将这些收件人自动添加到隔离列表，其设置为&#x200B;**[!UICONTROL Status]** **[!UICONTROL Quarantine]**。 要更正此问题，您需要通过查找和删除这些收件人或将其&#x200B;**[!UICONTROL Status]**&#x200B;更改为&#x200B;**[!UICONTROL Valid]**&#x200B;来更新活动中的隔离表，以便晚间清理工作流将删除它们。

要查找受此问题影响的收件人，或如果其他任何ISP再次出现此问题，请参阅下面的说明。

## 要更新的过程

您需要在隔离表上运行一个查询，以过滤掉所有Apple收件人(包括@icloud.com、@me.com、@mac.com)，这些可能受到中断的影响，因此可以从隔离列表中删除它们，并包含在将来的活动电子邮件投放中。

根据事件的时间范围，以下是本查询的建议准则。

>[!IMPORTANT]
>
>这些日期/时间基于东部标准时区(EST)。 请根据实例的时区进行调整。

* 对于活动实例，在隔离列表的&#x200B;**[!UICONTROL Error text]**&#x200B;字段中显示SMTP弹回响应信息：

   * **错误文本(隔离文本)** 包含“用户查找成功但找不到用户记录”，而 **错误文本(隔离文本)** 包含“support.apple.com”
   * **更新状态(@lastModified)** 在上午4/26/2021点或之后07:00:00点
   * **更新状态(@lastModified)** 在下午4/26/2021点或之前01:00:00点

* 对于活动实例，在隔离列表的&#x200B;**[!UICONTROL Error text]**&#x200B;字段中包含入站电子邮件规则信息：

   * **错误文本(隔离文** 本)包含“Momen_Code10_InvalidRecipient”
   * **Email domain(@domain)** equal to icloud.com&quot; OR Email domain(@domain)equal to me.com&quot; OR Email domain(@domain)equal to mac.com&quot;
   * **更新状态(@lastModified)** 在上午4/26/2021点或之后07:00:00点
   * **更新状态(@lastModified)** 在下午4/26/2021点或之前01:00:00点

列表受影响的收件人后，您可以将其设置为&#x200B;**[!UICONTROL Valid]**&#x200B;状态，以便通过&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流从隔离列表中删除它们，或只从表中删除它们。

**相关主题：**
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [退回邮件鉴别](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
