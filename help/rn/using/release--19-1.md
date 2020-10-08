---
title: 版本 19.1
seo-title: 版本 19.1
description: 版本 19.1
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '2639'
ht-degree: 6%

---


# 版本 19.1{#release-19-1}

## ![](assets/do-not-localize/limited_2.png) 版本 19.1.7 - 版本 9036 {#release-19-1-7-build-9036}

_2020年9月15日_

**改进**

* 针对Apache 2.4线程使用改进了nlsrvmod以修复nlsrvmod崩溃。
* 修复了将文件传输活动与Azure外部帐户和SSL加密一起使用时的问题。 连接是通过HTTP而不是HTTPS执行的。 (NEO-26720)
* 在投放属性中， **[!UICONTROL Archive emails]** 已重命名该选 **[!UICONTROL Email BCC]** 项以获得更好的用户体验。
* 修复了url缓存机制未检索标签或类别的问题。
* 修复了导致电子邮件镜像页面中错误定义投放URL的问题（由于ASCII字符控制不当）。 (NEO-26084)
* catalina.properties中的jarToSkip列表已更新，以删除对不再使用的jar文件（iOS通知）的引用。
* 修复了在放置后发布后阻止的回归问题。
* 修复了带有现成投放报告的回归，该回归在导出到PDF时显示被截断。 (NEO-25757)
* 修复了从跟踪URL重定向时删除编码参数值（对日语字符的影响）的问题。 (NEO-25637)
* 修复了导致个性化域中未签名链接在应允许时被阻止的问题。 (NEO-25210)
* 修复了影响工作流中计算字段的回归，导致工作流失败。 (NEO-25194)
* 修复了Microsoft Dynamics（从版本8.2）的兼容性问题，该问题可能会阻止某些API调用执行(RetrieveAllEntities)。 (NEO-24528)
* 修复了使用ACS连接器功能时导致无法连接到Campaign Standard实例的回归问题（FOH/FOH2连接管理不正确）。 (NEO-23433)
* 修复了数据库连接上的回归问题，该问题导致Web服务器由于数据库编码问题而不断重新启动。 这可能导致过度消费。 (NEO-23264)
* 修复了由于非托管数据源而导致数据库清理工作流失败的问题。 (NEO-23160, NEO-23364)
* 清理工作流现在按100批而不是逐批清除过期列表。
* 切换到新的序 [列ID机制后](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)，所有更新收件人表的Web应用程序都会在升级过程中重新发布。
* 修复了在HTML内容标记外存在Javascript代码时无法发送电子邮件的问题。 (NEO-18628)
* 修复了事务性消息跟踪指示器无法由跟踪工作流更新的问题。 (NEO-17770)
* 改进了数据库更新向导的性能，以减少SQL语句的数量，从而优化响应时间。
* 修复了由于未初始化变量，从“文本内容”选项卡取消检查电子邮件中 **跟踪的** URL时可能发生的控制台崩溃问题。 (NEO-13545)
* 修复了由于未初始化的变量(m_pCurlReader)，您无法使用Azure Blob活动外部帐户在文件传输存储中上传文件的问题。 (NEO-13717)
* 修复了在重新发布Web应用程序之前关闭Apache和Web服务器的错误升级问题。 (NEO-27155)
* 修复了在调度程序工作流活动中设置时间时导致选取错误时 **区** 的回归。

## ![](assets/do-not-localize/orange_2.png) 版本 19.1.6 - 版本 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>此版本仅用于内部部署安装。 对于混合部署，托管实例将继续运行9032版本。 请勿将您的营销实例升级到9035版本，因为它与9032不兼容。

_2019年10月3日_

**改进**

* 修复了在使用Salesforce的CRM连接器时的问题。 (NEO-17712)
* 修复了在发送事务性消息时可能导致性能问题的索引问题。
* 修复了发送消息时的性能问题。 (NEO-17558)
* 修复了可能导致某些邮件不被中间源服务器处理的问题。 (NEO-12395)
* 修复了阻止完全使用SQL数据管理活动(缺少名为right的“SQL数据管理”)的问题。

## ![](assets/do-not-localize/red_2.png) 版本 19.1.5 - 版本 9033{#release-19-1-5-build-9033}

_2019年8月13日_

**改进**

