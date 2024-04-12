---
product: campaign
title: 内部版本升级入门
description: 了解升级到新内部版本的关键步骤
feature: Monitoring, Upgrade
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 1%

---

# 执行内部版本升级{#performing-a-build-upgrade}



本节将深入介绍升级过程以及识别和解决冲突的步骤。

版本升级必须谨慎进行，必须事先充分考虑其影响，并且必须在完成升级程序时遵守高度的纪律。 要确保升级成功，请确保只有专家用户才能执行下面列出的步骤。 此外，我们强烈建议联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 在开始任何升级之前。

需要以下先决条件：

* 了解Campaign架构
* 系统和服务器端知识
* 管理权限

您可在以下部分找到更多信息： [更新Adobe Campaign](../../production/using/upgrading.md)， [迁移到新版本](../../migration/using/about-migration.md).

对于托管实例和混合实例，您必须向Adobe技术运营团队请求版本升级。 有关更多信息，请参阅底部的“常见问题解答”部分（如果此页面）。 另请参阅 [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md).

## 准备升级

![](assets/do-not-localize/icon_planification.png)

在开始内部版本升级之前，必须按照以下所述执行完整准备。
一旦系统准备好进行升级，就需要内部版本升级 **至少** 2小时。

内部版本升级过程需要以下资源：

* Adobe架构师 — 了解数据库结构（现成的架构和已添加的任何其他架构、活动设计以及必须按特定顺序启动和测试的任何关键路径功能）。
* 项目经理 — 如果版本升级涉及许多不同的实例（生产、暂存、测试）和其他第三方服务器和应用程序（数据库、SFTP站点、消息服务提供商），则由项目经理协调所有测试被视为最佳实践。
* Adobe Campaign管理员 — 您的管理员知道服务器的配置，包括但不限于：安全性、文件夹布局、报表以及导入\导出要求。 如果没有管理员，请不要执行内部版本升级。
* Adobe Campaign操作员（营销用户） — 成功升级取决于用户成功执行其日常任务的能力。 因此，在升级服务器的测试中应始终至少包含一个每日操作员。

### 规划

以下是如何规划内部版本升级的关键点：

1. 至少保留2个小时进行升级。
1. 为Adobe和客户员工分发联系人详细信息。
1. 对于托管实例：Adobe和客户员工将协调升级时间和执行人员。
1. 对于内部部署实例：客户员工管理整个流程 — 如果需要测试自定义工作流和交付逻辑方面的帮助，则应引入咨询服务。
1. 确定并确认要升级到哪个Adobe Campaign版本 — 请参阅 [Adobe Campaign Classic发行说明](../../rn/using/rn-overview.md).
1. 确认拥有升级可执行文件。

### 关键人员

内部版本升级过程需要以下人员参与：

* Adobe架构师：对于托管或混合架构，架构师必须与Adobe Campaign客户关怀团队进行协调。

* 项目经理：
   * 对于内部部署：客户的内部项目负责人负责升级并管理生命周期测试。

   * 对于托管安装：托管团队将与Adobe Campaign客户关怀团队和客户合作，协调所有实例的升级时间线。

* Adobe Campaign管理员：
   * 对于内部部署：管理员执行升级。

   * 对于托管安装：由托管团队执行升级。

* Adobe Campaign operator\marketing user：此运算符针对开发、测试和生产实例运行测试。

### 准备内部版本升级

在开始内部版本升级之前，内部部署客户需要执行以下准备工作：

1. 确保在升级之前可以导出任何开发工作，并导出为包。

1. 对源环境和目标环境的所有实例执行数据库的完整备份。

1. 获取最新版本的 [服务器配置文件](../../installation/using/the-server-configuration-file.md).

1. [下载最新的内部版本](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html). [了解详情](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hans)。

您还需要了解所有 [有用的命令行](../../installation/using/command-lines.md) 在开始内部版本升级之前：

* **nlserver pdump**：列出正在运行的进程
* **nlserver pdump -who**：列出活动的客户端会话
* **nlserver监视器 — missing**：列出缺少的属性
* **nlserver start process@instance-name**：启动进程
* **nlserver stop process@instance-name**：停止进程
* **nlserver重新启动process@instance-name**：重新启动进程
* **nlserver shutdown**：停止所有营销活动进程
* **nlserver监视程序 — svc**：启动监视程序（仅限UNIX）

## 执行升级

![](assets/do-not-localize/icon_process.png)

以下过程仅由执行 **内部部署** 客户。 对于托管客户，由托管团队负责。 要将Adobe Campaign更新到新的内部版本，请详述以下过程。

### 复制环境

下面是如何复制Adobe Campaign环境的，以便将源环境恢复到目标环境，从而生成两个相同的工作环境。

