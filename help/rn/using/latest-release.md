---
title: 最新版本
description: 最新版本
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
source-git-commit: eab67029d477044bc853f2a5c2de06ace70ebbee

---


# 最新版本{#latest-release}

[构建升级](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) |控 [制面板版本](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) |文 [档更新](../../rn/using/documentation-updates.md) |先 [前版本](../../rn/using/release--19-2.md) |已 [弃用功能](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>一般可用性</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>不再可用</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>已弃用</strong></td> 
  </tr> 
   <tr> 
   <td>提供最新的稳定版本。 构建在生产中经过验证的内容。<br> </td>
   <td>由Adobe验证的构建。 等待生产校样。<br> </td>
   <td>可用于错误修复的更新版本。 需要更新。<br> </td>
   <td>包含已知的回归。 更新是必需的。<br> </td>
  </tr> 
 </tbody> 
</table>

最 **后一个稳定版本** 为9032(3a9dc9c)。 单击此 [处](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/blue_2.png) 版本20.1.2 —— 内部版本9123 {#release-20-1-2-build-9123}

_2020年3月13日_

* 修复了阻止在Red Hat 7服务器上部署版本的问题。 (NEO-23332)

## ![](assets/do-not-localize/orange_2.png) 版本20.1 —— 内部版本9122 {#release-20-1-build-9122}

_2020年2月17日_

**新增内容?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>雪花联合数据访问连接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>雪花是一个完全受管的云数据仓库，可在存储和计算级别进行扩展。 有了这款新的连接器，Adobe Campaign现在可以利用雪花的强大功能来执行大数据分割。 此连接器适用于所有客户，包括Adobe托管的客户。</p>
    <p>有关详细信息，请参阅详细 <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">文档</a> 和教 <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">程视频</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Hadoop联合数据访问连接器增强功能</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Hadoop联合数据访问连接器已得到改进，可支持Hadoop 3.0和Cloudera。</p>
    <p>有关详细信息，请参阅详 <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">细文档</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全增强**

* 改进了报表配置中的安全性，以防止点击劫持。 这适用于新报告。 对于旧报告，您需要重新发布它们以应用更改。 (NEO-13282)

* 修复了cryptString中的小内存问题。 (NEO-20071)

* 改进了监视JSP以修复内部IP泄露。 (NEO-16821)

* 修复了堆栈跟踪信息可显示给非管理员用户的问题。 (NEO-12388)

* 改进了对以前会话中缓存数据的管理。 (NEO-17039)

* 修复了导致logins.log文件无法通过IMS记录成功登录尝试的问题。 (NEO-11004)

**改进**

* HTTP2连接器现在支持iOS 13。

* 改进了对推送通知功能（nms:address和nms:appSubscriptionRcp）使用的表的隔离管理和清理。 对于iOS（仅限HTTP2连接器），禁用的令牌现在处理方式与Android相同。 现在在NmsAppSubscriptionRcp表中设置了disable标志。 [阅读更多](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* 在 **JavaScript代码和高级JavaScript代码工作流活动中添加了一个新选项****** ，用于定义超时期。 这可以防止javascript执行阶段运行过长。 如果超时时间过去，则停止工作流。 默认超时为1小时。 [阅读更多](../../workflow/using/sql-code-and-javascript-code.md)

* 现在，当在投放服务器上未找到匹配的关联时，分析停止，并显示相应的错误消息。

* 现在支持Postgres的数据库故障转移：当数据库服务器崩溃和重新启动时，活动现在会自动重新连接到它。

* “ **开始待定** ”视图已添加到“管理”>“审核”>“工作流状态”节点。 这允许您监视实例上等待由operationMagt进程启动的所有 **工作流** 。 此视图包含营销活动包。 [阅读更多](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**其他更改**

* 在Linux上，nlserver服务启动现在使用系统单元而不是/etc/init.d/nlserver6脚本。 在安装20.1包时，会自动执行到新启动方案的迁移。 /etc/init.d/nlserver6仍然提供，但是为了与nlserver服务(开始、重新启动、停止等)进行交互，建议您直接使用systemctl命令。

* 最耗用的自定义表已从 **xtkNewId序列移到专用序列** 。 [阅读更多](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* 改进了查询性能，这些性能可能会受到不必要的数据库连接的影响。

* 改进了数据库更新向导的性能。

* 数据库记录管理得到了增强。

* 连接池的健壮性已得到改进，这可以防止意外连接故障的发生太频繁。

* 增强了在软错误时向隔离发送地址的电子邮件地址验证规则。 [阅读更多](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* 对于Debian,活动现在在系统PCRE库可用时使用它们。

* 活动现在允许使用更新的系统ODBC库。

* 在打开连接以加载富映像时，超时已添加到LINE servlet。 如果图像加载时间过长，Servlet将停止连接以避免出现瓶颈。

**修补程序**

* 修复了使用Hadoop连接器时的帐户密钥加密问题。

* 修复了由于实施SSL认证而导致用户连接在Windows服务器上失败的回归问题。 (NEO-20629)

* 修复了负工作流ID情况下增量查询活动的问题。 (NEO-19779)

* 修复了通过Netezza查询连接器运行联合数据访问时的编码问题。 (NEO-19594)

* 修复了在 **Web下载工作流事件活动中使用POST方法时导致错误的问** 题。

* 修复了生成优惠建议的问题。 (NEO-18176)

* 修复了使用客户获取Web表单模板时的页脚显示问题。

* 修复了分析连续投放内容中的URL时可能导致其崩溃的问题。 (NEO-16910)

* 修复了在创建新 **开始****** 时不计算活动和结束字段的问题。

* 修复了使用URL时“文 **件下载** ”工作流程活动的问题。

* 修复了在报表的查询列表中预览导入的活动时的问题。 (NEO-13119)

* 修复了在电子邮件编辑器中选择“按活动 **”个性化块时** ，显示过时图像的问题。

* 客户端与服务器之间的网络通信得到改进。

* 修复了在同一工作流中创建过多活动的问题。 现在，您创建的工作流不能超过28个。 此时将显示警告。

* 修复了在合并工作流 **活动中使用** “选择列对帐”选项 **时的问题** 。

* 修复了在工作流中使用损坏的扩充列表时可能发生的控制台崩溃问题。 (NEO-18096)

* 修复了可能在工作流中发生的各种控制台崩溃问题(NEO-18010、NEO-18032)

* 修复了即使禁用外部信号工作流 **活动时也允许执行** “外部信号”工作流程的问题。 (NEO-17524)

* 修复了创建新模式时的问题。

* 修复了发送SMS消息时的跟踪问题。 (NEO-19595)

* 修复了在受众指示器中显示错误的目标投放编号的问题。

* 修复了通过工作流活动生成描述性报告时显示错误百分比的问题。 (NEO-14314)

* 修复了在时间投放参数时，视图吞吐量报告显示不同数字的问题。 (NEO-11783)

* 修复了导致事务性消息跟踪指示器无法由跟踪工作流更新的问题。 (NEO-17770)

* 修复了在通过SOAP请求优惠时导致Web进程崩溃和重新启动的回归问题。 (NEO-19482)

* 修复了上传目录是远程共享位置时无法将数据上传到公共资源的问题。 (NEO-19361)

* 修复了导致Adobe Experience Cloud技 **术工作流程中的导入受众始终失败的问题** 。 (NEO-18463)

* 修复了使用从Experience Manager导入的模板时无法发送投放的问题。 (NEO-17540)

* 修复了升级到构建9032并阻止实例通过SSL协议连接到FTP服务器后出现的问题。 (NEO-20498)

* 修复了在使用活动模式作为联合数据访问的工作流中使用更新数据定位维度删除、插入或更新大量数据时发生的问题。 **** (NEO-13280)

* 修复了在标记外使用“if”语句时无法发送电子邮件的问 `body` 题。

* 修复了在尝试从已发送消息的投放日志显示镜像页面时发生的问题。 (NEO-17976)

* 修复了在镜像页面中单 **击“导入HTML** ”后，“文本内容”选项卡中无法显示“指向投放的链接” **(Link to** Inveration Personalization)块 **** 的问题。 (NEO-17568)

* 单击指向已过期的镜像页面的链接时显示错误消息。 (NEO-17340)

* 修复了“数据分发”创建屏幕中无法使用某些按 **钮的问** 题。

* 修复了在以亚洲／加尔各答为时区的实例中安排投放活动时发生的问题。 (NEO-20001)

* 现在，当投放有关联配置问题时，会显示错误。

* 修复了在“关于”菜单中显示错误版本标签 **号的问** 题。

* 修复了在工作流中尝试从重复的路由属性更新投放帐户时发生的问题。 (NEO-18684)

* 修复了通过重定向模块连接到实例时出现的一个问题，该问题导致连接在关闭后无法正确清理。
