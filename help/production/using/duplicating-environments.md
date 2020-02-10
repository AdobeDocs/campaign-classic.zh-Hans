---
title: 复制环境
seo-title: 复制环境
description: 复制环境
seo-description: null
page-status-flag: never-activated
uuid: b8fb8083-e3ec-4b1c-9449-73ac03508d89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 9f7118f4-aef0-469c-bbe1-b62bed674faa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# 复制环境{#duplicating-environments}

## 简介 {#introduction}

### 概述 {#overview}

>[!CAUTION]
>
>如果您无权访问服务器和数据库（托管环境），您将无法执行下面所述的过程。 请联系Adobe。

使用Adobe Campaign需要安装和配置一个或多个环境：开发、测试、预制作、生产等。

每个环境都包含一个Adobe Campaign实例，每个Adobe Campaign实例都链接到一个或多个数据库。 应用程序服务器可以执行一个或多个进程：几乎所有这些都可以直接访问实例数据库。

本节详细介绍了要应用于复制Adobe Campaign环境（即将源环境恢复到目标环境）的过程，从而生成两个相同的工作环境。

为此，请应用以下步骤：

1. 在源环境中创建所有实例上的数据库的副本，
1. 在目标环境的所有实例上恢复这些副本，
1. 在启 **** 动之前，在目标环境中运行nms:freezeInstance.js烧灼脚本。

   此过程不会影响服务器及其配置。

   >[!NOTE]
   >
   >在Adobe Campaign的上下文中， **烧灼法将可让您停止所有与外部交互的流程的操** 作组合在一起：日志、跟踪、分发、营销活动工作流等。\
   >此步骤是避免多次传送消息所必需的（一次是从标称环境传送消息，另一次是从复制环境传送消息）。

   >[!CAUTION]
   >
   >一个环境可以包含多个实例。 每个Adobe Campaign实例均需遵守许可合同。 检查您的许可协议，了解您可以拥有多少个环境。\
   >通过以下过程，您可以传输环境，而不会影响已安装的环境和实例数。

### 开始之前 {#before-you-start}

>[!CAUTION]
>
>我们强烈建议在开始传输过程之前，为源和目标环境的所有实例运行数据库的完整备份。 这样，如果出现问题，您就可以恢复备份并返回到初始配置。

要使此过程正常工作，源和目标环境必须具有相同数量的实例、相同的用途（营销实例、交付实例）和类似的配置。 技术配置必须符合软件先决条件。 两个环境中必须安装相同的组件。

## 实施 {#implementation}

### 转移过程 {#transfer-procedure}

本节将帮助您了解通过案例研究将源环境传输到目标环境所需的步骤：我们的目标是将生产环境(**prod** instance)恢复到开发环境(**** dev实例)，以便在尽可能靠近“实时”平台的上下文中工作。

必须谨慎执行以下步骤：复制源环境数据库时，某些进程可能仍在进行中。 烧灼（下面的步骤3）可防止消息发送两次并保持数据一致性。

>[!CAUTION]
>
>* 以下过程在PostgreSQL语言中有效。 如果SQL语言不同（例如，Oracle），则必须调整SQL查询。
>* 以下命令在 **prod** 实例和PostgreSQL下的 **** dev实例的上下文中应用。
>



### 第1步——备份源环境(prod)数据 {#step-1---make-a-backup-of-the-source-environment--prod--data}

复制数据库

首先复制所有源环境数据库。 此操作取决于数据库引擎，并由数据库管理员负责。

在PostgreSQL下，该命令为：

```
pg_dump mydatabase > mydatabase.sql
```

### 第2步——导出目标环境配置(dev) {#step-2---export-the-target-environment-configuration--dev-}

大多数配置元素对于每个环境都不同：外部帐户（中部采购、路由等）、技术选项（平台名称、数据库ID、电子邮件地址和默认URL等）。

在目标数据库上保存源数据库之前，您需要导出目标环境（开发）配置。 为此，请导出以下两个表的内容： **xtkoption** 和 **nmsextaccount**。

此导出允许您保留开发配置并只刷新开发数据（工作流、模板、Web应用程序、收件人等）。

为此，请对以下两个元素执行包导出：

