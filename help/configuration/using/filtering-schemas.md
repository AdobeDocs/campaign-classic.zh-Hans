---
product: campaign
title: 筛选模式
description: 筛选模式
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 3%

---

# 筛选模式{#filtering-schemas}

## 系统筛选器 {#system-filters}

您可以筛选对特定用户的架构访问权限，具体取决于其权限。 通过系统筛选器，您可以使用管理架构中详述的实体的读写权限 **readAccess** 和 **writeAccess** 参数。

>[!NOTE]
>
>此限制仅适用于非技术用户：具有相关权限或使用工作流的技术用户将能够检索和更新数据。

* **readAccess**：提供对架构数据的只读访问权限。

  **警告**  — 必须对所有链接表设置相同的限制。 此配置可能会影响性能。

* **writeAccess**：提供对架构数据的写入权限。

这些筛选器在主 **元素** 架构的级别，如以下示例中所示，可以形成来限制访问。

* 限制写入权限

  此处，过滤器用于禁止没有“管理”权限的操作员在架构上具有“写入”权限。 这意味着只有管理员对此架构描述的实体具有写入权限。

  ```
  <sysFilter name="writeAccess">      
   <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
  </sysFilter>
  ```

* 限制读取和写入权限：

  此处，该过滤器用于禁止所有操作员在架构上同时具有“读取”和“写入”权限。 仅 **内部** 帐户，由表达式“$(loginId)”表示！=0”，具有这些权限。

  ```
  <sysFilter name="readAccess"> 
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  
  <sysFilter name="writeAccess">  
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  ```

  可能 **表达式** 用于定义条件的属性值是TRUE或FALSE。

>[!NOTE]
>
>如果未指定筛选器，则所有操作员都将具有架构的读写权限。

## Protect内置架构 {#protecting-built-in-schemas}

默认情况下，只有具有ADMINISTRATION权限的操作员才可以通过WRITE权限访问内置架构：

* ncm：publishing
* nl：monitoring
* nms：calendar
* xtk：builder
* xtk：连接
* xtk：dbInit
* xtk：entityBackupNew
* xtk：entityBackupOriginal
* xtk：entityOriginal
* xtk：form
* xtk：funcList
* xtk：fusion
* xtk：image
* xtk：javascript
* xtk：jssp
* xtk：jst
* xtk：navtree
* xtk：operatorGroup
* xtk：package
* xtk：queryDef
* xtk：resourceMenu
* xtk：rights
* xtk：schema
* xtk：scriptContext
* xtk：specFile
* xtk：sql
* xtk：sqlSchema
* xtk：srcSchema
* xtk：字符串
* xtk：xslt

>[!IMPORTANT]
>
>的读写权限 **xtk：sessionInfo** 架构只能由Adobe Campaign实例的内部帐户访问。

## 修改内置模式的系统筛选器 {#modifying-system-filters-of-built-in-schemas}

您仍然可以修改现成模式的系统过滤器，由于与旧版本的兼容性问题，这些模式默认受保护。

>[!NOTE]
>
>但是，Adobe建议您不要修改默认参数以确保最佳安全性。

1. 为相关架构创建扩展或打开现有扩展。
1. 添加子元素 **`<sysfilter name="<filter name>" _operation="delete"/>`** 在主元素中删除应用程序下的筛选器，位于原始架构中的相同下。
1. 如果需要，您可以添加新过滤器，如中所述 [系统筛选器](#system-filters).
