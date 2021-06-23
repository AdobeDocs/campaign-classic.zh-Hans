---
product: campaign
title: 在 ISP 中断后更新退回限制条件
description: 了解如何在ISP中断后更新退件资格。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# 在Apple中断{#update-bounce-qualification.md}后更新错误的硬退回

## 上下文

2021年4月26日，Apple出现全局问题，导致发送给有效Apple电子邮件地址的某些电子邮件被错误地硬退回，因为Apple服务器将无效电子邮件地址，并出现以下退回响应： “550 5.1.1 &#39;电子邮件地址&#39;:用户查找成功，但未找到用户记录。”

此问题在4/26发生，并持续到美国东部时间上午7点至下午1点。

>[!NOTE]
>
>您可以在[此页面](https://www.apple.com/support/systemstatus/)上查看Apple系统状态功能板。

如果ISP发生中断，则无法成功将通过Campaign发送的电子邮件发送给其收件人：这些电子邮件将被错误地标记为退回。

根据标准退回处理逻辑，Adobe Campaign会自动将这些收件人添加到隔离列表，其中&#x200B;**[!UICONTROL Status]**&#x200B;设置为&#x200B;**[!UICONTROL Quarantine]**。 要更正此问题，您需要通过查找并删除这些收件人，或将其&#x200B;**[!UICONTROL Status]**&#x200B;更改为&#x200B;**[!UICONTROL Valid]**&#x200B;来更新Campaign中的隔离表，以便夜间清理工作流将删除这些收件人。

要查找受此问题影响的收件人，或者如果在其他ISP中再次出现此问题，请参阅下面的说明。

## 更新流程

您需要对隔离表格运行查询，以过滤掉所有可能受中断影响的Apple收件人(包括@icloud.com、@me.com、@mac.com)，以便从隔离列表中删除这些收件人，并将其包含在将来的Campaign电子邮件投放中。

根据事件的时间范围，以下是此查询的建议准则。

>[!IMPORTANT]
>
>这些日期/时间基于东部标准时区(EST)。 请根据实例的时区进行调整。

* 对于隔离列表&#x200B;**[!UICONTROL Error text]**&#x200B;字段中具有SMTP退回响应信息的Campaign实例：

   * **错误文本（隔离文本）** 包含“用户查找成功但未找到用户记录”，而 **错误文本（隔离文本）** 包含“support.apple.com”
   * **上午4/26/2021 07 00** 或之后:00:更新状态(@lastModified)
   * **在4/26/2021 01 00 PM或之前更新状态(@lastModified)** :00:

* 对于隔离列表&#x200B;**[!UICONTROL Error text]**&#x200B;字段中包含入站电子邮件规则信息的Campaign实例：

   * **错误文本（隔离文本）** 包含“Momen_Code10_InvalidRecipient”
   * **电子邮件域(@domain)** 等于icloud.com或 **电子邮件域(@domain)** 等于me.com或 **电子邮件域(@domain)** 等于mac.com
   * **上午4/26/2021 07 00** 或之后:00:更新状态(@lastModified)
   * **在4/26/2021 01 00 PM或之前更新状态(@lastModified)** :00:

获得受影响的收件人列表后，您可以将其设置为状态&#x200B;**[!UICONTROL Valid]** ，以便通过&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流将其从隔离列表中删除，或只从表中删除它们。

**相关主题：**
* [了解投放失败](understanding-delivery-failures.md)
* [退回邮件鉴别](understanding-delivery-failures.md#bounce-mail-qualification)
