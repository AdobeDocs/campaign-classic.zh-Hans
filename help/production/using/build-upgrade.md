---
solution: Campaign Classic
product: campaign
title: 构建升级入门
description: 了解升级到新版本的关键步骤
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: b77a56a97e499f60c092fae45c7809f7bfd9f2ea
workflow-type: tm+mt
source-wordcount: '2360'
ht-degree: 2%

---


# 执行内部版本升级{#performing-a-build-upgrade}

本节将为您提供有关升级过程以及识别和解决冲突的步骤的深入演练。

建设升级必须谨慎进行，其影响必须事先充分考虑，程序必须以高度纪律完成。 要确保升级成功，请确保只有专家用户才能执行下面列出的步骤。 此外，我们强烈建议在开始任何升级之前先与[Adobe客户服务部门](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)联系。

需要以下先决条件：

* 了解活动架构
* 系统和服务器端知识
* 管理权限

您可以在以下部分中找到更多信息：[更新Adobe Campaign](../../production/using/upgrading.md)、[迁移到新版本](../../migration/using/about-migration.md)。

对于托管实例和混合实例，您必须向Adobe技术运营团队请求内部版本升级。 有关此问题的详细信息，请参阅本页底部的常见问题解答部分。 另请查阅[构建升级常见问题解答](../../platform/using/faq-build-upgrade.md)。

## 准备升级

![](assets/do-not-localize/icon_planification.png)

在开始内部版本升级之前，您必须按照以下说明执行完整准备。
系统准备好升级后，生成升级至少需要**** 2小时。

构建升级过程需要以下资源：

* Adobe架构师 — 了解模式库结构(现成的和已添加的任何其他模式、活动设计以及任何必须按特定顺序启动和测试的关键路径功能)。
* 项目经理 — 如果构建升级涉及许多不同的实例（生产、升级、测试）和其他第三方服务器和应用程序(数据库、SFTP站点、消息服务提供商)，则由项目经理来协调所有测试被认为是最佳做法。
* Adobe Campaign管理员 — 您的管理员了解服务器的配置，包括但不限于：安全性、文件夹布局、报告和导入\导出要求。 请勿在没有管理员的情况下执行内部版本升级。
* Adobe Campaign运营商（营销用户） — 成功升级取决于用户成功执行其日常任务的能力。 因此，在测试升级服务器时，请务必至少包含您的日常操作员之一。

### 规划

下面是有关如何计划内部版本升级的要点：

1. 升级至少需要2小时。
1. 分发Adobe和客户员工的联系信息。
1. 对于托管实例：Adobe和客户员工将协调升级时间和执行人员。
1. 对于预置实例：客户员工负责整个流程 — 如果需要在测试自定义工作流和投放逻辑方面提供协助，则应引入咨询服务。
1. 确定并确认要升级到的Adobe Campaign版本 — 请参阅[Adobe Campaign Classic发行说明](../../rn/using/rn-overview.md)。
1. 确认拥有升级可执行文件。

### 关键人物

构建升级过程需要以下人员参与：

* Adobe架构师：对于托管或混合架构，架构师必须与Adobe Campaign Client Care协调。

* 项目经理：
   * 对于内部部署安装：客户的内部项目领导者负责升级并管理生命周期测试。

   * 对于托管安装：托管团队将与Adobe Campaign Client Care团队和客户合作，协调所有实例的升级时间线。

* Adobe Campaign管理员：
   * 对于内部部署安装：管理员执行升级。

   * 对于托管安装：托管团队执行升级。

* Adobe Campaign运营商\营销用户：运营商对开发、测试和生产实例运行测试。

### 准备内部版本升级

在开始内部版本升级之前，预置型客户需要执行以下准备工作：

1. 确保在升级之前可以导出任何开发工作，以包形式导出。

1. 为源环境和目标数据库的所有实例执行数据库的完全备份。

1. 获取[服务器配置文件](../../installation/using/the-server-configuration-file.md)的最新版本。

