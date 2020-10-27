---
title: 常规配置
seo-title: 常规配置
description: 常规配置
seo-description: null
page-status-flag: never-activated
uuid: 317a145d-36b0-40fe-a272-ad5e35b0b190
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: f4b1c108-7f71-4aa1-8394-a7f660834c9c
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '2822'
ht-degree: 0%

---


# 常规配置{#general-configurations}

如果您是从v5.11或v6.02迁移，则本节将详细介绍要在Adobe Campaignv7中执行的配置。

此外：

* 如果从v5.11迁移，则还必须完成v5.11中“特 [定配置”部分中详细的配置](../../migration/using/specific-configurations-in-v5-11.md) 。
* 如果从v6.02迁移，则还必须完成v6.02中“特 [定配置”部分中详细的配置](../../migration/using/specific-configurations-in-v6-02.md) 。

## 时区 {#time-zones}

### 多时区模式 {#multi-time-zone-mode}

在v6.02中，“多时区”模式仅对PostgreSQL数据库引擎可用。 现在，无论使用哪种类型的数据库引擎，都可提供该引擎。 我们强烈建议您将您的基础转换为“多时区”基础。

要使用TIMESTAMP WITH TIMEZONE模式，您还需要将-userTimestamptz: **1选项添加到** postupgrade命令行中。

>[!IMPORTANT]
>
>如果 **-usetimestamptz:1** 参数与不兼容的数据库引擎一起使用，您的数据库将已损坏，您必须恢复数据库的备份并重新执行上述命令。

>[!NOTE]
>
>迁移后，可以通过控制台（节点）更改&#x200B;**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** 时区。
>
>有关时区管理的详细信息，请参 [阅本节](../../installation/using/time-zone-management.md)。

### Oracle {#oracle}

如果在播放过 **程中出现** ORA 01805错误，这意味着应用程序服务器和数据库服务器之间的Oracle时区文件不同步。 要重新同步它们，请应用以下步骤：

1. 要标识所使用的时区文件，请运行以下命令：

   ```
   select * from v$timezone_file
   ```

   时区文件通常位于 **ORACLE_HOME/oracore/zoneinfo/文件夹** 中。

1. 确保两台服务器上的时区文件相同。

有关详细信息，请访问： [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004)。

客户端和服务器之间的时区未对准也会导致一些滞后。 因此，我们建议在客户端和服务器端使用相同版本的Oracle库，这两个时区必须相同。

要检查两侧是否位于同一时区：

1. 运行以下命令检查客户端上时区文件的版本：

   ```
   genezi -v
   ```

   genezi是$ORACLE_HOME/ **bin存储库中的二进制文件** 。

1. 运行以下命令检查服务器端时区文件的版本：

   ```
   select * from v$timezone_file
   ```

1. 要更改客户端上的时区文件，请使用 **ORA_TZFILE** 环境变量。

## 安全性 {#security}

### 安全区 {#security-zones}

>[!IMPORTANT]
>
>出于安全原因，Adobe Campaign平台在默认情况下不再可访问：您必须配置安全区域，并因此收集运营商IP地址。

Adobe Campaignv7涉及安全 **区的概念**。 每个用户必须与某个区域关联才能登录实例，并且用户的IP地址必须包含在安全区域中定义的地址或地址范围中。 配置安全区可在Adobe Campaign服务器配置文件中完成。 必须在控制台()中定义用户与之关联的安全&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;区。

**迁移前**，请要求网络管理员帮助您定义迁移后要激活的安全区域。

**配置升级后** （服务器重新启动之前），必须配置安全区域。

