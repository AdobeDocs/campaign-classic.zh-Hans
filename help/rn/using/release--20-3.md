---
product: campaign
title: Campaign 20.3发行说明
description: Campaign 20.3发行说明
feature: Overview
role: User
level: Beginner
exl-id: e927b7fc-95cd-4e08-bab7-ceeb6e67c265
source-git-commit: 01f91abe127629e2d3d0889172969f2f4ba09f46
workflow-type: tm+mt
source-wordcount: '2006'
ht-degree: 95%

---

# 20.3 版{#release-20-3}

![](../../assets/v7-only.svg)

## ![](assets/do-not-localize/red_2.png) 20.3.3 版 - 内部版本 9234 {#release-20-3-3-build-9234}

_2021年1月11日_

* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)
* 修复了与 broadlog 生成过程相关的回归问题，该问题可能导致 MTA 进程崩溃。

## ![](assets/do-not-localize/red_2.png) 20.3.1 版 - 内部版本 9228 {#release-20-3-1-build-9228}

_2020 年 10 月 27 日_

>[!CAUTION]
>
> * 此版本附带新的连接协议：如果您是通过 Adobe Identity Service (IMS) 连接到 Campaign，则 Campaign 服务器和客户端控制台都必须升级，这样才能在&#x200B;**2021 年 6 月 30 日**&#x200B;之后连接到 Campaign。[了解详情](../../technotes/using/ims-updates.md)
> * 此版本附带[安全修复](https://helpx.adobe.com/cn/security/products/campaign/apsb21-04.html)：必须升级以增强环境安全性。
> * 如果您是通过 oAuth 身份验证使用 Experience Cloud Triggers 集成，则需要按照[此页面](../../integrations/using/configuring-adobe-io.md)中的说明移至 Adobe I/O。Campaign [的旧版oAuth身份验证模式已在&#x200B;**2021年8月18日**&#x200B;停用](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。 托管环境将从扩展中受益，直到2021年11月30日&#x200B;**。**&#x200B;作为内部部署或混合型客户，请联系Adobe客户关怀团队，将支持延长至2021年11月30日。 您必须提供[OAuth应用程序](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)的AppID才能Adobe。


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
* 修复了可能阻止将工作流数据导出到FDA数据库的回归(Teradate、Snowflake)。
