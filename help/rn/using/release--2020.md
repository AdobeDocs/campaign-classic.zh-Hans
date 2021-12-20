---
product: campaign
title: 2020版
description: 了解有关Campaign Classic2020版本的更多信息
feature: Overview
role: User
level: Beginner
source-git-commit: eb0e572f0bb6196a58a7dab4999df784d5c4851f
workflow-type: tm+mt
source-wordcount: '6569'
ht-degree: 73%

---

# 2020版{#release-2020}

![](../../assets/v7-only.svg)


## 20.3 版{#release-20-3}

### ![](assets/do-not-localize/red_2.png) 20.3.3 版 - 版本 9234 {#release-20-3-3-build-9234}

_2021年1月11日_

* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)
* 修复了与 broadlog 生成过程相关的回归问题，该问题可能导致 MTA 进程崩溃。

### ![](assets/do-not-localize/red_2.png) 20.3.1 版 - 版本 9228 {#release-20-3-1-build-9228}

_2020 年 10 月 27 日_

>[!CAUTION]
>
> * 此版本附带新的连接协议：如果您是通过 Adobe Identity Service (IMS) 连接到 Campaign，则 Campaign 服务器和客户端控制台都必须升级，这样才能在&#x200B;**2021 年 6 月 30 日**&#x200B;之后连接到 Campaign。[了解详情](../../technotes/using/ims-updates.md)
> * 此版本附带[安全修复](https://helpx.adobe.com/cn/security/products/campaign/apsb21-04.html)：必须升级以增强环境安全性。
> * 如果您是通过 oAuth 身份验证使用 Experience Cloud Triggers 集成，则需要按照[此页面](../../integrations/using/configuring-adobe-io.md)中的说明移至 Adobe I/O。Campaign的旧版oAuth身份验证模式 [已经退休了](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) on **2021年9月**. 在扩展之前，托管环境将从扩展中受益  **2022年2月23日**. 作为内部部署或混合型客户，请联系Adobe客户关怀团队，将支持延长至2022年2月。 您必须向 Adobe 提供 [OAuth 应用程序的 AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)。


**新增功能**

<table> 
<thead>
<tr> 
<th> <strong>iOS 推送通知改进</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>在将移动应用程序与 Campaign 集成时，您需要保护与 Apple 推送通知服务 (APNs) 的通信。您可以使用基于证书或基于令牌的身份验证。
</p>
<p>以下两种身份验证模式现在可用于 Campaign Classic 中的 iOS 移动应用程序：
</p>
<ul> 
<li><p>基于令牌的身份验证（推荐）：此身份验证模式基于 .p8 文件。此身份验证模式速度更快，因为对 APNs 的每个请求都包含令牌。<a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">了解详情</a></p></li>
<li><p>基于证书的身份验证：此身份验证模式基于 .p12 文件。对于每个应用程序，需要单独的证书。此证书由 Apple 通过您的开发人员帐户提供。<a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">了解详情</a></p></li> 
</ul>
<p>在<a href="../../delivery/using/configuring-the-mobile-application.md">详细文档</a>中了解如何在 Campaign 中选择身份验证模式。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Android 推送通知改进</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">Android 推送通知已得到改进，可支持 FCM HTTP v1 API for Android 推送渠道身份验证。</a> </p>
<p>使用新的受支持 API 版本，您现在可以发送 FCM 通知消息，该消息提供增强的富推送消息传递功能。<a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">了解详情</a></p> 
<p>在<a href="../../delivery/using/configuring-the-mobile-application-android.md">此部分</a>中了解如何在 Adobe Campaign 中配置 FCM HTTP v1 API for Android。</p>
</td> 
</tr> 
</tbody> 
</table>

**安全性增强**

* 库的安全加载：为了防止 DLL 预加载攻击，Campaign 现在在加载 Campaign 客户端 (nlclient) 时仅从 Windows 默认系统 DLL 路径加载 Windows DLL。[了解详情](https://support.microsoft.com/zh-cn/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 攻击的防范。(NEO-25661)
* 修复了处理 GDPR 隐私请求时发生的问题，该问题导致无法从与收件人表具有二级关系的自定义表中删除记录。(NEO-25967)
* 修复了在尝试同步 Adobe Experience Manager 模板时使用非管理员用户发出的 API 调用的安全问题。(NEO-23487)

**兼容性更新**

Campaign 现在支持以下系统：
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

在 [Campaign 兼容性矩阵](../../rn/using/compatibility-matrix.md)中了解详情。

**已弃用的功能**

在 20.3 中弃用了以下功能：

* 弃用了用于将受众导入和导出到 Adobe Experience Cloud 的 demdex 域。如果您是将 demdex 域用于导入/导出外部帐户，则需要相应地调整实施。[了解详情](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* 最初基于 oAUTH 身份验证设置来访问管道的 Triggers 集成身份验证现已更改并移至 Adobe I/O。[了解详情](../../integrations/using/configuring-adobe-io.md)

在[已弃用和已删除的功能页面](../../rn/using/deprecated-features.md)中了解详情。

**改进**

* 已对&#x200B;**客户端控制台**&#x200B;进行多项改进。
   * 连接协议已经更新，以遵循新的 IMS 认证机制。必须升级服务器和客户端控制台，才能在2021年6月30日之后连接。
   * 为防止与某些互联网安全 GPO 规则限制不兼容，Campaign 客户端控制台登录屏幕已替换为内置标准 Windows 表单。
   * 修复了使用 64 位客户端控制台在工作流中复制/粘贴活动时的问题。(NEO-27635)
   * 在&#x200B;**关于**&#x200B;菜单中，已添加信息来区分 64 位和 32 位控制台。
* 现在，在恢复工作流时，日志中会显示工作流标识符，这使您能够更好地识别已恢复的工作流。
* 已引入新的永久 cookie：nllastdelid。此 cookie（UUID230 除外）将存储 deliveryId。当会话 cookie 不存在时，将从此 cookie 中存在的 deliveryId 获取 broadlog 信息。
此更改修复了浏览器会话结束时发生的问题：包含 deliveryId 和 broadlogId 的会话 cookie 遭到删除。如果没有 deliveryId，则在永久跟踪（最后投放）的情况下找不到 broadlog 信息，并会缺少跟踪表信息。
在[此部分](../../platform/using/privacy-and-recommendations.md#cookies)中了解有关 cookie 的详情。
* 通过在投放发送之前重新启动 MTA 进程，改进了可交付性服务器的大量投放吞吐量性能。

**其他变更**

* 对 SFTP 使用相对路径时，不再自动添加 `~/` 字符。如果需要，您可以手动将 `~/` 字符添加到路径中，但是 Adobe 建议使用绝&#x200B;**绝对路径**。
* 在使用 Microsoft SQL Server 配置新数据库时，已从可用身份验证方法中删除 Windows NT 身份验证。[阅读更多](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* 为了提高性能，已针对 Teradata 优化了数据库清理工作流。(NEO-19959)
* 改进了从 Adobe Target 插入图像时显示的错误消息，并且外部帐户中的租户名称为空。
* 在投放属性中，**[!UICONTROL Archive emails]** 选项已重命名为 **[!UICONTROL Email BCC]**。
* 为了提高稳健性，现在拒绝对无效节点执行 selectAll 查询。如果需要禁用检查并恢复先前行为，可将 XtkSecurity_Disable_QueryCheck 设置为 0。

**技术演进**

Tomcat 已从版本 7 (7.0.103) 更新到版本 8 (8.5.57)。

`tomcat-7` 目录替换为 `tomcat-8` 目录。

在 Windows 上，_iis_neolane_setup.vbs_ 和 _apache_neolane.conf_ 现在安装在 `conf` 目录（而非先前的 `tomcat-7/conf`）中。

在 Linux 上，_apache_neolane.conf_ 现在安装在 `conf` 目录中。

**修补程序**

* 修复了可能阻止重新计算投放统计信息的问题。
* 修复了在使用 Campaign Classic 9080 内部版本（已连接到使用更低内部版本的服务器）上传 CSV 文件时显示错误消息的问题。(NEO-23218)
* 修复了在为外部帐户配置 Microsoft Dynamics CRM 向导时可能显示错误消息的问题。这是由于与最新的 MS Dynamics CRM API 版本存在兼容性问题。(NEO-24528)
* 修复了阻止使用 CRM 连接器将查找类型记录（即，由与其他表连接的外键记录组成的数据）从 Campaign Classic 导出到 Microsoft Dynamics 的问题。(NEO-23864)
* 修复了在 CRM 连接器中启用&#x200B;**自动索引**&#x200B;选项时可能会阻止获取 Microsoft Dynamics 数据的问题。(NEO-25981)
* 修复了 IMS 身份验证问题，该问题可能导致连接即使结束也处于打开状态。现在，已终止的连接在结束后就将自动关闭，以避免累积连接并消耗系统资源。(NEO-25996)
* 修复了由于外部帐户配置错误（帐户或密码不正确）而导致用于投放的 Adobe Experience Manager 内容同步失败时未显示错误消息的问题。现在，在失败时会显示消息，使您能够更轻松地识别问题。(NEO-25586)
* 修复了在&#x200B;**更新数据**&#x200B;活动中选择&#x200B;**更新**&#x200B;操作类型时发生的问题。如果要更新的数据不正确，则工作流将出错并失败。在数据不正确的情况下，工作流将不会失败，并且记录将存储到&#x200B;**拒绝**&#x200B;出站过渡中。(NEO-23794)
* 修复了可能阻止包含子工作流的工作流正常工作的问题。(NEO-24036)
* 修复了在编辑活动模板描述时的问题，该问题会在复制粘贴符号（例如日语字符）时阻止显示&#x200B;**保存**&#x200B;按钮。(NEO-27071)
* 修复了可能会阻止您在实例配置向导中更改跟踪服务器的问题。
* 修复了在单击&#x200B;**保存**&#x200B;按钮之前单击窗口外部时阻止保存活动或活动模板的描述的问题。(NEO-27449)
* 修复了可能会阻止&#x200B;**有效付费用户档案数** (billingActiveContactCount) 技术工作流正常工作的问题。如果已对模式扩展中的计算字段执行了链接，则可能会发生这种情况。已创建大量数据，这可能导致数据库耗尽临时空间。(NEO-24062)
* 修复了&#x200B;**数据加载（文件）**&#x200B;活动的问题，该问题可能会阻止您从 txt 和 csv 文件导入日语字符（如果这些字符位于文件末尾）。(NEO-24957)
* 修复了连续投放的问题，该问题可能会阻止正确填充&#x200B;**已启动分析**&#x200B;和&#x200B;**已完成分析**&#x200B;字段。(NEO-20755)
* 修复了在查询除&#x200B;**收件人** (nms:recipient) 以外的其他模式后尝试预览 SMS 消息时可能显示错误消息的问题。(NEO-27517)
* 修复了使用 Snowflake FDA 连接器时的问题。具有 Snowflake FDA 访问名称权限的用户无法对 Snowflake 模式执行查询。日志中显示了类型为“Password not found”的错误。(NEO-23851)
* 修复了使用 FDA 连接器时的问题，当链接的 FDA 模式名称是当前模式的元素名称的子字符串时会发生该问题。例如，如果 FDA 模式为“cust”，而收件人模式中的其中一个元素为“customer”，则会发生这种情况。在提取“customer”元素中的列并从“cust”FDA 模式添加列时，缺少本地列的值。(NEO-20193)
* 修复了从外部数据库获取记录并在 Campaign 活动库中插入这些记录时工作流中的问题。(NEO-26359)
* 修复了&#x200B;**更新事件状态**&#x200B;技术工作流中的问题：为了与&#x200B;**投放统计**&#x200B;活动中传入的对应字段的大小匹配，**更新投放统计**&#x200B;活动中三个目标字段的大小已从 32 位更改为 64 位。(NEO-11557) 在&#x200B;**此部分**&#x200B;中了解有关[更新事件状态作](../../workflow/using/about-technical-workflows.md)工作流的详情。
* 修复了&#x200B;**消息中心事件历史记录**&#x200B;报告中的问题，该问题在尝试应用过滤器时导致脚本错误并造成无法按日期范围过滤。(NEO-23365)
* 修复了 **Campaign 作业** (operationMgt) 与&#x200B;**预览** (forecasting) 技术工作流之间的干扰问题。当计划投放处于“目标就绪”或“准备投放”状态时，会发生这种情况。(NEO-20819)
* 修复了 xtkOperator 中的 mdata 字段内不存在 XML 标识符时的 XML 解析问题。它导致升级后故障。(NEO-26113)
* 修复了使用&#x200B;**文件传输**&#x200B;活动时的问题，该活动链接到在 SSL 中加密的 Azure 外部帐户，其中使用 HTTP 而不是 HTTPS 建立连接。(NEO-26720)
* 修复了在清理工作流期间 up_updatestats 过程可能发生错误的 MSSQL 数据库问题。
* 修复了在 Web 进程关闭期间发生的崩溃（如果交互请求仍在处理中）。(NEO-26447)
* 修复了在升级 9032 后 Oracle DB 中的 **NoNull** 函数不再工作的问题。(NEO-26488)
* 修复了在升级 9171 后跟踪工作流失败（如果在没有消息中心包的情况下安装了 LINEV2 包）的问题。
* 修复了可伸缩性问题，该问题阻止连接池增加到所需的连接数，因为属性“APP”的数据库连接字符串最终获得无效值。(NEO-25105)
* 修复了代理配置级别上阻止您在最新的 Windows 10 更新后登录 Adobe Campaign 的问题。(NEO-27813)
* 修复了在导入包含跟踪链接的 HTML 模板后，使不需要的 URL 在投放的电子邮件中可见的问题。(NEO-25909)
* 修复了在显示工作流中&#x200B;**拆分**&#x200B;活动的其余目标数据时导致服务器 崩溃的问题。
* 通过防止在清除表达式分析器时内存损坏，修复了服务器崩溃问题。(NEO-26856)
* 修复了非管理员用户定义实例变量的扩充活动中的问题。(NEO-25653)
* 修复了可能阻止将工作流数据导出到FDA数据库的回归(Teradata、Snowflake)。

## 20.2 版{#release-20-2}

### ![](assets/do-not-localize/limited_2.png) 20.2.5 版 - 版本 9188 {#release-20-2-5-build-9188}

_2021 年 4 月 15 日_

* 修复了导致 IMS 连接屏幕上出现持续错误消息的客户端控制台回退问题。 (NEO-34821)

**必须执行仅控制台升级。无需升级服务器。**

>[!NOTE]
>
> 连接到 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html) 以下载新版本。 [在此页面中](../../installation/using/client-console-availability-for-windows.md)了解如何向所有最终用户建议更新控制台。

_2021 年 3 月 31 日_

**改进**

* 已进行改进，以防止无效soap调用发生崩溃。 这可能导致实例在尝试运行特定的复杂查询时停止工作。 (NEO-28796, NEO-30553)
* 修复了由于主机名验证而阻止发送具有TLS的短信投放的回归。 (NEO-29581)
* 修复了导致已签名跟踪链接无法在某些电子邮件客户端上工作的问题。 (NEO-28414, NEO-29615)
* 修复了在使用webApp跟踪标记时可能导致与重复ID冲突的跟踪ID序列。 (NEO-27931)
* 修复了导致每天wfserver重新启动时运行的工作流停止的问题。 (NEO-30047)
* 修复了在尝试同步 Adobe Experience Manager 模板时使用非管理员用户发出的 API 调用的安全问题。(NEO-32389, NEO-23487)
* 修复了在使用模板创建的投放上关闭投放对话框时导致控制台崩溃的问题。 (NEO-31547)
* 修复了在 **定位和工作流** 营销活动的选项卡：预览会失败，并出现以下错误。(NEO-29440)
* 修复了Tomcat 8.5发送无效答案的问题，该问题导致事务性消息日志中出现错误。 (NEO-30858)
* 修复了导致外部线程管理中内存损坏并影响性能的回归问题。
* 修复了在使用自定义目标映射时可能导致计费工作流失败的问题。 自定义架构的主键存储在“sourceId”列中，该列仅允许整数值。 现在，它允许使用整数和字符串值。 (NEO-25914, NEO-28146)
* 修复了导致无法使用某些控制台组件（如投放中的日期选择器和图像管理）的回退问题。(NEO-31453)

### ![](assets/do-not-localize/red_2.png) 20.2.4 版 - 版本 9187 {#release-20-2-4-build-9187}

_2021 年 4 月 15 日_

* 修复了导致 IMS 连接屏幕上出现持续错误消息的客户端控制台回退问题。 (NEO-34821)
* 修复了导致无法使用某些控制台组件（如投放中的日期选择器和图像管理）的回退问题。(NEO-31453, NEO-31454)

**必须执行仅控制台升级。无需升级服务器。**

>[!NOTE]
>
> 连接到 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下载新版本。 [在此页面中](../../installation/using/client-console-availability-for-windows.md)了解如何向所有最终用户建议更新控制台。

_2020 年 12 月 22 日_

>[!CAUTION]
>
> * 此版本附带新的连接协议：如果您是通过 Adobe Identity Service (IMS) 连接到 Campaign，则 Campaign 服务器和客户端控制台都必须升级，这样才能在&#x200B;**2021 年 6 月 30 日**&#x200B;之后连接到 Campaign。[了解详情](../../technotes/using/ims-updates.md)
> * 此版本附带[安全修复](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：必须升级以增强环境安全性。
> * 如果您是通过 oAuth 身份验证使用 Experience Cloud Triggers 集成，则需要按照[此页面](../../integrations/using/configuring-adobe-io.md)中的说明移至 Adobe I/O。Campaign的旧版oAuth身份验证模式 [已经退休了](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) on **2021年9月**. 在扩展之前，托管环境将从扩展中受益  **2022年2月23日**. 作为内部部署或混合型客户，请联系Adobe客户关怀团队，将支持延长至2022年2月。 您必须向 Adobe 提供 [OAuth 应用程序的 AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)。


**改进**

* 连接协议已经更新，以遵循新的 IMS 认证机制。
* 最初基于oAUTH身份验证设置来访问管道的Triggers集成身份验证已更改并移至Adobe I/O。 [了解更多](../../integrations/using/configuring-adobe-io.md)
* [终止支持 iOS APN 旧版二进制协议](https://developer.apple.com/news/?id=c88acm2b)之后，在升级后期间，所有使用此协议的实例都更新为 HTTP/2 协议。
* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)
* 修复了在发生连接错误后导致SMPP连接器停用、阻止发送其他短信投放并导致性能问题的问题。 (NEO-28609)
* 通过防止在清除表达式分析器时内存损坏，修复了服务器崩溃问题。(NEO-26856)
* 修复了在显示工作流中&#x200B;**拆分**&#x200B;活动的其余目标数据时导致服务器 崩溃的问题。
* 修复了在查询除&#x200B;**收件人** (nms:recipient) 以外的其他模式后尝试预览 SMS 消息时可能显示错误消息的问题。(NEO-27517)
* 修复了在发出具有主机名中明确定义的端口号的HTTPS连接请求时，调用失败并出现证书错误的问题。 (NEO-29146)
* 修复了POSIX线程管理中在营销实例上生成大型核心转储文件的问题。 (NEO-28117, NEO-29281)
* 修复了在准备投放或定期投放预览时可能导致Web进程崩溃的问题。 (NEO-27790, NEO-27517)
* 修复了由非管理员操作员触发时，导致投放或校样发送失败的问题。 (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **新控制面板 10 月版**，其中使用 CNAME 进行域配置并新增数据库监视功能。[了解详情](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=zh-Hans)。

### ![](assets/do-not-localize/red_2.png) 20.2.3 版 - 版本 9182 {#release-20-2-3-build-9182}

_2020 年 9 月 11 日_

* 修复了由于投放部分的单个错误函数造成内存过载而导致阻止投放准备的回归。(NEO-27346)
* 修复了在重新发布 Web 应用程序之前关闭 Apache 和 Web 服务器的升级后问题。(NEO-27155)
* 修复了由于选项卡的解释错误，导致跟踪URL变得可见的HTML模板管理回归。 (NEO-25909)
* 修复了由于非托管数据源而导致数据库清理工作流可能失败的问题。(NEO-23160, NEO-23364)
* 清理工作流现在按 100 批而不是逐批清除过期列表。
* 修复了阻止修改外部帐户的内部名称的回归。(NEO-27323)
* 修复了在升级后期导致 nlserver 启动错误的回归（错误日志）。
* 改进了共享内存的更新管理。不再需要 20.2 中必需的其他步骤。

### ![](assets/do-not-localize/red_2.png) 20.2.2 版 - 版本 9180 {#release-20-2-2-build-9180}

_2020 年 7 月 22 日_

* 修复了在禁用签名功能时跟踪无法正常工作的问题。(NEO-26411)
* 修复了导致在应当允许个性化域中的未签名链接时将其阻止的问题。(NEO-25210)
* 修复了在使用某些旧版 Outlook 时可能导致无法打开/单击跟踪 URL 的问题。  (NEO-25688)
* 修复了导致在电子邮件投放中错误定义镜像页面 URL 的问题（由于 ASCII 字符控制不当）。(NEO-26084)
* 修复了反网络钓鱼服务中的 URL 管理编码问题。(NEO-25283)
* 修复了在使用个性化参数（带井号的锚点标记）中的片段跟踪 URL 时无法正常工作的问题。(NEO-25774)
* 修复了使用特定自定义跟踪公式时的跟踪问题。(NEO-25277)
* 修复了跟踪“通知点击量”无法正常工作的问题（iOS 和 Android 推送通知）。(NEO-25965)
* 修复了由于工作流中的计算字段受影响而导致该工作流失败的回归。(NEO-25194)
* 修复了阻止动态创建 Web 跟踪 URL 正常工作的回归。(NEO-20999)
* 修复了现成投放报告在导出到 PDF 时似乎已截断的回归问题。(NEO-25757)
* 修复了部署向导中的崩溃问题。
* 修复了在升级后可能阻止优惠通知工作流正常工作的问题。
* iOS HTTP2 连接器已得到改进（第三方更新和错误管理）。(NEO-25904, NEO-25903)
* 更新了 catalina.properties 中的 jarToSkip 列表，以删除对不再使用的 jar 文件（iOS 通知）的引用。
* 修复了在升级后阻止投放准备的问题。
* 在切换到[新序列 ID 机制](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)后，所有更新收件人表的 Web 应用程序都会在升级后期间重新发布。
* 修复了投放内容中的潜在 XSS 漏洞。(NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **新的控制面板 6 月版本**，包含活动用户档案监测、子域投放能力审核和 GPG 密钥管理。[了解详情](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html)。

### ![](assets/do-not-localize/red_2.png) 20.2.1 版 - 版本 9178 {#release-20-2-1-build-9178}

_2020 年 6 月 8 日_

**新增内容？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>支持表情符号</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>在 Campaign 中设计邮件时，您现在可以使用专用按钮在邮件正文中轻松插入表情符号。还可以在电子邮件主题行中添加这些表情符号。您可以自定义界面中可用表情符号的列表。</p>
    <p>有关添加表情符号的详细信息，请参阅 <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">详细文档</a>。在<a href="../../delivery/using/customizing-emoticon-list.md">本部分</a>中了解如何自定义表情符号列表。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA 连接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>您现在可以将 Campaign 实例连接到 Azure Synapse 外部数据库。此连接通过新的外部帐户管理。</p>
    <p>Azure Synapse 仅适用于混合和内部部署环境。有关详细信息，请参阅<a href="../../installation/using/configure-fda-synapse.md">详细文档</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>泰国和巴西隐私法</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>泰国的《个人数据保护法》(PDPA) 是一项新的隐私法，旨在协调泰国的数据保护要求并使之现代化。 </p>
   <p>巴西的《通用数据保护法》(LGPD) 将从 2021 年初生效，适用于巴西境内所有收集或处理个人数据的公司。</p>
   <p>这些法规适用于为居住在这些国家/地区的数据主体持有数据的 Adobe Campaign 客户。除了 Campaign 中已有的隐私权功能（包括同意管理、数据保留设置和用户角色），我们还将利用此机会加入其他功能，以帮助您做好 PDPA 和 LGPD 的准备：</p>
   <ul> 
     <li><p>访问权和删除权：我们正在努力利用为 GDPR 和 CCPA 添加的功能。<a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html">阅读更多</a></p></li> 
     <li> <p>在使用 Campaign 接口或 API 创建隐私请求时，您现在可以选择<strong>法规</strong>类型：PDPA、LGPD、GDPR、CCPA。<a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">阅读更多</a>。</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 默认情况下，为所有客户启用了跟踪电子邮件中链接的安全性。另外还提供了增强的安全功能，可通过联系客户服务中心来启用此功能。有关此功能及非托管客户启用此功能的步骤的更多详细信息，请参阅[安全和隐私检查列表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)。(NEO-24232)

* 为了优化安全性，已通过 sha256 增强了用于生成文件名的 MD5 哈希算法，以用于公共文件上传。(NEO-17044)

* 为了增强针对 XSS 攻击的安全性，在执行镜像页面时禁用客户端脚本。(NEO-17987)

* 修复了阻止&#x200B;**隐私请求清理**&#x200B;技术工作流删除对帐数据的问题。(NEO-25168, NEO-21004)

* 修复了&#x200B;**文件传输**&#x200B;活动的问题，该问题导致基于 SFTP 密钥的身份验证无法在 Debian 9 上工作。(NEO-23183)

**兼容性增强**

Campaign 现在支持以下系统：
* 操作系统：Debian 10
* RDBMS：Oracle 18c 和 Oracle 19c
* FDA：Azure Synapse Analytics

请参阅 [Campaign 兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)了解详情。

**改进**

* 事务性消息已得到改进，可提供更好的用户体验。您现在可以取消发布事务性消息模板，这将从执行实例中删除它。[了解详情](../../message-center/using/publishing-message-templates.md#template-unpublication)。

* 新选项可用于设置发送包含图像或附件的电子邮件时的限制。这些限制可以避免性能问题，这对于事务性消息尤为有用。[阅读更多](../../installation/using/configuring-campaign-options.md#delivery)

* 新的&#x200B;**在数据库中准备投放部分**&#x200B;选项允许直接在数据库中执行投放准备，这可以显著加快分析。此选项仅适用于特定配置。[了解详情](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis)。(NEO-23886)

* Microsoft Dynamics 的 [CRM 连接器活动](../../workflow/using/crm-connector.md)的性能已得到改进。(NEO-13303, NEO-12710)

* 已增加共享内存版本。

   >[!WARNING]
   >
   >执行升级后，此改进需要执行额外的步骤。请参阅下面的&#x200B;**技术演变**&#x200B;部分。

* 清理工作流已得到增强。所有已删除工作流的孤立工作表现也由清理工作流自动删除。[了解详情](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances)。

* 使用 iOS HTTP2 连接器的 iOS 移动应用程序的证书现在将在发送推送通知之前经过验证，从而防止投放因证书过期而失败。

* HTTP 代理连接的管理已得到改进。[了解详情](../../installation/using/file-res-management.md)。

* **[!UICONTROL Javascript Code]**&#x200B;和&#x200B;**[!UICONTROL Advanced Javascript Code]**&#x200B;工作流活动中新增可在达到限制后停止执行的选项。默认值为 1 小时。[了解详情](../../workflow/using/sql-code-and-javascript-code.md#javascript-code)。

**其他更改**

* 现已弃用传统 SMS 连接器。请参阅[已弃用的功能页](../../rn/using/deprecated-features.md)。

* 您不能再使用自己的 Litmus 帐户来配置和使用 Adobe Campaign 中的收件箱呈现。[了解详情](../../delivery/using/inbox-rendering.md)。

* 为了更好地区分视图和文件夹，视图名称的颜色已从深蓝色更改为深青色。[阅读更多](../../platform/using/access-management-folders.md)

* Campaign Classic 现在可以连接到托管在英国、印度和加拿大地区的 Microsoft Dynamics CRM 帐户。这适用于 Office 365 和内部部署 (Dynamics 2015) 部署类型。

* Campaign 现在执行 TLS 验证来检查服务器的主机名是否与提供的证书中的主机名匹配。

* 投放和跟踪统计信息表现在为 SMS 渠道的每个投放显示一个条目，而不是每个投放收件人显示一个条目。

* 在日志文件中添加了一条错误消息，用于当下载的文件大于磁盘空间时警告用户。

* Snowflake 连接器现在提供以下功能：MonthsAgo、DaysAgoInt、ToDateTime、YearsAgo

**技术演进**

此新版本更新了共享内存，并需要执行其他步骤来进行升级。作为 Campaign 管理员，您需要删除内存区段。这些步骤是必需的，因为旧区段将阻止 nlserver/nlsrvmod 启动。

在 Windows 上，需要重新启动系统。

在 Debian/CentOs 上，需要删除共享内存。以下是步骤：

在升级之前，您需要执行以下步骤：

1. 如果 apache2（CentOS 上的 http2）服务正在运行，请停止该服务。
1. 如果 nlserver（旧版本为 nlserver6）服务正在运行，请停止该服务。

升级后：

1. 如果版本比当前版本旧，请使用 **ipcrm** 命令删除共享内存。
1. 启动 nlserver 服务（如果它正在运行）。
1. 启动 apache2 服务（如果它正在运行）。

下面是 Debian 的命令行：

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

[本页](../../configuration/using/additional-parameters.md#redirection-server-configuration)提供 Linux 的示例。

**修补程序**

* 修复了清理工作流日志中的次要回归。
* 修复了解析 WSDL 文件时工作流&#x200B;**加载 (SOAP)** 活动中的问题。
* 修复了使用&#x200B;**调查**&#x200B;活动升级多个工作流以高效处理大量工作流时导致错误的问题。
* 修复了处理来自增强型 MTA 的 inMail 邮件时的间歇性连接问题。(NEO-20380)
* 修复了在 HTML 中以 100% 宽度显示图像时，热点单击百分比无法正确显示的问题。(NEO-23203)
* 修复了导致投放的条件内容无法在热点单击报告中完全显示的问题。(NEO-18729)
* 修复了在恢复工作流以发送重复投放时跳过目标批准步骤的问题。(NEO-18166)
* 修复了在工作流中修复错误后，**重新启动邮件准备**&#x200B;按钮无法恢复投放的问题。(NEO-13488)
* 修复了在启动阶段的中间源模式下，目标包含的收件人为日语电子邮件格式时，可能导致投放失败的问题。(NEO-23846)
* 修复了 Snowflake 连接器的时区转换问题 (NEO-20105)
* 修复了外部帐户使用 FTP over SSL 时的问题。(NEO-20498)
* 修复了可能会导致图像无法在 Line 投放中显示的问题。(NEO-23207)
* 修复了在发布优惠时导致错误的问题。(NEO-23312)
* 修复了推送通知的问题，该问题导致即使证书已过期，测试连接也能在移动应用程序中工作。(NEO-22991)
* 修复了在以高频率发送时可能影响推送通知的问题。(NEO-20516)
* 修复了导致跟踪数据包含重复的问题，即使跟踪日志没有。(NEO-20040)
* 修复了在解决跟踪服务器通信失败后导致发送重复事务电子邮件的问题。(NEO-23640)
* 修复了从跟踪 URL 重定向时删除编码参数值的问题（影响日语字符）。(NEO-25637)
* 修复了在比较浮点数时查询无法工作的问题。(NEO-23243)
* 修复了在重新启动工作流后，**修改者**&#x200B;列内容无法显示的问题。(NEO-23035)
* 修复了从第二个容器下载日志时导致跟踪技术工作流失败的问题。(NEO-23159)
* 修复了在运行&#x200B;**扩充**&#x200B;活动时可能导致工作流失败的问题。(NEO-17338)
* 已向&#x200B;**重复数据删除**&#x200B;工作流活动中的&#x200B;**要保持的重复项**&#x200B;添加检查，以防输入空值或负值。
* 已从循环的活动删除&#x200B;**调度程序向导**，以避免提及小时和分钟数。只考虑日期。
* 修复了通过&#x200B;**脚本**&#x200B;工作流活动中的&#x200B;**由脚本计算**&#x200B;选项创建投放时，其他活动字段存在的一个问题。(NEO-20609)
* 修复了导致无法在数据库清理任务中删除幽灵工作流的问题。
* 修复了导致&#x200B;**计费（活动用户档案）**&#x200B;技术工作流失败的问题。(NEO-19777)
* 修复了使用 ACS 连接器功能时阻止连接到 Campaign Standard 实例的回归问题（FOH/FOH2 连接管理不正确）。(NEO-23433)
* 修复了导致无法在 Hadoop 表中多列的主键上创建模式扩展的问题。(NEO-17390)
* 修复了可能导致无法从 URL 加载 WSDL 文件的&#x200B;**加载 (SOAP)**&#x200B;活动中的一个问题。(NEO-16924)
* 修复了在负载平衡多个活动工作流服务器时，导致无法执行&#x200B;**无条件停止**&#x200B;的问题。(NEO-19556)
* 修复了导致清理工作流崩溃的回归。
* 修复了在执行实例上发布模板时可能发生的问题。
* 修复了可能阻止 collectPrivacyRequests 技术工作流运行的问题。(NEO-20513, NEO-25169)
* 修复了在升级到内部版本9080后尝试连接到Audience Manager时可能发生的问题。 (NEO-20511, NEO-25167)
* 修复了以 PDF 或 XLS 格式导出报表时可能出现的问题。(NEO-20982、NEO-23493、NEO-23348)
* 修复了在发送投放列表后，将投放显示两次的问题。
* 修复了投放准备问题，该问题在将路由配置设置为通过中间源发送投放时可能发生。
* 修复了在单击 Line 邮件中的 Web 应用程序链接时可能显示错误邮件的问题。
* 修复了在运行清理工作流后删除&#x200B;**增量查询**&#x200B;活动历史记录的问题。
* 修复了创建中间源外部帐户时缺少 NmsMidSourcing_LastBroadLog_&lt;InternalName> 选项的问题。
* 修复了数据库连接上的导致 Web 服务器由于数据库编码问题而不断重新启动的回归问题。这可能会造成过度使用。(NEO-23264)


## 20.1 版{#release-20-1}

### ![](assets/do-not-localize/limited_2.png) 20.1.4 版 - 版本 9126 {#release-20-1-4-build-9126}

_2021 年 4 月 15 日_

* 修复了导致 IMS 连接屏幕上出现持续错误消息的客户端控制台回退问题。 (NEO-34821)

**必须执行仅控制台升级。无需升级服务器。**

>[!NOTE]
>
> 连接到 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下载新版本。 [在此页面中](../../installation/using/client-console-availability-for-windows.md)了解如何向所有最终用户建议更新控制台。

_2021 年 3 月 22 日_

* 修复了导致无法使用某些控制台组件（如投放中的日期选择器和图像管理）的回退问题。(NEO-31453, NEO-31454)

**必须执行仅控制台升级。无需升级服务器。**

>[!NOTE]
>
> 连接到 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下载新版本。 [在此页面中](../../installation/using/client-console-availability-for-windows.md)了解如何向所有最终用户建议更新控制台。

_2020 年 12 月 23 日_

>[!CAUTION]
>
> * 此版本附带新的连接协议：如果您是通过 Adobe Identity Service (IMS) 连接到 Campaign，则 Campaign 服务器和客户端控制台都必须升级，这样才能在&#x200B;**2021 年 6 月 30 日**&#x200B;之后连接到 Campaign。[了解详情](../../technotes/using/ims-updates.md)
>
> * 此版本附带[安全修复](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：必须升级以增强环境安全性。


* 连接协议已经更新，以遵循新的 IMS 认证机制。
* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)

### ![](assets/do-not-localize/red_2.png) 20.1.3 版 - 版本 9124{#release-20-1-3-build-9124}

_2020年5月6日_

* 修复了&#x200B;**文件传输**&#x200B;活动的问题，该问题导致基于 SFTP 密钥的身份验证无法在 Debian 9 上工作。(NEO-23183)

### ![](assets/do-not-localize/red_2.png) 20.1.2 版 - 版本 9123{#release-20-1-2-build-9123}

_2020 年 3 月 13 日_

* 修复了阻止在Red Hat 7服务器上部署版本的问题。 (NEO-23332)

### ![](assets/do-not-localize/red_2.png) 20.1 版 - 版本 9122{#release-20-1-build-9122}

_2020年2月17日_

**新增功能**

<table> 
 <thead> 
  <tr> 
   <th> <strong>SnowflakeFDA连接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake是一个完全托管的云data warehouse，旨在在存储和计算级别进行扩展。 借助这款新连接器，Adobe Campaign现在可以利用Snowflake的强大功能执行大数据分段。 此连接器可供所有客户使用，包括由Adobe托管。</p>
    <p>有关更多信息，请参阅 <a href="../../installation/using/configure-fda-snowflake.md">详细文档</a> 和 <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">教程视频</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>HadoopFDA连接器增强</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>hadoopFDA连接器已得到改进，可支持Hadoop3.0和Cloudera。</p>
    <p>有关更多信息，请参阅<a href="../../installation/using/configure-fda-hadoop.md">详细文档</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 改进了报表配置中的安全性，以防止Clickjacking。 这适用于新报表。 对于旧报表，您需要重新发布这些报表以应用更改。 (NEO-13282)

* 修复了cryptString中的小内存问题。 (NEO-20071)

* 改进了监视器JSP以修复内部IP泄漏。 (NEO-16821)

* 修复了可向非管理员用户显示堆栈跟踪信息的问题。 (NEO-12388)

* 改进了对以前会话中缓存数据的管理。 (NEO-17039)

* 修复了导致logins.log文件无法通过IMS记录成功登录尝试的问题。 (NEO-11004)

**改进**

* iOS 13现在支持HTTP2连接器。

* 改进了推送通知功能（nms:address和nms:appSubscriptionRcp）所使用的表的隔离管理和清理。 对于iOS（仅限HTTP2连接器），禁用的令牌现在处理方式与Android相同。 现在，在NmsAppSubscriptionRcp表中设置了禁用标志。 [了解更多信息](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* 在 **JavaScript代码** 和 **高级JavaScript代码** 工作流活动以定义超时期限。 这可防止JavaScript执行阶段运行过长。 如果超时期间已过，工作流将停止。 默认超时为1小时。 [了解更多信息](../../workflow/using/sql-code-and-javascript-code.md)

* 现在，在中间源服务器上找不到匹配的亲和度时，将停止投放分析，并显示相应的错误消息。

* 现在支持Postgres的数据库故障切换：现在，当数据库服务器崩溃并重新启动时，Campaign会自动重新连接到该服务器。

* 的 **开始挂起** 视图已添加到“管理”>“审核”>“工作流状态”节点。 这样，您就可以监控实例上等待启动的所有工作流 **operationMgt** 进程。 此视图随营销活动包一起提供。 [了解更多信息](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**其他变更**

* 在Linux上，nlserver服务启动现在使用系统单元，而不是/etc/init.d/nlserver6脚本。 安装20.1程序包时，将自动执行到新启动方案的迁移。 /etc/init.d/nlserver6仍然提供，但是为了与nlserver服务（启动、重新启动、停止等）进行交互，我们建议您直接使用systemctl命令。

* 最耗时的自定义表已从 **xtkNewId** 序列。 [了解更多信息](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* 改进了查询性能，这些性能可能会受到不必要的数据库连接的影响。

* 改进了数据库更新向导的性能，以减少SQL语句的数量，从而优化响应时间。

* 数据库记录管理已得到增强。

* 连接池的稳健性已得到改进，这可能防止意外连接失败的发生频率过高。

* 电子邮件地址验证规则，用于在发生软错误时将地址添加到隔离。 [了解更多信息](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* 对于Debian，Campaign现在使用系统PCRE库（当它们可用时）。

* Campaign现在允许使用更新的系统ODBC库。

* 在打开连接以加载富图像时，已向LINE servlet添加超时。 如果图像加载时间过长，则Servlet会停止连接以避免瓶颈。

**修补程序**

* 修复了使用Hadoop连接器时的帐户密钥加密问题。

* 修复了由于实施SSL认证而导致Windows服务器上用户连接失败的回归问题。 (NEO-20629)

* 修复了当工作流ID为负时，增量查询活动存在的问题。 (NEO-19779)

* 修复了通过NetezzaFDA连接器运行查询时的编码问题。 (NEO-19594)

* 修复了在 **Web下载** 工作流事件活动。

* 修复了生成优惠建议时出现的问题。 (NEO-18176)

* 修复了使用客户获取Web表单模板时的页脚显示问题。

* 修复了解析连续投放内容中的URL时可能导致崩溃的问题。 (NEO-16910)

* 修复了 **开始** 和 **结束** 创建新营销活动时不计算的字段。

* 修复了 **文件下载** 工作流活动。

* 修复了在报表的查询活动中预览导入的列表时的问题。 (NEO-13119)

* 修复了在选择 **由Campaign提供支持** 电子邮件编辑器中的个性化块。

* 客户端与服务器之间的网络通信已得到改进。

* 修复了在同一营销活动中创建的工作流过多的问题。 现在，您无法创建28个以上的工作流。 将显示警告。

* 修复了在使用 **列选择** 协调选项 **并集** 工作流活动。

* 修复了在工作流中使用损坏的扩充列表时可能发生的控制台崩溃问题。 (NEO-18096)

* 修复了工作流中可能发生的各种控制台崩溃问题(NEO-18010、NEO-18032)

* 修复了允许执行 **外部信号** 工作流活动，即使该活动处于禁用状态。 (NEO-17524)

* 修复了创建新架构时的问题。

* 修复了发送短信消息时的跟踪问题。 (NEO-19595)

* 修复了投放指示器中显示错误的目标受众数量的问题。

* 修复了在通过工作流活动生成描述性报表时显示错误百分比的问题。 (NEO-14314)

* 修复了在时间视图参数下使投放吞吐量报表显示不同数字的问题。 (NEO-11783)

* 修复了阻止跟踪工作流更新事务型消息跟踪指示器的问题。 (NEO-17770)

* 修复了在通过SOAP请求选件时导致Web进程崩溃并重新启动的回归问题。 (NEO-19482)

* 修复了上载目录是远程共享位置时无法将数据上载到公共资源的问题。 (NEO-19361)

* 修复了导致 **从Adobe Experience Cloud导入受众** 技术工作流程经常失败。 (NEO-18463)

* 修复了使用从Experience Manager导入的模板时无法发送投放的问题。 (NEO-17540)

* 修复了在升级到构建9032并阻止实例通过SSL协议连接到FTP服务器后发生的问题。 (NEO-20498)

* 修复了在删除、插入或更新 **更新数据** 活动，使用FDA模式作为定向维度。 (NEO-13280)

* 修复了在HTML内容标记外部存在Javascript代码时无法发送电子邮件的问题。 (NEO-18628)

* 修复了在尝试从已发送消息的投放日志显示镜像页面时发生的问题。 (NEO-17976)

* 修复了阻止 **链接到镜像页面** 个性化块 **文本内容** 选项卡 **导入HTML** 投放。 (NEO-17568)

* 澄清了单击指向已过期镜像页面的链接时显示的错误消息。 (NEO-17340)

* 修复了导致某些按钮无法在 **数据分发** 创建屏幕。

* 修复了在以亚洲/加尔各答为时区的实例中计划投放活动时发生的问题。 (NEO-20001)

* 现在，当投放存在亲和度配置问题时，会显示错误。

* 修复了 **关于** 菜单。

* 修复了尝试从工作流中定期投放的属性更新路由帐户时发生的问题。 (NEO-18684)

* 修复了在通过重定向模块连接到实例时发生的问题，该问题会在关闭后阻止正确清理连接。
