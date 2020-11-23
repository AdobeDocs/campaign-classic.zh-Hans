---
solution: Campaign Classic
product: campaign
title: 版本 18.4
description: 版本 18.4
audience: rn
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2262'
ht-degree: 7%

---


# 版本 18.4{#release-18-4}

## 版本 18.4.5 - 版本 8937{#release-18-4-5-build-8937}

2018年11月21日

**改进**

* 修复了在工作流上使用MySQL运行联合数据访问时的各种问题。 (NEO-11652)
* 修复了导致部分投放口在特定情况下处于待定状态的问题。 (NEO-11336)
* 修复了SMS自动响应的间歇性问题。 (NEO-11811)
* 修复了在投放中使用种子地址时ID耗尽的问题。 (NEO-11842)
* 修复了在扩充工作流活动中执行排序时出现的语法错误。 (NEO-11394)
* 修复了在重新启动IIS时可能导致Web服务器崩溃的问题。 (NEO-10862)
* 修复了在生成升级(联合数据访问- SQL)后可能导致跟踪工作流失败的问题。 (NEO-11635)
* 修复了可能导致工作流列表数据丢失的问题。 (NEO-11696)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了阻止Web跟踪用于“com.au”域(NEO-4385)的问题。
* 修复了使用复杂工作流时可能发生的客户端冻结问题。 (NEO-11847)
* 修复了在选择特定投放的元素后保存新模式时出现的Oracle错误(NEO-11682)。
* 修复了查询包含重音字符(联合数据访问/Teradata)的字段时的问题。 该外部帐户现在允许您更改用于与Teradata驱动程序通信的编码。 (NEO-11818).
* 修复了在推送通知中传递其他变量中的URL时的跟踪问题，该问题可能会导致移动应用程序收到的格式错误或数据不正确。 (NEO-11468, NEO-11960)
* 修复了在使用1:N链接的值分布时导致显示问题的问题。 (NEO-11820)
* 修复了阻止批量加载在Teradata16上工作的问题。
* 增加了Teradata上时间戳的缓冲区大小，以避免与15.10驱动程序绑定问题。
* 改进了长名称索引的管理，这些索引可能导致错误升级问题。
* 改进了子级死区处理(MTA)期间的共享内存可用时间。
* 修复了Apache（跟踪）中的潜在死锁。

## 版本 18.4.4 - 版本 8936{#release-18-4-4-build-8936}

2018年8月1日

**改进**

* 电子邮件归档日志已得到增强，这使得检查哪些电子邮件已通过密送归档成功发送或失败变得更简单、更清晰。 (NEO-10675)
* 修复了导致在跟踪广播中显示负载平衡器IP而非客户IP的问题。 (NEO-11295)
* 修复了使用PostgreSQL联合数据访问库的连接时LATIN1编码错误。 (NEO-11299)
* 修复了使用投放选项时发 **[!UICONTROL Prepare the personalization data with a workflow]** 生的问题。 (NEO-11047, NEO-11301)
* 修复了导致投放属性被错误覆盖的随机问题。 (NEO-11015)
* 修复了在工作流活动中使用计算字段 **[!UICONTROL Survey answers]** 时的问题。 (NEO-11382)
* 修复了在工作流活动中使用XML中存储的数据时 **[!UICONTROL Survey answers]** 的问题。 (NEO-10816)
* 修复了使用内部版本8935执行服务器升级时的问题。
* 修复了在工作流活动未完全配置时，在配置级别日志中 **[!UICONTROL Survey answers]** 显示无用错误的问题。
* 联合数据访问Teradata:修复了SQL表中自动递增的字段和索引的问题。

## 版本 18.4.3 - 版本 8935{#release-18-4-3-build-8935}

2018年6月22日

**改进**

* 修复了Microsoft Edge和Internet Explorer的跟踪编码问题。 (NEO-11257)
* 修复了LINE投放中图像链接个性化的问题。 (NEO-11077)
* 修复了ID序列生成机制无法正常工作的问题。 (NEO-11115)
* 修复了在使用整数类型命名空间的自定义合并关键项时，隐私权(GDPR)请求无法工作的问题。 (NEO-11123)
* 修复了在工作流活动中使用选项 **[!UICONTROL Distribution of values]** 时可能发 **[!UICONTROL Query]** 生的错误。 (NEO-10958)
* 修复了将优惠空间从营销实例同步到交互实例时的问题。 (NEO-11162)
* 改进了配置升级期间长名称索引的管理

## 版本 18.4.2 - 版本 8932{#release-18-4-2-build-8932}

2018年5月22日

**改进**

* 修复了导致Windows Server更新无法正常工作的问题。
* 修复了使用XML中 **[!UICONTROL Survey Result]** 存储的活动时的问题。 报告显示不正确。 (NEO-10816)
* 修复了使用弹回邮件服务器时，inMail进程可能发生的性能问题。 (NEO-10641)
* 修复了在升级超过1000个模式时可能发生的数据库升级问题。

