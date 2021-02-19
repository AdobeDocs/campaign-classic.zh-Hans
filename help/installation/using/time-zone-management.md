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

Adobe Campaign允许您根据日期的时区来表示日期：这使国际用户能够在全球各个时区工作。 每个使用同一实例的国家/地区都可以管理活动的执行、跟踪、归档等。 取决于本地时间。

为了使Adobe Campaign平台能够在国际规模上使用，系统使用的所有日期都必须可链接到一个时区。 因此，其时区已知的日期可以导入任何其他时区，或者不管时区。

Adobe Campaign允许您以UTC（协调通用时间）格式存储日期/时间。 当数据公开时，它将转换为操作符的本地日期/时间。 在以UTC配置数据库时，将自动执行转换（请参阅[Configuration](#configuration)）。 如果数据库未以UTC进行配置，则平台中日期的时区信息会存储在一个选项中。

与时区管理相关的主要平台功能是：导入/导出数据、操作员和工作流管理。 **继承概念**&#x200B;可用于导入/导出或工作流。 默认情况下，它们是为数据库服务器时区配置的，但是，您可以为工作流甚至单个活动重新定义新时区。

**操** 作者在投放配 **置** 过程中扫描修改时区，并可以指定将执行投放的特定时区。

>[!IMPORTANT]
>
>如果查询库不管理多个时区，则对于所有数据过滤操作，必须在数据库服务器的时区中执行SQL。

每个Adobe Campaign运算符都链接到一个时区：此信息在其用户档案中配置。 有关详细信息，请参阅[此文档](../../platform/using/access-management.md)。

当Adobe Campaign平台不需要时区管理时，您可以将存储模式保留为具有特定链接时区的本地格式。

## 建议{#recommendations}

时区结合了几个现实：表达式可以描述与UTC日期或可能每年更改两次的区域的时间（夏令时）的恒定时差。

例如，在postgreSQL中，**SET TIME ZONE &#39;Europe/Paris&#39;;**&#x200B;命令将考虑夏季和冬季时间：日期将以UTC+1或UTC+2表示，具体取决于年份的时间。

但是，如果使用&#x200B;**SET TIME ZONE 0200;**&#x200B;命令，则时滞将始终为UTC+2。

## 配置{#configuration}

在创建存储库期间，将选择日期和时间的模式（请参阅[创建新实例](#creating-a-new-instance)）。 如果发生迁移，链接到日期的小时数将转换为本地日期和小时数（请参阅[迁移](#migration)）。

从技术视图点来看，有两种方法可以在数据库中存储&#x200B;**Date+time**&#x200B;类型信息：

1. 时区格式的时间戳：数据库引擎以UTC格式存储日期。 每个已打开的会话都将有一个时区，并会根据时区转换日期。
1. 本地格式+本地时区：所有日期都以本地格式存储（无时间延迟管理），并为它们分配一个时区。 时区存储在Adobe Campaign实例的&#x200B;**WdbcTimeZone**&#x200B;选项中，并可以通过树的&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;菜单进行更改。

>[!IMPORTANT]
>
>请注意，此修改可能会导致数据一致性和同步问题。

### 创建新实例{#creating-a-new-instance}

为了使多个国际用户在同一实例上工作，您需要在创建实例时配置时区，以管理国家/地区之间的时差。 在创建实例期间，在数据库配置阶段的&#x200B;**[!UICONTROL Time zone]**&#x200B;部分选择日期和时间管理模式。

选中&#x200B;**[!UICONTROL UTC database (date fields with time zone)]**&#x200B;选项，以UTC格式（SQL字段和XML字段）存储包含日期和时间的所有数据。

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>如果您使用&#x200B;**Oracle**，则Oracle客户端层的时区文件(.dat)必须与服务器上安装的时区文件兼容。

如果数据库不是UTC，则可以选择下拉列表中提供的时区之一。 您还可以使用服务器的时区或选择“UTC（协调通用时间）”选项。

![](assets/install_wz_unselect_utc_option.png)

选择&#x200B;**[!UICONTROL UTC Database (date fields with time zone)]**&#x200B;选项后，SQL字段将以TIMESTAMP WITH TIMEZONE格式存储。

否则，它们以本地格式存储，您需要选择要应用于数据库的时区。

### 迁移{#migration}

迁移到早期版本（无时区管理）时，您需要在数据库中定义日期存储模式。

为保证与访问Adobe Campaign数据库的外部工具兼容，默认情况下，**Date+time**&#x200B;类型的SQL字段仍以本地格式存储。

包含日期的XML字段现在以UTC存储。 在加载期间，非UTC格式的字段将使用服务器的时区自动转换。 这意味着所有XML字段将逐步转换为UTC格式。

要使用现有实例，请添加&#x200B;**WdbcTimeZone**&#x200B;选项并输入实例的时区。

>[!IMPORTANT]
>
>请确保为WdbcTimeZone选项配置了正确的值：后来所做的更改可能导致不一致。

可能值的示例：

* 欧洲/巴黎，
* 欧洲/伦敦，
* America/New_York等

   这些值取自tz(Olson)数据库。 有关详细信息，请参阅[https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)。

