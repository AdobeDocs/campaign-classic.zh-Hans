---
product: campaign
title: 用Adobe Campaign Classic在日本手机上发送电子邮件
description: 了解如何配置、设计和发送将在日文移动设备上阅读的电子邮件
exl-id: 44634227-2340-49c4-b330-740c739ea551
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# 在日本手机上发送电子邮件 {#sending-emails-on-japanese-mobiles}

![](../../assets/common.svg)

## 日本手机的电子邮件格式 {#email-formats-for-japanese-mobiles}

Adobe Campaign管理手机上电子邮件的三种特定日文格式： **Deco-mail** （DoCoMo手机）， **Decore Mail** （软银手机）及 **装饰邮件** （KDDI AU手机）。 这些格式限定了特定的编码、结构和大小限制。 进一步了解 [此部分](#limitations-and-recommendations).

为了让收件人正确接收这些格式之一的消息，我们建议选择 **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** 或 **[!UICONTROL Decoration Mail (KDDI AU)]** 在相应的用户档案中：

![](assets/deco-mail_03.png)

但是，如果您离开 **[!UICONTROL Email format]** 选项作为 **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** 或 **[!UICONTROL Text]**,Adobe Campaign将自动检测（发送电子邮件时）要使用的日语格式，以便正确显示消息。

此自动检测系统基于 **[!UICONTROL Management of Email Formats]** 邮件规则集。 有关管理电子邮件格式的更多信息，请参阅 [本页](../../installation/using/email-deliverability.md#managing-email-formats).

## 限制和建议 {#limitations-and-recommendations}

某些限制适用于发送将在由日本提供商（软银、DoCoMo、KDDI AU）运营的移动设备上读取的电子邮件。

因此，您必须：

* 仅以JPEG或GIF格式使用图像
* 创建文本节和HTML节严格小于10 000字节的投放（对于KDDI AU和DoCoMo）
* 使用总大小（编码前）小于100 KB的图像
* 每封邮件使用的图像不超过20张
* 使用缩小的HTML格式（每个运算符可以使用有限数量的标记）

>[!NOTE]
>
>创建消息时，应考虑每个运算符的特定限制。 请参阅:
>
>* 有关DoCoMo，请参阅 [本页](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* 对于KDDI AU，请参阅 [本页](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* 对于软银，请参阅 [本页](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


## 测试电子邮件内容 {#testing-the-email-content}

### 预览消息 {#previewing-the-message}

Adobe Campaign允许您检查消息格式是否已调整为发送到日语移动设备。

定义内容并输入电子邮件主题后，即可在创建消息时检查其显示和格式。

在 **[!UICONTROL Preview]** 选项卡，单击 **[!UICONTROL More... > Deco-mail diagnostic]** 允许您：

* 检查HTML内容标记是否符合日语格式限制
* 检查消息中的图像数量是否未超过格式（20张图像）所规定的限制
* 检查消息总大小（小于100kB）

   ![](assets/deco-mail_06.png)

### 运行分类规则 {#running-typology-rule}

除了预览诊断之外，还会在发送校样或投放时执行第二次检查：特定的分类规则， **[!UICONTROL Deco-mail check]**，分析期间会启动。

>[!IMPORTANT]
>
>仅当至少有一个收件人配置为在 **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** 或 **[!UICONTROL Decoration Mail (KDDI AU)]** 格式。

利用此分类规则，可确保投放遵循 [格式约束](#limitations-and-recommendations) 由日语运算符定义，特别是与电子邮件总大小、HTML和文本部分的大小、消息中的图像数量以及HTML内容中的标记有关。

###   发送验证 {#sending-proofs}

您可以发送校样以测试投放。 发送校样时，如果您使用的是替换地址，请输入与所用用户档案的电子邮件格式对应的地址。

例如，如果用户档案的电子邮件格式是在 **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

## 发送消息 {#sending-messages}

要使用Campaign以日语电子邮件格式向收件人发送电子邮件，可以选择以下两个选项：

* 创建两个投放：一个仅用于日语收件人，另一个用于其他收件人 — 请参阅 [此部分](#designing-a-specific-delivery-for-japanese-formats).
* 创建单个投放，Adobe Campaign将自动检测要使用的格式 — 请参阅 [此部分](#designing-a-delivery-for-all-formats).

### 为日语格式设计特定交付内容 {#designing-a-specific-delivery-for-japanese-formats}

您可以创建包含两个投放的工作流：一个在日文移动设备上阅读，另一个在标准电子邮件格式的收件人上阅读。

为此，请使用 **[!UICONTROL Split]** 活动，并将日语电子邮件格式（Deco-mail、Decore Mail和Decore Mail）定义为筛选条件。

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### 设计所有格式的投放 {#designing-a-delivery-for-all-formats}

当Adobe Campaign根据域(定义为 **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** 或 **[!UICONTROL Text]** )，则可以向所有收件人发送相同的投放。

消息联系人将正确显示给日本手机上的用户，就像标准收件人一样。

>[!IMPORTANT]
>
>确保遵循与每种日文电子邮件格式（Deco-mail、Decore Mail和Decore Mail）相关的特殊功能。 有关限制的更多信息，请参阅 [此部分](#limitations-and-recommendations).
