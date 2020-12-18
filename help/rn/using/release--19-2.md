---
solution: Campaign Classic
product: campaign
title: 版本 19.2
description: 版本 19.2
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 8%

---


# 版本 19.2{#release-19-2}

## ![](assets/do-not-localize/orange_2.png) 版本 19.2.3 - 版本 9081 {#release-19-2-3-build-9081}

_2020年2月7日_

**改进**

* 修复了由于实施SSL认证而导致用户连接在Windows服务器上失败的回归问题。 (NEO-20629)
* 修复了在&#x200B;**“关于**”菜单中显示错误版本标签号的问题。

## ![](assets/do-not-localize/orange_2.png) 版本 19.2 - 版本 9080 {#release-19-2-build-9080}

_2019年12月2日_

**新增功能**

<table> 
 <thead> 
  <tr> 
   <th> <strong>加利福尼亚消费者隐私法(CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA是加利福尼亚州新的隐私法，它协调2020年1月1日起生效的数据保护要求并使其现代化。 CCPA适用于持有居住在加利福尼亚的数据主体数据的Adobe Campaign客户。</p>
    <p>除了现有的隐私权功能（包括同意管理、数据保留设置和用户角色）之外，Adobe Campaign还有助于您为CCPA做好准备：</p>
    <ul>
      <li>访问权和删除权：我们正在利用为GDPR增加的功能。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">阅读更多</a></li>
      <li>您可以跟踪消费者是否已选择出售个人信息。 为此，您需要扩展用户档案表并添加<strong> CCPA</strong>退出字段。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">阅读更多</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>工作流实时监视</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>您现在可以使用预定义的工作流监视实例上所有视图的执行状态。</p>
   <p>有关详细信息，请参阅<a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">详细文档</a>。</p></td> 
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
<td> <p>Adobe Campaign允许您尝试新的交互式<a href="https://amp.dev/about/email/">电子邮件</a>格式，它允许营销人员在邮件中加入AMP组件，以通过丰富、动态和交互式内容增强电子邮件体验，并在邮件本身中直接具有可操作性。</p>
   <p>此功能作为公共测试版发布。</p>
   <p>有关更多信息，请参阅<a href="../../delivery/using/defining-interactive-content.md">详细文档</a>和<a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">教程视频</a>。</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>安全SMS消息(TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>现在，扩展通用SMPP连接器支持安全SMS。 这允许与提供者建立加密连接。</p> <p><strong>警</strong> 告此功能要求所有服务器上都有最新证书。无效、已吊销或过期的证书将生成影响整体SMS发送功能的错误。</p><p>有关详细信息，请参阅<a href="https://helpx.adobe.com/cn/campaign/kb/sms-connector-protocol-and-settings.html">详细文档</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 修复了活动界面中存储的跨站点脚本漏洞——输入数据验证和输出编码。 (NEO-16810)
* 修复了用户档案授权的安全问题，该问题通过增强登录限制策略可允许访问未经授权的数据。 (NEO-14445)

**改进**

* 推送通知的内存消耗优化。
* 为了性能和存储优化，**logins.log**&#x200B;文件的处理已得到增强。 该文件现在分为多个文件，每天一个，最多保留365个文件。 [阅读更多](../../production/using/log-files.md)
* 现在可以使用密码凭据（密码+用户名）或证书（私钥）配置Microsoft Dynamics CRM外部帐户。 [阅读更多](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* 为提高可靠性，Hadoop联合数据访问连接器增加了一些增强功能
* 添加了一个特定的保护栏，用于检查磁盘空间，然后允许在服务器上上传公共资源。
* 已添加新的[活动选项](../../installation/using/configuring-campaign-options.md):
   * **WdbcKillSessionPolicy**&#x200B;配置选项允许您对所有工作流和PostgreSQL查询影响&#x200B;**无条件停止**&#x200B;行为。
   * **NmsOperation_DeliveryPreparationWindow**&#x200B;选项允许您定义超过天数，在此天数内，状态不一致的投放将从运行投放的计数中排除。
   * **WdbcOptions_TempDbName**&#x200B;选项允许您为Microsoft SQL Server上的工作表配置单独的数据库。 这将优化备份和复制。 [阅读更多](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * **XtkCleanup_NoStats**&#x200B;选项已针对PostgreSQL进行了增强，以更好地控制存储库清除工作流的优化步骤的行为。 [阅读更多](../../production/using/database-cleanup-workflow.md#statistics-update)
* 已向&#x200B;**logon()** API添加帐户锁定机制。 它可防止在指定时间范围内连续登录尝试一定次数后再进行任何登录尝试。
* 投放属性中新增的&#x200B;**最大个性化运行时间**&#x200B;选项允许您为个性化运行时间定义超时时间，以防止个性化阶段运行过长。 [阅读更多](../../delivery/using/personalization-fields.md#timing-out-personalization)
* 已添加&#x200B;**ftp协议**&#x200B;选项，允许您对SFTP连接使用代理配置。 [阅读更多](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* 对本地环境的SFTP外部服务器代理访问的新支持。
* 已添加特定的护栏，以防止安装与活动实例不兼容的包。 [阅读更多](../../installation/using/installing-campaign-standard-packages.md)

_弃用的系统_

现在[已弃用](https://helpx.adobe.com/cn/campaign/kb/deprecated-and-removed-features.html)以下系统用于Campaign Classic实现：
* Apache 2.2
* Centos 6

请确保您使用最新活动兼容性矩阵中列出的所有系统的受支持版本。 [阅读更多](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

_活动移动SDK_

iOS SDK的内部版本1.0.26现已可用。 在此新版本中，我们增加了对iOS 13的支持。 此新版本现在支持iOS 13推送通知的通知优先级和新的注册令牌管理流程。 如果您在SDK的先前版本上运行应用程序，则需要使用新的SDK重新编译应用程序。 要获取SDK，请与Adobe客户关怀联系。

**修补程序**

* 修复了&#x200B;**数据加载(RDBMS)**&#x200B;工作流活动中&#x200B;**添加链接表**&#x200B;字段为空时的崩溃问题。 (NEO-12213)
* 修复了可能导致某些邮件不被中间源服务器处理的问题。 (NEO-12395)
* 修复了在Teradata使用查询条带选项时数据库清理工作流中的问题。 (NEO-12399)
* 修复了影响投放分析（包括ne.jp域）的问题。 (NEO-12609)
* 修复了与TLS更新上的SMS相关的问题，该问题暗示证书策略更加严格。 这些更新可能导致在证书过期时市场营销和中间源服务器之间发生连接故障。 (NEO-17698)
* 修复了在具有保管库身份验证的外部帐户环境中对中间源使用&#x200B;**测试连接**&#x200B;按钮时的问题。 (NEO-12722)
* 修复了在查询使用日期函数时与联合数据访问Hadoop连接的问题。 (NEO-12847)
* 修复了替换电子邮件编辑器中的图像时的问题。 (NEO-13098)
* 修复了一个问题，该问题可能导致已删除或移动到其他位置的文件夹出现升级后错误。 (NEO-13118)
* 修复了在LINE消息上使用&#x200B;**“按设备屏幕大小定义图像”**&#x200B;选项时图像显示的问题。 (NEO-13228)
* 修复了未选择“在投放期间排除重复地址”选项时的投放准备问题。 ****(NEO-13240)
* 修复了使用&#x200B;**文件传输**&#x200B;活动下载文件时工作流中的问题，该使用&#x200B;**传输**&#x200B;后删除源文件选项（名称包含空格字符）。 (NEO-13411)
* 修复了Tomcat缓存清除的一个问题，该问题可能导致内存问题。 (NEO-13456)
* 修复了在Microsoft SQL 2017中运行的现有优惠上安装具有执行实例&#x200B;**内置包的控制实例引擎的**&#x200B;控制时的问题。 (NEO-13539)
* 修复了由于未初始化变量，从&#x200B;**文本内容**&#x200B;选项卡取消检查电子邮件中跟踪的URL时可能发生的控制台崩溃问题。 (NEO-13545)
* 修复了中文发件人姓名的编码问题。 (NEO-13837)
* 修复了在从资源管理器显示调查响应数据时可能引发的错误。 (NEO-14590)
* 修复了可能导致投放日志分类与隔离表不一致的问题。 (NEO-16547)
* 修复了未嵌入到电子邮件中的DKIM密钥的问题。 (NEO-16804)
* 修复了在API调用的上下文中使用无效会话令牌触发事件时显示错误错误代码的问题。 错误代码为“HTTP 200 OK”，而不是“HTTP 403 Forbidden”。 (NEO-16826)
* 修复了通过Web访问显示投放报告时的问题。 (NEO-17015)
* 修复了登录Adobe Campaign时IMS身份验证问题。 (NEO-17312)
* 修复了在隐私管理流程中阻止删除隔离电子邮件的问题。 (NEO-17314)
* 修复了使用SQL数据库升级到9031后的吞吐量问题。 (NEO-17558)
* 修复了影响Salesforce的CRM连接器的问题。 (NEO-17712)
* 修复了从外部SFTP导入数据时的超时问题。 (NEO-19723)
* 修复了访问预测模型时的问题。 (NEO-19713)
* 修复了影响&#x200B;**Split**&#x200B;工作流活动中Hadoop联合数据访问库随机采样的问题。 (NEO-16636)
* 修复了Oracle上的回归，该回归导致某些函数在放置后被视为无效。 (NEO-12759)


