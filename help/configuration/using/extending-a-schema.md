---
title: 扩展架构
seo-title: 扩展架构
description: 扩展架构
seo-description: null
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# 扩展架构{#extending-a-schema}

>[!CAUTION]
>
>某些内置架构不能扩展：主要是定义了以下设置的用户：\
>**dataSource=&quot;file&quot;** and **mappingType=&quot;xmlFile&quot;**。\
>以下架构不得扩展： **xx:entityBackupNew**, **x:entityXxOriginal,** xxX: **xformXtk,Xtk:original:SoriginalScrem:NcomBackup:EntityBup:****************************************************ntyntyDentyS:S:XOrigS:PrinSnms:userAgentXagent规则：Xtk,Xtk:InitXtk连接，XinitXtk:XinitList Xtk,XfuncTkFusionXtk:tk融合Xtk:tk,Xtk:jst**, **xxtree:navschema**, **x:queryDefDef**, **xmenuMenu**, xXprodem:XPhotexContext, **promediaPhoteSphotContext,** jspXtktktktk ****************,xtk.tk.tk.xtk:xtk.
>此列表并非详尽无遗。

有两种方法可扩展现有架构：

1. 直接修改源架构。
1. 创建另一个名称相同但命名空间不同的架构。 优点在于，您无需修改原始架构即可扩展表。

   架构的根元素必须包含extendedSchema **** 属性，并且要扩展的架构的名称作为其值。

   扩展架构没有其自己的架构：将使用扩展架构的字段填充源架构生成的架构。

   >[!CAUTION]
   >
   >不允许修改应用程序的内置架构，而是模式扩展机制。 否则，在应用程序将来升级时，修改的架构将不会更新。 这可能导致Adobe Campaign使用中出现故障。

   **示例**:nms:recipient架构 **的扩展** 。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   nms: **recipient** extended schema填充了扩展架构中填充的字段：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   架 **构的根元素上的dependingSchemas** 属性引用扩展架构上的依赖关系。

   字段 **上的telsTo** 属性填充声明该字段的架构。

>[!CAUTION]
>
>要考虑修改，您需要重新生成架构。 有关详细信息，请参阅重新生 [成架构部分](../../configuration/using/regenerating-schemas.md) 。\
>如果修改影响到数据库的结构，您需要运行更新。 有关详细信息，请参阅更新数 [据库结构一节](../../configuration/using/updating-the-database-structure.md) 。

