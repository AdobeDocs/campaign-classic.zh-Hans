---
product: campaign
title: RDBMS 特定建议
description: RDBMS 特定建议
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 1%

---

# RDBMS 特定建议{#rdbms-specific-recommendations}

![](../../assets/v7-only.svg)

为了帮助您设置维护计划，本节列出了一些与Adobe Campaign支持的各种RDBMS引擎相适应的建议和最佳实践。 但是，这些只是建议。 根据您的内部流程和限制，由您自行调整以适应您的需求。 数据库管理员有责任构建和执行这些计划。

## PostgreSQL {#postgresql}

### 检测大表 {#detecting-large-tables}

1. 您可以将以下视图添加到数据库：

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. 您可以运行此查询以发现大型表和索引：

   ```
   SELECT * FROM uvSpace;
   ```

   或者，您也可以运行此查询，例如，以统一查看所有索引大小：

   ```
   SELECT
      tablename,
      sum(size_mbytes) AS "sizeMB_all",
      (
         SELECT sum(size_mbytes)
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_data",
      (
         SELECT sum(size_mbytes)
         FROM uvspace 
         AS uv2 
         WHERE
            INDEXNAME IS NOT NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_index",
      (
         SELECT ROW_COUNT
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS ROWS FROM uvspace AS uv1
      GROUP BY tablename
      ORDER BY 2 DESC
   ```

### 简单的维护 {#simple-maintenance}

在PostgreSQL中，您可以使用以下典型关键字：

* 真空（完整、分析、详细）
* 重新索引

要运行DAVUM操作，并对其进行分析和计时，可以使用以下语法：

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

我们强烈建议您不要忽略ANALYZE语句。 否则，抽真空表将保留没有统计数据。 原因是生成了新表，然后删除了旧表。 因此，表的对象ID(OID)会发生更改，但不会计算任何统计信息。 因此，您会立即遇到性能问题。

