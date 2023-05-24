---
product: campaign
title: 时区管理
description: 时区管理
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---

# 时区管理{#time-zone-management}



## 操作原则 {#operating-principle}

Adobe Campaign允许您根据时区来表示日期：这使国际用户能够在世界各地使用各种时区。 使用同一实例的每个国家/地区都可以管理营销活动的执行、跟踪、存档等。 取决于当地时间。

为了能够在国际范围内使用Adobe Campaign平台，各系统使用的所有日期必须可链接到某个时区。 因此，可以将时区已知的日期导入到任何其他时区中，或者不考虑时区。

通过Adobe Campaign，您可以采用UTC（国际标准时间）格式存储日期/时间。 数据公开后，将转换为运算符的本地日期/时间。 当数据库配置为UTC时，将自动执行转换(请参阅 [配置](#configuration))。 如果数据库未使用UTC进行配置，则平台中日期的时区信息将存储在选项中。

与时区管理相关的主要平台功能包括：导入/导出数据以及操作员和工作流管理。 此 **继承概念** 可用于导入/导出或工作流。 默认情况下，它们是针对数据库服务器时区配置的，但您可以为工作流甚至单个活动重新定义新时区。

**运算符** 可以在以下期间修改时区： **投放配置** 和可以指定执行投放的特定时区。

>[!IMPORTANT]
>
>如果数据库不管理多个时区，则对于所有数据过滤操作，必须按数据库服务器的时区执行SQL查询。

每个Adobe Campaign运算符均链接到时区：此信息在其配置文件中配置。 有关更多信息，请参阅 [本文档](../../platform/using/access-management.md).

当Adobe Campaign平台不需要时区管理时，您可以使用特定的链接时区以本地格式保留存储模式。

## 推荐 {#recommendations}

时区结合了多种现实情况：该表达式可以描述与UTC日期一致的持续时间延迟，或一个区域每年可能更改两次的时间（夏令时）。

例如，在postgreSQL **设置时区&#39;欧洲/巴黎&#39;；** 命令将考虑夏季和冬季时间：根据每年的时间，日期将以UTC+1或UTC+2表示。

但是，如果您使用 **设置时区0200；** 命令，滞后时间将始终为UTC+2。

## 配置 {#configuration}

在数据库创建期间选择日期和时间的存储模式(请参阅 [创建新实例](#creating-a-new-instance))。 如果进行迁移，则链接到日期的小时数将转换为本地日期和小时数(请参阅 [迁移](#migration))。

从技术角度来看，有两种存储方式 **日期+时间** 在数据库中键入信息：

1. 带有时区格式的时间戳：数据库引擎以UTC格式存储日期。 每个打开的会话都将有一个时区，日期将根据时区进行转换。
1. 本地格式+本地时区：所有日期都以本地格式存储（无滞后管理），并为它们分配一个时区。 时区存储在 **WdbcTimeZone** Adobe Campaign选项，并且可以通过以下方式更改 **[!UICONTROL Administration > Platform > Options]** 树的菜单。

>[!IMPORTANT]
>
>请注意，此修改可能会导致数据一致性和同步问题。

### 创建新实例 {#creating-a-new-instance}

为了让多个国际用户处理同一个实例，您需要在创建实例时配置时区，以管理国家/地区之间的时滞。 在创建实例期间，请在 **[!UICONTROL Time zone]** 数据库配置阶段的部分。

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

为确保与访问Adobe Campaign数据库的外部工具兼容， **日期+时间** 键入SQL字段默认保持本地格式。

包含日期的XML字段现在以UTC格式存储。 在加载期间，非UTC格式的字段会使用服务器的时区自动转换。 这意味着所有XML字段将逐步转换为UTC格式。

要使用现有实例，请添加 **WdbcTimeZone** 选项，然后输入实例的时区。

>[!IMPORTANT]
>
>请确保为WdbcTimeZone选项配置了正确的值：稍后执行的更改可能会导致不一致。

可能值的示例：

* 欧洲/巴黎，
* 欧洲/伦敦,
* 美洲/纽约等

   这些值取自tz (Olson)数据库。 有关更多信息，请参阅 [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
