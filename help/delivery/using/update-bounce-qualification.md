---
product: campaign
title: 在Apple 2021年中断后更新退回限制条件
description: 了解如何在Apple 2021年中断后更新退回鉴别
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# 在Apple中断{#update-bounce-qualification.md}后更新不正确的硬退回

## 上下文

2021年4月26日，Apple的一个全局问题导致发送到Apple有效电子邮件地址的一些电子邮件被错误地硬退回，作为Apple服务器的无效电子邮件地址，并返回以下响应：“550 5.1.1 ‘电子邮件地址’：用户查找成功但未找到用户记录。”

此问题于2026年4月26日出现，并持续到东部时间上午7点至下午1点。

>[!NOTE]
>
>您可以在[此页面](https://www.apple.com/support/systemstatus/)上查看Apple系统状态仪表板。

如果ISP发生中断，通过Campaign发送的电子邮件无法成功发送给收件人：这些电子邮件将被错误标记为退回。

根据标准退回处理逻辑，Adobe Campaign已使用&#x200B;**[!UICONTROL Status]**&#x200B;设置&#x200B;**[!UICONTROL Quarantine]**&#x200B;将这些收件人自动添加到隔离列表。 要更正此问题，您需要在Campaign中更新隔离表，方法是查找并移除这些收件人，或将其&#x200B;**[!UICONTROL Status]**&#x200B;更改为&#x200B;**[!UICONTROL Valid]**，以便夜间清理工作流将移除这些收件人。

要查找受此问题影响的收件人，或在其他任何ISP再次出现此问题的情况下，请参阅下面的说明。

## 更新流程

您需要对隔离表运行查询以过滤掉所有可能受中断影响的Apple收件人(包括、@icloud.com、@me.com、@mac.com)，以便将这些收件人从隔离列表中删除并包含在将来的Campaign电子邮件投放中。

根据事件的时间范围，以下是此查询的建议准则。

>[!IMPORTANT]
>
>这些日期/时间基于东部标准时区(EST)。 请根据实例的时区进行调整。

* 对于隔离列表的&#x200B;**[!UICONTROL Error text]**&#x200B;字段中包含SMTP退回响应信息的Campaign实例：

   * **错误文本（隔离文本）**&#x200B;包含“用户查找成功但未找到用户记录”以及&#x200B;**错误文本（隔离文本）**&#x200B;包含“support.apple.com”
   * 上午4/26/2021 07:00:00或之后的&#x200B;**更新状态(@lastModified)**
   * 下午4/26/2021 01:00:00或之前&#x200B;**更新状态(@lastModified)**

* 对于在隔离列表的&#x200B;**[!UICONTROL Error text]**&#x200B;字段中包含入站电子邮件规则信息的Campaign实例：

   * **错误文本（隔离文本）**&#x200B;包含“Momen_Code10_InvalidRecipient”
   * **电子邮件域(@domain)**&#x200B;等于icloud.com或&#x200B;**电子邮件域(@domain)**&#x200B;等于me.com或&#x200B;**电子邮件域(@domain)**&#x200B;等于mac.com
   * 上午4/26/2021 07:00:00或之后的&#x200B;**更新状态(@lastModified)**
   * 下午4/26/2021 01:00:00或之前&#x200B;**更新状态(@lastModified)**

在获得受影响的收件人列表后，您可以将他们的状态设置为&#x200B;**[!UICONTROL Valid]**，以便通过&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流将其从隔离列表中删除，或者只是从表中删除他们。

**相关主题：**
* [了解投放失败](understanding-delivery-failures.md)
* [退回邮件鉴别](understanding-delivery-failures.md#bounce-mail-qualification)
