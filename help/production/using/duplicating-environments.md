---
product: campaign
title: 复制环境
description: 复制环境
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 1%

---

# 复制环境{#duplicating-environments}

![](../../assets/v7-only.svg)

## 简介 {#introduction}

### 概述 {#overview}

>[!IMPORTANT]
>
>如果您无权访问服务器和数据库（托管环境），则将无法执行下面描述的过程。 请联系Adobe。

使用Adobe Campaign需要安装和配置一个或多个环境：开发、测试、预生产、生产等。

每个环境都包含一个Adobe Campaign实例，每个Adobe Campaign实例都链接到一个或多个数据库。 应用程序服务器可以执行一个或多个进程：几乎所有这些都可以直接访问实例数据库。

本节详细介绍了应用于复制Adobe Campaign环境（即将源环境恢复到目标环境，从而生成两个相同的工作环境）的流程。

要执行此操作，请应用以下步骤：

1. 在源环境中的所有实例上创建数据库的副本，
1. 在目标环境的所有实例上恢复这些副本，
1. 运行 **nms:freezeInstance.js** 目标环境中的烧灼脚本。

   此过程不会影响服务器及其配置。

   >[!NOTE]
   >
   >在Adobe Campaign, **灼烧** 将允许您停止所有进程与外部交互的操作组合在一起：日志、跟踪、投放、活动工作流等。\
   >此步骤对于避免多次投放消息（一次来自标称环境，一次来自复制环境）非常必要。

   >[!IMPORTANT]
   >
   >一个环境可以包含多个实例。 每个Adobe Campaign实例都需遵守许可证合同。 查看您的许可协议，了解您可以拥有多少个环境。\
   >通过以下过程，您可以传输环境，而不会影响已安装的环境和实例数。

### 开始之前 {#before-you-start}

>[!IMPORTANT]
>
>我们强烈建议在开始传输过程之前，为源环境和目标环境的所有实例运行数据库的完整备份。 这样，如果出现问题，您将能够恢复备份并返回初始配置。

要使此过程正常工作，源环境和目标环境必须具有相同数量的实例、相同的用途（营销实例、交付实例）和类似配置。 技术配置必须符合软件先决条件。 两个环境中必须安装相同的组件。

## 实施 {#implementation}

### 转移过程 {#transfer-procedure}

本节将通过案例研究帮助您了解将源环境传输到目标环境所需的步骤：我们的目标是恢复生产环境(**prod** 实例)到开发环境(**开发** 实例)以在尽可能靠近“live”平台的上下文中工作。

必须非常小心地执行以下步骤：复制源环境数据库时，某些进程可能仍在进行中。 烧灼（下面步骤3）可阻止消息发送两次并保持数据一致性。

>[!IMPORTANT]
>
>* 以下过程在PostgreSQL语言中有效。 如果SQL语言不同(例如Oracle)，则必须修改SQL查询。
>* 以下命令适用于 **prod** 实例和 **开发** 实例。

>


### 步骤1 — 备份源环境（生产）数据 {#step-1---make-a-backup-of-the-source-environment--prod--data}

复制数据库

首先复制所有源环境数据库。 操作取决于数据库引擎，并由数据库管理员负责。

在PostgreSQL下，命令为：

```
pg_dump mydatabase > mydatabase.sql
```

### 步骤2 — 导出目标环境配置（开发） {#step-2---export-the-target-environment-configuration--dev-}

每个环境的大多数配置元素都各不相同：外部帐户（中间源、路由等）、技术选项（平台名称、数据库ID、电子邮件地址和默认URL等）。

在目标数据库上保存源数据库之前，您需要导出目标环境（开发）配置。 为此，请导出以下两个表的内容： **xtkoption** 和 **nmsexaccount**.

通过此导出，您可以保留开发配置，并仅刷新开发数据（工作流、模板、Web应用程序、收件人等）。

为此，请为以下两个元素执行包导出：

* 导出 **xtk:option** 表格到“options_dev.xml”文件中，但不包含具有以下内部名称的记录：“WdbcTimeZone”、“NmsServer_LastPostUpgrade”和“NmsBroadcast_RegexRules”。
* 在“extaccount_dev.xml”文件中，导出 **nms:extAccount** ID不为0(@id &lt;> 0)的所有记录的表。

