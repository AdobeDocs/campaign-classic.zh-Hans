---
title: 使用本地批准活动
description: 了解如何使用本地批准活动
page-status-flag: never-activated
uuid: 6003aaed-543d-4e6b-b1f2-ad4e9757bff3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: c143d8c3-c3ce-470c-8812-4b19cdb8afbf
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '1272'
ht-degree: 1%

---


# 使用本地批准活动{#using-the-local-approval-activity}

通过 **[!UICONTROL Local approval]** 集成到定位工作流中的活动，您可以在发送收件人之前设置投放批准流程。

>[!CAUTION]
>
>要使用此功能，您需要购买分布式营销模块，这是一个活动选项。 请核实您的许可协议。

要设置此用例，我们创建了以下定位工作流：

![](assets/local_validation_workflow.png)

本地批准流程的主要步骤是：

1. 由于使用数据分发模型的类型活动, **[!UICONTROL Split]** 因此可以限制定位产生的人口。

   ![](assets/local_validation_intro_1.png)

1. 活动 **[!UICONTROL Local approval]** 接管并向每个本地主管发送通知电子邮件。 活动将暂停，直到每个本地主管批准分配给他们的收件人。

   ![](assets/local_validation_intro_4.png)

1. 在达到批准截止日期后，工作流将再次开始。 在此示例中，活动 **[!UICONTROL Delivery]** 开始和投放会发送到已批准的目标。

   >[!NOTE]
   >
   >到期后，未获批准的收件人将被排除在定位之外。

   ![](assets/local_validation_intro_6.png)

1. 几天后，第二种类型的活动 **[!UICONTROL Local approval]** 会向每个本地主管发送通知电子邮件，其中包含其联系人（单击、打开等）所执行操作的摘要。

   ![](assets/local_validation_intro_5.png)

## 第1步：创建数据分发模板 {#step-1--creating-the-data-distribution-template-}

通过数据分配模板，您可以根据数据分组限制由定位产生的填充，同时使您能够将每个值分配给本地主管。 在此示例中，我们将字段定 **[!UICONTROL Email address domain]** 义为分发字段，并为每个本地主管分配了一个域

有关创建数据分发模板的详细信息，请 [参阅限制每个数据分发的子集记录数](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)。

1. 要创建数据分发模板，请转到节 **[!UICONTROL Resources > Campaign management > Data distribution]** 点并单击 **[!UICONTROL New]**。

   ![](assets/local_validation_data_distribution_1.png)

1. 选择 **[!UICONTROL General]** 选项卡。

   ![](assets/local_validation_data_distribution_2.png)

1. 输入 **[!UICONTROL Label]** 和 **[!UICONTROL Distribution context]**。 在此示例中，我们选择了定 **[!UICONTROL Recipient]** 位模式和字 **[!UICONTROL Email domain]** 段作为分发字段。 收件人的列表将按域划分。
1. 在字 **[!UICONTROL Distribution type]** 段中，选择目标限制值在选项卡中的表达 **[!UICONTROL Distribution]** 方式。 我们选了 **[!UICONTROL Percentage]**。
1. 在字 **[!UICONTROL Approval storage]** 段中，输入与使用中的定位存储匹配的审批的模式。 下面我们将使用默认存储模式: **[!UICONTROL Local approval of recipients]**.
1. 然后，单击 **[!UICONTROL Advanced parameters]** 链接。

   ![](assets/local_validation_data_distribution_3.png)

