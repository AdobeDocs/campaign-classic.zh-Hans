---
product: campaign
title: 监督工作流
description: 了解如何监督活动工作流
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: ca6d4bf4-7b3a-4d36-9fc3-0b83531d0132
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---

# 用例：监督工作流{#supervising-workflows}



此使用案例详细说明了如何创建工作流，以便您监控一组“已暂停”、“已停止”或“出现错误”的工作流的状态。

其目的是：

* 使用工作流监视一组业务工作流。
* 通过“投放”活动向主管发送消息。

要监视一组工作流的状态，您需要执行以下步骤：

1. 创建监控工作流。
1. 编写JavaScript以确定工作流是暂停、停止还是出现错误。
1. 创建 **[!UICONTROL Test]** 活动。
1. 准备投放模板。

>[!NOTE]
>
>除了工作流之外，Campaign **工作流热图** 允许您详细分析当前运行的工作流。 有关详情，请参阅 [专用部分](heatmap.md).
>
>了解关于如何操作的更多信息 **监测工作流的执行**，请参阅 [本节](monitoring-workflow-execution.md).

## 步骤1：创建监控工作流 {#step-1--creating-the-monitoring-workflow}

我们要监控的工作流文件夹是 **&quot;CustomWorkflows&quot;** 文件夹存储在 **管理>生产>技术工作流** 节点。 此文件夹包含一组业务工作流。

此 **监控工作流** 存储在Technical Workflows文件夹的根下。 使用的标签为 **“监控”**.

以下架构显示了活动的顺序：

![](assets/uc_monitoring_workflow_overview.png)

此工作流由以下部分组成：

* a **&quot;Start&quot;** 活动。
* a **&quot;JavaScript代码&quot;** 负责分析业务工作流文件夹的活动。
* a **&quot;测试&quot;** 活动，向主管发送投放或重新启动工作流。
* a **&quot;交付&quot;** 负责消息布局的活动。
* a **&quot;Wait&quot;** 控制工作流迭代之间提前期的活动。

## 步骤2：编写JavaScript {#step-2--writing-the-javascript}

JavaScript代码的第一部分与 **查询(queryDef)** 通过它，您可以识别具有“pause”(@state == 13)、“error”(@failed == 1)或“stopped”(@state == 20)状态的工作流。

此 **内部名称** 在以下条件下给出了要监视的工作流文件夹的：

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

JavaScript代码的第二部分允许您 **显示每个工作流的消息** 基于查询期间恢复的状态。

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

## 步骤3：创建“测试”活动 {#step-3--creating-the--test--activity}

通过“测试”活动，可决定是否需要发送投放，或者监控工作流是否需要根据“等待”活动运行另一个周期。

将投放发送给主管 **如果三个事件变量“vars.strWorkflowError”、“vars.strWorkflowPaused”或“vars.strWorkflowStop”中至少有一个是非空的。**

![](assets/uc_monitoring_workflow_test.png)

可以将“等待”活动配置为定期重新启动监控工作流。 对于此用例， **等待时间设置为1小时**.

![](assets/uc_monitoring_workflow_attente.png)

## 步骤4：准备投放 {#step-4--preparing-the-delivery}

“投放”活动基于 **投放模板** 存储在 **资源>模板>投放模板** 节点。

此模板必须包括：

* **主管的电子邮件地址**.
* **HTML内容** 用于插入个性化文本。

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   声明的三个变量(WF_Stop、WF_Paused、WF_Error)与三个工作流事件变量匹配。

   这些变量必须在 **变量** 选项卡中显示的投放模板属性。

   恢复 **工作流事件变量的内容**，则需要声明特定于投放的变量，这些变量将使用JavaScript代码返回的值进行初始化。

   投放模板包含以下内容：

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

创建并批准模板后，您需要配置 **投放** 活动目标：

* 将“投放”活动链接到之前创建的投放模板。
* 将工作流的事件变量链接到特定于投放模板的事件变量。

双击 **投放** 活动并选择以下选项：

* 投放：选择 **新建，从模板创建**，然后选择之前创建的投放模板。
* 对于 **收件人和内容** 字段，选择 **在投放中指定**.
* 要执行的操作：选择 **准备和开始**.
* 取消选中 **进程错误** 选项。

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* 转到 **脚本** 的选项卡 **投放** 活动，添加三个 **字符串** 通过个性化字段菜单键入变量。

   ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

   ![](assets/uc_monitoring_workflow_linkvariables.png)

   声明的三个变量是：

   ```
   delivery.variables._var[0].stringValue = vars.strWorkflowError;
   delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
   delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
   ```

启动此监控工作流后，它会向收件人发送以下摘要：

![](assets/uc_monitoring_workflow_mailfinal.png)
