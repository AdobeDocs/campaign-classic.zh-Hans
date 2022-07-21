---
product: campaign
title: 一致性规则
description: 一致性规则
feature: Typology Rules
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 3%

---

# 一致性规则{#consistency-rules}

![](../../assets/v7-only.svg)

## 关于一致性规则 {#about-consistency-rules}

Adobe Campaign通过营销活动分类中包含的一组规则，确保通信的一致性。 其目标是控制发送给收件人的投放内容，如量、性质、相关性等。

**容量** 例如，规则可以避免消息投放所涉及的平台过载。 例如，不得同时向太多人发送包含下载链接的特殊选件，以避免服务器饱和；电话营销活动不得超过呼叫中心等的处理能力。 有关更多信息，请参阅 [控制能力](#controlling-capacity).

## 控制能力 {#controlling-capacity}

在投放消息之前，您需要确保贵组织具有处理投放（物理基础架构）、投放可生成的响应（入站消息）以及要与订阅者联系的呼叫数（呼叫中心处理能力）的能力。

为此，您需要创建 **[!UICONTROL Capacity]** 分类规则。

在以下示例中，我们为电话忠诚度促销活动创建分类规则。 我们将消息数量限制为每天20条，即呼叫中心的每日处理能力。 将规则应用于两个投放后，我们即可通过日志监控使用情况。

要设计新的容量规则，请执行以下步骤：

1. 在 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 节点，单击 **[!UICONTROL New]**.
1. 选择 **[!UICONTROL Capacity]** 规则类型。

   ![](assets/campaign_opt_create_capacity_01.png)

1. 在 **[!UICONTROL Capacity]** ，请创建可用行：在我们的示例中，这些是可进行调用的时间段。 选择24小时的时段，在初始数量中输入150，这意味着呼叫中心每天可以处理150个呼叫。

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >可用性行仅供参考。 如果需要在达到容量限制时排除消息，请参阅 [此部分](#exclude-messages-when-capacity-limit-reached).

1. 将此规则与分类关联，然后在投放中引用该分类以应用此容量规则。 如需详细信息，请参阅[此部分](applying-rules.md#applying-a-typology-to-a-delivery)。
1. 您可以监控规则的使用情况 **[!UICONTROL Consumptions]** 和 **[!UICONTROL Capacity]** 选项卡。

   在投放中使用规则时， **[!UICONTROL Consumed]** 和 **[!UICONTROL Remaining]** 列提供有关加载的信息，如下所示：

   ![](assets/campaign_opt_create_capacity_03.png)

   如需详细信息，请参阅[此部分](#monitoring-consumption)。

## 定义最大负载 {#defining-the-maximum-load}

要定义最大负荷，您需要定义可用性行。 要实现此目的，可使用以下两个选项：您可以手动创建一个或多个可用性行(请参阅 [逐行添加可用性行](#adding-availability-lines-one-by-one))或创建可用性范围。 这些时间段的频率可以自动执行(请参阅 [添加一组可用性行](#add-a-set-of-availability-lines))。

### 逐行添加可用性行 {#adding-availability-lines-one-by-one}

要创建可用性行，请单击 **[!UICONTROL Add]** 按钮，选择 **[!UICONTROL Add an availability line]**. 输入可用期和可用负荷。

![](assets/campaign_opt_create_capacity_02.png)

根据需要添加任意数量的行以适合您的处理能力。

### 添加一组可用性行 {#add-a-set-of-availability-lines}

要定义给定时间的可用期，请单击 **[!UICONTROL Add]** 按钮并选择 **[!UICONTROL Add a set of availability lines]** 选项。 指示每个时间段的持续时间和要创建的时段数。

要自动创建页面的频率，请单击 **[!UICONTROL Change]** 按钮和定义时间段计划。

![](assets/campaign_opt_create_capacity_07.png)

例如，让我们定义一个计划，以在上午9点到下午5点之间以每小时10次呼叫的速率为所有工作日创建可用期。 要执行此操作，请应用以下步骤：

1. 选择周期类型以及其有效的日期和时间：

   ![](assets/campaign_opt_create_capacity_08.png)

1. 指示有效日期：

   ![](assets/campaign_opt_create_capacity_09.png)

1. 在批准计划之前，请检查计划：

   ![](assets/campaign_opt_create_capacity_10.png)

的 **[!UICONTROL Forecasting]** 工作流会自动创建所有匹配行。

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>我们建议通过文件导入创建可用性行。 利用此选项卡，可查看和检查冲减行。

## 达到容量限制时排除消息 {#exclude-messages-when-capacity-limit-reached}

可用性行仅供参考。 要排除超出的消息，请检查 **[!UICONTROL Exclude from the target messages in excess of capacity]** 选项。 这样可防止超出容量。 对于与上例相同的人口，消费和剩余能力不得超过初始数量：

![](assets/campaign_opt_create_capacity_04.png)

要处理的消息数将在定义的可用范围内平均划分。 这对呼叫中心特别相关，因为呼叫中心的每天最大呼叫数有限。 对于电子邮件投放， **[!UICONTROL Do not limit instantaneous delivery capacity]** 选项允许您忽略此可用范围，并同时发送电子邮件。

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>如果过载，将根据投放属性中定义的公式选择保存的消息。

![](assets/campaign_opt_create_capacity_06.png)

## 监控使用情况 {#monitoring-consumption}

默认情况下，容量规则仅用于指示目的。 选择 **[!UICONTROL Exclude messages in excess of capacity from the target]** 选项来阻止超出定义的加载。 在这种情况下，将使用此分类规则自动从投放中排除多余的消息。

要监控消费情况，请查看 **[!UICONTROL Consumed]** 列 **[!UICONTROL Capacity]** 选项卡。

![](assets/campaign_opt_create_capacity_04.png)

要查看冲减行，请单击 **[!UICONTROL Consumptions]** 选项卡。
