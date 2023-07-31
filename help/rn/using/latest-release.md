---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '993'
ht-degree: 100%

---

# 最新版本{#latest-release}

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。每个新的内部版本都带有一个以颜色突出显示的状态。在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## 7.3.3 版 - 内部版本 9359 {#release-7-3-3}

[!BADGE 正式发布版]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="正式发布版"}

>[!CAUTION]
>
>必须升级客户端控制台。在[此页面](../../installation/using/installing-the-client-console.md)中了解如何升级您的客户端控制台。

_2023 年 3 月 20 日_

**安全性增强**

* 为了优化安全性，已将 Tomca 版本从 8.5.81 更新到 8.5.85。(NEO-56936)

**改进**

* 改进了计费工作流以优化性能。(NEO-47658)
* 改进了跟踪工作流程，从而优化在投放大小较高时的性能。(NEO-45064)
* 改进了跟踪管理，以修复 URL 中动态参数可能存在的问题。跟踪管理 v3 现在可以处理 AJAX 类型的 URL（在“#”后面带有参数）并可阻止第三方工具修改跟踪 URL。要应用此更改，请联系 Adobe。(NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**修补程序**

* 修复了一个可能导致无法从控制实例（事务性消息传递上下文）发送 iOS 验证推送通知的问题。(NEO-54713)
* 修复了可能导致无法在数字内容编辑器 (DCE) 的&#x200B;**编辑**&#x200B;选项卡中滚动的问题。(NEO-54474)
* 修复了两个扩充活动在其链接中使用相同名称标识符时导致第二个扩充活动使用第一个活动的链接的问题。(NEO-48851)

## 7.3.2 版 - 内部版本 9356 {#release-7-3-2}

[!BADGE 有限发布版]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="有限发布版"}

_2022 年 11 月 21 日_

>[!CAUTION]
>
>必须升级客户端控制台。在[此页面](../../installation/using/installing-the-client-console.md)中了解如何升级您的客户端控制台。

**兼容性更新**

* Adobe Campaign 现与 PostgreSQL 14 兼容。有关更多信息，请参见此[技术说明](../../technotes/using/tech-stack-upgrade.md)。

* 在 Microsoft Internet Explorer 11 的生命周期终止后，客户端控制台中仪表板的 HTML 渲染引擎现在使用的是 Edge Chromium。(NEO-20741)

