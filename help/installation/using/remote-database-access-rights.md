---
product: campaign
title: 访问外部数据库的权限
description: 外部数据库访问权限
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 1%

---

# 远程数据库访问权限 {#remote-database-access-rights}

首先，为了使用户能够通过FDA对外部数据库执行操作，后者必须在Adobe Campaign中具有特定的命名权限。

1. 在Adobe Campaign资源管理器中选择&#x200B;**[!UICONTROL Administration > Access Management > Named Rights]**&#x200B;节点。
1. 通过指定所选标签创建新权限。
1. **[!UICONTROL Name]**&#x200B;字段必须采用以下格式&#x200B;**user:base@server**，其中：

   * **** user对应于外部数据库中用户的名称。
   * **** basecorresponse使用外部数据库的名称。
   * **** 服务器与外部数据库服务器的名称相对应。

      >[!NOTE]
      >
      >**:base**&#x200B;部分在Oracle中是可选的。

1. 保存命名的权限，然后将其链接到Adobe Campaign资源管理器的&#x200B;**[!UICONTROL Administration > Access Management > Operators]**&#x200B;节点中的选定用户。

然后，要处理外部数据库中包含的数据，Adobe Campaign用户必须对数据库至少具有“写入”权限才能创建工作表。 这些内容将由Adobe Campaign自动删除。

一般而言，需要拥有以下权限：

* **CONNECT**:连接到远程数据库，
* **读取数据**:对包含客户数据的表的只读访问，
* **阅读“MetaData**”：访问服务器数据目录以获取表结构，
* **加载**:在工作表中批量加载（处理集合和联接时需要），
* **为表/** 索引/ **过程/函数创建/删除** (仅适用于由Adobe Campaign生成的工作表)、
* **说明** （推荐）：在出现问题时监控性能，
* **写入数据** （取决于集成方案）。

数据库管理员需要使这些权限与每个数据库引擎的特定权限相匹配。 有关更多信息，请参阅以下章节。

## FDA权限{#fda-rights}

|   | Snowflake | 红移 | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **连接到远程数据库** | 仓库的使用情况、数据库的使用情况和架构权限的使用情况 | 创建链接到AWS帐户的用户 | 创建会话权限 | CONNECT权限 | CONNECT权限 | 创建与具有所有权限的远程主机绑定的用户 |
| **创建表** | 创建关于架构权限的表 | 创建权限 | 创建表权限 | 创建表权限 | 创建权限 | 创建权限 |
| **创建索引** | N/A | 创建权限 | 索引或创建任何索引权限 | ALTER权限 | 创建权限 | 索引权限 |
| **创建函数** | 创建关于架构权限的函数 | 使用语言plpythonu权限可调用外部python脚本 | 创建过程或创建任何过程权限 | 创建函数权限 | 使用权限 | 创建例程权限 |
| **创建过程** | 不适用 | 使用语言plpythonu权限可调用外部python脚本 | 创建过程或创建任何过程权限 | 创建过程权限 | 使用权限（过程是函数） | 创建例程权限 |
| **删除对象（表、索引、函数、过程）** | 拥有对象 | 拥有对象或是超级用户 | 删除任意&lt;对象>权限 | ALTER权限 | 表：拥有表索引：拥有索引函数：拥有函数 | 删除权限 |
| **监控执行** | 所需对象的MONITOR权限 | 使用EXPLAIN命令无需任何权限 | INSERT和SELECT权限以及执行EXPLAIN PLAN所基于的语句的必要权限 | SHOWPLAN权限 | 使用EXPLAIN语句无需任何权限 | 选择权限 |
| **写入数据** | INSERT和/或UPDATE权限（取决于写入操作） | 插入和更新权限 | 插入和更新或插入和更新任何表权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 |
| **将数据加载到表中** | 在架构上创建暂存，选择并插入目标表权限 | 选择和插入权限 | 选择和插入权限 | 插入、管理批量操作和更改表权限 | 选择和插入权限 | 文件权限 |
| **访问客户端数据** | 选择“开（未来）表”或“查看”权限 | 选择权限 | 选择或选择任何表权限 | 选择权限 | 选择权限 | 选择权限 |
| **访问元数据** | 选择INFORMATION_SCHEMA权限 | 选择权限 | 使用DESCRIBE语句无需任何权限 | 查看定义权限 | 使用“\d表”命令无需权限 | 选择权限 |

|   | DB2 UDB | teradata | InfiniDB | sybase IQ/ Sybase ASE | Netezza | 绿梅 | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **连接到远程数据库** | CONNECT权限 | CONNECT权限 | 创建与具有所有权限的远程主机绑定的用户 | 使用CONNECT语句无需权限 | 无需权限 | CONNECT权限 | CONNECT权限 |
| **创建表** | CREATETAB权限 | 创建表或表关键字 | 创建权限 | 资源权限和创建权限 | 表权限 | 创建权限 | 创建权限 |
| **创建索引** | 索引权限 | 创建索引或索引关键字 | 索引权限 | 资源权限和创建权限 | 索引权限 | 创建权限 | 创建权限 |
| **创建函数** | IMPLICIT_SCHEMA权限或CREATEIN权限 | 创建函数或函数关键字 | 创建例程权限 | Java函数的RESOURCE权限或DBA权限 | 函数权限 | 使用权限 | 创建函数权限 |
| **创建过程** | IMPLICIT_SCHEMA权限或CREATEIN权限 | 创建过程或过程关键字 | 创建例程权限 | 资源权限 | 过程权限 | 使用权限 | 创建函数权限 |
| **删除对象（表、索引、函数、过程）** | DROPIN权限或CONTROL权限或拥有对象 | DROP &lt;对象>或与对象相关的关键字 | 删除权限 | 拥有对象或DBA权限 | 删除权限 | 拥有对象 | 拥有对象 |
| **监控执行** | 解释权限 | 使用EXPLAIN语句无需任何权限 | 选择权限 | 只有系统管理员才能执行sp_showplan | 使用EXPLAIN语句无需任何权限 | 使用EXPLAIN语句无需任何权限 | 使用EXPLAIN语句无需任何权限 |
| **写入数据** | INSERT和UPDATE权限或DATAACCESS权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 |
| **将数据加载到表中** | 加载权限 | 选择和插入权限以分别使用COPY TO和COPY FROM语句 | 文件权限 | 是表的所有者或ALTER权限。 根据 — gl选项，只有在用户具有DBA权限时，才可能执行LOAD TABLE | 选择和插入权限 | 选择和插入权限 | 选择和插入权限 |
| **访问客户端数据** | 插入/更新权限或DATAACCESS权限 | 选择权限 | 选择权限 | 选择权限 | 选择权限 | 选择权限 | 选择权限 |
| **访问元数据** | 使用DESCRIBE语句无需授权 | 显示权限 | 选择权限 | 无需使用DESCRIBE语句的权限 | 使用“\d表”命令无需权限 | 使用“\d表”命令无需权限 | 使用SHOW命令无需任何权限 |