## 版本 18.4 - 版本 8931{#release-18-4-build-8931}

2018年4月24日

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
   <td> EU General Data Protection Regulation (GDPR)<br /> </td> 
   <td> <p>GDPR是欧洲合并(EU)的新隐私法，它协调将于2018年5月25日生效的数据保护要求并使其现代化。 GDPR 适用于所持有数据的数据主体位于欧盟的 Adobe Campaign 客户。</p> <p>除了Adobe Campaign中已具备的隐私权功能（包括同意管理、数据保留设置和用户角色）之外，我们还将作为数据处理者的角色利用这一机会加入其他功能，以帮助您为某些GDPR请求做好数据管理者的准备工作：</p> 
    <ul> 
     <li> <p>访问权限：允许数据主体接收由数据管理者捕获的个人数据的副本，可能包括存储在Adobe Campaign中的数据。</p> </li> 
     <li> <p>删除权：数据主体有权擦除其由数据管理者捕获的个人数据，可能包括以Adobe Campaign存储的数据。</p> </li> 
    </ul> 有关详细信息，请参阅<a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html">详细文档</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用中的用户档案<br /> </td> 
   <td> <p>Adobe Campaign现在提供活动用户档案的列表，通过专用工作流每月更新一次。</p> <p>有关详细信息，请参阅<a href="../../platform/using/about-profiles.md#active-profiles">详细文档</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> Android推送连接器增强功能<br /> </td> 
   <td> <p>Android连接器已得到增强以支持更高的吞吐量。 </p> <p>有关详细信息，请参阅<a href="../../delivery/using/configuring-the-mobile-application.md">详细文档</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 现在禁用了外部实体的扩展，以防止未经身份验证的用户发生潜在攻击。 (NEO-10173)
* 加强权限，防止标准用户更改实例配置参数，如应用程序访问URL、LDAP设置等。 (NEO-10171)
* 修复了可通过堆栈跟踪显示敏感信息的问题。 错误详细信息现在记录在后端到外部网络无法访问的位置。 (NEO-10176)
* 强化权限，防止标准用户查看管理员的已上载文档和／或导出的包。 (NEO-10170)

**改进**

* **LINE渠道-架构增强**:与Adobe Campaign中的所有其他渠道一样，LINE渠道现在在所有部署类型中都受支持：托管、混合和内部部署。
* **序列自动生成**:ID生成机制已得到增强，可增加具有大量对象的活动实例的寿命。 For more information, refer to this [technote](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html).

**其他变更**

