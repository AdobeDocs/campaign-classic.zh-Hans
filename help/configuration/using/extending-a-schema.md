---
solution: Campaign Classic
product: campaign
title: 扩展模式
description: 了解如何扩展模式
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 扩展模式{#extending-a-schema}

>[!IMPORTANT]
>
>某些内置模式不能扩展：主要是定义了以下设置的用户：\
>**dataSource=&quot;file&quot;** and  **mappingType=&quot;xmlFile&quot;**。\
>以下模式不得扩展：**xtk:entityBackupNew**、**xtk:entityBackupOriginal**、**xtk:entityOriginal**、**xtk:form**、**xtk:srcSchema**、**ncm:publishing**、**nl:monitoring**、**nms:calendar**、**nms:remoteTracking**、**nms:userAgentRules**、**xtk:builder**、**xtk:connections**、**xtk:dbInit**、**xtk:funcList**、**xtk:fusion**, **xtk:jst**、**xtk:navtree**、**xtk:queryDef**、**xtk:resourceMenu**、**xtk:模式**、**xtk:scriptContext**、**xtk:session**、**xtk:sqlSchema**、**xtk:strings**。
>此列表并非完全。

扩展现有模式有两种方法：

1. 直接修改源模式。
1. 创建名称相同但命名空间不同的其他模式。 其优点是您无需修改原始模式即可扩展表。

   模式的根元素必须包含&#x200B;**extendedSchema**&#x200B;属性，其中要扩展的模式的名称为其值。

   扩展模式没有自己的模式:从源模式生成的模式将填入扩展模式的字段。

   >[!IMPORTANT]
   >
   >不允许修改应用程序的内置模式，而是模式扩展机制。 否则，在应用程序将来升级时，将不更新修改的模式。 这会导致Adobe Campaign使用中的故障。

   **示例**:nms:recipentschema **的** 扩展。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   **nms:收件人**&#x200B;扩展模式填充了在扩展模式中填充的字段：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   模式的根元素上的&#x200B;**dependingSchemas**&#x200B;属性引用了对扩展模式的依赖关系。

   字段上的&#x200B;**tersTo**&#x200B;属性填充声明该字段的模式。

>[!IMPORTANT]
>
>要考虑修改，您需要重新生成模式。 有关详细信息，请参阅[重新生成模式](../../configuration/using/regenerating-schemas.md)部分。\
>如果修改影响数据库结构，则需要运行更新。 有关更多信息，请参阅[更新数据库结构](../../configuration/using/updating-the-database-structure.md)。

