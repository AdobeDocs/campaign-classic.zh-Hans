---
product: campaign
title: 元素和属性
description: dbindex元素
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# dbindex元素 {#dbindex--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-3}

dbindex:==keyfield

## 属性 {#attributes-3}

* @_operation（字符串）
* @applicableIf（字符串）
* @label（字符串）
* @name(MNTOKEN)
* @unique（布尔）

## 父母 {#parents-3}

`<element>`

## 子项 {#children-3}

`<keyfield>`

## 说明 {#description-3}

利用此元素，可定义链接到表的索引。

## 使用和使用上下文 {#use-and-context-of-use-3}

可以定义多个索引。 一个索引可以引用表的一个或多个字段。 索引声明通常遵循主架构元素的定义。

的顺序 `<keyfield>` 在 `<dbindex>` 非常重要。 第一个 `<keyfield>` 必须是查询主要基于的索引条件。

数据库中索引的名称是通过连接表的名称和索引的名称来计算的。 例如：在索引创建查询期间索引字段的表名“示例”、命名空间“自定义”、索引名“MyIndex” — >名称：&quot;CusSample_myIndex&quot;。

## 属性描述 {#attribute-description-3}

* **_operation（字符串）**:定义在数据库中写入的类型。

   此属性主要用于扩展即装即用架构。

   可访问的值包括：

   * &quot;none&quot;:单独协调。 这意味着Adobe Campaign将在不更新元素的情况下恢复该元素，或者在元素不存在时生成错误。
   * &quot;insertOrUpdate&quot;:使用插入进行更新。 这意味着Adobe Campaign将更新元素，或在元素不存在时创建元素。
   * &quot;insert&quot;:插入。 这意味着Adobe Campaign将插入元素，而不检查它是否存在。
   * &quot;update&quot;:更新。 这意味着Adobe Campaign将更新元素，或在元素不存在时生成错误。
   * &quot;delete&quot;:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **appliableIf（字符串）**:考虑索引的条件 — 接收XTK表达式。
* **标签（字符串）**:索引标签。
* **name(MNTOKEN)**:唯一索引名称。
* **唯一（布尔）**:如果激活了此选项(@unique=&quot;true&quot;)，则属性可保证索引在其整个字段中的唯一性。

## 示例 {#examples-3}

在“id”字段上创建索引。 (“@unique”属性位于 `<dbindex>` 在数据库（查询）中创建索引时，元素会触发添加“UNIQUE” SQL关键字。

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