为此请执行以下操作步骤：

1. 在源环境中的所有实例上创建数据库的副本。

1. 在目标环境的所有实例上恢复这些副本。

1. 运行 **nms：freezeInstance.js** 启动前对目标环境编写的烧灼脚本。 这将停止与外界交互的所有进程：日志、跟踪、投放、活动工作流等。

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. 检查烧灼情况，如下所示：

   * 检查是否唯一将ID设置为的投放部分 **0**：

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

   * Web服务(IIS)： **iisreset /stop**
   * Adobe Campaign服务： **网络停止nlserver6**

   >[!NOTE]
   >
   >请确保重定向服务器(webmdl)已停止，以便能够将IIS使用的nlsrvmod.dll文件替换为新版本。
   >

1. 通过运行 **nlserver pdump** 命令。 如果没有任务，则输出应类似于以下内容：

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. 检查Windows任务管理器，确认所有进程都已停止。

### 升级Adobe Campaign Server应用程序

1. 运行 **Setup.exe** 文件。 如果您需要下载此文件，请访问 [下载中心](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html).

1. 选择安装模式： **更新** 或 **修复**.

1. 单击 **下一个**.

1. 单击 **完成**：安装程序复制新文件。

1. 操作完成后，单击 **完成**.

### 同步资源

1. 打开命令行。

1. 运行 **nlserver配置 — postupgrade -allinstances** 要执行以下操作，请执行以下操作：

   * 同步资源
   * 更新架构
   * 更新数据库

   >[!NOTE]
   >
   >此操作只应在nlserverweb应用程序服务器上执行一次。
   >

   要仅同步一个数据库，请运行以下命令：

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. 检查同步是否已生成任何错误或警告。

### 重新启动服务

需要重新启动以下服务：

* Web服务(IIS)： **issreset /start**
* Adobe Campaign服务： **网络启动nlserver6**

### 客户端控制台更新

客户端控制台必须与服务器实例位于同一内部版本上。

在安装了Adobe Campaign应用程序服务器的计算机(nlserverweb)上，下载并复制文件：

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

下次连接客户端控制台时，将显示一个窗口，通知用户有新的更新可用，并为用户提供下载和安装更新的可能性。

### 其他特定任务

某些配置需要特定的其他任务才能更新到新内部版本。

#### 事务性消息传递

在Campaign实例上启用事务性消息传递（消息中心）后，您需要执行以下附加步骤以进行升级：

1. 将消息中心生产服务器更新至所选版本。
1. 运行升级后脚本。
1. 运行测试并确保通过消息中心生产实例成功接收电子邮件。
1. 升级客户端并清除缓存。
1. 导出资源包：
   * 使用客户端包导出工具导出包
   * 导入架构包
   * 断开并重新连接客户端
   * 更新数据库
   * 断开并重新连接
   * 导入管理包
   * 导入内容包
   * 导入内容管理包
   * 断开并重新连接
   * 对工作流执行快速健康检查

1. 发布消息中心模板，以确保服务器与消息中心实例之间的接口正常工作。
1. 运行测试以确保通过消息中心生产实例成功接收电子邮件。
1. 在生产环境中运行工作流测试以确保接收投放。

#### 中间源

在中间源环境的上下文中，您需要执行以下附加步骤以进行升级：

1. 联系人 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 协调中间源服务器的升级。
1. 通过运行测试链接来验证版本是否已更新。 例如：

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>中间源服务器必须始终运行与营销服务器相同的版本（或更高版本）。
>

## 发生冲突时

### 识别冲突

您需要检查同步结果。 此过程仅由内部部署客户执行。 对于托管客户，由托管团队负责。 查看同步结果的方法有两种：

在命令行界面中，错误通过三个V形“>>>”实现，同步自动停止。 警告以双V形“>>”具体化，同步完成后必须解决这些警告。 升级后结束时，命令提示符中会显示摘要。 它看上去可能如下所示：

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

如果警告与资源冲突有关，则需要用户注意才能解决该问题。

此 **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** 文件包含同步结果。 默认情况下，它位于以下目录中： **installationDirectory/var/`<instance-name>`/postupgrade**. 错误和警告属性表示错误和警告。

### 分析冲突

**如何发现冲突？**

在相关服务器上的postupgrade.log或Campaign客户端界面（“管理”>“配置”>“包管理”>“编辑冲突”）中，可能会发现冲突。

标识符为“stockOverview”且类型为“nms：webApp”的文档与新版本冲突。

如果发现冲突，请检查以下条件是否匹配：

* 客户是否修改或自定义了对象？
* 对象在产品中是否发生了更改？

