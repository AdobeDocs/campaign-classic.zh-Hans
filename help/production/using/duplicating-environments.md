---
product: campaign
title: 复制环境
description: 复制环境
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 2%

---

# 复制环境{#duplicating-environments}



## 简介 {#introduction}

### 概述 {#overview}

>[!IMPORTANT]
>
>如果您无权访问服务器和数据库（托管环境），则将无法执行以下所述的过程。 请联系Adobe。

使用Adobe Campaign需要安装和配置一个或多个环境：开发、测试、预生产、生产等。

每个环境都包含一个Adobe Campaign实例，每个Adobe Campaign实例都链接到一个或多个数据库。 应用程序服务器可以执行一个或多个进程：几乎所有这些进程都可以直接访问实例数据库。

本节详细介绍复制Adobe Campaign环境（即将源环境恢复到目标环境）时要应用的过程，这些过程会导致两个相同的工作环境。

要执行此操作，请应用以下步骤：

1. 在源环境中的所有实例上创建数据库副本，
1. 在目标环境的所有实例上恢复这些副本，
1. 运行 **nms：freezeInstance.js** 启动前对目标环境编写的烧灼脚本。

   此过程不会影响服务器及其配置。

   >[!NOTE]
   >
   >在Adobe Campaign的环境中， **烧灼化** 可让您停止与外界交互的所有进程的组合操作：日志、跟踪、投放、活动工作流等。\
   >此步骤对于避免多次发送消息（一次来自名义环境，一次来自重复环境）是必需的。

   >[!IMPORTANT]
   >
   >一个环境可以包含多个实例。 每个Adobe Campaign实例都受许可合同的约束。 检查您的许可协议，了解可以拥有的环境数量。\
   >通过下面的过程，您可以在不影响已安装的环境和实例数的情况下传输环境。

### 开始之前 {#before-you-start}

>[!IMPORTANT]
>
>我们强烈建议在开始传输过程之前，对源环境和目标环境的所有实例运行数据库的完整备份。 这样，如果发生问题，您将能够恢复备份并返回到初始配置。

为了使此过程正常工作，源环境和目标环境必须具有相同的实例数、相同的用途（营销实例、投放实例）和类似的配置。 技术配置必须符合软件先决条件。 必须在两个环境中安装相同的组件。

## 实现 {#implementation}

### 传输过程 {#transfer-procedure}

本节将帮助您了解通过案例研究将源环境转移到目标环境所需的步骤：我们的目标是恢复生产环境(**prod** 实例)到开发环境(**开发** 实例)，以便在尽可能接近“实时”平台的上下文中工作。

必须谨慎地执行以下步骤：在复制源环境数据库时，某些进程可能仍在进行中。 烧灼操作（下面的步骤3）可防止发送两次消息，并保持数据一致性。

>[!IMPORTANT]
>
>* 以下过程在PostgreSQL语言中有效。 如果SQL语言不同(例如Oracle)，则必须调整SQL查询。
>* 以下命令适用于的上下文 **prod** 实例和 **开发** Postgresql下的实例。
>

### 步骤1 — 备份源环境(prod)数据 {#step-1---make-a-backup-of-the-source-environment--prod--data}

复制数据库

首先复制所有源环境数据库。 该操作依赖于数据库引擎，是数据库管理员的责任。

在PostgreSQL下，命令为：

```
pg_dump mydatabase > mydatabase.sql
```

### 步骤2 — 导出目标环境配置(dev) {#step-2---export-the-target-environment-configuration--dev-}

每个环境的大多数配置元素各不相同：外部帐户（中间源、路由等）、技术选项（平台名称、数据库ID、电子邮件地址和默认URL等）。

在将源数据库保存到目标数据库之前，需要导出目标环境(dev)配置。 为此，请导出这两个表的内容： **xtkoption** 和 **nmsextaccount**.

通过此导出，您可以保留开发配置并仅刷新开发数据（工作流、模板、Web应用程序、收件人等）。

