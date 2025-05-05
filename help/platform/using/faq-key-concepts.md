---
product: campaign
title: 重要概念
description: Campaign Classic 常见问题解答
feature: Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f0d884ae-0789-4ad9-a8fa-adeffbb560ea
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 96%

---

# 重要概念 {#key-concepts}



了解开始使用 Adobe Campaign 的关键步骤。

## 我可以使用 Adobe ID 连接到 Campaign Classic 吗？ {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

通过与 IMS（Adobe 身份管理系统）相集成，用户可以使用其 Adobe ID 连接到 Adobe Campaign 控制台。该集成具有以下优势︰

* 所有 Experience Cloud 解决方案都可以使用相同的 ID。
* 使用具有不同集成的 Adobe Campaign 时，可以记住该连接。
* 密码管理策略更安全。
* 使用联合 ID 帐户（外部 ID 提供商）。

[单击此处了解有关](../../integrations/using/about-adobe-id.md)使用 Adobe ID 访问 Campaign Classic 的更多信息。

## 我的 Campaign 是什么版本？ {#what-is-my-version-of-campaign-}

可通过 Campaign 客户端控制台的 **Help > About...** 菜单查看您的[版本号和构建号](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

## 在内部部署环境与托管环境中工作有何不同？ {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic 随附了一组模块和选项。这些模块及其配置的可用性可能取决于安装的[部署类型](../../installation/using/hosting-models.md)：托管（托管服务）、混合或本地。

[单击此处以了解详情](../../installation/using/capability-matrix.md)。

## 如何设置用户权限? {#how-can-i-set-up-user-permissions-}

作为 Campaign 管理员，您可以为组织的用户设置权限。

这些权限是一组权利或限制，可授权或拒绝用户执行以下操作：

* 访问特定功能，
* 访问特定数据，
* 创建、修改和/或删除数据。

[单击此处了解有关](../../platform/using/access-management.md)用户权限的更多信息。

## 如何确保Campaign的隐私合规性？ {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign 提供一套工具，可帮助您确保符合《欧盟通用数据保护条例》(GDPR) 和《加州消费者隐私法案》(CCPA) 的隐私政策。

请参阅[此文档](privacy-and-recommendations.md)，了解 Adobe Campaign 提供的工具、功能以及最佳实践，帮助您在使用我们的服务时遵循 GDPR 规定。[本文](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)介绍了 Campaign Classic 的实施步骤。

## 我应该了解哪些 Campaign 用户界面概念? {#what-are-campaign-user-interface-concepts-i-should-know-}

请参阅[此部分](../../platform/using/adobe-campaign-workspace.md)，了解有关 Adobe Campaign 工作区基本知识的更多信息。

![](assets/do-not-localize/how-to-video.png) [在视频中发现 Campaign 工作区](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/exploring-the-adobe-campaign-classic-user-interface.html?lang=zh-Hans)

## 如何选择消息的受众？ {#how-can-i-select-the-target-population-of-my-messages-}

凭借 Adobe Campaign，您可以使用不同策略来创建受众，并选择目标收件人。

[单击此处了解更多信息](../../delivery/using/steps-defining-the-target-population.md)。

## 什么是工作流？ {#what-is-a-workflow-}

Adobe Campaign 包括在不同的应用程序服务器模块之间编排所有流程和任务的工作流。您可以利用这个全面的图形环境设计各式流程，包括部分划分、活动执行、文件处理、人员参与等。工作流引擎会执行并跟踪这些流程。

例如，您可以使用某个工作流从服务器下载文件、解压缩，然后将其中包含的记录导入 Adobe Campaign 数据库。

此外，一个工作流也可能涉及到要通知一个或多个操作员，或者是可以作出决策和批准流程的相关人员。这样就可以创建一次投放行动，将内容相关任务指派给一位或多位操作员，指定目标并在开始投放前获得批准。

[单击此处了解有关](../../workflow/using/about-workflows.md)工作流的更多信息。您也可以阅读[工作流最佳实践](../../workflow/using/building-a-workflow.md)。

## 如何创建并发送第一封电子邮件？ {#how-to-create-and-send-a-first-email-}

[单击此处了解更多信息](../../delivery/using/about-email-channel.md)。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此内容](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/creating-a-campaign-and-an-email.html?lang=zh-Hans)

## 如何发送 SMS 消息？ {#how-to-send-sms-messages-}

在[此部分](../../delivery/using/sms-channel.md)中了解如何配置您的平台以及发送短信消息。

## 如何发送推送通知？ {#how-to-send-push-notifications-}

了解如何使用 Adobe Campaign 通过应用程序向 iOS 和 Android 设备[发送个性化的推送通知](../../delivery/using/create-notifications-ios.md)。

## 如何设计和分享在线调查？ {#how-to-design-and-share-an-online-survey-}

了解如何[创建在线调查](../../surveys/using/getting-started-with-surveys.md)，包括使用 Campaign Classic 设计和发布调查的关键步骤。

## 如何创建登陆页？ {#how-to-create-landing-page-}

您可以使用 Adobe Campaign 数字内容编辑器来设计登陆页，并定义与数据库字段的映射关系。

[单击此处了解更多信息](../../web/using/creating-a-landing-page.md)。

## 如何跟踪投放内容？ {#how-can-i-track-deliveries-}

在 Campaign Classic 中您可通过专用的[投放报告](../../reporting/using/delivery-reports.md)跟踪并监视您发送的投放内容。

在[本页](https://helpx.adobe.com/cn/campaign/kb/acc-tracking.html)了解有关 Campaign 中跟踪管理的更多信息。

## 什么是安全最佳实践（内部部署）？ {#what-are-security-best-practices--on-premise--}

阅读[安全配置检查列表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)，探索有关检查安全配置和强化内部部署的核心元素。

## 如何翻译错误消息？ {#how-to-translate-an-error-message-}

错误消息是用外文显示的？[此页面](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=zh-Hans)中列出了所有错误消息及其译文。

## 我能在 Campaign 中创建 Web 窗体并收集回答吗？ {#can-i-create-a-webform-and-collect-answers-in-campaign-}

了解如何 [创建 Web 窗体](../../web/using/about-web-forms.md)：设计、测试、发布 Web 窗体并收集答案。

## 是否有已弃用功能和版本的列表？ {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe 会持续评估产品功能，不断使用更强大的版本替换旧功能，也可能决定重新推出部分组件，更好地满足未来的期望或扩展要求。由于 Campaign 可与第三方工具配合使用，所以会定期更新产品兼容性，以仅实施所支持的版本。

[单击此处了解更多信息](../../rn/using/deprecated-features.md)。

## 是否发布了新的文档更新和帮助材料？ {#are-there-new-documentation-updates-and-help-materials-released-}

[此页面](https://experienceleague.adobe.com/docs/campaign-classic/using/documentation-updates.html?lang=zh-Hans)中列出了最新的 Campaign Classic 文档更新。

您也可以参照[此页面](https://helpx.adobe.com/cn/campaign/kb/article-list.html)中列出的最新的技术说明。
