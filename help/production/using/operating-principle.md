---
solution: Campaign Classic
product: campaign
title: 工作原理
description: 工作原理
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 1%

---


# 工作原理{#operating-principle}

从技术上讲，Adobe Campaign平台是基于几个模块的。

有许多Adobe Campaign模块。 有些操作是连续的，而有些则偶尔启动，以执行管理任务（例如配置数据库连接）或运行重复任务（例如合并跟踪信息）。

有三种类型的Adobe Campaign模块：

* 多实例模块：将为所有实例运行一个进程。 这适用于以下模块：**web**、**syslogd**、**trackinglogd**&#x200B;和&#x200B;**watchdog**(**config-default.xml**&#x200B;文件中的活动)。
* 单实例模块：每个实例运行一个进程。 这适用于以下模块：**mta**、**wfserver**、**inMail**、**sms**&#x200B;和&#x200B;**stat**(**config-`<instance>`.xml**&#x200B;文件中的活动)。.
* 实用程序模块：这些模块是偶尔运行的，以执行偶尔或重复的操作(**cleanup**、**config**、下载跟踪日志等)。

使用安装文件夹的&#x200B;**bin**&#x200B;目录中安装的命令行工具&#x200B;**nlserver**&#x200B;执行模块管理。

**nlserver**&#x200B;工具的一般语法如下：

**nlserver  `<command>``<command arguments>`**

要列表可用模块，请使用&#x200B;**nlserver**&#x200B;命令。

下表详细介绍了可用模块：

| 命令 | 说明 |
|---|---|
| aliasClacining | 标准化明细列表价值 |
| 帐单 | 将系统活动报告发送到billing@neolane.net |
| 清理 | 清理数据库：从数据库中删除过时的数据，并运行数据库引擎优化程序所使用统计信息的更新。 |
| config | 修改服务器配置 |
| 文库 | 数据库副本 |
| 导出 | 导出到命令行：允许您将在Adobe Campaign客户端控制台中创建的导出模型发送到命令行 |
| 文件 | 转换集大小文件 |
| 导入 | 导入到命令行：允许您向命令行发送在Adobe Campaign客户端控制台中创建的导入模型。 |
| inMail | 入站邮件分析器 |
| 安装程序 | 客户安装文件的可用性 |
| java | 通过访问SOAP API执行JavaScript脚本。 |
| 作业 | 命令行处理 |
| 合并 | 表单合并 |
| midSourcing | 在投放模式下恢复中间源信息 |
| 监视器 | XML按实例显示服务器进程和计划任务的状态。 |
| mta | 主代理传输消息 |
| 包 | 导入或导出实体包文件 |
| pdump | 显示服务器进程状态 |
| prepareda | 准备投放动作 |
| 重新启动 | 部分服务器重新启动 |
| runwf | 执行工作流实例 |
| 关闭 | 系统完全关闭 |
| sms | SMS通知处理 |
| sql | SQL脚本执行 |
| 开始 | 其他开始 |
| stat | 维护MTA连接统计 |
| 停止 | 部分系统关闭 |
| 提交 | 提交投放操作 |
| syslogd | 日志和跟踪写入服务器 |
| 跟踪 | 整合和检索跟踪日志 |
| trackinglogd | 跟踪日志写入和清除服务器 |
| 监视 | 启动和监视实例 |
| web | 应用程序服务器（HTTP和SOAP） |
| wfserver | 工作流服务器 |

>[!IMPORTANT]
>
>最后一个模块：链接到应用程序服务器的跟踪和中继模块，为了性能考虑，它通过本机机制通过动态库集成到Apache或IIS Web服务器中。 没有Adobe Campaign命令可让您开始或管理此模块。 因此，必须使用Web服务器本身的命令。

使用以下命令显示模块用法及其参数的语法：**nlserver `[module]` -?**

示例:

**nlserverconfig -?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initialises for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```

