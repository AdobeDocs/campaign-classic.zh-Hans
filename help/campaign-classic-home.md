---
keywords: Campaign Classic;home;popular topics
product: campaign
title: Adobe Campaign Classic v7 产品文档
exl-id: 6b3f1689-80de-49fd-b7ee-7a2a1931d157
TQID: 'https://experienceleague.adobe.com/Q6Oc24mo-1qDAxCWu2lGT4UvRLXB78Tr5X4sb2kHFw8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: 186021e65b592522f3c491fb518594b5bac5d003
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 40%
---
# Campaign Classic v7 文档 {#campaign-classic-documentation}

本文档介绍了适用于&#x200B;**内部部署和混合**&#x200B;部署的Campaign Classic v7：安装、配置、升级、操作以及特定于v7的功能。 如果您的实例由Adobe （托管云服务）托管，请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/campaign-home){target="_blank"}。 此处不再重复以相同方式使用Campaign v8文档的内容：请参阅[从v7到v8](#from-v7-to-v8)。

<!--![](platform/using/assets/do-not-localize/banner_acc_doc.jpg) -->

## 新增功能

概要了解 Adobe Campaign Classic v7 产品和文档中的最新增强功能！ 有关功能、改进和修复的完整列表，请查看详细的[发行说明](rn/using/latest-release.md)。

>[!BEGINTABS]


>[!TAB 2026年10月版本已上线！]

Campaign Classic v7.4.5 - 2026年10月版（内部版本9420）修复了Analytics外部帐户、停滞在个性化待定状态的投放、服务器CPU使用、间歇性数据模型更新失败、投放创建中的垃圾邮件检查错误以及定期软退回的隔离。

[![image](assets/do-not-localize/learn-more-button.svg)](rn/using/latest-release.md)

>[!TAB 迁移到 Adobe IMS]

为了加强安全和身份验证过程，Adobe Campaign 强烈建议将终端用户身份验证模式从登录/密码本机身份验证迁移到 Adobe Identity Management System (IMS)。

[![图像](assets/do-not-localize/learn-more-button.svg)](technotes/using/ac-ims.md)


>[!ENDTABS]

## 从基础知识开始

<table style="table-layout:fixed">
  <tr style="border: 0;">
    <td>
    <a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/start-launch.png"></a></a>
    <div><strong>启动 Adobe Campaign</strong><br/>了解如何启动 Campaign 客户端控制台并连接到 Campaign 应用程序服务器。</div>
    </td>
    <td>
    <a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/start-profiles.png"></a>
    <div><strong>添加和管理轮廓</strong><br/>探索如何轻松地在 Adobe Campaign v7 数据库中进行轮廓管理。 手动或通过导入添加轮廓，轻松优化客户数据和自定义营销活动。</div>
    </td>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/start-workflows.jpeg"></a>
    <div><strong>使用工作流实现自动化</strong><br/>了解如何利用工作流设计流程，包括分段、活动执行、文件处理、人员参与等。
    </div></td>
    <td>
    <a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/start-deliveries.jpeg"></a>
    <div><strong>创建投放</strong><br/>了解如何跨各种渠道（如电子邮件、短信、推送通知等）发送消息。</div>
    </td>
  </tr>
  <tr style="border: 0;">
    <td align="center"><a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    </tr>
</table>

## 浏览文档

