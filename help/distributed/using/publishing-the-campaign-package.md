---
product: campaign
title: 发布活动包
description: 发布活动包
feature: Distributed Marketing
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 2%

---

# 发布活动包{#publishing-the-campaign-package}

![](../../assets/v7-only.svg)

中央实体操作员将希望提供的营销活动发布到 **[!UICONTROL list of campaign packages]**.

营销活动包列表中的营销活动包必须经过中央实体批准，才能发布。 为此，您可以通过 **[!UICONTROL Approval parameters]** 链接。

## 分配审阅人 {#assigning-a-reviewer}

要选择审阅人，请单击 **[!UICONTROL Approval parameters]** 链接，然后从下拉列表中选择相关的审阅人。

![](assets/s_advuser_mkg_dist_define_valid.png)

然后，您可以通过单击 **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

然后，通知消息会发送给审阅人以确认此营销活动包的可用性。 该消息包含一个链接，用于通过Web访问接受或拒绝批准。

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>在组织实体级别，您还可以指定审核者来批准订单。 有关更多信息，请参阅 [组织实体](about-distributed-marketing.md#organizational-entities).

## 添加其他审阅人 {#adding-other-reviewers}

您可以从 **[!UICONTROL Edit...]** 链接，可在营销活动包中找到 **[!UICONTROL Approval parameters...]** 选项卡。

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## 审批期 {#approval-periods}

默认情况下，自提交之日起三天内即会为审阅人提供审批服务。

在“编辑审阅人”窗口中，您还可以设置提醒，在营销活动包未获批准时发送一条或多条消息。 为此，请单击 **[!UICONTROL Add reminder]** 链接，然后 **[!UICONTROL Add]** 按钮。

提醒可在给定日期和/或 **x** 提交日期后的天数。 提醒类型可在提醒表的第一列中配置。 在以下示例中，审阅人将在29/01/2014日(即在 **[!UICONTROL Date]** 列的日期，以及在批准期结束前的一天（即在提交以供批准日期后的两天）的第二个提醒。

![](assets/s_advuser_mkg_dist_reminder_planning.png)

定义资源包并提交该资源包以供审批后，执行计划将显示在 **[!UICONTROL Audit]** 选项卡。 它显示基于先前配置计算的处理截止日期以及所有已配置提醒的日期。

## 通过Adobe Campaign控制台批准 {#approving-via-the-adobe-campaign-console}

如果未指定审核者，或者如果通知的操作员均未批准该包，则 **[!UICONTROL Approve the package]** 按钮，您可以直接从营销活动包进行批准 **[!UICONTROL Dashboard]** 或从包概述中。

![](assets/s_advuser_mkg_dist_valid_button.png)

批准后，营销活动会被发布并添加到列表中，一旦到达其发布日期，本地实体便可使用它。 如果在创建营销活动时指定了本地实体，则会向通知组中的操作员发送一条消息，告知他们营销活动可用。 如果事先未指定任何实体，则默认情况下，该营销活动可供所有本地实体使用。 有关更多信息，请参阅 [组织实体](about-distributed-marketing.md#organizational-entities).