为此，请为以下两个元素执行资源包导出：

* 导出 **xtk：option** 表到“options_dev.xml”文件中，不包含具有以下内部名称的记录：“WdbcTimeZone”、“NmsServer_LastPostUpgrade”和“NmsBroadcast_RegexRules”。
* 在&#39;extaccount_dev.xml&#39;文件中，导出 **nms：extAccount** 表，用于所有ID不为0 (@id &lt;> 0)的记录。

检查导出的选项/帐户数是否等于每个文件中要导出的行数。

>[!NOTE]
>
>资源包导出中要导出的行数为1000行。 如果选项数或外部帐户数超过1000，则必须执行多次导出。
> 
>有关更多信息，请参见[此章节](../../platform/using/working-with-data-packages.md#exporting-packages)。

>[!NOTE]
>
>导出nmsextaccount表时，与外部帐户相关的密码（例如中间源、消息中心执行、SMPP、IMS和其他外部帐户的密码）不会导出。 请确保您提前能够访问正确的密码，因为在外部帐户导入回环境后，可能需要重新输入这些密码。

### 步骤3 — 停止目标环境（开发） {#step-3---stop-the-target-environment--dev-}

您需要停止所有目标环境服务器上的Adobe Campaign进程。 此操作取决于您的操作系统。

您可以停止所有进程，或仅停止写入数据库的进程。

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
>在Windows中 **webmdl** 进程仍可以处于活动状态，而不会影响其他操作。

您还可以检查是否没有系统进程仍在运行。

为此，请使用以下流程：

* 在Windows中：打开 **任务管理器** 检查是否没有 **nlserver.exe** 进程。
* 在Linux中：运行 **ps aux | grep nlserver** 命令，并检查是否存在 **nlserver** 进程。

### 步骤4 — 恢复目标环境中的数据库（开发） {#step-4---restore-the-databases-in-the-target-environment--dev-}

要在目标环境中恢复源数据库，请使用以下命令：

```
psql mydatabase < mydatabase.sql
```

### 步骤5 — 烧灼目标环境（开发） {#step-5---cauterize-the-target-environment--dev-}

为避免发生故障，在激活目标环境时，不得自动执行链接到投放发送和工作流执行的流程。

为此，请运行以下命令：

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 步骤6 — 检查烧灼化 {#step-6---check-cauterization}

1. 检查唯一的deliverypart是否是ID设置为0的部分：

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

在目标环境中，为所有服务器重新启动Adobe Campaign进程。

>[!NOTE]
>
>在上重新启动Adobe Campaign之前 **开发** 环境，您可以应用附加安全过程：启动 **Web** 仅限模块。
>  
>为此，请编辑实例的配置文件(**config-dev.xml**)，然后为每个模块（mta、stat等）在autoStart=&quot;true&quot;选项之前添加&quot;_&quot;字符。

运行以下命令以启动Web进程：

```
nlserver start web
```

使用以下命令检查是否仅启动了Web进程：

```
nlserver pdump
```

检查对客户端控制台的访问权限功能。

### 步骤8 — 将选项和外部帐户导入目标环境（开发） {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>在此步骤中只应启动Web进程。 如果不是这种情况，请先停止其他正在运行的进程，然后再继续

首先，在导入之前检查几行文件的值（例如：选项表的“NmsTracking_Pointer”和外部帐户表的投放或中间源帐户）

要从目标环境数据库(dev)导入配置，请执行以下操作：

1. 打开数据库的Admin Console并清除ID不是0 (@id &lt;> 0)的外部帐户（表nms：extAccount）。
1. 在Adobe Campaign控制台中，导入之前通过导入包功能创建的options_dev.xml包。

   检查中的选项是否确实已更新 **[!UICONTROL Administration > Platform > Options]** 节点。

1. 在Adobe Campaign控制台中，导入之前通过导入资源包功能创建的extaccount_dev.xml

   检查外部数据库是否确实已导入 **[!UICONTROL Administration > Platform > External accounts]** .

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
