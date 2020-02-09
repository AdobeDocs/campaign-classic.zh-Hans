---
title: 批准
seo-title: 批准
description: 批准
seo-description: null
page-status-flag: never-activated
uuid: 49285790-5aa7-4e15-a657-42e4f78be518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a0090c78-5873-446d-8d5f-b0f94ff5d373
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 批准{#approval}

“批 **准** ”任务需要操作员的参与。 操作员将获得一个任务，并可以通过电子邮件、电子邮件中链接的网页或控制台进行回复。

## 任务分配 {#task-assignment}

默认情况下，批准会分配给一组操作员。 此组表示角色，例如“新闻稿内容组”或“新闻稿定位组”。 组中的每个运算符都可以回答，但只考虑第一个回复（多次批准的情况除外）。

如有必要，您可以将批准任务分配给单个运算符或过滤器定义的一组运算符。

* 要选择单个运算符，请在字 **[!UICONTROL Operator]** 段中选 **[!UICONTROL Assignment type]** 择值，然后在字段的下拉列表中选择相关的运 **[!UICONTROL Assignee]** 算符。

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >只有选定的操作员才有权批准该任务。

* 您可以定义用于筛选批准运算符的查询。 为此，请在字段中 **[!UICONTROL Filter]** 选择值， **[!UICONTROL Assignment type]** 然后单击链接以 **[!UICONTROL Advanced parameters...]** 定义筛选条件，如以下示例所示：

   ![](assets/s_advuser_validation_box_filter.png)

在单次批准的情况下，激活与操作者选择相对应的转换，并完成任务：其他运营商无法回复。

在多个批准的情况下，启用与每个操作者的选择相对应的过渡。 当组的所有操作员都已回复时，或当任务过期时，任务即完成。

此活动不会阻止处理，并且工作流可以在等待回复时执行其他任务。

操作员可以从控制台批准分配给该操作员的任务。 具有管理员权限的操作员可以查看和删除分配给任何操作员的任务，但无法回复这些任务。

修改活动的标题或消息正文不会影响当前任务，但是，修改可能的选择会直接影响当前任务，这些任务会自动继承新的选择列表。

**可以从** “节点”访问批准类型 **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 任务：运营商可以直接通过此视图访问批准表单。

![](assets/s_advuser_validation_from_console.png)

## 属性 {#properties}

自定义变量可用于发送给审阅者的消息中。 可以将其插入到消息标题或正文中。

![](assets/edit_validation.png)

此 **[!UICONTROL Title]** 字段包含消息的标题：这是发送的电子邮件的主题。 标题和消息正文是JavaScript模板，因此可以包含根据工作流上下文计算的值。

编辑器的下部分允许您定义可能答案的列表。 每个答案都对应一个过渡。 名称是内部标识符，标签是将在选择列表中显示的文本。

单击链 **[!UICONTROL Advanced parameters...]** 接以选择要用于通知运营商的交付模板。 默认模板（内部名称&#39;notifyAssignee&#39;）会获取标题和消息，并添加指向用于回答的网页的链接。

可以修改此模板以个性化消息布局，但最好制作副本。 不能修改定位机制（外部文件，目标映射），因为通知要正确运行是必需的。

定义批准中显示了一个 [批准示例](../../workflow/using/executing-a-workflow.md#defining-approvals)。

## 输出参数 {#output-parameters}

* **[!UICONTROL response]**

   与响应相关的注释

* **[!UICONTROL responseOperator]**

   响应的操作符的标识符。 此字段是数值，但是是字 **[!UICONTROL String]** 段。

