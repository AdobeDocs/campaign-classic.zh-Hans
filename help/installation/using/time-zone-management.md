---
product: campaign
title: 时区管理
description: 时区管理
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---

# 时区管理{#time-zone-management}

![](../../assets/v7-only.svg)

## 操作原则 {#operating-principle}

Adobe Campaign允许您根据其时区来表示日期：这使国际用户能够在不同时区工作。 使用同一实例的每个国家/地区都可以管理促销活动的执行、跟踪、归档等。 取决于当地时间。

为了能够在国际范围内使用Adobe Campaign平台，系统使用的所有日期都必须可链接到一个时区。 因此，其时区已知的日期可以导入任何其他时区，或不管时区如何。

Adobe Campaign允许您以UTC（协调通用时间）格式存储日期/时间。 当数据公开时，它会转换为运算符的本地日期/时间。 当数据库以UTC进行配置时，会自动执行转换(请参阅 [配置](#configuration))。 如果数据库未按UTC进行配置，则平台中日期时区的信息将存储在一个选项中。

时区管理的主要平台功能包括：导入/导出数据和运算符以及工作流管理。 的 **继承概念** 可用于导入/导出或工作流。 默认情况下，它们是为数据库服务器时区配置的，但您可以为工作流甚至单个活动重新定义新时区。

**运算符** 可在 **投放配置** 和可以指定执行投放的特定时区。

>[!IMPORTANT]
>
>如果数据库不管理多个时区，则对于所有数据过滤操作，必须在数据库服务器的时区中执行SQL查询。

每个Adobe Campaign运算符都链接到一个时区：此信息在其配置文件中进行配置。 有关更多信息，请参阅 [本文档](../../platform/using/access-management.md).

当Adobe Campaign平台不需要时区管理时，您可以将存储模式保留为具有特定链接时区的本地格式。

## 推荐 {#recommendations}

时区结合了以下几个现实：表达式可以用UTC日期描述恒定的时滞，或者用某个区域的时间描述，该时间可能每年更改两次（夏令时）。

例如，在postgreSQL中， **设置时区“欧洲/巴黎”；** command将考虑夏季和冬季时间：日期将以UTC+1或UTC+2表示，具体取决于年份时间。

但是，如果您使用 **设置时区0200;** ，则滞后时间将始终为UTC+2。

## 配置 {#configuration}

在数据库创建期间选择日期和时间的存储模式(请参阅 [创建新实例](#creating-a-new-instance))。 在迁移时，链接到日期的小时数将转换为本地日期和小时数(请参阅 [迁移](#migration))。

从技术角度来看，存储有两种方式 **日期+时间** 在数据库中键入信息：

1. 带时区格式的时间戳：数据库引擎以UTC格式存储日期。 每个打开的会话都将有一个时区，并且日期将根据时区进行转换。
1. 本地格式+本地时区：所有日期都以本地格式存储（无时差管理），并且会为它们分配一个时区。 时区存储在 **WdbcTimeZone** 选项，可通过 **[!UICONTROL Administration > Platform > Options]** 菜单。

>[!IMPORTANT]
>
>请注意，此修改可能会导致数据一致性和同步问题。

### 创建新实例 {#creating-a-new-instance}

为了使多个国际用户能够处理同一实例，您需要在创建实例时配置时区，以管理不同国家/地区之间的时差。 在实例创建期间，在 **[!UICONTROL Time zone]** 数据库配置阶段的部分。

检查 **[!UICONTROL UTC database (date fields with time zone)]** 选项，以UTC格式（SQL字段和XML字段）存储所有日期和时间的数据。

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>如果您使用 **Oracle**，则Oracle客户端层的时区文件(.dat)必须与服务器上安装的时区文件兼容。

如果数据库不是UTC时区，则可以选择下拉列表中提供的时区之一。 您还可以使用服务器的时区或选择UTC（协调通用时间）选项。

![](assets/install_wz_unselect_utc_option.png)

当 **[!UICONTROL UTC Database (date fields with time zone)]** 选项时， SQL字段将以TIMESTAMP WITH TIMEZONE格式存储。

否则，它们将以本地格式存储，您将需要选择要应用于数据库的时区。

### 迁移 {#migration}

迁移到早期版本（不进行时区管理）时，您需要在数据库中定义日期存储模式。

为确保与访问Adobe Campaign数据库的外部工具兼容， **日期+时间** 默认情况下，类型SQL字段仍以本地格式存储。

包含日期的XML字段现在以UTC格式存储。 在加载期间，非UTC格式的字段会使用服务器的时区自动转换。 这意味着所有XML字段将逐步转换为UTC格式。

要使用现有实例，请将 **WdbcTimeZone** 选项，然后输入实例的时区。

>[!IMPORTANT]
>
>请确保为WdbcTimeZone选项配置了正确的值：以后进行的更改可能会导致不一致。

可能值的示例：

* 欧洲/巴黎，
* 欧洲/伦敦，
* 美国/纽约等

   这些值取自tz(Olson)数据库。 有关更多信息，请参阅 [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
