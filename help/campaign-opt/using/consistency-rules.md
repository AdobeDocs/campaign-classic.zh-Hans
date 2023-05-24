---
product: campaign
title: 一致性规则
description: 一致性规则
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Typology Rules
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 3%

---

# 一致性规则{#consistency-rules}

## 关于一致性规则 {#about-consistency-rules}

由于活动类型中包含一组规则，Adobe Campaign可确保通信的一致性。 其目的是控制发送给收件人的投放，如投放数量、性质、相关性等。

**容量** 例如，规则可以避免消息投放所关注的平台过载。 例如，包含下载链接的特殊优惠不得一次发送给太多人，以避免服务器饱和；电话营销活动不得超出呼叫中心的处理能力等。 有关更多信息，请参阅 [控制能力](#controlling-capacity).

## 控制能力 {#controlling-capacity}

在投放消息之前，您需要确保贵组织有能力处理投放（物理基础架构）、投放可能生成的响应（入站消息）以及联系订户的呼叫次数（呼叫中心处理能力），例如。

为此，您需要创建 **[!UICONTROL Capacity]** 类型规则。

在以下示例中，我们为电话忠诚度促销活动创建分类规则。 我们将消息数量限制为每天20条，即呼叫中心的每日处理能力。 将规则应用于两个投放后，我们可以通过日志监控使用情况。

要设计新容量规则，请执行以下步骤：

1. 在 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 节点，单击 **[!UICONTROL New]**.
1. 选择 **[!UICONTROL Capacity]** 规则类型。

   ![](assets/campaign_opt_create_capacity_01.png)

1. 在 **[!UICONTROL Capacity]** 选项卡，创建可用性行：在我们的示例中，这些是可以进行调用的时间段。 选择24小时期间并在初始数量中输入150，这意味着呼叫中心每天可以处理150个呼叫。

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >可用性行仅供参考。 如果在达到容量限制时需要排除消息，请参阅 [本节](#exclude-messages-when-capacity-limit-reached).

1. 将此规则与分类关联，然后在投放中引用该分类以应用此容量规则。 如需详细信息，请参阅[此部分](applying-rules.md#applying-a-typology-to-a-delivery)。
1. 您可以通过规则监控使用情况 **[!UICONTROL Consumptions]** 和 **[!UICONTROL Capacity]** 选项卡。

   在投放中使用规则时， **[!UICONTROL Consumed]** 和 **[!UICONTROL Remaining]** 列提供有关负载的信息，如下所示：

   ![](assets/campaign_opt_create_capacity_03.png)

   如需详细信息，请参阅[此部分](#monitoring-consumption)。

## 定义最大负载 {#defining-the-maximum-load}

要定义最大载荷，您需要定义可用性行。 要执行此操作，有两个选项可用：您可以手动创建一个或多个可用性行(请参阅 [逐一添加可用性行](#adding-availability-lines-one-by-one))或创建可用性范围。 这些时间段的频率可以自动化(请参阅 [添加一组可用性行](#add-a-set-of-availability-lines))。

### 逐一添加可用性行 {#adding-availability-lines-one-by-one}

要创建可用性行，请单击 **[!UICONTROL Add]** 按钮并选择 **[!UICONTROL Add an availability line]**. 输入可用性期间和可用负荷。

![](assets/campaign_opt_create_capacity_02.png)

根据需要添加任意数量的行以适合您的处理能力。

### 添加一组可用性行 {#add-a-set-of-availability-lines}

要定义给定时间的可用性时段，请单击 **[!UICONTROL Add]** 按钮并选择 **[!UICONTROL Add a set of availability lines]** 选项。 指示每个时段的持续时间以及要创建的时段数。

要自动设置页面创建频率，请单击 **[!UICONTROL Change]** 按钮和定义时间段计划。

![](assets/campaign_opt_create_capacity_07.png)

例如，我们定义一个时间表，以每小时10次呼叫的速率在上午9点到下午5点为所有工作日创建可用性时段。 要执行此操作，请应用以下步骤：

1. 选择周期类型以及有效天数与小时数：

   ![](assets/campaign_opt_create_capacity_08.png)

1. 指示有效日期：

   ![](assets/campaign_opt_create_capacity_09.png)

1. 在批准计划之前检查计划：

   ![](assets/campaign_opt_create_capacity_10.png)

此 **[!UICONTROL Forecasting]** 工作流会自动创建所有匹配的行。

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>我们建议通过文件导入创建可用性行。 通过此选项卡，您可以查看和检查消耗行。

## 达到容量限制时排除消息 {#exclude-messages-when-capacity-limit-reached}

可用性行仅供参考。 要排除多余的消息，请检查 **[!UICONTROL Exclude from the target messages in excess of capacity]** 选项。 这可以防止超出容量。 对于与上例相同的人口，冲减和剩余能力不能超过初始数量：

![](assets/campaign_opt_create_capacity_04.png)

要处理的消息数在定义的可用性范围内平均细分。 这尤其与呼叫中心相关，因为它们每天的最大呼叫数是有限的。 如果是电子邮件投放，则 **[!UICONTROL Do not limit instantaneous delivery capacity]** 选项允许您忽略此可用性范围并同时发送电子邮件。

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>如果过载，则根据投放属性中定义的公式选择已保存的消息。

![](assets/campaign_opt_create_capacity_06.png)

## 监测消耗 {#monitoring-consumption}

默认情况下，容量规则仅用于指示目的。 选择 **[!UICONTROL Exclude messages in excess of capacity from the target]** 选项以防止超出定义的负载。 在这种情况下，使用此分类规则将自动从投放中排除多余的消息。

要监控消耗，请查看 **[!UICONTROL Consumed]** 列 **[!UICONTROL Capacity]** 选项卡。

![](assets/campaign_opt_create_capacity_04.png)

要查看消耗行，请单击 **[!UICONTROL Consumptions]** 选项卡。
