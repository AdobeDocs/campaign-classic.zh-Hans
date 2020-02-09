---
title: 时区管理
seo-title: 时区管理
description: 时区管理
seo-description: null
page-status-flag: never-activated
uuid: b8926761-65e2-48fd-8689-2ae6b0596e72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: b9846eda-eeca-433e-b961-6dfc2aa2708b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c2b5ce9afa45b472f161d6d62517513888e062e

---


# 时区管理{#time-zone-management}

## 工作原理 {#operating-principle}

Adobe Campaign允许您根据日期的时区来表示日期：这使国际用户能够在世界各地的不同时区工作。 每个使用同一实例的国家／地区都可以管理营销活动、跟踪、存档等的执行。 取决于本地时间。

为了使Adobe Campaign平台能够在国际范围内使用，系统使用的所有日期必须可链接到某个时区。 因此，其时区已知的日期可以导入到任何其他时区，或者不管时区如何。

Adobe Campaign允许您以UTC（协调通用时间）格式存储日期／时间。 当数据公开时，它将转换为操作符的本地日期／时间。 在以UTC格式配置数据库时，将自动执行转换(请参 [阅配置](#configuration))。 如果数据库未以UTC格式配置，则平台中日期时区的信息会存储在一个选项中。

与时区管理相关的主要平台功能包括：导入／导出数据和操作员以及工作流管理。 继承 **概念可用于导入** /导出或工作流。 默认情况下，它们是为数据库服务器时区配置的，但是，您可以为工作流甚至单个活动重新定义新的时区。

**运营商** 可以在交付配置 **期间修改时区** ，并可以指定将执行交付的特定时区。

>[!CAUTION]
>
>如果数据库不管理多个时区，则对于所有数据过滤操作，必须在数据库服务器的时区中执行SQL查询。

每个Adobe Campaign运营商都链接到一个时区：此信息在其配置文件中进行配置。 For more on this, refer to [this document](../../platform/using/access-management.md).

当Adobe Campaign平台不需要时区管理时，您可以将存储模式保留为具有特定链接时区的本地格式。

## 建议 {#recommendations}

时区结合了几个现实：该表达式可以描述与UTC日期的恒定时滞，或可以改变每年两次的区域的时间（夏令时）。

**例如，在postgreSQL中，** SET TIME ZONE &#39;Europe/Paris&#39;;命令将考虑夏季和冬季时间：日期将以UTC+1或UTC+2表示，具体取决于年份的时间。

**但是，如果您使用** SET TIME ZONE 0200;命令时，时滞将始终为UTC+2。

## 配置 {#configuration}

在创建数据库期间，将选择日期和时间的存储模式(请参 [阅创建新实例](#creating-a-new-instance))。 如果是迁移，则链接到日期的小时数将转换为本地日期和小时数(请参阅 [迁移](#migration))。

从技术角度来看，有两种方法可以在数据库中存储 **Date+time** type信息：

1. 时区格式的时间戳：数据库引擎以UTC为单位存储日期。 每个打开的会话都将有一个时区，并会根据时区转换日期。
1. 本地格式+本地时区：所有日期都以本地格式存储（无时滞管理），并且会为它们分配一个时区。 时区存储在Adobe Campaign实例的 **WdbcTimeZone** 选项中，并可通过树的 **[!UICONTROL Administration > Platform > Options]** 菜单进行更改。

>[!CAUTION]
>
>请注意，此修改可能会导致数据一致性和同步问题。

### 创建新实例 {#creating-a-new-instance}

为了使多个国际用户在同一实例上工作，您需要在创建实例时配置时区，以管理国家／地区之间的时差。 在创建实例期间，在数据库配置阶段的部分中选 **[!UICONTROL Time zone]** 择日期和时间管理模式。

选中此 **[!UICONTROL UTC database (date fields with time zone)]** 选项，以UTC格式（SQL字段和XML字段）存储所有日期和时间的数据。

![](assets/install_wz_select_utc_option.png)

>[!CAUTION]
>
>如果您使用 **Oracle**，则Oracle客户端层的时区文件(.dat)必须与服务器上安装的时区文件兼容。

如果数据库不是UTC，则可以选择下拉列表中提供的某个时区。 您还可以使用服务器的时区或选择UTC（协调通用时间）选项。

![](assets/install_wz_unselect_utc_option.png)

选择该 **[!UICONTROL UTC Database (date fields with time zone)]** 选项后，SQL字段将以TIMESTAMP WITH TIMEZONE格式存储。

否则，它们以本地格式存储，您需要选择要应用于数据库的时区。

### 迁移 {#migration}

迁移到早期版本（无时区管理）时，您需要在数据库中定义日期存储模式。

为了确保与访问Adobe Campaign数据库的外部工具兼容， **Date+time** type SQL字段在默认情况下仍以本地格式存储。

包含日期的XML字段现在以UTC存储。 在加载过程中，非UTC格式的字段会使用服务器的时区自动转换。 这意味着所有XML字段将逐步转换为UTC格式。

要使用现有实例，请添加 **WdbcTimeZone** 选项并输入实例的时区。

>[!CAUTION]
>
>请确保为WdbcTimeZone选项配置了正确的值：稍后所做的更改可能导致不一致。

可能的值示例：

* 欧洲／巴黎，
* 欧洲／伦敦
* America/New_York等

   这些值取自tz(Olson)数据库。 有关详细信息，请参 [阅http://en.wikipedia.org/wiki/List_of_tz_database_time_zones](http://en.wikipedia.org/wiki/List_of_tz_database_time_zones)。

