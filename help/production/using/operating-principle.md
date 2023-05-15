---
product: campaign
title: 操作原则
description: 操作原则
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# 操作原则{#operating-principle}



从技术上讲，Adobe Campaign平台基于多个模块。

有许多Adobe Campaign模块。 有些操作是连续的，而有些则偶尔启动以执行管理任务（如配置数据库连接）或运行重复任务（如合并跟踪信息）。

有三种类型的Adobe Campaign模块：

* 多实例模块：所有实例都运行一个进程。 这适用于以下模块： **web**, **syslogd**, **trackinglogd** 和 **监视** ( **config-default.xml** 文件)。
* 单实例模块：每个实例运行一个进程。 这适用于以下模块： **mta**, **wfserver**, **inMail**, **短信** 和 **stat** ( **配置 — `<instance>`.xml** 文件)。
* 实用程序模块：这些模块偶尔运行以执行偶尔或重复的操作(**清理**, **配置**、下载跟踪日志等)。

使用命令行工具执行模块管理 **nlserver** 在 **宾** 安装文件夹的目录。

的常规语法 **nlserver** 工具如下所示：

**nlserver `<command>``<command arguments>`**

有关可用模块的列表，请使用 **nlserver** 命令。

下表详细介绍了可用模块：

| 命令 | 说明 |
|---|---|
| aliasClecaring | 标准化枚举值 |
| 计费 | 将系统活动报告发送到billing@neolane.net |
| 清理 | 清理数据库：从数据库中删除过时的数据，并运行数据库引擎优化程序所使用统计信息的更新。 |
| 配置 | 修改服务器配置 |
| 导出 | 导出到命令行：允许您将在Adobe Campaign客户端控制台中创建的导出模型发送到命令行 |
| fileconvert | 转换设置大小的文件 |
| 导入 | 正在导入到命令行：允许您将在Adobe Campaign客户端控制台中创建的导入模型发送到命令行。 |
| inMail | 入站邮件分析程序 |
| 安装程序 | 客户安装文件的可用性 |
| javascript | 执行JavaScript脚本，并具有对SOAP API的访问权限。 |
| 作业 | 命令行处理 |
| 合并 | 表单合并 |
| midSourcing | 在中间源模式下恢复投放信息 |
| 监测 | XML按实例显示服务器进程和计划任务的状态。 |
| mta | 主代理传输消息 |
| 软件包 | 导入或导出实体包文件 |
| pdump | 显示服务器进程状态 |
| prepareda | 准备投放操作 |
| 重新启动 | 部分服务器重新启动 |
| runwf | 执行工作流实例 |
| 关闭 | 完全系统关闭 |
| 短信 | 短信通知处理 |
| sql | SQL脚本执行 |
| 开始 | 其他开始 |
| stat | 维护MTA连接统计信息 |
| stop | 部分系统关闭 |
| submitda | 提交投放操作 |
| syslogd | 日志和跟踪写入服务器 |
| 跟踪 | 整合和检索跟踪日志 |
| trackinglogd | 跟踪日志写入和清除服务器 |
| 监视 | 启动和监视实例 |
| web | 应用程序服务器（HTTP和SOAP） |
| wfserver | 工作流服务器 |

>[!IMPORTANT]
>
>最后一个模块：链接到应用程序服务器的跟踪和中继模块，为了性能起见，它通过本机机制通过动态库集成到Apache或IIS Web服务器中。 没有可启动或管理此模块的Adobe Campaign命令。 因此，必须使用Web服务器本身的命令。

使用以下命令显示模块用法及其参数的语法： **nlserver `[module]` -?**

示例:

**nlserver配置 — ?**

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
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
