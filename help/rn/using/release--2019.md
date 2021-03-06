---
product: campaign
title: Campaign Classic 2019 版
description: 详细了解 Campaign Classic 2019 版
exl-id: 8a36a542-e095-4208-b624-e59845592863
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '4825'
ht-degree: 24%

---

# 2019 版{#release-2019}

![](../../assets/v7-only.svg)

## 19.2 版{#release-19-2}

### ![](assets/do-not-localize/limited_2.png) 19.2.4 版 - 版本 9082 {#release-19-2-4-build-9082}

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

### ![](assets/do-not-localize/red_2.png) 19.2.3 版 - 版本 9081 {#release-19-2-3-build-9081}

_2020年2月7日_

**改进**

* 修复了由于实施SSL认证而导致Windows服务器上用户连接失败的回归问题。 (NEO-20629)
* 修复了 **关于** 菜单。


### ![](assets/do-not-localize/red_2.png) 19.2 版 - 版本 9080 {#release-19-2-build-9080}

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
      <li>访问权和删除权：我们将利用为GDPR添加的功能。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">了解更多信息</a></li>
      <li>您可以跟踪消费者是否选择退出了出售个人信息。 为此，您需要扩展Profiles表并添加 <strong>选择退出CCPA</strong> 字段。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">了解更多信息</a></li></td> 
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
   <p>有关更多信息，请参阅<a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">详细文档</a>。</p></td> 
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
<td> <p>现在，通过扩展通用SMPP连接器支持安全短信。 这允许与提供商的加密连接。</p> <p><strong>警告</strong> 此功能要求在所有服务器上安装最新的证书。 无效、已吊销或过期的证书将生成影响整体短信发送功能的错误。</p><p>有关更多信息，请参阅<a href="https://helpx.adobe.com/cn/campaign/kb/sms-connector-protocol-and-settings.html">详细文档</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 修复了Campaign界面中存储的跨站点脚本漏洞 — 输入数据验证和输出编码。 (NEO-16810)
* 修复了配置文件授权的安全问题，该问题可通过加强登录限制策略来允许访问未经授权的数据。 (NEO-14445)

**改进**