<table style="table-layout:auto">
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon-configure.svg" width="35px">
      <br/>
      <strong>管理员</strong><br/><a href="production/using/general-architecture.md">架构原则</a> - <a href="production/using/configuration.md">配置Campaign</a> - <a href="platform/using/launching-adobe-campaign.md">连接到Campaign</a> - <a href="installation/using/external-accounts.md">连接到外部系统</a> - <a href="platform/using/access-management.md">权限</a> - <a href="platform/using/privacy-management.md">隐私和同意</a> - <a href="production/using/build-upgrade.md">执行内部版本升级</a> - <a href="delivery/using/about-deliverability.md">可投放性</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-send.svg" width="35px">
      <br/>
      <strong>营销人员</strong><br/><a href="https://experienceleague.adobe.com/zh-Hans/docs/campaign/campaign-v8/new/campaign-ui" target="_blank">用户界面</a> （Campaign v8文档） - <a href="https://experienceleague.adobe.com/zh-Hans/docs/campaign/campaign-v8/data/import" target="_blank">导入和导出数据</a> （Campaign v8文档） - <a href="https://experienceleague.adobe.com/zh-Hans/docs/campaign/campaign-v8/audience/create-audiences/create-audiences" target="_blank">创建列表</a> （Campaign v8文档） - <a href="delivery/using/about-services-and-subscriptions.md">服务和订阅</a> - <a href="delivery/using/communication-channels.md">通信渠道</a> - <a href="delivery/using/about-personalization.md">Personalization</a> - <a href="https://experienceleague.adobe.com/zh-Hans/docs/campaign/campaign-v8/send/create-message" target="_blank">发送校样</a> （Campaign v8文档） - <a href="delivery/using/get-started-a-b-testing.md">A/B测试</a> - <a href="message-center/using/about-transactional-messaging.md">事务性消息传递</a> - <a href="interaction/using/interaction-and-offer-management.md">交互和优惠管理</a> - <a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank">使用工作流实现自动化</a>（Campaign v8文档） - <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=zh-Hans" target="_blank">营销活动</a> - <a href="https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/analytics/tracking/tracking" target="_blank">消息跟踪</a>（Campaign v8文档） - <a href="https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/analytics/reports/gs-reporting" target="_blank">报表</a>（Campaign v8文档）
    </td>
    <td>
      <img src="assets/do-not-localize/icon-dev.svg" width="35px">
      <br/>
      <strong>开发人员</strong><br/><a href="https://experienceleague.adobe.com/zh-Hans/docs/campaign/campaign-v8/developer/datamodel" target="_blank">数据模型描述</a>（Campaign v8文档） - <a href="configuration/using/about-schema-reference.md">架构结构</a> - <a href="configuration/using/editing-forms.md">输入表单</a> - <a href="configuration/using/about-web-services.md">API</a> - <a href="https://experienceleague.adobe.com/zh-hans/tools/campaign-api" target="_blank">JSAPI参考文档</a> - <a href="configuration/using/about-custom-recipient-table.md">自定义收件人表</a>
    </td>
  </tr>
</table>

## 从v7到v8 {#from-v7-to-v8}

Campaign v8文档中记录的内容已从v7文档中删除。 使用此表查找它。

| 如果您正在查找…… | 转到Campaign v8文档 |
| --- | --- |
| 用户界面 | [发现用户界面](https://experienceleague.adobe.com/zh-Hans/docs/campaign/campaign-v8/new/campaign-ui){target="_blank"} |
| 用户档案、列表、导入和导出 | [导入用户档案和数据](https://experienceleague.adobe.com/zh-Hans/docs/campaign/campaign-v8/data/import){target="_blank"} |
| 工作流 | [关于工作流](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows){target="_blank"} |
| 营销活动 | [开始使用营销活动](https://experienceleague.adobe.com/en/docs/campaign/automation/campaign-orchestration/set-up-campaigns){target="_blank"} |
| 创建和发送投放 | [创建消息](https://experienceleague.adobe.com/zh-Hans/docs/campaign/campaign-v8/send/create-message){target="_blank"} |
| 内置报告 | [开始使用报告](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/analytics/reports/gs-reporting){target="_blank"} |
| 权限 | [开始使用权限](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"} |
| 输入表单 | [开始使用输入表单](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms){target="_blank"} |

## 其他资源

[Adobe Campaign 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"} - [兼容性矩阵](rn/using/compatibility-matrix.md) - [教程](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans){target="_blank"} - [Campaign 控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hans){target="_blank"} - [电子邮件跟踪像素和 CNIL 指南](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/new/cnil-pixel-tracking){target="_blank"}
