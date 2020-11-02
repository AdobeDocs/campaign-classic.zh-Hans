---
title: 在Adobe Campaign Classic定义交互式内容
description: 了解如何使用Adobe Campaign Classic的AMP定义交互式和动态电子邮件内容。
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
translation-type: tm+mt
source-git-commit: 4b98c23f4120cbea6dd54cd68b61202e74bee3e1
workflow-type: tm+mt
source-wordcount: '1572'
ht-degree: 3%

---


# 定义互动内容{#defining-interactive-content}

Adobe Campaign使您能够使用新的交 [互式AMP for Email](https://amp.dev/about/email/) ，该格式允许您在特定条件下发送动态电子邮件。

使用AMP for Email，您可以：
* 测试向正确配置的特定地址传送AMP电子邮件。
* 向相应提供商注册后，将AMP电子邮件发送到Gmail、Outlook或Mail.ru地址。

有关测试和发送AMP电子邮件的更多信息，请 [参阅定位AMP电子邮件](#targeting-amp-email)。

此功能可通过Adobe Campaign专用包获得。 要使用它，必须安装此包。 完成后，重新启动服务器以便考虑包。

>[!NOTE]
>
> 对于混合和托管架构，该软件包需要安装在所有服务器上，包括 [中间源服](../../installation/using/mid-sourcing-server.md) 务器和 [执行实例](../../message-center/using/creating-a-shared-connection.md#execution-instance)。 与您的客户经理联系。

## 关于AMP for Email {#about-amp-for-email}

电子 **邮件的AMP** 新格式允许在邮件中包含AMP组件，以增强具有丰富可操作内容的电子邮件体验。 借助电子邮件中直接提供的现代应用程序功能，收件人可以与邮件中的内容动态交互。

例如：
* 使用AMP编写的电子邮件可以包含交互式元素，如图像轮盘。
* 内容在消息中保持最新。
* 收件人可以采取类似响应表单的操作，而不离开其收件箱。

AMP for Email与现有电子邮件兼容。 除HTML和／或纯文本外，邮件的AMP版本作为新的MIME部分嵌入到电子邮件中，确保所有电子邮件客户端之间的兼容性。

有关AMP的电子邮件格式、规范和要求的详细信息，请参阅AMP开 [发人员文档](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email)。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#amp-email-video)

## 将AMP用于具有Adobe Campaign的电子邮件的关键步骤 {#key-steps-to-use-amp}

要成功测试和发送包含Adobe Campaign的AMP电子邮件，请执行以下步骤：
1. 安装 **[!UICONTROL AMP support]** 包。 请参 [阅安装活动标准包](../../installation/using/installing-campaign-standard-packages.md)。
1. 创建电子邮件并在Adobe Campaign内构建AMP内容。 请参 [阅使用Adobe Campaign构建AMP电子邮件内容](#build-amp-email-content)。
1. 确保遵循支持AMP格式的电子邮件提供商的所有投放要求。 请参 [阅AMP了解电子邮件投放要求](#amp-for-email-delivery-requirements)。
1. 定义目标时，请确保选择能够显示AMP格式的收件人。 请参 [阅定位AMP电子邮件](#targeting-amp-email)。

   >[!NOTE]
   >
   >目前，您只能将AMP电子邮件发送 [到特定电子邮件地址](#testing-amp-delivery-for-selected-addresses) （用于测试目的），或 [在注册](#delivering-amp-emails-by-registering) 到受支持的电子邮件客户端之后。

1. 按您通常的方式发送电子邮件。 请参 [阅发送AMP电子邮件](#sending-amp-email)。

## 在Adobe Campaign中构建AMP电子邮件内容 {#build-amp-email-content}

要使用AMP格式构建电子邮件，请按照以下步骤操作。

>[!IMPORTANT]
>
>确保遵循AMP的电子邮件要求和规范，详见AMP开发 [人员文档](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email)。 您还可以参考AMP [以了解电子邮件最佳实践](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email)。

1. 创建电子邮件投放时，请选择任何模板。

   >[!NOTE]
   >
   >特定AMP模板包含您可以使用的主要容量的示例：产品列表、传送、多次选择加入、调查和高级服务器请求。

1. 单击选 **[!UICONTROL AMP content]** 项卡。

   ![](assets/amp_tab.png)

1. 编辑AMP内容以满足您的需求。

   >[!NOTE]
   >
   >有关构建您的第一封AMP电子邮件的更多信息，请参 [阅AMP开发人员文档](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email)。

   例如，您可以使用AMP模板中的产品列表组件，并维护第三方系统甚至内部Adobe Campaign的产品列表。 无论您何时调整价格或其他元素，当收件人再次打开其邮箱中的电子邮件时，系统都会自动反映出来。

1. 根据需要个性化AMP内容，就像您通常使用Adobe Campaign的HTML格式、个性化字段和个性化块一样。

   ![](assets/amp_tab_perso.png)

1. 编辑完成后，选择整个AMP内容并将其复制粘贴到基于AMP [web的validator或类似的网站](https://validator.ampproject.org) 。

   >[!NOTE]
   >
   >确保从屏 **幕顶部的** “下拉”列表中选择AMP4 EMAIL。

   ![](assets/amp_validator.png)

   所有错误都将内联标记。

   >[!NOTE]
   >
   >Adobe CampaignAMP编辑器不是为内容验证而设计的。 使用外部网站(如基于 [AMP Web的validator](https://validator.ampproject.org) )检查您的内容是否正确。

1. 根据需要进行修改，直到AMP内容通过验证。

   ![](assets/amp_validator_pass.png)

1. 将验证的内容复制粘贴 [到AMP Player](https://playground.amp.dev) 或类似网站以预览您的内容。

   >[!NOTE]
   >
   >确保从屏 **幕顶部的下拉列表** ，选择“AMP for Email”。

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >您不能以预览直接Adobe CampaignAMP内容。 使用外部网站，如 [AMP Playmerd](https://playground.amp.dev)。

1. 返回Adobe Campaign并将验证的内容复制粘贴到选 **[!UICONTROL AMP content]** 项卡。

1. 切换到或选 **[!UICONTROL HTML content]** 项卡 **[!UICONTROL Text content]** ，并为这两种格式中的至少一种定义内容。

   >[!IMPORTANT]
   >
   >如果电子邮件中除AMP内容外不包含HTML或纯文本版本，则无法发送该版本。

## AMP for Email投放要求 {#amp-for-email-delivery-requirements}

在Adobe Campaign下构建AMP内容时，您必须遵守特定于收件人电子邮件提供商的动态电子邮件发送条件。

目前有三家电子邮件提供商支持测试此格式：Gmail、Outlook和Mail.ru。

在相应的Gmail、Outlook和Mail.ru开发人员文档中详细介绍了在Gmail帐户上测试 [使用AMP格式](https://developers.google.com/gmail/ampemail?)投放 [](https://docs.microsoft.com/en-gb/outlook/amphtml/) 所 [需](https://postmaster.mail.ru/amp) 的所有步骤和规范。

特别是必须满足以下要求：
* 遵循Gmail、Outlook和 [Mail](https://developers.google.com/gmail/ampemail/security-requirements).ru [特定](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements)[的](https://postmaster.mail.ru/amp/?lang=en#howto)AMP安全要求。
* AMP MIME部分必须包含有 [效的AMP文档](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email)。
* AMP MIME部件必须小于100KB。

您还可以查阅Tips [和Gmail的已知限制](https://developers.google.com/gmail/ampemail/tips) ，以 [及Outlook的AMP最佳实践](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices)。

## 定位AMP电子邮件 {#targeting-amp-email}

目前，您可以尝试通过两个步骤发送AMP电子邮件：

1. Adobe Campaign允许您测试向所选电子邮件地址传送AMP驱动的动态电子邮件是否进行了适当配置，以验证其内容和行为。 请参 [阅测试AMP电子邮件投放以了解选定的地址](#testing-amp-delivery-for-selected-addresses)。

1. 经过测试后，您可以向相关电子邮件提供商注册，将您的发件人域添加到投放中，从而将允许列表或活动作为电子邮件项目的AMP的一部分发送。 请参 [阅通过向电子邮件提供商注册来传送AMP电子邮件](#delivering-amp-emails-by-registering)。

### 测试选定地址的AMP电子邮件投放 {#testing-amp-delivery-for-selected-addresses}

您可以测试将动态消息从Adobe Campaign发送到选定的电子邮件地址。

>[!NOTE]
>
>目前，只有Gmail、Outlook和Mail.ru支持测试AMP格式。

对于Gmail和Outlook，您必须先将您使用的发件人地址添加到允许列表程序，以便从Adobe Campaign发送您所定位的Gmail和Outlook帐户。

操作步骤：
1. 确保为相关电子邮件提供商选中启用动态电子邮件的选项。
1. 复制投放字段中显示的发件人地 **[!UICONTROL From]** 址，并将其粘贴到电子邮件提供商帐户设置的相应部分。

有关更多详细信息，请 [查阅Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) 和 [Outlook开](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) 发人员文档。

![](assets/amp_from_field.png)

要测试向Mail.ru地址发送AMP电子邮件，请按照Mail.ru开发 [人员文档(如果您是](https://postmaster.mail.ru/amp/?lang=en#howto) 用户部分)中的步骤操作&#x200B;**** 。

### 通过向电子邮件提供商注册来传送AMP电子邮件 {#delivering-amp-emails-by-registering}

您可以尝试通过向受支持的电子邮件提供商注册来传送动态电子邮件，以便将您的发件人域添加到允许列表。

>[!NOTE]
>
>目前，只有Gmail、Outlook和Mail.ru支持AMP格式。

经过几个地址的测试后，您可以向任何Gmail或Outlook地址发送AMP电子邮件。 为此，你必须向谷歌或微软注册，并等待他们的回答。 按照Gmail和Outlook开发人 [员文档](https://developers.google.com/gmail/ampemail/register)[中的](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) 步骤。 成功注册后，您将成为授权发件人。

要向Mail.ru地址发送AMP电子邮件，请遵循Mail.ru开发人 [员文档(如果您是电子邮件发送者部分](https://postmaster.mail.ru/amp/?lang=en#howto)**)中列出的要求和步骤** 。

## 发送AMP电子邮件 {#sending-amp-email}

AMP内容和备份准备就绪后，定义兼容目标后，您可以像通常一样发送电子邮件。

目前，在某些条件下，只有Gmail、Outlook和Mail.ru支持AMP格式。 您可以目标来自其他电子邮件提供商的地址，但他们会收到您电子邮件的HTML或纯文本版本。

>[!IMPORTANT]
>
>如果电子邮件中除AMP内容外不包含HTML或纯文本版本，则无法发送该版本。

匹配的收件人将在其邮箱中显示电子邮件的AMP版本。

例如，如果您在电子邮件中包含产品列表，则在第三方系统中编辑价格时，每次收件人在其邮箱中再次打开该电子邮件时，价格都会自动调整。

>[!NOTE]
>
>您可以创建邮件处理规则，以阻止特定域接收AMP电子邮件。 请参阅 [管理电子邮件格式](../../installation/using/email-deliverability.md#managing-email-formats)。
>
>默认情况 **[!UICONTROL AMP inclusion]** 下，选项设置为 **[!UICONTROL No]**。

## 如何激活和使用AMP处理电子邮件 {#amp-email-video}

以下视频介绍如何在 Adobe Campaign Classic 中激活 AMP。

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)