在 [Campaign 兼容性矩阵](../../rn/using/compatibility-matrix.md#RDBMSservers)中了解详情。

**改进**

* Google BigQuery 连接器现在完全支持布尔字段。(NEO-49181)
* 您现在可以在 serverConf.xml 文件的 `Configuration for the redirection service` 部分配置 IMS Cookie 的有效期。这适用于以下 Cookie：`uuid230`、`nllastdelid` 和 `AMCV_` (NEO-42541)
* 现在通过在 serverConf.xml 文件的重定向节点中将 `showSourceIP` 设置为“false”，可将 IP 在“/r/test”请求中隐藏。[了解更多信息](../../installation/using/the-server-configuration-file.md#redirection-redirection) (NEO-46656)

**已弃用的功能**

* 通过 Facebook 进行社交媒体营销的功能现已弃用。您可以使用 Twitter 集成在社交媒体上发布内容，或与 Adobe 合作创建自定义渠道。
* ACS 连接器（高级服务）现已弃用。您可以使用 Campaign 的导出/导入功能来从两款产品中提取数据或向其中插入数据。

在[已弃用和已删除的功能页面](deprecated-features.md)中了解详情。

**其他变更**

* 网络日志已改进：`logonEscalation` 警告信息现在仅会向拥有管理员权限的用户显示。(NEO-47167)
* 为避免出现错误，**为热图服务收集数据** (collectDataHeatMapService) 工作流现在会默认处于停止状态。(NEO-33959)
* 实施了各种旨在优化活动仪表板的 CPU 使用率的改进。(NEO-46417)
* 为防止出现崩溃，loadLibraryDebug JS 方法已被移除。(NEO-46968)
* 对 log4j 库的其余引用已从 Windows 上的 Campaign 安装中移除。(NEO-44851)

**修补程序**

* 修复了会导致用户无法使用&#x200B;**合并所选行**&#x200B;工作流选项的问题。(NEO-48488)
* 修复了在使用 Adobe Campaign 增强 MTA 时，无法正确更新 **Success** 投放指标的问题。(NEO-50462)
* 修复了在电子邮件投放中重置内容批准时出现的问题，此问题会导致您无法进行重新批准。(NEO-44259)
* 修复了可能导致&#x200B;**投放批准**&#x200B;按钮无法显示的问题。(NEO-47547)
* 修复了投放的 HTML 选项卡的性能问题，该问题可能会在大型 HTML 代码中出现。(NEO-47440)
* 修复了当 `FeatureFlag_GZIP_Compression` 选项启用时，会影响 MID 实例上的投放日志状态更新的问题。(NEO-49183)
* 修复了在使用基于令牌的身份验证时，会导致无法从执行实例发送 iOS 移动应用程序通知的问题。(NEO-45961)
* 修复了&#x200B;**刷新可投放性**&#x200B;工作流 (deliverabilityUpdate) 的问题，此问题的表现为：当要同步的 broadlog 过多时，该工作流会卡住。(NEO-48287)
* 修复了会阻止&#x200B;**消息中心同步** (mcSynch) 工作流的事件类型问题。
* 修复了在&#x200B;**查询**&#x200B;工作流活动的附加数据中添加&#x200B;**已打开的收件人** (estimatedRecipientOpen) 指标时，可能会导致错误的问题。(NEO-46665)
* 修复了一项与&#x200B;**计费**&#x200B;工作流有关的问题，其具体表现为，当在同一实例上安装了消息中心控制和执行包时，该工作流会失败。(NEO-47674)
* 修复了一项与&#x200B;**计费**&#x200B;工作流有关的问题，其具体表现为：在具有其主键被定义为字符串而不是整数的表时，该工作流会失败。(NEO-46254)
* 修复了工作流名称过长时，热图过滤器会出现的一项问题。(NEO-46301)
* 修复了 7.3.1 版本中的 Snowflake FDA 连接器存在的问题，在扩充期间使用“0 或 1 基数简单联接”时，该问题会导致记录被丢弃。(NEO-48737)
* 修复了 Snowflake FFDA 的一个问题，在使用&#x200B;**拆分**&#x200B;工作流活动中的排序参数时，此问题会出现。(NEO-45899)
* 修复了可能会导致无法保存外部帐户配置的问题。对于具有解析器功能的连接器（Snowflake 和 Google BigQuery）而言，现在当连接测试完成后，外部帐户将被自动保存。(NEO-47636)
* 修复了会导致无法在 MSSQL 的&#x200B;**数据更新**&#x200B;工作流活动中插入时间数据类型的问题。(NEO-47763)
* 修复了在引擎时区未设置时（特定于 MSSQL），会导致 MTA 流程崩溃的问题。(NEO-46619)
* 修复了当映像节点 (img) 包含具有个性化字段的 URL 时，HTML 文件导入的问题。(NEO-48396)
* 修复了未在 serverConf.xml 中配置 `limit` 节点的情况下，当尝试连接实例时出现 HTTP 500 错误的问题。
* 修复了一项可能会导致“字符集匹配有误”的错误的问题，在未启用 NChar 的 Oracle Unicode 数据库中使用某些函数（如 `to_nclob`）时，该问题会出现。(NEO-49361)
* 修复了对 nmsDeliveryMapping 文件夹具有读取访问权限的用户尝试运行活动或工作流时会导致错误的问题。(NEO-48230)
* 修复了会导致 `JSPContext.sqlExecWithOneParam` 功能无法正常运行的问题。(NEO-50066)
* 修复了各种重定向错误。(NEO-50030)
