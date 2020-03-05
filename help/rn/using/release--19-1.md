---
title: 版本19.1
seo-title: 版本19.1
description: 版本19.1
seo-description: null
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
source-git-commit: fd7bc26fe12a26d8fb0dcccd2135b799e76b52bd

---


# 版本19.1{#release-19-1}

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
   <td>提供最新的稳定版本。 构建在生产中验证的内容。<br> </td>
   <td>由Adobe验证的构建。 等待生产校样。<br> </td>
   <td>可用于错误修复的更新版本。 需要更新。<br> </td>
   <td>包含已知的回归。 更新是必需的。<br> </td>
  </tr> 
 </tbody> 
</table>

最 **后一个稳定版本** 为9032(205c981c3)。 单击此 [处](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/orange_2.png) 版本19.1.6 —— 内部版本9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>此版本仅适用于内部部署安装。 对于混合部署，托管实例将继续运行9032版本。 请勿将您的营销实例升级到9035版本，因为它与9032不兼容。

_2019年10月3日_

**改进**

* 修复了在使用CRM Connector for Salesforce时的问题。 (NEO-17712)
* 修复了在发送事务性消息时可能导致性能问题的索引问题。
* 修复了发送消息时的性能问题。 (NEO-17558)
* 修复了一个问题，该问题可能导致某些消息无法由中间采购服务器处理。 (NEO-12395)
* 修复了导致无法充分使用SQL数据管理活动（缺少名为right的“SQL数据管理”）的问题。

## ![](assets/orange_2.png) 版本19.1.5 —— 内部版本9033{#release-19-1-5-build-9033}

_2019年8月13日_

**改进**

* 修复了在数据管理活动中提取数据期间在默认数据库而不是FDA数据库上执行的SQL语句“SELECT COUNT”的问题。
* 为了改进客户基础架构功能，服务器配置文件中现在提供了SFTP代理声明。
* 修复了在没有表名的数据加载(RDBMS)工作流活动中“添加链接表”时客户端控制台崩溃的问题。 (NEO-12213)
* 修复了通过命令行安装midEmetter包的问题。
* 新增了一个身份验证选项，用于在带Microsoft Dynamics的AC连接器内支持OAuth凭据。 (NEO-11982)
* 修复UUID（唯一通用标识符）问题会导致Hive FDA的浓缩活动失败。

## 版本19.1.4 —— 内部版本9032{#release-19-1-4-build-9032}

![](assets/green_2.png) 2020 **年3月5日**:新版本(9032-...205c981c3)，其中包括以下修复：

* 修复了使用FTP over SSL的外部帐户的问题。 (NEO-20498)

![](assets/orange_2.png) 2019 **年12月17日**:新版本(9032-...9d34fb17e)，包括以下修复：

* 修复了以下通信渠道上的跟踪问题：移动(SMS、MMS)、推送(iOS、Android)和社交网络(Facebook、Twitter)。
(NEO-19595)

![](assets/orange_2.png) 2019 **年12月11日**:新版本(9032-...e28b428b7)，包括以下修复：

* 修复了在发送包含MSSQL数据库的消息时的性能问题。 (NEO-17558)

![](assets/orange_2.png) 2019 **年11月20日**:新版本(9032-...3468c7bb5)，包含以下修复：

* 修复了通过IMS身份验证的登录问题。 (NEO-17312)
* 修复了显示多个分发的累积报告时的问题。 (NEO-18165)
* 修复了可能阻止或导致Web服务器崩溃的问题。

![](assets/orange_2.png) 2019 **年9月19日**:新版本(9032-...cee805c93)，其中包括以下修复：

* 修复了在使用CRM Connector for Salesforce时的问题。 (NEO-17712)
* 修复了在发送事务性消息时可能导致性能问题的索引问题。

![](assets/orange_2.png) 2019 **年8月13日**:初始19.1.4版本，包括以下修复：

