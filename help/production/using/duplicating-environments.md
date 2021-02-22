---
solution: Campaign Classic
product: campaign
title: 复制环境
description: 复制环境
audience: production
content-type: reference
topic-tags: data-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 1%

---


# 复制环境{#duplicating-environments}

## 简介 {#introduction}

### 概述 {#overview}

>[!IMPORTANT]
>
>如果您无权访问服务器和数据库(托管环境)，您将无法执行下面描述的过程。 请联系Adobe。

使用Adobe Campaign需要安装和配置一个或多个环境:开发、测试、预制、生产等。

每个环境都包含一个Adobe Campaign实例，每个Adobe Campaign实例都链接到一个或多个数据库。 应用程序服务器可以执行一个或多个进程：几乎所有这些都可以直接访问实例数据库。

本节详细介绍了要应用于重复Adobe Campaign环境的过程，即将源环境恢复到目标环境，从而产生两个相同的工作环境。

为此，请应用以下步骤：

1. 在源环境的所有实例上创建数据库的副本，
1. 在目标环境的所有实例中恢复这些副本，
1. 在启动目标环境之前，在Adobe Player上运行&#x200B;**nms:freezeInstance.js**&#x200B;烧灼脚本。

   此过程不会影响服务器及其配置。

   >[!NOTE]
   >
   >在Adobe Campaign的上下文中， **烧灼**&#x200B;组合了允许您停止所有进程与外部交互的操作：日志、跟踪、投放、活动工作流等\
   >必须执行此步骤，以避免多次(一次来自标称环境，一次来自复制环境)传送消息。

   >[!IMPORTANT]
   >
   >一个环境可以包含多个实例。 每个Adobe Campaign实例都受许可合同的约束。 查看您的许可协议，了解您可以拥有多少环境。\
   >通过以下过程，可以传输环境，而不会影响已安装的环境和实例数。

### 开始之前{#before-you-start}

>[!IMPORTANT]
>
>我们强烈建议在开始传输过程之前，为源环境和目标数据的所有实例运行数据库的完整备份。 这样，如果出现问题，您就可以恢复备份并返回初始配置。

要使此流程正常工作，源和目标环境必须具有相同数量的实例、相同的用途(营销实例、投放实例)和类似配置。 技术配置必须符合软件先决条件。 必须在两个环境上安装相同的组件。

## 实现{#implementation}

### 传输过程{#transfer-procedure}

本节将帮助您了解通过案例研究将源环境传输到目标环境所需的步骤：我们的目的是将生产环境（**prod**&#x200B;实例）恢复为开发环境（**dev**&#x200B;实例），以便在尽可能靠近“live”平台的上下文中工作。

必须谨慎执行以下步骤：复制源环境数据库时，某些进程可能仍在进行中。 烧灼（下面第3步）可防止两次发送消息并保持数据一致性。

>[!IMPORTANT]
>
>* 以下过程在PostgreSQL语言中有效。 如果SQL语言不同(例如Oracle)，则必须调整SQL查询。
>* 以下命令在&#x200B;**prod**&#x200B;实例和PostgreSQL下的&#x200B;**dev**&#x200B;实例的上下文中应用。
>



### 步骤1 — 备份源环境(prod)数据{#step-1---make-a-backup-of-the-source-environment--prod--data}

复制数据库

开始，方法是复制所有源环境数据库。 该操作取决于数据库引擎，并由数据库管理员负责。

在PostgreSQL下，命令为：

```
pg_dump mydatabase > mydatabase.sql
```

### 步骤2 — 导出目标环境配置(dev){#step-2---export-the-target-environment-configuration--dev-}

大多数配置元素对于每个环境都不同：外部帐户(中间源、路由等)、技术选项（平台名称、DatabaseId、电子邮件地址和默认URL等）。

在将源环境库保存到目标数据库之前，您需要导出目标(dev)配置。 为此，请导出以下两个表的内容：**xtkoption**&#x200B;和&#x200B;**nmsextaccount**。

此导出允许您保留开发配置，并仅刷新开发数据(工作流、模板、Web 应用程序、收件人等)。

为此，请对以下两个元素执行包导出：

