---
product: campaign
title: 监督工作流
description: 了解如何监督Campaign工作流
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: ca6d4bf4-7b3a-4d36-9fc3-0b83531d0132
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---

# 用例：监控工作流{#supervising-workflows}

此用例详细介绍了如何创建工作流，以便您监视“已暂停”、“已停止”或“有错误”的一组工作流的状态。

其目的是：

* 使用工作流监视一组业务工作流。
* 通过“投放”活动向主管发送消息。

要监视一组工作流的状态，您需要执行以下步骤：

1. 创建监控工作流。
1. 编写JavaScript以确定工作流是暂停、停止还是出错。
1. 创建&#x200B;**[!UICONTROL Test]**&#x200B;活动。
1. 准备投放模板。

>[!NOTE]
>
>除了工作流之外，Campaign **工作流热图**&#x200B;还允许您详细分析当前运行的工作流。 有关更多信息，请参阅[专用部分](../../workflow/using/heatmap.md)。
>
>有关如何&#x200B;**监控工作流执行的更多信息**，请参阅[此部分](../../workflow/using/monitoring-workflow-execution.md)。

## 步骤1:创建监控工作流{#step-1--creating-the-monitoring-workflow}

我们要监视的工作流文件夹是存储在&#x200B;**管理>生产>技术工作流**&#x200B;节点中的&#x200B;**&quot;CustomWorkflows&quot;**&#x200B;文件夹。 此文件夹包含一组业务工作流。

**监控工作流**&#x200B;存储在技术工作流文件夹的根目录下。 使用的标签是&#x200B;**&quot;Monitoring&quot;**。

以下架构显示了活动的顺序：

![](assets/uc_monitoring_workflow_overview.png)

此工作流由以下部分组成：

* a **&quot;Start&quot;**&#x200B;活动。
* **&quot;JavaScript代码&quot;**&#x200B;活动，负责分析业务工作流文件夹。
* **&quot;Test&quot;**&#x200B;活动，用于向主管发送投放或重新启动工作流。
* **&quot;投放&quot;**&#x200B;活动，负责消息布局。
* **&quot;Wait&quot;**&#x200B;活动，用于控制工作流迭代之间的提前期。

## 步骤2:编写JavaScript {#step-2--writing-the-javascript}

JavaScript代码的第一部分与&#x200B;**查询(queryDef)**&#x200B;一致，通过该查询，您可以使用“pause”(@state == 13)、“error”(@failed = 1)或“stopped”(@state == 20)状态来识别工作流。

在以下条件下，将提供要监视的工作流文件夹的&#x200B;**内部名称**:

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

JavaScript代码的第二部分允许您&#x200B;**根据查询期间恢复的状态显示每个工作流**&#x200B;的消息。

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

## 步骤3:创建“测试”活动{#step-3--creating-the--test--activity}

通过“测试”活动，您可以确定是否需要发送投放，或监控工作流是否需要基于“等待”活动运行另一个周期。

如果三个事件变量“vars.strWorkflowError”、“vars.strWorkflowPaused”或“vars.strWorkflowStop”中的至少一个事件变量为非void，则会向主管&#x200B;**发送投放。**

![](assets/uc_monitoring_workflow_test.png)

可以将“等待”活动配置为定期重新启动监控工作流。 对于此用例，将&#x200B;**等待时间设置为1小时**。

![](assets/uc_monitoring_workflow_attente.png)

## 步骤4:准备投放{#step-4--preparing-the-delivery}

“投放”活动基于存储在&#x200B;**资源>模板>投放模板**&#x200B;节点中的&#x200B;**投放模板**。

此模板必须包括：

* **主管的电子邮件地址**。
* **用于** 插入个性化文本的HTML内容。

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   声明的三个变量(WF_Stop、WF_Paused、WF_Error)与三个工作流事件变量匹配。

   必须在投放模板属性的&#x200B;**Variables**&#x200B;选项卡中声明这些变量。

   要恢复&#x200B;**工作流事件变量**&#x200B;的内容，您需要声明特定于投放的变量，这些变量将使用JavaScript代码返回的值进行初始化。

   投放模板具有以下内容：

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

创建并批准模板后，您需要将&#x200B;**Delivery**&#x200B;活动配置为：

* 将“投放”活动链接到之前创建的投放模板。
* 将工作流的事件变量链接到特定于投放模板的事件变量。

双击&#x200B;**Delivery**&#x200B;活动，然后选择以下选项：

* 投放：选择&#x200B;**新建，从模板**&#x200B;创建，然后选择之前创建的投放模板。
* 对于&#x200B;**收件人和内容**&#x200B;字段，选择&#x200B;**在投放中指定**。
* 要执行的操作：选择&#x200B;**准备并启动**。
* 取消选中&#x200B;**Process errors**&#x200B;选项。

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* 转到&#x200B;**Delivery**&#x200B;活动的&#x200B;**Script**&#x200B;选项卡，通过个性化字段菜单添加三个&#x200B;**字符串**&#x200B;类型变量。

   ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

   ![](assets/uc_monitoring_workflow_linkvariables.png)

   声明的三个变量为：

   ```
   delivery.variables._var[0].stringValue = vars.strWorkflowError;
   delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
   delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
   ```

启动此监控工作流后，它会向收件人发送以下摘要：

![](assets/uc_monitoring_workflow_mailfinal.png)
