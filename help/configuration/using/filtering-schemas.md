---
title: 筛选架构
seo-title: 筛选架构
description: 筛选架构
seo-description: null
page-status-flag: never-activated
uuid: 04a90785-3084-42fd-85af-77bc28687579
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 64d4c5b8-db0b-4287-8d30-4bf09878a401
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 筛选架构{#filtering-schemas}

## 系统过滤器 {#system-filters}

您可以根据特定用户的权限过滤对其架构的访问。 系统筛选器允许您使用readAccess和writeAccess参数管理架构中详细实体的读 **写权****限和写权限** 。

>[!NOTE]
>
>此限制仅适用于非技术用户：具有相关权限或使用工作流的技术用户将能够检索和更新数据。

* **readAccess**:提供对架构数据的只读访问。

   **警告** -必须使用相同的限制设置所有链接的表。 此配置可能会影响性能。

* **writeAccess**:提供对架构数据的写入访问。

这些过滤器是在架构的主 **要元素级别** ，并且可以按照以下示例中所示的方式形成以限制访问。

* 限制写入权限

   此处，过滤器用于在未具有“管理”权限的情况下禁止操作员对架构的“写入”权限。 这意味着只有管理员才对此架构描述的实体具有写入权限。

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 限制读取和写入权限：

   此处，过滤器用于禁止所有操作符对架构的“读取”和“写入”权限。 仅内 **部帐户** ，由表达式“$(loginId)!”表示=0&quot;，具有这些权限。

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   用 **于定义条件** 的可能expr属性值为TRUE或FALSE。

>[!NOTE]
>
>如果未指定过滤器，则所有操作符都将对该架构具有读写权限。

## 保护内置架构 {#protecting-built-in-schemas}

默认情况下，内置架构只能通过具有“管理”权限的操作员的“写入”权限访问：

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

>[!IMPORTANT]
>
>Adobe Campaign实例的内 **部帐户只能访问xtk:sessionInfo** 架构的读取和写入权限。

## 修改内置架构的系统过滤器 {#modifying-system-filters-of-built-in-schemas}

您仍然可以修改现成架构的系统过滤器，这些架构由于与旧版本的兼容性问题而默认受到保护。

>[!NOTE]
>
>但是，Adobe建议您不要修改默认参数以确保最佳安全性。

1. 为相关架构创建扩展或打开现有扩展。
1. 在主元素中添 **`<sysfilter name="<filter name>" _operation="delete"/>`** 加子元素，以删除源架构中相同的过滤器应用程序。
1. 如果您愿意，可以添加新的过滤器，如系统过滤器 [中所述](#system-filters)。