1. [下载最新版本](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。[了解详情](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)。

在开始生成升级之前，您还需要了解所有[有用的命令行](../../installation/using/command-lines.md):

* **nlserver pdump**:列表运行进程
* **nlserver pdump -who**:列表活动客户端会话
* **nlserver监视器 — missing**:列表缺少属性
* **nlserver开始process@instanceName**:开始流程
* **nlserver stop process@instanceName**:停止进程
* **nlserver restart process@instanceName**:重新启动进程
* **nlserver shutdown**:停止所有活动进程
* **nlserver watchdog -svc**:开始监视程序（仅限UNIX）

## 执行升级

![](assets/do-not-localize/icon_process.png)

以下步骤仅由&#x200B;**内部部署**&#x200B;客户执行。 对于托管客户，托管团队会负责处理。 要将Adobe Campaign更新到新版本，详细过程如下所述。

### 重复环境

下面是您如何重复Adobe Campaign环境，以将源环境恢复为目标环境，从而产生两个相同的工作环境。

为此请执行以下操作步骤：

1. 在源环境中的所有实例上创建数据库的副本。

1. 在目标环境的所有实例中恢复这些副本。

1. 在启动目标环境之前，在Adobe Player上运行&#x200B;**nms:freezeInstance.js**&#x200B;烧灼脚本。 这将阻止所有进程与外部交互：日志、跟踪、投放、活动工作流等

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. 检查烧灼，如下所示：

   * 检查唯一的投放部分是ID设置为&#x200B;**0**&#x200B;的部分：

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

要用新版本替换所有文件，需要关闭nlserverservice的所有实例。

1. 关闭以下服务：

   * Web服务(IIS):**ireset /stop**
   * Adobe Campaign服务：**net stop nlserver6**

   >[!NOTE]
   >
   >确保已停止重定向服务器(webmdl)，以便IIS使用的nlsrvmod.dll文件可替换为新版本。

1. 通过运行&#x200B;**nlserver pdump**&#x200B;命令验证没有任务处于活动状态。 如果没有任务，则输出应类似于以下内容：

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. 检查Windows任务管理器以确认所有进程都已停止。

### 升级Adobe Campaign Server应用程序

1. 运行&#x200B;**Setup.exe**&#x200B;文件。 如果需要下载此文件，请访问[下载中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。

1. 选择安装模式：**更新**&#x200B;或&#x200B;**修复**。

1. 单击&#x200B;**下一步**。

1. 单击&#x200B;**完成**:安装项目会复制新文件。

1. 操作完成后，单击&#x200B;**完成**。

### 同步资源

1. 打开命令行。

1. 运行&#x200B;**nlserver config -postupgrade -allinstances**&#x200B;以执行以下操作：

   * 同步资源
   * 更新模式
   * 更新数据库

   >[!NOTE]
   >
   >此操作只应执行一次，并且只应在Serverweb应用程序服务器上执行。

   要仅同步一个数据库，请运行以下命令：

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. 检查同步是否生成了任何错误或警告。

### 重新启动服务

需要重新启动以下服务：

* Web服务(IIS):**issreset /开始**
* Adobe Campaign服务：**净开始nlserver6**

### 客户端控制台更新

客户端控制台必须与服务器实例位于同一版本上。

在安装Adobe Campaign应用程序服务器(nlserverweb)的计算机上，下载并复制文件：

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

下次连接客户端控制台时，将出现一个窗口，告知用户新更新的可用性，并优惠用户下载和安装该更新的可能性。

### 特定附加任务

某些配置需要特定的附加任务才能更新到新版本。

#### 事务型消息传递

在您的活动实例上启用Transactional Messaging(Message Center)后，您需要执行以下其他步骤来升级：

1. 将Message Center生产服务器更新到所选版本。
1. 运行配置脚本。
1. 运行测试并确保通过Message Center生产实例成功接收电子邮件。
1. 升级客户端并清除缓存。
1. 导出包：
   * 使用客户端包导出工具导出包
   * 导入模式包
   * 断开和重新连接客户端
   * 更新数据库
   * 断开连接并重新连接
   * 导入管理包
   * 导入内容包
   * 导入内容管理包
   * 断开连接并重新连接
   * 快速检查工作流

1. 发布消息中心模板，以确保服务器和消息中心实例之间的接口正常工作。
1. 运行测试，确保通过Message Center生产实例成功接收电子邮件。
1. 在生产中运行工作流测试以确保接收投放。

#### 中间源

在中间源环境的上下文中，您需要执行以下其他步骤才能进行升级：

1. 联系[Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以协调中间源服务器的升级。
1. 通过运行测试链接验证版本是否已更新。 例如：

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>中间源服务器必须始终运行与营销服务器相同的版本（或更新的版本）。


## 如果发生冲突

### 识别冲突

您需要检查同步结果。 此过程仅由预置型客户执行。 对于托管客户，托管团队会负责处理。 有两种方法可视图同步结果：

在命令行接口中，错误由三个V形标记“>>>”实现，同步会自动停止。 警告由多次V形标记“>>”实现，并且必须在同步完成后解决。 在配置的末尾，将在命令提示符下显示摘要。 它可以是这样的：

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

如果警告涉及资源冲突，则需要用户注意才能解决。

**postupgrade_ServerVersionNumber_TimeOfPostupgrade.log**&#x200B;文件包含同步结果。 默认情况下，它位于以下目录中：**installationDirectory/var/instanceName/postupgrade**。 错误和警告由错误和警告属性指示。

### 分析冲突

**如何找到冲突？**

可在相关服务器上的postupgrade.log或活动客户端界面（“管理”>“配置”>“包管理”>“编辑冲突”）中找到冲突。

标识符为“stockOverview”且键入“nms:webApp”的文档与新版本冲突。

如果发现冲突，请检查以下条件是否匹配：

* 客户是否修改或自定义了对象？
* 对象在产品中是否发生更改？

如果这两种情况都不适用，则这是假阳性。 如果这两种情况都适用，则发现了真正的冲突。

**客户是否修改了对象？**

1. 识别冲突对象。
1. 询问客户是否修改了对象。
1. 这个物体有什么不同寻常之处吗？
1. 是否在对象的代码中设置上次修改日期？
1. 检查冲突中的XML代码是否有“_conflict”属性。 它看起来像是自定义的吗？

**新生成中的对象是否已更改？**

1. 有&quot;常见嫌犯&quot; 内置的Web应用程序或报告(例如：“deliveryValidation”、“deliveryOverview”、“budget”)。
1. 检查更改日志中是否有任何更新。
1. 咨询Adobe Campaign专家。
1. 对代码执行“diff”。

### 解决冲突

要解决冲突，请应用以下流程：

1. 在Adobe Campaign资源管理器中，转至&#x200B;**“管理”>“配置”>“包管理”>“编辑冲突”**。

1. 在列表中选择要解决的冲突。
有三种解决冲突的方法：**接受新版本**、**保留当前版本**、**合并代码（并声明为已解决）**、**忽略冲突（不推荐）**。

**我何时可以接受新版本？**

* 如果您需要标准功能，
* 如果您没有自定义项（将删除所有自定义项）

**何时可以保留当前版本？**

* 如果您有自定义项
* 如果您不想合并
* 如果升级时不需要对冲突对象进行任何修复

**何时执行合并？**

* 只能合并表单、报表和Web应用程序。
* 某些次合并可以在不理解代码的情况下进行解决。
* 更复杂的合并应由具备适当技能和能力的人进行。
* 请参阅[执行合并](#perform-a-merge)。

**如果我忽视冲突呢？**

* 冲突将继续存在
* 对象将不会升级
* 长期影响：版本不兼容，客户将不会从错误修复中受益。

>[!IMPORTANT]
>强烈建议解决冲突。


### 执行合并{#perform-a-merge}

有不同类型的合并：

1. 轻松合并：自定义元素和新元素很小且互不相关，无需编码。
1. 无更改：接受新版本，仅更改上次更新日期，仅更改注释、制表符、空格或新行。 示例：意外保存。
1. 微小的更改：只换了一行。 示例：xpathToLoad
1. 复杂合并：需要编码时。 需要开发技能。 请参阅[复杂合并](#complex-merges)。

#### 如何合并？

1. 获取所有三个版本：原始版本、新版本和自定义版本。
1. 在原始版本和新版本之间运行“差异”。
1. 隔离更改。
1. 如果没有更改，请通过保留当前版本来解决。

#### 在哪里找到代码？

1. 内置代码存储在datakit文件夹的XML文件中。 查找与冲突对象匹配的XML文件。 示例：installationDirectory\datakit\nms\fra\form\recipient.xml
1. 检索原始版本：通过[下载中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)或其他未升级的产品安装。
1. 检索新版本：通过[下载中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)或客户安装的文件。
1. 检索自定义版本：从活动客户端中检索对象的源代码。

### 如何进行差异比较？

1. 安装文本或合并编辑器，例如Notepad ++、AraxisMerge、WinMerge。
1. 在编辑器中打开原始文件和新文件。
1. 运行差异比较（比较两个文件）。
1. 识别任何差异。

### 如何合并？

1. 开始。
1. 应用更改。
1. 通过声明冲突已解决来解决冲突。
1. 检查不回归。

如果选择手动解决冲突，请按如下步骤继续：

1. 在窗口的下半部分，搜索&#x200B;**_conflict_string_**&#x200B;以查找存在冲突的实体。 随新版本安装的实体包含新参数，与先前版本匹配的实体包含自定义参数。
1. 删除您不想保留的版本。 删除要保留的实体的&#x200B;**_conflict_argument_**&#x200B;字符串。
1. 转到已解决的冲突。 单击&#x200B;**Actions**&#x200B;图标，然后选择&#x200B;**声明为已解析**。
1. 保存更改：冲突现已解决。

#### 复杂合并{#complex-merges}

1. 了解更改的作用：对更改进行逆向工程，检查更改日志，与Adobe Campaign专家跟进。
1. 决定如何处理更改。
1. 了解自定义项的用途：反向工程更改

以下是执行复杂合并的步骤：

1. 从更改集中复制代码位
1. 粘贴到自定义版本
1. 定制化的非回归检验
1. 测试更改的功能
1. 执行用户接受测试
1. 在测试环境中执行


>[!IMPORTANT]
>执行复杂合并需要具备开发技能。


**相关主题**

* [构建升级常见问题解答](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic发行说明](../../rn/using/rn-overview.md)
* [有关Campaign Classic的帮助和支持选项](https://helpx.adobe.com/cn/campaign/kb/ac-support.html)
* [[!DNL Gold Standard] 项目](../../rn/using/gs-overview.md)
