---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2312'
ht-degree: 100%

---

# 最新版本{#latest-release}

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。每个新的内部版本都带有一个以颜色突出显示的状态。在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## 7.3.5 版 - 内部版本 9368 {#release-7-3-5}

[!BADGE 正式发布版]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="正式发布版"}


_2023 年 12 月 5 日_


### 安全性增强 {#release-7-3-5-security}


* 在 Campaign Classic v7.3.5 中，身份验证过程已得到改进并受保护。现在，技术操作员应使用 Adobe Identity Management System (IMS) 连接到 Campaign。请阅读[此技术说明](../../technotes/using/ims-migration.md)，了解如何迁移现有技术帐户。

* 此外，作为加强安全和身份验证过程的一部分，Adobe Campaign 强烈建议将终端用户身份验证模式从登录/密码本机身份验证迁移到 Adobe Identity Management System (IMS)。请阅读[此技术说明](../../technotes/using/migrate-users-to-ims.md)，了解如何迁移操作员。

* 现在，如果 Web 窗体有&#x200B;**待发布**&#x200B;状态，它不会自动上线。为防止出现安全问题，必须先将其发布，然后才能使其&#x200B;**上线**&#x200B;并通过 Web 浏览器中的 Web 窗体 URL 访问它。[了解更多信息](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### 修补程序 {#release-7-3-5-patches}

* 修复了使用 Google Big Query 数据库中的数据和更新 Oracle 数据库中的数据时出现的问题：在工作流临时表中，将所有键都设置为 `0`。(NEO-65091)
* 修复了当 Google Big Query 数据库上的两个查询合并到 **Union** 工作流活动中时导致工作流执行失败的问题。(NEO-63705)
* 修复了在 Campaign 报告中单击 `Back` 按钮时请求用户重新进行身份验证的问题。(NEO-65087)
* 修复了数据库清理工作流中发生的错误，在投放证明前删除投放时会发生该错误。(NEO-48114)
* 修复了连接到客户端控制台时的问题：最近对 TLS 验证的更新导致连接错误。(NEO-50488)
* 修复了 Campaign 升级到 7.3.1 后 HTTP 代理身份验证的问题。活动工作流中的 HTTP 请求失败，并出现 `error 407 – proxy auth required is returned`。(NEO-49624)
* 修复了&#x200B;**脚本**&#x200B;工作流活动中 GPG 解密的间歇性故障。相关的错误消息为：`gpg: decryption failed: No secret key`。(NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

## 7.3.4 版 - 内部版本 9364 {#release-7-3-4}

[!BADGE 有限发布版]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="有限发布版"}


>[!CAUTION]
>
>必须升级客户端控制台。在[此页面](../../installation/using/installing-the-client-console.md)中了解如何升级您的客户端控制台。
>
>如果您使用 [Campaign - Microsoft Dynamics CRM 连接器](../../platform/using/crm-connectors.md)，您必须使用此全新内部版本升级营销和中间源服务器。

_2023 年 9 月 7 日_

### 安全性增强 {#release-7-3-4-security}

* 提高了 IMS API 的安全性。已从 URL 参数中移除客户端敏感信息（即访问令牌）。 这些凭据现在以 POST 数据或授权标头的形式发送，确保通信过程更加安全。(NEO-63045)
* 提高了 Web 应用程序的安全性，以防止 DDOS 攻击。(NEO-50757)
* 增强了安全性，以防止在 Web 日志错误中暴露 PII 数据。(NEO-46827)
* 安全性已得到优化，以防止安全令牌包含在 Campaign 主页 URL 中。(NEO-38519)

### 兼容性更新  {#release-7-3-4-compat}

* Tomcat 已更新至 8.5.91 版
* libexpat 库已更新至 2.5.0 以提高安全性。(NEO-51023)

### 改进 {#release-7-3-4-improvements}

