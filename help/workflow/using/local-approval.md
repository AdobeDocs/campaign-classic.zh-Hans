---
product: campaign
title: 本地审批
description: 本地审批
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 2d9cbfc8-1f99-4b38-8460-77c7c986e9ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# 本地审批{#local-approval}

![](../../assets/common.svg)

将&#x200B;**[!UICONTROL Local approval]**&#x200B;活动集成到定位工作流后，您可以在发送投放之前设置收件人批准流程。

![](assets/local_validation_0.png)

>[!CAUTION]
>
>要使用此活动，您需要购买“分布式营销”模块（即营销活动选项）。 请核实您的许可协议。

有关具有分发模板的&#x200B;**[!UICONTROL Local approval]**&#x200B;活动的示例，请参阅[使用本地批准活动](using-the-local-approval-activity.md)。

首先，输入活动的标签和&#x200B;**[!UICONTROL Action to execute]**&#x200B;字段：

![](assets/local_validation_1.png)

* 选择&#x200B;**[!UICONTROL Target approval notification]**&#x200B;选项，在投放前向本地主管发送通知电子邮件，要求他们批准分配给他们的收件人。

   ![](assets/local_validation_intro_2.png)

* **增量查询**:允许您执行查询并规划其执行。请参阅[增量查询](incremental-query.md)一节。

   ![](assets/local_validation_intro_3.png)

## Target批准通知 {#target-approval-notification}

在这种情况下，**[!UICONTROL Local approval]**&#x200B;活动位于上游定位和投放之间：

![](assets/local_validation_2.png)

在发出目标批准通知时要输入的字段包括：

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**:如果您 **[!UICONTROL Specified in the transition]** 使用类型活动来限 **[!UICONTROL Split]** 制目标群体，请选择选项。在这种情况下，分发模板会在拆分活动中输入。 如果不限制目标群体，请在此处选择&#x200B;**[!UICONTROL Explicit]**&#x200B;选项，然后在&#x200B;**[!UICONTROL Data distribution]**&#x200B;字段中输入分发模板。

   有关创建数据分发模板的更多信息，请参阅[限制每个数据分发的子集记录数](split.md#limiting-the-number-of-subset-records-per-data-distribution)。

* **[!UICONTROL Approval management]**

   * 选择投放模板以及用于电子邮件通知的主题。 默认模板可用：**[!UICONTROL Local approval notification]**。 您还可以添加将在批准和反馈通知中收件人列表上方显示的描述。
   * 指定与批准截止时间（从批准开始的日期或截止时间）对应的&#x200B;**[!UICONTROL Approval type]**。 在此日期，工作流将再次启动，并且定向中不会考虑未获批准的收件人。 发送通知后，活动将排入队列，以便本地主管可以批准其联系人。

      >[!NOTE]
      >
      >默认情况下，当批准流程启动时，该活动会暂停三天。

      您还可以添加一个或多个提醒，以告知本地主管截止时间即将到来。 为此，请单击&#x200B;**[!UICONTROL Add a reminder]**&#x200B;链接。

* **[!UICONTROL Complementary set]**:利用 **[!UICONTROL Generate complement]** 选项，可生成第二组，其中包含所有未批准的目标。

   >[!NOTE]
   >
   >默认情况下，此选项处于禁用状态。

## 投放反馈报告 {#delivery-feedback-report}

在这种情况下，**[!UICONTROL Local approval]**&#x200B;活动会放在投放之后：

![](assets/local_validation_4.png)

如果是投放反馈报告，则必须输入以下字段：

![](assets/local_validation_workflow_4.png)

* 如果在上一活动期间输入了投放，请选择&#x200B;**[!UICONTROL Specified in the transition]**&#x200B;选项。 选择&#x200B;**[!UICONTROL Explicit]**&#x200B;以指定本地批准活动中的投放。
* 选择投放模板和通知电子邮件的对象。 有一个默认模板：**[!UICONTROL Local approval notification]**。

## 示例：批准工作流投放 {#example--approving-a-workflow-delivery}

此示例展示了如何为工作流投放设置批准流程。 有关创建投放工作流的更多信息，请参阅[示例：投放工作流](delivery.md#example--delivery-workflow)部分。

操作员可以通过以下两种方式之一批准投放：使用电子邮件中链接的网页，或通过控制台进行访问。

* Web批准

   通过发送给管理员组操作员的电子邮件，您可以批准投放目标。 消息使用定义的文本，JavaScript表达式将被计算值替换（在本例中为“574”）

   要批准投放，请单击相关链接，然后登录到Adobe Campaign控制台。

   ![](assets/new-workflow-valid-webaccess.png)

   选择并单击&#x200B;**[!UICONTROL Submit]**&#x200B;按钮。

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* 通过控制台进行批准

   在树结构中，**[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]**&#x200B;节点包含要由当前连接的操作员批准的任务列表。 列表应显示一行。 双击此行以做出响应。 将显示以下窗口：

![](assets/new-workflow-7.png)

选择&#x200B;**是**，然后单击&#x200B;**[!UICONTROL Approve]**。 系统会显示一条消息，通知您响应已被记录。

返回到工作流屏幕：大约10秒后，该图表显示如下：

![](assets/new-workflow-8.png)

工作流已执行&#x200B;**[!UICONTROL Delivery control]**&#x200B;任务，在此例中，这意味着开始之前创建的投放。 工作流已完成，且未出现错误。
