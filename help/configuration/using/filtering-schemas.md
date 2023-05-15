---
product: campaign
title: 筛选模式
description: 筛选模式
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 筛选模式{#filtering-schemas}

## 系统过滤器 {#system-filters}

您可以根据特定用户的权限筛选对架构的访问权限。 系统过滤器允许您使用 **readAccess** 和 **writeAccess** 参数。

>[!NOTE]
>
>此限制仅适用于非技术用户：具有相关权限或使用工作流的技术用户将能够检索和更新数据。

* **readAccess**:提供对架构数据的只读访问权限。

   **警告**  — 必须使用相同的限制设置所有链接的表。 此配置可能会影响性能。

* **writeAccess**:提供对架构数据的写入访问权限。

这些过滤器在主 **元素** 架构的级别和（如以下示例所示）可以采用以限制访问的方式来形成。

* 限制写入权限

   在此，过滤器用于禁止在没有ADMINISTRATION权限的情况下对操作员的架构具有WRITE权限。 这意味着只有管理员才具有此架构描述的实体的写入权限。

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 限制读和写权限：

   在此，过滤器用于禁止所有运算符对架构的读取和写入权限。 仅 **内部** 帐户，由表达式“$(loginId)!=0”，具有这些权限。

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   可能 **expr** 用于定义条件的属性值为TRUE或FALSE。

>[!NOTE]
>
>如果未指定过滤器，则所有运算符都将具有架构的读写权限。

## Protect内置模式 {#protecting-built-in-schemas}

默认情况下，内置架构仅可通过具有ADMINISTRATION权限的操作员的WRITE权限访问：

* ncm:publishing
* nl：监控
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
* xtk:image
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
>的读取和写入权限 **xtk:sessionInfo** 架构只能由Adobe Campaign实例的内部帐户访问。

## 修改内置架构的系统筛选器 {#modifying-system-filters-of-built-in-schemas}

您仍然可以修改现成架构的系统筛选器，由于与旧版本存在兼容性问题，这些架构默认受到保护。

>[!NOTE]
>
>但是，Adobe建议您不要修改默认参数，以确保最佳安全性。

1. 为相关架构创建扩展或打开现有扩展。
1. 添加子元素 **`<sysfilter name="<filter name>" _operation="delete"/>`** 在主元素中，删除源架构中相同下的过滤器应用程序。
1. 如果需要，可以添加新过滤器，详情请参阅 [系统过滤器](#system-filters).