安全区配置位于此 [部分中](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

### 用户密码 {#user-passwords}

在v7中，内 **部** 和管 **理员** 连接必须由密码保护。 我们强烈建议在迁移之前为这些帐户和所有操作员帐户 **分配口令**。 如果您没有为内部指定 **口令**，您将无法连接。 要将密码指定给 **内部**，请输入以下命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>内 **部密码** （对于所有跟踪服务器）必须相同。 有关详细信息，请参 [阅本节](../../installation/using/campaign-server-configuration.md#internal-identifier)[和本节](../../platform/using/access-management.md#about-permissions)。

### v7的新增功能 {#new-features-in-v7}

* 没有权限的用户无法再连接到Adobe Campaign。 必须手动添加其权限，例如，通过创建名为connect的 **权限**。

   在播放过程中，将识别并列出受此修改影响的用户。

* 如果密码为空，跟踪将不再有效。 如果出现这种情况，将显示一条错误消息，通知您并要求您重新配置它。
* 用户口令不再存储在xtk: **sessionInfo模式** 。
* 现在，使用xtk:builder:EvaluateJavaScript **和xtk** : **builder:EvaluateJavaScriptTemplate函数需要管理权限** 。

某些现成模式已修改，默认情况下，现在只能通过具有管理员权限的操作员的写入访问 **权限** :

* ncm：发布
* nl：监视
* nms：日历
* xtk:builder
* xtk：连接
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk：表单
* xtk:funcList
* xtk:fusion
* xtk：图像
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk：包
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:模式
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk：字符串
* xtk:xslt

### 会话令牌参数 {#sessiontoken-parameter}

在v5中，会 **话令牌** 参数在客户端都有效(概述类型屏幕、链接编辑器等的列表) 服务器端（web应用程序、报表、jsp、jssp等）。 在v7中，它仅在服务器端工作。 如果要恢复v5上的完整功能，则必须使用此参数修改链接并通过连接页传递：

链接示例：

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

使用连接页面新建链接：

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!IMPORTANT]
>
>如果您使用与信任的IP掩码链接的运算符，请检查它是否具有最低权限，以及它是否处于sessionTokenOnly模式 **下的安全** 区。

### SQL函数 {#sql-functions}

未知的SQL函数调用不再自然地发送到服务器。 当前，必须将所有SQL函数添加 **到xtk:funcList** 模式(有关详细信息，请参 [阅本节](../../configuration/using/adding-additional-sql-functions.md))。 迁移时，在postupgrade中会添加一个选项，它允许您与旧的未声明的SQL函数保持兼容性。 如果要继续使用这些函数，请检查XtkPassUnknownSQLFunctionsToRDBMS **选项是否确实在节点级别** 定 **[!UICONTROL Administration > Platform > Options]** 义了。

>[!IMPORTANT]
>
>我们强烈建议不要使用此选项，因为它会带来安全风险。

### JSSP {#jssp}

例如，如果要授权通过HTTP协议（而非HTTPS）访问某些页面，则无论在安全区域中执行何种配置，都必须在相应的中继规则中指定 **httpAllowed=** &quot;true&quot;参数。

如果使用匿名JSSP，则必须在JSSP( **文件)的中继规则中添** 加httpAllowed=&quot;true **[!UICONTROL serverConf.xml]** &quot;参数：

例如：

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## 语法 {#syntax}

### JavaScript {#javascript}

Adobe Campaignv7集成了更新的JavaScript解释器。 但是，此更新可能导致某些脚本发生故障。 由于以前的引擎权限更大，因此某些语法会起作用，而新版本的引擎不再适用。

语 **[!UICONTROL myObject.@attribute]** 法现在仅对XML对象有效。 此语法可用于个性化投放和内容管理。 如果在非XML对象上使用此类语法，个性化功能将不再有效。

对于所有其他对象类型，语法现 **[!UICONTROL myObject`[`在为“attribute”`]`]**。 例如，使用以下语法的非XML对象： **[!UICONTROL employee.@sn]**，现在必须使用以下语法： **[!UICONTROL employee`[`“sn”`]`]**。

* 以前的语法：

   ```
   employee.@sn
   ```

* 新语法：

   ```
   employee["sn"]
   ```

要更改XML对象中的值，您现在需要先更新该值，然后再添加XML节点：

* 旧JavaScript代码：

   ```
   var cellStyle = node.style.copy();
   this.styles.appendChild(cellStyle);
   cellStyle.@width = column.@width;
   ```

* 新的JavaScript代码：

   ```
   var cellStyle = node.style.copy();
   cellStyle.@width = column.@width;
   this.styles.appendChild(cellStyle);
   ```

不再能将XML属性用作表键。

* 以前的语法：

   ```
   if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
   ```

* 新语法：

   ```
   if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
   ```

### SQLData {#sqldata}

为了增强实例安全性，在v7Adobe Campaign中引入了新的语法来取代基于SQLData的语法。 如果将这些代码元素与此语法一起使用，则必须修改它们。 主要内容有：

* 按子查询筛选：新的语法基于元 `<subQuery>` 素来定义子查询
* 聚合:新语法为“聚合函数（集合）”
* 按连接过滤：新语法为 `[schemaName:alias:xPath]`

已修改queryDef(xtk:queryDef)模式:

* 新元 `<subQuery>` 素可用于替换SQLData中包含的SELECT
* 为@setOperator属性引入了两个新值“IN”和“NOT IN”
* 新元 `<where>` 素，它是元素的子 `<node>` 元素：这使您能够在SELECT中进行“子选择”

当使用“@expr”属性时，可能存在SQLData。 可以搜索以下术语：&quot;SQLData&quot;、&quot;aliasSqlTable&quot;、&quot;sql&quot;。

Adobe Campaignv7实例默认为安全。 安全性是指文件中安全区域的定 **[!UICONTROL serverConf.xml]** 义：allowSQLI **njoffent** 属性管理SQL语法安全。

如果在配置级执行期间发生SQLData错误，则必须修改此属性以暂时允许使用基于SQLData的语法，从而允许您重写代码。 为此，必须在serverConf.xml文件中更改以 **下选项** :

```
allowSQLInjection="true"
```

因此，请使用以下命令重新启动应用程序：

```
nlserver config -postupgrade -instance:<instance_name> -force
```

您必须配置安全区域(请参 [阅安](#security)全)，然后通过更改选项重新激活安全性：

```
allowSQLInjection="false"
```

在下面，您将找到新旧语法之间的比较示例。

**按子查询筛选**

* 以前的语法：

   ```
   <condition expr="@id NOT IN ([SQLDATA[SELECT iOperatorId FROM XtkOperatorGroup WHERE iGroupId = $(../@owner-id)]])" enabledIf="$(/ignored/@ownerType)=1"/>
   ```

* 新语法：

   ```
   <condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
     <subQuery schema="xtk:operatorGroup">
        <select>
          <node expr="[@operator-id]" />
        </select>
        <where>
          <condition expr="[@group-id]=$long(../@owner-id)"/>
        </where>
      </subQuery>
   </condition>
   ```

* 以前的语法：

   ```
   <queryFilter name="dupEmail" label="Emails duplicated in the folder" schema="nms:recipient">
       <where>
         <condition sql="sEmail in (select sEmail from nmsRecipient where iFolderId=$(folderId) group by sEmail having count(sEmail)>1)" internalId="1"/>
       </where>
       <folder _operation="none" name="nmsSegment"/>
     </queryFilter>
   ```

* 新语法：

   ```
   <queryFilter name="dupEmail" label=" Emails duplicated in the folder " schema="nms:recipient">
       <where>
         <condition expr="@email" setOperator="IN" internalId="1">
           <subQuery schema="nms:recipient">
             <select><node expr="@email"/></select>
             <where><condition expr="[@folder-id]=$(folderId)"/></where>
             <groupBy><node expr="@email"/></groupBy>
             <having><condition expr="count(@email)>1"/></having>
           </subQuery>
         </condition>
       </where>
       <folder _operation="none" name="nmsSegment"/>
     </queryFilter>
   ```

**聚合**

聚合函数（集合）

* 以前的语法：

   ```
   <node sql="(select count(*) from NmsNewsgroup WHERE O0.iOperationId=iOperationId)" alias="@nbMessages"/>
   ```

* 新语法：

   ```
   <node expr="count([newsgroup/@id])" alias="../@nbMessages"/>
   ```

   >[!NOTE]
   >
   >关节自动执行聚合功能。 不再需要指定条件WHERE O0.iOperationId=iOperationId。
   >
   >不再能使用“count(*)”函数。 必须使用“countall()”。

* 以前的语法：

   ```
   <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
   ```

* 新语法：

   ```
   <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                     <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
   ```

**过滤器（按连接）**

`[schemaName:alias:xPath]`

别名是可选的

* 以前的语法：

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [SQLDATA[W." + joinPart.source.SQLName + "]]"}
                                            aliasSqlTable={nodeSchemaRoot.SQLTable + " W"}/>
   ```

* 新语法：

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [" + nodeSchema.id + ":" + joinPart.source.nodePath + "]]"}/>
   ```

**提示与技巧**

在元 `<subQuery>` 素中，要引用主元素的“字段”字 `<queryDef>` 段，请使用以下语法： `[../@field]`

示例:

```
<queryDef operation="select" schema="xtk:jobLog" startPath="/" xtkschema="xtk:queryDef">
  <select>
    <node expr="[job/@pid]" alias="@pid"/>
    <node expr="@id" ordered="true"/>
    <node expr="@logType"/>
  </select>
  <where>
    <condition expr="[@job-id]=99"/>
    <condition expr="@logType" setOperator="IN">
      <subQuery schema="xtk:jobLog">
        <select><node expr="@logType"/></select>
        <where><condition expr="[@job-id]=[../job/@id]"/></where>
        <groupBy><node expr="@logType"/></groupBy>
        <having><condition expr="count(@logType)>1"/></having>
      </subQuery>
    </condition>
  </where>
</queryDef>
```

## 冲突 {#conflicts}

迁移是通过程序升级执行的，冲突可能会在报表、表单或Web应用程序中出现。 这些冲突可以通过控制台解决。

资源同步后，postupgrade命 **令允许您** 检测同步是否生成错误或警告。

### 视图同步结果 {#view-the-synchronization-result}

同步结果可通过两种方式查看：

* 在命令行接口中，错误由三个V形标记>> **实现** ，同步将自动停止。 警告由多次V形标记 **>>实** 现，并且必须在同步完成后解决。 在播放结束时，命令提示符下会显示一个摘要。 例如：

   ```
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   如果警告涉及资源冲突，则需要操作员注意才能解决该问题。

* postupgrade **.log文`<server version number>`件的postupgrade_time`>`包含同步结果** 。 默认情况下，它位于以下目录中： **安装目录/var/`<instance>`postupgrade**。 错误和警告由错误和 **警告****属性指** 示。

### 解决冲突 {#resolve-a-conflict}

解决冲突必须仅由高级运算符和那些已被授予“管理员”权限的运算符来执行。

要解决冲突，请应用以下流程：

1. 在Adobe Campaign树结构中，将光标放在上 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**&#x200B;方。
1. 在列表中选择要解决的冲突。

解决冲突有三种可能的方法：

* **[!UICONTROL Declared as resolved]**:需要事先操作员干预。
* **[!UICONTROL Accept the new version]**:如果用户未更改随Adobe Campaign提供的资源，则建议使用此选项。
* **[!UICONTROL Keep the current version]**:表示更新被拒绝。

   >[!IMPORTANT]
   如果选择此解决模式，则可能丢失新版本中的修补程序。 因此，强烈建议不要仅为专家操作员使用或保留此选项。

如果选择手动解决冲突，请按如下步骤继续：

1. 在窗口的下半部分，搜索以 **`_conflict_ string`** 查找存在冲突的实体。 随新版本一起安装的实体包 **含** new参数，与先前版本匹配的实体包含 **cus** 参数。

   ![](assets/s_ncs_production_conflict002.png)

1. 删除您不想保留的版本。 删除 **`_conflict_argument_ string`** 要保留的实体。

   ![](assets/s_ncs_production_conflict003.png)

1. 转到您应已解决的冲突。 单击图 **[!UICONTROL Actions]** 标并选择 **[!UICONTROL Declare as resolved]**。
1. 保存更改：冲突现已解决。

## Tomcat {#tomcat}

Adobe Campaignv7中集成的Tomcat服务器已更改版本(Tomcat 7)。 因此，其安装文件夹(tomcat-6)也已更改(tomcat 7)。 配置升级后，确保检查路径是否链接到更新的文件夹(在文件 **[!UICONTROL serverConf.xml]** 中):

```
$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
```

## 互动 {#interaction}

### 先决条件{#prerequisites}

**在配置升级**&#x200B;之前，必须从6.02中删除v7中将不再存在的所有模式引用。

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### 优惠内容 {#offer-content}

在v7中，已移动优惠内容。 在v6.02中，内容位于每个表示模式(**nms:emailOfferView**)中。 在v7中，内容现在处于优惠模式。 配置升级后，内容将不会显示在界面中。 在播放后，您必须重新创建优惠内容，或开发一个脚本，该脚本将内容从表示模式自动移动到优惠模式。

>[!IMPORTANT]
如果迁移后要发送使用已配置优惠的某些投放，则必须删除这些投放并在v7中重新创建这些。 如果您无法这样做，则提供“兼容性模式”。 不建议使用此模式，因为您不会从Interaction v7中的所有新增功能中受益。 这是一种过渡模式，允许您在实际6.1迁移之前完成正在进行的活动。 有关此模式的详细信息，请联系我们。

移动脚本(interactionTo610_**full_XX.js**)的示例位于Adobe Campaignv7文件夹 **的Migration** 文件夹中。 此文件显示了一个客户端脚本示例，该脚本使用每个优惠（和字段）使用单 **[!UICONTROL htmlSource]** 一电 **[!UICONTROL textSource]** 子邮件表示。 NmsEmailOfferView表中 **的内容** 已移到优惠表。

>[!NOTE]
使用此脚本不允许您从“内容管理”和“渲染函数”选项中受益。 要从这些功能中受益，您必须重新思考目录优惠，特别是优惠内容和配置空间。

```
loadLibrary("/nl/core/shared/nl.js");

NL.require("/nl/core/shared/xtk.js");

// 1. Restore old emailOfferView schema
logInfo("Restoring old emailOfferView schema");
var oldOfferViewSchemas = <entities schema="xtk:srcSchema"/>;

oldOfferViewSchemas.appendChild(
  <srcSchema img="nms:offerView.png"
             label="Email offer representations"
             labelSingular="Email offer representation"
             name="emailOfferView" namespace="nlmig"
             genAccessors="false" implements="xtk:persist">
    <element name="emailOfferView" template="nms:offerView" sqltable="NmsEmailOfferView">
      <element name="offer" revLabel="Email representation" revIntegrity="owncopy"/>
      <element   name="htmlSource"      type="html" label="HTML content"  xml="true"/>
      <element   name="textSource"      type="CDATA" label="Text content" xml="true"/>
      <element   name="htmlSource_jst"  type="CDATA" label="HTML script"  desc="HTML content calculation script."  xml="true" advanced="true"/>
      <element   name="textSource_jst"  type="CDATA" label="Text script" desc="Text content calculation script." xml="true" advanced="true"/>
    </element>
  </srcSchema>);

var oldOfferViewsPkg = <builder><package buildNumber="*">{oldOfferViewSchemas}</package></builder>;
xtk.builder.InstallPackage(oldOfferViewsPkg);

// 2. Migrate data from old emailOfferView table to nms:offer
logInfo("Moving data from old EmailOfferView table to NmsOffer");
var OFFER_STATUS_VALIDATED = 3;

var queryDef = xtk.queryDef.create(
  <queryDef operation="select" schema="nlmig:emailOfferView">
    <select>
      <node expr="[@offer-id]"/>
      <node expr="[@space-id]"/>
      <node expr="htmlSource_jst"/>
      <node expr="textSource_jst"/>
    </select>
  </queryDef>);
var res = queryDef.ExecuteQuery();

var processedOffers = {};
for each( var emailOfferView in res.emailOfferView )
{
  if( processedOffers[String(emailOfferView.@["offer-id"])] != undefined )
  {
    logWarning("Found 2 or more eff fffffmail representations for offer " + String(emailOfferView.@["offer-id"]) + ". Only keep the first one here.");
    continue;
  }
  xtk.session.Write(
    <offer id={emailOfferView.@["offer-id"]} status={OFFER_STATUS_VALIDATED} xtkschema="nms:offer">
      <view>
        {emailOfferView.mdSource_jst}
        {emailOfferView.textSource_jst}
      </view>
    </offer>
  );
  processedOffers[String(emailOfferView.@["offer-id"])] = 1;
}

// 3. Get rid of emailOfferView schema now that data has been moved.
logInfo("Deleting EmailOfferView schema");
xtk.session.Write(<srcSchema xtkschema="xtk:srcSchema" name="emailOfferView" namespace="nlmig" _operation="delete"/>);

logInfo("Done");
```

### 测试和配置 {#tests-and-configuration}

如果您只有一个优惠，则在移动了环境内容后，将遵循以下过程。 在此例中，我们以“ENV”为例。

1. 在所有“ENV”环境优惠空间中，更新所用字段的列表。 例如，对于仅使用的优惠空间, **[!UICONTROL htmlSource]**&#x200B;必须添加 **[!UICONTROL view/htmlSource]**。

   ![](assets/migration_interaction_2.png)

1. 在选项 **[!UICONTROL Type of Environment]** 卡中的字 **[!UICONTROL General]** 段中，选择 **[!UICONTROL Live]**。

   ![](assets/migration_interaction_3.png)

1. 创建一个设计环境（例如“ENV_DESIGN”）并将其连接到ENV联机环境。

   ![](assets/migration_interaction_4.png)

1. 部署所有“ENV”环境优惠空间(右键单 **[!UICONTROL Actions > Deploy]**&#x200B;击>)并选择“ENV_DESIGN”环境。

   ![](assets/migration_interaction_5.png)

1. 对所有“ENV”环境优惠执行相同操作。
1. 激活相关环境上的所有优惠“ENV_DESIGN”。
1. 试制优惠上线。 如果您没有遇到任何问题，请在最新的工作流任务(offerMgt)上执 **[!UICONTROL Offer notification]** 行挂起的任务，以使所有优惠都生效。

   ![](assets/migration_interaction_6.png)

1. 执行全面的测试。

   >[!NOTE]
   在线类别和优惠的名称在上线后进行修改。 在传入渠道上，更新对优惠和类别的所有引用。

## 报告 {#reports}

### 标准报表 {#standard-reports}

所有标准报告当前都使用渲染引擎v6.x。如果已将JavaScript添加到这些报表中，某些元素可能不再有效。 事实上，旧版JavaScript与v6.x渲染引擎不兼容。 因此，您必须检查JavaScript代码，然后重新调整它。 应测试每个报告，特别是导出功能。

### 个性化报告 {#personalized-reports}

如果要使用v7中的蓝色横幅（允许您访问宇宙），则必须重新发布报告。 如果遇到问题，可以强制使用v6.0渲染引擎。 为此，请转到报 **[!UICONTROL Properties]** 表中，单击并 **[!UICONTROL Rendering]** 选择渲 **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** 染引擎。

![](assets/migration_reports_1.png)

如果您希望从新报告功能中受益，则必须选择v.6.x渲染引擎。 在这种情况下，请检查所有脚本并在必要时更改它们。 在PDF导出方面，如果您为OpenOffice添加了特定脚本，则新的PDF导出引擎(PhantomJS)将不再支持该脚本。

## Web 应用程序 {#web-applications}

有两个Web应用程序系列：

* 确定的Web应用程序（综合查看，批准表单，外部网内部开发）,
* 匿名Web应用程序（Web或调查表表单）。

### 已识别的Web应用程序 {#identified-web-applications}

与报表(请参阅 [报表](#reports))一样，如果您添加了JavaScript，则必须检查并调整。 如果您希望从v7蓝色横幅（包含宇宙）受益，则必须重新发布Web应用程序。 如果您的JavaScript代码正在工作，则可以选择v6.x渲染引擎。 如果不是这样，您可以在调整代码时使用v6.0渲染引擎，然后使用v6.x渲染引擎。

>[!NOTE]
选择渲染引擎的步骤与选择报告的步骤相同。 请参阅 [个性化报告](#personalized-reports)。

Web 应用程序连接方法在v7中已更改。 如果在已识别的Web应用程序中遇到任何连接问题，则必须临 **时激活serverConf.xml** 文件中的 **allowUserPassword** 和 **** sessionTokenOnly选项。 在配置升级后，修改以下选项值：

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

因此，请使用以下命令重新启动应用程序：

```
nlserver config -postupgrade -instance:<instance_name> -force
```

在发布之前，在v6.x渲染引擎中测试Web应用程序。 然后取消激活这两个选项。

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### 匿名Web应用程序 {#anonymous-web-applications}

如果遇到任何问题，请重新发布Web应用程序。 如果问题仍然存在，您可以选择v6.0渲染引擎。 如果您尚未添加JavaScript，则可以选择v6.x渲染引擎并从其新增功能中受益。

>[!NOTE]
选择渲染引擎的步骤与选择报告的步骤相同。 请参阅 [个性化报告](#personalized-reports)。

## 红帽 {#red-hat}

如果在v6.02或v5.11中删除了现成模式，则在播放后您可能无法再编辑模式。 如果发生这种情况，请执行以下命令：

```
su - neolane
nlserver config -postupgrade -instance:<instance name> -force
```