* 修改了服务器配置文件 (serverConf.xml) 中的 MaxWorkingSetMb 参数，以优化投放的内存分配。(NEO-49204)
* BigQuery 外部帐户已通过用于设置 GCloud SDK 的新选项得到增强。(NEO-63879) [阅读更多](../../installation/using/configure-fda-google-big-query.md#google-external)
* 服务器配置文件 (serverConf.xml) 中添加了新的 `cusHeader` 部分。这允许您在从外部服务器上传文件时添加自定义标头。(NEO-58339) [阅读更多](../../installation/using/the-server-configuration-file.md#cusheaders)。
* 跟踪日志管理得到了改进，以避免 lastMsgId 出现负 ID。已从 int32 更改为 int64。(NEO-52290)
* 增添了开箱即用的中间源（投放统计数据）工作流程。这一新工作流可将投放统计数据 (nms:deliveryStat) 从中间实例同步到营销实例。(NEO-36802)

### 修补程序 {#release-7-3-4-patches}

* 修复了如果服务请求调用身份验证正在使用服务令牌，在 IMS 登录之前发出服务请求时可能发生的问题。(NEO-64903)
* 修复了在使用数字内容编辑器时可能导致出现滚动问题的回退问题。(NEO-64671、NEO-59256)
* 修复了将内容从 Excel 粘贴到数字内容编辑器时的回退问题。(NEO-63287)
* 修复了可能会导致 Web 应用程序在 v5 兼容模式下无法正确显示的问题。(NEO-63174)
* 修复了导致非管理员操作员无法发送 WebAnalytics 投放的问题。(NEO-62750)
* 修复了在投放中使用条件内容时导致浏览器无法添加额外空格的问题。(NEO-62132)
* 修复了使用与多个日志模式关联的目标模式时，导致活跃联系人计算无法在计费工作流中正确工作的回退问题。(NEO-61468)
* 修复了在编辑投放内容时可能导致出现错误且无法滚动的问题。(NEO-61364)
* 修复了在电子邮件内容编辑器中单击图像时导致打开弹出窗口的问题。(NEO-60752)
* 修复了可能导致投放的 HTML 内容中的特殊字符在多个浏览器中被错误编码的问题。(NEO-60081)
* 修复了在使用 in短信工作流活动时可能发生的同步问题。(NEO-59544)
* 修复了使用具有时间戳或日期时间字段的 Big Query 连接器时的问题。(NEO-59502、NEO-49768)
* 修复了导致无法使用累积投放报告的问题。(NEO-59211)
* 修复了在与 People 核心服务共享受众时可能导致错误的问题。(NEO-58637)
* 修复了显示投放镜像页面时的问题。(NEO-58325)
* 修复了导致 XtkLibrary.Right() xtk 表达式无法工作的问题。(NEO-57870)
* 修复了在数字内容编辑器中上传图像时导致主体标记样式属性更改的问题。(NEO-57697)
* 修复了使用 CRM 连接器活动执行批量导出时的特殊字符问题。(NEO-54300)
* 修复了在使用数据加载活动和 Big Query 连接器时，导致批量加载功能无法处理“字符串”数据类型的问题。(NEO-53748)
* 修复了可能导致优惠呈现问题的缓存键问题。(NEO-51516、NEO-49995)
* 修复了在使用获得批准的 targetMapping 发送直邮投放时可能导致验证错误的问题。(NEO-50758)
* 修复了可能影响投放性能的查询管理问题。(NEO-49991)
* 修复了在营销活动工作流投放活动中使用外部帐户时，可能导致外部帐户配置错误的问题。(NEO-49959)
* 修复了发送推送通知时的性能问题。(NEO-49953)
修复了在导出报告时可能导致日语字符错误显示的问题 (NEO-49308)。
* 修复了导致 Tomcat 错误报告显示过多错误详细信息的问题。(NEO-49029)
* 修复了在使用大量优惠时可能导致投放错误的问题。(NEO-48807)
* 修复了可能导致&#x200B;**更新数据**&#x200B;工作流活动无法正常工作的问题。(NEO-48140)
* 修复了可能导致无法使用电子邮件以外的外部帐户为投放同步点击跟踪数据的问题。(NEO-47277)
* 修复了可能导致实时跟踪日志无法在消息中心营销实例上同步的问题。(NEO-42540)
* 修复了 Snowflake 数据库表的工作区前缀无法显示在模式的发现窗口中的问题。(NEO-40297)
* 修复了导致 `<img-amp>` 标记无法在电子邮件内容中正常工作的问题。(NEO-38685)
* 修复了在使用 HTTP 中继时可能导致消息中心存档工作流失败的问题。(NEO-33783)
* 修复了可能导致电子邮件内容编辑器中出现字体名称和大小错误的问题。(NEO-61342)

## 7.3.3 版 - 内部版本 9359 {#release-7-3-3}

[!BADGE 有限发布版]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="有限发布版"}

>[!AVAILABILITY]
>
>针对此版本提供了特定的 Campaign v7.3.3.IMS 修补程序升级 - 如果未在您的环境安装其他修补程序，则可以安装它。它将 [v7.3.5 附带的 Adobe Identity Management System (IMS) 安全更新](#release-7-3-5-security)应用到现有 v7.3.3 环境。


_2023 年 3 月 20 日_


### 安全性增强 {#release-7-3-3-security}

* 为了优化安全性，已将 Tomca 版本从 8.5.81 更新到 8.5.85。(NEO-56936)



### 改进 {#release-7-3-3-improvements}

* 改进了计费工作流以优化性能。(NEO-47658)
* 改进了跟踪工作流程，从而优化在投放大小较高时的性能。(NEO-45064)
* 改进了跟踪管理，以修复 URL 中动态参数可能存在的问题。跟踪管理 v3 现在可以处理 AJAX 类型的 URL（在“#”后面带有参数）并可阻止第三方工具修改跟踪 URL。要应用此更改，请联系 Adobe。(NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

>[!CAUTION]
>
>必须升级客户端控制台。在[此页面](../../installation/using/installing-the-client-console.md)中了解如何升级您的客户端控制台。

### 修补程序 {#release-7-3-3-patches}

* 修复了一个可能导致无法从控制实例（事务性消息传递上下文）发送 iOS 验证推送通知的问题。(NEO-54713)
* 修复了可能导致无法在数字内容编辑器 (DCE) 的&#x200B;**编辑**&#x200B;选项卡中滚动的问题。(NEO-54474)
* 修复了两个扩充活动在其链接中使用相同名称标识符时导致第二个扩充活动使用第一个活动的链接的问题。(NEO-48851)

## 7.3.2 版 - 内部版本 9356 {#release-7-3-2}

[!BADGE 有限发布版]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="有限发布版"}


>[!AVAILABILITY]
>
>针对此版本提供了特定的 Campaign v7.3.2.IMS 修补程序升级 - 如果未在您的环境安装其他修补程序，则可以安装它。它将 [v7.3.5 附带的 Adobe Identity Management System (IMS) 安全更新](#release-7-3-5-security)应用到现有 v7.3.3 环境。

_2022 年 11 月 21 日_

### 兼容性更新 {#release-7-3-2-compat}

* Adobe Campaign 现与 PostgreSQL 14 兼容。有关更多信息，请参见此[技术说明](../../technotes/using/tech-stack-upgrade.md)。

* 在 Microsoft Internet Explorer 11 的生命周期终止后，客户端控制台中仪表板的 HTML 渲染引擎现在使用的是 Edge Chromium。(NEO-20741)

在 [Campaign 兼容性矩阵](../../rn/using/compatibility-matrix.md#RDBMSservers)中了解详情。

>[!CAUTION]
>
>必须升级客户端控制台。在[此页面](../../installation/using/installing-the-client-console.md)中了解如何升级您的客户端控制台。

### 改进 {#release-7-3-2-improvements}

* Google BigQuery 连接器现在完全支持布尔字段。(NEO-49181)
* 您现在可以在 serverConf.xml 文件的 `Configuration for the redirection service` 部分配置 IMS Cookie 的有效期。这适用于以下 Cookie：`uuid230`、`nllastdelid` 和 `AMCV_` (NEO-42541)
* 现在通过在 serverConf.xml 文件的重定向节点中将 `showSourceIP` 设置为“false”，可将 IP 在“/r/test”请求中隐藏。[了解更多信息](../../installation/using/the-server-configuration-file.md#redirection-redirection) (NEO-46656)

### 已弃用的功能  {#release-7-3-2-deprecated}

* 通过 Facebook 进行社交媒体营销的功能现已弃用。您可以使用 X（以前称为 Twitter）集成在社交媒体上发布内容，或与 Adobe 合作创建自定义渠道。
* ACS 连接器（高级服务）现已弃用。您可以使用 Campaign 的导出/导入功能来从两款产品中提取数据或向其中插入数据。

在[已弃用和已删除的功能页面](deprecated-features.md)中了解详情。

### 其他变更  {#release-7-3-2-other}

<!--* Web logs have been improved: `logonEscalation` warnings are now only displayed for users with admin privileges. (NEO-47167)-->
* 为避免出现错误，**为热图服务收集数据** (collectDataHeatMapService) 工作流现在会默认处于停止状态。(NEO-33959)
* 实施了各种旨在优化活动仪表板的 CPU 使用率的改进。(NEO-46417)
* 为防止出现崩溃，loadLibraryDebug JS 方法已被移除。(NEO-46968)
* 对 log4j 库的其余引用已从 Windows 上的 Campaign 安装中移除。(NEO-44851)

### 修补程序 {#release-7-3-2-patches}

* 修复了会导致用户无法使用&#x200B;**合并所选行**&#x200B;工作流选项的问题。(NEO-48488)
* 修复了在使用 Adobe Campaign 增强 MTA 时，无法正确更新 **Success** 传递指示器的问题。(NEO-50462)
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