1. 保持选 **[!UICONTROL Approve the targeted messages]** 中此选项，以便从要批准的收件人的列表中预先选择所有收件人。
1. 在字 **[!UICONTROL Delivery label]** 段中，我们保留了默认表达式(投放的计算字符串)。 反馈通知中将使用投放的标准标签。
1. 在部 **[!UICONTROL Grouping field]** 分中，我们选择了该 **[!UICONTROL Gender]** 字段作为分组字段，以在审批和反馈通知中显示收件人。
1. 在部 **[!UICONTROL Edit targeted messages]** 分中，我们选择了Web应 **[!UICONTROL Edit recipients]** 用程序和参 **[!UICONTROL recipientId]** 数。 在批准和反馈通知中，收件人可以单击并指向Web应用程序的URL。 其他URL参数将为 **[!UICONTROL recipientId]**。
1. 然后单击选 **[!UICONTROL Distribution]** 项卡。 对于每个域，输入以下字段：

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**:输入域名的值。
   * **[!UICONTROL Percentage / Fixed]**:对于每个域，输入max。 要将收件人发送到的投放数。 在此示例中，我们希望将投放限制为每个域10%。
   * **[!UICONTROL Label]**:输入要在批准和反馈通知中显示的域的标签。
   * **[!UICONTROL Group or operator]**:选择分配给域的运算符或操作员组。

      >[!CAUTION]
      >
      >确保已为操作员分配了适当的权限。

## 第2步：创建定位工作流 {#step-2--creating-the-targeting-workflow}

要设置此用例，我们创建了以下定位工作流：

![](assets/local_validation_workflow.png)

添加了以下活动:

* Two **[!UICONTROL Query]** activities,
* 一个 **[!UICONTROL Intersection]** 活动,
* 一个 **[!UICONTROL Split]** 活动,
* 一个 **[!UICONTROL Local approval]** 活动,
* 一个 **[!UICONTROL Delivery]** 活动,
* 一个 **[!UICONTROL Wait]** 活动,
* 第二个 **[!UICONTROL Local approval]** 活动,
* 一个 **[!UICONTROL End]** 活动。

### 查询、交叉和拆分 {#queries--intersection-and-split}

上游目标定位由两个查询组成，一个交叉点和一个分割。 使用活动分发模板，可以限制定位 **[!UICONTROL Split]** 产生的人口。

有关配置拆分活动的详细信息，请参 [阅拆分](../../workflow/using/split.md)。 在限制每个数据分发的子集记录数 [目中详细介绍了数据分发模板的创建](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)。

如果您不想限制查询的人口，则不必使用、 **[!UICONTROL Query]**&#x200B;和 **[!UICONTROL Intersection]**&#x200B;活动 **[!UICONTROL Split]** 。 在这种情况下，请在第一个活动填写数据分发模 **[!UICONTROL Local approval]** 板。

1. 在部分 **[!UICONTROL Record count limitation]** 中，选择选 **[!UICONTROL Limit the selected records]** 项并单击链 **[!UICONTROL Edit]** 接。

   ![](assets/local_validation_split_1.png)

1. Select the **[!UICONTROL Keep only the first records after sorting]** option and click **[!UICONTROL Next]**.

   ![](assets/local_validation_split_1bis.png)

1. 在部 **[!UICONTROL Sort columns]** 分中，添加要应用排序的字段。 这里，我们选了 **[!UICONTROL Email]** 田。 单击 **[!UICONTROL Next]**.

   ![](assets/local_validation_split_2.png)

