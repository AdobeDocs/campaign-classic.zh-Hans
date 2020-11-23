---
solution: Campaign Classic
product: campaign
title: 筛选模式
description: 筛选模式
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# 筛选模式{#filtering-schemas}

## 系统过滤器 {#system-filters}

您可以根据特定用户的权限过滤模式访问权限。 系统过滤器允许您使用readAccess和writeAccess参数管理模式中详细实 **体的读****写权限** 。

>[!NOTE]
>
>此限制仅适用于非技术用户：具有相关权限或使用工作流的技术用户将能够检索和更新数据。

* **readAccess**:提供对模式数据的只读访问。

   **警告** -必须使用相同的限制设置所有链接的表。 此配置可能影响性能。

* **writeAccess**:提供对模式数据的写入访问。

这些过滤器在的 **主要元素** 级别上输入，并且如以下示例所示，可以形成这些模式以限制访问。

* 限制写入权限

   此处，过滤器用于禁止未具有“管理”权限的操作员对模式进行WRITE权限。 这意味着只有管理员才对此模式描述的实体具有写权限。

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 限制读和写权限：

   此处，过滤器用于禁止所有操作符对模式的读取和写入权限。 仅内 **部帐** 户，由表达式“$(loginId)!=0&quot;，具有这些权限。

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   用 **于定** 义条件的可能expr属性值为TRUE或FALSE。

>[!NOTE]
>
>如果未指定过滤器，则所有操作符都对模式具有读写权限。

## 保护内置模式 {#protecting-built-in-schemas}

默认情况下，内置模式只能通过具有“管理”权限的操作员的“写入”权限访问：

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

>[!IMPORTANT]
>
>xtk:sessionInfo模式的 **读取和写入权限** ，只能由Adobe Campaign实例的内部帐户访问。

## 修改内置过滤器的系统模式 {#modifying-system-filters-of-built-in-schemas}

您仍可以修改现成模式的系统过滤器，这些由于与旧版本的兼容性问题而默认受保护。

>[!NOTE]
>
>但是，Adobe建议您不要修改默认参数以确保最佳安全性。

1. 为相关模式创建扩展或打开现有扩展。
1. 在主元素中添 **`<sysfilter name="<filter name>" _operation="delete"/>`** 加子元素，以删除来源模式中相同的筛选器应用程序。
1. 如果您愿意，可以添加新的过滤器，详情请见系 [统过滤器](#system-filters)。

