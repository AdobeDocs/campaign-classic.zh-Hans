---
solution: Campaign Classic
product: campaign
title: 监督工作流
description: 了解如何监督活动工作流
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---


# 监督工作流{#supervising-workflows}

此用例详细介绍了如何创建工作流，它允许您监视“已暂停”、“已停止”或“有错误”的工作流集的状态。

其目的是：

* 使用工作流来监视一组业务工作流。
* 通过“投放”活动向主管发送消息。

要监视一组工作流的状态，您需要执行以下步骤：

1. 创建监视工作流。
1. 编写JavaScript以确定工作流是暂停、停止还是出错。
1. 创建 **[!UICONTROL Test]** 活动。
1. 准备投放模板。

>[!NOTE]
>
>除了工作流之外，活动工 **作流热图** 还允许您详细分析当前运行的工作流。 For more on this, refer to the [dedicated section](../../workflow/using/heatmap.md).
>
>有关如何监视 **工作流执行情况的详细**，请参 [阅本节](../../workflow/using/monitoring-workflow-execution.md)。

## 第1步：创建监视工作流 {#step-1--creating-the-monitoring-workflow}

我们要监视的工作流文件夹是“管理”>“ **生产”** >“技术工作流”节 **点中存储的“CustomWorkflow** ”文件夹。 此文件夹包含一组业务工作流。

监 **视工作流** 存储在技术工作流文件夹的根目录下。 使用的标签 **为“监视”**。

以下模式显示了活动的顺序：

![](assets/uc_monitoring_workflow_overview.png)

此工作流由以下部分组成：

* “ **开始** ”。
* 一个 **“JavaScript代码** ”活动，负责分析业务工作流文件夹。
* “测 **试”活动** ，用于向主管发送投放或重新开始工作流。
* 负责 **消息布局** 的“投放”活动。
* “等 **待”活动** ，控制工作流迭代之间的提前期。

## 第2步：编写JavaScript {#step-2--writing-the-javascript}

JavaScript代码的第一部分与一个 **查询符(queryDef)** ，它允许您用“pause”(@state == 13)、“error”(@failed == 1)或“stopped”(@state == 20)状态标识工作流符。

在 **以下条件下** ，将给出要监视的工作流文件夹的内部名称：

```
<condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
```

```
var strError = "";
var strPaused = "";
var strStop = "";

var queryWkfError = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
      <node expr="@state"/>
      <node expr="@label"/>
      <node expr="@failed"/>
      <node expr="@state"/>   
    </select>
    <where id="12837805386">
      <condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
        <condition boolOperator="AND" internalId="2">
          <condition boolOperator="OR" expr="@state = 20" internalId="3"/>
          <condition expr="@state = 13" internalId="4"/>
        </condition>  
    </where>
  </queryDef>
);
var ndWkfError = queryWkfError.ExecuteQuery(); 
```

JavaScript代码的第二部分允许您根 **据在查询期间恢复的状态** ，为每个工作流显示一条消息。

>[!NOTE]
>
>创建的字符串必须加载到工作流的事件变量中。

```
for each ( var wkf in ndWkfError.workflow ) 
{
  if ( wkf.@state == 13 )  // Status 13 = paused
  {
    if ( wkf.@failed == 1 )
      strError += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
    else
      strPaused += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
  }
  
  if ( wkf.@state == 20 )  // Status 20 = stop
    strStop += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
}

vars.strWorkflowError = strError;
vars.strWorkflowPaused = strPaused;
vars.strWorkflowStop = strStop;
```

## 第3步：创建“测试”活动 {#step-3--creating-the--test--activity}

“测试”活动允许您根据“等待”活动确定是否需要发送投放或监视工作流是否需要运行另一个周期。

如果三个投放变 **量“vars.strWorkflowError”、“vars.strWorkflowPaused”或“vars.strWorkflowStop”中的至少一个事件为非无效，则向主管发送。**

![](assets/uc_monitoring_workflow_test.png)

“等待”活动可以配置为定期重新开始监视工作流。 对于此用例， **等待时间设置为1小时**。

![](assets/uc_monitoring_workflow_attente.png)

## 第4步：准备投放 {#step-4--preparing-the-delivery}

“投放”活动基于存储在“资 **源** ”>“模 **板”>“投放模板”节点中的** 投放模板。

此模板必须包括：

* **主管的电子邮件地址**。
* **用于插入个** 性化文本的HTML内容。

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   声明的三个变量(WF_Stop、WF_Paused、WF_Error)与三个工作流事件变量匹配。

   这些变量必须在投放模板属 **性的** “变量”选项卡中声明。

   要恢 **复工作流事件变量的内容**，您需要声明特定于投放的变量，该变量将使用JavaScript代码返回的值进行初始化。

   投放模板具有以下内容：

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

创建并批准模板后，您需要将投放 **活动配** 置：

* 将“投放”活动链接到先前创建的投放模板。
* 将工作流的事件变量链接到特定于投放模板的变量。

多次-单击 **投放** 活动，然后选择以下选项：

* 投放:选 **择“新建”、从模板创建**，然后选择之前创建的投放模板。
* 对于“ **收件人”和** “内容”字 **段，在投放中选择“指定”**。
* 要执行的操作：选择 **准备和开始**。
* 取消选中“ **处理错误** ”选项。

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* 转到 **投放** 活动的“脚本”选 **项卡** ，通过个性化字段菜 **单添加三个字** 符串类型变量。

   ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

   ![](assets/uc_monitoring_workflow_linkvariables.png)

   声明的三个变量是：

   ```
   delivery.variables._var[0].stringValue = vars.strWorkflowError;
   delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
   delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
   ```

启动此监视工作流后，它会向收件人发送以下摘要：

![](assets/uc_monitoring_workflow_mailfinal.png)