* 修复了SQL语句“SELECT COUNT”的问题，该语句在数据管理活动中的联合数据访问提取期间在默认数据库而不是数据库上执行。
* 为了改进客户基础架构功能，服务器配置文件中现在提供了SFTP代理声明。
* 修复了在数据加载( **RDBMS)工作流活动** 中“添加链接表” **字段为空时的崩** 溃问题。 (NEO-12213)
* 修复了通过命令行安装midEmitter包的问题。
* 新增了一个身份验证选项，用于在AC连接器中通过Microsoft Dynamics支持OAuth凭据。 (NEO-11982)
* 修复了UUID（唯一通用标识符）管理导致查询和数据加载工作流活动在配置单元联合数据访问时失败的问题。
* 修复了Oracle上的回归，该回归导致某些函数在错误升级后被视为无效。 (NEO-12759)
* 修复了在调度程序工作流活动中设置时间时，导致选取错误时区的回归问题。

## ![](assets/do-not-localize/green_2.png) 版本 19.1.4 - 版本 9032{#release-19-1-4-build-9032}

>[!NOTE]
>
>19.1.4金本位币版本列在本 [页](../../rn/using/gold-standard.md)。


## ![](assets/do-not-localize/red_2.png) 版本 19.1.2 - 版本 9029{#release-19-1-2-build-9029}

_2019年6月21日_

**安全性增强**

* 为优化安全性，Java库(Netty)已更新至最新版本(4.1.34)。 (NEO-12788)

**改进**

* 修复了链接到域列管理的回归，该回归可防止在某些配置上发送电子邮件。
* 为了提高性能，已将_operation=&quot;none&quot;属性添加到rtEvent SOAP调用中以避免“SELECT FOR UPDATE”请求。
* 修复了测试过渡后出站活动的工作流显示问题。 (NEO-12727)
* 现在，我们允许在导入工作流程期间删除在Microsoft Dynamics中创建的虚拟记录。
* 改进了使用内部帐户时执行安全区包的权限。