* 将&#x200B;**xtk:option**&#x200B;表导出到“options_dev.xml”文件中，但没有以下内部名称的记录：“WdbcTimeZone”、“NmsServer_LastPostUpgrade”和“NmsBroadcast_RegexRules”。
* 在“extaccount_dev.xml”文件中，导出ID不为0(@id &lt;> 0)的所有记录的&#x200B;**nms:extAccount**&#x200B;表。

检查导出的选项/帐户数是否等于每个文件中要导出的行数。

>[!NOTE]
>
>在包导出中要导出的行数为1000行。 如果选项或外部帐户的数量超过1000，则必须执行多项导出。
> 
>有关更多信息，请参见[此章节](../../platform/using/working-with-data-packages.md#exporting-packages)。

>[!NOTE]
>
>导出nmsexaccount表时，与外部帐户(例如，中间源、消息中心执行、SMPP、IMS和其他外部帐户的口令)相关的口令不会导出。 请确保您提前获得正确的密码，因为在将外部帐户导入环境后，可能需要重新输入这些密码。

### 步骤3 — 停止目标环境(dev){#step-3---stop-the-target-environment--dev-}

您需要停止所有Adobe Campaign环境服务器上的目标进程。 此操作取决于您的操作系统。

可以停止所有进程，或只停止那些写入数据库的进程。

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
>在Windows中，**webmdl**&#x200B;进程仍可处于活动状态，而不会影响其他操作。

您还可以检查是否没有系统进程仍在运行。

要执行此操作，请使用以下过程：

* 在Windows中：打开&#x200B;**任务管理器**&#x200B;并检查是否没有&#x200B;**nlserver.exe**&#x200B;进程。
* 在Linux中：运行&#x200B;**ps aux | grep nlserver**&#x200B;命令并检查是否没有&#x200B;**nlserver**&#x200B;进程。

### 步骤4 — 在目标环境(dev)中恢复数据库{#step-4---restore-the-databases-in-the-target-environment--dev-}

要在目标环境中恢复源数据库，请使用以下命令：

```
psql mydatabase < mydatabase.sql
```

### 步骤5 — 警告目标环境(dev){#step-5---cauterize-the-target-environment--dev-}

要避免故障，在激活投放环境时，不能自动执行链接到目标发送和工作流执行的进程。

为此，请运行以下命令：

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 步骤6 — 检查烧灼{#step-6---check-cauterization}

1. 请检查唯一的deliverypart是ID设置为0的部件：

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

### 步骤7 — 重新启动目标 环境 Web进程(dev){#step-7---restart-the-target-environment-web-process--dev-}

在目标环境上，重新开始所有服务器的Adobe Campaign进程。

>[!NOTE]
>
>在&#x200B;**dev** Adobe Campaign重新启动环境之前，您可以应用其他安全过程：仅开始&#x200B;**web**&#x200B;模块。
>  
>为此，请编辑实例的配置文件(**config-dev.xml**)，然后在每个模块（mta、stat等）的autoStart=&quot;true&quot;选项前添加&quot;_&quot;字符。

运行以下命令以开始Web进程：

```
nlserver start web
```

使用以下命令检查是否只启动了Web进程：

```
nlserver pdump
```

检查客户端控制台的访问功能。

### 步骤8 — 将选项和外部帐户导入目标环境(dev){#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>此步骤应仅启动Web进程。 如果不是这样，请在继续之前停止其他正在运行的进程

最重要的是，在导入前检查几行文件的值(例如：选项表的“NmsTracking_Pointer”和投放表的中间源帐户)

要从目标环境数据库(dev)导入配置：

1. 打开数据库的管理控制台，并清除ID不为0(@id &lt;> 0)的外部帐户（表nms:extAccount）。
1. 在Adobe Campaign控制台中，导入之前通过导入包功能创建的options_dev.xml包。

   检查&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;节点中的选项是否确实已更新。

1. 在Adobe Campaign控制台中，导入之前通过导入包功能创建的extaccount_dev.xml

   检查是否确实已在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中导入了外部数据库。

### 步骤9 — 重新启动所有进程并更改用户(dev){#step-9---restart-all-processes-and-change-users--dev-}

要开始Adobe Campaign进程，请使用以下命令：

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
