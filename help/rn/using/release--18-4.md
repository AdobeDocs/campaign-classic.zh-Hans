---
title: 版本18.4
seo-title: 版本18.4
description: 版本18.4
seo-description: null
page-status-flag: never-activated
uuid: d132570e-20e6-4550-95bd-176701f43b19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 4dc87ff3-eb6a-40ac-97ee-00b64cd7718d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# 版本18.4{#release-18-4}

## 版本18.4.5 —— 内部版本8937{#release-18-4-5-build-8937}

2018年11月21日

**改进**

* 修复了在FDA上使用MySQL运行工作流时的各种问题。 (NEO-11652)
* 修复了在特定情况下导致部分交付人口保持待定状态的问题。 (NEO-11336)
* 修复了SMS自动响应的间歇性问题。 (NEO-11811)
* 修复了在传送中使用种子地址时的ID耗尽问题。 (NEO-11842)
* 修复了在丰富化工作流活动中执行排序时的语法错误。 (NEO-11394)
* 修复了重新启动IIS时可能导致Web服务器崩溃的问题。 (NEO-10862)
* 修复了可能导致构建升级(FDA - SQL)后跟踪工作流失败的问题。 (NEO-11635)
* 修复了可能导致工作流列表数据丢失的问题。 (NEO-11696)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了阻止Web跟踪用于“com.au”域(NEO-4385)的问题。
* 修复了使用复杂工作流时可能发生的客户端冻结问题。 (NEO-11847)
* 修复了在选择特定方案的元素后保存新交付时出现的Oracle错误(NEO-11682)。
* 修复了在查询包含重音字符(FDA/Teradata)的字段时的问题。 外部帐户现在允许您更改用于与Teradata驱动程序通信的编码。 (NEO-11818)。
* 修复了在推送通知中传递其他变量中的URL时的跟踪问题，该问题可能会导致移动应用程序收到的格式错误或数据不正确。 (NEO-11468, NEO-11960)
* 修复了在1:N链接中使用值分布时导致显示问题的问题。 (NEO-11820)
* 修复了阻止批量加载在Teradata 16上工作的问题。
* 增加了Teradata上时间戳的缓冲区大小，以避免与15.10驱动程序发生绑定问题。
* 改进了长名称索引的管理，这可能会导致错误升级问题。
* 改进了子级死区处理(MTA)期间的共享内存可用时间。
* 修复了Apache（跟踪）中的潜在死锁。

## 版本18.4.4 —— 内部版本8936{#release-18-4-4-build-8936}

2018年8月1日

**改进**

* 电子邮件归档日志已得到增强，这样可以更轻松、更清晰地检查哪些电子邮件已通过密件抄送归档成功发送或失败。 (NEO-10675)
* 修复了导致在跟踪广播中显示负载平衡器IP而不是客户IP的问题。 (NEO-11295)
* 修复了在使用FDA连接到PostgreSQL数据库时LATIN1编码错误。 (NEO-11299)
* 修复了使用提交选项时出 **[!UICONTROL Prepare the personalization data with a workflow]** 现的问题。 (NEO-11047, NEO-11301)
* 修复了导致错误覆盖交付属性的随机问题。 (NEO-11015)
* 修复了在工作流活动中使用计算字段 **[!UICONTROL Survey answers]** 的问题。 (NEO-11382)
* 修复了在工作流活动中使用XML中存储的数据时 **[!UICONTROL Survey answers]** 的问题。 (NEO-10816)
* 修复了使用内部版本8935执行服务器升级时的问题。
* 修复了在工作流活动未完全配置时在配置升级日志中 **[!UICONTROL Survey answers]** 显示无用错误的问题。
* FDA Teradata:修复了SQL表中自动递增的字段和索引的问题。

## 版本18.4.3 —— 内部版本8935{#release-18-4-3-build-8935}

2018年6月22日

**改进**

* 修复了Microsoft edge和Internet explorer的跟踪编码问题。 (NEO-11257)
* 修复了LINE交付中的图像链接个性化问题。 (NEO-11077)
* 修复了ID序列生成机制无法正常工作的问题。 (NEO-11115)
* 修复了在使用具有整数类型协调密钥的自定义命名空间时，隐私(GDPR)请求无法工作的问题。 (NEO-11123)
* 修复了在工作流活动中使用选项时 **[!UICONTROL Distribution of values]** 可能发 **[!UICONTROL Query]** 生的错误。 (NEO-10958)
* 修复了将促销空间从营销实例同步到交互实例时的问题。 (NEO-11162)
* 改进了配置阶段长名称索引的管理

## 版本18.4.2 —— 内部版本8932{#release-18-4-2-build-8932}

2018年5月22日

**改进**

* 修复了导致Windows server更新无法正常工作的问题。
* 修复了使用XML中存 **[!UICONTROL Survey Result]** 储的数据时活动中的问题。 报告显示不正确。 (NEO-10816)
* 修复了使用弹回邮件服务器时inMail进程可能发生的性能问题。 (NEO-10641)
* 修复了在升级超过1000个架构时可能发生的数据库升级问题。

