---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 7f24c8be599d6dece41de848d64feb8079b10ff3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 最新版本{#latest-release}

![](../../assets/v7-only.svg)

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。每个新的内部版本都带有一个以颜色突出显示的状态。在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## ![](assets/do-not-localize/limited_2.png) 7.3.1 版 - 版本 9352 {#release-7-3-1}

_2022年7月1日_

**新增功能**

<table> 
<thead>
<tr> 
<th> <strong>时效性通知</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>在 iOS 15 中，Apple 新增了“即时通知”的概念，当通知具有时效性并且需要实时联系用户时，该概念让应用程序开发人员可以控制对“专注”模式的绕过。</p>
<p>了解如何在 <a href="../../delivery/using/create-notifications-ios.md">详细文档</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**兼容性更新**

* Adobe Campaign SDK现在支持Android 12和iOS 15进行推送通知。
* Adobe Campaign现在与MySQL 8兼容。
* Adobe Campaign 现在与 Windows 11 兼容。
* Adobe Campaign现在与Debian 11兼容。

请参阅 [Campaign 兼容性矩阵](../../rn/using/compatibility-matrix.md#OperatingSystems)。

**改进**

* 在Internet Explorer 11生命周期结束后，控制台中Adobe Services的HTML渲染引擎现在使用Edge Chromium。 此外，现在，任何客户端控制台安装(从Campaign Classic7.3内部版本开始)都需要安装Microsoft Edge Webview 2运行时。 [了解更多信息](../../installation/using/installing-the-client-console.md)
* Adobe Campaign中的数据库连接管理已得到改进，以优化稳定性。
* Campaign 现在支持适用于 POP3 的 Microsoft Exchange Online OAuth 2.0 身份验证。[了解更多信息](../../installation/using/external-accounts.md#bounce-mails-external-account)
* 修复了将扩充工作流活动与外部数据结合使用时的各种问题。 (NEO-38069)
* SAP Hana FDA连接器已更新，可与最新的SAP Hana数据库版本(2.x)一起正常运行。
* teradataFDA连接器已更新，可使用最新Teradata版本(17)正常运行。
* 20.2中，为新投放和投放模板引入了对iOS投放基于令牌的身份验证支持。 在7.2中，向升级后添加了一个修补程序，以将基于令牌的身份验证支持最多应用于10,000个之前创建的投放和投放模板。 在7.3中，修补程序已得到改进，并且限制已被删除。

**修补程序**

* 修复了上一个内部版本中的错误，该错误会阻止用户调整IMS登录页面的大小。
* 修复了在现有实例上安装内容管理器包时发生的错误。
* 修复了 **促销活动** 连续显示“操作正在进行”消息的菜单。
* 启用Adobe Analytics后，修复了在发送带有URL的电子邮件时，如果不保存投放，则会从URL中删除BID(Broadlog ID)和CID（促销活动ID）的问题。
* 修复了在具有消息中心特定配置的实例的公共资源文件夹中上传图像时的问题。 将显示以下错误消息：“无法将图像上传到跟踪服务器”。
* 修复了在配置文件不正确的情况下重新生成配置时导致系统崩溃的问题。
* 修复了可能导致投放指示器无法正确更新的问题。 (NEO-44827)
* 修复了在使用复杂查询时可能导致升级后错误的问题。 (NEO-43648)
* 修复了可能阻止webApps预览工作的问题。 (NEO-43242)
* 修复了在具有数据加载（文件）活动的工作流中使用外部目标映射文件时，可能导致投放准备失败的问题。 (NEO-43691)
* 修复了可能导致崩溃并需要完全重新启动实例的问题。 (NEO-44645)
* 修复了可能阻止工作流热图加载任何结果的问题。 (NEO-43360)
* 修复了使用FDA外部连接器时可能导致连接问题的问题。 (NEO-42722)
* 修复了使用地址替换和控制组排除时校样的问题。 (NEO-39695)
* 修复了由于Snowflake连接器问题而可能导致工作流失败的问题。 (NEO-46299)
* 修复了由于个性化块中的无效字符而可能冻结客户端控制台的问题。 (NEO-45761)
* 修复了在创建外部帐户以将Snowflake作为外部数据库时可能导致连接问题的问题。 (NEO-45744)
* 修复了可能导致显示受visibleIf属性保护的表信息的问题。 (NEO-37865)
* 修复了在投放分析阶段可能显示“$ is not defined”错误消息的问题。 (NEO-32940)
* 修复了导致投放与错误的eventType关联的问题。 (NEO-45743)
* 修复了由于间歇性核心转储而导致崩溃的问题(NEO-30549)
* 修复了在投放中使用错误HTML代码时可能导致崩溃的问题。 (NEO-40385)
* 修复了可能阻止非管理员用户访问 **分析** 选项卡。 (NEO-34025)

## ![](assets/do-not-localize/green_2.png) 7.2.2 版 - 版本 9349 {#release-7-2-2}

_2022 年 3 月 1 日_

>[!NOTE]
>
> 此内部版本与 v7.2.1 客户端控制台兼容。

**修补程序**

* 修复了在配置&#x200B;**网站分析**&#x200B;外部帐户时，导致即使发生错误，集成状态也始终显示为“Integration successful”的问题。(NEO-36672)
* 修复了当具有负 ID 时与序列 ID 机制相关的多个升级后错误。(NEO-43205、NEO-42846、NEO-42845)
* 修复了在使用具有循环和连续投放的&#x200B;**网站分析**&#x200B;外部帐户时导致外部帐户中的数据部分丢失的问题。(NEO-38548)
* 修复了更新 NmsActiveContact 表时升级后速度减慢的问题。(NEO-43206)
* 修复了将现成文件夹从&#x200B;**管理**&#x200B;节点移动到任何其他位置时出现的升级后故障问题。(NEO-42875)
* 修复了在使用&#x200B;**更新数据**&#x200B;工作流活动时，可能会导致无法使用 Google Cloud 外部数据库中的收件人数据更新收件人模式的问题。(NEO-42343)
* 修复了升级后与 Adobe Analytics 连接器相关的问题。(NEO-43318、NEO-38136)
* 修复了升级后 CUID 被“VALUE_TO_CHANGE”覆盖的问题。(NEO-43267)
* 修复了在多中间配置上同步中间源和营销实例时导致出现错误的问题。(NEO-10432)
* 修复了在同时拥有 1000 个以上 broadlog 时刷新可投放性工作流时导致出现错误的问题。(NEO-40276)
* 修复了导致打开率和点击率投放指标无法自动更新的问题。(NEO-43253)

## ![](assets/do-not-localize/limited_2.png) 7.2.1 版 - 版本 9346 {#release-7-2-1}

_2022 年 1 月 10 日_

**安全性增强**

FDA 帐户已进行多项安全性增强：

* 配置 FDA 外部帐户时，您现在可以使用密钥对身份验证登录到 Snowflake 帐户，以增强身份验证安全性。[了解更多信息](../../installation/using/configure-fda-snowflake.md)
* 在配置 FDA 外部帐户时，您现在可以使用系统分配的托管身份登录到 Azure Synapse Analytics 帐户。[了解更多信息](../../installation/using/configure-fda-synapse.md#azure-external)
* 已从 Campaign 中删除对 log4j 库的所有引用，以确保获得最佳安全性。

**兼容性更新**

Adobe Campaign 现在与 Windows Server 2019 兼容。请参阅 [Campaign 兼容性矩阵](../../rn/using/compatibility-matrix.md#OperatingSystems)。

**改进**

* Microsoft Dynamics CRM 365 连接器

   已对 Microsoft Dynamics Connector Web API 应用了以下重要修复：

   * 修复了在由工作流触发的导入过程中，导致字符串类型字段的 null 值保存为 Null 而不是空值的问题。
   * 修复了使用 Web API 调用时导致数据导入或导出出现以下错误的问题：“Invalid URI: The URI scheme is too long”。
   * 修复了从 Microsoft Dynamics 365 导入包含查找字段的数据时出现的各种问题。

* Google BigQuery FDA 连接器

   * Google BigQuery FDA 连接器现在可用于托管部署。[了解更多信息](../../installation/using/configure-fda-google-big-query.md)
   * 增加了对 Google BigQuery FDA 连接器启用代理服务器连接的支持。所需的代理选项可通过外部帐户配置的选项字段设置。[了解更多信息](../../installation/using/configure-fda-google-big-query.md#google-external)

**其他变更**

* 弃用后，已从界面中移除 Microsoft CRM、Salesforce、Oracle CRM On Demand 操作活动。要配置 Adobe Campaign 与 CRM 系统之间的数据同步，您可以使用 CRM 连接器活动。[了解更多信息](../../workflow/using/crm-connector.md)
* **[!UICONTROL Encrypted identifier]** 字段已添加至访客模式 (nms:visitor)。会计算该字段并将其用于 Web 应用程序。这适用于在中间源实例上配置 Line 渠道的情况。
* CRM 数据源现在可以与&#x200B;**更改数据源**&#x200B;活动一起使用。
* 在工作流活动的 **Error management** 属性中新增了一个选项：**Abort on error** 选项会自动停止工作流。之后您将无法重新启动它 (NEO-29661)。[了解更多信息](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* 现在，会使用专用序列来生成 nmsGroup 表的主键，该表格用于创建收件人的统计组。以前，使用的是 xtknewId 序列。(NEO-30832)
* 增加了对使用 CRM 连接器活动进行批量更新操作的支持。
* 改进了事务性消息传递的性能，缩短了处理时间。(NEO-40370)

**修补程序**

* 修复了在创建投放时会导致 **Tracking &amp; images** 窗口的 **Images** 选项卡中出现错误的问题。这种情况会在使用自动代理配置时发生。(NEO-33260)
* 修复了可能导致您无法在同步模式下在 Debian 10 服务器 (HTTPS) 上上传文件的问题。
* 修复了在数据库清理期间，在删除相关投放后，可能导致投放统计表 (`nmsDeliveryLogStats`) 的记录无法从中间源实例中清除的问题。(NEO-31034)
* 修复了在使用基于令牌的身份验证时，导致您无法在 iOS 上发送移动应用程序通知的问题 (NEO-38640)。
* 修复了在尝试创建和配置报告时可能显示脚本错误消息的问题 (NEO-38393)。
* 修复了由于同时更新大量投放指标，可能导致 Oracle 上的跟踪工作流失败的问题 (NEO-39653)。
* 修复了由于执行控制类型时出现错误而可能导致无法发送投放的问题 (NEO-39833)。
* 修复了登陆页面中可能导致特殊字符无法在在线调查响应的 HTML 页面中正确显示的问题 (NEO-39438)。
* 修复了右键单击“Explorer”选项卡中的任意文件夹时，可能导致 Campaign Classic 控制台无法工作的问题 (NEO-38884)。
* 修复了在新投放中使用之前创建的链接到网站分析帐户的投放模板时缺失网站分析配置的错误。(NEO-28666)
* 修复了可能导致您无法预览附加到工作流的移动投放的问题。
* 修复了在启用跟踪链接的 URL 签名机制时导致个性化的跟踪 URL 无法重定向的错误。
* 修复了由于索引管理问题而可能导致升级后出现故障的问题。
* 修复了在&#x200B;**导入**&#x200B;或&#x200B;**导出**&#x200B;工作流活动中通过 Microsoft Dynamics CRM 使用查找字段数据类型时发生的错误。
* 修复了由于代理配置问题而可能导致您无法登录到控制台的问题。(NEO-38388)
* 修复了导致&#x200B;**清除文件夹**&#x200B;功能无法正常运行的问题。(NEO-37459)
* 修复了在引用的 xml 包含双引号的情况下，通过 Microsoft Dynamics CRM 帐户使用 xml 数据字段时导致出现请求错误的问题。
* 修复了导致网络超时问题被错误记录为脚本中断而非网络错误的问题。在 JavaScript 活动中包含的 HTTP 请求中，会发生此问题。(NEO-38079)
* 修复了在尝试提取时间组件时，运行 Amazon Redshift HoursDiff 和 MinutesDiff 函数时返回错误结果的问题。(NEO-31673)
* 修复了导致&#x200B;**热门点击**&#x200B;报告无法加载自内部版本 9182 以来的投放的问题。(NEO-28900)
* 修复了会将 URL 中的 &amp; 符号替换为字符实体引用 (`&amp;`)，从而导致用户无法访问链接到 QR 代码的 URL 的问题。(NEO-28621)
* 修复了每次用户创建新的营销活动工作流和链接到网站分析帐户的投放活动时，都会创建一个新的外部帐户的问题。这是由于 webAnalyticsAccount 投放对象中缺少 ID 所导致。(NEO-39691)
* 修复了当数据库中的列表以负值 ID 标识时，可能会导致&#x200B;**读取列表**&#x200B;工作流活动无法运行的问题。(NEO-39607)
* 修复了可能导致&#x200B;**中间源（投放日志）**&#x200B;工作流失败的问题。(NEO-39662)
* 修复了可能导致您无法预览附加到工作流的电子邮件投放的问题。(NEO-37840)
* 修复了可能导致数据库清理工作流删除包含列表值的有效表的问题。(NEO-34911)
* 修复了可能导致营销实例上的计费工作流崩溃的问题。
