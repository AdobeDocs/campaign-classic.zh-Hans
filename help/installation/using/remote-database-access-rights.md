---
product: campaign
title: 访问外部数据库的权限
description: 外部数据库访问权限
feature: Installation, Instance Settings, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 1%

---

# 远程数据库访问权限 {#remote-database-access-rights}



首先，为了使用户能够通过联合数据访问对外部数据库执行操作，后者必须在Adobe Campaign中具有特定的命名权限。

1. 选择 **[!UICONTROL Administration > Access Management > Named Rights]** Adobe Campaign节点。
1. 通过指定您选择的标签来创建新的权限。
1. 此 **[!UICONTROL Name]** 字段必须采用以下格式 **user：base@server**，其中：

   * **用户** 对应于外部数据库中的用户名称。
   * **基础** 与外部数据库的名称相对应。
   * **服务器** 与外部数据库服务器的名称相对应。

     >[!NOTE]
     >
     >此 **：base** 部件在Oracle中是可选的。

1. 保存指明权限，然后将其链接到您从 **[!UICONTROL Administration > Access Management > Operators]** Adobe Campaign节点。

然后，要处理外部数据库中包含的数据，Adobe Campaign用户必须至少具有数据库的“写入”权限才能创建工作表。 Adobe Campaign会自动删除它们。

一般而言，以下权利是必要的：

* **CONNECT**：连接到远程数据库，
* **读取数据**：对包含客户数据的表的只读访问权限，
* **读取&#39;元数据&#39;**：访问服务器数据目录以获取表结构，
* **加载**：在工作表中成批加载（处理集合和连接时需要），
* **创建/删除** 对象 **表/索引/过程/函数** (仅适用于Adobe Campaign生成的工作表)，
* **说明** （建议）：用于监视出现问题时的性能，
* **写入数据** （具体取决于集成方案）。

数据库管理员需要使这些权限与特定于每个数据库引擎的权限相匹配。 有关更多信息，请参阅以下部分。

## FDA权限 {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **正在连接到远程数据库** | 仓库使用情况、数据库使用情况以及架构权限使用情况 | 创建链接到AWS帐户的用户 | 创建会话权限 | CONNECT权限 | CONNECT权限 | 创建与具有ALL PRIVILEGES的远程主机绑定的用户 |
| **创建表** | 根据方案权限创建表 | CREATE权限 | CREATE TABLE权限 | “创建表”权限 | CREATE权限 | CREATE权限 |
| **创建索引** | N/A | CREATE权限 | INDEX或CREATE ANY INDEX | ALTER权限 | CREATE权限 | INDEX权限 |
| **创建函数** | CREATE函数ON方案权限 | USAGE ON LANGUAGE plythonu权限用于调用外部python脚本 | CREATE PROCEDURE或CREATE ANY PROCEDURE权限 | 创建函数权限 | USAGE权限 | CREATE ROUTINE权限 |
| **创建过程** | N/A | USAGE ON LANGUAGE plythonu权限用于调用外部python脚本 | CREATE PROCEDURE或CREATE ANY PROCEDURE权限 | “创建过程”权限 | USAGE权限（过程是函数） | CREATE ROUTINE权限 |
| **删除对象（表、索引、函数、过程）** | 拥有对象 | 拥有对象或成为超级用户 | 删除任意&lt;对象>权限 | ALTER权限 | 表：拥有表索引：拥有索引函数：拥有函数 | DROP权限 |
| **监视执行** | 对所需对象的MONITOR权限 | 使用EXPLAIN命令不需要任何特权 | INSERT和SELECT权限以及执行EXPLAIN PLAN所基于的语句的必要权限 | SHOWPLAN权限 | 使用EXPLAIN语句不需要特权 | SELECT权限 |
| **写入数据** | INSERT和/或UPDATE权限（取决于写入操作） | INSERT and UPDATE权限 | INSERT和UPDATE或INSERT和UPDATE ANY TABLE权限 | INSERT和UPDATE权限 | INSERT and UPDATE权限 | INSERT and UPDATE权限 |
| **将数据加载到表中** | 在方案上创建阶段，在目标表权限上选择并插入 | SELECT和INSERT权限 | SELECT和INSERT权限 | 插入、管理批量操作和ALTER TABLE权限 | SELECT和INSERT权限 | FILE权限 |
| **访问客户端数据** | 选择（将来）表或视图权限 | SELECT权限 | 选择或选择任何表权限 | 选择权限 | SELECT权限 | SELECT权限 |
| **访问元数据** | SELECT on INFORMATION_SCHEMA方案权限 | SELECT权限 | 使用DESCRIBE语句不需要特权 | 查看定义权限 | 使用“\d table”命令不需要权限 | SELECT权限 |

|   | DB2 UDB | teradata | InfiniDB | sybase IQ/Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **正在连接到远程数据库** | CONNECT权限 | CONNECT权限 | 创建与具有ALL PRIVILEGES的远程主机绑定的用户 | 使用CONNECT语句无需权限 | 无需权限 | CONNECT权限 |
| **创建表** | CREATETAB权限 | CREATE TABLE或TABLE关键字 | CREATE权限 | 资源权限和CREATE权限 | TABLE权限 | CREATE权限 |
| **创建索引** | INDEX权限 | CREATE INDEX或INDEX关键字 | INDEX权限 | 资源权限和CREATE权限 | INDEX权限 | CREATE权限 |
| **创建函数** | IMPLICIT_SCHEMA权限或CREATEIN权限 | CREATE FUNCTION或FUNCTION关键字 | CREATE ROUTINE权限 | Java函数的RESOURCE权限或DBA权限 | FUNCTION权限 | CREATE函数权限 |
| **创建过程** | IMPLICIT_SCHEMA权限或CREATEIN权限 | CREATE PROCEDURE或PROCEDURE关键字 | CREATE ROUTINE权限 | RESOURCE权限 | PROCEDURE权限 | CREATE函数权限 |
| **删除对象（表、索引、函数、过程）** | DROPIN权限或CONTROL权限，或拥有对象 | DROP &lt; object >或对象相关关键字 | DROP权限 | 拥有对象或DBA权限 | DROP权限 | 拥有对象 |
| **监视执行** | 说明权限 | 使用EXPLAIN语句不需要特权 | SELECT权限 | 只有系统管理员可以执行sp_showplan | 使用EXPLAIN语句不需要特权 | 使用EXPLAIN语句不需要特权 |
| **写入数据** | INSERT和UPDATE权限或DATACCESS权限 | INSERT and UPDATE权限 | INSERT and UPDATE权限 | INSERT和UPDATE权限 | INSERT and UPDATE权限 | INSERT and UPDATE权限 |
| **将数据加载到表中** | LOAD权限 | SELECT和INSERT权限分别使用COPY TO和COPY FROM语句 | FILE权限 | 是表的所有者或ALTER权限。 根据 — gl选项的不同，可能只有在用户具有DBA权限时才执行LOAD TABLE | SELECT和INSERT权限 | SELECT和INSERT权限 |
| **访问客户端数据** | INSERT/UPDATE权限或DATACCESS权限 | SELECT权限 | SELECT权限 | 选择权限 | SELECT权限 | SELECT权限 |
| **访问元数据** | 使用DESCRIBE语句无需授权 | 显示权限 | SELECT权限 | 使用DESCRIBE语句无需权限 | 使用“\d table”命令不需要权限 | 使用SHOW命令不需要任何特权 |
