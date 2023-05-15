---
product: campaign
title: 使用本地审批活动
description: 了解如何使用本地批准活动
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: cc29eec9-9c97-4d1b-9567-2581154d7b3f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1272'
ht-degree: 2%

---

# 使用本地审批活动{#using-the-local-approval-activity}



的 **[!UICONTROL Local approval]** 通过将活动集成到定位工作流，您可以在发送投放之前设置收件人批准流程。

>[!CAUTION]
>
>要使用此功能，您需要购买分布式营销模块，该模块是一个Campaign选项。 请核实您的许可协议。

要设置此用例，我们创建了以下定位工作流：

![](assets/local_validation_workflow.png)

本地批准流程的主要步骤是：

1. 定位后产生的人口可能会因 **[!UICONTROL Split]** 使用数据分发模型键入活动。

   ![](assets/local_validation_intro_1.png)

1. 的 **[!UICONTROL Local approval]** 然后，活动接管并向每个本地主管发送通知电子邮件。 在每个本地主管批准分配给他们的收件人之前，活动将被暂停。

   ![](assets/local_validation_intro_4.png)

1. 一旦达到批准截止日期，工作流程将再次启动。 在本例中， **[!UICONTROL Delivery]** 活动开始，并将投放发送到批准的目标。

   >[!NOTE]
   >
   >到达截止时间后，将排除未获得批准的收件人。

   ![](assets/local_validation_intro_6.png)

1. 几天后，第二个 **[!UICONTROL Local approval]** 类型活动会向每个本地主管发送通知电子邮件，其中包含其联系人执行的操作（点击次数、打开次数等）的摘要。

   ![](assets/local_validation_intro_5.png)

## 步骤1:创建数据分发模板 {#step-1--creating-the-data-distribution-template-}

利用数据分发模板，可限制根据数据分组进行定位所产生的群体，同时允许您将每个值分配给本地主管。 在本例中，我们定义了 **[!UICONTROL Email address domain]** 字段作为分发字段，并为每个本地主管分配了域

