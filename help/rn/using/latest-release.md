---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: fc49c0ec80c8741b01ea150c3bc7362b73357607
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 100%

---

# 最新版本{#latest-release}

![](../../assets/v7-only.svg)

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。每个新的内部版本都带有一个以颜色突出显示的状态。在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## ![](assets/do-not-localize/green_2.png) 7.2.1 版 - 版本 9346 {#release-7-2-1}

_2022 年 1 月 10 日_

**安全性增强**

FDA 帐户已进行多项安全性增强：

* 配置 FDA 外部帐户时，您现在可以使用密钥对身份验证登录到 Snowflake 帐户，以增强身份验证安全性。[了解更多信息](../../installation/using/configure-fda-snowflake.md)
* 在配置 FDA 外部帐户时，您现在可以使用系统分配的托管身份登录到 Azure Synapse Analytics 帐户。[了解更多信息](../../installation/using/configure-fda-synapse.md#azure-external)
* 已从 Campaign 中删除对 log4j 库的所有引用，以确保获得最佳安全性。

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
