---
product: campaign
title: 定义审批
description: 通过审批，操作员能够做出管理工作流的决策或确认其继续执行
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# 定义审批 {#defining-approvals}

通过审批，操作员能够做出管理工作流的决策或确认其继续执行。

系统会向一组运算符发送消息，工作流会等待响应后再恢复。 工作流未停止，并且可以执行其他操作。 例如，可能有多个同时等待批准。

批准可以包含多个选项供操作员选择。 但是，可以将选择数限制为一个，以便将要执行的任务提交给操作员，例如执行定位。 然后，操作员可以在执行任务后做出响应（该过程随后恢复）。 以下示例说明了这些类型的批准：

![](assets/validation-1.png)

在操作中，所有需要批准的阶段都基于相同的原则。

![](assets/validation-1-in-op.png)

批准示例可在此[部分](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)中找到。

操作员可以采取以下两种方式之一做出响应：使用电子邮件中链接的网页进行验证，或通过控制台进行验证。

>[!NOTE]
>
>保存响应后，无法修改该响应。

## 发送电子邮件 {#sending-emails}

可能会收到一条批准消息，其中包含一个指向网页的链接，可通过该网页做出响应。 要使目标操作员接收批准电子邮件，操作员电子邮件地址必须填写完整。 如果情况并非如此，则运算符必须使用控制台做出响应

此[部分](../../platform/using/access-management.md)中详细描述了操作员管理。

批准电子邮件会持续发送。 默认投放模板为&#x200B;**[!UICONTROL notifyAssignee]**:该文件夹保存在&#x200B;**[!UICONTROL Administration > Campaign management > Technical delivery templates]**&#x200B;文件夹中。 此方案可以自定义，还建议制作副本并更改每个活动的模板。

通过此模板创建的投放存储在&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**&#x200B;文件夹中。

## 通过控制台{#approval-via-the-console}进行批准

在操作中，要批准的元素显示在营销活动仪表板上。

对于技术工作流，可以从&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]**&#x200B;文件夹的树结构访问用户可以批准的任务。

![](assets/validation-node.png)

## 群组 {#groups}

批准被分配给一组运算符、单个运算符或通过筛选条件选择的一组运算符。

1. 就最简单的批准形式而言，一旦操作员做出响应，任务就会完成。 任何其他尝试做出响应的操作员都会收到通知，告知某人已经执行了该操作。
1. 有关多个批准，请参阅[多个批准](#multiple-approval)。

审批的操作员组应指定为角色或职能，而不是指定个人。 例如，“促销活动预算”组比“Harry&#39;s组”更可取。 我们建议一个组中至少有两个人可以批准一项任务。 这样，如果一个人缺席，另一个人可以做出响应。

## 过期 {#expirations}

过期是在不同类型的活动（特别是在批准中）中使用的特定过渡。 您可以使用过期功能在给定时间后触发某个操作，而无需响应。 例如，还可以使用它来跟踪工作流，并将批准分配给其他组。

利用活动批准属性中的第二个选项卡，可定义一个或多个过期日期。 事实上，您可以定义多种过期类型。

![](assets/expiration.png)

要添加新过期，请单击&#x200B;**[!UICONTROL Add]**。 过渡会添加到创建的每个过期日期。 您可以：

* 通过单击列表中的单元格（或按F2）直接修改典型参数，
* 或者，单击&#x200B;**[!UICONTROL Detail...]**&#x200B;按钮以编辑表达式。

>[!NOTE]
>
>无需指定过期的顺序，因为过期的处理顺序按时间顺序排列。

当延迟超时时，**[!UICONTROL Do not terminate the task]**&#x200B;选项会使批准保持活动状态。 通过此模式，可以在保持批准活动状态时管理提醒：操作员仍可以响应。 默认情况下，此选项处于禁用状态，这意味着任务在过期时被视为已完成，并且操作员可能不再做出响应。

您可以创建四种类型的过期日期：

* **任务开始后延迟**:到期时间的计算方式是向批准激活的日期添加指定的时间长度。
* **指定日期后的延迟**:过期时间的计算方式是向指定的日期添加一个时间长度。
* **在给定日期之前延迟**:过期时间的计算方式是从您指定的日期减去一段时间。
* **由脚本计算的到期时间**:过期时间是使用JavaScript计算的。

   以下示例计算投放开始日期24小时之前的过期时间（由&#x200B;**vars.deliveryId**&#x200B;标识）：

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

## 多次批准{#multiple-approval}

多个批准是一种机制，允许所有批准操作员做出响应。 为每个响应激活一个过渡。

多项批准对投票或调查机制非常有用。 您可以通过添加截止时间来计算答案并在给定时间段后处理其结果。

## 所需权限{#required-rights}

群组中的操作员必须至少具有以下权限才能响应批准请求：

* 工作流的写入权限。
* 对包含待批准任务的文件夹的读取和写入权限。

“工作流执行”组具有这些权限。 添加到此组的操作员有权响应批准请求。
