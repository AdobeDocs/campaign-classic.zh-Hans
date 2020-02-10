---
title: 执行工作流
seo-title: 执行工作流
description: 执行工作流
seo-description: null
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4b4ec97e52a494dd88b2516650ae514294f00934

---


# 执行工作流{#executing-a-workflow}

本节提供与工作流执行相关的疑难解答 [指南](../../production/using/workflow-execution.md)。

## 启动工作流 {#starting-a-workflow}

工作流始终手动启动。 但是，启动时，它可以根据通过调度程序指定的信息(请参阅 [Scheduler](../../workflow/using/scheduler.md))或活动调度保持非活动状态。

与定位工作流执行（启动、停止、暂停等）相关的操作是异 **步进程** :订单将被记录，并在服务器可用时生效。

工具栏允许您启动和跟踪工作流的执行。

菜单和右键单击菜 **[!UICONTROL Actions]** 单中的可用选项列表详述如下。

### 操作工具栏 {#actions-toolbar}

此部分详细介绍了工具栏 [按钮](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)。 通过 **[!UICONTROL Actions]** 该按钮，您可以访问其他执行选项以对选定的工作流执行操作。 您还可以使用菜 **[!UICONTROL File > Actions]** 单，或右键单击工作流并选择 **[!UICONTROL Actions]**。

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   通过此操作，您可以开始执行工作流：已完成、正在编 **辑或已暂停的工作流**，将状态更 **改为“已** 开始”( ******** Started)。 然后，工作流引擎将处理此工作流的执行。 如果暂停了工作流，则它会继续，否则，工作流会从开始开始并激活初始活动。

   启动是一个异步进程：将保存该请求，并由工作流服务器尽快进行处理。

* **[!UICONTROL Pause]**

   此操作会将工作流的状态设置为“已 **暂停**”。 在继续工作流之前，不会激活任何活动；但是，不会暂停进行中的操作。

* **[!UICONTROL Stop]**

   此操作会停止当前正在执行的工作流。 实例的状态设置为“已完 **成”**。 如果可能，停止正在进行的操作。 导入和SQL查询将立即取消。

   停止是一个异步进程。 注册请求，然后工作流服务器或服务器取消正在进行的操作。 因此，停止工作流实例可能需要时间，尤其是当工作流在多台服务器上运行时，其中每台服务器必须控制以取消正在进行的任务。

