---
product: campaign
title: SQL 数据管理
description: 了解有关SQL数据管理工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: cada78cb-658f-4b9e-8136-31c17cb1d82f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 4%

---

# SQL 数据管理{#sql-data-management}

![](../../assets/common.svg)

的 **SQL数据管理** 活动允许您编写自己的SQL脚本以创建和填充工作表。

## 先决条件 {#prerequisites}

在配置活动之前，请确保满足以下先决条件：

* 活动仅可用于远程数据源。 的 **[!UICONTROL FDA]** 因此，必须在实例上安装（联合数据访问）包。 [了解详情](../../installation/using/about-fda.md)。

   有关更多信息，请根据您的Campaign版本，参阅以下章节：

   ![](assets/do-not-localize/v7.jpeg)[  Campaign v7 文档](../../installation/using/about-fda.md)

   ![](assets/do-not-localize/v8.png)[  Campaign v8 文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html)

* 叫客模式必须存在于数据库中，并且必须链接到FDA数据库。
* 执行工作流的操作员必须具有 **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** 右名。 [了解详情](../../platform/using/access-management-named-rights.md)。

## 配置SQL数据管理活动 {#configuring-the-sql-data-management-activity}

1. 指定活动 **[!UICONTROL Label]**.
1. 选择 **[!UICONTROL External account]** 要使用，请选择 **[!UICONTROL Outbound schema]** 链接到此外部帐户。

   >[!CAUTION]
   >
   >叫客架构已修复，无法编辑。

1. 添加SQL脚本。

   >[!CAUTION]
   >
   >SQL脚本编写器负责确保SQL脚本正常工作，并且其引用（字段名称等） 符合叫客架构。

   如果要加载现有SQL代码，请选择 **[!UICONTROL The SQL script is contained in an entity stored in the database]** 选项。 必须在 **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** 菜单。

   否则，请在专用区域中键入或复制粘贴您的SQL脚本。

   ![](assets/sql_datamanagement.png)

   利用活动，可在脚本中使用以下变量：

   * **activity.tableName**:出站工作表的SQL名称。
   * **task.incomingTransitionByName(&#39;name&#39;)。tableName**:传入过渡所携带的要使用的工作表的SQL名称（过渡由其名称标识）。

      >[!NOTE]
      >
      >(&#39;name&#39;)值对应于 **[!UICONTROL Name]** 字段。

1. 如果SQL脚本已包含用于创建出站工作表的命令，请取消选择 **[!UICONTROL Automatically create work table]** 选项。 否则，一旦工作流执行，将自动创建工作表。
1. 单击 **[!UICONTROL Ok]** 以确认活动配置。

活动现已配置完成。 它已准备好在工作流中执行。

>[!CAUTION]
>
>一旦执行活动，则叫客过渡记录计数仅指示性。 它可能因SQL脚本的复杂程度而异。
>  
>如果活动重新启动，则无论其执行状态如何，整个脚本都会从其开头执行。

## SQL脚本示例 {#sql-script-samples}

>[!NOTE]
>
>此部分中的脚本示例将用于在PostgreSQL下执行。

通过下面的脚本，您可以创建工作表并将数据插入到同一工作表中：

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

通过以下脚本，您可以执行CTAS操作（创建表作为选择）并创建工作表索引：

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

通过下面的脚本，您可以合并两个工作表：

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```