* 优化了推送通知的内存消耗。
* 为了优化性能和存储， **logins.log** 文件已得到增强。 现在，该文件可拆分为多个文件，每天一个，最多保留365个文件。 [了解更多信息](../../production/using/log-files.md)
* Microsoft Dynamics CRM外部帐户现在可以使用密码凭据（密码+用户名）或证书（私钥）进行配置。 [了解更多信息](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* hadoopFDA连接器中添加了一些增强功能，以提高可靠性
* 添加了特定护栏，以在允许在服务器上上传公共资源之前检查磁盘空间。
* 新建 [促销活动选项](../../installation/using/configuring-campaign-options.md) 已添加：
   * 的 **WdbcKillSessionPolicy** 配置选项允许您 **无条件停止** 所有工作流和PostgreSQL数据库查询的行为。
   * 的 **NmsOperation_DeliveryPreparationWindow** 选项，用于定义从运行投放计数中排除状态不一致的投放的天数。
   * 的 **WdbcOptions_TempDbName** 选项用于为Microsoft SQL Server上的工作表配置单独的数据库。 这可以优化备份和复制。 [了解更多信息](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * 的 **XtkCleanup_NoStats** 增强了PostgreSQL的选项，以更好地控制数据库清理工作流的存储优化步骤的行为。 [了解更多信息](../../production/using/database-cleanup-workflow.md#statistics-update)
* 已向 **logon()** API。 它可以防止在指定时间范围内连续多次失败的登录尝试之后再进行任何登录尝试。
* 新 **最大个性化运行时间** 投放属性中的选项允许您为个性化运行时间定义超时时段，以防止个性化阶段运行过长。 [了解更多信息](../../delivery/using/personalization-fields.md#timing-out-personalization)
* 的 **ftp协议** 已添加选项，允许您对SFTP连接使用代理配置。 [了解更多信息](../../installation/using/file-res-management.md)
* 新增了对本地环境的SFTP外部服务器的代理访问支持。
* 已添加特定护栏，以阻止安装与Campaign实例不兼容的包。 [了解更多信息](../../installation/using/installing-campaign-standard-packages.md)

_已弃用的系统_

以下系统现已 [已弃用](deprecated-features.md) 对于Campaign Classic实施：
* Apache 2.2
* Centos 6

请确保您使用最新Campaign兼容性矩阵中列出的任何系统的受支持版本。 [了解更多信息](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

iOS SDK的版本1.0.26现已可用。 在此新内部版本中，我们添加了对iOS 13的支持。 此新版本现在支持iOS 13推送通知的通知优先级和新注册令牌管理流程。 如果您在以前版本的SDK上运行应用程序，则需要使用新的SDK重新编译您的应用程序。 要获取SDK，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**修补程序**

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


## 19.1 版{#release-19-1}

### ![](assets/do-not-localize/limited_2.png) 19.1.8 版 - 版本 9039 {#release-19-1-8-build-9039}

_2021 年 4 月 15 日_

* 修复了导致 IMS 连接屏幕上出现持续错误消息的客户端控制台回退问题。 (NEO-34821)
* 修复了可能阻止将工作流数据导出到FDA数据库的回归(Teradata、Snowflake)。

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

_2020 年 12 月 16 日_

>[!CAUTION]
>
> * 此版本附带新的连接协议：如果您是通过 Adobe Identity Service (IMS) 连接到 Campaign，则 Campaign 服务器和客户端控制台都必须升级，这样才能在&#x200B;**2021 年 6 月 30 日**&#x200B;之后连接到 Campaign。[了解详情](../../technotes/using/ims-updates.md)
> * 此版本附带[安全修复](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：必须升级以增强环境安全性。
> * 如果您是通过 oAuth 身份验证使用 Experience Cloud Triggers 集成，则需要按照[此页面](../../integrations/using/configuring-adobe-io.md)中的说明移至 Adobe I/O。Campaign 的旧版 oAuth 身份验证模式已于 **2021 年 9 月**[停用](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。托管环境的支持时间可延长至 **2022 年 2 月 23 日**。作为内部部署或混合型客户，请联系Adobe客户关怀团队，将支持期限延长至2022年2月。 您必须向 Adobe 提供 [OAuth 应用程序的 AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)。



**改进**

* 连接协议已经更新，以遵循新的 IMS 认证机制。
* 最初基于oAUTH身份验证设置来访问管道的Triggers集成身份验证已更改并移至Adobe I/O。 [了解更多](../../integrations/using/configuring-adobe-io.md)
* 在 iOS APNs 旧版二进制协议支持结束后，在配置升级期间，使用此协议的所有实例全部更新为 HTTP/2 协议。
* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)
* 修复了在发生连接错误后导致SMPP连接器停用、阻止发送其他短信投放并导致性能问题的问题。
* 修复了在通过工作流活动生成描述性报表时显示错误百分比的问题。 (NEO-14314)
* 修复了 **在投放期间排除重复地址** 选项。 (NEO-13240)
* 修复了在运行&#x200B;**扩充**&#x200B;活动时可能导致工作流失败的问题。(NEO-17338)
* 修复了从外部数据库获取记录并在 Campaign 活动库中插入这些记录时工作流中的问题。(NEO-26359)
* 通过防止在清除表达式分析器时内存损坏，修复了服务器崩溃问题。
* 修复了阻止 **NoNull** 函数在升级到构建9032后在Oracle数据库中工作。 (NEO-26488)
* 修复了在编辑活动模板描述时的问题，该问题会在复制粘贴符号（例如日语字符）时阻止显示&#x200B;**保存**&#x200B;按钮。(NEO-27071)
* 修复了在单击&#x200B;**保存**&#x200B;按钮之前单击窗口外部时阻止保存活动或活动模板的描述的问题。(NEO-27449)
* 修复了代理配置级别上阻止您在最新的 Windows 10 更新后登录 Adobe Campaign 的问题。(NEO-27813)
* 修复了与管理日志文件中的空行有关的问题，该问题会导致MTA进程行为失败并导致投放发送性能下降。

**技术演进**

Tomcat 已从版本 7 (7.0.103) 更新到版本 8 (8.5.57)。`tomcat-7` 目录替换为 `tomcat-8` 目录。在 Windows 上，_iis_neolane_setup.vbs_ 和 _apache_neolane.conf_ 现在安装在 `conf` 目录（而非先前的 `tomcat-7/conf`）中。在 Linux 上，_apache_neolane.conf_ 现在安装在 `conf` 目录中。

在Linux上，nlserver服务启动现在使用系统单元，而不是/etc/init.d/nlserver6脚本。 安装19.1.8程序包时，将自动执行到新启动方案的迁移。 /etc/init.d/nlserver6仍然提供，但是为了与nlserver服务（启动、重新启动、停止等）进行交互，我们建议您直接使用systemctl命令。


### ![](assets/do-not-localize/red_2.png) 19.1.7 版 - 版本 9036 {#release-19-1-7-build-9036}

_2020年9月15日_

**改进**

* 改进了Apache 2.4线程用法的nlsrvmod，以修复nlsrvmod崩溃问题。
* 修复了在Azure外部帐户和SSL加密中使用文件传输活动时的问题。 通过HTTP而不是HTTPS执行连接。 (NEO-26720)
* 修复了URL缓存机制无法检索标签或类别的问题。
* 修复了导致在电子邮件投放中错误定义镜像页面 URL 的问题（由于 ASCII 字符控制不当）。(NEO-26084)
* 更新了 catalina.properties 中的 jarToSkip 列表，以删除对不再使用的 jar 文件（iOS 通知）的引用。
* 修复了在升级后发布后阻止的回归问题。
* 修复了现成投放报告在导出到PDF时似乎被截断的回归。 (NEO-25757)
* 修复了从跟踪 URL 重定向时删除编码参数值的问题（影响日语字符）。(NEO-25637)
* 修复了导致在应当允许个性化域中的未签名链接时将其阻止的问题。(NEO-25210)
* 修复了由于工作流中的计算字段受影响而导致该工作流失败的回归。(NEO-25194)
* 修复了Microsoft Dynamics（从版本8.2开始）存在的一个兼容性问题，该问题可能会阻止执行某些API调用(RetrieveAllEntities)。 (NEO-24528)
* 修复了使用 ACS 连接器功能时阻止连接到 Campaign Standard 实例的回归问题（FOH/FOH2 连接管理不正确）。(NEO-23433)
* 修复了数据库连接上的导致 Web 服务器由于数据库编码问题而不断重新启动的回归问题。这可能会造成过度使用。(NEO-23264)
* 修复了由于非托管数据源而导致数据库清理工作流可能失败的问题。(NEO-23160, NEO-23364)
* 清理工作流现在按 100 批而不是逐批清除过期列表。
* 在切换到新序列 ID 机制后，所有更新收件人表的 Web 应用程序都会在升级后期间重新发布。
* 修复了在HTML内容标记外部存在Javascript代码时无法发送电子邮件的问题。 (NEO-18628)
* 修复了阻止跟踪工作流更新事务型消息跟踪指示器的问题。 (NEO-17770)
* 改进了数据库更新向导的性能，以减少SQL语句的数量，从而优化响应时间。
* 修复了在从 **文本内容** 选项卡。 (NEO-13545)
* 修复了由于未初始化的变量(m_pCurlReader)，阻止您使用Azure Blob Storage外部帐户在文件传输活动中上传文件的问题。 (NEO-13717)
* 修复了在重新发布 Web 应用程序之前关闭 Apache 和 Web 服务器的升级后问题。(NEO-27155)
* 修复了在 **调度程序** 工作流活动。


### ![](assets/do-not-localize/red_2.png) 19.1.6 版 - 版本 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>此内部版本仅用于内部部署安装。 对于混合部署，托管实例将继续运行9032内部版本。 请勿将营销实例升级到9035内部版本，因为该内部版本与9032不兼容。

_2019年10月3日_

**改进**

* 修复了使用 CRM Connector for Salesforce 时的问题。(NEO-17712)
* 修复了在发送事务性消息时可能导致性能问题的索引问题。
* 修复了发送消息时的性能问题。 (NEO-17558)
* 修复了可能导致中间源服务器无法处理某些消息的问题。 (NEO-12395)
* 修复了阻止完全使用SQL数据管理活动的问题（缺少“SQL数据管理”命名权限）。

### ![](assets/do-not-localize/red_2.png) 19.1.5 版 - 版本 9033{#release-19-1-5-build-9033}

_2019 年 8 月 13 日_

**改进**

* 修复了SQL语句“SELECT COUNT”的问题，该语句在数据管理活动的数据提取期间在默认数据库而不是FDA数据库上执行。
* 为了改进客户基础架构功能，服务器配置文件中现在提供了SFTP代理声明。
* 修复了 **添加链接的表** 字段 **数据加载(RDBMS)** 工作流活动。 (NEO-12213)
* 修复了通过命令行安装midEmitter包的问题。
* 添加了新的身份验证选项，以在具有Microsoft Dynamics的AC连接器中支持OAuth凭据。 (NEO-11982)
* 修复了UUID（唯一通用标识符）管理导致配置单元FDA的查询和数据加载工作流活动失败的问题。
* 修复了Oracle上导致某些函数在升级后被视为无效的回归。 (NEO-12759)
* 修复了在调度程序工作流活动中设置时间时导致选取错误时区的回归。

### ![](assets/do-not-localize/green_2.png) 19.1.4 版 - 内部版本 9032{#release-19-1-4-build-9032}


>[!NOTE]
>
>19.1.4 [!DNL Gold Standard] 本 [页面](../../rn/using/gold-standard.md).


### ![](assets/do-not-localize/red_2.png) 19.1.2 版 - 版本 9029{#release-19-1-2-build-9029}

_2019年6月21日_

**安全性增强**

* 为了优化安全性，Java库(Netty)已更新至最新版本(4.1.34)。 (NEO-12788)

**改进**

* 修复了链接到域列管理的回归，该回归会阻止在某些配置上发送电子邮件。
* 为了提高性能，已在rtEvent SOAP调用中添加了_operation=&quot;none&quot;属性，以避免“SELECT FOR UPDATE”请求。
* 修复了测试活动后叫客过渡的工作流显示问题。 (NEO-12727)
* 现在，允许在导入工作流期间删除在Microsoft Dynamics中创建的虚拟记录。
* 改进了在使用内部帐户时执行安全区域包的权限。


### ![](assets/do-not-localize/red_2.png) 19.1 版 - 版本 9026{#release-19-1-build-9026}

_2019年5月30日_

**新增功能**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 说明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 控制面板<br /> </td> 
   <td> <p>要提高管理员用户的工作效率，请通过监控存储、添加要的IP地址并为每个实例安装SSH密钥来管理SFTP服务允许列表器的设置。 请注意，控制面板仅适用于自今天起托管在AWS上的客户(<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">立即通过Experience Cloud登录</a>)。</p> <p>有关更多信息，请参阅<a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans">详细文档</a>和<a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=zh-Hans">操作方法视频</a>。 </p><p>注意：要访问控制面板，无需升级到最新的Campaign内部版本。</p> </td> 
  </tr> 
    <tr> 
   <td> 审核跟踪<br /> </td> 
   <td> <p>作为管理员，可通过监控和管理Adobe Campaign Classic实例中所做的更改来提高生产效率。 审核跟踪将记录对源架构、工作流和选项所执行的操作。 您可以快速查看是否已创建、修改或删除某个元素。</p><p>有关更多信息，请参阅 <a href="../../production/using/audit-trail.md">详细文档</a> 和 <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html">操作方法视频</a>.</p></td> 
  </tr> 
  <tr> 
   <td> 护栏、稳健性和可扩展性<br /> </td> 
   <td> 向Campaign Classic添加了一系列改进功能。 下面列出了护栏、稳健性和可扩展性方面的改进。<br /> </td> 
  </tr> 
  <tr> 
   <td> 兼容性矩阵更新<br /> </td> 
   <td> 使用此新版本，Adobe Campaign现在支持以下数据库系统。 请参阅 <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">兼容性矩阵</a>.<br /> 
    <ul> 
     <li> <p>Oracle18c</p> </li> 
     <li> <p>MySQL 5.7(FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata16(FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 出于安全原因，在使用 **[!UICONTROL Pre-process the file]** 选项 **[!UICONTROL Data loading (file)]** 工作流活动。 现在提供了一个下拉列表，允许您从3个选项中进行选择： **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat)或 **[!UICONTROL Decrypt]** (gpg)。 已添加XtkSecurity_Disable_Preproc安全标志。 对于新客户，此选项将设置为0。 对于现有客户，为了保持先前的行为，升级后会将此选项设置为1。 请参阅 [部分](../../workflow/using/data-loading--file-.md).
* 修复了在未设置时区的情况下测试FDA外部帐户的连接时出现的密码可见性问题。
* 已删除PDFBox库。
* Tomcat已更新到版本7.0.93。
* 修复了安全令牌无效时发生的令牌可见性问题。
* 修复了WSDL JSP(schemawsdl.jsp)中潜在的XTK注入问题。
* 优化了应用程序源代码和内存中的凭据和密码存储。
* PII视图限制已优化。 (NEO-12339、NEO-12396、NEO-12398、NEO-12339、NEO-12667)
* 修复了密钥管理中的不一致问题。
* 现在，使用有效或无效的用户名对失败的登录尝试显示相同的常规错误。
* 已上传文件的命名已得到增强。
* 已添加新的XtkSecurity_Disable_GetSetEnv选项，以阻止使用setEnv和getEnv函数。
* 敏感信息现在隐藏在应用程序堆栈跟踪中。

**护栏、稳健性和可扩展性方面的改进**

* 生命周期 — XtkNewId序列使用优化：最耗费的表已从xtkNewId序列移至专用序列。
* 通过HTTP v2进行FDA:通过HTTP的FDA协议广泛用于混合部署，特别是用于broadLog检索和交付准备。 增强了稳健性，以避免在检索或推送数据时出现网络问题和可能出现的错误。 这要求连接两端的内部版本是最新的，否则仍将使用旧协议。
* 跟踪工作流：跟踪工作流的稳健性已得到增强。 修复了与跟踪日志插入/更新和URL跟踪自定义相关的几个问题。 此外，跟踪工作流现在会检测可能导致错误的跟踪日志问题并停止工作流。 这些问题现已被丢弃且未处理。
* 清理工作流：清理工作流已得到改进，以避免潜在错误和停止。 这可优化数据库大小和性能。
* 事务型消息中的嵌入式图像：我们在事务型消息中增加了对嵌入式图像的完全支持，以避免可能的崩溃或缺少图像。
* 数据库大小 — XtkJobLog:清除机制已添加到此表。 这对数据库大小有积极影响。
* 密送存档：密送归档的默认参数已更改，以提高归档速度。 [了解更多信息](../../installation/using/email-archiving.md#parameters)
* 数据库结构更新：数据库结构更新向导生成的SQL请求已得到改进，以加快执行速度。
* 操作员操作的防护：已实施若干护栏，以防止操作员执行可能影响平台完整性的操作。 内置架构不能再通过界面删除。 此外，非管理员用户无法再编辑工作流源XML。
* 提供了两个新选项： **XtkSecurity_Restrict_EditXML** （用于禁用投放的XML代码版本）和 **NmsOperation_OperationMgtDebug** （用于监视操作Mgt技术工作流的执行）。 [了解更多信息](../../installation/using/configuring-campaign-options.md)

**其他变更**

* 推送通知：现在，我们支持“线程ID”选项进行iOS推送。
* 改进了对可能导致升级后问题的长名称索引的管理。
* 现在，在分析反编译投放时，如果将发布模式设置为 **[!UICONTROL None]** 在部署向导中，记录一个错误并停止分析：“发布模式”设置为“无”：无法嵌入图像。 图像无法在功能手机上显示。” (NEO-12208)
* 事务型消息传递的broadlog管理已得到改进。 将broadlogs从执行实例同步到控制实例时， @lastModified字段会更新为系统的当前日期。 为控制实例添加了MC_Update_BlLastModified选项。 True表示将在控制实例上使用当前日期（默认行为）。 False表示我们使用执行实例broadlog的@lastModified日期。 (NEO-12579)
* 在优惠券临时表中添加了索引，以优化投放发送。 (NEO-12437)
* 在Analytics集成中，现在允许检索包含%字符的AAM区段数据。 (NEO-12025)
* 删除了工作流热图中的10,000条记录限制，以修复缺失的数据问题。 (NEO-12329)
* Open Office不受支持，现在已从应用程序中完全删除。 如果您仍在使用它，请转到Libre Office，因为从19.1开始，它将不再工作。
* 您现在可以使用sysfilter属性限制对工作流中更新数据活动的写入访问。 [了解更多信息](../../configuration/using/filtering-schemas.md)

**修补程序**

* 修复了阻止为iOS移动推送通知上传证书的问题。
* 修复了事务推送通知的潜在重复服务器崩溃问题。 已修复其他崩溃问题。
* 修复了导致用户活动与打开投放指示器的跟踪报表之间存在报表差异的问题。 (NEO-11742)
* 修复了IMS登录问题。
* 修复了从库添加图像时，可能导致投放中缺少图像的问题。 (NEO-11900)
* 修复了在直邮投放中提取选件详细信息时可能发生的问题。 (NEO-11700)
* 修复了可能影响短信事务型消息性能的问题。 (NEO-9812)
* 修复了在外部文件中为投放主要目标使用定义选项时可能发生的控制台崩溃。 (NEO-12349)
* 修复了分析日语(.JP)域的目标收件人的消息时的问题。 (NEO-12246)
* 修复了在1:N链接中使用值分布时的显示问题。 (NEO-12212、NEO-11820)
* 修复了在升级后可能导致MTA日志中出现NmsMxDomain错误的问题。 (NEO-12752)
* 修复了在扩充工作流活动中使用“从主集中保留所有其他数据”选项时的问题。 (NEO-13291)
* 修复了使用HTTP2发送推送通知时的Tomcat崩溃问题。 (NEO-12701)
* 修复了HTTPRequest API未等待所有回调完成的问题。 (NEO-12628)
* 修复了事务型消息的跟踪指标的计算过程中存在的问题。 (NEO-12529)
* 修复了在选件管理中使用主题的问题。 (NEO-11804)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了在选件管理中预览出站XML或CSV文件以进行直邮投放的问题。 (NEO-11290)
* 修复了安装 **管理社交网络** （社交营销）包。 (NEO-12081)
* 修复了即使您拥有正确的访问权限，也无法删除Web应用程序的问题。 (NEO-12072)
* 修复了在导出并通过XML导入对象时可能会覆盖某些值的问题。 已添加XtkExport_IncludeDefaultValues选项。 当设置为True（默认行为）时，将导出所有值。 设置为False时，将使用默认值覆盖修改。 (NEO-11979)
* 修复了导致 **[!UICONTROL Alert]** 在查询后添加扩充活动时，工作流活动失败。 (NEO-12132)
* 修复了Oracle设置中管道（触发器）偏移未从数据库成功检索的问题，该问题会导致重复。 (NEO-12121)
* 修复了在使用Analytics集成时可能导致数据透视表显示错误的问题(NEO-12103)
* 修复了描述性分析报表的问题。 (NEO-11414)
* 修复了当远程表包含名称带有下划线的字段时，CRM连接器出现的问题。
* 修复了可能导致假设验证报表中货币符号出现显示问题的问题。 (NEO-11634)
* 修复了在跟踪链接中使用某些字符时的重定向和跟踪问题。
* 修复了阻止选件预览正常工作的问题。
* 修复了软退回未从地址表中删除的问题。
* 修复了使用条形码时的JAVA错误。
* 修复了Web应用程序中的翻译问题(NEO-12460)
* 修复了s3文件传输工作流活动的问题。 (NEO-12473)
* 修复了Web应用程序中的日期字段问题。 (NEO-12496)
* 修复了在投放中使用种子地址时的ID耗尽问题。 (NEO-11842)
* 修复了phantomjs和Debian 9兼容性的问题。
* 修复了批准校样内容时的错误。 (NEO-12725)
* 修复了“从群体中排除此子集”工作流功能的问题。 (NEO-12441)
* 修复了HTTPRequest-wait API未等待所有回调完成的问题。 (NEO-12628)
* 修复了拆分活动中的“更新共享受众”任务存在的问题。 (NEO-11562)
* 修复了Web服务器崩溃问题。 (NEO-12904)
* 修复了事务模板中Nature（自然）参数的问题。 (NEO-12334)
* 修复了在电子邮件文本编辑器中显示跟踪的URL时控制台崩溃的问题。 (NEO-13122)
* 修复了从受众导入受众时拆分文件活动存在的问题Audience Manager。 (NEO-11550)
* 修复了导致热点单击报告中出现错误的问题。 (NEO-11459)
* 修复了选件渲染的问题。 (NEO-11565)
* 修复了从受众导入受众时列表更新活动出现的问题。Audience Manager (NEO-11226)
* 修复了计划活动和时区配置的问题。 (NEO-11662)
* 修复了在URL格式错误的情况下导致跟踪工作流失败的问题。
* 修复了导入移动应用程序包后外部帐户出现的问题。
* 修复了向运算符分配时区时的问题。 (NEO-12464)
* 修复了可能导致匹配字段日志中出现错误的问题。 (NEO-11539、NEO-8978)
* 修复了在保存的报表中单击历史记录图标时的问题。 (NEO-11620)
* 修复了在报表中编辑数据透视表时的问题。 (NEO-12068)
