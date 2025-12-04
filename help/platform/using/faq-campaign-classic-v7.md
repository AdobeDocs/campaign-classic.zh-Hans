---
product: campaign
title: Campaign Classic 常见问题解答
description: 特定于Adobe Campaign Classic v7架构、部署和功能的问题
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 295e3596d9291cbcc55e2d264309141526c3806b
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 2%

---

# Campaign Classic v7常见问题解答 {#campaign-classic-v7-faq}

此常见问题解答解答解答了特定于Adobe Campaign Classic v7体系结构、部署模型和特定于v7的功能的问题。

**有关常见的Campaign问题**（工作流、投放、受众、报表、个性化等）的完整答案，请参阅&#x200B;[**Campaign v8全面常见问题解答**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}，其中提供了按主题组织的详细答案。

## Campaign Classic v7架构和部署 {#v7-architecture}

### Campaign Classic v7中有哪些托管模型可用？ {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7提供三种部署模型：

* **托管(Managed Services)** — 由Adobe基础架构上的Adobe完全管理
* **内部部署** — 已在您自己的基础架构上安装并管理
* **混合** — 混合了云和内部部署组件的中间源架构

每个部署模型具有不同的能力和管理责任。 模块、选项和配置的可用性取决于您的部署类型。

[单击此处了解有关](../../installation/using/hosting-models.md)托管模型及其差异的更多信息。

**注意：** Campaign v8仅作为托管云服务提供。 [了解Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html?lang=zh-Hans){target="_blank"}。

### 在内部部署环境与托管环境中工作有何不同？ {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7提供了一组模块和选项。 这些模块及其配置的可用性取决于安装的[部署类型](../../installation/using/hosting-models.md)：托管(Managed Services)、混合或内部部署。

主要区别：

* **内部部署** — 完全控制安装、基础架构和配置。 需要内部IT资源来维护、升级和安全。
* **托管/Managed Services** — 由Adobe管理的基础结构和维护。 自动升级和增强安全性。 有限的直接服务器访问。
* **混合** — 兼具两个模型的优点。 由Adobe托管的营销实例，单独管理执行/中间源。

[单击此处获取完整功能矩阵](../../installation/using/capability-matrix.md)。

### 如何从内部部署/混合部署迁移到Adobe Managed Services？ {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

迁移到Adobe Managed Services可提高可扩展性和安全性，并减少IT开销。 在过渡到Campaign v8之前，这通常是垫脚石。

**关键点：**

* 没有可用的自动迁移工具 — 需要手动规划和执行
* 强烈建议支持Adobe Professional Services
* 其优势包括云基础架构、自动安全修补程序、专家支持和更轻松的v8途径
* 迁移包括尽职调查、环境审核、数据清理、暂存迁移和生产切换

**快速入门：**&#x200B;请联系您的Adobe代表以评估您的环境，并使用Adobe Professional Services制定详细的迁移计划。

了解有关[迁移到Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}的更多信息。

## 内部版本升级(Campaign Classic v7) {#build-upgrades-v7}

### Campaign Classic v7中的内部版本升级是什么？ {#what-is-a-build-upgrade-v7}

内部版本升级是指将Adobe Campaign Classic v7软件更新到最新的安全内部版本号，但仍保留相同的主/次内部版本级别。 例如：Campaign Classic v7内部版本9026到Campaign v7内部版本9032。

Adobe Campaign 会定期更新。发布了包含新增功能、改进和修复的次要版本。 此外，定期发布仅包含累积修复的版本。

在本节[中了解更多](../../rn/using/rn-overview.md)。

### 如何将Campaign Classic v7升级到最新版本？ {#how-can-i-upgrade-campaign-classic-v7}

Adobe Campaign Classic使用一系列技术来创造价值。 这一技术组合要求您定期升级Campaign Classic v7实例，以确保使用最新版本提供出众的安全性、稳定性和性能。

**对于托管客户：**&#x200B;您可以使用最新稳定版本自动从Campaign年度升级中受益。 Adobe管理升级过程并与您协调时间。

