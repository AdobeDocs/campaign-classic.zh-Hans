---
product: campaign
title: 内部版本升级入门
description: 了解升级到新内部版本的关键步骤
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2353'
ht-degree: 3%

---

# 执行内部版本升级{#performing-a-build-upgrade}

![](../../assets/v7-only.svg)

本节将为您提供有关升级过程以及识别和解决冲突的步骤的深入演练。

建设升级必须谨慎进行，其影响必须事先充分考虑，程序必须严守纪律。 要确保成功升级，请确保只有专家用户才能执行下面列出的步骤。 此外，我们强烈建议您联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 开始任何升级之前。

需要满足以下先决条件：

* 了解营销活动架构
* 系统和服务器端知识
* 管理权限

您可以在以下部分中找到更多信息： [更新Adobe Campaign](../../production/using/upgrading.md), [迁移到新版本](../../migration/using/about-migration.md).

对于托管实例和混合实例，您必须向Adobe技术运营团队请求内部版本升级。 有关更多信息，请参阅本页底部的常见问题解答部分。 另请查阅 [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md).

## 准备升级

![](assets/do-not-localize/icon_planification.png)

在开始内部版本升级之前，必须执行如下所述的完整准备。
系统准备好升级后，将需要升级内部版本 **至少** 2小时。

内部版本升级过程需要以下资源：

* Adobe架构师 — 了解数据库结构（即装即用模式和任何已添加的其他模式、营销活动设计以及必须按特定顺序启动和测试的任何关键路径功能）。
* 项目经理 — 如果内部版本升级涉及许多不同的实例（生产、暂存、测试）和其他第三方服务器和应用程序（数据库、SFTP站点、消息服务提供商），则有项目经理来协调所有测试被视为最佳做法。
* Adobe Campaign管理员 — 您的管理员知道服务器的配置，包括但不限于：安全性、文件夹布局、报告和导入\导出要求。 如果没有管理员，请勿执行内部版本升级。
* Adobe Campaign运营商（营销用户） — 成功升级取决于用户成功执行其日常任务的能力。 因此，在测试已升级的服务器时，应始终至少包含一位每日操作员。

### 规划

以下是有关如何规划内部版本升级的要点：

1. 至少保留2小时进行升级。
1. 为Adobe和客户员工分发联系详细信息。
1. 对于托管实例：Adobe和客户人员将协调升级的时间以及执行人员。
1. 对于内部部署实例：客户员工负责管理整个流程 — 如果需要协助测试自定义工作流和交付逻辑，则应引入咨询服务。
1. 确定并确认要升级到的Adobe Campaign版本 — 请查阅 [Adobe Campaign Classic发行说明](../../rn/using/rn-overview.md).
1. 确认拥有升级可执行文件。

### 关键人员

内部版本升级过程需要以下人员参与：

* Adobe架构师：对于托管或混合架构，架构师必须与Adobe Campaign客户关怀团队进行协调。

* 项目经理：
   * 对于On Premise安装：客户的内部项目领导者负责领导升级并管理生命周期测试。

   * 对于托管安装：托管团队将与Adobe Campaign客户关怀团队和客户合作，协调所有实例的升级时间轴。

* Adobe Campaign管理员：
   * 对于On Premise安装：管理员将执行升级。

   * 对于托管安装：托管团队会执行升级。

* Adobe Campaign操作员\营销用户：操作员对开发、测试和生产实例运行测试。

### 准备内部版本升级

在开始内部版本升级之前，内部部署客户需要执行以下准备：

1. 确保在升级之前可以导出任何开发工作，导出为资源包。

1. 为源环境和目标环境的所有实例执行数据库的完全备份。

1. 获取 [服务器配置文件](../../installation/using/the-server-configuration-file.md).

1. [下载最新内部版本](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html). [了解详情](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hans)。

你还需要知道 [有用命令行](../../installation/using/command-lines.md) 开始内部版本升级之前：

* **nlserver pdump**:列出运行进程
* **nlserver pdump -who**:列出活动客户端会话
* **nlserver监视器 — 缺少**:列出缺少的属性
* **nlserver开始process@instanceName**:启动进程
* **nlserver停止process@instanceName**:停止进程
* **nlserver重新启动process@instanceName**:重新启动进程
* **nlserver关闭**:停止所有Campaign进程
* **nlserver watckdog -svc**:启动监视程序（仅限UNIX）

## 执行升级

![](assets/do-not-localize/icon_process.png)

以下程序仅由 **内部部署** 客户。 对于托管客户，托管团队会负责处理。 要将Adobe Campaign更新为新内部版本，请参阅下面的详细过程。

### 复制环境

以下是复制Adobe Campaign环境的方式，以便将源环境恢复到目标环境，从而生成两个相同的工作环境。

