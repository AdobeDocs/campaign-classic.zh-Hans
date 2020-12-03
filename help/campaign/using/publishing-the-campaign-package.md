---
solution: Campaign Classic
product: campaign
title: 发布活动包
description: 发布活动包
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 2%

---


# 发布活动包{#publishing-the-campaign-package}

中央实体运算符将希望优惠的活动发布到&#x200B;**[!UICONTROL list of campaign packages]**&#x200B;中的本地实体。

在活动包列表中发布活动包之前，包必须得到中央实体的批准。 为此，可以通过活动包中的&#x200B;**[!UICONTROL Approval parameters]**&#x200B;链接指定审阅者或审阅者组。

## 分配审阅者{#assigning-a-reviewer}

要选择活动包中的&#x200B;**[!UICONTROL Approval parameters]**&#x200B;链接，请从下拉列表中选择相关审阅者。

![](assets/s_advuser_mkg_dist_define_valid.png)

然后，您可以单击&#x200B;**[!UICONTROL Submit for approval]**&#x200B;开始审批过程。

![](assets/s_advuser_mkg_dist_valid_process.png)

然后向审阅者发送通知消息以确认此活动包的可用性。 此消息包含一个链接，用于通过Web访问接受或拒绝批准。

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>在组织实体级别，您还可以指定审阅者批准订单。 有关详细信息，请参阅[组织实体](../../campaign/using/about-distributed-marketing.md#organizational-entities)。

## 添加其他审阅者{#adding-other-reviewers}

您可以从&#x200B;**[!UICONTROL Edit...]**&#x200B;链接添加其他审阅者，该链接位于活动包的&#x200B;**[!UICONTROL Approval parameters...]**&#x200B;选项卡中。

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## 批准期{#approval-periods}

默认情况下，审阅者会从提交日期起三天内获得批准。

在“编辑审阅者”窗口中，您还可以设置提醒，在活动包未获批准时发送一个或多个消息。 为此，请单击&#x200B;**[!UICONTROL Add reminder]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮。

提醒可以在指定日期和／或提交日期后的&#x200B;**x**&#x200B;天发出。 提醒类型可以在提醒表的第一列中配置。 在以下示例中，审阅者将在2014年12月29日（即在&#x200B;**[!UICONTROL Date]**&#x200B;列中选定日期的前两天）收到提醒消息，在批准期结束的前一天（即提交批准日期后的两天）收到第二个提醒。

![](assets/s_advuser_mkg_dist_reminder_planning.png)

一旦定义了该包并提交了该包以供审批，执行计划就会显示在&#x200B;**[!UICONTROL Audit]**&#x200B;选项卡中。 它显示根据先前配置计算的处理截止日期以及所有已配置提醒的日期。

## 通过Adobe Campaign控制台{#approving-via-the-adobe-campaign-console}进行批准

如果未指定审核者，或者通知的操作员均未批准该包，则使用&#x200B;**[!UICONTROL Approve the package]**&#x200B;按钮可以直接从活动包&#x200B;**[!UICONTROL Dashboard]**&#x200B;或包概述中进行批准。

![](assets/s_advuser_mkg_dist_valid_button.png)

批准后，活动将发布、添加到列表，一旦达到发布日期，本地实体即可使用它。 如果在创建本地实体时指定了活动，则会向通知组中的操作符发送一条消息，告知其活动可用。 如果之前未指定任何实体，则默认情况下，活动对所有本地实体均可用。 有关详细信息，请参阅[组织实体](../../campaign/using/about-distributed-marketing.md#organizational-entities)。
