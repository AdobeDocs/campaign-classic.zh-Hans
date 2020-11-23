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

每个环境包含一个Adobe Campaign实例，每个Adobe Campaign实例都链接到一个或多个数据库。 应用程序服务器可以执行一个或多个进程：几乎所有这些都可以直接访问实例数据库。

本节详细介绍了应用于重复Adobe Campaign环境的流程，即将源环境恢复到目标环境，从而产生两个相同的工作环境。

为此，请应用以下步骤：

1. 在源环境中，在所有实例上创建数据库的副本，
1. 在目标环境的所有实例中恢复这些副本，
1. 在启动 **** 目标环境前，在上运行nms:freezeInstance.js烧灼脚本。

   此过程不会影响服务器及其配置。

   >[!NOTE]
   >
   >在Adobe Campaign环境中， **烧尾** 会结合使用操作，停止与外部交互的所有进程：日志、跟踪、投放、活动工作流等。\
   >必须执行此步骤，以避免多次传送消息(一次来自标称环境，另一次来自重复环境)。

   >[!IMPORTANT]
   >
   >一个环境可以包含多个实例。 每个Adobe Campaign实例均需遵守许可合同。 检查您的许可协议，了解您可以拥有多少环境。\
   >通过以下过程，您可以传输环境，而不会影响已安装的环境和实例数。

### 开始之前 {#before-you-start}

>[!IMPORTANT]
>
>我们强烈建议在开始传输过程之前，为源目标和环境的所有实例运行数据库的完全备份。 这样，如果出现问题，您将能够恢复备份并返回初始配置。

要使此流程正常工作，源目标和环境必须具有相同数量的实例、相同的用途(营销实例、投放实例)和类似配置。 技术配置必须符合软件先决条件。 必须在两个环境上安装相同的组件。

## 实施 {#implementation}

### 转移过程 {#transfer-procedure}

本节将帮助您了解通过案例研究将源环境传输到目标环境所需的步骤：我们的目标是将生产环境(**prod** instance)恢复为开发环境(**** dev instance)，以在尽可能接近“live”平台的上下文中工作。

必须谨慎执行以下步骤：复制源环境库时，某些进程可能仍在进行中。 烧灼（下面的步骤3）可防止消息发送两次并保持数据一致性。

>[!IMPORTANT]
>
>* 以下过程在PostgreSQL语言中有效。 如果SQL语言不同(例如，Oracle语)，则必须调整SQL查询。
>* 以下命令在prod实例和PostgreSQL下 **的** dev实例 **的上下** 文中应用。

>



### 步骤1 —— 备份源环境(prod)数据 {#step-1---make-a-backup-of-the-source-environment--prod--data}

复制数据库

开始，方法是复制所有源环境数据库。 此操作取决于数据库引擎，并由数据库管理员负责。

在PostgreSQL下，命令为：

```
pg_dump mydatabase > mydatabase.sql
```

### 步骤2 —— 导出目标环境配置(dev) {#step-2---export-the-target-environment-configuration--dev-}

大多数配置元素对于每个环境都是不同的：外部帐户(中间源、路由等)、技术选项（平台名称、数据库ID、电子邮件地址和默认URL等）。

在目标库上保存源数据库之前，您需要导出目标环境(dev)配置。 为此，请导出以下两个表的内容： **xtkoption** 和 **nmsextaccount**。

此导出允许您保留开发配置，并只刷新开发数据(工作流、模板、Web 应用程序、收件人等)。

为此，请对以下两个元素执行包导出：

* 将xtk: **option表导出** 到“options_dev.xml”文件中，但没有以下内部名称的记录：“WdbcTimeZone”、“NmsServer_LastPostUpgrade”和“NmsBroadcast_RegexRules”。
* 在“extaccount_dev.xml”文件中，导出 **ID不为0** (@id &lt;> 0)的所有记录的nms:extAccount表。

检查导出的选项／帐户数是否等于每个文件中要导出的行数。

>[!NOTE]
>
>在包导出中要导出的行数为1000行。 如果选项或外部帐户数超过1000，则必须执行多项出口。
> 
>有关更多信息，请参见[此章节](../../platform/using/working-with-data-packages.md#exporting-packages)。

>[!NOTE]
>
>导出nmsexaccount表时，与外部帐户(例如中间源、消息中心执行、SMPP、IMS和其他外部帐户的口令)相关的口令将不导出。 请确保您提前有权访问正确的密码，因为在将外部帐户导入环境后，可能需要重新输入这些密码。

### 步骤3 —— 停止目标环境(dev) {#step-3---stop-the-target-environment--dev-}

您需要停止所有Adobe Campaign服务器上的目标环境进程。 此操作取决于您的操作系统。

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

使用以下命令检查所有进程是否已停止：

```
nlserver pdump
```

>[!NOTE]
>
>在Windows中，webmdl进 **程仍可** 以处于活动状态，而不会影响其他操作。

您还可以检查系统进程是否仍在运行。

为此，请使用以下流程：

* 在Windows中：打开 **任务** ，检查是否没有 **nlserver.exe** 进程。
* 在Linux中：运行 **ps aux | grep nlserver** 命令并检查没有nlserver **进程** 。

### 第4步——在目标环境中恢复数据库(dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

要在目标环境中恢复源数据库，请使用以下命令：

```
psql mydatabase < mydatabase.sql
```

### 第5步——审核目标环境(dev) {#step-5---cauterize-the-target-environment--dev-}

要避免故障，在激活投放环境时，不能自动执行链接到目标发送和工作流执行的进程。

为此，请运行以下命令：

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 第6步——检查烧灼 {#step-6---check-cauterization}

1. 检查唯一的deliverypart是ID设置为0的部件：

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

### 步骤7 —— 重新启动目标环境Web进程(dev) {#step-7---restart-the-target-environment-web-process--dev-}

在目标环境中，重新开始所有服务器的Adobe Campaign进程。

>[!NOTE]
>
>在开发Adobe Campaign重新启 **动环境** 之前，您可以应用其他安全过程：仅开始 **web** 模块。
>  
>为此，请编辑实例的配置文件&#x200B;**(config-dev.xml**)，然后在每个模块（mta、stat等）的autoStart=&quot;true&quot;选项前添加&quot;_&quot;字符。

运行以下命令以开始Web进程：

```
nlserver start web
```

使用以下命令检查是否只启动了Web进程：

```
nlserver pdump
```

检查客户端控制台的访问功能。

### 第8步——将选项和外部帐户导入目标环境(dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>此步骤应仅启动Web进程。 如果不是这样，请在继续之前停止其他正在运行的进程

最重要的是，在导入之前检查多行文件的值(例如：选项表的“NmsTracking_Pointer”和投放表的中间源帐户)

要从目标环境库(dev)导入配置：

1. 打开数据库的管理控制台并清除ID不为0的外部帐户（表nms:extAccount）(@id &lt;> 0)。
1. 在Adobe Campaign控制台中，导入之前通过导入包功能创建的options_dev.xml包。

   检查节点中的选项是否确实已更 **[!UICONTROL Administration > Platform > Options]** 新。

1. 在Adobe Campaign控制台中，导入之前通过导入包功能创建的extaccount_dev.xml

   检查外部数据库是否确实已导入到 **[!UICONTROL Administration > Platform > External accounts]** 。

### 第9步——重新启动所有进程并更改用户（开发） {#step-9---restart-all-processes-and-change-users--dev-}

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

更改用户以查找已存在于开发平台上的用户。
