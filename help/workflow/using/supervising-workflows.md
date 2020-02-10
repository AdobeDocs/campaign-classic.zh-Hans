---
title: 监督工作流
seo-title: 监督工作流
description: 监督工作流
seo-description: null
page-status-flag: never-activated
uuid: e16d1c40-50ae-4c3d-95df-fac62f987a15
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 978cbe62-f06a-46a6-b8a1-e30a65b8470a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# 监督工作流{#supervising-workflows}

此用例详细介绍了如何创建一个工作流，它允许您监视“已暂停”、“已停止”或“有错误”的一组工作流的状态。

其目的是：

* 使用工作流来监视一组业务工作流。
* 通过“交付”活动向主管发送消息。

要监视一组工作流的状态，您需要执行以下步骤：

1. 创建监视工作流。
1. 编写JavaScript以确定工作流是暂停、停止还是出错。
1. 创建活 **[!UICONTROL Test]** 动。
1. 准备交付模板。

>[!NOTE]
>
>除了工作流之外，Campaign **Workflow热图** ，还允许您详细分析当前运行的工作流。 For more on this, refer to the [dedicated section](../../workflow/using/heatmap.md).
>
>有关如何监视工 **作流执行的详细信息**，请参 [阅此部分](../../workflow/using/monitoring-workflow-execution.md)。

## 第1步：创建监视工作流 {#step-1--creating-the-monitoring-workflow}

我们要监视的工作流文件夹是“管理” **>“生产”>“技术工作流”节点中** 存储的“CustomWorkflows”文件夹 **** 。 此文件夹中包含一组业务工作流。

监 **视工作流** ，存储在Technical Workflows文件夹的根目录下。 使用的标签 **为“监视”**。

以下架构显示了活动的顺序：

![](assets/uc_monitoring_workflow_overview.png)

此工作流由以下几部分组成：

* “开 **始”活动** 。
* 负责 **分析业务工作流文件夹的** “JavaScript代码”活动。
* “测 **试”活动** ，用于向主管发送交付或重新启动工作流。
* 负责 **消息布局的** “交付”活动。
* “等 **待”活动** ，用于控制工作流迭代之间的提前期。

## 第2步：编写JavaScript {#step-2--writing-the-javascript}

JavaScript代码的第一部分与查询(queryDef) **** (它允许您用“pause”(@state == 13)、“error”(@failed == 1)或“stopped”(@state == 20)状态标识工作流。

要监 **视的工作流文件夹** ，在以下条件下会给出其内部名称：

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

JavaScript代码的第二部分允许您根据 **查询过程中恢复的状态为每个工作流显示一条消息** 。

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

“测试”活动允许您根据“等待”活动确定是否需要发送交付或监视工作流是否需要运行另一个周期。

如果三个事件变量“ **vars.strWorkflowError”、“vars.strWorkflowPaused”或“vars.strWorkflowStop”中的至少一个为非void，则发送给主管。**

![](assets/uc_monitoring_workflow_test.png)

“等待”活动可以配置为定期重新启动监视工作流。 对于此用例， **等待时间设置为1小时**。

![](assets/uc_monitoring_workflow_attente.png)

## 第4步：准备交付 {#step-4--preparing-the-delivery}

“交付”活动基于存储在“资源” **>“模板** ”>“交 **付模板”节点中的交付模板** 。

此模板必须包括：

* **主管的电子邮件地址**。
* **用于插入个性化文本的HTML内容** 。

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   声明的三个变量(WF_Stop、WF_Paused、WF_Error)与三个工作流事件变量匹配。

   这些变量必须在交付模板属性 **的** “变量”选项卡中声明。

   要恢 **复工作流事件变量的内容**，您需要声明特定于将使用JavaScript代码返回的值初始化的交付的变量。

   分发模板具有以下内容：

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

创建并批准模板后，您需要将“交付”活动配 **置为** :

* 将“交付”活动链接到先前创建的交付模板。
* 将工作流的事件变量链接到特定于交付模板的事件变量。

双击“交 **付** ”活动并选择以下选项：

* 交付：选 **择“新建”，从模板创建**，然后选择之前创建的交付模板。
* 对于“收件 **人”和“内容** ”字段 **，选择**&#x200B;分发中的“指定”。
* 要执行的操作：选择 **准备并开始**。
* 取消选中“ **处理错误** ”选项。

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* 转到“交 **付** ”活动的“脚本”选项卡 **，通过个性化字段菜****** 单添加三个字符串类型变量。

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