1. 选择选 **[!UICONTROL By data distribution]** 项，选择之前创建的分发模板(请参 [阅步骤1:创建数据分发模板](#step-1--creating-the-data-distribution-template-))，然后单击 **[!UICONTROL Finish]**。

   ![](assets/local_validation_split_3.png)

在分配模板中，我们选择将填充限制为每个分组值10%，这与工作流中显示的值（340作为输入，34作为输出）一致。

![](assets/local_validation_intro_1.png)

### 批准通知 {#approval-notification}

活动 **[!UICONTROL Local approval]** 允许您向每个本地主管发送通知。

有关配置活动的 **[!UICONTROL Local approval]** 详细信息，请参 [阅本地批准](../../workflow/using/local-approval.md)。

![](assets/local_validation_workflow_2.png)

需要输入以下字段：

1. In the **[!UICONTROL Action to execute]** section, select the **[!UICONTROL Target approval notification]** option.
1. In the **[!UICONTROL Distribution context]** section, select the **[!UICONTROL Specified in the transition]** option.

   如果不想限制目标人口，请在此处选择选 **[!UICONTROL Explicit]** 项，然后输入之前在字段中创建的分发模 **[!UICONTROL Data distribution]** 板。

1. 在部 **[!UICONTROL Notification]** 分中，选择投放模板和用于通知电子邮件的主题。 在此，我们选择了默认模板： **[!UICONTROL Local approval notification]**.
1. 在部 **[!UICONTROL Approval schedule]** 分中，我们保留了默认的批准截止日期（3天）并添加了提醒。 投放将于批准开始后3天离开。 一旦达到批准截止日期，未获批准的收件人就不会通过定位予以考虑。

活动向本地主管发送 **[!UICONTROL Local approval]** 的通知电子邮件如下：

![](assets/local_validation_intro_2.png)

### 等待 {#wait}

等待活动允许您推迟发送投放反馈通知的第二个本地批准活动的开始。 在字 **[!UICONTROL Duration]** 段中，我们输入 **[!UICONTROL 5d]** 了值（5天）。 收件人在发送投放后5天内执行的操作将包括在反馈通知中。

![](assets/local_validation_workflow_3.png)

### 反馈通知 {#feedback-notification}

第二个活动 **[!UICONTROL Local approval]** 允许您向每个本地主管发送投放反馈通知。

![](assets/local_validation_workflow_4.png)

需要输入以下字段。

1. 在部分 **[!UICONTROL Action to execute]** 中，选择 **[!UICONTROL Delivery feedback report]**。
1. 在部分 **[!UICONTROL Delivery]** 中，选择 **[!UICONTROL Specified in the transition]**。
1. 在部 **[!UICONTROL Notification]** 分中，选择投放模板和用于通知电子邮件的主题。

在等待活动中配置的截止期限到达后，第二类型 **[!UICONTROL Local approval]** 活动会向每个本地主管发送以下通知电子邮件：

![](assets/local_validation_intro_3.png)

### 管理员的批准跟踪 {#approval-tracking-by-the-administrator}

每次本地批准活动开始时，都会创建批准任务。 管理员可以控制这些批准任务。

转到活动的定位工作流，然后单击选 **[!UICONTROL Local approval tasks]** 项卡。

![](assets/local_validation_admin_1.png)

还可以通过数据分发模板的选项卡访 **[!UICONTROL Approval tasks]** 问本地批准任务的列表。

![](assets/local_validation_admin_2.png)

选择要监视的任务并单击 **[!UICONTROL Detail]** 按钮。 通 **[!UICONTROL General]** 过本地批准任务的选项卡，您可以视图任务的信息。 如有必要，您可以更改审批和提醒日期。

![](assets/local_validation_admin_3.png)

此选项卡显示以下信息：

* 任务的标签及其ID
* 使用的分发模板
* 目标消息数
* 链接的工作流和活动
* 任务计划

任务 **[!UICONTROL Distribution]** 的选项卡允许您视图批准日志、其状态、目标消息数、批准日期以及批准投放的操作员。

![](assets/local_validation_admin_4.png)

选择批准日志并单击按 **[!UICONTROL Detail]** 钮以显示详细信息。 本地 **[!UICONTROL General]** 批准日志的选项卡允许您视图一般日志信息。 您还可以更改批准状态。

![](assets/local_validation_admin_5.png)

此选项卡显示以下信息：

* 链接的批准任务
* 批准状态(**[!UICONTROL Approved]** 或 **[!UICONTROL Pending]**)
* 使用的分发模板
* 批准日期和批准日期的当地主管
* 已定位和批准的邮件数

批 **[!UICONTROL Targeted]** 准日志的选项卡显示目标收件人的列表及其批准状态。 您可以根据需要更改此状态。

![](assets/local_validation_admin_6.png)

