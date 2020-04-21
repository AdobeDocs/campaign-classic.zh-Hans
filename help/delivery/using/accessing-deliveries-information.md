---
title: 访问投放信息
seo-title: 访问投放信息
description: 访问投放信息
seo-description: null
page-status-flag: never-activated
uuid: dc8f0267-1884-4a39-9a7d-d5ef21932928
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: d2631c67-7781-4baa-b24e-e7921353d131
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 631e29bd6e59b8ae46084dee3a1d470916a2032b

---


# 访问投放信息{#accessing-deliveries-information}

## 访问投放的列表 {#accessing-the-list-of-deliveries}

要访问投放的列表，请转到宇宙， **[!UICONTROL Campaigns]** 然后单击链 **[!UICONTROL Deliveries]** 接。

如果您使用 [资源管理器视图](../../platform/using/adobe-campaign-workspace.md#about-adobe-campaign-explorer)，则可以通过树中的节点访问 **[!UICONTROL Campaign management > Deliveries]** 所有投放。

>[!NOTE]
>
>Adobe Campaign工作区显示在 [本节中](../../platform/using/adobe-campaign-workspace.md)。

通过此页面，您可以访问投放的整体视图:它显示数据库中的所有投放。 您可以视图其状态、成功率和修改日期。

![](assets/d_ncs_user_filter_interface_delivery01.png)

>[!NOTE]
>
>信息过滤功能在此部 [分中介绍](../../platform/using/filtering-options.md)。

该投放向导允许您配置投放、启动批准流程和发送。 向导的内容取决于通信渠道（电子邮件、移动设备、推送、直邮）和运营商权限。

要操作列表中的投放，请单击投放。 它在新窗口中打开，例如，您可以确认其投放或暂停。

![](assets/s_ncs_user_interface_delivery02.png)

根据投放周期的阶段，主要可能的状态为：

* 已取消
* 失败
* 待定
* 已完成
* 已暂停
* 重试等待
* 进行中
* 准备投放
* 正在准备
* 目标计算
* 正在编辑

每个状态都有其自己的颜色和标签。

![](assets/s_ncs_user_status_campaigns_120.png)

通过按钮旁边的下拉列表卡， **[!UICONTROL Create]** 您可以根据投放的状态筛选出相应的信息。

![](assets/delivery_filter_status.png)

## 访问投放日历 {#accessing-the-delivery-calendar}

要访问投放日历，请转到宇宙 **[!UICONTROL Campaign]** 并单击链 **[!UICONTROL Campaign calendar]** 接。 此日历显示一段时间内的活动细分。 您可以按月、周或天个性化展示。

![](assets/s_ncs_user_interface_delivery04.png)

单击投放的名称可显示有关它的主要信息。 您还可以根据需要通过单击打开活动 **[!UICONTROL Open]**。

![](assets/s_ncs_user_interface_delivery05.png)

## 访问投放吞吐量信息 {#accessing-deliveries-throughput-information}

该页面上的信 **[!UICONTROL Delivery throughput]** 息涉及该平台的所有投放。 为了测量消息的传送速度，标准是每小时发送的消息数和消息的大小（以位／秒为单位）。 在以下示例中，第一个图以蓝色显示成功的投放，以橙色显示错误投放的数量。

您可以选择计算吞吐量的时隙。 为此，请从下拉列表中选择值，然后单击 **[!UICONTROL Refresh]**。

![](assets/s_ncs_user_interface_delivery06.png)

>[!NOTE]
>
>对于托管或混合安装，如果您已升级到增强的MTA，该页 **[!UICONTROL Delivery throughput]** 面将不再显示电子邮件收件人的吞吐量。 它将显示消息从活动到增强MTA的中继的吞吐量速度。
>
>有关Adobe Campaign增强MTA的详细信息，请参阅本 [文档](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)。