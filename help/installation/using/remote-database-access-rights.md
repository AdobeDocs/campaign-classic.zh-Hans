---
solution: Campaign Classic
product: campaign
title: 访问外部数据库的权限
description: 外部数据库访问权限
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 远程数据库访问权限 {#remote-database-access-rights}

首先，为了使用户能够通过联合数据访问对外部数据库执行操作，后者必须在Adobe Campaign中具有特定的命名权限。

1. 在Adobe Campaign资源管理器中选择&#x200B;**[!UICONTROL Administration > Access Management > Named Rights]**&#x200B;节点。
1. 通过指定所选标签创建新权限。
1. **[!UICONTROL Name]**&#x200B;字段必须采用以下格式&#x200B;**user:base@server**，其中：

   * **user** 与外部数据库中用户的名称相对应。
   * **** basecorresponses使用外部数据库的名称。
   * **服** 务器与外部数据库服务器的名称相对应。

      >[!NOTE]
      >
      >**:base**&#x200B;部件在Oracle是可选的。

1. 保存指定的权限，然后将其从Adobe Campaign资源管理器的&#x200B;**[!UICONTROL Administration > Access Management > Operators]**&#x200B;节点链接到选定用户。

然后，要处理外部Adobe Campaign库中包含的数据，用户必须对数据库至少具有“写入”权限才能创建工作表。 这些内容会由Adobe Campaign自动删除。

一般而言，下列权利是必要的：

* **CONNECT**:连接到远程数据库，
* **读取数据**:只读访问包含客户数据的表，
* **阅读“MetaData”**:访问服务器数据目录以获取表结构，
* **加载**:在工作表中成批加载（处理集合和联接时需要）,
* **为TABLE/** INDEX/ **PROCEDURE/FUNCTION创建/DROP** (仅用于由Adobe Campaign生成的工作表),
* **说明** （推荐）:以监测出问题时的表现，
* **WRITE Data** （取决于集成方案）。

数据库管理员需要使这些权限与每个数据库引擎的特定权限相匹配。 有关详细信息，请参阅下面的部分。

## 联合数据访问权限{#fda-rights}

|   | Snowflake | 红移 | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **连接到远程数据库** | 仓库使用、数据库使用和模式权限使用 | 创建链接到AWS帐户的用户 | 创建会话权限 | CONNECT权限 | CONNECT权限 | 创建绑定到具有所有权限的远程主机的用户 |
| **创建表** | 创建模式权限表 | 创建权限 | 创建表权限 | 创建表权限 | 创建权限 | 创建权限 |
| **创建索引** | N/A | 创建权限 | 索引或创建任何索引权限 | ALTER权限 | 创建权限 | INDEX权限 |
| **创建函数** | 创建模式权限函数 | 使用ON语言plythonu权限能够调用外部python脚本 | 创建过程或创建任何过程权限 | CREATE FUNCTION权限 | 使用权限 | 创建例程权限 |
| **创建过程** | N/A | 使用ON语言plythonu权限能够调用外部python脚本 | 创建过程或创建任何过程权限 | 创建过程权限 | 使用权限（过程是函数） | 创建例程权限 |
| **删除对象（表、索引、函数、过程）** | 拥有对象 | 拥有对象或是超级用户 | 删除任何&lt;对象>权限 | ALTER权限 | 表：拥有表索引：拥有索引函数：拥有函数 | DROP权限 |
| **监视执行** | 对所需对象的监视权限 | 使用EXPLAIN命令无需权限 | INSERT和SELECT权限以及执行EXPLAIN PLAN所基于的语句的必要权限 | SHOWPLAN权限 | 使用EXPLAIN语句无需权限 | SELECT权限 |
| **写入数据** | INSERT和／或UPDATE权限（取决于写入操作） | 插入和更新权限 | 插入、更新或插入和更新任何表权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 |
| **将数据加载到表中** | 在模式上创建舞台，在目标表权限上选择并插入 | 选择和插入权限 | 选择和插入权限 | 插入、管理批量操作和更改表权限 | 选择和插入权限 | 文件权限 |
| **访问客户端数据** | 选择“开始（未来）”表或视图权限 | SELECT权限 | 选择或选择任何表权限 | SELECT权限 | SELECT权限 | SELECT权限 |
| **访问元数据** | 选择“信息模式”模式权限 | SELECT权限 | 使用DESCRIBE语句无需权限 | 视图定义权限 | 使用“\d表”命令不需要权限 | SELECT权限 |

|   | DB2 UDB | teradata | InfiniDB | sybase IQ/Sybase ASE | Netezza | 青梅 | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **连接到远程数据库** | CONNECT权 | CONNECT权限 | 创建绑定到具有所有权限的远程主机的用户 | 无需权限即可使用CONNECT语句 | 无需权限 | CONNECT权限 | CONNECT权限 |
| **创建表** | CREATETAB权限 | 创建TABLE或TABLE关键字 | 创建权限 | 资源权限和创建权限 | TABLE权限 | 创建权限 | 创建权限 |
| **创建索引** | INDEX权限 | 创建INDEX或INDEX关键字 | INDEX权限 | 资源权限和创建权限 | INDEX权限 | 创建权限 | 创建权限 |
| **创建函数** | IMPLICIT_模式权限或CREATEIN权限 | CREATE FUNCTION或FUNCTION关键字 | 创建例程权限 | Java函数的RESOURCE权限或DBA权限 | FUNCTION权限 | 使用权限 | 创建函数权限 |
| **创建过程** | IMPLICIT_模式权限或CREATEIN权限 | CREATE PROCEDURE或PROCEDURE关键字 | 创建例程权限 | 资源权限 | PROCEDURE特权 | 使用权限 | 创建函数权限 |
| **删除对象（表、索引、函数、过程）** | DROPIN权限或CONTROL权限或拥有对象 | DROP &lt;对象>或与对象相关的关键字 | DROP权限 | 拥有对象或DBA权限 | DROP权限 | 拥有对象 | 拥有对象 |
| **监视执行** | 说明权限 | 使用EXPLAIN语句无需权限 | SELECT权限 | 只有系统管理员才能执行sp_showplan | 使用EXPLAIN语句无需权限 | 使用EXPLAIN语句无需权限 | 使用EXPLAIN语句无需权限 |
| **写入数据** | INSERT和UPDATE权限或DATAACCESS权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 |
| **将数据加载到表中** | 加载权限 | 选择和插入权限分别使用COPY TO和COPY FROM语句 | 文件权限 | 成为表或ALTER权限的所有者。 根据-gl选项，仅当用户具有DBA权限时，才可执行LOAD TABLE | 选择和插入权限 | 选择和插入权限 | 选择和插入权限 |
| **访问客户端数据** | INSERT/UPDATE权限或DATAACCESS权限 | SELECT权限 | SELECT权限 | SELECT权限 | SELECT权限 | SELECT权限 | SELECT权限 |
| **访问元数据** | 使用DESCRIBE语句无需授权 | 显示权限 | SELECT权限 | 无需使用DESCRIBE语句的权限 | 使用“\d表”命令不需要权限 | 使用“\d表”命令不需要权限 | 使用SHOW命令不需要权限 |