## ![](assets/do-not-localize/red_2.png) 版本 19.1 - 版本 9026{#release-19-1-build-9026}

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
   <td> <p>要提高管理员用户的工作效率，请通过监视存储、向允许列表添加IP地址以及为每个实例安装SSH密钥来管理SFTP服务器的设置。 请注意，控制面板仅适用于今天在AWS上托管的客户(<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">今天通过Experience Cloud登录</a>)。</p> <p>有关更多信息，请参阅<a href="https://docs.adobe.com/content/help/zh-Hans/control-panel/using/control-panel-home.html">详细文档</a>和<a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">操作方法视频</a>。 </p><p>注意：升级到最新活动版本不是访问控制面板的必需条件。</p> </td> 
  </tr> 
    <tr> 
   <td> 审核跟踪<br /> </td> 
   <td> <p>作为管理员，通过监控和管理Adobe Campaign Classic实例中所做的更改来提高生产效率。 审核跟踪将记录对源模式、工作流和选项执行的操作。 您可以快速查看元素是已创建、修改还是已删除。</p><p>For more information, refer to the <a href="../../production/using/audit-trail.md">detailed documentation</a> and <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">how-to video</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Guardrail、强健性和可伸缩性<br /> </td> 
   <td> 在Campaign Classic方面增加了一系列改进。 下面列出了护栏、强健性和可伸缩性改进。<br /> </td> 
  </tr> 
  <tr> 
   <td> 兼容性矩阵更新<br /> </td> 
   <td> 有了此新版本，Adobe Campaign现在支持以下数据库系统。 Refer to the <a href="https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html">Compatibility Matrix</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7(联合数据访问)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16(联合数据访问)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 出于安全原因，在工作流活动中使用选项时，您不 **[!UICONTROL Pre-process the file]** 能再插入任 **[!UICONTROL Data loading (file)]** 意命令。 现在提供一个下拉列表，允许您从3个选项中进行选择： **[!UICONTROL None]**、 **[!UICONTROL Decompression]** (zcat)或 **[!UICONTROL Decrypt]** (gpg)。 已添加XtkSecurity_Disable_Preproc安全标志。 对于新客户，此选项将设置为0。 对于现有客户，此选项将由配置级设置为1，以保持以前的行为。 Refer to this [section](../../workflow/using/data-loading--file-.md).
* 修复了在未设置时区的情况下测试联合数据访问外部帐户连接时发生的口令可见性问题。
* 已删除PDFBox库。
* Tomcat已更新至版本7.0.93。
* 修复了安全令牌无效时发生的令牌可见性问题。
* 修复了WSDL JSP(schemawsdl.jsp)中潜在的XTK注入问题。
* 已优化应用程序源代码和内存中的凭据和密码存储。
* PII视图限制已优化。 (NEO-12339、NEO-12396、NEO-12398、NEO-12339、NEO-12667)
* 修复了密钥管理中的不一致问题。
* 现在，对于使用有效或无效用户名的失败登录尝试显示相同的常规错误。
* 已增强已上载文件的命名。
* 新增了一个XtkSecurity_Disable_GetSetEnv选项以阻止使用setEnv和getEnv函数。
* 敏感信息现在隐藏在应用程序堆栈跟踪中。

**护栏、强健性和可伸缩性改进**

* 寿命- XtkNewId序列使用优化：最耗用的表已从xtkNewId序列移动到专用序列。 [阅读更多](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* 联合数据访问HTTP v2:联合数据访问HTTP协议广泛用于混合部署，尤其用于广泛的日志检索和投放准备。 增强了健壮性，以避免在检索或推送数据时出现网络问题和可能的错误。 这要求连接两端的构建都是最新的，否则仍将使用旧协议。
* 跟踪工作流：跟踪工作流的鲁棒性得到增强。 已修复与跟踪日志插入／更新和URL跟踪自定义相关的几个问题。 此外，跟踪工作流现在会检测可能导致错误的跟踪日志问题并停止该工作流。 这些问题现已丢弃，且未处理。
* 清除工作流：已改进清理工作流，以避免潜在错误和停止。 这将优化数据库大小和性能。
* 事务性消息中的嵌入图像：我们已在事务性消息中添加了对嵌入图像的完全支持，以避免可能的崩溃或丢失图像。
* 数据库大小- XtkJobLog:已将清除机制添加到此表。 这对数据库大小有积极影响。
* 密送存档：已更改BCC归档的默认参数以提高归档速度。 [阅读更多](../../installation/using/email-archiving.md#parameters)
* 数据库结构更新：数据库结构更新向导生成的SQL请求已得到改进，可加快执行速度。
* 操作员操作的护栏：已实施若干护栏，以防止运营商采取可能影响平台完整性的行动。 内置模式不再能通过界面删除。 此外，非管理员用户不再可以编辑工作流源XML。
* 提供了两个新选项： **XtkSecurity_Restrict_EditXML** (允许您禁用投放的XML代码版本)和 **NmsOperation_OperationMgtDebug** （允许您监视操作管理技术工作流执行）。 [阅读更多](../../installation/using/configuring-campaign-options.md)

**其他变更**

* 推送通知：现在，我们支持iOS推送的“线程ID”选项。
* 改进了长名称索引的管理，这些索引可能导致错误升级问题。
* 现在，在反编译分析投放期间，如果发布模式在部署向导 **[!UICONTROL None]** 中设置为，则会记录错误并停止分析:&quot;发布模式设置为&#39;none&#39;:无法嵌入图像。 功能电话上不显示图像。” (NEO-12208)
* 针对事务性消息传递，广播管理已得到改进。 当广播从执行实例同步到控制实例时，@lastModified字段将更新为系统的当前日期。 已为控制实例添加MC_Update_BlLastModified选项。 True表示当前日期将用于控制实例（默认行为）。 False表示我们使用执行实例广播的@lastModified日期。 (NEO-12579)
* 在优惠券临时表中添加了索引以优化投放发送。 (NEO-12437)
* 在Analytics集成中，现在允许检索包含%字符的AAM区段数据。 (NEO-12025)
* 已删除工作流热图中的10,000记录限制，以修复缺少的数据问题。 (NEO-12329)
* 不支持Open Office，现在已完全从应用程序中删除。 如果您仍在使用它，请转到Libre Office，因为从19.1开始它将不再工作。
* 您现在可以使用sysfilter属性限制对工作流中的“更新活动”的“写入”访问。 [阅读更多](../../configuration/using/filtering-schemas.md)

**修补程序**

* 修复了阻止为iOS移动推送通知上传证书的问题。
* 修复了事务推送通知的潜在重复服务器崩溃。 其他崩溃问题已修复。
* 修复了导致用户报告与打开的投放指示器的跟踪报告之间出现活动差异的问题。 (NEO-11742)
* 修复了IMS登录的问题。
* 修复了从库添加图像时可能导致投放中缺失图像的问题。 (NEO-11900)
* 修复了在直接邮件优惠中提取投放详细信息时可能发生的问题。 (NEO-11700)
* 修复了可能影响SMS事务性消息性能的问题。 (NEO-9812)
* 修复了在投放的主目标使用外部文件中的定义选项时可能发生的控制台崩溃。 (NEO-12349)
* 修复了分析消息时瞄准日语(.JP)域的收件人的问题。 (NEO-12246)
* 修复了在1:N链接中使用值分布时的显示问题。 (NEO-12212, NEO-11820)
* 修复了一个问题，该问题可能导致MTA日志中在错误升级后出现NmsMxDomain错误。 (NEO-12752)
* 修复了在扩充工作流活动中使用“从主集保留所有其他数据”选项时的问题。 (NEO-13291)
* 修复了使用HTTP2发送推送通知时的Tomcat崩溃问题。 (NEO-12701)
* 修复了HTTPRequest API的一个问题，该问题未等待所有回调完成。 (NEO-12628)
* 修复了事务性消息跟踪指示器的计算流程问题。 (NEO-12529)
* 修复了在主题管理中使用优惠的问题。 (NEO-11804)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了在优惠管理中预览出站XML或CSV文件以进行直接邮件投放时的问题。 (NEO-11290)
* 修复了安装管理社交 **网络(社交营销** )包时的问题。 (NEO-12081)
* 修复了一个问题，该问题导致您无法删除Web应用程序，即使您具有正确的访问权限也是如此。 (NEO-12072)
* 修复了在导出然后通过XML导入对象时，可能会覆盖某些值的问题。 已添加XtkExport_IncludeDefaultValues选项。 当设置为True（默认行为）时，将导出所有值。 设置为False时，修改将被默认值覆盖。 (NEO-11979)
* 修复了在添加活动 **[!UICONTROL Alert]** 后扩充活动时导致工作流查询失败的问题。 (NEO-12132)
* 修复了Oracle设置上的一个问题，该问题导致管线（触发器）偏移未从数据库成功检索，从而导致重复。 (NEO-12121)
* 修复了在使用Analytics集成时，可能导致透视表显示错误的问题(NEO-12103)
* 修复了描述性分析报表的问题。 (NEO-11414)
* 修复了远程表包含名称带有下划线的字段时CRM连接器的问题。
* 修复了可能导致假设验证报表中货币符号显示的问题。 (NEO-11634)
* 修复了在跟踪链接中使用某些字符时的重定向和跟踪问题。
* 修复了导致优惠预览无法正常工作的问题。
* 修复了软弹回未从地址表删除的问题。
* 修复了使用条码时的JAVA错误。
* 修复了Web应用程序中的翻译问题(NEO-12460)
* 修复了s3文件传输工作流活动的问题。 (NEO-12473)
* 修复了Web应用程序中日期字段的问题。 (NEO-12496)
* 修复了在投放中使用种子地址时ID耗尽的问题。 (NEO-11842)
* 修复了phantomjs和Debian 9兼容性的问题。
* 修复了批准验证内容时出错的问题。 (NEO-12725)
* 修复了“从填充中排除此子集”工作流功能的问题。 (NEO-12441)
* 修复了HTTPRequest-wait API的一个问题，该问题未等待所有回调完成。 (NEO-12628)
* 修复了拆分受众中“更新共享任务”活动的问题。 (NEO-11562)
* 修复了Web服务器崩溃问题。 (NEO-12904)
* 修复了事务模板中“自然”参数的问题。 (NEO-12334)
* 修复了在电子邮件文本编辑器中显示跟踪的URL时的控制台崩溃问题。 (NEO-13122)
* 修复了从活动导入受众时拆分文件Audience Manager的问题。 (NEO-11550)
* 修复了热点单击报告中导致错误的问题。 (NEO-11459)
* 修复了优惠渲染问题。 (NEO-11565)
* 修复了从列表导入受众时的活动更新Audience Manager的问题。 (NEO-11226)
* 修复了计划活动和时区配置的问题。 (NEO-11662)
* 修复了在URL格式错误时导致跟踪工作流失败的问题。
* 修复了导入移动应用程序包后外部帐户的问题。
* 修复了向操作员分配时区时的问题。 (NEO-12464)
* 修复了在匹配域日志中可能导致错误的问题。 (NEO-11539, NEO-8978)
* 修复了在已保存的报告中单击历史记录图标时的问题。 (NEO-11620)
* 修复了在报表中编辑透视表时的问题。 (NEO-12068)
