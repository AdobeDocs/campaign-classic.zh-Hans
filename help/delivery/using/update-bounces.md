---
product: campaign
title: 在 ISP 中断后更新退回鉴定
description: 了解如何在ISP中断后更新退回限制条件
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Deliverability
hide: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
TQID: https://experienceleague.adobe.com/91YUAuxL17kfBm6-hryEpf-A8SPJzA-z-ss9f2maszY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 501
ht-degree: 3%

---

# ISP 中断后更新错误的硬退回 {#update-bounces}



## 上下文{#update-bounce-context}

如果ISP发生中断，通过Campaign发送的电子邮件无法成功发送给收件人：这些电子邮件将被错误标记为退回。

例如，Apple或Gmail中的全局问题可能会导致ISP服务器将发送到有效Apple或Gmail电子邮件地址的某些电子邮件错误地硬退为无效电子邮件地址，并返回以下响应：

* “550 5.1.1 ‘电子邮件地址’：用户查找成功，但未找到用户记录。”

* “550‘电子邮件地址’收件人被拒绝”

请注意，如果观察到延迟跳出并显示消息“452请求的操作已中止：请稍后重试”，则将自动重试这些操作，并且无需任何操作。 随着ISP恢复全部容量，这些功能应该得到改善。

>[!NOTE]
>
>您可以在[此页面](https://www.apple.com/support/systemstatus/){_blank}上查看Apple系统状态仪表板。
>
>您可以在[此页面](https://www.google.com/appsstatus#hl=en&v=status){_blank}上查看Google Workspace状态仪表板。
>

## 影响{#update-bounce-impact}

如果ISP发生中断，通过Campaign发送的电子邮件无法成功发送给收件人：这些电子邮件将被错误标记为退回。

根据标准退回处理逻辑，Adobe Campaign已使用&#x200B;**[!UICONTROL Status]**&#x200B;设置&#x200B;**[!UICONTROL Quarantine]**&#x200B;将这些收件人自动添加到隔离列表。 要更正此问题，您需要在Campaign中更新隔离表，方法是查找并移除这些收件人，或将其&#x200B;**[!UICONTROL Status]**&#x200B;更改为&#x200B;**[!UICONTROL Valid]**，以便夜间清理工作流将移除这些收件人。

要查找受此问题影响的收件人，请参阅下面的说明。

## 更新流程{#update-bounce-update}

您需要对隔离表运行查询以过滤掉所有受影响的收件人，例如Apple，这些地址包括、@icloud.com、@me.com、@mac.com — 这些地址可能受到此次服务中断的影响，因此可以从隔离列表中删除这些地址，并将其包含在将来的Campaign电子邮件投放中。

根据事件的时间范围和ISP，以下是此查询的建议准则。

* 对于在隔离列表的&#x200B;**[!UICONTROL Error text]**&#x200B;字段中包含入站电子邮件规则信息的Campaign环境：

   * **错误文本（隔离文本）**&#x200B;包含“Momen_Code10_InvalidRecipient”
   * **电子邮件域(@domain)**&#x200B;等于domain1.com或&#x200B;**电子邮件域(@domain)**&#x200B;等于domain2.com或&#x200B;**电子邮件域(@domain)**&#x200B;等于domain3.com
   * **更新状态(@lastModified)**&#x200B;在`MM/DD/YYYY HH:MM:SS AM`或之后
   * **在`MM/DD/YYYY HH:MM:SS PM`或之前更新状态(@lastModified)**

* 对于隔离列表的&#x200B;**[!UICONTROL Error text]**&#x200B;字段中包含SMTP退回响应信息的Campaign环境：

   * **错误文本（隔离文本）**&#x200B;包含“550-5.1.1”且&#x200B;**错误文本（隔离文本）**&#x200B;包含“support.ISP.com”

     其中“support.ISP.com”可以是：例如“support.apple.com”或“support.google.com”

   * **更新状态(@lastModified)**&#x200B;在`MM/DD/YYYY HH:MM:SS AM`或之后
   * **在`MM/DD/YYYY HH:MM:SS PM`或之前更新状态(@lastModified)**


在获得受影响的收件人列表后，您可以将他们的状态设置为&#x200B;**[!UICONTROL Valid]**，以便通过&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流将其从隔离列表中删除，或者只是从表中删除他们。

**相关主题：**
* [了解投放失败](delivery-failures-quarantine.md)
* [退回邮件鉴别](delivery-failures-quarantine.md#bounce-mail-qualification)