* 使用命令行可以使用新模式导入包，从而允许循环依赖项（对于大包，不推荐使用）。 有关详细信息，请参阅“技术演化”部分。 (NEO-8979)
* 改进了在Teradata进行大量数据加载的性能，并修复了无法显示日志中处理数据的正确值的问题。 (NEO-10429)
* 从Audience Manager导入受众现在可以处理拆分文件。 以前，只有区段的最后一个文件是由importSharedAudience技术工作流导入的。 (NEO-10156)
* 在Windows上，活动服务器默认安装路径已更改。 启动64位版本设置时，默认安装路径现在为： **C:\Program Files\Adobe\Adobe Campaign Classic v7** 而不 **是C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* 默认MX规则已得到增强，可包含更多域并优化吞吐量。
* 对部署向导SOAP调用(xtk:serverOptions#SaveOptions)强制实施访问限制。
* weka.jar过时库已删除，OpenSSL库已更新，可进行安全优化。
* 改进了付费技术工作流以保护实例性能。
* 管理员设置或重置任何操作员的口令的功能已恢复。 为此，请右键单击运算符，选择 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 并设置运算符的新密码。 我们建议运营商在首次重新连接时更改其口令。 有关详细信息，请参阅[详细文档](../../production/using/lost-password.md)。
* 为支持Adobe Target的新多租功能，在配置选项和外部帐户以与目标集成时，现在可以向URL添加一个新的“at_property”参数。 此参数的值可在Adobe Target找到，活动在执行对目标的调用时将使用。 有关详细信息，请参阅[详细文档](../../integrations/using/inserting-a-dynamic-image.md)。
* 现在，您可以指定在单击由Adobe Target提供的图像时打开的默认登陆页。 以前，单击该图像会导致在创建电子邮件时出现默认图像集。 有关详细信息，请参阅[详细文档](../../integrations/using/inserting-a-dynamic-image.md)。
* 在外部帐户 **中添加了** “启用SMPP跟踪”复选框以强制跟踪输出。 有关详细信息，请参阅[详细文档](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

**技术演进**

queryDef

queryDef已针对“orderBy”子句进行修改。 在更改之前，查询的表的主键将隐式添加到“orderBy”子句中。 在某些数据库引擎（至少是postgresql）上，它会阻止索引的使用（orderBy子句的所有字段必须由同一索引覆盖）。 如果您依赖于此行为，则必须在“orderBy”子句中显式添加主键。

例如，如果您具有以下查询:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

它将隐含地作为（在18.4更改之前）:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitely added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode函数

对于非ASCII字符，“urlEncode”JavaScript函数无法正常工作。 它已得到更正，现在应使用所有Unicode字符（包括日文字符）。 如果您依赖非ASCII字符的“urlEncode”行为，则必须调整代码。

包导入新模式

使用命令行可以使用新模式导入包，从而允许循环依赖项（对于大包，不推荐使用）。 保留现有功能。 对于具有循环依赖关系的此类包， **已向命令行** 包导入添加了新标志-usejs。 执行时，它将像从接口执行包导入时一样使用JSEngine。

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**修补程序**

* 修复了将投放和跟踪日志从Adobe Campaign Standard复制到Adobe Campaign Classic时的同步问题。 (NEO-10023)
* 修复了在快速加载操作失败后恢复ETL工作流时，在Teradata处理错误和日志表的问题。 现在，每次恢复工作流时，错误和日志表都会正确删除。 (NEO-10672)
* 修复了在安装了配置包时自动安装配置包(Hadoop需要)的配置升级问题。 (NEO-10592)
* 修复了将无效域视为未定义 **错误的错** 误。 (NEO-10248)
* 修复了在发送android推送投放时，deliveryLogStats表中的日志重复的问题。 (NEO-10234)
* 修复了可能导致条形码扫描程序无法读取某些条形码格式的问题。 (NEO-10125)
* 修复了在使用非ASCII字符时“urlEncode”JavaScript函数的问题。 有关详细信息，请参阅“技术演化”部分。 (NEO-10123)
* 修复了在Teradata查询库上执行包括sha256功能的时的问题。 (NEO-10119)
* 修复了使用超大SalesForce表时SalesForce活动中可能发生的工作流内存错误。 (NEO-9900)
* 修复了在使用活动时 **定位工作流** 联合数据访问中生成补充选项的问题。 (NEO-9878)
* 修复了在使用中间源时，可能导致 **营销实** 例上 **“已处** 理”和“成功”量度不能更新的问题。 (NEO-9454)
* 在平台中总优惠超过10k时，固定交互非重命题规则(NEO-9352)
* 修复了在使用XML外部文件时无法指定投放目标的问题。 (NEO-9312)
* 修复了在假设验证上运行优惠并更新提议状态时可能导致工作流错误的问题。 (NEO-9304)
* 修复了根据Android投放映射的属性使用压力规则时在分析投放期间出现的错误。 (NEO-9202)
* 修复了在收件人列表中对列排序时可能导致性能问题的问题。 有关queryDef修改的详细信息，请参阅下面的“技术演化”部分。 (NEO-9042)
* 修复了审批电子邮件中的链接可能指向错误的登录URL的问题，尤其是在使用Federated ID登录类型时。 (NEO-9011)
* 修复了一个问题，该问题可能导致某些时区报表的日期选择器中显示错误日期。 (NEO-9007)
* 修复了在使用目标SQL数据库时无法查看出站联合数据访问的问题。 (NEO-8924)
* 修复了导致MS Dynamics CRM连接器在每月前7天无法拉取数据的问题。 (NEO-8803)
* 修复了Analytics集成错误，该错误导致用户无法包含国际字符。 (NEO-8719)
* 修复了在没有适当权限的情况下启用工作流编辑的问题。 (NEO-8708)
* 修复了在混合架构中使用消息中心时联合数据访问HTTP的问题，该问题会导致连接中断或连接丢失（超时）。 (NEO-8438)
* 修复了负ID的增量查询活动中出现的工作流错误。 (NEO-8229)
* 修复了可能导致在某些屏幕中显示多次滚动条的问题。 (NEO-8208)
* 修复了导致运行更新数据库结构向导时显示错误消息的问题。 PostUpgrade将执行名称大于30的索引重命名。 请注意，对于大表，索引替换将需要时间。 (NEO-7983)
* 修复了跟踪日志无法从消息中心执行实例正确同步到控制实例的问题。 (NEO-7286)
* 修复了优惠扩充活动的性能问题。 (NEO-7263)
* 修复了在通过联合数据访问查询Redshift数据库时无法使用DaysAgo函数的问题。 (NEO-7099)
* 修复了数据管理中的回归，该回归阻止了在类似扩充的工作流活动上创建索引。
* 修复了在创建标题为@id的外部资源时可能出现的问题
* 修复了通过FTP服务器上传压缩文件或在文件名称中上传带有通配符的文件时可能发生的问题。
* 修复了外部自定义资源中创建为明细列表的长基类型Campaign Standard的问题。
* 修复了即使与提供商的连接失败，也会导致SMS丢失的问题。
* 修复了导致SMTP连接无限期卡住的错误。
* 修复了在使用LINE映射或筛选和定位类型规则不同时在消息准备过程中压力模式的问题。
