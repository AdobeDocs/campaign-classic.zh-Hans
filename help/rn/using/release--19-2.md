---
product: campaign
title: 19.2 版
description: Campaign 19.2发行说明
exl-id: 3c529e4e-8787-41d2-b85d-3feaa5432196
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '1537'
ht-degree: 21%

---

# 19.2 版{#release-19-2}

![](../../assets/v7-only.svg)

## ![](assets/do-not-localize/limited_2.png) 19.2.4 版 - 版本 9082 {#release-19-2-4-build-9082}

_2021 年 4 月 15 日_

* 修复了导致 IMS 连接屏幕上出现持续错误消息的客户端控制台回退问题。 (NEO-34821)

**必须执行仅控制台升级。无需升级服务器。**

>[!NOTE]
>
> 连接到 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html) 以下载新版本。 [在此页面中](../../installation/using/client-console-availability-for-windows.md)了解如何向所有最终用户建议更新控制台。

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
> * 此版本附带[安全修复](https://helpx.adobe.com/cn/security/products/campaign/apsb21-04.html)：必须升级以增强环境安全性。



* 连接协议已经更新，以遵循新的 IMS 认证机制。
* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)

## ![](assets/do-not-localize/red_2.png) 19.2.3 版 - 版本 9081 {#release-19-2-3-build-9081}

_2020年2月7日_

**改进**

* 修复了由于实施SSL认证而导致Windows服务器上用户连接失败的回归问题。 (NEO-20629)
* 修复了 **关于** 菜单。

## ![](assets/do-not-localize/red_2.png) 19.2 版 - 版本 9080 {#release-19-2-build-9080}

_2019 年 12 月 2 日_

**新增功能**