* 将 **** xtk:option表导出到“options_dev.xml”文件中，不带有以下内部名称的记录：“WdbcTimeZone”、“NmsServer_LastPostUpgrade”和“NmsBroadcast_RegexRules”。
* 在“extaccount_dev.xml”文件中，导出 **nms:extAccount** 表，以查看ID不为0(@id &lt;> 0)的所有记录。

检查导出的选项／帐户数是否等于每个文件中要导出的行数。

>[!NOTE]
>
>包导出中要导出的行数为1000行。 如果选项或外部帐户的数量超过1000，则必须执行多项导出操作。
> 
>有关更多信息，请参见[此部分](../../platform/using/working-with-data-packages.md#exporting-packages)。

### 第3步——停止目标环境（开发） {#step-3---stop-the-target-environment--dev-}

您需要在所有目标环境服务器上停止Adobe Campaign流程。 此操作取决于您的操作系统。

您可以停止所有进程，或只停止那些写入数据库的进程。

要停止所有进程，请使用以下命令：

* 在Windows中：

   ```
   net stop nlserver6
   ```

* 在Linux中：

   ```
   /etc/init.d/nlserver6 stop
   ```

使用以下命令检查是否已停止所有进程：

```
nlserver pdump
```

>[!NOTE]
>
>在Windows中， **webmdl进程仍然可以处于活动状态** ，而不会影响其他操作。

您还可以检查系统进程是否仍在运行。

为此，请使用以下过程：

* 在Windows中：打开任 **务管理器** ，检查是否没有 **nlserver.exe进程** 。
* 在Linux中：运行 **ps aux| grep nlserver** 命令并检查没有nlserver进 **程** 。

### 第4步——在目标环境中恢复数据库(dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

要在目标环境中恢复源数据库，请使用以下命令：

```
psql mydatabase < mydatabase.sql
```

### 第5步——审核目标环境（开发） {#step-5---cauterize-the-target-environment--dev-}

为避免出现故障，在目标环境被激活时，不能自动执行链接到交付发送和工作流执行的进程。

为此，请运行以下命令：

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 第6步——检查烧灼 {#step-6---check-cauterization}

1. 检查唯一的deliverypart是ID设置为0的部件：

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. 检查提交状态更新是否正确：

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. 检查工作流状态更新是否正确：

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### 第7步——重新启动目标环境Web进程（开发） {#step-7---restart-the-target-environment-web-process--dev-}

在目标环境中，重新启动所有服务器的Adobe Campaign流程。

>[!NOTE]
>
>在开发环境中重新启动Adobe Campaign **** ，您可以应用其他安全程序：仅启 **动Web** 模块。
>  
>为此，请编辑实例的配置文件(**config-dev.xml**)，然后在每个模块（mta、stat等）的autoStart=&quot;true&quot;选项前添加&quot;_&quot;字符。

运行以下命令以启动Web进程：

```
nlserver start web
```

使用以下命令检查是否只启动了Web进程：

```
nlserver pdump
```

检查对客户端控制台功能的访问。

### 第8步——将选项和外部帐户导入目标环境（开发） {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!CAUTION]
>
>在此步骤中应仅启动Web进程。 如果不是这样，请在继续之前停止其他正在运行的进程

首先，在导入之前检查几行文件的值(例如：选项表的“NmsTracking_Pointer”和外部帐户表的交付或中部帐户)

要从目标环境数据库(dev)导入配置，请执行以下操作：

1. 打开数据库的管理控制台并清除ID不为0(@id &lt;> 0)的外部帐户（表nms:extAccount）。
1. 在Adobe Campaign控制台中，导入之前通过导入包功能创建的options_dev.xml包。

   检查节点中的选项是否确实已更 **[!UICONTROL Administration > Platform > Options]** 新。

1. 在Adobe Campaign控制台中，导入之前通过导入包功能创建的extaccount_dev.xml

   检查外部数据库是否确实已导入到 **[!UICONTROL Administration > Platform > External accounts]** 。

### 第9步——重新启动所有进程并更改用户（开发） {#step-9---restart-all-processes-and-change-users--dev-}

要启动Adobe Campaign进程，请使用以下命令：

* 在Windows中：

   ```
   net start nlserver6
   ```

* 在Linux中：

   ```
   /etc/init.d/nlserver6 start
   ```

使用以下命令检查进程是否已启动：

```
nlserver pdump
```

更改用户以查找已在开发平台上存在的用户。
