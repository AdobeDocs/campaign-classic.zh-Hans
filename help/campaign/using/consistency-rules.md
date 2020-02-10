---
title: 一致性规则
seo-title: 一致性规则
description: 一致性规则
seo-description: null
page-status-flag: never-activated
uuid: 9b497460-ba42-4bc7-98e0-55c1b4be5e44
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 9bcb5dc1-8cb4-4781-a8cd-8d072ff28b1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 一致性规则{#consistency-rules}

## 关于一致性规则 {#about-consistency-rules}

Adobe Campaign通过营销活动类型中包含的一组规则，保证了一致的通信。 其目标是控制发送给接收方的递送，如数量、性质、相关性等。

**例如** ，容量规则可以避免消息传送所涉及的平台过载。 例如，包含下载链接的特价优惠不能同时发送给太多人，以避免服务器饱和；电话活动不得超过呼叫中心等的处理能力。 For more on this, refer to [Controlling capacity](#controlling-capacity).

## 控制容量 {#controlling-capacity}

在发送消息之前，您需要确保您的组织具有处理发送（物理基础结构）的能力，发送可生成的响应（入站消息），以及要与订阅者联系的呼叫数（呼叫中心处理能力）。

为此，您需要创建排 **[!UICONTROL Capacity]** 版规则。

在以下示例中，我们为电话忠诚度营销活动创建了一个排版规则。 我们将消息数量限制为每天20条，即呼叫中心的日常处理能力。 一旦将规则应用于两个提交，我们就可以通过日志监控消费情况。

要设计新的容量规则，请执行以下步骤：

1. 在节点 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 下，单击 **[!UICONTROL New]**。
1. 选择规 **[!UICONTROL Capacity]** 则类型。

   ![](assets/campaign_opt_create_capacity_01.png)

1. 在标签 **[!UICONTROL Capacity]** 中，创建可用性行：在我们的示例中，这些是可以进行调用的时间段。 选择24小时的时段，并输入150作为初始数量，这意味着呼叫中心每天可以处理150个呼叫。

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >可用性行仅供参考。 如果您需要在达到容量限制时排除消息，请参阅 [此部分](#exclude-messages-when-capacity-limit-reached)。

1. 将此规则关联到类型学，然后将类型学引用到交付中以应用此容量规则。 如需详细信息，请参阅[此部分](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)。
1. 您可以监视规则和选项卡中的 **[!UICONTROL Consumptions]** 使用情况 **[!UICONTROL Capacity]** 情况。

   在分发中使用规则时，和列会 **[!UICONTROL Consumed]** 提供 **[!UICONTROL Remaining]** 有关加载的信息，如下所示：

   ![](assets/campaign_opt_create_capacity_03.png)

   如需详细信息，请参阅[此部分](#monitoring-consumption)。

## 定义最大负载 {#defining-the-maximum-load}

要定义最大负载，您需要定义可用性行。 为此，有两个选项可用：您可以手动创建一个或多个可用性行(请参阅逐 [个添加可用性行](#adding-availability-lines-one-by-one))或创建可用性范围。 这些时间段的频率可以自动化(请参 [阅添加一组可用行](#add-a-set-of-availability-lines))。

### 逐个添加可用行 {#adding-availability-lines-one-by-one}

要创建可用行，请单击按 **[!UICONTROL Add]** 钮并选择 **[!UICONTROL Add an availability line]**。 输入可用期和可用负载。

![](assets/campaign_opt_create_capacity_02.png)

根据需要添加多行以适合您的处理能力。

### 添加一组可用行 {#add-a-set-of-availability-lines}

要定义给定时间的可用期，请单击按 **[!UICONTROL Add]** 钮并选择 **[!UICONTROL Add a set of availability lines]** 选项。 指示每个时间段的持续时间和要创建的时间段数。

要自动创建页面的频率，请单击按钮并 **[!UICONTROL Change]** 定义时间段计划。

![](assets/campaign_opt_create_capacity_07.png)

例如，我们定义一个计划，以每小时10次呼叫的速率（在上午9点到下午5点之间）为所有工作日创建可用时间段。 为此，请应用以下步骤：

1. 选择周期类型以及其有效的天数和小时数：

   ![](assets/campaign_opt_create_capacity_08.png)

1. 指示有效日期：

   ![](assets/campaign_opt_create_capacity_09.png)

1. 在批准计划之前先检查计划：

   ![](assets/campaign_opt_create_capacity_10.png)

该工 **[!UICONTROL Forecasting]** 作流会自动创建所有匹配行。

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>我们建议通过文件导入创建可用行。 通过此标签可以查看和检查冲减行。

## 达到容量限制时排除消息 {#exclude-messages-when-capacity-limit-reached}

可用性行仅供参考。 要排除多余消息，请选中该 **[!UICONTROL Exclude from the target messages in excess of capacity]** 选项。 这可以防止超出容量。 对于与上一示例中相同的人口，消耗和剩余能力不能超过初始数量：

![](assets/campaign_opt_create_capacity_04.png)

要处理的消息数会在定义的可用范围内平均细分。 这对于呼叫中心尤其重要，因为其每天的最大呼叫数有限。 在发送电子邮件时，该选 **[!UICONTROL Do not limit instantaneous delivery capacity]** 项允许您忽略此可用范围并同时发送电子邮件。

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>在过载的情况下，根据在传送属性中定义的公式选择保存的消息。

![](assets/campaign_opt_create_capacity_06.png)

## 监控消费 {#monitoring-consumption}

默认情况下，容量规则仅用于指示用途。 选择 **[!UICONTROL Exclude messages in excess of capacity from the target]** 此选项可防止超出定义的加载。 在这种情况下，使用此排版规则的发送将自动排除多余消息。

要监控消费情况，请查看在排版规则 **[!UICONTROL Consumed]** 中选项卡的 **[!UICONTROL Capacity]** 列中显示的值。

![](assets/campaign_opt_create_capacity_04.png)

要查看冲减行，请单击规 **[!UICONTROL Consumptions]** 则中的标签。
