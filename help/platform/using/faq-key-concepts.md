---
title: 重要概念
seo-title: 活动功能常见问题解答
description: Campaign Classic常见问题解答
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 72%

---


# 重要概念 {#key-concepts}

了解开始使用 Adobe Campaign 的关键步骤。

## Can I connect to Campaign Classic with an Adobe ID? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

通过与 IMS（Adobe 身份管理系统）相集成，用户可以使用其 Adobe ID 连接到 Adobe Campaign 控制台。该集成具有以下优势︰

* 所有 Experience Cloud 解决方案都可以使用相同的 ID。
* 使用具有不同集成的 Adobe Campaign 时，可以记住该连接。
* 密码管理策略更安全。
* 使用联合 ID 帐户（外部 ID 提供商）。

[单击此处了解有关](../../integrations/using/about-adobe-id.md)使用 Adobe ID 访问 Campaign Classic 的更多信息。

## What is my version of Campaign? {#what-is-my-version-of-campaign-}

可通过 Campaign 客户端控制台的 **Help > About...** 菜单查看您的[版本号和构建号](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

## What are the differences when working on-premise vs. in a hosted environment? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic 随附了一组模块和选项。这些模块及其配置是否可用取决于您的安装[部署类型](../../installation/using/hosting-models.md)：托管（受管理的服务）还是内部部署。

[单击此处了解更多信息](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)。

## 如何设置用户权限? {#how-can-i-set-up-user-permissions-}

作为 Campaign 管理员，您可以为组织的用户设置权限。

这些权限是一组权利或限制，可授予或拒绝用户执行以下操作：

* 访问特定功能，
* 访问特定数据，
* 创建、修改和/或删除数据。

[单击此处了解有关](../../platform/using/access-management.md)用户权限的更多信息。

## 如何确保隐私符合活动? {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign优惠一组工具，帮助您遵守GDPR和CCPA的隐私权。

请参阅[此文档](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html)，了解 Adobe Campaign 提供的工具、功能以及最佳实践，帮助您在使用我们的服务时遵循 GDPR 规定。本文介绍了Campaign Classic的实 [施步骤](https://helpx.adobe.com/campaign/kb/acc-privacy.html)。

## 我应该了解哪些 Campaign 用户界面概念? {#what-are-campaign-user-interface-concepts-i-should-know-}

请参阅[此部分](../../platform/using/adobe-campaign-workspace.md)，了解有关 Adobe Campaign 工作区基本知识的更多信息。您也可以观看[此视频](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/interface-overview.html)。

## How can I select the audience of my messages? {#how-can-i-select-the-target-population-of-my-messages-}

凭借 Adobe Campaign，您可以使用不同策略来创建受众，并选择目标收件人。

[单击此处了解更多信息](../../delivery/using/steps-defining-the-target-population.md)。

## What is a workflow? {#what-is-a-workflow-}

Adobe Campaign 包括在不同的应用程序服务器模块之间编排所有流程和任务的工作流。您可以利用这个全面的图形环境设计各式流程，包括部分划分、活动执行、文件处理、人员参与等。工作流引擎会执行并跟踪这些流程。

例如，您可以使用某个工作流从服务器下载文件、解压缩，然后将其中包含的记录导入 Adobe Campaign 数据库。

此外，一个工作流也可能涉及到要通知一个或多个操作员，或者是可以作出决策和批准流程的相关人员。这样就可以创建一次投放行动，将内容相关任务指派给一位或多位操作员，指定目标并在开始投放前获得批准。

[单击此处了解有关](../../workflow/using/about-workflows.md)工作流的更多信息。您也可以阅读[工作流最佳实践](../../workflow/using/building-a-workflow.md)。

## How to create and send a first email? {#how-to-create-and-send-a-first-email-}

[单击此处了解更多](../../delivery/using/about-email-channel.md)或[观看此视频](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-campaign-and-an-email.html)，在营销活动中创建电子邮件。

## How to send SMS messages? {#how-to-send-sms-messages-}

在[此部分](../../delivery/using/sms-channel.md)中了解如何配置您的平台以及发送 SMS 消息。

## How to send push notifications? {#how-to-send-push-notifications-}

了解如何使用 Adobe Campaign 通过应用程序向 iOS 和 Android 设备[发送个性化的推送通知](../../delivery/using/creating-notifications.md)。

## How to design and share an online survey? {#how-to-design-and-share-an-online-survey-}

了解如何[创建在线调查](../../web/using/getting-started-with-surveys.md)，包括使用 Campaign Classic 设计和发布调查的关键步骤。

## How to create landing page? {#how-to-create-landing-page-}

您可以使用 Adobe Campaign 数字内容编辑器来设计登陆页，并定义与数据库字段的映射关系。

[单击此处了解更多信息](../../web/using/creating-a-landing-page.md)。

## How can I track deliveries? {#how-can-i-track-deliveries-}

在 Campaign Classic 中您可通过专用的[投放报告](../../reporting/using/delivery-reports.md)跟踪并监视您发送的投放内容。

在本页了解有关活动中跟踪管 [理的更多信息](https://helpx.adobe.com/campaign/kb/acc-tracking.html)。

## What are security best practices (on-premise)? {#what-are-security-best-practices--on-premise--}

阅读[安全配置检查列表](https://helpx.adobe.com/campaign/kb/acc-security.html)，探索有关检查安全配置和强化内部部署的核心元素。

## How to translate an error message? {#how-to-translate-an-error-message-}

错误消息是用外文显示的？[此页面](https://docs.adobe.com/content/help/zh-Hans/campaign-classic/technicalresources/error_messages/error_codes.html)中列出了所有错误消息及其译文。

## Can I create a webform and collect answers in Campaign? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

了解如何 [创建Web表单](../../web/using/about-web-forms.md):设计、测试、发布Web表单并收集答案。

## Is there a list of deprecated features and versions? {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe 会持续评估产品功能，不断使用更强大的版本替换旧功能，也可能决定重新推出部分组件，更好地满足未来的期望或扩展要求。由于 Campaign 可与第三方工具配合使用，所以会定期更新产品兼容性，以仅实施所支持的版本。

[单击此处了解更多信息](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)。

## Are there new documentation updates and help materials released? {#are-there-new-documentation-updates-and-help-materials-released-}

[此页面](https://docs.adobe.com/content/help/en/campaign-classic/using/documentation-updates.html)中列出了最新的 Campaign Classic 文档更新。

您也可以参照[此页面](https://helpx.adobe.com/campaign/kb/article-list.html)中列出的最新的技术说明。
