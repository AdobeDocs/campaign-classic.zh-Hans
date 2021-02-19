---
solution: Campaign Classic
product: campaign
title: 使用Adobe Campaign Classic在日本手机上发送电子邮件
description: 了解如何配置、设计和发送将在日文移动设备上阅读的电子邮件。
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: fe4262a1da011cb155651c5e786f19188139cff1
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# 在日文手机上发送电子邮件{#sending-emails-on-japanese-mobiles}

## 日本手机的电子邮件格式{#email-formats-for-japanese-mobiles}

Adobe Campaign管理手机上电子邮件的三种特定日文格式：**Deco-mail**（DoCoMo移动设备）、**Decore Mail**（Softbank移动设备）和&#x200B;**Decoration Mail**（KDDI AU移动设备）。 这些格式会施加特定的编码、结构和大小限制。 了解有关[本节](#limitations-and-recommendations)中限制和建议的更多信息。

为了让收件人正确接收这些格式之一的消息，我们建议在相应用户档案中选择&#x200B;**[!UICONTROL Deco-mail (DoCoMo)]**、**[!UICONTROL Decore Mail (Softbank)]**&#x200B;或&#x200B;**[!UICONTROL Decoration Mail (KDDI AU)]**:

![](assets/deco-mail_03.png)

但是，如果将&#x200B;**[!UICONTROL Email format]**&#x200B;选项保留为&#x200B;**[!UICONTROL Unknown]**、**[!UICONTROL HTML]**&#x200B;或&#x200B;**[!UICONTROL Text]**，则Adobe Campaign将自动检测（发送电子邮件时）要使用的日文格式，以便正确显示消息。

此自动检测系统基于对&#x200B;**[!UICONTROL Management of Email Formats]**&#x200B;邮件规则集中定义的预定义域的列表。 有关管理电子邮件格式的详细信息，请参阅[此页](../../installation/using/email-deliverability.md#managing-email-formats)。

## 限制和建议{#limitations-and-recommendations}

某些限制适用于发送将在日本提供商(Softbank、DoCoMo、KDDI AU)所运营的移动设备上读取的电子邮件。

因此，您必须：

* 仅使用JPEG或GIF格式的图像
* 创建一个投放，其文本和HTML部分严格低于10 000字节（对于KDDI AU和DoCoMo）
* 使用总大小（编码前）小于100 KB的图像
* 每封邮件使用的图像不超过20张
* 使用缩小的HTML格式（每个运算符可以使用有限数量的标签）

>[!NOTE]
>
>创建消息时，应考虑每个运算符的特定限制。 请参阅:
>
>* 对于DoCoMo，请参阅[此页](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* 对于KDDI AU，请参阅[此页](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* 有关软件库，请参阅[此页](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


## 测试电子邮件内容{#testing-the-email-content}

### 预览消息{#previewing-the-message}

Adobe Campaign允许您检查消息格式是否已调整为发送到日文移动设备。

在定义内容并输入电子邮件主题后，您可以检查创建邮件时的显示和格式。

在内容编辑窗口的&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中，单击&#x200B;**[!UICONTROL More... > Deco-mail diagnostic]**&#x200B;可以：

* 检查HTML内容标签是否符合日文格式限制
* 检查邮件中的图像数是否未超过格式设置的限制（20张图像）
* 检查邮件总大小（小于100kB）

   ![](assets/deco-mail_06.png)

### 运行类型规则{#running-typology-rule}

除了预览诊断之外，在发送验证或投放时还执行第二个检查：特定类型规则&#x200B;**[!UICONTROL Deco-mail check]**&#x200B;在分析期间启动。

>[!IMPORTANT]
>
>仅当将至少一个类型规则配置为以&#x200B;**[!UICONTROL Deco-mail (DoCoMo)]**、**[!UICONTROL Decore Mail (Softbank)]**&#x200B;或&#x200B;**[!UICONTROL Decoration Mail (KDDI AU)]**&#x200B;格式接收电子邮件时，才执行此收件人。

此类型规则允许您确保投放遵守日语运算符定义的[格式约束](#limitations-and-recommendations)，特别是与电子邮件的总大小、HTML和文本部分的大小、消息中的图像数以及HTML内容中的标记有关。

### 发送校样{#sending-proofs}

您可以发送验证来测试投放。 发送验证时，如果您使用的是替代地址，请输入与所使用用户档案的电子邮件格式对应的地址。

例如，如果此用户档案的电子邮件格式是在&#x200B;**[!UICONTROL Decore Mail (Softbank)]**&#x200B;上预先定义的，则可以用test@softbank.ne.jp替换用户档案的地址。

![](assets/deco-mail_05.png)

## 发送消息 {#sending-messages}

要向具有活动的日文电子邮件格式的收件人发送电子邮件，可以使用以下两个选项：

* 创建两个投放:一个仅适用于日语收件人，另一个适用于其他收件人 — 请参阅[此部分](#designing-a-specific-delivery-for-japanese-formats)。
* 创建一个投放,Adobe Campaign将自动检测要使用的格式 — 请参阅[此部分](#designing-a-delivery-for-all-formats)。

### 设计日文格式{#designing-a-specific-delivery-for-japanese-formats}的特定投放

您可以创建包含两个投放的工作流：一个在日文移动设备上阅读，另一个在标准电子邮件格式收件人上阅读。

要执行此操作，请在工作流中使用&#x200B;**[!UICONTROL Split]**&#x200B;活动，并将日文电子邮件格式（Deco邮件、装饰邮件和Decore邮件）定义为筛选条件。

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### 设计所有格式{#designing-a-delivery-for-all-formats}的投放

当Adobe Campaign根据域(电子邮件格式定义为&#x200B;**[!UICONTROL Unknown]**、**[!UICONTROL HTML]**&#x200B;或&#x200B;**[!UICONTROL Text]**&#x200B;的用户档案)动态管理格式时，您可以向所有收件人发送相同的投放。

与标准收件人一样，日文手机上的用户将正确显示消息联系人。

>[!IMPORTANT]
>
>请务必遵守与每个日文电子邮件格式（Deco-mail、Decore Mail和Decore Mail）关联的特殊功能。 有关限制的详细信息，请参阅[本节](#limitations-and-recommendations)。
