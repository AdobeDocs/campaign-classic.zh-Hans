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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 常规配置{#general-configurations}

如果您是从v5.11或v6.02迁移，则本节将详细介绍在Adobe Campaign v7中执行的配置。

此外：

* 如果从v5.11迁移，则还必须完成v5.11中“特定配置”部 [分中详细介绍的配置](../../migration/using/specific-configurations-in-v5-11.md) 。
* 如果您从v6.02迁移，则还必须完成v6.02中“特定配置” [部分中详细介绍的配置](../../migration/using/specific-configurations-in-v6-02.md) 。

## 时区 {#time-zones}

### 多时区模式 {#multi-time-zone-mode}

在v6.02中，“多时区”模式仅对PostgreSQL数据库引擎可用。 现在，无论使用哪种类型的数据库引擎，都可以提供该功能。 我们强烈建议您将您的基础转换为“多时区”基础。

要使用TIMESTAMP WITH TIMEZONE模式，您还需要将 **-userTimestamptz:1** 选项添加到postupgrade命令行。

>[!CAUTION]
>
>如果 **-usetimestamptz:1** 参数与不兼容的数据库引擎一起使用，则您的数据库将损坏，您必须恢复数据库的备份并重新执行上述命令。

>[!NOTE]
>
>可以通过控制台（节点）在迁移后更改&#x200B;**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** 时区。
>
>有关时区管理的详细信息，请参 [阅本节](../../installation/using/time-zone-management.md)。

### Oracle {#oracle}

如果在升级过程中出现 **ORA 01805** ，这意味着应用程序服务器和数据库服务器之间的Oracle时区文件不同步。 要重新同步它们，请应用以下步骤：

1. 要标识使用的时区文件，请运行以下命令：

   ```
   select * from v$timezone_file
   ```

   时区文件通常位于 **ORACLE_HOME/oracore/zoneinfo/文件夹** 中。

1. 确保两台服务器上的时区文件相同。

有关详细信息，请访问： [https://download.oracle.com/docs/cd/E11882_01/server.112/e10729/ch4datetime.htm](http://download.oracle.com/docs/cd/E11882_01/server.112/e10729/ch4datetime.htm)。

客户端和服务器之间的时区未对准也会导致一些滞后。 因此，我们建议在客户端和服务器端使用相同版本的Oracle库，这两个时区必须相同。

要检查双方是否位于同一时区，请执行以下操作：

1. 运行以下命令检查客户端上时区文件的版本：

   ```
   genezi -v
   ```

   genezi是在 **$ORACLE_HOME/bin存储库中找到的二进制文件** 。

1. 运行以下命令检查服务器端时区文件的版本：

   ```
   select * from v$timezone_file
   ```

1. 要更改客户端的时区文件，请使用 **ORA_TZFILE环境变量** 。

## 安全性 {#security}

### 安全区 {#security-zones}

>[!CAUTION]
>
>出于安全原因，Adobe Campaign平台在默认情况下不再可访问：您必须配置安全区域，因此必须收集运营商IP地址。

Adobe Campaign v7包含安全区 **的概念**。 每个用户都必须与某个区域相关联才能登录到实例，并且用户的IP地址必须包含在安全区域中定义的地址或地址范围中。 配置安全区可在Adobe Campaign服务器配置文件中完成。 必须在控制台()中定义用户关联到的安全区&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;域。

**迁移前**，请要求网络管理员帮助您定义迁移后要激活的安全区。

**配置升级后** （服务器重新启动之前），必须配置安全区。

此部分提供安全区 [配置](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

### 用户密码 {#user-passwords}

在v7中，内部 **和** admin运 **** 营商连接必须由密码保护。 我们强烈建议在迁移之前为这些帐户和所有操作员帐户分 **配密码**。 如果尚未为内部指定密 **码**，则将无法连接。 要为内部分配密 **码**，请输入以下命令：

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>对于 **所有跟踪服务器** ，内部密码必须相同。 有关详细信息，请参 [阅本节](../../installation/using/campaign-server-configuration.md#internal-identifier)[和本节](../../platform/using/access-management.md#about-permissions)。

### v7中的新增功能 {#new-features-in-v7}

* 无权限的用户无法再连接到Adobe Campaign。 必须手动添加其权限，例如，通过创建名为connect的权 **限**。

   受此修改影响的用户在配置过程中进行标识和列出。

* 如果密码为空，则跟踪不再有效。 如果出现这种情况，将显示一条错误消息，通知您并要求您重新配置它。
* 用户口令不再存储在 **xtk:sessionInfo架构中** 。
* 现在，使用 **xtk:builder:EvaluateJavaScript** 和 **xtk:builder:EvaluateJavaScriptTemplate函数需要管理权限** 。

某些现成架构已修改，默认情况下，仅可通过具有管理员权限的操作员的写访问权限访 **问** :

* ncm：发布
* nl：监视
* nms:calendar
* xtk:builder
* xtk：连接
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk：图像
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

### Sessiontoken参数 {#sessiontoken-parameter}

在v5中，会话 **令牌参数在客户端工作** （概述类型屏幕、链接编辑器等的列表）和服务器端（Web应用程序、报告、jsp、jssp等）。 在v7中，它仅在服务器端工作。 如果要像v5一样返回完整功能，则必须使用此参数修改链接并通过连接页面传递：

链接示例：

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

使用连接页面的新链接：

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!CAUTION]
>
>如果您使用与信任的IP掩码链接的运算符，请检查它是否具有最小权限，以及它是否处于 **sessionTokenOnly模式的安全区** 。

### SQL函数 {#sql-functions}

未知的SQL函数调用不再自然地发送到服务器。 当前，所有SQL函数都必须添加到 **xtk:funcList架构中** (有关详细信息，请参 [阅此部分](../../configuration/using/adding-additional-sql-functions.md))。 迁移时，在配置过程中会添加一个选项，该选项允许您保持与旧的未声明的SQL函数的兼容性。 如果要继续使用这些函数，请检查 **XtkPassUnknownSQLFunctionsToRDBMS** 选项是否确实在节点级 **[!UICONTROL Administration > Platform > Options]** 定义。

>[!CAUTION]
>
>由于此选项带来的安全风险，我们强烈建议不要使用此选项。

### JSSP {#jssp}

例如，如果要授权通过HTTP协议（而非HTTPS）访问某些页面，则无论在安全区域中执行何种配置，都必须在相应的中继规则中指定 **httpAllowed=&quot;true&quot;** 。

如果使用匿名JSSP，则必须在JSSP（文件）的中继规则中添加 **httpAllowed=&quot;true&quot;****[!UICONTROL serverConf.xml]** 参数：

例如：

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## 语法 {#syntax}

### JavaScript {#javascript}

Adobe Campaign v7集成了更新的JavaScript解释器。 但是，此更新可能导致某些脚本发生故障。 由于以前的引擎权限更大，某些语法会起作用，而新版本的引擎不再适用。

该 **[!UICONTROL myObject.@attribute]** 语法现在仅对XML对象有效。 此语法可用于个性化分发和内容管理。 如果您在非XML对象上使用了此类语法，个性化功能将不再有效。

对于所有其他对象类型，语法现在 **[!UICONTROL myObject`[`为“attribute”`]`]**。 例如，使用以下语法的非XML对象：现&#x200B;**[!UICONTROL employee.@sn]**在必须使用以下语法：**[!UICONTROL employee`[`“sn”`]`]**。

* 以前的语法：

   ```
   employee.@sn
   ```

* 新语法：

   ```
   employee["sn"]
   ```

要更改XML对象中的值，现在需要先更新该值，然后再添加XML节点：

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

您不能再将XML属性用作表键。

* 以前的语法：

   ```
   if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
   ```

* 新语法：

   ```
   if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
   ```

### SQLData {#sqldata}

为了加强实例安全性，Adobe Campaign v7中引入了新的语法以取代基于SQLData的语法。 如果将这些代码元素与此语法一起使用，则必须修改它们。 主要内容有：

* 按子查询过滤：新语法基于元素来 `<subQuery>` 定义子查询
* 聚合：新语法是“aggregate function(collection)”
* 通过连接过滤：新语法是 `[schemaName:alias:xPath]`

queryDef(xtk:queryDef)架构已修改：

* 有新元 `<subQuery>` 素可用于替换SQLData中包含的SELECT
* 为@setOperator属性引入了两个新值，即“IN”和“NOT IN”
* 新元 `<where>` 素，它是元素的子 `<node>` 元素：这使您能够在SELECT中进行“子选择”

当使用“@expr”属性时，可能存在SQLData。 可以搜索以下术语：“SQLData”、“aliasSqlTable”、“sql”。

默认情况下，Adobe Campaign v7实例是安全的。 安全性体现在文件中安全区域的定 **[!UICONTROL serverConf.xml]** 义上：allowSQLInjopten **属性管理** SQL语法安全性。

如果在配置升级执行期间发生SQLData错误，则必须修改此属性以暂时允许使用基于SQLData的语法，从而允许您重写代码。 为此，必须在serverConf.xml文件中更改以 **下选项** :

```
allowSQLInjection="true"
```

因此，请使用以下命令重新启动配置升级：

```
nlserver config -postupgrade -instance:<instance_name> -force
```

您必须配置安全区域(请参 [阅安全](#security))，然后通过更改以下选项重新激活安全性：

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

**集合**

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
   >为集合函数自动执行连接。 不再需要指定条件WHERE O0.iOperationId=iOperationId。
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

**通过连接过滤器**

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

例如：

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

迁移通过配置程序执行，并且冲突可能会出现在报告、表单或Web应用程序中。 这些冲突可以从控制台中解决。

在资源同步之后，postupgrade命 **** 令允许您检测同步是否生成错误或警告。

### 查看同步结果 {#view-the-synchronization-result}

同步结果可通过两种方式查看：

* 在命令行界面中，错误由三个V形标记 **>>>实现** ，同步会自动停止。 警告由双V形标记 **>>实现** ，并且必须在同步完成后解决。 在配置文件的末尾，命令提示符下会显示一个摘要。 例如：

   ```
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   如果警告涉及资源冲突，则需要操作员注意以解决该问题。

* postupgrade **.log文件的postupgrade_`<server version number>`_time包含同步结果`>`** 。 默认情况下，它位于以下目录中：安 **装目录/var/`<instance>`postupgrade**。 错误和警告由错误和警 **告属** 性 **指示** 。

### 解决冲突 {#resolve-a-conflict}

解决冲突只能由高级操作符和那些被授予“管理员”权限的操作符执行。

要解决冲突，请应用以下进程：

1. 在Adobe Campaign树结构中，将光标放在上方 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**。
1. 在列表中选择要解决的冲突。

解决冲突有三种可能的方法：

* **[!UICONTROL Declared as resolved]**:需要提前操作员干预。
* **[!UICONTROL Accept the new version]**:如果用户未更改随Adobe Campaign提供的资源，则建议使用此选项。
* **[!UICONTROL Keep the current version]**:表示更新被拒绝。

   >[!CAUTION]
   如果选择此解决模式，则可能丢失新版本中的修补程序。 因此，强烈建议不要仅为专家操作员使用或保留此选项。

如果选择手动解决冲突，请按如下步骤继续：

1. 在窗口的下半部分，搜索以查找 **`_conflict_ string`** 存在冲突的实体。 随新版本一起安装的实体包含 **new** 参数，与先前版本匹配的实体包含 **cus** 参数。

   ![](assets/s_ncs_production_conflict002.png)

1. 删除您不想保留的版本。 删除 **`_conflict_argument_ string`** 要保留的实体。

   ![](assets/s_ncs_production_conflict003.png)

1. 转到您应已解决的冲突。 单击图 **[!UICONTROL Actions]** 标并选择 **[!UICONTROL Declare as resolved]**。
1. 保存更改：冲突现已解决。

## Tomcat {#tomcat}

Adobe Campaign v7中集成的Tomcat服务器已更改版本(Tomcat 7)。 因此，其安装文件夹(tomcat-6)也已更改(tomcat 7)。 配置升级后，请确保检查路径是否链接到已更新的文件夹(在文件 **[!UICONTROL serverConf.xml]** 中):

```
$(XTK_INSTALL_DIR)/tomcat-7/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-7/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/el-api.jar
```

## 交互 {#interaction}

### 先决条件 {#prerequisites}

**在配置升级之前**，必须从6.02中删除v7中将不再存在的所有架构引用。

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### 优惠内容 {#offer-content}

在v7中，已移动选件内容。 在v6.02中，内容位于每个表示架构(**nms:emailOfferView**)中。 在v7中，内容现在位于选件架构中。 配置升级后，内容将不会显示在界面中。 配置升级后，您必须重新创建选件内容，或开发一个脚本，该脚本会自动将内容从表示架构移到选件架构。

>[!CAUTION]
如果迁移后要发送使用已配置选件的某些交付，则必须删除这些交付并在v7中重新创建所有这些交付。 如果您无法这样做，则提供“兼容性模式”。 不建议使用此模式，因为您不会从Interaction v7中的所有新增功能中受益。 这是一种过渡模式，允许您在实际6.1迁移之前完成正在进行的营销活动。 有关此模式的详细信息，请联系我们。

Adobe Campaign v7文件夹的“迁移”**文件夹中提供了移动脚本(interactionTo610_full_XX.js****** )的示例。 此文件显示了一个客户端脚本示例，该脚本使用每个选件（和字段）的单一电子 **[!UICONTROL htmlSource]** 邮件 **[!UICONTROL textSource]** 表示形式。 NmsEmailOfferView表中 **的内容已移至** offer表。

>[!NOTE]
使用此脚本不允许您从“内容管理”和“渲染功能”选项中受益。 要从这些功能中受益，您必须重新思考目录选件，特别是选件内容和配置空间。

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

如果您只有一个环境，则在移动了选件内容后要遵循的步骤如下。 在此例中，我们以“ENV”为例。

1. 在所有“ENV”环境中提供空格，请更新所用字段列表。 例如，对于仅使用的选件空间， **[!UICONTROL htmlSource]**&#x200B;必须添加 **[!UICONTROL view/htmlSource]**。

   ![](assets/migration_interaction_2.png)

1. 在选项卡 **[!UICONTROL Type of Environment]** 中的字段 **[!UICONTROL General]** 中，选择 **[!UICONTROL Live]**。

   ![](assets/migration_interaction_3.png)

1. 创建一个设计环境（例如“ENV_DESIGN”）并将其连接到ENV在线环境。

   ![](assets/migration_interaction_4.png)

1. 部署所有“ENV”环境提供空间(右键单击> **[!UICONTROL Actions > Deploy]**)，然后选择“ENV_DESIGN”环境。

   ![](assets/migration_interaction_5.png)

1. 对所有“ENV”环境提供的功能执行相同操作。
1. 激活所有环境，在相关渠道上提供“ENV_DESIGN”。
1. 测试提供的产品是否实时可用。 如果您没有遇到任何问题，请对最新的工作流任务(offerMgt)执 **[!UICONTROL Offer notification]** 行待定任务，以使所有选件变为现用。

   ![](assets/migration_interaction_6.png)

1. 执行全面的测试。

   >[!NOTE]
   在线类别和选件的名称在上线后会被修改。 在传入的渠道中，更新对选件和类别的所有引用。

## 报告 {#reports}

### 标准报告 {#standard-reports}

所有标准报告当前都使用渲染引擎v6.x。如果已将JavaScript添加到这些报告中，某些元素可能不再有效。 事实上，旧版JavaScript与v6.x渲染引擎不兼容。 因此，您必须检查JavaScript代码，然后重新调整它。 应测试每个报告，尤其是导出功能。

### 个性化报告 {#personalized-reports}

如果要使用v7中的蓝色横幅（允许您访问宇宙），则必须重新发布报告。 如果遇到问题，可强制使用v6.0渲染引擎。 为此，请转到报 **[!UICONTROL Properties]** 表中，单击并 **[!UICONTROL Rendering]** 选择渲 **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** 染引擎。

![](assets/migration_reports_1.png)

如果您希望从新的报告功能中受益，则必须选择v.6.x渲染引擎。 在这种情况下，请检查所有脚本并根据需要更改它们。 关于PDF导出，如果您为OpenOffice添加了特定脚本，则新的PDF导出引擎(PhantomJS)将不再适用。

## Web应用程序 {#web-applications}

有两个Web应用程序系列：

* 确定的Web应用程序（一起查看，批准表单，外部网内部开发）,
* 匿名Web应用程序（Web或调查表单）。

### 已识别的Web应用程序 {#identified-web-applications}

与报表一样(请参 [阅报表](#reports))，如果您添加了JavaScript，则必须检查并调整。 如果您希望从v7蓝色横幅（包含宇宙）中获益，则必须重新发布Web应用程序。 如果您的JavaScript代码正在工作，则可以选择v6.x渲染引擎。 如果不是这样，您可以在调整代码时使用v6.0渲染引擎，然后使用v6.x渲染引擎。

>[!NOTE]
选择渲染引擎的步骤与选择报告的步骤相同。 请参阅 [个性化报告](#personalized-reports)。

在v7中，Web应用程序连接方法已更改。 如果您在所标识的Web应用程序中遇到任何连接问题，则必须临时激活 **serverConf.xml文件中的** allowUserPassword **** 和sessionTokenOnly **** 选项。 配置升级后，修改以下选项值：

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

因此，请使用以下命令重新启动配置升级：

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

## Red-Hat {#red-hat}

如果在v6.02或v5.11中删除了现成的架构，则在配置升级后，您可能无法再编辑您的架构。 如果发生这种情况，请执行以下命令：

```
su - neolane
nlserver config -postupgrade -instance:<instance name> -force
```
