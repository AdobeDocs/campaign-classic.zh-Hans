---
product: campaign
title: 扩展模式
description: 了解如何扩展模式
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 4%

---

# 扩展模式{#extending-a-schema}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
>不得扩展某些内置架构：主要是定义了以下设置的用户：\
>**dataSource=&quot;file&quot;** 和 **mappingType=&quot;xmlFile&quot;**.\
>不能扩展以下架构： **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl：监控**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk：连接**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusion**, **xtk:j**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.
>此列表并不详尽。

扩展现有模式的方法有两种：

1. 直接修改源架构。
1. 创建另一个具有相同名称但命名空间不同的架构。 其优势在于，您无需修改原始架构即可扩展表。

   架构的根元素必须包含 **extendedSchema** 属性，其名称为要扩展的架构的值。

   扩展架构没有其自己的架构：将使用扩展架构的字段填充从源架构生成的架构。

   >[!IMPORTANT]
   >
   >不允许修改应用程序的内置模式，而是模式扩展机制。 否则，在应用程序未来升级时，修改的架构将不会更新。 这可能会导致使用Adobe Campaign时出现故障。

   **示例**:扩展 **nms:recipient** 架构。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   的 **nms:recipient** 扩展架构中填充了扩展架构中填充的字段：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   的 **depingSchemas** 架构的根元素上的属性引用了对扩展架构的依赖关系。

   的 **属于** 字段中的属性将填充声明该属性的架构。

>[!IMPORTANT]
>
>要考虑修改，您需要重新生成架构。 有关详细信息，请参见[此页面](../../configuration/using/regenerating-schemas.md)。\
>如果修改影响数据库的结构，则需要运行更新。 有关详细信息，请参见[此页面](../../configuration/using/updating-the-database-structure.md)。
