---
product: campaign
title: 在Adobe Campaign Classic中定义交互式内容
description: 了解如何在Adobe Campaign中使用AMP定义交互式动态电子邮件内容
feature: Email Design, Dynamic Content
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 3%

---

# 定义交互式内容{#defining-interactive-content}

![](../../assets/common.svg)

Adobe Campaign允许您使用新的 [用于电子邮件的AMP](https://amp.dev/about/email/) 格式，它允许在特定条件下发送动态电子邮件。

使用AMP for Email，您可以：
* 测试向正确配置的特定地址发送AMP电子邮件。
* 在向相应的提供商注册后，将AMP电子邮件发送到Gmail、Outlook或Mail.ru地址。

有关测试和发送AMP电子邮件的更多信息，请参阅 [此部分](#targeting-amp-email).

此功能可通过Adobe Campaign中的专用包获取。 根据您的权限和部署模型，您可以安装此包或联系Adobe以为您安装。

>[!NOTE]
>
> 对于混合和托管架构，必须在所有服务器上安装该包，包括 [中间源服务器](../../installation/using/mid-sourcing-server.md) 和 [执行实例](../../message-center/using/configuring-instances.md#execution-instance).


## 关于电子邮件的AMP {#about-amp-for-email}

使用 **用于电子邮件的AMP** 新格式，可在邮件中包含AMP组件，并通过丰富且可操作的内容改善电子邮件体验。 借助电子邮件中直接提供的现代应用程序功能，收件人可以动态地与消息本身中的内容进行交互。

例如：
* 使用AMP编写的电子邮件可以包含交互式元素，如图像轮播。
* 消息中的内容保持为最新。
* 收件人无需离开收件箱即可回复表单。

AMP for Email与现有电子邮件兼容。 除了HTML和/或纯文本之外，AMP版本的消息还会作为新的MIME部分嵌入到电子邮件中，从而确保所有电子邮件客户端之间的兼容性。

有关AMP for Email格式、规范和要求的更多信息，请参阅 [AMP开发人员文档](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email).

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#amp-email-video)

## 将AMP用于电子邮件与Adobe Campaign结合使用的关键步骤 {#key-steps-to-use-amp}

要使用Adobe Campaign成功测试和发送AMP电子邮件，请执行以下步骤：
1. 安装 **[!UICONTROL AMP support]** 包。 请参阅 [安装Campaign内置软件包](../../installation/using/installing-campaign-standard-packages.md).
1. 在Adobe Campaign中创建电子邮件并构建AMP内容。 请参阅 [使用Adobe Campaign构建AMP电子邮件内容](#build-amp-email-content).
1. 确保遵循支持AMP格式的电子邮件提供商的所有投放要求。 请参阅 [适用于电子邮件投放要求的AMP](#amp-for-email-delivery-requirements).
1. 在定义目标时，请确保选择能够显示AMP格式的收件人。 请参阅 [定位AMP电子邮件](#targeting-amp-email).

   >[!NOTE]
   >
   >目前，您只能将AMP电子邮件发送到 [特定电子邮件地址](#testing-amp-delivery-for-selected-addresses) （用于测试目的或之后） [注册](#delivering-amp-emails-by-registering) 与支持的电子邮件客户端。

1. 照常发送电子邮件。 请参阅 [发送AMP电子邮件](#sending-amp-email).

## 在Adobe Campaign中构建AMP电子邮件内容 {#build-amp-email-content}

要使用AMP格式构建电子邮件，请执行以下步骤。

>[!IMPORTANT]
>
>确保您遵循AMP中有关电子邮件要求和规范的详细说明，详见 [AMP开发人员文档](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email). 您还可以查阅 [AMP for Email最佳实践](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email).

1. 创建电子邮件投放时，选择任意模板。

   >[!NOTE]
   >
   >特定的AMP模板包含您可以使用的主要容量示例：产品列表、轮播、双重选择加入、调查和高级服务器请求。

1. 单击 **[!UICONTROL AMP content]** 选项卡。

   ![](assets/amp_tab.png)

1. 编辑AMP内容以满足您的需求。

   >[!NOTE]
   >
   >有关构建您的第一封AMP电子邮件的更多信息，请参阅 [AMP开发人员文档](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email).

   例如，您可以使用AMP模板中的产品列表组件，并维护第三方系统甚至Adobe Campaign中的产品列表。 每当您调整价格或其他元素时，当收件人从其邮箱中打开电子邮件时，系统都会自动反映该价格或其他元素。

1. 根据需要，使用个性化字段和个性化块对AMP内容进行个性化，就像Adobe Campaign中的HTML格式一样。

   ![](assets/amp_tab_perso.png)

1. 完成编辑后，选择整个AMP内容，并将其复制粘贴到 [基于AMP Web的验证器](https://validator.ampproject.org) 或类似的网站。

   >[!NOTE]
   >
   >确保选择 **AMP4电子邮件** 从屏幕顶部的下拉列表。

   ![](assets/amp_validator.png)

   错误标记为内联。

   >[!NOTE]
   >
   >Adobe Campaign AMP编辑器不用于内容验证。 使用外部网站，例如 [基于AMP Web的验证器](https://validator.ampproject.org) 来检查内容是否正确。

1. 在AMP内容通过验证之前，根据需要进行修正。

   ![](assets/amp_validator_pass.png)

1. 要预览内容，请将已验证的内容复制粘贴到 [AMP游乐场](https://playground.amp.dev) 或类似的网站。

   >[!NOTE]
   >
   >确保选择 **用于电子邮件的AMP** 从屏幕顶部的下拉列表。

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >无法直接在Adobe Campaign中预览AMP内容。 使用外部网站，例如 [AMP游乐场](https://playground.amp.dev).

1. 返回Adobe Campaign，并将已验证的内容复制粘贴到 **[!UICONTROL AMP content]** 选项卡。

1. 切换到 **[!UICONTROL HTML content]** 或 **[!UICONTROL Text content]** 选项卡，并为这两种格式中的至少一种格式定义内容。

   >[!IMPORTANT]
   >
   >如果除AMP内容外，您的电子邮件中不包含HTML或纯文本版本，则无法发送该版本。

## 适用于电子邮件投放要求的AMP {#amp-for-email-delivery-requirements}

在Adobe Campaign中构建AMP内容时，您必须符合要发送的动态电子邮件的条件，这些条件特定于收件人的电子邮件提供商。

目前有三个电子邮件提供商支持测试此格式：Gmail、Outlook和Mail.ru。

在Gmail帐户上使用AMP格式测试投放所需的所有步骤和规范都将在相应的 [Gmail](https://developers.google.com/gmail/ampemail?), [Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/)和 [Mail.ru](https://postmaster.mail.ru/amp) 开发人员文档。

特别是必须满足以下要求：
* 遵循特定于的AMP安全要求 [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements)和 [Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto).
* AMP MIME部分必须包含 [有效的AMP文档](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email).
* AMP MIME部分必须小于100KB。

您还可以查阅 [Gmail的提示和已知限制](https://developers.google.com/gmail/ampemail/tips) 和 [Outlook的AMP最佳实践](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices).

## 定位AMP电子邮件 {#targeting-amp-email}

目前，您可以尝试通过两个步骤发送AMP电子邮件：

1. Adobe Campaign允许您测试向已正确配置的选定电子邮件地址发送AMP支持的动态电子邮件，以验证其内容和行为。 请参阅 [测试选定地址的AMP电子邮件投放](#testing-amp-delivery-for-selected-addresses).

1. 测试后，您可以向相关电子邮件提供商注册，将发件人域名添加到，以便在AMP for Email计划中发送投放或营销活动，作为该计划的一部允许列表分。 请参阅 [通过向电子邮件提供商注册来发送AMP电子邮件](#delivering-amp-emails-by-registering).

### 测试选定地址的AMP电子邮件投放 {#testing-amp-delivery-for-selected-addresses}

您可以测试将动态消息从Adobe Campaign发送到选定的电子邮件地址。

>[!NOTE]
>
>目前只支持测试AMP格式的Gmail、Outlook和Mail.ru。

对于Gmail和Outlook，您必须首先将您使用的发件人地址添加到从允许列表Adobe Campaign为您定位的Gmail和Outlook帐户发送的邮件中。

操作步骤：
1. 确保为相关电子邮件提供商勾选了启用动态电子邮件的选项。
1. 复制投放中显示的发件人地址 **[!UICONTROL From]** 字段，并将其粘贴到电子邮件提供商帐户设置的相应部分中。

有关更多详细信息，请查阅 [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) 和 [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) 开发人员文档。

![](assets/amp_from_field.png)

要测试向Mail.ru地址发送AMP电子邮件，请按照 [Mail.ru开发人员文档](https://postmaster.mail.ru/amp/?lang=en#howto) (**如果您是用户** )。

### 通过向电子邮件提供商注册来发送AMP电子邮件 {#delivering-amp-emails-by-registering}

您可以尝试通过向受支持的电子邮件提供商注册来发送动态电子邮件，以便将您的发件人域名添加到允许列表。

>[!NOTE]
>
>目前，只有Gmail、Outlook和Mail.ru支持AMP格式。

使用几个地址进行测试后，您可以向任何Gmail或Outlook地址发送AMP电子邮件。 为此，您必须向Google或Microsoft注册，并等待他们的回答。 按照 [Gmail](https://developers.google.com/gmail/ampemail/register) 和 [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) 开发人员文档。 成功注册后，您将成为授权发件人。

要向Mail.ru地址发送AMP电子邮件，请按照 [Mail.ru开发人员文档](https://postmaster.mail.ru/amp/?lang=en#howto) (**如果您是电子邮件发件人** )。

## 发送AMP电子邮件 {#sending-amp-email}

AMP内容和回退准备就绪后，如果您定义了兼容的目标，那么您便可以像往常一样发送电子邮件。

目前，在某些情况下，只有Gmail、Outlook和Mail.ru支持AMP格式。 您可以定位来自其他电子邮件提供商的地址，但他们将收到您电子邮件的HTML或纯文本版本。

>[!IMPORTANT]
>
>如果除AMP内容外，您的电子邮件中不包含HTML或纯文本版本，则无法发送该版本。

匹配的收件人的邮箱中将显示电子邮件的AMP版本。

例如，如果您在电子邮件中包含产品列表，则在第三方系统中编辑价格时，每次收件人在其邮箱中再次打开电子邮件时，价格都会自动调整。

>[!NOTE]
>
>您可以创建邮件处理规则，以阻止特定域接收AMP电子邮件。 请参阅 [管理电子邮件格式](../../installation/using/email-deliverability.md#managing-email-formats).
>
>默认情况下， **[!UICONTROL AMP inclusion]** 选项设置为 **[!UICONTROL No]**.

## 教程视频 {#amp-email-video}

以下视频介绍如何在 Adobe Campaign 中激活 AMP 并展示其用法。

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

还提供其他Campaign操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
