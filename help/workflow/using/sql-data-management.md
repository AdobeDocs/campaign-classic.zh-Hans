---
title: SQL 数据管理
seo-title: SQL 数据管理
description: SQL 数据管理
seo-description: null
page-status-flag: never-activated
uuid: b6057496-2dd5-4289-96df-98378e4f0ae7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 18d6f5e1-308f-4080-b7c4-ebf836f74842
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 3%

---


# SQL 数据管理{#sql-data-management}

使用 **SQL数据管理** 活动，您可以编写自己的SQL脚本来创建和填充工作表。

## 先决条件{#prerequisites}

在配置活动之前，请确保满足以下先决条件：

* 该活动仅适用于远程数据源。 因 **[!UICONTROL FDA]** 此，(联合数据访问)包必须安装在实例上(请参 [阅本节](../../platform/using/about-fda.md))。
* 出站模式必须存在于联合数据访问库中，并且必须链接到数据库(有关数据模式的详细信息，请参 [阅此部分](../../configuration/using/about-schema-reference.md))。
* 执行工作流的运算符必须具有 **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** 命名权限。 For more on named rights, refer to [this section](../../platform/using/access-management.md#named-rights).

## 配置SQL数据管理活动 {#configuring-the-sql-data-management-activity}

1. 指定活动 **[!UICONTROL Label]**。
1. 选择要 **[!UICONTROL External account]** 使用的外部帐户，然后选择 **[!UICONTROL Outbound schema]** 链接到此。

   >[!CAUTION]
   >
   >出站模式已修复，无法编辑。

1. 添加SQL脚本。

   >[!CAUTION]
   >
   >SQL脚本编写者有责任确保SQL脚本正常工作，并确保其引用（字段名称等） 符合出站模式。

   如果要加载现有SQL代码，请选择该 **[!UICONTROL The SQL script is contained in an entity stored in the database]** 选项。 必须创建SQL脚本并将其存储在/ **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** 菜单 **[!UICONTROL SQL scripts]** 中。

   否则，在专用区域键入或复制粘贴SQL脚本。

   ![](assets/sql_datamanagement.png)

   该活动允许您在脚本中使用以下变量：

   * **活动.tableName**:出站工作表的SQL名称。
   * **任务.incomingTransitionByName(‘name’)。tableName**:传入过渡要使用的工作表的SQL名称(过渡由其名称标识)。

      >[!NOTE]
      >
      >(&#39;name&#39;)值与过渡属性 **[!UICONTROL Name]** 中的字段对应。

1. 如果SQL脚本已包含用于创建出站工作表的命令，请取消选择该 **[!UICONTROL Automatically create work table]** 选项。 否则，工作流一旦执行，将自动创建工作表。
1. 单击 **[!UICONTROL Ok]** 以确认活动配置。

活动现已配置。 它已准备好在工作流中执行。

>[!CAUTION]
>
>一旦执行活动，出站过渡记录计数仅表示。 它可能因SQL脚本的复杂程度而异。
>  
>如果活动重新启动，则无论脚本的执行状态如何，都从脚本的开始执行整个脚本。

## SQL脚本范例 {#sql-script-samples}

>[!NOTE]
>
>本节中的脚本范例将在PostgreSQL下执行。

通过以下脚本，您可以创建工作表并将数据插入到同一工作表中：

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

通过以下脚本，您可以执行CTAS操作(CREATE TABLE AS SELECT)并创建工作表索引：

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

通过以下脚本可以合并两个工作表：

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

