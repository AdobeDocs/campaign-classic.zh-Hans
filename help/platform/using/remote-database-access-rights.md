---
title: 访问外部数据库
seo-title: 访问外部数据库
description: 访问外部数据库
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6143f23e05f4528a9d76aece3a6e41165e2f95d4

---


# 远程数据库访问权限 {#remote-database-access-rights}

首先，为了使用户能够通过联合数据访问对外部数据库执行操作，后者必须在Adobe Campaign中具有特定的命名权限。

1. 在Adobe Campaign资 **[!UICONTROL Administration > Access Management > Named Rights]** 源管理器中选择节点。
1. 通过指定所选标签创建新权限。
1. 字段 **[!UICONTROL Name]** 必须采用以下格式 **用户：base@server**，其中：

   * **user** 与外部数据库中用户的名称相对应。
   * **base** 与外部数据库的名称相对应。
   * **server** 对应于外部数据库服务器的名称。

      >[!NOTE]
      >
      >Oracle **中的** :base部件是可选的。

1. 保存指定的右侧，然后将其从Adobe Campaign浏览器的节点 **[!UICONTROL Administration > Access Management > Operators]** 链接到所选用户。

然后，要处理外部数据库中包含的数据，Adobe Campaign用户必须对数据库至少具有“写入”权限才能创建工作表。 这些内容会由Adobe Campaign自动删除。

一般而言，下列权利是必要的：

* **CONNECT**:连接到远程数据库，
* **读取数据**:只读访问包含客户数据的表，
* **阅读“MetaData”**:访问服务器数据目录以获得表结构，
* **加载**:在工作表中成批加载（处理集合和连接时需要）,
* **为TABLE** /INDEX/ **PROCEDURE/FUNCTION创建／删除** (仅针对由Adobe Campaign生成的工作表),
* **说明** （建议）:以便在遇到问题时监控性能，
* **写入数据** （取决于集成方案）。

数据库管理员需要使这些权限与每个数据库引擎的特定权限相匹配。 有关详细信息，请参阅下面的部分。

## 联合数据访问权 {#fda-rights}

|   | 雪花 | 红移 | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **连接到远程数据库** | 仓库使用、数据库使用和模式权限使用 | 创建链接到AWS帐户的用户 | 创建会话权限 | CONNECT权限 | CONNECT权限 | 创建绑定到具有所有权限的远程主机的用户 |
| **创建表** | 创建模式权限表 | 创建权限 | 创建表权限 | 创建表权限 | 创建权限 | 创建权限 |
| **创建索引** | N/A | 创建权限 | 索引或创建任何索引权限 | ALTER权限 | 创建权限 | INDEX权限 |
| **创建函数** | 创建关于模式权限的函数 | 使用ON语言plythonu权限能够调用外部python脚本 | 创建过程或创建任何过程权限 | “创建函数”权限 | 使用权限 | 创建例程权限 |
| **创建过程** | N/A | 使用ON语言plythonu权限能够调用外部python脚本 | 创建过程或创建任何过程权限 | 创建过程权限 | 使用权限（过程是函数） | 创建例程权限 |
| **删除对象（表、索引、函数、过程）** | 拥有对象 | 拥有对象或是超级用户 | 删除任何&lt;对象>权限 | ALTER权限 | 表：拥有表索引：拥有索引函数：拥有函数 | DROP权限 |
| **监视执行** | 对所需对象的监视权限 | 使用EXPLAIN命令不需要权限 | INSERT和SELECT权限以及执行EXPLAIN PLAN所基于的语句的必要权限 | SHOWPLAN权限 | 无需特权即可使用EXPLAIN语句 | SELECT权限 |
| **写入数据** | INSERT和／或UPDATE权限（取决于写入操作） | 插入和更新权限 | 插入、更新或插入和更新任何表权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 |
| **将数据加载到表中** | 在模式上创建舞台，选择并插入目标表权限 | 选择和插入权限 | 选择和插入权限 | 插入、管理批量操作和更改表权限 | 选择和插入权限 | 文件权限 |
| **访问客户端数据** | 选择（未来）表或视图权限 | SELECT权限 | 选择或选择任何表权限 | SELECT权限 | SELECT权限 | SELECT权限 |
| **访问元数据** | 选择“信息模式”模式权限 | SELECT权限 | 无需权限即可使用DESCRIBE语句 | 视图定义权限 | 使用“\d表”命令不需要权限 | SELECT权限 |

|   | DB2 UDB | TeraData | InfiniDB | Sybase IQ/Sybase ASE | 内泰扎 | 青梅 | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **连接到远程数据库** | CONNECT权限 | CONNECT权限 | 创建绑定到具有所有权限的远程主机的用户 | 无需权限即可使用CONNECT语句 | 无需权限 | CONNECT权限 | CONNECT权限 |
| **创建表** | CREATETAB颁发机构 | 创建表或表关键字 | 创建权限 | RESOURCE authority and CREATE permission | TABLE权限 | 创建权限 | 创建权限 |
| **创建索引** | INDEX权限 | 创建INDEX或INDEX关键字 | INDEX权限 | RESOURCE authority and CREATE permission | INDEX权限 | 创建权限 | 创建权限 |
| **创建函数** | IMPLICIT_模式机构或CREATEIN权限 | 创建FUNCTION或FUNCTION关键字 | 创建例程权限 | Java函数的RESOURCE权限或DBA权限 | FUNCTION权限 | 使用权限 | 创建函数权限 |
| **创建过程** | IMPLICIT_模式机构或CREATEIN权限 | 创建过程或过程关键字 | 创建例程权限 | 资源授权 | PROCEDURE权限 | 使用权限 | 创建函数权限 |
| **删除对象（表、索引、函数、过程）** | DROPIN权限或CONTROL权限，或拥有对象 | DROP &lt;对象>或对象相关关键字 | DROP权限 | 拥有对象或DBA权限 | DROP权限 | 拥有对象 | 拥有对象 |
| **监视执行** | EXPLAIN authority | 无需特权即可使用EXPLAIN语句 | SELECT权限 | 只有系统管理员才能执行sp_showplan | 无需特权即可使用EXPLAIN语句 | 无需特权即可使用EXPLAIN语句 | 无需特权即可使用EXPLAIN语句 |
| **写入数据** | INSERT和UPDATE权限或DATAACCESS颁发机构 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 | 插入和更新权限 |
| **将数据加载到表中** | LOAD Authority | 选择和插入权限可分别使用“复制到”和“复制自”语句 | 文件权限 | 成为表或ALTER权限的所有者。 根据-gl选项，仅当用户具有DBA权限时才可能执行LOAD TABLE | 选择和插入权限 | 选择和插入权限 | 选择和插入权限 |
| **访问客户端数据** | INSERT/UPDATE权限或DATAACCESS颁发机构 | SELECT权限 | SELECT权限 | SELECT权限 | SELECT权限 | SELECT权限 | SELECT权限 |
| **访问元数据** | 使用DESCRIBE语句不需要授权 | 显示权限 | SELECT权限 | 无需权限即可使用DESCRIBE语句 | 使用“\d表”命令不需要权限 | 使用“\d表”命令不需要权限 | 无需权限即可使用SHOW命令 |