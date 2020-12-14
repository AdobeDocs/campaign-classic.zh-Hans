---
solution: Campaign Classic
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 2%

---


# dbindex元素{#dbindex--element}

## 内容模型{#content-model-3}

dbindex:==keyfield

## 属性{#attributes-3}

* @_operation（字符串）
* @applicableIf（字符串）
* @label(string)
* @name(MNTOKEN)
* @unique（布尔值）

## 父项{#parents-3}

`<element>`

## 子项{#children-3}

`<keyfield>`

## 说明{#description-3}

此元素允许您定义链接到表的索引。

## 使用和使用上下文{#use-and-context-of-use-3}

可以定义多个索引。 一个索引可以引用表的一个或多个字段。 索引声明通常遵循主模式元素的定义。

`<dbindex>`中定义的`<keyfield>`元素的顺序很重要。 第一个`<keyfield>`必须是查询主要基于的索引标准。

数据库中索引的名称是通过连接表的名称和索引的名称来计算的。 例如：在创建索引查询期间，表名“Sample”、命名空间“Cus”、索引名“MyIndex”->索引字段的名称：&quot;CusSample_myIndex&quot;。

## 属性描述{#attribute-description-3}

* **_operation(string)**:定义数据库中写入的类型。

   此属性主要用于扩展现成模式。

   可访问值包括：

   * “无”:和解。 这意味着Adobe Campaign将恢复元素，而不更新它，如果元素不存在，也将生成错误。
   * &quot;insertOrUpdate&quot;:插入更新。 这意味着Adobe Campaign将更新元素，如果元素不存在，则会创建它。
   * “插入”:插入。 这意味着Adobe Campaign将插入元素，而不检查元素是否存在。
   * “更新”:更新。 这意味着Adobe Campaign将更新元素，如果元素不存在，则会生成错误。
   * “删除”:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **applicableIf(string)**:考虑索引的条件——接收XTK表达式。
* **label(string)**:索引标签。
* **name(MNTOKEN)**:唯一索引名称。
* **唯一（布尔值）**:如果激活了此选项(@unique=&quot;true&quot;)，则属性将保证索引在其整个字段中的唯一性。

## 示例{#examples-3}

在“id”字段上创建索引。 (`<dbindex>`元素上的“@unique”属性会触发在数据库(查询)中创建索引时添加“UNIQUE” SQL关键字。)

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

在“@mail”和“@phoneNumber”字段上创建复合索引：

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```
