---
solution: Campaign Classic
product: campaign
title: 在ISP中断后更新退出资格
description: 了解如何在ISP中断后更新跳出资格。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 0c93193ff30737870803f9fb25019f3162dcc96d
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---


# 在ISP中断{#update-bounce-qualification.md}后更新跳出资格

## 上下文

如果ISP中断，则无法将通过活动发送的电子邮件成功发送给其收件人:这些电子邮件会被错误地标为弹回。

2020年12月，Gmail出现全球问题，导致一些发送到有效Gmail电子邮件地址的电子邮件被Gmail服务器错误地硬弹回为无效电子邮件地址，并出现以下弹回响应：*&quot;550-5.1.1您尝试访问的电子邮件帐户不存在。&quot;*

谷歌称，导致此问题的Gmail中断和中断从12月14日早6:55开始，到12月15日美国东部标准时间下午6:09结束。 我们的数据分析还显示，美国东部标准时间12月16日凌晨2点06分，Gmail弹回率出现了非常短的飙升，其中大部分发生在美国东部标准时间12月15日下午2点至下午6点30分之间。

>[!NOTE]
>
>您可以在[此页面](https://www.google.com/appsstatus#hl=en&amp;v=status)上检查Google Workspace状态仪表板。


根据标准弹出处理逻辑，Adobe Campaign将这些收件人自动添加到隔离列表，其设置为&#x200B;**[!UICONTROL Status]** **[!UICONTROL Quarantine]**。 要更正此问题，您需要通过查找和删除这些收件人或将其&#x200B;**[!UICONTROL Status]**&#x200B;更改为&#x200B;**[!UICONTROL Valid]**&#x200B;来更新活动中的隔离表，以便晚间清理工作流将删除它们。

要查找受此Gmail问题影响的收件人，或如果在任何其他ISP中再次出现此问题，请参阅下面的说明。

## 要更新的过程

您需要在隔离表上运行查询，以过滤掉所有可能受中断影响的Gmail（或其他ISP）收件人，以便从隔离列表中删除这些，并将其包含在将来的活动电子邮件投放中。

根据事件的时间范围，以下是本查询的建议准则。

>[!IMPORTANT]
>
>这些日期/时间基于东部标准时区(EST)。 请根据实例的时区进行调整。

* 对于活动实例，在隔离列表的&#x200B;**[!UICONTROL Error text]**&#x200B;字段中显示SMTP弹回响应信息：

   * **错误文本(隔离文** 本)包含“550-5.1.1您尝试访问的电子邮件帐户不存在”，错误 **文本(隔离文本)** 包含“support.google.com” **
   * **更新状态(@lastModified)** 在上午12/14/2020点或之后6:55:00点
   * **更新状态(@lastModified)** 在上午12/16/2020点或之前6:00:00点

* 对于活动实例，在隔离列表的&#x200B;**[!UICONTROL Error text]**&#x200B;字段中包含入站电子邮件规则信息：

   * **错误文本(隔离文** 本)包含“Momen_Code10_InvalidRecipient”
   * **电子邮件域(@domain)** 等于“gmail.com”，或电子邮件域(@domain)等于“googlemail.com”
   * **更新状态(@lastModified)** 在上午12/14/2020点或之后6:55:00点
   * **更新状态(@lastModified)** 在上午12/16/2020点或之前6:00:00点

列表受影响的收件人后，您可以将其设置为&#x200B;**[!UICONTROL Valid]**&#x200B;状态，以便通过&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流从隔离列表中删除它们，或只从表中删除它们。

**相关主题：**
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [退回邮件鉴别](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)