检查导出的选项/帐户数是否等于每个文件中要导出的行数。

>[!NOTE]
>
>在包导出中要导出的行数为1000行。 如果选项或外部帐户的数量超过1000，则必须执行多次导出。
> 
>有关更多信息，请参见[此章节](../../platform/using/working-with-data-packages.md#exporting-packages)。

>[!NOTE]
>
>导出nmsextaccount表时，与外部帐户相关的密码（例如，中间源、消息中心执行、SMPP、IMS和其他外部帐户的密码）将不会导出。 请确保您提前有权访问正确的密码，因为在将外部帐户导入回环境后，可能需要重新输入这些密码。

### 步骤3 — 停止目标环境（开发） {#step-3---stop-the-target-environment--dev-}

您需要在所有目标环境服务器上停止Adobe Campaign进程。 此操作取决于您的操作系统。

您可以停止所有进程，或只停止写入数据库的进程。

要停止所有进程，请使用以下命令：

* 在Windows中：

   ```
   net stop nlserver6
   ```

* 在Linux中：

   ```
   /etc/init.d/nlserver6 stop
   ```

使用以下命令检查所有进程是否已停止：

```
nlserver pdump
```

>[!NOTE]
>
>在Windows中， **webmdl** 进程仍可以处于活动状态，而不会影响其他操作。

您还可以检查系统进程是否尚未运行。

为此，请使用以下过程：

* 在Windows中：打开 **任务管理器** 并检查 **nlserver.exe** 进程。
* 在Linux中：运行 **ps aux | grep nlserver** 命令并检查 **nlserver** 进程。

### 步骤4 — 在目标环境中恢复数据库（开发） {#step-4---restore-the-databases-in-the-target-environment--dev-}

要在目标环境中恢复源数据库，请使用以下命令：

```
psql mydatabase < mydatabase.sql
```

### 步骤5 — 警告目标环境（开发） {#step-5---cauterize-the-target-environment--dev-}

为避免出现故障，在激活目标环境时，不得自动执行链接到投放发送和工作流执行的进程。

为此，请运行以下命令：

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 步骤6 — 检查烧灼 {#step-6---check-cauterization}

1. 检查唯一的deliverypart是ID设置为0的部分：

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. 检查投放状态更新是否正确：

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. 检查工作流状态更新是否正确：

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### 步骤7 — 重新启动目标环境Web进程（开发） {#step-7---restart-the-target-environment-web-process--dev-}

在目标环境中，重新启动所有服务器的Adobe Campaign进程。

>[!NOTE]
>
>在上重新启动Adobe Campaign之前 **开发** 环境中，您可以应用附加的安全过程：开始 **web** 仅模块。
>  
>为此，请编辑实例的配置文件(**config-dev.xml**)，然后在每个模块（mta、stat等）的autoStart=&quot;true&quot;选项之前添加“_”字符。

运行以下命令以启动Web进程：

```
nlserver start web
```

使用以下命令检查是否只启动了Web进程：

```
nlserver pdump
```

检查对客户端控制台功能的访问。

### 步骤8 — 将选项和外部帐户导入目标环境（开发） {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>在此步骤中只应启动Web进程。 如果情况不同，请在继续之前停止其他正在运行的进程

最重要的是，在导入之前，请检查几行文件的值(例如：选项表的“NmsTracking_Pointer”以及外部帐户表的投放或中间源帐户)

要从目标环境数据库（开发）导入配置，请执行以下操作：

1. 打开数据库的管理控制台并清除ID不为0(@id &lt;> 0)的外部帐户（表nms:extAccount）。
1. 在Adobe Campaign控制台中，导入之前通过导入包功能创建的options_dev.xml包。

   检查 **[!UICONTROL Administration > Platform > Options]** 节点。

1. 在Adobe Campaign控制台中，导入之前通过导入包功能创建的extaccount_dev.xml

   检查外部数据库是否确实已在 **[!UICONTROL Administration > Platform > External accounts]** .

### 步骤9 — 重新启动所有进程并更改用户（开发） {#step-9---restart-all-processes-and-change-users--dev-}

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

更改用户以查找开发平台上已存在的用户。
