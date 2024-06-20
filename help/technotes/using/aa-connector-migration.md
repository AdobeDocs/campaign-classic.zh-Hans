---
product: campaign
title: 迁移到Adobe Analytics连接器
description: Campaign - Analytics连接器常见问题解答
feature: Technote, Analytics Integration
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于v7内部部署和混合部署"
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
hide: true
hidefromtoc: true
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# 如何将现有Genesis集成迁移到Adobe Analytics连接器 {#acc-aa-faq}

从Campaign Classicv7 21.1.3版本开始，弃用Adobe Analytics Data Connector。 [了解更多信息](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

2021年8月1日，Adobe Campaign Classic已从旧版Data Connectors UI中删除，但是，在2022年8月17日之前，现有Campaign集成将继续收集数据并传递到Adobe Analytics。 在此日期之后，集成将停止收集数据并传递到Adobe Analytics。

您 **必须实施** Adobe Exchange上新的Adobe Analytics Connector集成，它取代了旧版Data Connectors集成。 要了解有关Adobe Analytics Connector的更多信息，请参阅 [此页面](../../integrations/using/gs-aa.md).

有关这些更改的任何问题，请阅读 [常见问题解答](#faq-aa). 有关详细信息，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

>[!NOTE]
>
>如果您从现有的Adobe Analytics Data Connector(以前称为Genesis集成)迁移并使用Adobe Analytics中的新分类架构，则需要从7.3.1或8.4.1开始的内部版本才能迁移到新的Adobe Analytics Connector。

## 更改了哪些内容？

Campaign Classic v7与Adobe Analytics之间的新集成现已可用。 下面列出了主要更改。

* 此 **联系日期** 分类通常为日期类型，已被Adobe Analytics弃用。 对于已迁移的集成，它仍将保持相同类型。 对于任何 **联系日期** 由营销活动创建，类型将为 **字符串**.

* **处理规则** 由Adobe Campaign作为新集成的一部分创建。 或者 **处理规则** 应当从Adobe Analytics手动创建，或者直接使用客户端Javascript实施。 **处理规则** 对于现有集成，将保持不变。

* 内置的技术工作流及其行为保持不变。 只有工作流用于向/从Adobe Analytics推送/提取数据的后端API发生了更改。

* 请注意 `nlserver` 应使用IMS技术帐户用户配置进程，以使新连接器正常工作。 此更改必须由Adobe完成。 要实施此功能，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* 如果您在自定义工作流程中是Adobe Genesis API，用于从Adobe Analytics提取和推送数据，则现在需要使用新的Adobe Analytics 1.4/2.0 API。 [了解更多信息](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## 您是否受影响？

如果您使用现有的Adobe Analytics Data Connector(以前称为Genesis集成)，并且集成是在低于Campaign 21.1.3的内部版本上实现的，则您会受到影响。

了解如何检查您的版本 [在此部分中](../../integrations/using/launching-adobe-campaign.md#getting-your-campaign-version).

## 如何更新？

您需要升级到Campaign 21.1.3（或更高版本） **2022年8月17日之前**.

作为托管客户，Adobe将与您合作，将您的实例升级到新版本。 然后，您将能够使用 [Adobe Analytics连接器](../../platform/using/gs-aa.md).

作为内部部署/混合部署客户，您需要升级到较新版本之一以从新集成中受益。
升级所有实例后，您将能够 [实施新的集成](../../integrations/using/adobe-analytics-provisioning.md) 到Adobe Analytics连接器，并确保无缝过渡。

## 常见问题解答{#faq-aa}

**如何获取日志？**

用户界面配置和工作流配备 **冗长** 日志记录。

在详细模式下，还会为发送到Adobe Analytics的每个API请求打印请求和响应标头。

作为内部部署用户，您可以实施详细模式，如下所示：

* 要为用户界面启用详细模式：重新运行 `web` 详细模式下的进程。
* 要启用详细模式，请执行以下操作 **网站分析** 工作流：选择 **在引擎中执行** 选项，然后重新运行 `wfserver` 详细模式。

**“集成所有者不是管理员”错误意味着什么？**

了解有关Data Connectors的更多信息 `Integration Owner Not Admin` 中的错误 [此页面](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**迁移到新连接器后，旧数据和报表包会发生什么情况？**

迁移后，新连接器（从旧连接器迁移）将开始将数据推送到同一报表包，并且现有数据不会受到影响：它将添加到现有数据。

**Analytics中存在的一些现有evar/事件/报表包在Campaign中不可见。 我该怎么办？**

集成依赖于技术帐户令牌的数据才能进行日常操作。 如果与技术帐户用户关联的产品配置文件中缺少对维度/量度/报表包的权限，则我们使用的API将只会针对这些请求而失败。

如果我们正在阅读Analytics组件的详细信息（如量度/维度/区段/报表包），则API不会在结果中返回这些组件（这看起来可能像是某些内容在Analytics端被删除或不存在）。 Analytics API将拒绝这些请求并出错。

解决方案是更新 **产品配置文件** 在包含新创建/缺少的组件的技术用户令牌的Analytics用户上下文中，将这些组件添加到 [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}. 如需更多指导，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 有用的链接

* [升级环境](../../production/using/build-upgrade.md)
* [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md)
* [下载Campaign Classic版本](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)
* [使用户可以使用新的客户端控制台](../../installation/using/client-console-availability-for-windows.md)
* [安装 Campaign Client Console](../../installation/using/installing-the-client-console.md)
