---
product: campaign
title: 时区管理
description: 时区管理
feature: Installation, Instance Settings
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---

# 时区管理{#time-zone-management}



## 操作原则 {#operating-principle}

Adobe Campaign允许您根据时区来表示日期：这使得国际用户可以在世界各地使用各种时区。 每个国家/地区使用同一实例可以管理营销活动的执行、跟踪、存档等。 取决于当地时间

为了能够在国际范围内使用Adobe Campaign平台，各系统使用的所有日期都必须可链接到时区。 因此，时区已知的日期可以导入到任何其他时区中，或者与时区无关。

Adobe Campaign允许您以UTC（协调世界时）格式存储日期/时间。 数据公开后，将转换为运算符的本地日期/时间。 当数据库配置为UTC时会自动执行转换(请参阅 [配置](#configuration))。 如果未使用UTC配置数据库，则平台中日期的时区信息将存储在选项中。

与时区管理相关的主要平台功能包括：导入/导出数据、操作员以及工作流管理。 此 **继承概念** 可用于导入/导出或工作流。 默认情况下，它们是针对数据库服务器时区配置的，但您可以为工作流甚至单个活动重新定义新时区。

**运算符** 可以在以下期间修改时区： **投放配置** 并且可以指定执行投放的特定时区。

>[!IMPORTANT]
>
>如果数据库不管理多个时区，则对于所有数据过滤操作，必须以数据库服务器的时区执行SQL查询。

每个Adobe Campaign运算符均链接到时区：此信息在其配置文件中进行配置。 有关详细信息，请参见 [本文档](../../platform/using/access-management.md).

当Adobe Campaign平台不需要时区管理时，您可以保留具有特定链接时区的本地格式存储模式。

## 推荐做法 {#recommendations}

时区结合了多种现实情况：该表达式可能描述了与UTC日期相同的恒定时间延迟，或区域每年可能更改两次的时间（夏令时）。

例如，在postgresql中， **设置时区&#39;欧洲/巴黎&#39;；** 命令将考虑夏季和冬季时间：根据每年的时间，日期将以UTC+1或UTC+2表示。

但是，如果您使用 **设置时区0200；** 命令，滞后时间将始终为UTC+2。

## 配置 {#configuration}

创建数据库时选择日期和时间的存储模式(请参阅 [创建新实例](#creating-a-new-instance))。 在迁移的情况下，链接到日期的小时数将转换为本地日期和小时数(请参阅 [迁移](#migration))。

从技术角度来看，有两种存储方式 **日期+时间** 在数据库中键入信息：

1. 时区格式的时间戳：数据库引擎以UTC格式存储日期。 每个打开的会话都有一个时区，日期将根据时区进行转换。
1. 本地格式+本地时区：所有日期都以本地格式存储（无时间延迟管理），并为它们分配一个时区。 时区存储在 **WdbcTimeZone** Adobe Campaign选项，并且可以通过 **[!UICONTROL Administration > Platform > Options]** 树的菜单。

>[!IMPORTANT]
>
>请注意，此修改可能会导致数据一致性和同步问题。

### 创建新实例 {#creating-a-new-instance}

为了让多个国际用户处理同一实例，您需要在创建实例时配置时区，以管理国家/地区之间的时差。 在创建实例期间，请在中选择日期和时间管理模式 **[!UICONTROL Time zone]** 数据库配置阶段的部分。

查看 **[!UICONTROL UTC database (date fields with time zone)]** 用于以UTC格式存储所有日期和时间数据的选项（SQL字段和XML字段）。

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>如果您使用 **oracle**，Oracle客户端层的时区文件(.dat)必须与服务器上安装的时区文件兼容。

如果数据库不是UTC时区，您可以选择下拉列表中提供的时区之一。 您还可以使用服务器的时区或选择UTC（协调世界时）选项。

![](assets/install_wz_unselect_utc_option.png)

当 **[!UICONTROL UTC Database (date fields with time zone)]** 选项，则SQL字段将以TIMESTAMP WITH TIMEZONE格式存储。

否则，它们将以本地格式存储，您需要选择要应用于数据库的时区。

### 迁移 {#migration}

迁移到早期版本（没有时区管理）时，您需要在数据库中定义日期存储模式。

要确保与访问Adobe Campaign数据库的外部工具兼容，请 **日期+时间** 默认情况下，类型SQL字段仍以本地格式存储。

包含日期的XML字段现在以UTC格式存储。 在加载期间，非UTC格式的字段会使用服务器的时区自动转换。 这意味着所有XML字段将逐步转换为UTC格式。

要使用现有实例，请添加 **WdbcTimeZone** 选项，然后输入实例的时区。

>[!IMPORTANT]
>
>请确保为WdbcTimeZone选项配置了正确的值：稍后执行的更改可能导致不一致。

可能值的示例：

* 欧洲/巴黎，
* 欧洲/伦敦，
* 美洲/纽约等

  这些值取自tz (Olson)数据库。 有关更多信息，请参阅 [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## oracle数据库和服务器时区

对于主数据库，Campaign使用服务器时区设置数据库连接上的会话时区。 “WdbcTimeZone”选项没有影响。 因此，服务器时区应与Campaign使用的主数据库的时区匹配。 如果无法更改服务器时区，则可以通过在customer.sh中设置TZ环境变量来覆盖Campaign使用的时区。