## 版本18.4 —— 内部版本8931{#release-18-4-build-8931}

2018年4月24日

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
   <td> 欧盟一般数据保护规定(GDPR)<br /> </td> 
   <td> <p>GDPR是欧盟(EU)的新隐私法，该法规将2018年5月25日生效的数据保护要求协调化并现代化。 GDPR 适用于所持有数据的数据主体位于欧盟的 Adobe Campaign 客户。</p> <p>除了Adobe Campaign中已有的隐私权（包括同意管理、数据保留设置和用户角色）外，我们还将作为数据处理者的角色利用此机会加入其他功能，以帮助您为某些GDPR请求做好数据管理者的准备：</p> 
    <ul> 
     <li> <p>访问权限：允许数据主体接收由数据管理者捕获的个人数据的副本，可能包括Adobe Campaign中存储的数据。</p> </li> 
     <li> <p>删除权：使数据主体能够擦除由数据管理者捕获的个人数据，可能包括存储在Adobe Campaign中的数据。</p> </li> 
    </ul> 有关详细信息，请参阅详 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">细文档</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用中的用户档案<br /> </td> 
   <td> <p>Adobe Campaign现在提供活动配置文件列表，通过专用工作流程每月更新。</p> <p>有关详细信息，请参阅详 <a href="../../platform/using/about-profiles.md#active-profiles">细文档</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> Android Push Connector增强功能<br /> </td> 
   <td> <p>Android连接器已得到增强以支持更高的吞吐量。 </p> <p>有关详细信息，请参阅详 <a href="../../delivery/using/configuring-the-mobile-application.md">细文档</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全增强**

* 现在禁用了外部实体的扩展功能，以防止未经身份验证的用户发生潜在攻击。 (NEO-10173)
* 增强的权限，以防止标准用户更改实例配置参数，如应用程序访问URL、LDAP设置等。 (NEO-10171)
* 修复了可通过堆栈跟踪显示敏感信息的问题。 错误详细信息现在记录在后端到外部网络无法访问的位置。 (NEO-10176)
* 增强的权限，以防止标准用户查看管理员上传的文档和／或导出的包。 (NEO-10170)

**改进**

* **LINE渠道——体系结构增强**:与Adobe Campaign中的所有其他渠道一样，LINE渠道现在支持所有部署类型：托管、混合和内部部署。
* **序列自动生成**:ID生成机制已得到增强，可延长具有大量对象的Campaign实例的寿命。 For more information, refer to this [technote](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html).

**其他更改**

