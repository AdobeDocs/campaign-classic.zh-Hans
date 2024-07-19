---
product: campaign
title: 访问外部数据库的权限
description: 外部数据库访问权限
feature: Installation, Instance Settings, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# 远程数据库访问权限 {#remote-database-access-rights}



首先，为了使用户能够通过联合数据访问对外部数据库执行操作，后者必须在Adobe Campaign中具有特定的命名权限。

1. 在Adobe Campaign资源管理器中选择&#x200B;**[!UICONTROL Administration > Access Management > Named Rights]**&#x200B;节点。
1. 通过指定您选择的标签来创建新的权限。
1. **[!UICONTROL Name]**&#x200B;字段必须采用以下格式&#x200B;**user：base@server**，其中：

   * **用户**&#x200B;对应于外部数据库中的用户名称。
   * **base**&#x200B;对应于外部数据库的名称。
   * **服务器**&#x200B;对应于外部数据库服务器的名称。

     >[!NOTE]
     >
     >**：base**&#x200B;部分在Oracle中是可选的。

1. 保存指明权限，然后将其从Adobe Campaign资源管理器的&#x200B;**[!UICONTROL Administration > Access Management > Operators]**&#x200B;节点链接到您选择的用户。

然后，要处理外部数据库中包含的数据，Adobe Campaign用户必须至少具有数据库的“写入”权限才能创建工作表。 Adobe Campaign会自动删除它们。

一般而言，以下权利是必要的：

* **CONNECT**：连接到远程数据库，
* **读取数据**：对包含客户数据的表的只读访问权限，
* **读取&#39;MetaData&#39;**：访问服务器数据目录以获取表结构，
* **LOAD**：在工作表中成批加载（处理集合和连接时需要），
* 为&#x200B;**TABLE/INDEX/PROCEDURE/FUNCTION**&#x200B;创建/删除&#x200B;**CREATE/DROP**(仅适用于Adobe Campaign生成的工作表)，
* **EXPLAIN**（推荐）：用于监视出现问题的性能，
* **写入数据**（取决于集成方案）。

数据库管理员需要使这些权限与特定于每个数据库引擎的权限相匹配。 有关更多信息，请参阅以下部分。

## FDA权限 {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **正在连接到远程数据库** | 仓库使用情况、数据库使用情况以及架构权限使用情况 | 创建链接到AWS帐户的用户 | 创建会话权限 | CONNECT权限 | CONNECT权限 | 创建与具有ALL PRIVILEGES的远程主机绑定的用户 |
| **正在创建表** | 根据方案权限创建表 | CREATE权限 | CREATE TABLE权限 | “创建表”权限 | CREATE权限 | CREATE权限 |
| **正在创建索引** | N/A | CREATE权限 | INDEX或CREATE ANY INDEX | ALTER权限 | CREATE权限 | INDEX权限 |
| **正在创建函数** | CREATE函数ON方案权限 | USAGE ON LANGUAGE plythonu权限用于调用外部python脚本 | CREATE PROCEDURE或CREATE ANY PROCEDURE权限 | 创建函数权限 | USAGE权限 | CREATE ROUTINE权限 |
| **正在创建过程** | N/A | USAGE ON LANGUAGE plythonu权限用于调用外部python脚本 | CREATE PROCEDURE或CREATE ANY PROCEDURE权限 | “创建过程”权限 | USAGE权限（过程是函数） | CREATE ROUTINE权限 |
| **正在删除对象（表、索引、函数、过程）** | 拥有对象 | 拥有对象或成为超级用户 | 删除任意&lt;对象>权限 | ALTER权限 | 表：拥有表索引：拥有索引函数：拥有函数 | DROP权限 |
| **正在监视执行** | 对所需对象的MONITOR权限 | 使用EXPLAIN命令不需要任何特权 | INSERT和SELECT权限以及执行EXPLAIN PLAN所基于的语句的必要权限 | SHOWPLAN权限 | 使用EXPLAIN语句不需要特权 | SELECT权限 |
| **正在写入数据** | INSERT和/或UPDATE权限（取决于写入操作） | INSERT and UPDATE权限 | INSERT和UPDATE或INSERT和UPDATE ANY TABLE权限 | INSERT和UPDATE权限 | INSERT and UPDATE权限 | INSERT and UPDATE权限 |
| **将数据加载到表中** | 在方案上创建阶段，在目标表权限上选择并插入 | SELECT和INSERT权限 | SELECT和INSERT权限 | 插入、管理批量操作和ALTER TABLE权限 | SELECT和INSERT权限 | FILE权限 |
| **正在访问客户端数据** | 选择（将来）表或视图权限 | SELECT权限 | 选择或选择任何表权限 | 选择权限 | SELECT权限 | SELECT权限 |
| **正在访问元数据** | SELECT on INFORMATION_SCHEMA方案权限 | SELECT权限 | 使用DESCRIBE语句不需要特权 | 查看定义权限 | 使用“\d table”命令不需要权限 | SELECT权限 |

|   | teradata | InfiniDB | sybase IQ/Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|
| **正在连接到远程数据库** | CONNECT权限 | 创建与具有ALL PRIVILEGES的远程主机绑定的用户 | 使用CONNECT语句无需权限 | 无需权限 | CONNECT权限 |
| **正在创建表** | CREATE TABLE或TABLE关键字 | CREATE权限 | 资源权限和CREATE权限 | TABLE权限 | CREATE权限 |
| **正在创建索引** | CREATE INDEX或INDEX关键字 | INDEX权限 | 资源权限和CREATE权限 | INDEX权限 | CREATE权限 |
| **正在创建函数** | CREATE FUNCTION或FUNCTION关键字 | CREATE ROUTINE权限 | Java函数的RESOURCE权限或DBA权限 | FUNCTION权限 | CREATE函数权限 |
| **正在创建过程** | CREATE PROCEDURE或PROCEDURE关键字 | CREATE ROUTINE权限 | RESOURCE权限 | PROCEDURE权限 | CREATE函数权限 |
| **正在删除对象（表、索引、函数、过程）** | DROP &lt; object >或对象相关关键字 | DROP权限 | 拥有对象或DBA权限 | DROP权限 | 拥有对象 |
| **正在监视执行** | 使用EXPLAIN语句不需要特权 | SELECT权限 | 只有系统管理员可以执行sp_showplan | 使用EXPLAIN语句不需要特权 | 使用EXPLAIN语句不需要特权 |
| **正在写入数据** | INSERT and UPDATE权限 | INSERT and UPDATE权限 | INSERT和UPDATE权限 | INSERT and UPDATE权限 | INSERT and UPDATE权限 |
| **将数据加载到表中** | SELECT和INSERT权限分别使用COPY TO和COPY FROM语句 | FILE权限 | 是表的所有者或ALTER权限。 根据 — gl选项的不同，可能只有在用户具有DBA权限时才执行LOAD TABLE | SELECT和INSERT权限 | SELECT和INSERT权限 |
| **正在访问客户端数据** | SELECT权限 | 选择权限 | SELECT权限 | SELECT权限 |
| **正在访问元数据** | 显示权限 | SELECT权限 | 使用DESCRIBE语句无需权限 | 使用“\d table”命令不需要权限 | 使用SHOW命令不需要任何特权 |