<table> 
 <thead> 
  <tr> 
   <th> <strong>《加州消费者隐私法案》(CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA是加利福尼亚州新推出的隐私法，旨在协调数据保护要求并使之现代化，于2020年1月1日正式生效。 CCPA适用于为居住在加利福尼亚州的数据主体持有数据的Adobe Campaign客户。</p>
    <p>除了已有的可用隐私功能（包括同意管理、数据保留设置和用户角色）之外，Adobe Campaign还可帮助您为CCPA做好准备：</p>
    <ul>
      <li>访问权和删除权：我们将利用为GDPR添加的功能。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">阅读更多</a></li>
      <li>您可以跟踪消费者是否选择退出了出售个人信息。 为此，您需要扩展Profiles表并添加 <strong>选择退出CCPA</strong> 字段。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">阅读更多</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>工作流实时监控</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>您现在可以使用预定义视图监控实例上所有工作流的执行状态。</p>
   <p>有关详细信息，请参阅<a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">有详细说明的文档</a>。</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>使用AMP的交互式内容</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Adobe Campaign让您能够试用新的交互式 <a href="https://amp.dev/about/email/">用于电子邮件的AMP</a> format ，它允许营销人员在邮件中包含AMP组件，以通过可在邮件中直接操作的丰富、动态和交互式内容增强电子邮件体验。</p>
   <p>此功能已作为公共测试版发布。</p>
   <p>有关更多信息，请参阅<a href="../../delivery/using/defining-interactive-content.md">详细文档</a>和<a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">教程视频</a>。</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>安全短信(TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>现在，通过扩展通用SMPP连接器支持安全短信。 这允许与提供商的加密连接。</p> <p><strong>警告</strong> 此功能要求在所有服务器上安装最新的证书。 无效、已吊销或过期的证书将生成影响整体短信发送功能的错误。</p><p>有关详细信息，请参阅<a href="https://helpx.adobe.com/cn/campaign/kb/sms-connector-protocol-and-settings.html">有详细说明的文档</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 修复了Campaign界面中存储的跨站点脚本漏洞 — 输入数据验证和输出编码。 (NEO-16810)
* 修复了配置文件授权的安全问题，该问题可通过加强登录限制策略来允许访问未经授权的数据。 (NEO-14445)

**改进**

* 优化了推送通知的内存消耗。
* 为了优化性能和存储， **logins.log** 文件已得到增强。 现在，该文件可拆分为多个文件，每天一个，最多保留365个文件。 [阅读更多](../../production/using/log-files.md)
* Microsoft Dynamics CRM外部帐户现在可以使用密码凭据（密码+用户名）或证书（私钥）进行配置。 [阅读更多](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* hadoopFDA连接器中添加了一些增强功能，以提高可靠性
* 添加了特定护栏，以在允许在服务器上上传公共资源之前检查磁盘空间。
* 新建 [促销活动选项](../../installation/using/configuring-campaign-options.md) 已添加：
   * 的 **WdbcKillSessionPolicy** 配置选项允许您 **无条件停止** 所有工作流和PostgreSQL数据库查询的行为。
   * 的 **NmsOperation_DeliveryPreparationWindow** 选项，用于定义从运行投放计数中排除状态不一致的投放的天数。
   * 的 **WdbcOptions_TempDbName** 选项用于为Microsoft SQL Server上的工作表配置单独的数据库。 这可以优化备份和复制。 [阅读更多](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * 的 **XtkCleanup_NoStats** 增强了PostgreSQL的选项，以更好地控制数据库清理工作流的存储优化步骤的行为。 [阅读更多](../../production/using/database-cleanup-workflow.md#statistics-update)
* 已向 **logon()** API。 它可以防止在指定时间范围内连续多次失败的登录尝试之后再进行任何登录尝试。
* 新 **最大个性化运行时间** 投放属性中的选项允许您为个性化运行时间定义超时时段，以防止个性化阶段运行过长。 [阅读更多](../../delivery/using/personalization-fields.md#timing-out-personalization)
* 的 **ftp协议** 已添加选项，允许您对SFTP连接使用代理配置。 [阅读更多](../../installation/using/file-res-management.md)
* 新增了对本地环境的SFTP外部服务器的代理访问支持。
* 已添加特定护栏，以阻止安装与Campaign实例不兼容的包。 [阅读更多](../../installation/using/installing-campaign-standard-packages.md)

_已弃用的系统_

以下系统现已 [已弃用](deprecated-features.md) 对于Campaign Classic实施：
* Apache 2.2
* Centos 6

请确保您使用最新Campaign兼容性矩阵中列出的任何系统的受支持版本。 [阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

iOS SDK的版本1.0.26现已可用。 在此新内部版本中，我们添加了对iOS 13的支持。 此新版本现在支持iOS 13推送通知的通知优先级和新注册令牌管理流程。 如果您在以前版本的SDK上运行应用程序，则需要使用新的SDK重新编译您的应用程序。 要获取SDK，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**补丁程序**

* 修复了 **添加链接的表** 字段 **数据加载(RDBMS)** 工作流活动。 (NEO-12213)
* 修复了可能导致中间源服务器无法处理某些消息的问题。 (NEO-12395)
* 修复了对Teradata使用查询分段选项时数据库清理工作流中的问题。 (NEO-12399)
* 修复了包含ne.jp域的分类规则影响投放分析的问题。 (NEO-12609)
* 修复了与通过TLS更新的短信相关的问题，该问题暗含更严格的证书策略。 如果证书过期，这些更新可能会导致营销服务器和中间源服务器之间的连接失败。 (NEO-17698)
* 修复了在使用 **测试连接** 中间源环境中外部帐户的按钮。 (NEO-12722)
* 修复了在FDAHadoop连接中使用日期函数进行查询的问题。 (NEO-12847)
* 修复了在电子邮件编辑器中替换图像时的问题。 (NEO-13098)
* 修复了可能导致已删除或已移动到其他位置的文件夹出现升级后错误的问题。 (NEO-13118)
* 修复了在使用 **按设备屏幕大小定义图像** 选项。 (NEO-13228)
* 修复了 **在投放期间排除重复地址** 选项。 (NEO-13240)
* 修复了使用 **文件传输** 活动，使用 **传输后删除源文件** 选项，名称中包含空格字符。 (NEO-13411)
* 修复了Tomcat缓存清理可能导致内存问题的问题。 (NEO-13456)
* 修复了安装 **具有执行实例的优惠引擎控制** 在Microsoft SQL 2017中运行的现有控制实例上内置的包。 (NEO-13539)
* 修复了在从 **文本内容** 选项卡。 (NEO-13545)
* 修复了中文发件人名称的编码问题。 (NEO-13837)
* 修复了在显示资源管理器中的调查响应数据时可能引发的错误。 (NEO-14590)
* 修复了可能导致投放日志分类与隔离表不一致的问题。 (NEO-16547)
* 修复了DKIM键未嵌入到电子邮件中的问题。 (NEO-16804)
* 修复了在API调用的上下文中使用无效会话令牌来触发事件时显示错误错误代码的问题。 错误代码为“HTTP 200 OK”，而不是“HTTP 403 Forbidden”。 (NEO-16826)
* 修复了通过Web访问显示投放报告时的问题。 (NEO-17015)
* 修复了登录Adobe Campaign时的IMS身份验证问题。 (NEO-17312)
* 修复了阻止隐私管理流程删除隔离电子邮件的问题。 (NEO-17314)
* 修复了使用SQL数据库升级到9031后的吞吐量问题。 (NEO-17558)
* 修复了影响使用Salesforce的CRM连接器的问题。 (NEO-17712)
* 修复了从外部SFTP导入数据时的超时问题。 (NEO-19723)
* 修复了访问预测模型时的问题。 (NEO-19713)
* 修复了影响 **拆分** 使用HadoopFDA数据库进行工作流活动。 (NEO-16636)
* 修复了Oracle上导致某些函数在升级后被视为无效的回归。 (NEO-12759)
