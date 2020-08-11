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
source-git-commit: 251244225076dd11a319d1c4b2124c0d05168eaa
workflow-type: tm+mt
source-wordcount: '1976'
ht-degree: 3%

---


# 最新版本{#latest-release}

![](assets/do-not-localize/cp-icon.png) **新控制面板6月版** ，包含活动用户档案监视、子域交付性审核和GPG密钥管理。 [了解更多](https://docs.adobe.com/content/help/zh-Hans/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/blue_2.png) 版本20.2.2 —— 内部版本9180 {#release-20-2-2-build-9180}

_2020年7月22日_

* 修复了在禁用签名功能时跟踪无法工作的问题。 (NEO-26411)
* 修复了导致个性化域中未签名链接在应允许时被阻止的问题。 (NEO-25210)
* 修复了在使用某些旧版Outlook时无法打开／单击跟踪URL的问题。 (NEO-25688)
* 修复了导致镜像页面URL在电子邮件投放中定义不正确的问题。 (NEO-26084)
* 修复了防网络钓鱼服务中的URL管理编码问题。 (NEO-25283)
* 修复了在个性化参数（带磅签名的锚点标记）中使用片段跟踪URL时无法正常工作的问题。 (NEO-25774)
* 修复了使用特定自定义跟踪公式时的跟踪问题。 (NEO-25277)修复了导致跟踪“通知单击”无法工作的问题（iOS和Android推送通知）。 (NEO-25965)
* 修复了影响工作流中计算字段的回归问题。 (NEO-25194)
* 修复了导致动态创建Web跟踪URL无法正常工作的回归问题。 (NEO-20999)
* 修复了现成投放报告的问题，该问题在导出到PDF时显示被截断。 (NEO-25757)
* 修复了部署向导中的崩溃问题。
* 修复了一个问题，该问题可能会阻止优惠通知工作流在配置升级后正常工作。
* iOS HTTP2连接器已得到改进（第三方更新和错误管理）。 (NEO-25904, NEO-25903)
* catalina.properties中的jarToSkip列表已更新，以删除对不再使用的jar文件（iOS通知）的引用。
* 修复了在放置后阻止投放准备的问题。
* 切换到新的序 [列ID机制后](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)，所有更新收件人表的Web应用程序都会在升级过程中重新发布。
* 修复了投放内容中的潜在XSS漏洞。 (NEO-17987, NEO-26073)

## ![](assets/do-not-localize/orange_2.png) 版本20.2.1 —— 内部版本9178 {#release-20-2-1-build-9178}

_2020年6月8日_

**新增功能**

<table> 
 <thead> 
  <tr> 
   <th> <strong>支持表情图标</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>在活动中设计消息时，您现在可以使用专用按钮在消息正文中轻松插入表情图标。 还可以在电子邮件主题行中添加这些内容。 您可以自定义界面中可用表情图标的列表。</p>
    <p>有关添加表情图标的详细信息，请参阅详 <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">细文档</a>。 在本节中了解如何自定义 <a href="../../delivery/using/customizing-emoticon-list.md">表情列表</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure突触联合数据访问连接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>您现在可以将活动实例连接到Azure突触外部数据库。 此连接通过新外部帐户管理。</p>
    <p>Azure Synapse仅适用于混合和内部部署环境。 有关详细信息，请参阅<a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">详细文档</a>。</p>
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
   <td> <p>泰国的个人数据保护法(PDPA)是一项新的隐私法，旨在协调泰国的数据保护要求并使之现代化。 </p>
   <p>巴西的Lei Geral de Proteção de Dados(LGPD)将从8月16日起生效，适用于巴西所有收集或处理个人数据的公司。</p>
   <p>这些法规适用于为居住在这些国家／地区的Adobe Campaign主体持有数据的客户。 除了活动中已有的隐私权功能（包括同意管理、数据保留设置和用户角色），我们还将利用此机会加入其他功能，以帮助您做好PDPA和LGPD的准备：</p>
   <ul> 
     <li><p>访问权和删除权：我们将充分利用 GDPR 和 CCPA 所增加的权利。<a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">阅读更多</a></p></li> 
     <li> <p>使用活动接口或API创建隐私请求时，您现在选择规 <strong>定类</strong> 型：PDPA、LGPD、GDPR、CCPA。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">了解更多</a>。</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 默认情况下，为所有客户启用了对跟踪电子邮件中链接的安全性。 另外还提供了增强的安全功能，可通过联系客户服务中心来启用此功能。 有关非托管客户启用此功能的功能和步骤的更多详细信息，请参阅安 [全和隐私核对清单](https://helpx.adobe.com/campaign/kb/acc-security.html)。 (NEO-24232)

* 为了优化安全性，用于生成文件名的MD5哈希算法已通过sha256得到增强，以用于公共文件上传。 (NEO-17044)

* 为了增强XSS攻击的安全性，在执行镜像页面时禁用客户端脚本。 (NEO-17987)

* 修复了隐私请求清除 **技术工作流无法** 删除对帐数据的问题。 (NEO-25168, NEO-21004)

* 修复了文件传输 **活动的问题** ，该问题导致基于SFTP密钥的身份验证无法在Debian 9上工作。 (NEO-23183)

**兼容性增强**

活动现在支持以下系统：
* 操作系统：德比10
* RDBMS:Oracle 18c和Oracle 19c
* 联合数据访问:Azure突触分析

了解有关活动 [兼容性矩阵的更多信息](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

**改进**

* 交易消息已得到改进，可获得更好的用户体验。 您现在可以取消发布事务性消息模板，这将从执行实例中删除它。 [了解更多](../../message-center/using/template-unpublication.md).

* 新选项可用于设置发送包含图像或附件的电子邮件时的限制。 这些护栏可以避免性能问题，这对于事务性消息尤为有用。 [阅读更多](../../installation/using/configuring-campaign-options.md#delivery)

* 新的“ **在投放库中准备部分** ”选项允许直接在数据库中执行投放准备，这可以显着加快分析。 此选项仅适用于特定配置。 [了解更多](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* 针对Microsoft Dynamics [的CRM连接器活动](../../workflow/using/crm-connector.md) (CRM Connector Connector)的性能已得到改进。 (NEO-13303, NEO-12710)

* 已增加共享内存版本。

   >[!WARNING]
   >
   >执行升级后，此改进需要执行额外的步骤。 请参阅下 **面的技术** 演变部分。

* 清理工作流已得到增强。 所有已删除工作流的孤立工作表现在也由清除工作流自动删除。 [了解更多](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* 使用iOS HTTP2连接器的iOS移动应用程序的证书现在在发送推送通知之前经过验证，从而防止投放因证书过期而失败。

* HTTP代理连接的管理已得到改进。 [了解更多](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**其他变更**

* 现已弃用传统SMS连接器。 请参阅“已弃 [用的功能”页](../../rn/using/deprecated-features.md)。

* 您不能再使用自己的Litmus帐户来配置和使用Adobe Campaign中的收件箱呈现。 [了解更多](../../delivery/using/inbox-rendering.md).

* 为了更好地区分视图和文件夹，视图名称的颜色已从深蓝色更改为深青色。 [阅读更多](../../platform/using/access-management.md#about-views)

* Campaign Classic现在可以连接到托管在英国、印度和加拿大地区的Microsoft Dynamics CRM帐户。 这适用于Office 365和内部部署(Dynamics 2015)部署类型。

* 活动现在执行TLS验证以检查服务器的主机名是否与提供的证书中的主机名匹配。

* 投放和跟踪统计信息表现在为SMS渠道显示每个投放一个条目，而不是每个投放收件人显示一个条目。

* 在日志文件中添加了一条错误消息，当下载的文件大于磁盘空间时警告用户。

* Snowflake连接器现在可使用以下功能：几个月前，几天前Int,ToDateTime，几年前。

**技术演进**

此新版本更新了共享内存，并需要执行升级的其他步骤。 作为活动管理员，您需要删除内存段。 这些步骤是必需的，因为旧段将阻止nlserver/nlsrvmod启动。

在Windows上，需要重新启动系统。

在Debian/CentOs上，需要删除共享内存。 以下是步骤：

在升级之前，您需要执行以下步骤：

1. 如果apache2（CentOS上的http2）服务正在运行，请停止该服务。
1. 如果nlserver(nlserver6 for older builds)服务正在运行，请停止它。

升级后：

1. 如果版本比当前版 **本旧** ，请使用ipcrm命令删除共享内存。
1. 开始nlserver服务（如果它正在运行）。
1. 开始apache2服务（如果它正在运行）。

下面是Debian的命令行：

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

本页提供Linux的示 [例](../../configuration/using/additional-parameters.md#redirection-server-configuration)。

**修补程序**

* 修复了清除工作流日志中的次要回归。
* 修复了分析WSDL文件 **时工作流加载(SOAP** )活动中的问题。
* 修复了使用工作流活动升级大量调查以有效处理大量工作流 **时** ，导致出错的问题。
* 修复了处理增强MTA中的inMail邮件时的间歇性连接问题。 (NEO-20380)
* 修复了在HTML中以100%宽度显示图像时，热点单击百分比无法正确显示的问题。 (NEO-23203)
* 修复了导致投放的条件内容无法在热点单击报告中完全显示的问题。 (NEO-18729)
* 修复了在恢复工作流以发送重复目标时跳过投放批准步骤的问题。 (NEO-18166)
* 修复了在工作流中修 **复错误后** ,“重新启动消息准备”按钮无法恢复投放的问题。 (NEO-13488)
* 修复了在中间源阶段可能导致投放在目标包括日语电子邮件格式的收件人的模式下失败的问题。 (NEO-23846)
* 修复了Snowflake连接器的时区转换问题(NEO-20105)
* 修复了外部帐户使用FTP over SSL时的问题。 (NEO-20498)
* 修复了一个问题，该问题可能会阻止图像以行投放显示。 (NEO-23207)
* 修复了在发布优惠时导致错误的问题。 (NEO-23312)
* 修复了推送通知的问题，该问题导致即使证书已过期，测试连接也能在移动应用程序中工作。 (NEO-22991)
* 修复了在以高频率发送时可能影响推送通知的问题。 (NEO-20516)
* 修复了导致跟踪数据包含重复的问题，即使跟踪日志没有。 (NEO-20040)
* 修复了在跟踪服务器通信失败后导致发送重复事务电子邮件的问题。 (NEO-23640)
* 修复了从跟踪URL重定向时删除编码参数值的问题。 (NEO-25637)
* 修复了在比较浮点数时查询无法工作的问题。 (NEO-23243)
* 修复了在重新启动工作流 **后，** “修改者”列内容无法显示的问题。 (NEO-23035)
* 修复了从第二个容器下载日志时导致跟踪技术工作流失败的问题。 (NEO-23159)
* 修复了在运行工作流活动时可能导致扩充失败 **的问题** 。 (NEO-17338)
* 已向多次添加检查以 **将字段保留** 在外部重复数据删除工 **作流活动** 中，以防输入null或负值。
* 已从重复 **的调度程序** 中删除活动向导，以避免提及小时和分钟数。 只考虑日期。
* 修复了通过“脚本”工作流存储中的“由脚本计 **算”选项创建投放时** ，其他活动字段 **存在的一** 个问题。 (NEO-20609)
* 修复了阻止在工作流库清除任务中删除Ghost的问题。
* 修复了导致计费(活 **动用户档案)技术工作** 流失败的问题。 (NEO-1977)
* 修复了测试acsDefaultAccount外部帐户连接时的问题。 (NEO-23433)
* 修复了一个问题，该问题导致您无法使用Hadoop表创建具有多列的主键模式扩展。 (NEO-17390)
* 修复了加载(SOAP) **活动中的一个问题** ，该问题可能会阻止从URL加载WSDL文件。 (NEO-16924)
* 修复了在负载平衡多个活动工作流服 **务器时** ，无法通过控制台执行无条件停止的问题。 (NEO-19556)
* 修复了导致清除工作流崩溃的回归。
* 修复了在执行实例上发布模板时可能发生的问题。
* 修复了可能阻止collectPrivacyRequests技术工作流运行的问题。 (NEO-20513, NEO-25169)
* 修复了在升级到构建9080后尝试连接到Audience Manager时可能发生的问题。 (NEO-20511, NEO-25167)
* 修复了以PDF或XLS格式导出报表时可能出现的问题。 (NEO-20982、NEO-23493、NEO-23348)
* 修复了在投放列表发送后，在投放中显示两次的问题。
* 修复了投放准备问题，该问题在将路由配置设置为通过中间源发送投放时可能发生。
* 修复了在单击“行”消息中的Web应用程序链接时可能显示错误消息的问题。
* 修复了可能阻止Microsoft Dynamics CRM检索所有实体的问题。 (NEO-24528)
* 修复了在运行清理工作流 **后删除增量查询** 活动历史记录的问题。
* 修复了创建中间源外部帐户时缺少NmsMidSourcing_LastBroadLog_&lt;InternalName>选项的问题
