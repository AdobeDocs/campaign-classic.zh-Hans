---
product: campaign
title: Campaign Classic 2022 版
description: 详细了解 Campaign Classic 2022 版
feature: Release Notes
role: User
level: Beginner
exl-id: 28490323-41d0-4d61-b309-6892fb826d21
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: ht
source-wordcount: '2100'
ht-degree: 100%

---

# 2022 版{#release-2022}

## 7.3.1 版 - 内部版本 9352 {#release-7-3-1}

[!BADGE 已弃用]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="已弃用"}

_2022 年 7 月 1 日_

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
<p>请参阅<a href="../../delivery/using/create-notifications-ios.md">详细文档</a>以了解如何创建时效性通知。</p>
</td> 
</tr> 
</tbody> 
</table>

**兼容性更新**

* 现在，Adobe Campaign SDK 支持在 Android 12 和 iOS 15 上使用“推送通知”。
* Adobe Campaign 现与 MySQL 8 兼容。
* Adobe Campaign 现与 Windows 11 兼容。
* Adobe Campaign 现与 Debian 11 兼容。有关更多信息，请参见此[技术说明](../../technotes/using/tech-stack-upgrade.md)。

请参阅 [Campaign 兼容性矩阵](../../rn/using/compatibility-matrix.md#OperatingSystems)。

**改进**

* 在 Microsoft Internet Explorer 11 生命周期终止后，客户端控制台中的 Adobe 服务（登录页）的 HTML 渲染引擎现使用 Edge Chromium。请注意，Microsoft Internet Explorer 11 仍是客户端控制台中的仪表板的 HTML 渲染引擎。此外，任何客户端控制台安装（从 Campaign Classic 7.3 内部版本开始）现在都需要安装 Microsoft Edge Webview 2 运行时。[了解更多信息](../../installation/using/installing-the-client-console.md)
* 改进了 Adobe Campaign 中的数据库连接管理，以优化稳定性。
* Campaign 现在支持适用于 POP3 的 Microsoft Exchange Online OAuth 2.0 身份验证。[了解更多信息](../../installation/using/external-accounts.md#bounce-mails-external-account)
* 修复了将扩充工作流活动与外部数据结合使用时的各种问题。(NEO-38069)
* 更新了 SAP Hana FDA 连接器，可支持 SAP Hana 数据库最新版本 (2.x)。
* 更新了 Teradata FDA 连接器，可支持 Teradata 最新版本 (17)。
* 在 20.2 中，为新投放和投放模板引入了针对 iOS 投放的基于令牌的身份验证支持。在 7.2 中，为向升级后添加了一个修补程序，以便可以将基于令牌的身份验证支持应用于最多 10,000 个之前创建的投放和投放模板。在 7.3 中，改进了此修补程序，并移除了限制。

**修补程序**

* 修复了上一内部版本中的错误，该错误会导致用户无法调整 IMS 登录页面的大小。(NEO-30085)
* 修复了在现有实例上安装内容管理器包时发生的错误。(NEO-32349)
* 修复了 **Campaigns** 菜单中持续显示“operation in progress”消息的问题。(NEO-44904)
* 修复了在启用 Adobe Analytics 后发送带有 URL 的电子邮件时，会从 URL 中删除 BID (Broadlog ID) 和 CID（营销活动 ID）而不保存投放的问题。(NEO-38678)
* 修复了在使用消息中心特定配置的实例的公共资源文件夹中上传图像时出现的问题。会显示以下错误消息：“Unable to upload the images to the tracking servers”。(NEO-38546、NEO-45572)
* 修复了在配置文件不正确的情况下重新生成配置时导致系统崩溃的问题。(NEO-38752)
* 修复了可能导致传递指示器无法正确更新的问题。(NEO-44827)
* 修复了在使用复杂查询时可能导致升级后错误的问题。(NEO-43648)
* 修复了可能导致 webApps 预览无法运行的问题。(NEO-43242)
* 修复了在具有数据加载（文件）活动的工作流中使用外部目标映射文件时，可能导致投放准备失败的问题。(NEO-43691)
* 修复了可能导致崩溃并需要完全重启实例的问题。(NEO-44645)
* 修复了可能导致工作流热图无法加载任何结果的问题。(NEO-43360)
* 修复了使用 FDA 外部连接器时可能导致连接错误的问题。(NEO-42722)
* 修复了使用地址替换和对照组排除时验证的问题。(NEO-39695)
* 修复了由于 Snowflake 连接器问题而可能导致工作流失败的问题。(NEO-46299)
* 修复了可能由于个性化块中的无效字符而冻结客户端控制台的问题。(NEO-45761)
* 修复了为用作外部数据库的 Snowflake 创建外部帐户时可能导致连接错误的问题。(NEO-45744)
* 修复了可能导致显示受 visibleIf 属性保护的表信息的问题。(NEO-37865)
* 修复了在投放分析阶段可能显示“$ is not defined”错误消息的问题。(NEO-32940)
* 修复了导致投放与错误的 eventType 关联的问题。(NEO-45743)
* 修复了由于间歇性核心转储而导致崩溃的问题 (NEO-30549)
* 修复了在投放中使用错误 HTML 代码时可能导致崩溃的问题。(NEO-40385)
* 修复了可能导致非管理员用户无法访问投放属性中的 **Analysis** 选项卡的问题。(NEO-34025)
* 修复了在消息准备期间可能会阻止图像以块模式从外部服务器上传的问题。(NEO-40307)
* 修复了可能导致向比预期更多的收件人发送投放的问题。(NEO-45108)

## 7.2.2 版 - 内部版本 9349 {#release-7-2-2}

[!BADGE 已弃用]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="已弃用"}

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
* 修复了导致打开率和点击率传递指示器无法自动更新的问题。(NEO-43253)

## 7.2.1 版 - 内部版本 9346 {#release-7-2-1}

[!BADGE 已弃用]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="已弃用"}

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
* 修复了由于同时更新大量传递指示器，可能导致 Oracle 上的跟踪工作流失败的问题 (NEO-39653)。
* 修复了由于执行控制类型时出现错误而可能导致无法发送投放的问题 (NEO-39833)。
* 修复了登陆页面中可能导致特殊字符无法在在线调查响应的 HTML 页面中正确显示的问题 (NEO-39438)。
* 修复了右键单击“探索工具”选项卡中的任意文件夹时，可能导致 Campaign Classic 控制台无法工作的问题 (NEO-38884)。
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