为此请执行以下操作步骤：

1. 在源环境中的所有实例上创建数据库的副本。

1. 在目标环境的所有实例上恢复这些副本。

1. 运行 **nms:freezeInstance.js** 目标环境中的烧灼脚本。 这将阻止所有进程与外部交互：日志、跟踪、投放、活动工作流等。

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. 检查烧灼，如下所示：

   * 检查唯一的投放部分是ID设置为 **0**:

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

   * 检查投放状态更新是否正确：

      ```
      SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
      ```

   * 检查工作流状态更新是否正确：

      ```
      SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
      SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
      ```

### 关闭服务

要使用新版本替换所有文件，需要关闭nlserverservice的所有实例。

1. 关闭以下服务：

   * Web服务(IIS): **iisreset /stop**
   * Adobe Campaign服务： **net stop nlserver6**

   >[!NOTE]
   >
   >确保已停止重定向服务器(webmdl)，以便IIS使用的nlsrvmod.dll文件可以替换为新版本。

1. 通过运行 **nlserver pdump** 命令。 如果没有任务，则输出应类似于以下内容：

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. 检查Windows任务管理器，确认所有进程都已停止。

### 升级Adobe Campaign Server应用程序

1. 运行 **Setup.exe** 文件。 如果需要下载此文件，请访问 [下载中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html).

1. 选择安装模式： **更新** 或 **修复**.

1. 单击 **下一个**.

1. 单击 **完成**:安装程序会复制新文件。

1. 操作完成后，单击 **完成**.

### 同步资源

1. 打开命令行。

1. 运行 **nlserver config -postupgrade -allinstances** 要执行以下操作：

   * 同步资源
   * 更新架构
   * 更新数据库

   >[!NOTE]
   >
   >此操作只应在nlserverweb应用程序服务器上执行一次且只能执行一次。

   要仅同步一个数据库，请运行以下命令：

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. 检查同步是否生成了任何错误或警告。

### 重新启动服务

需要重新启动以下服务：

* Web服务(IIS): **issreset /start**
* Adobe Campaign服务： **网络启动nlserver6**

### 客户端控制台更新

客户端控制台必须与服务器实例位于同一内部版本。

在安装Adobe Campaign应用程序服务器的计算机上(nlserverweb)，下载并复制文件：

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

下次连接客户端控制台时，窗口会告知用户新更新的可用性，并为用户提供下载和安装该更新的可能性。

### 特定的其他任务

某些配置需要特定的其他任务才能更新到新内部版本。

#### 事务性消息传递

在Campaign实例上启用事务性消息传递（消息中心）后，您需要执行以下其他步骤才能升级：

1. 将消息中心生产服务器更新为所选版本。
1. 运行升级后的脚本。
1. 运行测试并确保通过消息中心生产实例成功接收电子邮件。
1. 升级客户端并清除缓存。
1. 导出包：
   * 使用客户端包导出工具导出包
   * 导入架构包
   * 断开和重新连接客户端
   * 更新数据库
   * 断开连接并重新连接
   * 导入管理包
   * 导入内容包
   * 导入内容管理包
   * 断开连接并重新连接
   * 对工作流执行快速健全检查

1. 发布消息中心模板，以确保服务器和消息中心实例之间的接口正常工作。
1. 运行测试以确保通过消息中心生产实例成功接收电子邮件。
1. 在生产中运行工作流测试，以确保收到投放。

#### 中间源

在中间源环境的上下文中，您需要执行以下其他步骤才能升级：