* **[!UICONTROL Restart]**

   此操作会停止，然后重新启动工作流。 在大多数情况下，它使得可以更快地重新开始。 在停止需要一定时间时自动重新启动也很有用：这是因为当工作流停止时“停止”命令不可用。

   操 **[!UICONTROL Start / Pause / Stop / Restart]** 作也可通过工具栏中的执行图标来使用。 For more on this, refer to this [section](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

   通过此操作，您可以清除工作流历史记录。 有关此问题的详细信息，请参 [阅清除日志](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs)。

* **[!UICONTROL Start in simulation mode]**

   此选项允许您在模拟模式下启动工作流，而不是在实际模式下启动。 这意味着，当您启用此模式时，只执行不影响数据库或文件系统的活动(例如， **[!UICONTROL Query]**、 **[!UICONTROL Union]**、 **[!UICONTROL Intersection]**&#x200B;等)。 具有影响的活动(例如， **[!UICONTROL Export]**、 **[!UICONTROL Import]**&#x200B;等)以及之后（在同一分支中）不执行的签名。

* **[!UICONTROL Execute pending tasks now]**

   通过此操作，您可以尽快启动所有待处理任务。 要启动特定任务，请右键单击其活动并选择 **[!UICONTROL Execute pending task(s) now]**。

* **[!UICONTROL Unconditional stop]**

   此选项会将工作流状态更改为 **[!UICONTROL Finished]**。 仅当正常停止过程在几分钟后失败时，此操作才应作为最后的手段。 仅当您确定没有实际的工作流作业正在进行时，才使用无条件停止。

   >[!CAUTION]
   >
   >此选项为专家用户保留。

* **[!UICONTROL Save as template]**

   此操作将基于选定的工作流创建新的工作流模板。 您需要指定保存该文件夹的文件夹(在字 **[!UICONTROL Folder]** 段中)。

   和 **[!UICONTROL Mass update of selected lines]** 选项 **[!UICONTROL Merge selected lines]** 是所有菜单中可用的通用平台 **[!UICONTROL Actions]** 选项。 For more on this, refer to this [section](../../platform/using/updating-data.md).

### 右键单击菜单 {#right-click-menu}

选择一个或多个工作流活动后，您可以右键单击以根据您的选择进行操作。

![](assets/contextual_menu.png)

右键单击菜单中提供以下选项：

**[!UICONTROL Open]**:此选项允许您访问活动属性。

**[!UICONTROL Display logs:]** 此选项允许您查看选定活动的任务执行日志。 请参阅显 [示日志](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)。

**[!UICONTROL Execute pending task(s) now:]** 通过此操作，您可以尽快启动待处理任务。

**[!UICONTROL Workflow restart from a task:]** 此选项允许您使用先前为此活动存储的结果重新启动工作流。

**[!UICONTROL Cut/Copy/Paste/Delete:]** 这些选项允许您剪切、复制、粘贴和删除活动。

**[!UICONTROL Copy as bitmap:]** 通过此选项，您可以获取所有活动的屏幕截图。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 这些选项也位于活动属 **[!UICONTROL Advanced]** 性的选项卡中。 执行中详细介绍 [了这些](../../workflow/using/advanced-parameters.md#execution)。

**[!UICONTROL Save / Cancel:]** 允许您保存或取消对工作流所做的更改。

>[!NOTE]
>
>您可以选择一组活动，并将这些命令之一应用于这些活动。

右键单击菜单在本节中也有详细 [说明](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow)。

## 工作流生命周期 {#workflow-life-cycle}

工作流循环有三个主要步骤。

* **正在编辑**

   这是初始设计阶段：创建新工作流时，其状态为“正在编辑”。 该工作流尚未由服务器处理，并且可以无风险修改。

* **开始**

   完成初始设计阶段后，可以启动工作流。 在此阶段，实例由服务器处理并执行单个任务。 仍然可以使用某些预防措施修改工作流。

* **已完成**

   当不再有任何任务正在进行或当操作符明确停止实例时，工作流将变为“已完成”。

例如，开始和 **交付****活动列出，而****** 批准活动在下面的工作区闪烁。

![](assets/new-workflow-6.png)

这意味着前两项活动已成功执行且正在进行批准，即已创建但尚未完成。

在“ **Delivery** ”活动后的过渡上方显示的字符为574 - Ok **** ，这意味着交付准备已针对574个收件人，并且操作已成功完成。 此信息在执行转换时添加到转换，由处理数据的活动计算。

此时将启动工作流，并等待属于“批准”活动中指定组的运 **营商** 作出决定。 将通知属于该组的运营商和具有电子邮件地址或移动电话号码的运营商。

本节详细介绍了运营 [商管理](../../platform/using/access-management.md)。

有关如何监视工作流的详细信息，请参阅 [此部分](../../workflow/using/monitoring-workflow-execution.md)。

## 数据生命周期 {#data-life-cycle}

### 工作表 {#work-table}

在工作流中，从一个活动传输到另一个活动的数据被存储在临时工作表中。

可通过右键单击相应的过渡来显示和分析此数据。

![](assets/wf-right-click-analyze.png)

为此，请选择相关菜单：

* 显示目标

   此菜单显示目标人群的可用数据以及工作表（选项卡）**[!UICONTROL Schema]** 的结构。

   ![](assets/wf-right-click-display.png)

   有关此功能的详细信息，请参阅工作 [表和工作流架构](../../workflow/using/monitoring-workflow-execution.md#worktables-and-workflow-schema)。

* 分析目标

   通过此菜单，您可以访问描述性分析向导，该向导可生成有关过渡数据的统计信息和报告。

   For more on this, refer to this [section](../../reporting/using/using-the-descriptive-analysis-wizard.md).

在执行工作流时，目标数据会被清除。 只有最后一个工作表可供访问。 您可以配置工作流，以便所有工作表仍可访问：选中工 **[!UICONTROL Keep the result of interim populations between two executions]** 作流属性中的选项。

但是，我们建议您在出现大量数据时避免激活此选项。

![](assets/wf-purge-data-option.png)

### 目标数据 {#target-data}

可在个性化字段中访问存储在工作流工作表中的数据。

这样，您就可以使用通过列表收集的数据，或根据投递中调查的答案收集的数据。 为此，请使用以下语法：

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData)类型个性化元素不适用于定位工作流。 必须在工作流中构建交付目标，并在交付的入站过渡中指定该目标。

如果要创建交付校样，则需要基于该模式构建证明目标， **[!UICONTROL Address substitution]** 以便输入个性化数据。 For more on this, refer to this [section](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof).

在以下示例中，我们将收集客户信息列表，并在个性化电子邮件中使用。

应用以下步骤：

1. 创建一个工作流以收集信息，将其与数据库中已有的数据进行协调，然后开始分发。

   ![](assets/wf-targetdata-sample-1.png)

   在我们的示例中，文件内容如下：

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   要加载文件，请应用以下步骤：

   ![](assets/wf-targetdata-sample-2.png)

1. 配置类 **[!UICONTROL Enrichment]** 型活动以协调收集的数据与Adobe Campaign数据库中已有的数据。

   此处，对帐密钥是帐号：

   ![](assets/wf-targetdata-sample-3.png)

1. 然后，配置 **[!UICONTROL Delivery]**:它基于模板创建，收件人由入站过渡指定。

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >只能使用转换中包含的数据来个性化交付。 **targetData** type personalization字段仅可用于活动的入站 **[!UICONTROL Delivery]** 人群。

1. 在传送模板中，使用在工作流中收集的字段。

   为此，请插入类 **[!UICONTROL Target extension]** 型个性化字段。

   ![](assets/wf-targetdata-sample-5.png)

   在此，我们希望按工作流收集的文件中所述插入客户最喜欢的音乐类型和媒体类型（CD或DVD）。

   作为一个加号，我们将为忠诚卡持有人添加优惠券，即“卡”值等于1的收件人。

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** (targetData)类型数据会使用与所有个性化字段相同的特性插入到分发中。 它们也可用于主题、链接标签或链接本身。

   发送给收集的收件人的消息将包含以下数据：

   ![](assets/wf-targetdata-sample-7.png)

## 定义批准 {#defining-approvals}

通过批准，运营商可以做出管理工作流的决策或确认其持续执行。

将向一组操作符发送消息，而工作流会在恢复之前等待响应。 此工作流不会停止，并且可以执行其他操作。 例如，可能有多个同时等待批准。

批准可以包含多个选项供操作员选择。 但是，可以将选择的数量限制为一个，以便向操作员提交要执行的任务，例如执行定位。 然后，操作员可以在执行任务后做出响应（然后恢复进程）。 以下示例说明了这些类型的批准：

![](assets/validation-1.png)

在运营中，所有需要批准的阶段都基于相同的原则。

![](assets/validation-1-in-op.png)

此部分提供了批准示 [例](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。

运营商可以通过以下两种方式之一做出响应：使用电子邮件中链接的网页或通过控制台进行验证。

>[!NOTE]
>
>保存响应后，不能对其进行修改。

### 发送电子邮件 {#sending-emails}

可以接收包含指向网页的链接的批准消息，通过该链接可以进行响应。 要使目标运营商接收批准电子邮件，运营商电子邮件地址必须完整。 如果不是这样，则操作员必须使用控制台进行响应

本节详细介绍了运营 [商管理](../../platform/using/access-management.md)。

批准电子邮件会持续发送。 默认的交付模板为 **[!UICONTROL notifyAssignee]**:它保存在文件夹 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 中。 可以自定义此方案，还建议制作副本并更改每个活动的模板。

通过此模板创建的分发存储在文件夹 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** 中。

### 通过控制台进行批准 {#approval-via-the-console}

在操作中，要批准的元素显示在营销活动控制板上。

对于技术工作流，可以从文件夹的树结构访问用户可以批准的任 **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** 务。

![](assets/validation-node.png)

### 用户组 {#groups}

将批准分配给一组操作符、单个操作符或通过过滤条件选择的一组操作符。

1. 对于最简单的批准形式，操作员一做出响应，任务即完成。 任何其他试图做出响应的运营商都会收到有人已经这样做的通知。
1. 有关多个批准，请参阅多 [个批准](#multiple-approval)。

批准的运营商组应被指定为角色或职能，而不是指定为个人。 例如，“营销活动预算”组比“Harry&#39;s组”更好。 我们建议在一个组中至少有两个人可以批准任务。 这样，如果一个人缺席，另一个人就能做出回应。

### 过期时间 {#expirations}

过期是在不同类型的活动（尤其是在批准中）中使用的特定过渡。 到期可用于在给定时间之后在没有响应的情况下触发操作或继续工作流（例如，将批准分配给其他组）。

通过活动批准属性中的第二个选项卡，您可以定义一个或多个过期时间。 事实上，您可以定义多个过期类型。

![](assets/expiration.png)

要添加新的过期时间，请单击 **[!UICONTROL Add]**。 将过渡添加到创建的每个过渡。 您可以：

* 通过单击列表中的单元格（或按F2）直接修改典型参数，
* 或通过单击按钮编辑表达 **[!UICONTROL Detail...]** 式。

>[!NOTE]
>
>不必指定到期顺序，因为它们按时间顺序处理。

当延 **[!UICONTROL Do not terminate the task]** 迟超出时，此选项会使批准保持活动状态。 通过此模式，可以在保持批准处于活动状态时管理提醒：运营商仍然可以做出响应。 此选项默认处于禁用状态，这意味着任务在到期时被视为已完成，并且操作员可能不再响应。

可以创建四种过期类型：

* **任务开始后延迟**:到期时间是通过向激活批准的日期添加指定的时间长度来计算的。
* **在指定日期后延迟**:到期时间是通过向指定的日期添加时间长度来计算的。
* **在给定日期之前延迟**:过期时间的计算方法是从您指定的日期减去时间长度。
* **按脚本计算过期时间**:过期时间是使用JavaScript计算的。

   以下示例计算在开始交付之日(由 **vars.deliveryId标识**)前24小时的到期日：

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

### 多次批准 {#multiple-approval}

多重批准是一种机制，使所有批准运营商都能做出响应。 为每个响应激活过渡。

多项批准对投票或调查机制有用。 您可以通过添加截止日期来计算答案并处理其在给定时间段后的结果。

### 所需权限 {#required-rights}

群中的经营者必须至少拥有下列权利才能对批准请求作出答复：

* 工作流的写入权限。
* 包含要批准的任务的文件夹的读写权限。

“工作流执行”组具有这些权限。 添加到此组的运营商有权响应批准请求。

## 架构 {#architecture}

工作流由特定模块处理。 此模块可以在多台服务器上启动以共享处理负载。

![](assets/architecture.png)

* “工作流实例运行器”(runwf)进程执行给定工作流实例的所有任务。 当目前没有任务需要执行时，它会变为“被动”，即将状态保存在数据库中，然后停止。
* “Workflow Server”(wfserver)模块监视当前的工作流实例。 当有任务需要执行时，此模块会创建一个过程以激活（或重新激活）相应的实例。

当操作员对工作流执行操作（启动、停止、暂停等）时，“nlserver”模块不会立即执行该操作，而是将该操作置于队列中以便由工作流模块处理。
