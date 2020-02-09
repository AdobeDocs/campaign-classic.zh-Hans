---
title: 发布营销活动包
seo-title: 发布营销活动包
description: 发布营销活动包
seo-description: null
page-status-flag: never-activated
uuid: f2d35a8d-191f-4c53-8682-7ccce2a94257
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 8653d4fc-e47f-451a-95f2-c9209a252664
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# 发布营销活动包{#publishing-the-campaign-package}

中央实体运营商将希望提供的营销活动发布到中的本地实体 **[!UICONTROL list of campaign packages]**。

在营销活动包列表中发布营销活动包之前，必须由中央实体批准营销活动包。 为此，您可以通过系列活动包中的链接指定 **[!UICONTROL Approval parameters]** 审阅人或审阅人组。

## 分配审阅人 {#assigning-a-reviewer}

要选择审阅人，请单 **[!UICONTROL Approval parameters]** 击营销活动包中的链接，然后从下拉列表中选择相关的审阅人。

![](assets/s_advuser_mkg_dist_define_valid.png)

然后，您可以单击以开始审批过程 **[!UICONTROL Submit for approval]**。

![](assets/s_advuser_mkg_dist_valid_process.png)

随后将向审阅者发送通知消息以确认此系列活动包的可用性。 该消息包含通过Web访问接受或拒绝批准的链接。

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>在组织实体级别，您还可以指定审阅者批准订单。 For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## 添加其他审阅者 {#adding-other-reviewers}

您可以从营销活动包的选 **[!UICONTROL Edit...]** 项卡中的链接添加其他审阅 **[!UICONTROL Approval parameters...]** 人。

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## 批准期 {#approval-periods}

默认情况下，审阅者会从提交日期起三天内获得批准。

在编辑审阅者窗口中，您还可以设置提醒以在营销活动包尚未获得批准时发送一个或多个消息。 要执行此操作，请单击链 **[!UICONTROL Add reminder]** 接，然后单击按 **[!UICONTROL Add]** 钮。

提醒可在给定日期和／或提交日期后 **x天** 发出。 提醒类型可以在提醒表的第一列中配置。 在以下示例中，审阅者将在2014年12月29日（即在列中选定日期的前两天）收到提醒消息，在批准期结束的前一天（即在提交以请求批准日期的两天后）收到第二个提醒消息。 **[!UICONTROL Date]**

![](assets/s_advuser_mkg_dist_reminder_planning.png)

定义包并提交包进行审批后，执行计划会显示在选项卡 **[!UICONTROL Audit]** 中。 它显示基于先前配置计算的处理截止日期以及所有已配置提醒的日期。

## 通过Adobe Campaign控制台进行批准 {#approving-via-the-adobe-campaign-console}

如果未指定审阅者，或者如果通知的操作员未批准该包，则通过该按钮，您可以直接从营销活动包或包概述中 **[!UICONTROL Approve the package]****[!UICONTROL Dashboard]** 继续审批。

![](assets/s_advuser_mkg_dist_valid_button.png)

批准后，营销活动会发布并添加到列表中，一旦达到发布日期，本地实体就可以使用它。 如果在创建营销活动时指定了本地实体，则会向通知组中的操作员发送一条消息，告知他们该营销活动可用。 如果之前未指定任何实体，则默认情况下，该营销活动对所有本地实体都可用。 For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).
