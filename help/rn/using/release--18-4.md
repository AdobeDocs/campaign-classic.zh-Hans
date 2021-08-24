---
product: campaign
title: Campaign 18.4发行说明
description: Campaign 18.4发行说明
exl-id: bbad81ba-a09f-4d67-9309-628ea7a08c9b
source-git-commit: 2a92cfc705e27332cfdf8c7357a6a03c84dc6c9f
workflow-type: tm+mt
source-wordcount: '2267'
ht-degree: 7%

---

# 18.4 版{#release-18-4}

## 18.4.5 版 - 内部版本 8937{#release-18-4-5-build-8937}

2018年11月21日

**改进**

* 修复了在FDA上使用MySQL运行工作流时的各种问题。 (NEO-11652)
* 修复了在特定情况下导致部分投放群体保持待定状态的问题。 (NEO-11336)
* 修复了短信自动响应的间歇性问题。 (NEO-11811)
* 修复了在投放中使用种子地址时的ID耗尽问题。 (NEO-11842)
* 修复了在扩充工作流活动中执行排序时的语法错误。 (NEO-11394)
* 修复了重新启动IIS时可能导致Web服务器崩溃的问题。 (NEO-10862)
* 修复了在升级内部版本(FDA - SQL)后可能导致跟踪工作流失败的问题。 (NEO-11635)
* 修复了可能导致工作流列表数据丢失的问题。 (NEO-11696)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了Web跟踪无法用于“com.au”域(NEO-4385)的问题。
* 修复了在使用复杂工作流时可能发生的客户端冻结问题。 (NEO-11847)
* 修复了在选择特定架构的元素后保存新投放时的Oracle错误(NEO-11682)。
* 修复了查询包含带重音符的字段(FDA/Teradata)时的问题。 现在，外部帐户允许您更改用于与Teradata驱动程序通信的编码。 (NEO-11818).
* 修复了在推送通知中以其他变量传递URL时可能导致移动设备应用程序收到格式错误或数据不正确的跟踪问题。 (NEO-11468, NEO-11960)
* 修复了在将值分布与1:N链接结合使用时导致显示问题的问题。 (NEO-11820)
* 修复了批量加载无法在Teradata16上工作的问题。
* 增加了Teradata上时间戳的缓冲大小，以避免15.10驱动程序的绑定问题。
* 改进了对可能导致升级后问题的长名称索引的管理。
* 改进了子代死机处理(MTA)期间的共享内存可用时间。
* 修复了Apache（跟踪）中的潜在死锁。

## 18.4.4 版 - 内部版本 8936{#release-18-4-4-build-8936}

2018年8月1日

**改进**

* 电子邮件存档日志已得到增强，这使得检查哪些电子邮件已成功发送或通过密送存档失败变得更加容易和清晰。 (NEO-10675)
* 修复了导致在跟踪广播中显示负载平衡器IP而不是客户IP的问题。 (NEO-11295)
* 修复了使用FDA连接到PostgreSQL数据库时LATIN1编码错误。 (NEO-11299)
* 修复了使用&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;提交选项时发生的问题。 (NEO-11047, NEO-11301)
* 修复了导致投放属性被错误覆盖的随机问题。 (NEO-11015)
* 修复了在&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流活动中使用计算字段时的问题。 (NEO-11382)
* 修复了在&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流活动中使用XML中存储的数据时的问题。 (NEO-10816)
* 修复了在版本8935中执行服务器升级时的问题。
* 修复了在&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流活动未完全配置时，在升级后日志中显示无用错误的问题。
* FDATeradata:修复了SQL表中自动递增的字段和索引的问题。

## 18.4.3 版 - 内部版本 8935{#release-18-4-3-build-8935}

2018年6月22日

**改进**

* 修复了Microsoft Edge和Internet Explorer的跟踪编码问题。 (NEO-11257)
* 修复了LINE投放中图像链接个性化的问题。 (NEO-11077)
* 修复了ID序列生成机制无法正常工作的问题。 (NEO-11115)
* 修复了在使用具有整数类型协调键值的自定义命名空间时隐私(GDPR)请求无法工作的问题。 (NEO-11123)
* 修复了在&#x200B;**[!UICONTROL Query]**&#x200B;工作流活动中使用&#x200B;**[!UICONTROL Distribution of values]**&#x200B;选项时可能发生的错误。 (NEO-10958)
* 修复了将选件空间从营销实例同步到交互实例时的问题。 (NEO-11162)
* 改进了升级后期间长名称索引的管理

## 18.4.2 版 - 内部版本 8932{#release-18-4-2-build-8932}

2018年5月22日

**改进**

* 修复了Windows Server更新无法正常工作的问题。
* 修复了使用XML中存储的数据时&#x200B;**[!UICONTROL Survey Result]**&#x200B;活动中的问题。 报表显示不正确。 (NEO-10816)
* 修复了使用退回邮件服务器时inMail进程可能发生的性能问题。 (NEO-10641)
* 修复了在升级1000个以上架构时可能发生的数据库升级问题。