如果这些条件都不适用，则为误报。 如果这两个条件都适用，则发现真正的冲突。

**客户是否修改了对象？**

1. 识别冲突对象。
1. 询问客户是否修改了对象。
1. 这个物体有什么不寻常的地方吗？
1. 对象的代码中是否设置了上次修改日期？
1. 从冲突中检查XML代码的“_conflict”属性。 它是否看起来像自定义？

**对象在新内部版本中是否进行了更改？**

1. 有“常见嫌犯”吗？ 内置Web应用程序或报告（例如：“deliveryValidation”、“deliveryOverview”、“budget”）。
1. 检查更改日志是否有任何更新。
1. 询问Adobe Campaign专家。
1. 对代码执行“差异”。

### 解决冲突

要解决冲突，请应用以下流程：

1. 在Adobe Campaign资源管理器中，转到 **管理>配置>包管理>编辑冲突**.

1. 在列表中选择要解决的冲突。
解决冲突有三种方法： **接受新版本**， **保留当前版本**， **合并代码（并声明为已解析）**， **忽略冲突（不推荐）**.

**我何时可以接受新版本？**

* 如果您需要标准特征。
* 如果您没有自定义项（将删除所有自定义项）

**何时可以保留当前版本？**

* 如果您有自定义项
* 如果您不想合并
* 如果您不需要对升级中的冲突对象进行任何修复

**何时执行合并？**

* 只能合并表单、报表和Web应用程序。
* 某些次要合并无需了解代码即可得到解决。
* 更复杂的合并应由具有相应技能和能力的人进行。
* 请参阅 [执行合并](#perform-a-merge).

**如果我不理会冲突怎么办？**

* 冲突将依然存在
* 将不会升级该对象
* 长期影响：版本不兼容，客户将无法从错误修复中受益。

>[!IMPORTANT]
>强烈建议解决冲突。
>

### 执行合并{#perform-a-merge}

有不同类型的合并：

1. 轻松合并：自定义元素和新元素很小且没关系，无需编码。
1. 无更改：接受新版本，仅上次更新日期已更改，仅注释、制表符、空格或新行。 示例：意外保存。
1. 细微的更改：仅更改了一行。 示例： xpathToLoad
1. 复杂合并：需要编码时。 需要发展技能。 请参阅 [复杂合并](#complex-merges).

#### 如何合并？

1. 获取所有三个版本：原始版本、新版本和自定义版本。
1. 运行原始版本和新版本之间的“差异”。
1. 隔离更改。
1. 如果没有更改，请通过保留当前版本来解决。

#### 在哪里查找代码？

1. 内置代码存储在datakit文件夹的XML文件中。 查找与冲突对象匹配的XML文件。 示例： installationDirectory\datakit\nms\fra\form\recipient.xml
1. 检索原始版本：通过 [下载中心](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html) 或产品的另一个未升级安装。
1. 检索新版本：通过 [下载中心](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html) 或客户安装的文件。
1. 检索自定义版本：从Campaign客户端中检索对象的源代码。

### 如何进行区分？

1. 安装文本或合并编辑器，例如Notepad ++、AraxisMerge、WinMerge。
1. 在编辑器中打开原始文件和新文件。
1. 运行diff（比较两个文件）。
1. 识别任何差异。

### 如何合并？

1. 从自定义版本开始。
1. 应用更改。
1. 通过声明冲突已解决来解决冲突。
1. 检查无回归。

如果选择手动解决冲突，请按以下步骤操作：

1. 在窗口的下部，搜索 **_冲突字符串_** 以查找具有冲突的图元。 与新版本一起安装的实体包含新参数，与先前版本匹配的实体包含自定义参数。
1. 删除您不想保留的版本。 删除 **_conflict_argument_** 要保留的实体的字符串。
1. 转到您已解决的冲突。 单击 **操作** 图标并选择 **声明为已解决**.
1. 保存更改：冲突现已解决。

#### 复杂合并{#complex-merges}

1. 了解更改的作用：对更改进行逆向工程、检查更改日志、与Adobe Campaign专家跟进。
1. 决定如何处理更改。
1. 了解自定义项的作用：对更改进行逆向工程

以下是执行复杂合并的步骤：

1. 从更改集中复制代码位
1. 粘贴到自定义版本
1. 测试自定义项的不回归
1. 测试更改的功能
1. 执行用户验收测试
1. 在测试环境中执行


>[!IMPORTANT]
>执行复杂的合并需要具备开发技能。
>

**相关主题**

* [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic发行说明](../../rn/using/rn-overview.md)
* [Campaign Classic的帮助和支持选项](../../support.md)
* [Campaign年度升级计划](../../rn/using/rn-overview.md)
