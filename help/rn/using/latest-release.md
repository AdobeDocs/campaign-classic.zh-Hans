---
title: 最新版本
description: Campaign Classic 19.2发行说明
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 37946a63a0cd0312de31b26dd4d115895d959638

---


# 最新版本{#latest-release}

[构建升级](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) |控 [制面板版本](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) |文 [档更新](../../rn/using/documentation-updates.md) |先 [前版本](../../rn/using/release--19-1.md) |已 [弃用功能](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>一般可用性</strong></td>
   <td><img src="assets/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/orange3.png"/><strong>不再可用</strong></td> 
   <td><img src="assets/red3.png"/><strong>已弃用</strong></td> 
  </tr> 
   <tr> 
   <td>提供最新的稳定版本。 <br>构建在生产中验证的内容。 </td>
   <td>由Adobe验证的构建。 <br>等待生产校样。 </td>
   <td>可用于错误修复的更新版本。 <br>需要更新。 </td>
   <td>包含已知的回归。 <br>更新是必需的。 </td>
  </tr> 
 </tbody> 
</table>

单 [击此处](../../rn/using/release--19-1.md#release-19-1-4-build-9032) ，查看上 **一个稳定版本** (GA)。

## ![](assets/orange2.png) 版本19.2.3 —— 内部版本9081 {#release-19-2-2-build-9081}

2020年2月7日_

**改进**

* 修复了由于实施SSL认证而导致用户连接在Windows服务器上失败的回归问题。 (NEO-20629)
* 修复了在“关于”菜单中显示错误版本标签 **号的问** 题。

## ![](assets/orange2.png) 版本19.2 —— 内部版本9080 {#release-19-2-build-9080}

_2019年12月2日_

**有什么新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>加利福尼亚消费者隐私法(CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA是加利福尼亚州新的隐私法，该法规将2020年1月1日生效的数据保护要求协调并现代化。 CCPA适用于持有居住在加利福尼亚的数据主体数据的Adobe Campaign客户。</p>
    <p>除了现有的隐私权功能（包括同意管理、数据保留设置和用户角色）之外，Adobe Campaign还可帮助您做好CCPA准备：</p>
    <ul>
      <li>访问权和删除权：我们正在利用为GDPR添加的功能。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">阅读更多</a></li>
      <li>您可以跟踪消费者是否已选择退出个人信息的销售。 为此，您需要扩展“配置文件”(Profiles)表格，并添 <strong>加“CCPA退出”(Opt-Out for CCPA</strong> )字段。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">阅读更多</a></li></td> 
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
   <td> <p>您现在可以使用预定义视图监视实例上所有工作流的执行状态。</p>
   <p>有关详细信息，请参阅详 <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">细文档</a>。</p></td> 
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
<td> <p>Adobe Campaign使您能够试用新的交互式 <a href="https://amp.dev/about/email/">AMP for Email</a> 格式，该格式允许营销人员将AMP组件包含在邮件中，以通过丰富、动态和交互式内容增强电子邮件体验，这些内容在邮件本身中直接具有可操作性。</p>
   <p>此功能作为公共测试版发布。</p>
   <p>有关详细信息，请参阅详细 <a href="../../delivery/using/defining-interactive-content.md">文档</a> 和教 <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">程视频</a>。</p><br /></td> 
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
<td> <p>现在通过扩展通用SMPP连接器支持安全SMS。 这允许与提供者进行加密连接。</p> <p><strong>警告</strong> ：此功能要求所有服务器上都有最新的证书。 无效、已吊销或过期的证书将生成影响整体SMS发送功能的错误。</p><p>有关详细信息，请参阅详 <a href="https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html">细文档</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**安全增强**

* 修复了Campaign界面中存储的跨站点脚本漏洞——输入数据验证和输出编码。 (NEO-16810)
* 修复了配置文件授权的安全问题，该问题通过增强登录限制策略可允许访问未经授权的数据。 (NEO-14445)

**改进**

* 推送通知的内存消耗优化。
* 为了优化性能和存储，对 **logins.log文件的处理已得到增强** 。 该文件现在被拆分为多个文件，每天一个文件，最多保留365个文件。 [阅读更多](../../production/using/log-files.md)
* Microsoft Dynamics CRM外部帐户现在可使用密码凭据（密码+用户名）或证书（私钥）进行配置。 [阅读更多](../../platform/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Hadoop FDA连接器中增加了一些增强功能以提高可靠性
* 添加了一个特定的保护栏，用于检查磁盘空间，然后允许在服务器上上传公共资源。
* 已添 [加新的系列活](../../installation/using/configuring-campaign-options.md) 动选项：
   * 使用 **WdbcKillSessionPolicy** (WdbcKillSessionPolicy **)配置选项可以影响所有工作流和PostgreSQL数据库查询的“无条件停止** ”行为。
   * 使用 **NmsOperation_DeliveryPreparationWindow** 选项可以定义超过天数，在天数内，状态不一致的提交将从正在运行的提交计数中排除。
   * 使用 **WdbcOptions_TempDbName** 选项可以为Microsoft SQL server上的工作表配置单独的数据库。 这将优化备份和复制。 [阅读更多](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * PostgreSQL **的XtkCleanup_NoStats** 选项已得到增强，可更好地控制数据库清理工作流的存储优化步骤的行为。 [阅读更多](../../production/using/database-cleanup-workflow.md#statistics-update)
* 帐户锁定机制已添加到 **logon()** API。 它可防止在指定时间范围内连续多次登录尝试失败后再进行任何登录尝试。
* 交付属 **性中新增的“最大个性化运行时间** ”选项允许您为个性化运行时间定义超时时间段，以防止个性化阶段运行过长。 [阅读更多](../../delivery/using/personalization-fields.md#timing-out-personalization)
* 已 **添加ftp协议** ，以允许您对SFTP连接使用代理配置。 [阅读更多](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* 对本地环境对SFTP外部服务器的代理访问的新支持。
* 已添加特定的保护栏，以防止安装与Campaign实例不兼容的包。 [阅读更多](../../installation/using/installing-campaign-standard-packages.md)

_已弃用的系统_

Campaign Classic实施现在不 [推荐使用](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) 以下系统：
* Apache 2.2
* Centos 6

请确保您使用最新营销活动兼容性列表中列出的任何系统的受支持版本。 [阅读更多](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

iOS SDK的内部版本1.0.26现已推出。 在此新版本中，我们添加了对iOS 13的支持。 此新版本现在支持iOS 13推送通知的通知优先级和新的注册令牌管理过程。 如果您在SDK的先前版本上运行应用程序，则需要使用新的SDK重新编译应用程序。 要获取SDK，请联系Adobe客户关怀。

**修补程序**

* 修复了在数据加载(RDBMS)工作流活动中添加空链接表 **时可能发生的控制台崩溃** 。 (NEO-12213)
* 修复了一个问题，该问题可能导致某些消息无法由中间采购服务器处理。 (NEO-12395)
* 修复了在Teradata中使用查询条带选项时数据库清理工作流中的一个问题。 (NEO-12399)
* 修复了影响包括ne.jp域的排版规则的交付分析的问题。 (NEO-12609)
* 修复了与TLS更新上的SMS相关的问题，该问题暗示存在更严格的证书策略。 这些更新可能导致在发生过期证书时，营销和中部采购服务器之间发生连接故障。 (NEO-17698)
* 修复了在具有Vault身份验证 **的中间资源环境中对外部帐户使用** “测试连接”按钮时的问题。 (NEO-12722)
* 修复了在FDA Hadoop连接中使用日期函数的查询的问题。 (NEO-12847)
* 修复了在电子邮件编辑器中替换图像时的问题。 (NEO-13098)
* 修复了一个问题，该问题可能导致已删除或移到其他位置的文件夹出现升级后错误。 (NEO-13118)
* 修复了在LINE消息上使用“按设备屏幕大小定 **义图像”选项时** ，图像显示上的问题。 (NEO-13228)
* 修复了取消选择“在传送过程中排 **除重复地址”选项时的传送准备** 问题。 (NEO-13240)
* 修复了使用“文件传输 **”活动下载文件时工作流中的一个问题，该问题是使用“传输后删除源文件”选项(名称中包含空格字符****** )。 (NEO-13411)
* 修复了Tomcat缓存清除的一个问题，该问题可能导致内存问题。 (NEO-13456)
* 修复了在Microsoft SQL 2017中运行的现 **** 有控件实例上安装具有内置执行实例包的选件引擎控制时的问题。 (NEO-13539)
* 修复了在“文本内容”选项卡中取消检查电子邮件中跟踪的URL时可能发生 **的控制台崩溃** 。 (NEO-13545)
* 修复了中文发送者姓名的编码问题。 (NEO-13837)
* 修复了在从资源管理器显示调查响应数据时可能引起的错误。 (NEO-14590)
* 修复了可能导致交付日志分类与隔离表不一致的问题。 (NEO-16547)
* 修复了未嵌入到电子邮件中的DKIM键的问题。 (NEO-16804)
* 修复了在API调用上下文中使用无效会话令牌触发事件时显示错误错误代码的问题。 错误代码为“HTTP 200 OK”，而不是“HTTP 403 Forbidded”。 (NEO-16826)
* 修复了通过Web访问显示交付报告时的问题。 (NEO-17015)
* 修复了登录Adobe Campaign时的IMS身份验证问题。 (NEO-17312)
* 修复了导致隔离电子邮件无法被隐私管理进程删除的问题。 (NEO-17314)
* 修复了使用SQL数据库升级到9031后的吞吐量问题。 (NEO-17558)
* 修复了影响Salesforce的CRM连接器的问题。 (NEO-17712)
* 修复了从外部SFTP导入数据时的超时问题。 (NEO-19723)
* 修复了访问预测模型时的问题。 (NEO-19713)
* 修复了影响Hadoop FDA数据库 **Split工作流程** (Workflow)活动中随机采样的问题。 (NEO-16636)

