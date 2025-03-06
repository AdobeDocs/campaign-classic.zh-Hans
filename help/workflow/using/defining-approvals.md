---
product: campaign
title: 定义审批
description: 通过批准，操作员能够做出管理工作流的决策或确认工作流的继续执行
feature: Approvals
hide: true
hidefromtoc: true
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 2%

---

# 定义审批 {#defining-approvals}



通过批准，操作员能够做出管理工作流的决策或确认工作流的继续执行情况。

消息将发送给一组操作员，工作流会等待响应后再继续。 工作流不会停止，并且可能会执行其他操作。 例如，可能有多个同步审批待处理。

批准可以包含多个选项供操作员选择。 但是，可以将选择数量限制为一个，以便向操作员提交要执行的任务，例如执行定位。 执行任务后，操作员可以响应（然后恢复流程）。 以下示例说明了这些类型的批准：

![](assets/validation-1.png)

在操作中，所有需要批准的阶段都基于相同的原则。

![](assets/validation-1-in-op.png)

在[此部分](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)中可找到批准示例。

操作员可通过以下两种方式之一进行响应：使用电子邮件中链接的网页进行验证，或通过控制台进行验证。

>[!NOTE]
>
>保存响应后，可能无法对其进行修改。

## 通过电子邮件审批 {#sending-emails}

可以接收包含指向网页的链接的批准消息，可以通过该链接进行响应。 对于要接收批准电子邮件的目标操作员，操作员电子邮件地址必须完整。 如果不是这种情况，操作员必须使用控制台进行响应

操作员管理在此[部分](../../platform/using/access-management.md)中详述。

批准电子邮件会持续发送。 默认投放模板为&#x200B;**[!UICONTROL notifyAssignee]**：它保存在&#x200B;**[!UICONTROL Administration > Campaign management > Technical delivery templates]**&#x200B;文件夹中。 此方案可以自定义，也建议制作副本并更改每个活动的模板。

通过此模板创建的投放存储在&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**&#x200B;文件夹中。

## 通过控制台审批 {#approval-via-the-console}

在操作中，要批准的元素会显示在活动仪表板上。

对于技术工作流，可以从&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]**&#x200B;文件夹中的树结构访问用户可以批准的任务。

![](assets/validation-node.png)

## 群组 {#groups}

批准被分配给通过筛选条件选择的一组操作员、单个操作员或一组操作员。

1. 对于最简单的批准形式，操作员作出响应后任务即告完成。 尝试响应的任何其他操作员都会收到通知，表明有人已经执行该操作。
1. 有关多个审批，请参阅[多个审批](#multiple-approval)。

要审批的操作员组应指定为角色或功能，而不是指名的人员。 例如，“营销活动预算”组比“哈里组”更可取。 我们建议一个组中至少有两名可批准任务的人员。 这样，如果其中一个组件缺席，另一个组件就可以做出回应。

## 过期时间 {#expirations}

过期是不同类型的活动（尤其是批准）中使用的特定过渡。 您可以使用过期时间在给定时间后触发操作，而无需响应。 例如，也可以使用此工作流来追踪工作流并将审批分配给其他组。

利用活动审批属性中的第二个选项卡，可定义一个或多个过期。 事实上，您可以定义多种到期类型。

![](assets/expiration.png)

若要添加新的过期时间，请单击&#x200B;**[!UICONTROL Add]**。 创建的每个过期都将添加一个过渡。 您可以：

* 通过单击列表中的单元格（或按F2）直接修改典型参数。
* 或单击&#x200B;**[!UICONTROL Detail...]**&#x200B;按钮编辑表达式。

>[!NOTE]
>
>无需指定过期顺序，因为过期时间按时间顺序处理。

当延迟超限时，**[!UICONTROL Do not terminate the task]**&#x200B;选项使审批保持活动状态。 利用此模式，可以在保持审批活动的情况下管理提醒：操作员仍然可以响应。 此选项默认处于禁用状态，这意味着任务在过期时被视为已完成，并且操作员可能不再响应。

您可以创建四种类型的过期日期：

* **任务开始后延迟**：计算到期时间的方法是将指定的时间长度添加到激活审批的日期。
* **在给定日期之后延迟**：过期时间是通过将时间长度添加到您指定的日期来计算的。
* **在给定日期之前延迟**：通过从您指定的日期中减去一个时间长度来计算到期时间。
* 由脚本计算的&#x200B;**过期**：使用JavaScript计算过期。

  以下示例计算在投放开始日期前24小时的过期时间（由&#x200B;**vars.deliveryId**&#x200B;标识）：

  ```
  var delivery = nms.delivery.get(vars.deliveryId)
  var expiration = delivery.scheduling.contactDate
  var oneDay = 1000*60*60*24
  expiration.setTime(expiration.getTime() - oneDay)
  return expiration
  ```

## 多重审批 {#multiple-approval}

多重批准是一种机制，它允许所有批准操作员做出响应。 为每个响应激活过渡。

多重批准对投票或调查机制很有用。 您可以通过添加截止日期来计数答案并在给定时间段后处理其结果。

## 所需权限 {#required-rights}

组中的操作员必须至少具有以下权限才能响应审批请求：

* 工作流的写入权限。
* 包含要批准的任务的文件夹的读写权限。

“工作流执行”组具有这些权限。 添加到此组的操作员有权响应审批请求。