## 18.4 版 - 内部版本 8931{#release-18-4-build-8931}

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
   <td> 欧盟《通用数据保护条例》(GDPR)<br /> </td> 
   <td> <p>GDPR是欧盟(EU)的新隐私法，旨在协调数据保护要求并使之现代化，于2018年5月25日正式生效。 GDPR 适用于所持有数据的数据主体位于欧盟的 Adobe Campaign 客户。</p> <p>除了Adobe Campaign中已有的可用隐私功能（包括同意管理、数据保留设置和用户角色）之外，我们还将利用我们作为数据处理者的角色提供的这一机会，加入其他功能，以帮助您作为数据控制者为某些GDPR请求做好准备：</p> 
    <ul> 
     <li> <p>访问权：允许数据主体接收由数据控制者捕获的其个人数据的副本，可能包括存储在Adobe Campaign中的数据。</p> </li> 
     <li> <p>删除权：数据主体有权擦除“数据控制者”捕获的个人数据，这可能包括存储在Adobe Campaign中的数据。</p> </li> 
    </ul> 有关详细信息，请参阅<a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html">有详细说明的文档</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用中的用户档案<br /> </td> 
   <td> <p>Adobe Campaign现在提供活动用户档案的列表，通过专用工作流每月更新。</p> <p>有关详细信息，请参阅<a href="../../platform/using/about-profiles.md#active-profiles">有详细说明的文档</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> Android推送连接器增强<br /> </td> 
   <td> <p>Android连接器已得到增强，可支持更高的吞吐量。 </p> <p>有关详细信息，请参阅<a href="../../delivery/using/configuring-the-mobile-application.md">有详细说明的文档</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 现在禁用了外部实体的扩展，以防止未经身份验证的用户发生潜在攻击。 (NEO-10173)
* 强化了权限，以防止标准用户更改实例配置参数，如应用程序访问URL、LDAP设置等。 (NEO-10171)
* 修复了可能通过堆栈跟踪显示敏感信息的问题。 错误详细信息现在记录在后端到外部网络无法访问的位置。 (NEO-10176)
* 强化了权限，以防止标准用户查看管理员上传的文档和/或导出的包。 (NEO-10170)

**改进**

* **LINE渠道 — 架构增强**:与Adobe Campaign中的所有其他渠道一样，现在所有部署类型都支持LINE渠道：托管、混合和内部部署。
* **序列自动生成**:ID生成机制已得到增强，可增加具有大量对象的Campaign实例的有效期。有关更多信息，请参阅此[技术说明](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html)。

**其他变更**

* 新模式可用于使用命令行导入包，允许循环依赖项（对于大型包，不建议使用）。 有关更多信息，请参阅“技术演变”部分。 (NEO-8979)
* 改进了Teradata中大量数据加载的性能，并修复了阻止显示日志中处理数据的正确值的问题。 (NEO-10429)
* 现在，从Audience Manager导入受众可以处理拆分文件。 以前，只有区段的最后一个文件是由importSharedAudience技术工作流导入的。 (NEO-10156)
* 在Windows上，Campaign服务器默认安装路径已更改。 启动64位版本设置时，默认安装路径现在为：**C:\Program Files\Adobe\Adobe Campaign Classic v7**，而不是&#x200B;**C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* 默认MX规则已得到增强，可包含更多域并优化吞吐量。
* 对部署向导SOAP调用(xtk:serverOptions#SaveOptions)强制实施访问限制。
* 已删除weka.jar过时库，并更新OpenSSL库以进行安全优化。
* 改进了计费技术工作流以保护实例性能。
* 恢复了管理员设置或重置任何操作员密码的功能。 要执行此操作，请右键单击某个运算符，选择&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Reset password]**&#x200B;并设置该运算符的新密码。 我们建议操作员在首次重新连接时更改其密码。 有关详细信息，请参阅[有详细说明的文档](../../production/using/lost-password.md)。
* 为了支持Adobe Target中新增的多租户功能，现在在配置与Target集成的选项和外部帐户时，可以向URL中添加新的“at_property”参数。 可在Adobe Target中找到用于此参数的值，该值将在调用Target时由Campaign使用。 有关详细信息，请参阅[有详细说明的文档](../../integrations/using/inserting-a-dynamic-image.md)。
* 现在，您可以指定在单击Adobe Target提供的图像时要打开的默认登录页面。 以前，单击该图像会导致在创建电子邮件时设置默认图像。 有关详细信息，请参阅[有详细说明的文档](../../integrations/using/inserting-a-dynamic-image.md)。
* 在外部帐户中添加了&#x200B;**启用SMPP跟踪**&#x200B;复选框以强制执行跟踪输出。 有关详细信息，请参阅[有详细说明的文档](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)。

**技术演进**

queryDef

已针对“orderBy”子句修改queryDef。 在更改之前，查询表的主键将隐式添加到“orderBy”子句中。 在某些数据库引擎（至少是postgresql）上，它会阻止使用索引（orderBy子句的所有字段都必须由同一索引覆盖）。 如果您依赖于此行为，则必须在“orderBy”子句中显式添加主键。

