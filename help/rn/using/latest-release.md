---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 630a62c5e5c9782c5c55fdebd651493a2d68fc54
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 17%

---

# 最新版本{#latest-release}

![](../../assets/v7-only.svg)

本页列出了 **最新Campaign Classicv7版本**. 每个新内部版本都带有一个状态，该状态以颜色实现。 进一步了解Campaign Classicv7在中的构建状态 [本页](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) 7.2.1 版 - 版本 9346 {#release-7-2-1}

_2022年1月10日_

**安全性增强**

FDA帐户已进行多项安全改进：

* ODBC驱动程序现在直接与Adobe Campaign第三方安装。 安装这些驱动程序不再需要手动步骤。
* 配置FDA外部帐户时，您现在可以使用密钥对身份验证登录到Snowflake帐户，以增强身份验证安全性。 [了解更多信息](../../installation/using/configure-fda-snowflake.md)
* 现在，在配置FDA外部帐户时，您可以使用系统分配的托管身份登录到Azure synapse分析帐户。 [了解更多信息](../../installation/using/configure-fda-synapse.md#azure-external)
* 已从Campaign中删除对log4j库的所有引用，以确保获得最佳安全性。

**改进**

* Microsoft Dynamics CRM 365 Connector

   已对Microsoft Dynamics Connector Web API应用了以下关键修复：

   * 修复了在由工作流触发的导入期间导致字符串类型字段的null值保存为Null而不是空值的问题。
   * 修复了使用Web API调用导致数据导入或导出出现以下错误的问题：&quot;无效的URI:URI方案太长”。
   * 修复了从Microsoft Dynamics 365导入包含查找字段的数据时出现的各种问题。

* Google BigQuery FDA连接器

   * Google BigQuery FDA连接器现已可用于托管部署。 [了解更多信息](../../installation/using/configure-fda-google-big-query.md)
   * 添加了对为Google BigQuery FDA连接器启用与代理服务器的连接的支持。 必需的代理选项可通过外部帐户配置的选项字段设置。 [了解更多信息](../../installation/using/configure-fda-google-big-query.md#google-external)

**其他变更**

* 弃用后，已从界面中删除Microsoft CRM、Salesforce、OracleCRM按需操作活动。 要配置Adobe Campaign与CRM系统之间的数据同步，您可以使用CRM连接器活动。 [了解更多信息](../../workflow/using/crm-connector.md)
* 的 **[!UICONTROL Encrypted identifier]** 字段已添加到访客模式(nms:visitor)。 会计算该字段并将其用于 Web 应用程序。在中间源实例上配置Line渠道时，这种情况适用。
* CRM数据源现在可以与 **更改数据源** 活动。
* 在 **错误管理** 工作流活动的属性：的 **出错时中止** 选项会自动停止工作流。 之后将无法重新启动它(NEO-29661)。 [了解更多信息](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* 现在，专用序列用于生成nmsGroup表的主密钥，该表用于创建收件人的统计组。 以前，使用xtknewId序列。 (NEO-30832)
* 添加了对使用CRM连接器活动进行批量更新操作的支持。
* 改进了事务性消息传递处理时间的性能。 (NEO-40370)

**修补程序**

* 修复了在创建投放时导致 **图像** 选项卡 **跟踪和图像** 窗口。 使用自动代理配置时发生此情况。 (NEO-33260)
* 修复了可能阻止您在同步模式下在Debian 10服务器(HTTPS)上上传文件的问题。
* 修复了可能阻止投放统计表记录(`nmsDeliveryLogStats`)，以阻止在删除相关投放后在数据库清理期间从中间源实例中清除。 (NEO-31034)
* 修复了在使用基于令牌的身份验证(NEO-38640)时，阻止在iOS上发送移动应用程序通知的问题。
* 修复了在尝试创建和配置报表时可能显示脚本错误消息的问题(NEO-38393)。
* 修复了由于大量投放指标同时更新，可能导致跟踪工作流在Oracle时失败的问题(NEO-39653)。
* 修复了可能由于执行控制分类时出现错误而阻止发送投放的问题(NEO-39833)。
* 修复了登陆页面中可能阻止特殊字符在在线调查响应的HTML页面中正确显示的问题(NEO-39438)。
* 修复了在Explorer选项卡中右键单击任意文件夹时可能会阻止Campaign Classic控制台工作的问题(NEO-38884)。
* 修复了在新投放中使用之前创建的投放模板（该模板链接到缺少Web分析配置的Web分析帐户）时的错误。 (NEO-28666)
* 修复了可能导致您无法预览附加到工作流的移动投放的问题。
* 修复了在启用跟踪链接的URL签名机制时阻止重定向个性化跟踪URL的错误。
* 修复了由于索引管理问题而可能导致升级后失败的问题。
* 修复了在中将查找字段数据类型与Microsoft Dynamics CRM结合使用时发生的错误 **导入** 或 **导出** 工作流活动。
* 修复了由于代理配置问题而阻止您登录控制台的问题。 (NEO-38388)
* 修复了导致&#x200B;**清除文件夹**&#x200B;功能无法正常运行的问题。(NEO-37459)
* 修复了在引用的xml包含双引号的情况下，将xml-data字段与Microsoft Dynamics CRM帐户一起使用时导致请求错误的问题。
* 修复了导致网络超时被错误记录为脚本中断而非网络错误的问题。在 JavaScript 活动中包含的 HTTP 请求中，会发生此问题。(NEO-38079)
* 修复了在尝试提取时间组件时，运行 Amazon Redshift HoursDiff 和 MinutesDiff 函数时返回错误结果的问题。(NEO-31673)
* 修复了阻止 **热点点击** 从9182内部版本开始报告投放的加载情况。 (NEO-28900)
* 修复了将URL中的&amp;符号替换为字符实体引用(`&amp;`)会阻止用户访问链接到二维码的URL。 (NEO-28621)
* 修复了每次用户创建新的营销活动工作流程和链接到Web Analytics帐户的投放活动时，都会创建一个新的外部帐户的问题。 这是由webAnalyticsAccount交付对象中缺少ID所导致。 (NEO-39691)
* 修复了当数据库中的列表以负值 ID 标识时，可能会导致&#x200B;**读取列表**&#x200B;工作流活动无法运行的问题。(NEO-39607)
* 修复了可能导致 **中间源（投放日志）** 工作流失败。 (NEO-39662)
* 修复了可能阻止预览附加到工作流的电子邮件投放的问题。 (NEO-37840)
* 修复了可能导致数据库清理工作流删除包含列表值的有效表的问题。 (NEO-34911)
* 修复了可能导致营销实例上的计费工作流崩溃的问题。
