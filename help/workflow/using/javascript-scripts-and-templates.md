---
solution: Campaign Classic
product: campaign
title: JavaScript 脚本和模板
description: JavaScript 脚本和模板
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1234'
ht-degree: 2%

---


# JavaScript 脚本和模板{#javascript-scripts-and-templates}

脚本使计算值、在进程中不同任务之间交换数据以及使用SOAP调用执行特定操作成为可能。

脚本在工作流程图中无处不在：

* 所有活动都有初始化脚本。 初始化脚本在激活活动时执行，并可用于初始化变量和修改属性。
* “JavaScript代码”活动只用于执行脚本。
* “测试”活动评估JavaScript表达式，以激活相应的过渡。
* 大多数文本字段是JavaScript模板：JavaScript表达式可以包含在&lt;%=和%>之间。 这些字段优惠一个按钮，该按钮打开一个下拉列表，帮助您输入表达式。

   ![](assets/script-button.png)

## 公开的对象 {#objects-exposed}

在工作流上下文中执行的JavaScripts可访问一系列附加的全局对象。

* **实例**:表示正在执行的工作流。 此对象的模式为 **xtk:workflow**。
* **任务**:表示正在执行的任务。 此对象的模式 **为xtk:workflowTask**。
* **事件**:表示激活了正在执行的事件的任务。 此对象的模式 **为xtk:workflowEvent**。 未针对已从多个 **活动激活的** AND-join类型过渡初始化此对象。
* **事件**:表示激活当前任务的事件的列表。 此对象的模式 **为xtk:workflowEvent**。 此表通常包含一个元素，但对于AND-join类 **型活动** ，可能包含多个元素，这些已基于多个过渡激活。
* **活动**:表示正在执行的任务的模型。 此对象的模式取决于活动类型。 此对象可由初始化脚本修改，在其他脚本中，修改具有不可确定的效果。

通过单击脚本工具栏右侧的按钮，可以在下拉列表中查看这些对象的可用属性。

>[!CAUTION]
>
>这些对象的属性是只读的，vars属性的子属性除外。
>  
>大多数这些属性仅在执行基本任务或实例被钝化后才更新。 读取的值不一定与当前状态匹配，而是与之前的状态匹配。

**示例**

在本示例和以下示例中，创建一个包含JavaScript代码 **活动和** End **活动的工作流，如** 下图所示。

![](assets/script-1.png)

多次-单击 **JavaScript代码** 活动，然后插入以下脚本：

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

该函 **[!UICONTROL logInfo(message)]** 数在日志中插入一条消息。

单 **[!UICONTROL OK]** 击以关闭创建向导，然后使用位于开始列表右上方的操作按钮来工作流工作流。 执行结束时，请查阅日志。 您应当看到与脚本对应的两条消息：一个显示工作流的标签，另一个显示激活脚本的日期。

## 变量 {#variables}

变量是对象和对象 **[!UICONTROL instance]**&#x200B;的 **[!UICONTROL task]** 自由 **[!UICONTROL event]** 属性。 授权这些变量的JavaScript类型 **[!UICONTROL string]**&#x200B;是 **[!UICONTROL number]** 和 **[!UICONTROL Date]**。

### 实例变量 {#instance-variables}

实例变量(**[!UICONTROL instance.vars.xxx]**)与全局变量类似。 所有活动都共享。

### 任务变量 {#task-variables}

任务变量(**[!UICONTROL task.vars.xxx]**)与局部变量类似。 它们只供当前任务使用。 持久活动使用这些变量来保留数据，有时还用于在同一活动的不同脚本之间交换数据。

### 事件变量 {#event-variables}

事件变量(**[!UICONTROL vars.xxx]**)允许在工作流程的基本任务之间交换数据。 这些变量由激活进行中的任务传递。 可以修改它们并定义新的。 然后，将其传递给以下活动。

>[!CAUTION]
>
>对于AND-join [类型活动](../../workflow/using/and-join.md) ，变量会合并，但如果同一变量定义了两次，则存在冲突，且值仍未确定。

事件是最常用的变量，它们应优先用于实例变量。

某些事件变量由不同活动修改或读取。 这些都是字符串类型变量。 例如，导出会用刚 **[!UICONTROL vars.filename]** 刚导出的文件的全名设置变量。 所有这些读取或修改的变量都在 [关于活动](../../workflow/using/about-activities.md)、的输 **入参数** 和活动 **的输出参数中记录** 。

