---
solution: Campaign Classic
product: campaign
title: 时区管理
description: 时区管理
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---


# 时区管理{#time-zone-management}

## 工作原理 {#operating-principle}

Adobe Campaign允许您根据日期的时区来表示日期：这使国际用户能够在世界各地的不同时区工作。 每个使用同一实例的国家／地区都可以管理活动的执行、跟踪、归档等。 取决于当地时间。

为了能够在国际范围内使用Adobe Campaign平台，系统使用的所有日期都必须可链接到一个时区。 因此，其时区已知的日期可以导入任何其他时区，或者不管时区。

Adobe Campaign允许您以UTC（协调通用时间）格式存储日期／时间。 当数据被公开时，它将转换为操作符的本地日期／时间。 当数据库以UTC进行配置时，将自动执行转换(请参 [阅配置](#configuration))。 如果数据库未以UTC进行配置，则平台中日期的时区信息会存储在一个选项中。

与时区管理相关的主要平台功能包括：导入／导出数据、操作员和工作流管理。 继 **承概念** 适用于导入／导出或工作流。 默认情况下，它们是为数据库服务器时区配置的，但是您可以为工作流甚至单个活动重新定义新时区。

**操作** 员可以在投放配 **置期间修改时** 区，并可以指定将执行投放的特定时区。

>[!IMPORTANT]
>
>如果查询库不管理多个时区，则对于所有数据过滤操作，必须在数据库服务器的时区中执行SQL。

每个Adobe Campaign运算符都链接到一个时区：此信息在其用户档案中配置。 For more on this, refer to [this document](../../platform/using/access-management.md).

当Adobe Campaign平台不需要时区管理时，您可以将存储模式保留为具有特定链接时区的本地格式。

## 建议{#recommendations}

时区结合了几个现实：该表达式可以描述与UTC日期一起的连续时间延迟，或者描述一个区域的时间，该时间可以每年更改两次（夏令时）。

例如，在postgreSQL中， **SET TIME ZONE为“Europe/Paris”;** command将考虑夏季和冬季时间：日期将以UTC+1或UTC+2表示，具体取决于年份的时间。

但是，如果您使 **用设置时区0200;** 命令时，时差将始终为UTC+2。

## 配置{#configuration}

在创建存储库时，将选择日期和时间的模式(请参 [阅创建新实例](#creating-a-new-instance))。 在迁移时，链接到日期的小时数将转换为本地日期和小时数(请参阅 [迁移](#migration))。

从视图的技术角度来看，有两种方法可以在 **库中存储** “日期+时间”类型信息：

1. 带时区格式的时间戳：数据库引擎以UTC为单位存储日期。 每个打开的会话都有一个时区，并且日期将根据它进行转换。
1. 本地格式+本地时区：所有日期都以本地格式存储（无时差管理），并且会为它们分配一个时区。 时区存储在Adobe Campaign **实例的** WdbcTimeZone选项中 **[!UICONTROL Administration > Platform > Options]** ，并可通过树的菜单进行更改。

>[!IMPORTANT]
>
>请注意，此修改可能导致数据一致性和同步问题。

### Creating a new instance {#creating-a-new-instance}

为了使多个国际用户能够处理同一实例，您需要在创建实例时配置时区，以管理不同国家／地区之间的时差。 在实例创建过程中，在数据库配置阶段的一 **[!UICONTROL Time zone]** 节中选择日期和时间管理模式。

选中该 **[!UICONTROL UTC database (date fields with time zone)]** 选项，以UTC格式（SQL字段和XML字段）存储所有日期和时间的数据。

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>如果您使用 **Oracle**，则Oracle客户端层的时区文件(.dat)必须与服务器上安装的时区文件兼容。

如果数据库不是UTC，则可以选择下拉列表中提供的某个时区。 您还可以使用服务器的时区或选择UTC（协调通用时间）选项。

![](assets/install_wz_unselect_utc_option.png)

选择 **[!UICONTROL UTC Database (date fields with time zone)]** 此选项后，SQL字段将以TIMESTAMP WITH TIMEZONE格式存储。

否则，它们以本地格式存储，您需要选择要应用于数据库的时区。

### 迁移 {#migration}

迁移到早期版本（无时区管理）时，您需要在存储库中定义日期模式。

为确保与访问Adobe Campaign库的外部工具兼容， **默认情况下** ,Date+time类型SQL字段仍以本地格式存储。

包含日期的XML字段现在以UTC存储。 在加载过程中，非UTC格式的字段会使用服务器的时区自动转换。 这意味着所有XML字段将逐步转换为UTC格式。

要使用现有实例，请添 **加WdbcTimeZone** 选项并输入实例的时区。

>[!IMPORTANT]
>
>请确保为WdbcTimeZone选项配置了正确的值：后来所做的更改可能导致不一致。

可能值的示例：

* 欧洲／巴黎，
* 欧洲／伦敦，
* America/New_York等

   这些值取自tz(Olson)数据库。 有关详细信息，请参 [阅https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)。

