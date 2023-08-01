---
product: campaign
title: 元素和属性 — dbindex元素
description: dbindex元素
feature: Schema Extension
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 1%

---

# dbindex元素 {#dbindex--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-3}

dbindex：==keyfield

## 属性 {#attributes-3}

* @_operation（字符串）
* @applicableIf（字符串）
* @label（字符串）
* @name (MNTOKEN)
* @unique（布尔型）

## 父项 {#parents-3}

`<element>`

## 子项 {#children-3}

`<keyfield>`

## 说明 {#description-3}

利用此元素，可定义链接到表的索引。

## 使用和使用环境 {#use-and-context-of-use-3}

可以定义多个索引。 一个索引可以引用表的一个或多个字段。 索引声明通常遵循主架构元素的定义。

的顺序 `<keyfield>` 中定义的元素 `<dbindex>` 非常重要。 第一个 `<keyfield>` 必须是查询所主要依据的索引标准。

通过连接表的名称和索引的名称来计算数据库中索引的名称。 例如：表名“Sample”、命名空间“Cus”、索引名“MyIndex” — >索引创建期间索引字段的名称，查询：“CusSample_myIndex”。

## 属性说明 {#attribute-description-3}

* **操作（字符串）(_O)**：定义在数据库中写入的类型。

  此属性主要用于扩展现成架构。

  可访问值包括：

   * “无”：仅和解。 这意味着Adobe Campaign将恢复元素，而不更新它，如果元素不存在则生成错误。
   * &quot;insertOrUpdate&quot;：使用insertion更新。 这意味着Adobe Campaign将更新元素，如果它不存在，则创建它。
   * &quot;insert&quot;： insertion. 这意味着Adobe Campaign将插入元素而不检查元素是否存在。
   * &quot;update&quot;：更新。 这意味着Adobe Campaign将更新元素，如果它不存在，则产生错误。
   * &quot;delete&quot;：删除。 这意味着Adobe Campaign将恢复和删除元素。

* **appliedIf（字符串）**：考虑索引的条件 — 接收XTK表达式。
* **标签（字符串）**：索引标签。
* **名称(MNTOKEN)**：唯一索引名称。
* **唯一（布尔值）**：如果激活此选项(@unique=&quot;true&quot;)，则属性将保证索引在其整个字段中的唯一性。

## 示例 {#examples-3}

在“id”字段上创建索引。 @unique ( `<dbindex>` 在数据库中创建索引时，元素会触发添加“唯一”SQL关键字（查询）。

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
