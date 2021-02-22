---
solution: Campaign Classic
product: campaign
title: RDBMS 特定建议
description: RDBMS 特定建议
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 1%

---


# RDBMS 特定建议{#rdbms-specific-recommendations}

为了帮助您设置维护计划，本节将列表一些适用于Adobe Campaign支持的各种RDBMS引擎的建议/最佳实践。 然而，这些只是建议。 根据您的内部流程和限制，您应根据自己的需求调整它们。 数据库管理员有责任构建和执行这些计划。

## PostgreSQL {#postgresql}

### 检测大表{#detecting-large-tables}

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

1. 运行以下命令可发现大表和索引：

   ```
   select * from uvSpace;
   ```

### 简单维护{#simple-maintenance}

在PostgreSQL下，您可以使用的典型命令为&#x200B;**真空完全**&#x200B;和&#x200B;**重新索引**。

以下是使用以下两个命令定期执行SQL维护计划的典型示例：

```
vacuum full nmsdelivery;
 reindex table nmsdelivery;
 
 vacuum full nmsdeliverystat;
 reindex table nmsdeliverystat;
 
 vacuum full xtkworkflow;
 reindex table xtkworkflow;
 
 vacuum full xtkworkflowevent;
 reindex table xtkworkflowevent;
 
 vacuum full xtkworkflowjob;
 reindex table xtkworkflowjob;
 
 vacuum full xtkworkflowlog;
 reindex table xtkworkflowlog;
 
 vacuum full xtkworkflowtask;
 reindex table xtkworkflowtask;
 
 vacuum full xtkjoblog;
 reindex table xtkjoblog;
 
 vacuum full xtkjob;
 reindex table xtkjob;
 
 vacuum full nmsaddress;
 reindex table nmsaddress;

 vacuum full nmsdeliverypart;
 reindex table nmsdeliverypart;
 
 vacuum full nmsmirrorpageinfo;
 reindex table nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe建议从较小的表开始：这样，在大型表（故障风险最高）上出现故障时，至少部分维护已完成。
>* Adobe重新命令添加特定于数据模型的表，这些表可能会受到重要更新的影响。 如果您有大的每日数据复制流，则&#x200B;**NmsRecipient**&#x200B;可能是这种情况。
>* **真空**&#x200B;和&#x200B;**重新索引**&#x200B;命令将锁定表，在执行维护时会暂停某些进程。
>* 对于超大表（通常高于5 Gb），**真空完全**&#x200B;可能会变得非常低效，并且需要很长时间。 Adobe不建议将其用于&#x200B;**YyyNmsBroadLogXxx**&#x200B;表。
>* 此维护操作可通过Adobe Campaign工作流使用&#x200B;**[!UICONTROL SQL]**&#x200B;活动来实现（有关详细信息，请参阅[此部分](../../workflow/using/architecture.md)）。 确保计划维护时间较短，不会与备份窗口相冲突。
>



### 正在重建数据库{#rebuilding-a-database}

由于&#x200B;**真空完全**&#x200B;锁定表，因此PostgreSQL不提供执行联机表重建的简单方法，因此防止了常规生产。 这意味着必须在不使用表时执行维护。 您可以：

* 在Adobe Campaign平台停止时执行维护，
* 停止可能写入正在重建的表中的各种Adobe Campaign子服务（**nlserver停止wfserver instance_name**&#x200B;以停止工作流进程）。

以下是使用特定函数生成必需DDL的表碎片整理示例。 以下SQL允许您创建两个新函数：**GenRebuildTablePart1**&#x200B;和&#x200B;**GenRebuildTablePart2**，可用于生成重新创建表所需的DDL。

* 第一个函数允许您创建工作表（** _tmp**此处），它是原始表的副本。
* 然后，第二个函数删除原始表并重命名工作表及其索引。
* 使用两个函数而不是一个函数意味着如果第一个函数失败，您不会冒删除原始表的风险。

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

以下示例可用于工作流中重建所需的表，而不是使用&#x200B;**真空/rebuild**&#x200B;命令：

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

请联系您的数据库管理员，了解最适合您的Oracle版本的过程。

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>对于Microsoft SQL Server，您可以使用有关[本页](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html)的详细维护计划。

以下示例涉及Microsoft SQL Server 2005。 如果您使用的是其他版本，请与数据库管理员联系以了解有关维护过程的信息。

1. 首先，使用具有管理员权限的登录名连接到Microsoft SQL Server Management Studio。
1. 转到&#x200B;**[!UICONTROL Management > Maintenance Plans]**&#x200B;文件夹，右键单击它并选择&#x200B;**[!UICONTROL Maintenance Plan Wizard]**
1. 出现第一页时，单击&#x200B;**[!UICONTROL Next]**。
1. 选择要创建的维护计划类型(每个任务单独计划或整个计划单个计划)，然后单击&#x200B;**[!UICONTROL Change...]**&#x200B;按钮。
1. 在&#x200B;**[!UICONTROL Job schedule properties]**&#x200B;窗口中，选择所需的执行设置并单击&#x200B;**[!UICONTROL OK]** ，然后单击&#x200B;**[!UICONTROL Next]**。
1. 选择要执行的维护任务，然后单击&#x200B;**[!UICONTROL Next]**。

   >[!NOTE]
   >
   >我们建议至少执行下面所示的维护任务。 您也可以选择统计信息更新任务，尽管它已由数据库清理工作流执行。

1. 在下拉列表中，选择要运行&#x200B;**[!UICONTROL Database Check Integrity]**&#x200B;任务的数据库。
1. 选择数据库并单击&#x200B;**[!UICONTROL OK]** ，然后单击&#x200B;**[!UICONTROL Next]**。
1. 配置分配给数据库的最大大小，然后单击&#x200B;**[!UICONTROL Next]**。

   >[!NOTE]
   >
   >如果数据库的大小超过此阈值，维护计划将尝试删除未使用的数据以释放空间。

1. 重新组织或重新构建索引：

   * 如果指数碎片化率在10%至40%之间，建议进行重组。

      选择要重新组织的数据库和对象(表或视图)，然后单击&#x200B;**[!UICONTROL Next]**。

      >[!NOTE]
      >
      >根据您的配置，您可以选择以前选择的表或数据库中的所有表。

   * 如果指数碎片率高于40%，建议重建。

      选择要应用于索引重建任务的选项，然后单击&#x200B;**[!UICONTROL Next]**。

      >[!NOTE]
      >
      >在处理器使用方面，重建索引过程更加紧张，它锁定了数据库资源。 如果希望索引在重建过程中可用，请勾选&#x200B;**[!UICONTROL Keep index online while reindexing]**&#x200B;选项。

1. 选择要在活动报告中显示的选项，然后单击&#x200B;**[!UICONTROL Next]**。
1. 检查为维护计划配置的任务的列表，然后单击&#x200B;**[!UICONTROL Finish]**。

   系统会显示维护计划及其各个步骤的状态汇总。

1. 完成维护计划后，单击&#x200B;**[!UICONTROL Close]**。
1. 在Microsoft SQL Server资源管理器中，多次单击&#x200B;**[!UICONTROL Management > Maintenance Plans]**&#x200B;文件夹。
1. 选择Adobe Campaign维护计划：各个步骤在工作流中有详细介绍。

   请注意，已在&#x200B;**[!UICONTROL SQL Server Agent > Jobs]**&#x200B;文件夹中创建了一个对象。 此对象允许您开始维护计划。 在我们的示例中，只有一个对象，因为所有维护任务都是同一计划的一部分。

   >[!IMPORTANT]
   >
   >要运行此对象，必须启用Microsoft SQL Server代理。

**为工作表配置单独的数据库**

>[!NOTE]
>
>此配置是可选的。

**WdbcOptions_TempDbName**&#x200B;选项允许您为Microsoft SQL Server上的工作表配置单独的数据库。 这将优化备份和复制。

如果希望在另一个数据库上创建工作表（例如，在执行工作流期间创建的表），则可以使用此选项。

将选项设置为“tempdb.dbo.”时，将在Microsoft SQL Server的默认临时数据库上创建工作表。 数据库管理员需要允许对tempdb数据库的写访问。

如果设置了该选项，则该选项将用于所有以Adobe Campaign(主数据库和外部帐户)配置的Microsoft SQL Server数据库。 请注意，如果两个外部帐户共享同一服务器，则可能会发生冲突（因为tempdb将是唯一的）。 同样，如果两个活动实例使用相同的MSSQL服务器，则使用相同的tempdb时可能会发生冲突。
