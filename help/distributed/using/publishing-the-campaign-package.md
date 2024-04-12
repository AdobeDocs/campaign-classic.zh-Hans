---
product: campaign
title: 发布活动包
description: 发布活动包
feature: Distributed Marketing
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 2%

---

# 发布活动包{#publishing-the-campaign-package}



中央实体操作员在中发布他们要提供给本地实体的营销活动 **[!UICONTROL list of campaign packages]**.

在营销活动包列表中发布营销活动包之前，必须获得中央实体的批准。 为此，您可以通过 **[!UICONTROL Approval parameters]** 活动包中的链接。

## 分配审阅人 {#assigning-a-reviewer}

要选择审阅者，请单击 **[!UICONTROL Approval parameters]** 活动包中的链接，并从下拉列表中选择相关的查看者。

![](assets/s_advuser_mkg_dist_define_valid.png)

然后，您可以通过单击开始批准流程 **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

然后，将向查看者发送通知消息，以确认此Campaign包的可用性。 该消息包含通过Web访问接受或拒绝批准的链接。

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>在组织实体级别，您还可以指定审阅人来批准订单。 有关详细信息，请参见 [组织实体](about-distributed-marketing.md#organizational-entities).

## 添加其他审阅人 {#adding-other-reviewers}

您可以从以下位置添加其他审阅人 **[!UICONTROL Edit...]** 链接，可在campaign包的 **[!UICONTROL Approval parameters...]** 选项卡。

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## 审批期 {#approval-periods}

默认情况下，审核者将在提交日期起三天后进行审批。

在“编辑审阅者”窗口中，您还可以设置提醒，以便在活动包未获批准时发送一条或多条消息。 要执行此操作，请单击 **[!UICONTROL Add reminder]** 链接，然后 **[!UICONTROL Add]** 按钮。

可以在给定日期发送提醒和/或 **x** 天后提交。 可以在提醒表的第一列中配置提醒类型。 在以下示例中，查看者将在2014年1月29日(即在 **[!UICONTROL Date]** 以及于审批期结束前1日（即提交审批日期后2日）提交第二次提醒。

![](assets/s_advuser_mkg_dist_reminder_planning.png)

在定义包并将其提交审批后，执行计划将显示在 **[!UICONTROL Audit]** 选项卡。 它显示根据以前的配置计算出的处理截止日期，以及所有已配置提醒的日期。

## 通过Adobe Campaign控制台进行审批 {#approving-via-the-adobe-campaign-console}

如果未指定审查者或通知的操作员均未批准包，则 **[!UICONTROL Approve the package]** 按钮允许您直接从营销活动包进行审批 **[!UICONTROL Dashboard]** 或者从包概述中进行访问。

![](assets/s_advuser_mkg_dist_valid_button.png)

批准后，该营销活动会发布并添加到列表，一旦达到其可用日期，本地实体即可使用它。 如果在创建营销策划时指定了本地实体，则会向通知组中的操作员发送消息，告知他们营销策划可用。 如果未预先指定实体，则默认情况下所有本地实体都可以使用营销活动。 有关详细信息，请参见 [组织实体](about-distributed-marketing.md#organizational-entities).