**对于内部部署/混合部署客户：**&#x200B;您负责执行升级。 Adobe强烈建议每年至少升级一次。

[阅读此部分](../../production/using/build-upgrade.md)以了解如何更新环境，并阅读[内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md)以了解有关此特定主题的详细问题。

### Adobe Campaign Classic v7的最新版本是什么？ {#what-is-the-latest-version-v7}

最新[发行说明](../../rn/using/latest-release.md)中详细介绍了最新的Campaign Classic v7版本，包括新增功能和文档。

### 如何知道我运行的是哪个Campaign Classic v7版本？ {#how-do-i-know-which-version-v7}

从Adobe Campaign客户端控制台的&#x200B;**[!UICONTROL Help > About...]**&#x200B;菜单中检查您的版本号和内部版本号。 **[!UICONTROL About]**&#x200B;框包含有关控制台和服务器正在运行的版本和内部版本的详细信息。

在本节[中了解更多](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

### 内部版本升级与版本升级是否相同？ {#is-build-upgrade-same-as-version-upgrade}

没有。内部版本升级是给定主版本中的增量更新，而版本升级是从一个主版本到另一个主版本的更改。 构建升级非常简单，通常不涉及重大的体系结构、技术或数据模型更改。

版本升级（例如，v7到v8）通常伴随重大技术更改，根据您的自定义设置，可能需要配置更改或部分重新实施。

## Campaign Classic v7配置 {#v7-configuration}

### 我可以更改Campaign Classic v7界面的语言吗？ {#can-i-change-language-v7}

创建实例时可选择Campaign Classic v7语言。 **以后不能更改它。**

Adobe Campaign v7用户界面提供4种语言版本：英语、法语、德语和日语。 客户端控制台和服务器必须使用相同的语言设置。 每个Campaign Classic v7实例只能以一种语言运行。

如果是英语，在安装Campaign v7时，您可以选择美式英语还是英式英语：二者的日期和时间格式有所不同。

[在此章节中了解详情](../../installation/using/creating-an-instance-and-logging-on.md)。

**注意：** Campaign v8 Web UI允许用户单独更改其界面语言。 [了解详情](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}。

### 如何在Campaign Classic v7中配置安全区域？ {#how-can-i-configure-security-zones-v7}

Security Zones自助服务界面可用于管理Adobe Campaign Classic v7部署的VPN Security Zone配置中的条目。 这主要与内部部署和混合部署相关。

阅读[本节](../../installation/using/security-zones.md)以了解Campaign v7中的安全区域。

[单击此处了解有关Security Zone自助服务UI的更多信息](https://helpx.adobe.com/cn/campaign/kb/configuring-security-zones-self-service.html){target="_blank"}。

**注意：**&#x200B;托管/Managed Services客户应联系Adobe以配置安全区域。

### Adobe Campaign Classic v7能否与LDAP集成？ {#can-campaign-classic-integrate-with-ldap}

是的。 作为&#x200B;**内部部署/混合部署客户**，您可以将Campaign Classic v7与LDAP目录集成，以实现集中身份验证和用户管理。

此集成允许：

* 用于针对您的公司LDAP目录进行身份验证的用户
* 集中化的用户和权限管理
* 自动同步用户组和权限
* 单点登录功能

[单击此处了解如何](../../installation/using/connecting-through-ldap.md)在Campaign Classic v7中设置LDAP集成。

**注意：** LDAP集成可用于内部部署和混合部署。 托管客户使用Adobe IMS进行身份验证。

### 内部部署的安全最佳实践是什么？ {#security-best-practices-on-premise}

与托管环境相比，内部部署和混合部署需要额外的安全配置和强化。

**关键安全区域：**

* 网络安全和防火墙配置
* 数据库访问和安全性
* 操作系统强化
* 文件权限和访问控制
* 安全区域配置
* 加密（静态和传输中的数据）
* 用户访问管理
* 定期安全修补
* 审核日志记录和监控

阅读[安全配置检查清单](https://helpx.adobe.com/cn/campaign/kb/acc-security.html){target="_blank"}以发现有关检查安全配置和强化内部部署的关键元素。

### 如何清除客户端控制台缓存？ {#how-do-i-clear-console-cache}

清除Campaign客户端控制台缓存解决了许多常见的显示和功能问题。 缓存存储有时可能会损坏或过时的本地配置文件。

**何时清除缓存：**

* 新品牌元素显示不正确
* 导出/导入函数意外失败
* 配置更改后未更新界面元素
* 性能问题或控制台响应缓慢
* 升级到新客户端控制台版本后

**如何清除缓存：**

1. **软缓存已清除（请先尝试）：**
   * 打开Campaign客户端控制台
   * 转到&#x200B;**[!UICONTROL File]**&#x200B;菜单
   * 选择&#x200B;**[!UICONTROL Clear the local cache...]**
   * 出现提示时确认操作
   * 重新启动客户端控制台

2. **硬缓存清除（如果软清除不能解决此问题）：**
   * 首先执行软缓存清除
   * 注销并完全关闭客户端控制台
   * 导航到：
      * Windows 7/10： `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP： `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * 删除所有名为`nlclient-config-<alphanumerical value>.xml`的XML文件和关联的文件夹
   * **重要信息：**&#x200B;不删除`nlclient_cnx.xml`文件
   * 重新启动客户端控制台

请参阅[Campaign客户端控制台文档](../../platform/using/launching-adobe-campaign.md)以了解详情。

## 获取帮助 {#getting-help}

### 在哪里可以找到有关Campaign Classic v7的更多信息？ {#where-to-find-more-info-v7}

**文档和资源：**

* [Campaign Classic v7文档](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=zh-Hans){target="_blank"} — 完整文档
* [Campaign Classic v7发行说明](../../rn/using/latest-release.md) — 最新发行信息
* [Campaign Classic兼容性矩阵](../../rn/using/compatibility-matrix.md) — 支持的系统和版本
* [Campaign Classic教程](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans){target="_blank"} — 视频教程

有关Campaign的常见问题：**&#x200B;**

请参阅&#x200B;[**Campaign v8综合常见问题解答**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}，其中提供了有关以下内容的详细答案：

* Campaign快速入门
* 轮廓和受众
* 邮件设计和投放
* 工作流和自动化
* 报告和分析
* Campaign设置和配置
* 开发人员资源
* 隐私和合规性

**社区和支持：**

* [Campaign社区论坛](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}
* [Adobe支持](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [控制面板（托管客户）](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans){target="_blank"}

### 我应该从Campaign Classic v7迁移到Campaign v8吗？ {#should-i-migrate-to-v8}

Campaign v8是Adobe的战略平台，非常适合需要大量促销活动、现代Web UI、云原生优势以及长期支持的组织。 Campaign Classic v7将在未来几年停止支持。

**如果您：**，请考虑迁移到Campaign v8

* 处理大量数据或遇到性能问题
* 希望减少IT开销和基础架构管理（v8仅用于托管式云服务）
* 需要现代化的UI和Adobe Experience Platform集成
* 希望采用具有自动更新的未来防护技术
* 当前位于托管/托管服务上（更简单的迁移路径）

**重要注意事项：**

* Campaign v8专门作为托管云服务提供（无内部部署/混合选项）
* 需要规划自定义项和集成的迁移
* FFDA架构带来了性能，但需要一些工作流/API调整

**后续步骤：**&#x200B;请联系您的Adobe代表以评估迁移准备情况并访问迁移工具。

了解详情：

* [Campaign v8概述](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html?lang=zh-Hans){target="_blank"}
* [从Campaign Classic v7过渡到v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [Campaign v8综合常见问题解答](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}

**有关工作流、投放、受众、报表、个性化等常见营销活动问题的详细答案**，请访问[Campaign v8全面常见问题解答](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}。
