---
product: campaign
title: 迁移到Adobe Analytics Connector
description: Campaign - Analytics连接器常见问题解答
hide: true
hidefromtoc: true
source-git-commit: 248bd7774c01adb44ce33d0499c2b01d013e75bd
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 6%

---

# 如何迁移到Adobe Analytics Connector {#acc-aa-faq}

从Campaign Classicv7 21.1.3版本开始，弃用Adobe Analytics Data Connector。 [了解详情](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

2021年8月1日，Adobe Campaign Classic将从旧版Data Connectors UI中删除，但是，现有的Campaign集成将继续收集数据并将数据传递到Adobe Analytics，直到2022年3月1日为止。 2022年3月1日，集成将停止收集数据并将数据传递到Adobe Analytics。

您必须迁移到AdobeExchange上的新Adobe Analytics Connector集成，该集成将取代旧版Data Connectors集成，如[此页面](../platform/using/adobe-analytics-connector.md)中所述。


>[!NOTE]
>
>有关这些更改的任何问题，请联系 [Adobe 客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。


## 更改了哪些内容？

Campaign Classic与Adobe Analytics之间的新集成现已可用。 下面列出了主要更改。

* Adobe Campaign Classic与Adobe Analytics身份验证之间的集成已从用户/密码移至AdobeIdentity Management服务(IMS)。 因此，您必须实施AdobeIMS，并通过Adobe ID](../integrations/using/about-adobe-id.md)连接到Campaign [，然后才能开始实施Analytics连接器。

* **联系日期**&#x200B;分类（使用的类型为日期）已被Adobe Analytics弃用。 对于迁移的集成，它仍将保持相同类型。 对于Campaign创建的任何&#x200B;**联系日期**，类型将为&#x200B;**String**。

* **处理** 规则由Adobe Campaign作为新集成的一部分创建。应从Adobe Analytics手动创建&#x200B;**处理规则**，或直接使用客户端Javascript实施。 **处理** 规则将保持现有集成的原样。

* 内置的技术工作流及其行为保持不变。 只有工作流用于向Adobe Analytics推送数据/从API的后端API已更改。

* 请注意，`nlserver`进程应使用IMS技术帐户用户进行配置，以便新连接器正常工作。 此更改必须通过Adobe完成。 要实施此功能，请联系[Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

* 如果您是自定义工作流中用于从Adobe Analytics提取和推送数据的Adobe Genesis API，则现在需要使用新的Adobe Analytics 1.4/2.0 API。 [了解详情](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## 您是否受影响？

如果您使用现有的Adobe Analytics Data Connector(以前称为Genesis集成)，并且该集成的内部版本低于Campaign 21.1.3，则您会受到影响。

在此部分](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的版本[。

## 如何更新？

您需要在2022年3月1日之前升级到Campaign 21.1.3（或更高版本）****。

作为托管客户，Adobe将与您合作，将您的实例升级到较新版本。

作为内部部署/混合客户，您需要升级到某个较新版本，以便从新集成中受益。

升级所有实例后，您将能够[实施到Adobe Analytics Connector的新集成](../platform/using/adobe-analytics-connector.md)，并确保无缝过渡。


## 常见问题解答

**如何获取日志？**

用户界面配置和工作流都配备了&#x200B;**verbose**&#x200B;日志记录。

在详细模式下，还会为每个对Adobe Analytics的API请求打印请求和响应标头。

作为内部部署用户，您可以按如下方式实施详细模式：

* 要为用户界面启用详细模式，请执行以下操作：以详细模式重新运行`web`进程。
* 要为&#x200B;**webAnalytics**&#x200B;工作流启用详细模式，请执行以下操作：从工作流属性中选择&#x200B;**在引擎中执行**&#x200B;选项，然后在详细模式下重新运行`wfserver`。

**集成所有者不是管理员**

详细了解[此页面](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error)中的Data Connectors“集成所有者不是管理员”错误。

**分析中存在的现有evar/事件/报表包在Campaign中不可见**

集成依赖于技术帐户令牌中的日常操作数据。 如果与技术帐户用户关联的产品配置文件中缺少对维度/量度/报表包的权限，则我们使用的API在这些请求中将会闪烁。

如果我们正在阅读Analytics组件（如量度/维度/区段/报表包）的详细信息，则API将不会在结果中返回这些组件（这可能看起来类似于在Analytics端删除的内容或不存在）。 Analytics API将拒绝这些请求并发出错误。

解决方案是，通过在[Adobe Admin Console](https://adminconsole.adobe.com/)中添加新创建/缺失的组件，使用技术用户令牌的Analytics用户上下文中的产品配置文件更新这些组件。

## 有用链接

* [升级环境](../production/using/build-upgrade.md)
* [内部版本升级常见问题解答](../platform/using/faq-build-upgrade.md)
* [下载Campaign Classic内部版本](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [使新客户端控制台可供用户使用](../installation/using/client-console-availability-for-windows.md)
* [安装 Campaign Client Console](../installation/using/installing-the-client-console.md)