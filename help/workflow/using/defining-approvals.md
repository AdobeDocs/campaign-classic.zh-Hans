---
solution: Campaign Classic
product: campaign
title: 定义审批
description: 通过批准，操作员可以做出管理工作流的决策或确认其继续执行
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: ae342f41b9b74159607b313e1c29549b17488db5
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---


# 定义审批 {#defining-approvals}

通过批准，操作员可以做出管理工作流的决策或确认其继续执行。

消息将发送到操作员组，工作流会等待响应再恢复。 此工作流不会停止，并且可以执行其他操作。 例如，可能有多个同时等待批准。

批准可以包含多个选项供操作员选择。 但是，可以将选择数限制为一个，以便将要执行的任务提交给操作员，例如执行定位。 然后，操作员可以在执行任务后做出响应（然后恢复该过程）。 以下示例说明了这些类型的审批：

![](assets/validation-1.png)

在运营中，所有需要批准的阶段都基于相同的原则。

![](assets/validation-1-in-op.png)

此部分提供批准示 [例](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。

操作员可以通过以下两种方式之一做出响应：使用电子邮件中链接的网页或通过控制台进行验证。

>[!NOTE]
>
>保存响应后，不能修改响应。

## 发送电子邮件 {#sending-emails}

可以接收包含指向网页的链接的批准消息，可以通过该链接进行响应。 要使目标操作员接收批准电子邮件，操作员电子邮件地址必须完整。 如果不是，操作员必须使用控制台进行响应

操作员管理在本节中有 [详细介绍](../../platform/using/access-management.md)。

批准电子邮件会持续发送。 默认投放模板为 **[!UICONTROL notifyAssignee]**:它保存在文件夹 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 中。 可以自定义此方案，还建议制作副本并更改每个活动的模板。

通过此模板创建的投放存储在文 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** 件夹中。

## 通过控制台进行批准 {#approval-via-the-console}

在操作中，要批准的元素会显示在活动仪表板中。

对于技术工作流，可以从文件夹的树结构中访问用户可以批准的 **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** 任务。

![](assets/validation-node.png)

## 组 {#groups}

将批准分配给通过过滤条件选择的操作员组、单个操作符或一组操作符。

1. 对于最简单的批准形式，只要操作员做出响应，任务即完成。 任何其他试图回复的运营商都会收到有人已经这样做的通知。
1. 有关多个批准，请参阅 [多个批准](#multiple-approval)。

审批的操作员组应指定为角色或职能，而不是指定个人。 例如，“活动预算”组比“Harry&#39;s组”更可取。 我们建议在一个小组中至少有两个人可以批准任务。 这样，如果一个缺席，另一个可以做出回应。

## 过期 {#expirations}

过期是在不同类型的过渡中使用的特定活动，尤其是在批准中。 您可以在给定时间后使用过期来触发操作，而无需响应。 例如，还可以使用它来追踪工作流并将批准分配给其他组。

活动批准属性中的第二个选项卡允许您定义一个或多个过期时间。 事实上，您可以定义多个过期类型。

![](assets/expiration.png)

要添加新的过期，请单击 **[!UICONTROL Add]**。 过渡会添加到创建的每个过期。 您可以：

* 通过单击列表中的单元格（或按F2）直接修改典型参数，
* 或者，通过单击按钮编辑 **[!UICONTROL Detail...]** 表达式。

>[!NOTE]
>
>无需指定到期顺序，因为它们按时间顺序进行处理。

当延 **[!UICONTROL Do not terminate the task]** 迟超出时，此选项会使批准保持活动状态。 通过此模式，可以在保留审批活动状态时管理提醒：运营商仍然可以响应。 此选项默认处于禁用状态，这意味着任务在过期时被视为已完成，并且操作符可能不再响应。

您可以创建四种过期类型：

* **任务开始后延迟**:到期时间的计算方法是将指定的时间长度添加到激活批准的日期。
* **在指定日期后延迟**:到期时间通过向指定的日期添加时间长度来计算。
* **在给定日期之前延迟**:过期时间的计算方法是从您指定的日期减去一段时间。
* **按脚本计算过期时间**:过期时间是使用JavaScript计算的。

   以下示例计算投放开始之日（由vars.deliveryId标识）前24小 **时的到期**:

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

## 多次批准 {#multiple-approval}

多个批准是一种机制，使所有批准操作员都能做出响应。 为每个响应激活过渡。

多项批准对投票或调查机制有用。 您可以通过添加截止日期来计算答案并在给定时间段后处理其结果。

## 所需权限 {#required-rights}

群中的运营商必须至少拥有下列权利才能响应批准请求：

* 工作流的写入权限。
* 包含要批准的任务的文件夹的读写权限。

“工作流执行”组具有这些权限。 添加到此组的操作员有权响应批准请求。