### 用例 {#example}

>[!NOTE]
>
>本节提供其他工作流 [使用案例](../../workflow/using/about-workflow-use-cases.md)。

**示例1**

在此示例中，一个实例变量用于动态计算要应用于人口的拆分百分比。

1. 创建工作流并添加开始活动。

1. 添加和配置JavaScript代码活动以定义实例变量。

   例如：`instance.vars.segmentpercent = 10;`

   ![](assets/js_ex1.png)

1. 根据您的需要添加查询活动和目标收件人。

1. 添加“拆分”活动并将其配置为对传入人口执行随机采样。 抽样百分比可以是您选择的任何内容。 在本例中，它设置为50%。

   它是动态更新的百分比，这要归功于之前定义的实例变量。

   ![](assets/js_ex2.png)

1. 在“拆分”活动的“高级”选项卡的“初始化脚本”部分中，定义JS条件。 JS条件选择从“拆分”过渡中出现的第一个活动的随机采样百分比，并将其更新为先前创建的实例变量设置的值。

   ```
   activity.transitions.extractOutput[0].limiter.percent = instance.vars.segmentpercent;
   ```

   ![](assets/js_ex3.png)

1. 确保在“拆分”活动的单独过渡中生成补码，并在每个出站过渡之后添加“结束”活动。

1. 保存并执行工作流。 动态采样根据实例变量进行。

   ![](assets/js_ex4.png)

**示例 2**

1. 从上一个示例中采用工作流，将JavaScript代码 **活动的脚本** 替换为以下脚本：

   ```
   instance.vars.foo = "bar1"
   vars.foo = "bar2"
   task.vars.foo = "bar3"
   ```

1. 将以下脚本添加到结束活动的初始 **化脚本** :

   ```
   logInfo("instance.vars.foo = " + instance.vars.foo)
   logInfo("vars.foo = " + vars.foo)
   logInfo("task.vars.foo = " + task.vars.foo)
   ```

1. 开始工作流，然后查看日志。

   ```
   Workflow finished
   task.vars.foo = undefined
   vars.foo = bar2
   instance.vars.foo = bar1
   Starting workflow (operator 'admin')
   ```

此示例说明以下JavaScript **代码的活动** ，访问实例变量和事件变量，但任务变量无法从外部访问(“undefined”)。

### 在查询中调用实例变量 {#calling-an-instance-variable-in-a-query}

在活动中指定实例变量后，您可以在工作流查询中重复使用它。

因此，要在筛选 **器中调用变量instance.vars.xxx = &quot;yyy** &quot;，请 **输入$(instance/vars/xxx)**。

例如：

1. 创建一个实例变量，它通过以下方式定义投放的内部名称 **[!UICONTROL JavaScript code]**: **instance.vars.deliveryIN = &quot;DM42&quot;**。

   ![](assets/wkf_js_activity_1.png)

1. 创建定位和过滤维度是查询的收件人。 在条件中，指定要查找发送了变量指定的收件人符的所有投放符。

   作为提醒，此信息存储在投放日志中。

   要引用列中的实 **[!UICONTROL Value]** 例变量， **请输入$(instance/vars/@deliveryIN)**。

   该工作流将返回DM42收件人的投放。

   ![](assets/wkf_var_in_query.png)

## 高级功能 {#advanced-functions}

除了标准JavaScript函数外，还有特殊函数可用于处理文件、读取或修改数据库中的数据或向日志添加消息。

### 日志 {#journal}

**[!UICONTROL logInfo(message)]** 详见上述示例。 此函数向日志添加信息消息。

**[!UICONTROL logError(message)]** 向日志中添加错误消息。 脚本中断其执行，而工作流将更改为错误状态（默认情况下，将暂停实例）。

## 初始化脚本 {#initialization-script}

在某些情况下，您可以在执行时修改活动的属性。

活动的大多数属性都可以动态计算，这既可以使用JavaScript模板，也可以是因为工作流属性明确允许脚本计算该值。

但是，对于其他属性，必须使用初始化脚本。 在执行任务之前，将评估此脚本。 变 **[!UICONTROL activity]** 量引用与活动对应的任务。 此活动的属性可以修改，且仅影响此任务。