例如，如果您具有以下查询：

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

在18.4号变更之前，它将被隐式地递交为：

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

对于非ASCII字符，“urlEncode” JavaScript函数无法正常工作。 已更正该字符，现在应该可以处理所有Unicode字符（包括日语字符）。 如果您依赖非ASCII字符的“urlEncode”行为，则必须调整您的代码。

包导入新模式

新模式可用于使用命令行导入包，允许循环依赖项（对于大型包，不建议使用）。 现有功能会保留。 对于具有循环依赖关系的此类包，已在命令行包导入中添加了新标记&#x200B;**-usejs**。 执行时，将像从界面执行包导入时一样使用JSEngine。

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**修补程序**

* 修复了从Adobe Campaign Standard复制投放和跟踪日志到Adobe Campaign Classic时的同步问题。 (NEO-10023)
* 修复了在快速加载操作失败后恢复ETL工作流时，处理Teradata中的错误和日志表时出现的问题。 现在，每次工作流继续时，错误和日志表都会被正确删除。 (NEO-10672)
* 修复了在安装FDA包时自动安装Hive包(Hadoop需要)的升级后问题。 (NEO-10592)
* 修复了将无效域视为&#x200B;**未定义**&#x200B;错误的错误。 (NEO-10248)
* 修复了发送Android推送投放时，deliveryLogStats表中的日志重复的问题。 (NEO-10234)
* 修复了可能导致条形码扫描仪无法读取某些条形码格式的问题。 (NEO-10125)
* 修复了使用非ASCII字符时“urlEncode” JavaScript函数的问题。 有关更多信息，请参阅“技术演变”部分。 (NEO-10123)
* 修复了在Teradata库上执行包含sha256函数的查询时的问题。 (NEO-10119)
* 修复了在使用非常大的SalesForce表时，SalesForce活动中可能发生的工作流内存错误。 (NEO-9900)
* 修复了使用FDA定位工作流活动时&#x200B;**生成补码**&#x200B;选项的问题。 (NEO-9878)
* 修复了在使用中间源时可能导致营销实例上未更新&#x200B;**已处理**&#x200B;和&#x200B;**成功**&#x200B;量度的问题。 (NEO-9454)
* 修复了在平台中总选件超过10k时的交互非重命题规则(NEO-9352)
* 修复了在使用XML外部文件时可能无法指定投放目标的问题。 (NEO-9312)
* 修复了在选件上运行假设并更新建议状态时可能导致工作流错误的问题。 (NEO-9304)
* 修复了基于Android投放映射的属性使用压力规则时在投放分析期间出现的错误。 (NEO-9202)
* 修复了对收件人列表中的列进行排序时可能导致性能问题的问题。 有关queryDef修改的更多信息，请参阅下面的“技术演变”部分。 (NEO-9042)
* 修复了批准电子邮件中的链接可能指向错误的登录URL的问题，尤其是在使用Federated ID登录类型时。 (NEO-9011)
* 修复了可能导致某些时区的报表日期选取器中显示错误日期的问题。 (NEO-9007)
* 修复了使用FDA SQL数据库时无法查看出站目标的问题。 (NEO-8924)
* 修复了导致MS Dynamics CRM连接器无法提取每月前7天数据的问题。 (NEO-8803)
* 修复了Analytics集成中阻止用户包含国际字符的错误。 (NEO-8719)
* 修复了在没有适当权限的情况下可以启用工作流编辑的问题。 (NEO-8708)
* 修复了在混合架构中使用消息中心时，通过HTTP进行联合数据访问导致连接丢失或连接丢失（超时）的问题。 (NEO-8438)
* 修复了负ID的增量查询活动中发生的工作流错误。 (NEO-8229)
* 修复了可能导致在某些屏幕中显示双滚动条的问题。 (NEO-8208)
* 修复了在运行更新数据库结构向导时导致显示错误消息的问题。 PostUpgrade将执行名称超过30的索引的重命名。 请注意，对于大型表，替换索引将需要时间。 (NEO-7983)
* 修复了跟踪日志无法从消息中心执行实例正确同步以控制实例的问题。 (NEO-7286)
* 修复了选件扩充活动的性能问题。 (NEO-7263)
* 修复了在通过FDA查询Redshift数据库时无法使用DaysAgo函数的问题。 (NEO-7099)
* 修复了数据管理中阻止在扩充类工作流活动上创建索引的回归。
* 修复了在使用标题创建外部资源时可能发生的@id问题
* 修复了在通过FTP服务器上传压缩文件或在文件名中上传带通配符的文件时可能发生的问题。
* 修复了在创建到Campaign Standard的外部自定义资源中较长的基类型枚举的问题。
* 修复了即使与提供商的连接失败也可能导致短信丢失的问题。
* 修复了导致SMTP连接无限期卡住的错误。
* 修复了在使用LINE映射或筛选和定位架构不同时在消息准备期间压力分类规则存在的问题。