* 使用命令行可以使用新模式导入包，从而允许循环依赖关系（对于大包，不建议使用此模式）。 有关详细信息，请参阅“技术演化”部分。 (NEO-8979)
* 改进了在Teradata中加载大量数据的性能，并修复了阻止显示日志中处理的正确数据值的问题。 (NEO-10429)
* 从Audience Manager导入受众现在可处理拆分文件。 以前，只有区段的最后一个文件是由importSharedAudience技术工作流导入的。 (NEO-10156)
* 在Windows上，Campaign服务器默认安装路径已更改。 启动64位版本设置时，默认安装路径现在为： **C:\Program Files\Adobe\Adobe Campaign Classic v7** ，而 **不是C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* 默认MX规则已得到增强，可包含更多域并优化吞吐量。
* 对部署向导SOAP调用(xtk:serverOptions#SaveOptions)强制实施访问限制。
* weka.jar过时的库已删除，OpenSSL库已更新，以便进行安全优化。
* 改进了付费技术工作流以保护实例性能。
* 管理员设置或重置任何操作员密码的功能已恢复。 要执行此操作，请右键单击某个运算符，选择 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 并设置该运算符的新密码。 我们建议运营商在首次重新连接时更改其口令。 有关详细信息，请参阅详 [细文档](../../production/using/lost-password.md)。
* 为了支持Adobe Target中新增的多租功能，现在在配置选项和外部帐户以与Target集成时，可以向URL添加新的“at_property”参数。 此参数的值可在Adobe Target中找到，Campaign在调用Target时将使用它。 有关详细信息，请参阅详 [细文档](../../integrations/using/inserting-a-dynamic-image.md)。
* 您现在可以指定在单击Adobe Target提供的图像时打开的默认登录页面。 以前，单击该图像会导致在创建电子邮件时出现默认图像集。 有关详细信息，请参阅详 [细文档](../../integrations/using/inserting-a-dynamic-image.md)。
* 在外 **部帐户中添加了“启用SMPP跟踪** ”复选框以强制执行跟踪输出。 有关详细信息，请参阅详 [细文档](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

**技术演进**

queryDef

queryDef已针对“orderBy”子句进行修改。 在更改之前，查询的表的主键将隐式添加到“orderBy”子句中。 在某些数据库引擎（至少是postgresql）上，它会阻止索引的使用（orderBy子句的所有字段必须由同一索引覆盖）。 如果您依赖于此行为，则必须在“orderBy”子句中显式添加主键。

例如，如果您有以下查询：

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

对于非ASCII字符，“urlEncode”JavaScript函数无法正常工作。 它已更正，现在应使用所有Unicode字符（包括日语字符）。 如果您依赖非ASCII字符的“urlEncode”行为，则必须调整代码。

包导入新模式

使用命令行可以使用新模式导入包，从而允许循环依赖关系（对于大包，不建议使用此模式）。 保留现有功能。 对于具有循环依赖关系的此类包，已 **在命令行包导入中添加了新标志-usejs** 。 执行时，它将像从接口执行包导入时一样使用JSEngine。

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**修补程序**

* 修复了将分发和跟踪日志从Adobe Campaign standard复制到Adobe Campaign Classic时的同步问题。 (NEO-10023)
* 修复了在快速加载操作失败后恢复ETL工作流时，Teradata中的错误和日志表处理问题。 现在，每次恢复工作流时，错误和日志表都会正确删除。 (NEO-10672)
* 修复了在安装FDA包时自动安装Hive包（Hadoop需要）的配置升级问题。 (NEO-10592)
* 修复了将无效域视为未定义错误 **的错误** 。 (NEO-10248)
* 修复了在发送android推送交付时，deliveryLogStats表中的日志重复的问题。 (NEO-10234)
* 修复了可能导致条形码扫描器无法读取某些条形码格式的问题。 (NEO-10125)
* 修复了在使用非ASCII字符时“urlEncode”JavaScript函数的问题。 有关详细信息，请参阅“技术演化”部分。 (NEO-10123)
* 修复了在Teradata数据库上执行包含sha256函数的查询时的问题。 (NEO-10119)
* 修复了使用超大的SalesForce表时SalesForce活动中可能发生的工作流内存错误。 (NEO-9900)
* 修复了在使用FDA时，在定 **位工作流活动中** ,“生成补充”选项的问题。 (NEO-9878)
* 修复了在使用中间采购时，可能导致 **营销实例上** 未更新 **** “已处理”和“成功”量度的问题。 (NEO-9454)
* 修复了在平台中总提供超过10k时的交互非重命题规则(NEO-9352)
* 修复了在使用XML外部文件时无法指定交付目标的问题。 (NEO-9312)
* 修复了在选件上运行假设并更新命题状态时可能导致工作流错误的问题。 (NEO-9304)
* 修复了在基于Android交付映射的属性使用压力规则进行交付分析时出现的错误。 (NEO-9202)
* 修复了在收件人列表中对列进行排序时可能导致性能问题的问题。 有关queryDef修改的详细信息，请参阅下面的“技术演变”部分。 (NEO-9042)
* 修复了批准电子邮件中的链接可能指向错误的登录URL的问题，尤其是在使用Federated ID登录类型时。 (NEO-9011)
* 修复了一个问题，该问题可能导致某些时区的报表的日期选择器中显示错误的日期。 (NEO-9007)
* 修复了在使用FDA SQL数据库时无法查看出站目标的问题。 (NEO-8924)
* 修复了导致MS Dynamics CRM连接器在每月前7天无法拉取数据的问题。 (NEO-8803)
* 修复了Analytics集成错误，该错误导致用户无法包含国际字符。 (NEO-8719)
* 修复了在没有相应权限的情况下启用工作流编辑的问题。 (NEO-8708)
* 修复了在混合架构中使用消息中心时FDA通过HTTP的问题，该问题会导致连接中断或连接丢失（超时）。 (NEO-8438)
* 修复了负ID的增量查询活动中出现的工作流错误。 (NEO-8229)
* 修复了可能导致在某些屏幕中显示双滚动条的问题。 (NEO-8208)
* 修复了导致运行更新数据库结构向导时显示错误消息的问题。 PostUpgrade将执行名称大于30的索引重命名。 请注意，对于大表，索引替换将需要时间。 (NEO-7983)
* 修复了跟踪日志无法从消息中心执行实例正确同步到控制实例的问题。 (NEO-7286)
* 修复了选件扩充活动的性能问题。 (NEO-7263)
* 修复了在通过FDA查询Redshift数据库时无法使用DaysAgo功能的问题。 (NEO-7099)
* 修复了数据管理中的回归问题，该回归问题导致在类似丰富化的工作流活动上无法创建索引。
* 修复了在创建标题为@id的外部资源时可能发生的问题
* 修复了通过FTP服务器上传压缩文件或在文件名中上传带有通配符的文件时可能出现的问题。
* 修复了在Campaign standard中创建的外部自定义资源中长基本类型枚举的问题。
* 修复了即使与提供商的连接失败导致SMS丢失也可能导致发送SMS的问题。
* 修复了导致SMTP连接无限期卡住的错误。
* 修复了在使用LINE映射时或过滤和定位架构不同时，在准备消息时压力类型规则存在的问题。