以下是定期执行SQL维护计划的典型示例：

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdelivery;
REINDEX TABLE nmsdelivery;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverystat;
REINDEX TABLE nmsdeliverystat;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflow;
REINDEX TABLE xtkworkflow;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowevent;
REINDEX TABLE xtkworkflowevent;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowjob;
REINDEX TABLE xtkworkflowjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowlog;
REINDEX TABLE xtkworkflowlog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowtask;
REINDEX TABLE xtkworkflowtask;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjoblog;
REINDEX TABLE xtkjoblog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjob;
REINDEX TABLE xtkjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsaddress;
REINDEX TABLE nmsaddress;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverypart;
REINDEX TABLE nmsdeliverypart;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsmirrorpageinfo;
REINDEX TABLE nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe建议从较小的表开始：这样，如果流程在大型表（故障风险最高）上失败，则至少部分维护已完成。
>* Adobe建议您添加特定于数据模型的表，这些表可能会进行重大更新。 这种情况可能适用于 **NmsRecipient** 如果您的每日数据复制流量较大，则为。
>* VAFU和REINDEX语句将锁定表，在执行维护时会暂停某些进程。
>* 对于非常大的表（通常高于5 Gb），真空FULL语句可能会非常低效，并且需要很长时间。 Adobe不建议将它用于 **YyyNmsBroadLogXxx** 表。
>* 此维护操作可通过Adobe Campaign工作流(使用 **[!UICONTROL SQL]** 活动。 如需详细信息，请参阅[此部分](../../workflow/using/architecture.md)。确保将维护安排在活动时间较短的时间内，该时间不会与备份窗口发生冲突。

>


### 重建数据库 {#rebuilding-a-database}

PostgreSQL不提供执行联机表重建的简单方法，因为VAFUM FULL语句锁定表，从而防止了常规生产。 这意味着，在未使用表时必须执行维护。 您可以：

* 在Adobe Campaign平台停止时执行维护，
* 停止可能写入正在重建的表(**nlserver stop wfserver instance.name** 以停止工作流进程)。

以下是使用特定函数生成必需DDL的表碎片整理示例。 以下SQL允许您创建两个新函数： **GenRebuildTablePart1** 和 **GenRebuildTablePart2**，用于生成重新创建表所需的DDL。

* 第一个函数允许您创建工作表(此处为**_tmp**)，该表是原始表的副本。
* 然后，第二个函数删除原始表并重命名工作表及其索引。
* 使用两个函数而不是一个函数意味着如果第一个函数失败，您不会面临删除原始表的风险。

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
```

以下示例可用于工作流中以重建所需的表，而不是使用 **真空/重建** 命令：

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here
```

## Oracle {#oracle}

请联系您的数据库管理员，以了解最适合您的Oracle版本的过程。

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>对于Microsoft SQL Server，您可以使用 [本页](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

以下示例涉及Microsoft SQL Server 2005。 如果您使用的是其他版本，请与数据库管理员联系以了解有关维护过程的信息。

1. 首先，使用具有管理员权限的登录名连接到Microsoft SQL Server Management Studio。
1. 转到 **[!UICONTROL Management > Maintenance Plans]** 文件夹，右键单击该文件夹并选择 **[!UICONTROL Maintenance Plan Wizard]**.
1. 单击 **[!UICONTROL Next]** 第一页出现时。
1. 选择要创建的维护计划类型（为每个任务单独计划或为整个计划单独计划），然后单击 **[!UICONTROL Change...]** 按钮。
1. 在 **[!UICONTROL Job schedule properties]** 窗口，选择所需的执行设置并单击 **[!UICONTROL OK]**，然后单击 **[!UICONTROL Next]**.
1. 选择要执行的维护任务，然后单击 **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >我们建议至少执行下面显示的维护任务。 您也可以选择统计信息更新任务，尽管该任务已经由数据库清理工作流执行。

1. 在下拉列表中，选择要运行的数据库 **[!UICONTROL Database Check Integrity]** 任务。
1. 选择数据库并单击 **[!UICONTROL OK]**，然后单击 **[!UICONTROL Next]**.
1. 配置分配给数据库的最大大小，然后单击 **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >如果数据库的大小超过此阈值，维护计划将尝试删除未使用的数据以释放空间。

1. 重新组织或重建索引：

   * 如果指数碎片化率在10%到40%之间，建议进行重组。

      选择要重新组织的数据库和对象（表或视图），然后单击 **[!UICONTROL Next]**.

      >[!NOTE]
      >
      >根据您的配置，您可以选择以前选择的表或数据库中的所有表。

   * 如果指数碎片率高于40%，则建议重建。

      选择要应用于索引重建任务的选项，然后单击 **[!UICONTROL Next]**.

      >[!NOTE]
      >
      >重建索引过程在处理器使用方面更加受限，它锁定数据库资源。 选择 **[!UICONTROL Keep index online while reindexing]** 选项。

1. 选择要在活动报表中显示的选项，然后单击 **[!UICONTROL Next]**.
1. 检查为维护计划配置的任务列表，然后单击 **[!UICONTROL Finish]**.

   此时将显示维护计划及其各个步骤的状态摘要。

1. 完成维护计划后，单击 **[!UICONTROL Close]**.
1. 在Microsoft SQL Server资源管理器中，双击 **[!UICONTROL Management > Maintenance Plans]** 文件夹。
1. 选择Adobe Campaign维护计划：工作流中详细介绍了各个步骤。

   请注意，已在 **[!UICONTROL SQL Server Agent > Jobs]** 文件夹。 此对象允许您启动维护计划。 在本例中，只有一个对象，因为所有维护任务都属于同一计划的一部分。

   >[!IMPORTANT]
   >
   >要运行此对象，必须启用Microsoft SQL Server代理。

**为工作表配置单独的数据库**

>[!NOTE]
>
>此配置是可选的。

的 **WdbcOptions_TempDbName** 选项用于为Microsoft SQL Server上的工作表配置单独的数据库。 这可以优化备份和复制。

如果希望在另一个数据库上创建工作表（例如，在执行工作流期间创建的表），则可以使用此选项。

将选项设置为“tempdb.dbo.”时，将在Microsoft SQL Server的默认临时数据库上创建工作表。 数据库管理员需要允许对tempdb数据库进行写访问。

如果设置了选项，则它将用于在Adobe Campaign中配置的所有Microsoft SQL Server数据库（主数据库和外部帐户）。 请注意，如果两个外部帐户共享同一服务器，则可能会发生冲突（因为tempdb是唯一的）。 同样，如果两个Campaign实例使用相同的MSSQL服务器，则使用相同的tempdb时可能会发生冲突。
