---
product: campaign
title: 扩展模式
description: 了解如何扩展模式
role: Data Engineer, Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 4%

---

# 扩展模式{#extending-a-schema}

>[!IMPORTANT]
>
>某些内置架构不得扩展：主要是那些定义了以下设置的架构：\
>**dataSource=&quot;file&quot;** 和 **mappingType=&quot;xmlFile&quot;**.\
>不得扩展以下架构： **xtk：entityBackupNew**， **xtk：entityBackupOriginal**， **xtk：entityOriginal**， **xtk：form**， **xtk：srcSchema**， **ncm：publishing**， **nl：monitoring**， **nms：calendar**， **nms：remoteTracking**， **nms：userAgentRules**， **xtk：builder**， **xtk：连接**， **xtk：dbInit**， **xtk：funcList**， **xtk：fusion**， **xtk： jst**， **xtk：navtree**， **xtk：queryDef**， **xtk：resourceMenu**， **xtk：schema**， **xtk：scriptContext**， **xtk：session**， **xtk：sqlSchema**， **xtk：字符串**.
>这份清单并非详尽无遗。

扩展现有模式的方法有两种：

1. 直接修改源架构。
1. 创建另一个名称相同但命名空间不同的架构。 其优点是，无需修改原始模式即可扩展表。

   架构的根元素必须包含 **extendedschema** 属性，其值为要扩展的模式的名称。

   扩展架构没有自己的架构：从源架构生成的架构将填充扩展架构的字段。

   >[!IMPORTANT]
   >
   >您不得修改应用程序的内置架构，而不得修改架构扩展机制。 否则，修改后的架构将不会在应用程序未来升级时更新。 这可能会导致使用Adobe Campaign时出现问题。

   **示例**：的扩展 **nms：recipient** 架构。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   此 **nms：recipient** 扩展架构中填充了扩展架构中填充的字段：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   此 **依赖模式** 架构的根元素上的属性引用扩展架构的依赖关系。

   此 **beystsTo** 字段上的属性会填充声明该属性的架构。

>[!IMPORTANT]
>
>要考虑修改，您需要重新生成模式。 有关详细信息，请参见[此页面](../../configuration/using/regenerating-schemas.md)。\
>如果修改影响数据库的结构，则需要运行更新。 有关详细信息，请参见[此页面](../../configuration/using/updating-the-database-structure.md)。