有关创建数据分发模板的更多信息，请参阅 [限制每个数据分发的子集记录数](split.md#limiting-the-number-of-subset-records-per-data-distribution).

1. 要创建数据分发模板，请转到 **[!UICONTROL Resources > Campaign management > Data distribution]** 节点，单击 **[!UICONTROL New]**.

   ![](assets/local_validation_data_distribution_1.png)

1. 选择 **[!UICONTROL General]** 选项卡。

   ![](assets/local_validation_data_distribution_2.png)

1. 输入 **[!UICONTROL Label]** 和 **[!UICONTROL Distribution context]**. 在本例中，我们选择了 **[!UICONTROL Recipient]** 定位模式和 **[!UICONTROL Email domain]** 字段。 收件人列表将按域进行划分。
1. 在 **[!UICONTROL Distribution type]** 字段中，选择目标限制值在 **[!UICONTROL Distribution]** 选项卡。 在这里，我们选择了 **[!UICONTROL Percentage]**.
1. 在 **[!UICONTROL Approval storage]** 字段中，输入与正在使用的定位模式匹配的批准的存储模式。 下面我们将使用默认存储架构： **[!UICONTROL Local approval of recipients]**.
1. 然后，单击 **[!UICONTROL Advanced parameters]** 链接。

   ![](assets/local_validation_data_distribution_3.png)

1. 保留 **[!UICONTROL Approve the targeted messages]** 选项，以便从要批准的收件人列表中预先选择所有收件人。
1. 在 **[!UICONTROL Delivery label]** 字段中，我们保留了默认表达式（投放的计算字符串）。 投放的标准标签将用在反馈通知中。
1. 在 **[!UICONTROL Grouping field]** 部分，我们已选择 **[!UICONTROL Gender]** 字段作为用于在批准和反馈通知中显示收件人的分组字段。
1. 在 **[!UICONTROL Edit targeted messages]** 部分，我们已选择 **[!UICONTROL Edit recipients]** web应用程序和 **[!UICONTROL recipientId]** 参数。 在批准和反馈通知中，收件人是可单击的，并将指向Web应用程序的URL。 其他URL参数将为 **[!UICONTROL recipientId]**.
1. 然后，单击 **[!UICONTROL Distribution]** 选项卡。 对于每个域，输入以下字段：

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**:输入域名的值。
   * **[!UICONTROL Percentage / Fixed]**:对于每个域，输入最大值。 要将投放发送到的收件人数量。 在本例中，我们希望将投放限制为每个域10%。
   * **[!UICONTROL Label]**:输入要在批准和反馈通知中显示的域的标签。
   * **[!UICONTROL Group or operator]**:选择分配给域的运算符或运算符组。

      >[!CAUTION]
      >
      >确保为运算符分配了相应的权限。

## 步骤2:创建定位工作流 {#step-2--creating-the-targeting-workflow}

要设置此用例，我们创建了以下定位工作流：

![](assets/local_validation_workflow.png)

添加了以下活动：

* 两个 **[!UICONTROL Query]** 活动，
* 一个 **[!UICONTROL Intersection]** 活动，
* 一个 **[!UICONTROL Split]** 活动，
* 一个 **[!UICONTROL Local approval]** 活动，
* 一个 **[!UICONTROL Delivery]** 活动，
* 一个 **[!UICONTROL Wait]** 活动，
* 一秒 **[!UICONTROL Local approval]** 活动，
* 一个 **[!UICONTROL End]** 活动。

### 查询、交集和拆分 {#queries--intersection-and-split}

上游定位由两个查询组成，一个交集，一个拆分。 通过使用 **[!UICONTROL Split]** 活动。

有关配置拆分活动的更多信息，请参阅 [拆分](split.md). 有关创建数据分发模板的详情，请参阅 [限制每个数据分发的子集记录数](split.md#limiting-the-number-of-subset-records-per-data-distribution).

如果不想限制查询中的群体，则不必使用 **[!UICONTROL Query]**, **[!UICONTROL Intersection]**&#x200B;和 **[!UICONTROL Split]** 活动。 在这种情况下，请在第一个 **[!UICONTROL Local approval]** 活动。

1. 在 **[!UICONTROL Record count limitation]** 选择 **[!UICONTROL Limit the selected records]** 选项，然后单击 **[!UICONTROL Edit]** 链接。

   ![](assets/local_validation_split_1.png)

1. 选择 **[!UICONTROL Keep only the first records after sorting]** 选项并单击 **[!UICONTROL Next]**.

   ![](assets/local_validation_split_1bis.png)

1. 在 **[!UICONTROL Sort columns]** 部分，添加要应用排序的字段。 在这里，我们选择了 **[!UICONTROL Email]** 字段。 单击 **[!UICONTROL Next]**。

   ![](assets/local_validation_split_2.png)

1. 选择 **[!UICONTROL By data distribution]** 选项，选择之前创建的分发模板(请参阅 [步骤1:创建数据分发模板](#step-1--creating-the-data-distribution-template-))并单击 **[!UICONTROL Finish]**.

   ![](assets/local_validation_split_3.png)

在分发模板中，我们选择将群体限制为每个分组值10%，该值与工作流中显示的值（340作为输入，34作为输出）一致。

![](assets/local_validation_intro_1.png)

### 批准通知 {#approval-notification}

的 **[!UICONTROL Local approval]** 活动允许您向每个本地主管发送通知。

有关配置的更多信息 **[!UICONTROL Local approval]** 活动，请参阅 [本地批准](local-approval.md).

![](assets/local_validation_workflow_2.png)

需要输入以下字段：

1. 在 **[!UICONTROL Action to execute]** 部分中，选择 **[!UICONTROL Target approval notification]** 选项。
1. 在 **[!UICONTROL Distribution context]** 部分中，选择 **[!UICONTROL Specified in the transition]** 选项。

   如果不想限制目标群体，请选择 **[!UICONTROL Explicit]** 选项，然后输入之前在 **[!UICONTROL Data distribution]** 字段。

1. 在 **[!UICONTROL Notification]** 部分，选择投放模板和用于通知电子邮件的主题。 在本例中，我们选择了默认模板： **[!UICONTROL Local approval notification]**.
1. 在 **[!UICONTROL Approval schedule]** 部分，我们保留了默认的批准截止时间（3天）并添加了提醒。 交货将在批准后3天后离开。 在达到批准截止时间后，未获得批准的收件人不会被定位。

由 **[!UICONTROL Local approval]** 对本地主管的活动如下：

![](assets/local_validation_intro_2.png)

### 等待 {#wait}

等待活动允许您推迟开始第二个将发送投放反馈通知的本地批准活动。 在 **[!UICONTROL Duration]** 字段，我们已输入 **[!UICONTROL 5d]** 值（5天）。 反馈通知中将包含收件人在发送投放后5天内执行的操作。

![](assets/local_validation_workflow_3.png)

### 反馈通知 {#feedback-notification}

第二个 **[!UICONTROL Local approval]** 活动允许您向每个本地主管发送投放反馈通知。

![](assets/local_validation_workflow_4.png)

需要输入以下字段。

1. 在 **[!UICONTROL Action to execute]** ，选择 **[!UICONTROL Delivery feedback report]**.
1. 在 **[!UICONTROL Delivery]** ，选择 **[!UICONTROL Specified in the transition]**.
1. 在 **[!UICONTROL Notification]** 部分，选择投放模板和用于通知电子邮件的主题。

达到等待活动中配置的截止时间后，第二个 **[!UICONTROL Local approval]** 类型活动会向每个本地主管发送以下通知电子邮件：

![](assets/local_validation_intro_3.png)

### 管理员的批准跟踪 {#approval-tracking-by-the-administrator}

每次本地批准活动启动时，都会创建一个批准任务。 管理员可以控制这些批准任务中的每项。

转到营销活动的定位工作流，然后单击 **[!UICONTROL Local approval tasks]** 选项卡。

![](assets/local_validation_admin_1.png)

也可以通过 **[!UICONTROL Approval tasks]** 选项卡。

![](assets/local_validation_admin_2.png)

选择要监视的任务，然后单击 **[!UICONTROL Detail]** 按钮。 的 **[!UICONTROL General]** “本地批准”任务的选项卡，可查看有关该任务的信息。 如有必要，您可以更改批准和提醒日期。

![](assets/local_validation_admin_3.png)

此选项卡显示以下信息：

* 任务的标签及其ID
* 使用的分发模板
* 定向消息的数量
* 链接的工作流和营销活动
* 任务计划

的 **[!UICONTROL Distribution]** 选项卡，用于查看批准日志、其状态、定向消息数、批准日期以及批准投放的操作员。

![](assets/local_validation_admin_4.png)

选择批准日志，然后单击 **[!UICONTROL Detail]** 按钮以显示更多信息。 的 **[!UICONTROL General]** “本地批准日志”的选项卡可让您查看常规日志信息。 您还可以更改批准状态。

![](assets/local_validation_admin_5.png)

此选项卡显示以下信息：

* 链接的批准任务
* 批准状态(**[!UICONTROL Approved]** 或 **[!UICONTROL Pending]**)
* 使用的分发模板
* 批准的地方主管和批准日期
* 已定位和已批准的消息数

的 **[!UICONTROL Targeted]** 批准日志的选项卡会显示目标收件人的列表及其批准状态。 您可以根据需要更改此状态。

![](assets/local_validation_admin_6.png)