* 修复了在向导配置过程中调度程序活动生成不需要的错误消息的问题。 从NEO-11662还原更新。 (NEO-17097)
* 修复了由NEO-12727导致的回归，该回归可能导致在执行两次测试活动时工作流停止。 (NEO-16835)
* 修复了在API调用中使用无效或过期的会话令牌时导致返回错误的HTTP代码（HTTP 200 OK而不是HTTP 403已禁止）的问题。 (NEO-16826)
* 修复了DKIM密钥的问题，该问题不再嵌入到电子邮件中，从而导致可交付性问题。 (NEO-16804)
* 修复了工作流计划的各种问题。 将工作流安排为每天执行一次，而不考虑调度程序配置。 (NEO-16619, NEO-16426)

## ![](assets/orange_2.png) 版本19.1.2 —— 内部版本9029{#release-19-1-2-build-9029}

_2019年6月21日_

**安全增强**

* 为优化安全性，Java库(Netty)已更新至最新版本(4.1.34)。 (NEO-12788)

**改进**

* 修复了链接到域列管理的回归，该回归可防止在某些配置上发送电子邮件。
* 为了提高性能，已将_operation=&quot;none&quot;属性添加到rtEvent SOAP调用中以避免“SELECT FOR UPDATE”请求。
* 修复了测试活动后出站过渡的工作流显示问题。 (NEO-12727)
* 现在，我们允许在导入工作流程期间删除在Microsoft Dynamics中创建的虚拟记录。
* 改进了在使用内部帐户时执行安全区包的权限。

## ![](assets/orange_2.png) 版本19.1 —— 内部版本9026{#release-19-1-build-9026}

_2019年5月30日_

