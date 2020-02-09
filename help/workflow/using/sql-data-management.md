---
title: SQL数据管理
seo-title: SQL数据管理
description: SQL数据管理
seo-description: null
page-status-flag: never-activated
uuid: b6057496-2dd5-4289-96df-98378e4f0ae7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 18d6f5e1-308f-4080-b7c4-ebf836f74842
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# SQL数据管理{#sql-data-management}

通过 **“SQL数据管理** ”活动，您可以编写自己的SQL脚本来创建和填充工作表。

## 先决条件 {#prerequisites}

在配置活动之前，请确保满足以下先决条件：

* 活动仅对远程数据源可用。 因 **[!UICONTROL FDA]** 此，(Federated Data Access)包必须安装在实例上(请参 [阅本节](../../platform/using/accessing-an-external-database.md))。
* 出站架构必须存在于数据库中并链接到FDA数据库(有关数据架构的详细信息，请参 [阅本节](../../configuration/using/about-schema-reference.md))。
* 执行工作流的操作符必须具有命 **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** 名权限。 For more on named rights, refer to [this section](../../platform/using/access-management.md#named-rights).

## 配置SQL数据管理活动 {#configuring-the-sql-data-management-activity}

1. 指定活动 **[!UICONTROL Label]**。
1. 选择要 **[!UICONTROL External account]** 使用的帐户，然后选择链 **[!UICONTROL Outbound schema]** 接到此外部帐户的帐户。

   >[!CAUTION]
   >
   >出站架构已修复，无法编辑。

1. 添加SQL脚本。

   >[!CAUTION]
   >
   >SQL脚本编写者有责任确保SQL脚本正常工作并确保其引用（字段名称等）与“出站”架构相符。

   如果要加载现有SQL代码，请选择该 **[!UICONTROL The SQL script is contained in an entity stored in the database]** 选项。 必须创建SQL脚本并将其存储在 **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** /菜 **[!UICONTROL SQL scripts]** 单中。

   否则，在专用区域键入或复制粘贴SQL脚本。

   ![](assets/sql_datamanagement.png)

   该活动允许您在脚本中使用以下变量：

   * **activity.tableName**:出站工作表的SQL名称。
   * **task.incomingTransitionByName(‘name’)。tableName**:传入的转换要使用的工作表的SQL名称（转换由其名称标识）。

      >[!NOTE]
      >
      >(&#39;name&#39;)值与转换属性中 **[!UICONTROL Name]** 的字段相对应。

1. 如果SQL脚本已包含用于创建出站工作表的命令，请取消选择该 **[!UICONTROL Automatically create work table]** 选项。 否则，工作流执行后将自动创建工作表。
1. 单击 **[!UICONTROL Ok]** 以确认活动配置。

活动现已配置。 它已准备好在工作流中执行。

>[!CAUTION]
>
>一旦执行活动，出站转换记录计数仅指示。 它可能因SQL脚本的复杂程度而异。
>  
>如果重新启动活动，则无论其执行状态如何，都将从开始执行整个脚本。

## SQL脚本示例 {#sql-script-samples}

>[!NOTE]
>
>本节中的脚本范例将在PostgreSQL下执行。

通过以下脚本，您可以创建工作表并将数据插入同一工作表：

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

通过以下脚本，可以合并两个工作表：

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

