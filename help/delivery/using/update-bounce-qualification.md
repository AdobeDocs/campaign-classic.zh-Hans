---
product: campaign
title: 在Apple 2021年中断后更新退回限制条件
description: 了解如何在Apple 2021年中断后更新退回鉴别
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# 在Apple中断后更新不正确的硬退回 {#update-bounce-qualification.md}

## 上下文

2021年4月26日，Apple的一个全局问题导致发送到Apple有效电子邮件地址的一些电子邮件被错误地硬退回，作为Apple服务器的无效电子邮件地址，并返回以下响应：“550 5.1.1 ‘电子邮件地址’：用户查找成功但未找到用户记录。”

此问题于2026年4月26日出现，并持续到东部时间上午7点至下午1点。

>[!NOTE]
>
>您可以在以下位置查看Apple系统状态功能板： [此页面](https://www.apple.com/support/systemstatus/).

如果ISP发生中断，通过Campaign发送的电子邮件无法成功发送给收件人：这些电子邮件将被错误标记为退回。

根据标准退回处理逻辑，Adobe Campaign会使用自动将这些收件人添加到隔离列表 **[!UICONTROL Status]** 设置 **[!UICONTROL Quarantine]**. 要更正此问题，您需要通过查找并移除这些收件人或更改其在Campaign中的隔离表来更新隔离表 **[!UICONTROL Status]** 到 **[!UICONTROL Valid]** 以便“夜间清理”工作流会删除它们。

要查找受此问题影响的收件人，或在其他任何ISP再次出现此问题的情况下，请参阅下面的说明。

## 更新流程

您需要对隔离表运行查询以过滤掉所有可能受中断影响的Apple收件人(包括、@icloud.com、@me.com、@mac.com)，以便将这些收件人从隔离列表中删除并包含在将来的Campaign电子邮件投放中。

根据事件的时间范围，以下是此查询的建议准则。

>[!IMPORTANT]
>
>这些日期/时间基于东部标准时区(EST)。 请根据实例的时区进行调整。

* 对于包含SMTP退回响应信息的Campaign实例，请参阅 **[!UICONTROL Error text]** 隔离列表的字段：

   * **错误文本（隔离文本）** 包含“用户查找成功但未找到用户记录”和 **错误文本（隔离文本）** 包含“support.apple.com”
   * **更新状态(@lastModified)** 2021年4月26日或之后07:00:上午00
   * **更新状态(@lastModified)** 2021年4月26日或之前01:00:下午00

* 对于包含入站电子邮件规则信息的Campaign实例 **[!UICONTROL Error text]** 隔离列表的字段：

   * **错误文本（隔离文本）** 包含“Momen_Code10_InvalidRecipient”
   * **电子邮件域(@domain)** 等于icloud.com或 **电子邮件域(@domain)** 等于me.com或 **电子邮件域(@domain)** 等于mac.com
   * **更新状态(@lastModified)** 2021年4月26日或之后07:00:上午00
   * **更新状态(@lastModified)** 2021年4月26日或之前01:00:下午00

获得受影响的收件人列表后，您可以将其设置为状态 **[!UICONTROL Valid]** 因此它们将被从隔离列表中删除 **[!UICONTROL Database cleanup]** 工作流，或者只是从表中删除它们。

**相关主题：**
* [了解投放失败](understanding-delivery-failures.md)
* [退回邮件鉴别](understanding-delivery-failures.md#bounce-mail-qualification)
