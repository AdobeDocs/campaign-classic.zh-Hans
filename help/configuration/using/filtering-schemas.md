---
product: campaign
title: 筛选架构
description: 筛选架构
feature: Custom Resources
role: Developer
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
TQID: https://experienceleague.adobe.com/-EcD9suVVxnqRIgsLdaADQ7T0CIMw1CzSnoqJqNe8xs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2:
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 387
ht-degree: 1%

---

# 筛选架构{#filtering-schemas}

## 系统筛选器 {#system-filters}

您可以筛选对特定用户的架构访问权限，具体取决于其权限。 系统筛选器允许您使用&#x200B;**readAccess**&#x200B;和&#x200B;**writeAccess**&#x200B;参数管理架构中详细描述的实体的读取和写入权限。

>[!NOTE]
>
>此限制仅适用于非技术用户：具有相关权限或使用工作流的技术用户将能够检索和更新数据。

* **readAccess**：提供对架构数据的只读访问权限。

  **警告** — 必须对所有链接表设置相同的限制。 此配置可能会影响性能。

* **writeAccess**：提供对架构数据的写入权限。

这些筛选器是在架构的主&#x200B;**元素**&#x200B;级别输入的，如以下示例所示，可以形成以限制访问。

* 限制写入权限

  此处，过滤器用于禁止没有“管理”权限的操作员在架构上具有“写入”权限。 这意味着只有管理员对此架构描述的实体具有写入权限。

  ```
  <sysFilter name="writeAccess">      
   <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
  </sysFilter>
  ```

* 限制读取和写入权限：

  此处，该过滤器用于禁止所有操作员在架构上同时具有“读取”和“写入”权限。 只有由表达式“$(loginId)&lbrace;0”表示的&#x200B;**internal&lbrace;1!=帐户具有这些权限。**

  ```
  <sysFilter name="readAccess"> 
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  
  <sysFilter name="writeAccess">  
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  ```

  用于定义条件的可用&#x200B;**expr**&#x200B;属性值是TRUE或FALSE。

>[!NOTE]
>
>如果未指定筛选器，则所有操作员都将具有架构的读写权限。

## 保护内置架构 {#protecting-built-in-schemas}

默认情况下，只有具有ADMINISTRATION权限的操作员才可以通过WRITE权限访问内置架构：

* ncm:publishing
* nl:monitoring
* nms:calendar
* xtk:builder
* xtk:connections
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
>**xtk:sessionInfo**&#x200B;架构的读取和写入权限只能由Adobe Campaign实例的内部帐户访问。

## 修改内置模式的系统筛选器 {#modifying-system-filters-of-built-in-schemas}

您仍然可以修改现成模式的系统过滤器，由于与旧版本的兼容性问题，这些模式默认受保护。

>[!NOTE]
>
>但是，Adobe建议您不要修改默认参数以确保最佳安全性。

1. 为相关架构创建扩展或打开现有扩展。
1. 在主元素中添加子元素&#x200B;**`<sysfilter name="<filter name>" _operation="delete"/>`**&#x200B;以删除原始架构中同一元素下的筛选器的应用程序。
1. 如果需要，您可以添加新筛选器，如[系统筛选器](#system-filters)中所述。