1. 联系人 [Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 协调中间源服务器的升级。
1. 通过运行测试链接验证版本是否已更新。 例如：

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>中间源服务器必须始终运行与营销服务器相同（或更新）的版本。

## 在发生冲突时

### 识别冲突

您需要检查同步结果。 此过程仅由内部部署客户执行。 对于托管客户，托管团队会负责处理。 有两种方法可查看同步结果：

在命令行界面中，错误由三个V形标记“>>”实现，并自动停止同步。 警告由双V形标记“>>”实现，并且必须在同步完成后进行解析。 在升级后，命令提示符中会显示一个摘要。 它可以如下所示：

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

如果警告涉及资源冲突，则需要用户注意才能解决该问题。

的 **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** 文件包含同步结果。 默认情况下，该插件可在以下目录中使用： **installationDirectory/var/instanceName/postupgrade**. 错误和警告属性会指示错误和警告。

### 分析冲突

**如何发现冲突？**

冲突可在相关服务器的postupgrade.log中或Campaign客户端界面（管理>配置>包管理>编辑冲突）中找到。

标识符为“stockOverview”且类型为“nms:webApp”的文档与新版本冲突。

如果发现冲突，请检查以下条件是否匹配：

* 客户是否修改或自定义了对象？
* 对象在产品中是否发生更改？

如果这两种条件都不适用，则为误报。 如果这两种条件都适用，则发现了真正的冲突。

**客户是否修改了对象？**

1. 识别冲突的对象。
1. 询问客户是否修改了对象。
1. 这个物体有什么不寻常的吗？
1. 对象代码中是否设置了上次修改日期？
1. 检查冲突中“_conflict”属性的XML代码。 它看起来像个自定义吗？

**对象是否已在新内部版本中更改？**

1. 有“常见的疑犯？” 内置Web应用程序或报表(例如：“deliveryValidation”、“deliveryOverview”、“budget”)。
1. 检查更改日志以获取任何更新。
1. 问Adobe Campaign专家。
1. 对代码执行“diff”。

### 解决冲突

要解决冲突，请应用以下流程：

1. 在Adobe Campaign资源管理器中，转到 **管理>配置>包管理>编辑冲突**.

1. 在列表中选择要解决的冲突。
有三种解决冲突的选项： **接受新版本**, **保留当前版本**, **合并代码（并声明为已解析）**, **忽略冲突（不建议）**.

**我何时可以接受新版本？**

* 如果您需要标准功能。
* 如果您没有自定义（所有自定义项都将被删除）

**我何时可以保留当前版本？**

* 如果您有自定义设置
* 如果您不想合并
* 如果升级中不需要对冲突对象进行任何修复

**何时执行合并？**

* 只能合并表单、报表和Web应用程序。
* 某些次要合并可以在不了解代码的情况下进行解析。
* 更复杂的合并应由拥有适当技能和能力的人进行。
* 请参阅 [执行合并](#perform-a-merge).

**如果我忽视冲突呢？**

* 冲突将继续存在
* 不会升级对象
* 长期影响：版本不兼容，客户将不会从错误修复中受益。

>[!IMPORTANT]
>强烈建议解决冲突。

### 执行合并{#perform-a-merge}

合并的类型不同：

1. 轻松合并：自定义元素和新元素很小且不相关，无需编码。
1. 无更改：接受新版本，仅更改上次更新日期，仅更改注释、制表符、空格或新行。 示例：意外保存。
1. 琐碎的更改：只更改了一行。 示例：xpathToLoad
1. 复杂合并：需要编码时。 需要发展技能。 请参阅 [复杂合并](#complex-merges).

#### 如何合并？

1. 获取所有三个版本：原始版本、新版本和自定义版本。
1. 在原始版本和新版本之间运行“差异”。
1. 隔离更改。
1. 如果没有更改，请通过保留当前版本来解决。

#### 在哪里找代码？

1. 内置代码存储在Datakit文件夹的XML文件中。 查找与冲突对象匹配的XML文件。 示例：installationDirectory\datakit\nms\fra\form\recipient.xml
1. 检索原始版本：通过 [下载中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 或另一个未升级的产品安装。
1. 检索新版本：通过 [下载中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 或客户安装的文件。
1. 检索自定义版本：从Campaign客户端中检索对象的源代码。

### 如何进行差异比较？

1. 安装文本或合并编辑器，例如记事本++、AraxisMerge、WinMerge。
1. 在编辑器中打开原始文件和新文件。
1. 运行差异比较（比较两个文件）。
1. 识别任何差异。

### 如何合并？

1. 从自定义版本开始。
1. 应用更改。
1. 通过将冲突声明为已解决来解决冲突。
1. 检查非回归。

如果选择手动解决冲突，请按如下方式继续：

1. 在窗口的下部，搜索 **_conflict_string_** 查找存在冲突的实体。 随新版本安装的实体包含新参数，与先前版本匹配的实体包含自定义参数。
1. 删除您不希望保留的版本。 删除 **_conflict_argument_** 要保留的实体的字符串。
1. 转到已解决的冲突。 单击 **操作** 图标，选择 **声明为已解析**.
1. 保存更改：冲突现已解决。

#### 复杂合并{#complex-merges}

1. 了解更改的功能：对更改进行逆向工程，检查更改日志，跟踪Adobe Campaign专家。
1. 决定该怎么做。
1. 了解自定义的功能：反向工程更改

以下是执行复杂合并的步骤：

1. 从更改集复制代码位
1. 粘贴到自定义版本
1. 定制的非回归测试
1. 测试更改的功能
1. 执行用户接受测试
1. 在测试环境中执行


>[!IMPORTANT]
>执行复杂合并需要具备开发技能。

**相关主题**

* [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic发行说明](../../rn/using/rn-overview.md)
* [帮助和支持选项以进行Campaign Classic](../../support.md)
* [[!DNL Gold Standard] 项目](../../rn/using/gs-overview.md)
