---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign Classic中定义交互式内容
description: 了解如何使用Adobe Campaign Classic中的AMP定义交互式和动态电子邮件内容。
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
translation-type: tm+mt
source-git-commit: d5579fa1928888a088fe99b685f4d12bf2bde25b
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 3%

---

# 定义互动内容{#defining-interactive-content}

Adobe Campaign使您能够使用新的交互式[AMP for Email](https://amp.dev/about/email/)格式，该格式允许在某些条件下发送动态电子邮件。

通过AMP for Email，您可以：
* 测试向正确配置的特定地址传送AMP电子邮件。
* 向相应的提供商注册后，将AMP电子邮件发送到Gmail、Outlook或Mail.ru地址。

有关测试和发送AMP电子邮件的详细信息，请参阅[定位AMP电子邮件](#targeting-amp-email)。

此功能可通过Adobe Campaign中的专用包获得。 要使用它，必须安装此包。 完成后，重新启动服务器以便将包考虑在内。

>[!NOTE]
>
> 对于混合和托管架构，包需要安装在所有服务器上，包括[中间源服务器](../../installation/using/mid-sourcing-server.md)和[执行实例](../../message-center/using/creating-a-shared-connection.md#execution-instance)。 联系您的客户经理。

## 关于电子邮件{#about-amp-for-email}的AMP

**Email**&#x200B;的AMP新格式允许将AMP组件包含在邮件中，以增强包含丰富且可操作内容的电子邮件体验。 借助电子邮件中直接提供的现代应用程序功能，收件人可以与邮件中的内容动态交互。

例如：
* 使用AMP编写的电子邮件可以包含交互式元素，如图像轮盘。
* 内容在消息中保持最新。
* 收件人可以采取类似响应表单等操作，而不离开其收件箱。

AMP for Email与现有电子邮件兼容。 除HTML和/或纯文本外，邮件的AMP版本作为新的MIME部分嵌入到电子邮件中，可确保所有电子邮件客户端之间的兼容性。

有关AMP的电子邮件格式、规范和要求的详细信息，请参阅[AMP开发人员文档](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email)。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#amp-email-video)

## 将AMP用于电子邮件且Adobe Campaign{#key-steps-to-use-amp}的关键步骤

要成功测试和发送包含Adobe Campaign的AMP电子邮件，请执行以下步骤：
1. 安装&#x200B;**[!UICONTROL AMP support]**&#x200B;包。 请参阅[安装活动内置包](../../installation/using/installing-campaign-standard-packages.md)。
1. 在Adobe Campaign中创建电子邮件并构建AMP内容。 请参阅[使用Adobe Campaign](#build-amp-email-content)构建AMP电子邮件内容。
1. 确保遵循支持AMP格式的电子邮件提供商的所有投放要求。 请参阅[AMP以了解电子邮件投放要求](#amp-for-email-delivery-requirements)。
1. 定义目标时，请确保选择能够显示AMP格式的收件人。 请参阅[定位AMP电子邮件](#targeting-amp-email)。

   >[!NOTE]
   >
   >目前，您只能将AMP电子邮件发送到[特定电子邮件地址](#testing-amp-delivery-for-selected-addresses)（用于测试目的）或在[注册](#delivering-amp-emails-by-registering)之后。

1. 按您通常的方式发送电子邮件。 请参阅[发送AMP电子邮件](#sending-amp-email)。

## 在Adobe Campaign {#build-amp-email-content}中构建AMP电子邮件内容

要使用AMP格式构建电子邮件，请执行以下步骤。

>[!IMPORTANT]
>
>确保按照[AMP开发人员文档](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email)中详细说明的电子邮件要求和规范遵循AMP。 您还可以查阅[AMP以了解电子邮件最佳实践](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email)。

1. 创建电子邮件投放时，选择任何模板。

   >[!NOTE]
   >
   >特定AMP模板包含您可以使用的主要容量的示例：产品列表、传送、多次选择加入、调查和高级服务器请求。

1. 单击&#x200B;**[!UICONTROL AMP content]**&#x200B;选项卡。

   ![](assets/amp_tab.png)

1. 编辑AMP内容以满足您的需求。

   >[!NOTE]
   >
   >有关构建您的第一封AMP电子邮件的详细信息，请参阅[AMP开发人员文档](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email)。

   例如，您可以使用AMP模板中的产品列表组件，并维护第三方系统甚至Adobe Campaign内的产品列表。 无论您何时调整价格或其他元素，当收件人再次打开其邮箱中的电子邮件时，系统都会自动反映价格或其他元素。

1. 根据需要个性化AMP内容，就像您通常使用Adobe Campaign中的HTML格式、个性化字段和个性化块一样。

   ![](assets/amp_tab_perso.png)

1. 编辑完成后，选择整个AMP内容并将其复制粘贴到[基于AMP Web的validator](https://validator.ampproject.org)或类似网站中。

   >[!NOTE]
   >
   >确保从屏幕顶部的下拉列表中选择&#x200B;**AMP4 EMAIL**。

   ![](assets/amp_validator.png)

   所有错误都将内联标记。

   >[!NOTE]
   >
   >Adobe Campaign AMP编辑器不是为内容验证而设计的。 使用外部网站（如[AMP基于Web的validator](https://validator.ampproject.org)）检查您的内容是否正确。

1. 根据需要进行修改，直到AMP内容通过验证。

   ![](assets/amp_validator_pass.png)

1. 将已验证的内容复制 — 粘贴到[AMP Playment](https://playground.amp.dev)或类似网站中，以预览您的内容。

   >[!NOTE]
   >
   >确保从屏幕顶部的下拉列表中为Email **选择** AMP。

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >不能直接在Adobe Campaign中预览AMP内容。 使用外部网站，如[AMP Playment](https://playground.amp.dev)。

1. 返回Adobe Campaign并将验证内容复制粘贴到&#x200B;**[!UICONTROL AMP content]**&#x200B;选项卡。

1. 切换到&#x200B;**[!UICONTROL HTML content]**&#x200B;或&#x200B;**[!UICONTROL Text content]**&#x200B;选项卡，为这两种格式中的至少一种定义内容。

   >[!IMPORTANT]
   >
   >如果您的电子邮件除了AMP内容之外不包含HTML或纯文本版本，则无法发送该版本。

## 电子邮件投放要求{#amp-for-email-delivery-requirements}

在Adobe Campaign中构建AMP内容时，您必须遵守特定于收件人电子邮件提供商的动态电子邮件发送条件。

目前有三家电子邮件提供商支持测试此格式：Gmail、Outlook和Mail.ru。

在相应的[Gmail](https://developers.google.com/gmail/ampemail?)、[Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/)和[Mail.ru](https://postmaster.mail.ru/amp)开发人员文档中详细说明了在Gmail帐户上测试使用AMP格式投放所需的所有步骤和规范。

特别是，必须满足以下要求：
* 按照特定于[Gmail](https://developers.google.com/gmail/ampemail/security-requirements)、[Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements)和[Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto)的AMP安全要求进行操作。
* AMP MIME部分必须包含[有效的AMP文档](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email)。
* AMP MIME部分必须小于100KB。

您还可以查阅[Tips和Gmail](https://developers.google.com/gmail/ampemail/tips)的已知限制以及Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices)的[AMP最佳实践。

## 定位AMP电子邮件{#targeting-amp-email}

目前，您可以尝试通过两个步骤发送AMP电子邮件：

1. Adobe Campaign允许您测试向正确配置的选定电子邮件地址传送AMP驱动的动态电子邮件，以验证其内容和行为。 请参阅[测试选定地址的AMP电子邮件投放](#testing-amp-delivery-for-selected-addresses)。

1. 经过测试后，您可以向相关电子邮件提供商注册，将您的发件人域添加到投放中，从而将允许列表或活动作为AMP for Email项目的一部分发送。 请参阅[通过向电子邮件提供商注册来传送AMP电子邮件](#delivering-amp-emails-by-registering)。

### 正在测试选定地址{#testing-amp-delivery-for-selected-addresses}的AMP电子邮件投放

您可以测试将动态消息从Adobe Campaign发送到选定的电子邮件地址。

>[!NOTE]
>
>目前只有Gmail、Outlook和Mail.ru支持测试AMP格式。

对于Gmail和Outlook，您必须首先将您使用的发件人地址添加允许列表到Adobe Campaign，以便从您定位的Gmail和Outlook帐户发送。

操作步骤：
1. 确保为相关电子邮件提供商选中了启用动态电子邮件的选项。
1. 复制投放&#x200B;**[!UICONTROL From]**&#x200B;字段中显示的发件人地址，并将其粘贴到您的电子邮件提供商帐户设置的相应部分。

有关更多详细信息，请查阅[Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email)和[Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration)开发人员文档。

![](assets/amp_from_field.png)

要测试向Mail.ru地址发送AMP电子邮件，请按照[Mail.ru开发人员文档](https://postmaster.mail.ru/amp/?lang=en#howto)（**如果您是用户**&#x200B;部分）中的步骤进行操作。

### 通过向电子邮件提供商{#delivering-amp-emails-by-registering}注册来传送AMP电子邮件

您可以通过向支持的电子邮件提供商注册来尝试传送动态电子邮件，以便将您的发件人域添加到允许列表。

>[!NOTE]
>
>目前只有Gmail、Outlook和Mail.ru支持AMP格式。

经过几个地址的测试后，您可以向任何Gmail或Outlook地址发送AMP电子邮件。 为此，你必须向谷歌或微软注册，并等待他们的回答。 按照[Gmail](https://developers.google.com/gmail/ampemail/register)和[Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration)开发人员文档中介绍的步骤操作。 成功注册后，您将成为授权发件人。

要将AMP电子邮件发送到Mail.ru地址，请按照[Mail.ru开发人员文档](https://postmaster.mail.ru/amp/?lang=en#howto)（**如果您是电子邮件发件人**&#x200B;部分）中列出的要求和步骤进行操作。

## 发送AMP电子邮件{#sending-amp-email}

AMP内容和备份准备就绪后，定义了兼容目标后，您可以像正常情况下一样发送电子邮件。

目前，在某些条件下，只有Gmail、Outlook和Mail.ru支持AMP格式。 您可以目标其他电子邮件提供商的地址，但他们会收到您电子邮件的HTML或纯文本版本。

>[!IMPORTANT]
>
>如果您的电子邮件除了AMP内容之外不包含HTML或纯文本版本，则无法发送该版本。

匹配的收件人将在其邮箱中显示电子邮件的AMP版本。

例如，如果您在电子邮件中包含产品列表，则在第三方系统中编辑价格时，每次收件人在其邮箱中再次打开该电子邮件时，价格将自动调整。

>[!NOTE]
>
>您可以创建邮件处理规则，以阻止特定域接收AMP电子邮件。 请参阅[管理电子邮件格式](../../installation/using/email-deliverability.md#managing-email-formats)。
>
>默认情况下，**[!UICONTROL AMP inclusion]**&#x200B;选项设置为&#x200B;**[!UICONTROL No]**。

## 教程视频{#amp-email-video}

以下视频介绍如何在 Adobe Campaign 中激活 AMP。

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

其他活动操作视频[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)可用。
