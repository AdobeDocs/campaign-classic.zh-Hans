---
title: 本地批准
seo-title: 本地批准
description: 本地批准
seo-description: null
page-status-flag: never-activated
uuid: 4de59c8a-e229-4c8d-acab-2b116cafb70b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a223641e-93e1-42ef-bb6b-8e1a0f8f6a65
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 本地批准{#local-approval}

在集成到定位工作流中后，该活 **[!UICONTROL Local approval]** 动允许您在发送分发之前设置收件人批准流程。

![](assets/local_validation_0.png)

>[!CAUTION]
>
>要使用此活动，您需要购买“分布式营销”模块（即“营销活动”选项）。 请检查您的许可协议。

有关具有分发模 **[!UICONTROL Local approval]** 板的活动的示例，请参阅 [使用本地批准活动](../../workflow/using/using-the-local-approval-activity.md)。

首先，为活动和字段输入标 **[!UICONTROL Action to execute]** 签：

![](assets/local_validation_1.png)

* 选择选 **[!UICONTROL Target approval notification]** 项，在发送之前向本地主管发送通知电子邮件，要求他们批准分配给他们的收件人。

   ![](assets/local_validation_intro_2.png)

* **增量查询**:允许您执行查询并计划其执行。 请参阅增量 [查询部分](../../workflow/using/incremental-query.md) 。

   ![](assets/local_validation_intro_3.png)

## 目标批准通知 {#target-approval-notification}

在这种情况下，活 **[!UICONTROL Local approval]** 动将位于上游定位和交付之间：

![](assets/local_validation_2.png)

目标批准通知时要输入的字段包括：

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**:如果您 **[!UICONTROL Specified in the transition]** 使用类型活动来限制目 **[!UICONTROL Split]** 标人群，请选择此选项。 在这种情况下，分发模板将输入到拆分活动中。 如果不限制目标人群，请选择此 **[!UICONTROL Explicit]** 处的选项，然后在字段中输入分发模 **[!UICONTROL Data distribution]** 板。

   有关创建数据分发模板的详细信息，请参 [阅限制每个数据分发的子集记录数](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)。

* **[!UICONTROL Approval management]**

   * 选择用于电子邮件通知的传送模板和主题。 默认模板可用： **[!UICONTROL Local approval notification]**. 您还可以添加将在批准和反馈通知中收件人列表上方显示的描述。
   * 指定与 **[!UICONTROL Approval type]** 批准截止日期（从批准开始的日期或截止日期）对应的日期。 在此日期，工作流将再次启动，并且定位中不会考虑尚未批准的收件人。 发送通知后，活动将排队，以便本地主管可以批准其联系人。

      >[!NOTE]
      >
      >默认情况下，当启动批准流程时，活动将暂停三天。

      您还可以添加一个或多个提醒，以通知本地主管截止日期即将到来。 要执行此操作，请单击链 **[!UICONTROL Add a reminder]** 接。

* **[!UICONTROL Complementary set]**:通过 **[!UICONTROL Generate complement]** 此选项，您可以生成包含所有未批准目标的第二组。

   >[!NOTE]
   >
   >此选项默认处于禁用状态。

## 交付反馈报告 {#delivery-feedback-report}

在这种情况下，活 **[!UICONTROL Local approval]** 动将放在交付之后：

![](assets/local_validation_4.png)

如果是提交反馈报告，则必须输入以下字段：

![](assets/local_validation_workflow_4.png)

* 如果在 **[!UICONTROL Specified in the transition]** 上一个活动期间输入了交货，请选择此选项。 选择 **[!UICONTROL Explicit]** 以在本地批准活动中指定交付。
* 选择传送模板和通知电子邮件的对象。 默认模板： **[!UICONTROL Local approval notification]**.

## 示例：批准工作流交付 {#example--approving-a-workflow-delivery}

此示例说明如何为工作流交付设置审批流程。 有关创建交付工作流的详细信息，请参阅 [示例：“交付工作流](../../workflow/using/delivery.md#example--delivery-workflow) ”部分。

操作员可以通过以下两种方式之一批准交付：使用电子邮件中链接的网页，或通过控制台。

* Web批准

   发送给管理员组操作员的电子邮件允许您批准交付目标。 消息使用定义的文本，JavaScript表达式将替换为计算值（本例中为“574”）

   要批准分发，请单击相关链接并登录到Adobe Campaign控制台。

   ![](assets/new-workflow-valid-webaccess.png)

   做出选择，然后单击 **[!UICONTROL Submit]** 按钮。

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* 通过控制台进行批准

   在树结构中，节点 **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 包含要由当前连接的操作员批准的任务列表。 列表应显示一行。 双击此行以响应。 此时将显示以下窗口：

![](assets/new-workflow-7.png)

选择 **是**，然后单击 **[!UICONTROL Approve]**。 将显示一条消息，通知您已录制响应。

返回工作流屏幕：大约10秒后，图显示如下：

![](assets/new-workflow-8.png)

工作流已执行该任 **[!UICONTROL Delivery control]** 务，在这种情况下，这意味着开始之前创建的交付。 工作流已完成且未出错。
