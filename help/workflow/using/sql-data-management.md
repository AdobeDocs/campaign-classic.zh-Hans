---
solution: Campaign Classic
product: campaign
title: SQL 数据管理
description: 了解有关SQL数据管理工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 3%

---


# SQL 数据管理{#sql-data-management}

**SQL数据管理**&#x200B;活动允许您编写自己的SQL脚本以创建和填充工作表。

## 先决条件{#prerequisites}

在配置活动之前，请确保满足以下先决条件：

* 该活动仅适用于远程数据源。 因此，**[!UICONTROL FDA]**(联合数据访问)包必须安装在实例上。 [了解详情](../../installation/using/about-fda.md)。
* 出站模式必须存在于数据库中，并且必须链接到联合数据访问数据库。 [了解详情](../../configuration/using/about-schema-reference.md)。
* 执行工作流的运算符必须具有名为right的&#x200B;**[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]**。 [了解详情](../../platform/using/access-management-named-rights.md)。

## 配置SQL数据管理活动{#configuring-the-sql-data-management-activity}

1. 指定活动&#x200B;**[!UICONTROL Label]**。
1. 选择要使用的&#x200B;**[!UICONTROL External account]**，然后选择链接到此外部帐户的&#x200B;**[!UICONTROL Outbound schema]**。

   >[!CAUTION]
   >
   >出站模式已修复，无法编辑。

1. 添加SQL脚本。

   >[!CAUTION]
   >
   >SQL脚本编写者有责任确保SQL脚本正常工作，并确保其引用（字段名称等） 符合出站模式。

   如果要加载现有SQL代码，请选择&#x200B;**[!UICONTROL The SQL script is contained in an entity stored in the database]**&#x200B;选项。 必须在&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]**&#x200B;菜单中创建并存储SQL脚本。

   否则，在专用区域键入或复制粘贴您的SQL脚本。

   ![](assets/sql_datamanagement.png)

   该活动允许您在脚本中使用以下变量：

   * **活动.tableName**:出站工作表的SQL名称。
   * **任务.incomingTransitionByName(&#39;name&#39;)。tableName**:由传入过渡携带的要使用的工作表的SQL名称(过渡由其名称标识)。

      >[!NOTE]
      >
      >(&#39;name&#39;)值与过渡属性中的&#x200B;**[!UICONTROL Name]**&#x200B;字段相对应。

1. 如果SQL脚本已包含用于创建出站工作表的命令，请取消选择&#x200B;**[!UICONTROL Automatically create work table]**&#x200B;选项。 否则，工作流一旦执行，将自动创建工作表。
1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;确认活动配置。

活动现已配置。 它已准备好在工作流中执行。

>[!CAUTION]
>
>一旦活动执行，出站过渡记录计数仅指示性。 它可能因SQL脚本的复杂程度而异。
>  
>如果活动重新启动，则无论脚本的执行状态如何，都从脚本的开头开始执行整个脚本。

## SQL脚本示例{#sql-script-samples}

>[!NOTE]
>
>本节中的脚本示例将在PostgreSQL下执行。

使用以下脚本，您可以创建工作表并将数据插入到同一工作表中：

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

通过以下脚本，您可以合并两个工作表：

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