**有什么新增功能？**

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
   <td> <p>要提高管理员用户的工作效率，请通过监控存储、将IP地址列入白名单以及为每个实例安装SSH密钥来管理SFTP服务器的设置。 请注意，控制面板仅适用于今天起在AWS上托管的客户(<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">今天通过Experience Cloud登录</a>)。</p> <p>有关详细信息，请参 <a href="https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html">阅详细文档</a><a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">和操作方法视频</a>。 </p><p>注意：访问控制面板不需要升级到最新的Campaign版本。</p> </td> 
  </tr> 
    <tr> 
   <td> 审核跟踪<br /> </td> 
   <td> <p>作为管理员，通过监视和管理Adobe Campaign Classic实例中所做的更改来提高工作效率。 审核跟踪将记录对源架构、工作流和选项执行的操作。 您可以快速查看是否已创建、修改或删除元素。</p><p>有关详细信息，请参阅详 <a href="../../production/using/audit-trail.md">细文档</a><a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">和操作方法视频</a>。</p></td> 
  </tr> 
  <tr> 
   <td> Guardrail、强健性和可伸缩性<br /> </td> 
   <td> 系列改进已添加到Campaign Classic。 下面列出了增强的安全性、强健性和可伸缩性。<br /> </td> 
  </tr> 
  <tr> 
   <td> 兼容性矩阵更新<br /> </td> 
   <td> Adobe Campaign现在支持以下数据库系统。 请参阅兼 <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">容性表</a>。<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7(FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16(FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**安全增强**

* 出于安全原因，在工作流活动中使用该选项时，您不 **[!UICONTROL Pre-process the file]** 能再插入任 **[!UICONTROL Data loading (file)]** 意命令。 现在提供了一个下拉列表，允许您从3个选项中进行选择： **[!UICONTROL None]**、 **[!UICONTROL Decompression]** (zcat)或 **[!UICONTROL Decrypt]** (gpg)。 已添加XtkSecurity_Disable_Preproc安全标志。 对于新客户，此选项将设置为0。 对于现有客户，此选项将由配置级设置为1以保持先前的行为。 请参阅此 [部分](../../workflow/using/data-loading--file-.md)。
* 修复了在未设置时区的情况下测试FDA外部帐户连接时出现的口令可见性问题。
* 已删除PDFBox库。
* Tomcat已更新至版本7.0.93。
* 修复了安全令牌无效时发生的令牌可见性问题。
* 修复了WSDL JSP(schemawsdl.jsp)中潜在的XTK注入问题。
* 应用程序源代码和内存中的凭证和密码存储已优化。
* PII视图限制已优化。 (NEO-12339、NEO-12396、NEO-12398、NEO-12339、NEO-12667)
* 修复了密钥管理中的不一致问题。
* 对于使用有效或无效用户名的失败登录尝试，现在会显示相同的常规错误。
* 已上传文件的命名已得到增强。
* 新增了一个XtkSecurity_Disable_GetSetEnv选项以阻止setEnv和getEnv函数的使用。
* 敏感信息现在隐藏在应用程序堆栈跟踪中。

**Guardrail、强健性和可伸缩性改进**

* 寿命- XtkNewId序列使用优化：最耗用的表已从xtkNewId序列移到专用序列。 [阅读更多](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* 通过HTTP v2的FDA:fda over HTTP协议广泛用于混合部署，尤其用于广泛的日志检索和交付准备。 增强了健壮性，以避免在检索或推送数据时出现网络问题和可能的错误。 这要求连接两端的内部版本保持最新，否则仍将使用旧协议。
* 跟踪工作流：跟踪工作流的鲁棒性得到增强。 已修复与跟踪日志插入／更新和URL跟踪自定义相关的几个问题。 此外，跟踪工作流现在会检测可能导致错误的跟踪日志问题并停止该工作流。 这些问题现在被丢弃且未得到处理。
* 清除工作流：已改进清理工作流，以避免潜在错误和停止。 这将优化数据库大小和性能。
* 交易消息中的嵌入图像：我们在事务性消息中添加了对嵌入图像的完全支持，以避免可能的崩溃或丢失图像。
* 数据库大小- XtkJobLog:已将清除机制添加到此表。 这对数据库大小有积极影响。
* 密送存档：BCC归档的默认参数已更改，以提高归档速度。 [阅读更多](../../installation/using/email-archiving.md#parameters)
* 数据库结构更新：数据库结构更新向导生成的SQL请求已得到改进，可加快执行速度。
* 操作符操作的护栏：已实施若干保护栏以防止运营商执行可能影响平台完整性的操作。 内置架构无法再通过界面删除。 此外，非管理员用户不再可以编辑工作流源XML。
* 提供了两个新选项： **XtkSecurity_Restrict_EditXML** （允许您禁用交付版本的XML代码）和 **NmsOperation_OperationMgtDebug** （允许您监视操作管理技术工作流执行）。 [阅读更多](../../installation/using/configuring-campaign-options.md)

**其他更改**

* 推送通知：我们现在支持iOS推送的线程ID选项。
* 改进了长名称索引的管理，这可能会导致错误升级问题。
* 现在，在分析反编译交付过程中，如果发布模式在部署向导中 **[!UICONTROL None]** 设置为，则会记录一个错误并停止分析：“发布模式设置为‘无’:无法嵌入图像。 功能电话上不显示图像。” (NEO-12208)
* 针对事务性消息传递改进了广播管理。 当广播从执行实例同步到控制实例时，@lastModified字段将更新为系统的当前日期。 MC_Update_BlLastModified选项已添加用于控制实例。 True表示当前日期将用于控件实例（默认行为）。 False表示我们使用执行实例广播的@lastModified日期。 (NEO-12579)
* 在优惠券临时表中添加了索引以优化交付发送。 (NEO-12437)
* 在Analytics集成中，现在允许检索字符为%的AAM区段数据。 (NEO-12025)
* 删除了“工作流热图”中的10,000记录限制以修复缺少的数据问题。 (NEO-12329)
* 不支持Open Office，现在已完全从应用程序中删除。 如果您仍在使用它，请转到Libre Office，因为从19.1开始它将不再工作。
* 您现在可以使用sysfilter属性限制对工作流中更新数据活动的写入访问。 [阅读更多](../../configuration/using/filtering-schemas.md)

**修补程序**

* 修复了阻止为iOS移动推送通知上传证书的问题。
* 修复了事务推送通知的潜在重复服务器崩溃问题。 其他崩溃问题已修复。
* 修复了导致用户活动与打开的交付指示器的跟踪报告不一致的问题。 (NEO-11742)
* 修复了IMS登录的问题。
* 修复了在从库添加图像时可能导致传送中丢失图像的问题。 (NEO-11900)
* 修复了在直邮发送中提取选件详细信息时可能发生的问题。 (NEO-11700)
* 修复了可能影响SMS交易消息性能的问题。 (NEO-9812)
* 修复了在外部文件选项中为分发的主要目标使用“已定义”时可能发生的控制台崩溃问题。 (NEO-12349)
* 修复了分析日文(.JP)域的目标收件人的消息时的问题。 (NEO-12246)
* 修复了在1:N链接中使用值分布时的显示问题。 (NEO-12212, NEO-11820)
* 修复了一个问题，该问题可能会导致MTA日志中在配置升级后出现NmsMxDomain错误。 (NEO-12752)
* 修复了在丰富化工作流活动中使用“保留主集的所有其他数据”选项时的问题。 (NEO-13291)
* 修复了使用HTTP2发送推送通知时的Tomcat崩溃问题。 (NEO-12701)
* 修复了HTTPRequest API的一个问题，该问题未等待所有回调完成。 (NEO-12628)
* 修复了事务性消息跟踪指示符的计算过程的问题。 (NEO-12529)
* 修复了在选件管理中使用主题的问题。 (NEO-11804)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了在选件管理中预览出站XML或CSV文件以进行直邮发送时的问题。 (NEO-11290)
* 修复了安装“管理社交网络 **** （社交营销）”包时的问题。 (NEO-12081)
* 修复了即使您拥有正确的访问权限也无法删除Web应用程序的问题。 (NEO-12072)
* 修复了在通过XML导出和导入对象时，可能导致某些值被覆盖的问题。 已添加XtkExport_IncludeDefaultValues选项。 设置为True（默认行为）时，将导出所有值。 设置为False时，修改将被默认值覆盖。 (NEO-11979)
* 修复了在查询后添 **[!UICONTROL Alert]** 加丰富化活动时导致工作流活动失败的问题。 (NEO-12132)
* 修复了Oracle设置上的一个问题，该问题导致管线（触发器）偏移未从数据库成功检索并导致重复。 (NEO-12121)
* 修复了在使用Analytics集成时，导致透视表中显示错误的问题(NEO-12103)
* 修复了描述性分析报告的问题。 (NEO-11414)
* 修复了CRM连接器在远程表名称中包含带下划线的字段时的问题。
* 修复了可能导致假设报告中货币符号显示问题的问题。 (NEO-11634)
* 修复了在跟踪链接中使用某些字符时的重定向和跟踪问题。
* 修复了导致选件预览无法正常工作的问题。
* 修复了软弹回未从地址表中删除的问题。
* 修复了使用条形码时的JAVA错误。
* 修复了Web应用程序中的翻译问题(NEO-12460)
* 修复了s3文件传输工作流活动的问题。 (NEO-12473)
* 修复了Web应用程序中的日期字段问题。 (NEO-12496)
* 修复了在传送中使用种子地址时的ID耗尽问题。 (NEO-11842)
* 修复了phantomjs和Debian 9兼容性的问题。
* 修复了批准证明内容时出错的问题。 (NEO-12725)
* 修复了“从人口中排除此子集”工作流功能的问题。 (NEO-12441)
* 修复了HTTPRequest-wait API的一个问题，该问题未等待所有回调完成。 (NEO-12628)
* 修复了拆分活动中的“更新共享受众”任务的问题。 (NEO-11562)
* 修复了Web服务器崩溃问题。 (NEO-12904)
* 修复了事务模板中的“自然”参数的问题。 (NEO-12334)
* 修复了在电子邮件文本编辑器中显示跟踪的URL时的控制台崩溃问题。 (NEO-13122)
* 修复了从Audience Manager导入受众时“拆分文件”活动的问题。 (NEO-11550)
* 修复了导致热点单击报告错误的问题。 (NEO-11459)
* 修复了选件呈现的问题。 (NEO-11565)
* 修复了从Audience Manager导入受众时“列表更新”活动的问题。 (NEO-11226)
* 修复了计划活动和时区配置的问题。 (NEO-11662)
* 修复了在URL格式错误的情况下导致跟踪工作流失败的问题。
* 修复了导入移动应用程序包后外部帐户的问题。
* 修复了将时区分配给操作员时的问题。 (NEO-12464)
* 修复了可能导致匹配字段日志错误的问题。 (NEO-11539, NEO-8978)
* 修复了在保存的报告中单击“历史记录”图标时的问题。 (NEO-11620)
* 修复了在报表中编辑透视表时的问题。 (NEO-12068)
