---
solution: Campaign Classic
product: campaign
title: 筛选模式
description: 筛选模式
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# 滤镜模式{#filtering-schemas}

## 系统过滤器{#system-filters}

您可以根据特定用户的权限筛选对其的模式访问权限。 系统过滤器允许您使用&#x200B;**readAccess**&#x200B;和&#x200B;**writeAccess**&#x200B;参数管理模式中详细实体的读和写权限。

>[!NOTE]
>
>此限制仅适用于非技术用户：具有相关权限或使用工作流的技术用户将能够检索和更新数据。

* **readAccess**:提供对模式数据的只读访问。

   **警告**  — 必须使用相同的限制设置所有链接的表。此配置会影响性能。

* **writeAccess**:提供对模式数据的写入访问。

这些过滤器在模式的主&#x200B;**元素**&#x200B;级别输入，并且如以下示例所示，可以形成这些以限制访问。

* 限制写入权限

   此处，过滤器用于在没有ADMINISTRATION权限的情况下禁止操作员对模式的WRITE权限。 这意味着只有管理员才对本模式描述的实体具有写权限。

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 限制读取和写入权限：

   此处，过滤器用于禁止所有操作符对模式的读取和写入权限。 仅&#x200B;**internal**&#x200B;帐户，由表达式&quot;$(loginId)!=0&quot;，具有这些权限。

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   用于定义条件的可能&#x200B;**expr**&#x200B;属性值为TRUE或FALSE。

>[!NOTE]
>
>如果未指定任何过滤器，则所有运算符都将具有对模式的读写权限。

## Protect内置模式{#protecting-built-in-schemas}

默认情况下，内置模式只能通过具有“管理”权限的操作员的“写入”权限访问：

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
* xtk:strings
* xtk:xslt

>[!IMPORTANT]
>
>**xtk:sessionInfo**&#x200B;模式的读和写权限只能由Adobe Campaign实例的内部帐户访问。

## 修改内置模式{#modifying-system-filters-of-built-in-schemas}的系统过滤器

您仍然可以修改现成模式的系统过滤器，这些默认受保护，因为与旧版本的兼容性问题。

>[!NOTE]
>
>但是，Adobe建议您不要修改默认参数以确保最佳安全性。

1. 为相关模式创建扩展或打开现有扩展。
1. 在主元素中添加一个子元素&#x200B;**`<sysfilter name="<filter name>" _operation="delete"/>`**，以删除来源模式中相同的滤镜应用。
1. 如果您愿意，可以添加新的过滤器，如[系统过滤器](#system-filters)中所述。

