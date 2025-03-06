---
product: campaign
title: 压力规则
description: 了解如何在Adobe Campaign中使用压力规则
role: User, Data Engineer
feature: Fatigue Management, Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: c23212f2-fdf8-4820-b389-546f7c84db27
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '3336'
ht-degree: 6%

---

# 压力规则{#pressure-rules}

## 关于营销疲劳度 {#about-marketing-fatigue}

通过实施销售压力管理，您可以避免在数据库中过度招徕顾客，这也称为营销疲劳度。 为此，您可以定义每个收件人的最大消息数。 它还允许您在营销活动之间实施仲裁规则，以将最佳消息发送给目标受众。

**压力**&#x200B;规则，用于管理营销疲劳度，例如，将发送给一个群体的信件数量限制为两个，选择最符合一组订阅者利益的通信，避免向不满意的客户发送短信等。

根据定义的阈值和消息权重选择营销活动。

* 阈值是在给定时段内为给定收件人授权的最大投放数量。 它可以为set或variable。 在分类规则设置中对其进行设置或计算。 请参阅[最大消息数](#maximum-number-of-messages)。
* 利用投放权重，您可以确定压力管理框架内的优先级最高的投放。具有最高权重的消息具有优先级。 请参阅[消息权重](#message-weight)。

仲裁包括确保权重大于正在进行的营销活动的计划营销活动不会导致过多的用户档案请求：如果是这种情况，则将从投放中排除用户档案。

仲裁标准（消息权重和/或阈值）可能因两种类型的信息而异：

* 收件人首选项，它是声明性信息：新闻稿订阅、收件人状态（客户或潜在客户）、
* 收件人行为：购买、访问的链接等。

用于定义符合条件的消息的仲裁规则在分析阶段应用。 对于每个收件人和相关时段，如果以下公式为true，则将发送消息： **（已发送的消息数）+ （具有较大权重的消息数）&lt;阈值**。

否则，收件人将为&#x200B;**[!UICONTROL Excluded by arbitration]**。 有关详细信息，请参阅[仲裁后排除](#exclusion-after-arbitration)。

## 创建压力规则 {#creating-a-pressure-rule}

要使用Adobe Campaign在营销活动之间设置仲裁，首先要创建营销活动类型并定义链接类型规则（**压力**&#x200B;规则）。

要创建和配置 **[!UICONTROL Pressure]** 分类规则，请应用以下步骤：

1. 在营销活动类型规则列表中，单击列表上方的&#x200B;**[!UICONTROL New]**&#x200B;图标。

   ![](assets/campaign_opt_create_a_rule_01.png)

1. 在新规则的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，选择&#x200B;**压力**&#x200B;类型规则并为其输入名称和描述。

   ![](assets/campaign_opt_create_a_rule_02.png)

1. 根据需要更改执行顺序。 将多个分类规则应用为&#x200B;**[!UICONTROL Typology]**&#x200B;集时，首先应用排序较低的规则。 有关详细信息，请参阅[执行顺序](applying-rules.md#execution-order)。
1. 在&#x200B;**[!UICONTROL Calculation parameters]**&#x200B;部分中，定义频率（如果要在下次每日重新仲裁执行之后保存定位）。 有关详情，请参阅[调整计算频率](applying-rules.md#adjusting-calculation-frequency)。
1. 单击&#x200B;**[!UICONTROL Pressure]**&#x200B;选项卡，然后选择应用分类规则的日历期间。

   ![](assets/campaign_opt_create_a_rule_03.png)

   该规则将应用于联系日期包含在相关时间段的投放。

   >[!NOTE]
   >
   >仅当选择了&#x200B;**[!UICONTROL Take the deliveries into account in the provisional calendar]**&#x200B;选项时，才会考虑计划的投放。 有关详细信息，请参阅[设置句点](#setting-the-period)。
   >

1. 定义计算最大消息数的方法。

   阈值表示在相关时段内可发送给收件人的消息的最大数量。

   默认情况下，阈值为常量，您需要指定规则授权的消息数量上限。

   ![](assets/campaign_opt_create_a_rule_03b.png)

   要定义变量阈值，请在&#x200B;**[!UICONTROL Type of threshold]**&#x200B;字段中选择&#x200B;**[!UICONTROL Depends on the recipient]**&#x200B;值，然后使用右侧的图标打开表达式编辑器。

   ![](assets/campaign_opt_create_a_rule_04.png)

   有关详细信息，请参阅[最大消息数](#maximum-number-of-messages)。

1. 指定计算交货重量的方法。

   每个投放都有一个权重，即表示其优先级的值：这支持在营销活动之间进行仲裁。 权重是使用分类规则和/或其属性中定义的公式来计算的。 有关详情，请参阅[消息权重](#message-weight)。

1. 默认情况下，所有消息都会考虑阈值计算式。通过&#x200B;**[!UICONTROL Restriction]**&#x200B;选项卡，可筛选分类规则关注的消息：

   * 利用此选项卡的上半部分，可限制相关的收件人。
   * 利用此选项卡的下半部分，可筛选要计数的消息。

     在下面的示例中，只考虑保存在&#x200B;**NewContacts**&#x200B;文件夹中的收件人，并关注以&#x200B;**新闻稿**&#x200B;开头的投放。

   ![](assets/campaign_opt_create_a_rule_05.png)

1. **[!UICONTROL Typologies]**&#x200B;选项卡允许您查看应用此规则的促销活动分类，或将规则链接到一个或多个现有分类。 有关详细信息，请参阅[应用分类](about-campaign-typologies.md#applying-typologies)。

## 定义阈值和权重 {#defining-thresholds-and-weights}

### 最大消息数 {#maximum-number-of-messages}

每个压力规则定义一个阈值，即在给定时间段内可以向一个收件人发送的最大消息数。 达到此阈值后，只有在所考虑的时段结束后，才会再进行投放。通过此流程，您可以在消息数量超过设置的阈值时自动将收件人从投放中排除，从而避免过度通信。

阈值可以是常量，也可以通过带有变量的公式来计算。 这意味着在给定的时间段内，阈值可能因收件人而异，甚至对于同一收件人也可能有所不同。

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>输入&#x200B;**0**&#x200B;作为阈值会阻止在所考虑时段内向目标群体投放所有内容。

**示例：**

您可以根据收件人所属的区段索引授权消息的数量。 这意味着属于Web区段的收件人可能会收到比其他收件人更多的消息。 **[!UICONTROL Iif (@origin='Web', 5, 3)]**&#x200B;类型公式授权向收件人投放5封邮件，为其他区段投放3封邮件。 配置将如下所示：

![](assets/campaign_opt_pressure_sample.png)

要定义阈值，您可以使用链接到定向维度的维度：例如，要包含传递到访客表中存储的收件人用户档案的消息（有关访客表的详细信息，请参阅[本节](../../surveys/using/use-case-creating-a-refer-a-friend-form.md)），或者要避免每周向同一家庭发送多条消息（可能指多个电子邮件地址），这些消息是在链接到收件人地址的维度中标识的。

为此，请选择&#x200B;**[!UICONTROL Count messages on a linked dimension]**&#x200B;选项，然后选择访客或Contact表。

### 消息权重 {#message-weight}

每个投放都有一个代表其优先级的权重。默认情况下，投放权重设置为 5。压力规则允许您定义将应用这些规则的投放的权重。

可以通过公式设置或计算权重以满足收件人的需求。例如，您可以根据收件人兴趣来定义投放权重。

>[!CAUTION]
>
>可以在&#x200B;**[!UICONTROL Properties]**&#x200B;选项卡中为每个投放单独重载在类型规则中定义的权重。 单击&#x200B;**[!UICONTROL Typology]**&#x200B;选项卡以选择营销活动类型，并根据需要指定要应用的权重。\
>但是，在A分类规则中声明的权重不会用于计算B分类规则：此权重将仅涉及使用A规则的投放。

**示例：**

在以下示例中，我们希望将新闻稿在音乐中的权重与其收件人的倾向分数关联起来。 操作步骤：

1. 创建新字段以存储收件人倾向分数。 在此例中，字段&#x200B;**@Music**&#x200B;将包含调查和在线投票、收集的跟踪数据等的答案。
1. 创建分类规则以根据此字段计算消息权重。

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. 将此规则应用于包含以下主题的消息：新闻稿、特殊优惠等。 这些投放的权重，因此其优先级将取决于每个收件人的倾向分数。

## 设置期间 {#setting-the-period}

压力规则定义于&#x200B;**n**&#x200B;天的滚动周期。

该期间在规则的&#x200B;**[!UICONTROL Pressure]**&#x200B;选项卡中配置。 您可以指定天数，并根据需要选择要应用的分组类型（日、周、月、季度等）。

分组类型允许您将&#x200B;**[!UICONTROL Period considered]**&#x200B;字段扩展到期间日期的整天、日历周、日历月或日历年。

例如，如果压力规则规定每周发送2条消息的阈值并对每个日历月进行分组，则将阻止在同一周内和同一日历月内发送超过2条消息。 警告：如果时段与两个月重叠，则计算阈值将考虑这两个日历月内的投放情况，因此可能会阻止第二个月内的所有新投放情况。

请注意，默认情况下，计算阈值时只考虑已发送的投放。 在Campaign Classic v7中，如果您还希望考虑在相关时段内计划的投放，请选中&#x200B;**[!UICONTROL Take the deliveries into account in the provisional calendar]**&#x200B;选项。 在这种情况下，考虑的时段会加倍，以便将未来投放与之前投放整合在一起。

要将考虑的投放限制在2周内，您可以：

1. 在&#x200B;**[!UICONTROL Concerned period]**&#x200B;字段中输入&#x200B;**15d**：在计算中将考虑在应用规则的投放日期前两周发送的投放，

或者

1. 在&#x200B;**[!UICONTROL Period considered]**&#x200B;字段中输入&#x200B;**7d**&#x200B;并选中&#x200B;**[!UICONTROL Take the deliveries into account in the provisional calendar]**&#x200B;选项：在计算时，将考虑在投放日期之前7天内发送的投放以及在应用规则的投放日期之后7天内计划发送的投放。

期间开始日期取决于数据库的配置方式。

例如，如果您对日期为12/11的投放应用了15天压力规则，但没有将其分组，则会考虑11/27至12/12之间的投放。 如果压力规则考虑临时日程表中的交付，则会考虑计划于11/27至12/27之间的所有交付。 最后，如果您在规则中为每个日历月配置分组，则计算阈值时将考虑11月和12月的所有投放（从11/1到12/31）。


**常见案例**

为了确保不考虑当前日历周的投放，以及为了不冒风险也考虑计算阈值的前一周的投放，请在“0”处指定&#x200B;**[!UICONTROL Period considered]**，并选择“按日历周分组”作为&#x200B;**[!UICONTROL Period type]**。

当时段高于0（例如1）时，计算阈值可能会考虑前天的投放。 因此，如果前一天对应于上一个日历周，并且所选的期间类型是“按日历周分组”，则将考虑所有上一周的计算阈值。

**示例：**

我们希望创建一个压力规则，将每两周的请求限制为3条消息，并将分组限制在日历月份。

![](assets/campaign_opt_pressure_period_sample_1a.png)

我们来看看预定在05/30、06/3、06/8、06/12、06/22和06/30出版的6份相同重量的通讯。

![](assets/campaign_opt_pressure_period_sample_0.png)

预定在6月12日和30日进行的投放将不会发送：06/12投放将超过每两周发送3条消息的阈值，第30次投放将超过每个日历月授权通信的阈值。

![](assets/campaign_opt_pressure_period_sample_1.png)

在分析阶段，仲裁会排除这些投放的所有收件人：

![](assets/campaign_opt_pressure_period_sample_2.png)

对于同一规则，如果您按季度对投放进行分组，则还将排除&#x200B;**新闻稿5**&#x200B;的收件人，并且不会发送该新闻稿。

最后，如果未选择分组，则仅不会发送&#x200B;**新闻稿4**，因为该新闻稿与前三个新闻稿的预定时间相同，为期2周。

>[!NOTE]
>
>在更改分类规则的定义时，可以创建&#x200B;**模拟**&#x200B;来控制它对应用它的投放的影响，并监视投放之间的相互影响。 有关详细信息，请参阅[促销活动模拟](campaign-simulations.md)。

## 仲裁后排除 {#exclusion-after-arbitration}

每晚通过&#x200B;**[!UICONTROL Forecasting]**&#x200B;技术工作流和&#x200B;**[!UICONTROL Campaign jobs]**&#x200B;工作流重新应用仲裁。

**[!UICONTROL Forecasting]**&#x200B;工作流会预计算正在进行的时段（从其开始日期到当前日期）的数据，从而可以在分析期间应用分类规则。 它还每晚重新计算用于仲裁的排除计数器。

因此，对于每个收件人，Adobe Campaign会检查要发送的消息数是否不超过阈值，并会考虑在相关时间段内已发送的消息数。 此信息是一个&#x200B;**指示器**，因为所有计算都在交付时更新。

如果此数字超过阈值，则会应用营销活动类型中定义的仲裁规则，并从权重较低的营销活动中排除收件人。

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>如果多个投放具有相等分数，则将发送为最早日期计划的营销活动。

## 压力规则用例 {#use-cases-on-pressure-rules}

### 根据标准调整阈值 {#adapting-the-threshold-based-on-criterion}

我们希望创建一个分类规则，防止每周向客户投放超过4条消息，每周向潜在客户投放2条消息。

要识别客户和潜在客户，请使用&#x200B;**[!UICONTROL Status]**&#x200B;字段，其中的0表示潜在客户，1表示客户。

要创建规则，请应用以下步骤：

1. 创建新的&#x200B;**Pressure**&#x200B;类型分类规则。
1. 编辑&#x200B;**[!UICONTROL Pressure]**&#x200B;选项卡：在&#x200B;**[!UICONTROL Maximum number of messages]**&#x200B;部分中，我们要创建一个公式以根据每个收件人计算阈值。 在&#x200B;**[!UICONTROL Threshold type]**&#x200B;字段中选择&#x200B;**[!UICONTROL Depends on the recipient]**&#x200B;值，然后单击&#x200B;**[!UICONTROL Formula]**&#x200B;字段右侧的&#x200B;**[!UICONTROL Edit expression]**。

   单击&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;按钮以定义计算公式。

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. 选择&#x200B;**[!UICONTROL Edit the formula using an expression]**&#x200B;选项并单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. 在函数列表中，双击&#x200B;**[!UICONTROL Others]**&#x200B;节点中的&#x200B;**Iif**&#x200B;函数。

   然后在&#x200B;**[!UICONTROL Available fields]**&#x200B;部分中选择收件人的&#x200B;**状态**。

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   输入以下公式： **Iif(@status=0,2，4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   使用此公式后，如果 Status 等于 0，则分配值“2”；对于所有其他 Status，则分配值“4”。

   单击 **[!UICONTROL Finish]** 以批准公式。

1. 指示应用规则的时段：在本例中为7天，用于计算每周的消息数量。

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. 保存规则以批准创建。

现在，可将之前创建的规则链接到分类，以将其应用于投放。 操作步骤：

1. 创建活动类型。
1. 转到&#x200B;**[!UICONTROL Rules]**&#x200B;选项卡，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并选择您刚刚创建的规则。

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 保存分类：是否将其添加到现有分类的列表。

要在投放中使用此分类，请在&#x200B;**[!UICONTROL Typology]**&#x200B;选项卡的投放属性中选择它，如下所示：

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>可以在投放模板中定义分类，以自动应用至使用此模板创建的所有投放。

在投放分析期间，会根据已发送给投放收件人的投放数量，将符合条件的投放收件人从投放中排除。 要查看此信息，您可以：

* 查看分析结果：

  ![](assets/campaign_opt_pressure_sample_1_8.png)

* 编辑投放并单击&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡和&#x200B;**[!UICONTROL Exclusions]**&#x200B;子选项卡：

  ![](assets/campaign_opt_pressure_sample_1_9.png)

* 单击&#x200B;**[!UICONTROL Audit]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Causes of exclusions]**&#x200B;子选项卡以显示排除项数和应用的分类规则：

  ![](assets/campaign_opt_pressure_sample_1_10.png)

### 根据行为计算投放权重 {#calculating-the-delivery-weight-based-on-behavior}

您可以根据收件人行为定义压力规则：因此，投放的权重可以适应因收件人而异的标准。 例如，您可以决定发送消息，这取决于收件人是否访问了您的互联网网站、点击了最新新闻稿的特定部分、订阅了信息服务，甚至取决于对调查、在线游戏等的回答。

在以下示例中，我们要创建权重为5的投放。 此权重中根据收件人行为加入了倾向分数：已从此网站订购的客户得分将为5，而从未在线订购的客户得分将为4。

要执行此类型的配置，需要使用公式来定义消息权重。 有关倾向分数和调查答案的信息必须在数据模型中可访问。 在我们的示例中，已添加&#x200B;**Propensity**&#x200B;字段。

应用以下配置步骤：

1. 创建新的&#x200B;**Pressure**&#x200B;类型分类规则。
1. 编辑&#x200B;**[!UICONTROL Pressure]**&#x200B;选项卡。 我们要创建一个阈值公式，该公式将基于每个单独的收件人：单击&#x200B;**[!UICONTROL Weight formula]**&#x200B;字段右侧的&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标。

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. 默认情况下，表达式编辑器的上半部分将显示值&#x200B;**5**。 我们希望将每个收件人的倾向得分添加到此权重：将光标置于5的右侧，输入&#x200B;**+**&#x200B;字符并选择&#x200B;**倾向**&#x200B;字段。

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. 然后，为已购买的收件人添加更高的值。 对于他们，投放的重量必须增加5，而对于其他人，仅增加4。

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;保存此规则。
1. 将规则链接到活动分类，并在投放中引用此分类以进行批准。

### 仅发送权重最高的消息 {#sending-only-the-highest-weighted-messages}

您想在同一周内向每位收件人发送不超过2封邮件，限制每天发送2封邮件，并且只希望投放权重较高的邮件。

为此，您需要为同一收件人计划多个具有不同权重的投放，并应用压力规则以排除权重较低的投放。

首先，配置压力规则。

1. 创建压力规则。 有关详情，请参阅[创建压力规则](#creating-a-pressure-rule)。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中选择&#x200B;**[!UICONTROL Re-apply the rule at the start of personalization]**&#x200B;选项。

   ![](assets/campaign_opt_pressure_example_5.png)

   此选项会覆盖&#x200B;**[!UICONTROL Frequency]**&#x200B;字段中定义的值，并在个性化阶段自动应用该规则。 有关详情，请参阅[调整计算频率](applying-rules.md#adjusting-calculation-frequency)。

1. 在&#x200B;**[!UICONTROL Pressure]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL 7d]**&#x200B;作为&#x200B;**[!UICONTROL Period considered]**，选择&#x200B;**[!UICONTROL Grouping per day]**&#x200B;作为&#x200B;**[!UICONTROL Period type]**。
1. 选择&#x200B;**[!UICONTROL Take the deliveries into account in the provisional calendar]**&#x200B;选项以包含计划的投放。

   ![](assets/campaign_opt_pressure_example_1.png)

   计算时，将考虑在投放日期前7天发送的投放以及投放日期后7天计划的投放。 有关详细信息，请参阅[设置句点](#setting-the-period)。

1. 在&#x200B;**[!UICONTROL Typologies]**&#x200B;选项卡中，将规则链接到营销活动类型。
1. 保存您的更改。

现在，为要应用压力规则的每个投放创建和配置工作流。

1. 创建营销策划。 如需详细信息，请参阅[此小节](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在营销活动的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡中，将&#x200B;**查询**&#x200B;活动添加到您的工作流。 有关使用此活动的详细信息，请参阅[此部分](../../workflow/using/query.md)。
1. 将&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动添加到工作流并打开它。 有关使用此活动的详细信息，请参阅[此部分](../../workflow/using/delivery.md)。
1. 转到&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Approvals]**&#x200B;选项卡并禁用所有审批。

   ![](assets/campaign_opt_pressure_example_2.png)

1. 在&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Typology]**&#x200B;选项卡中，引用要应用规则的营销活动类型。 定义投放的权重。

   ![](assets/campaign_opt_pressure_example_3.png)

1. 在投放中，单击&#x200B;**[!UICONTROL Scheduling]**&#x200B;并选择&#x200B;**[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]**。 在此示例中，选择&#x200B;**[!UICONTROL Use a calculation formula]**&#x200B;选项。
1. 将提取日期设置为10分钟（当前日期+ 10分钟）。
1. 将联系日期设置为第二天（当前日期+ 1天）。

   ![](assets/campaign_opt_pressure_example_4.png)

   为了成功实施压力规则排除，请确保在联系日期和时间之前以及重新应用夜间仲裁之前设置提取日期和时间。 有关详细信息，请参阅[仲裁后排除](#exclusion-after-arbitration)。

1. 取消选择&#x200B;**[!UICONTROL Confirm the delivery before sending]**&#x200B;选项并保存更改。
1. 对于要发送的每次投放，均以类似方式继续。 确保为每个投放设置所需的权重。
1. 运行相关工作流以准备和发送投放。

应用夜间仲裁时，将排除对同一收件人具有较低权重的投放。 只考虑具有最高权重的投放进行发送。 有关详情，请参阅[消息权重](#message-weight)。

考虑到本周早些时候已向相关收件人发送了电子邮件，下表显示了可以再应用于两次投放的配置示例。

<table> 
 <thead> 
  <tr> 
   <th> 投放<br /> </th> 
   <th> 审批<br /> </th> 
   <th> 权重<br /> </th> 
   <th> 提取日期/时间<br /> </th> 
   <th> 联系日期<br /> </th> 
   <th> 传递开始日期/时间<br /> </th> 
   <th> 仲裁工作流执行日期/时间<br /> </th> 
   <th> 传递状态<br /> </th> 
   <th> 已发送投放（日期/时间）<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 投放1<br /> </td> 
   <td> 已禁用<br /> </td> 
   <td> 5<br /> </td> 
   <td> 下午3点<br /> </td> 
   <td> 上午8点（第二天）<br /> </td> 
   <td> 下午2点<br /> </td> 
   <td> 夜间<br /> </td> 
   <td> 已排除<br /> </td> 
   <td> 已排除<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放2<br /> </td> 
   <td> 已禁用<br /> </td> 
   <td> 10<br /> </td> 
   <td> 下午4点<br /> </td> 
   <td> 上午9点（第二天）<br /> </td> 
   <td> 下午2点<br /> </td> 
   <td> 夜间<br /> </td> 
   <td> 已发送<br /> </td> 
   <td> 上午9点（第二天）<br /> </td> 
  </tr> 
 </tbody> 
</table>

超过两个投放的提取日期后，将在两个投放的联系日期之前重新应用夜间仲裁。 这样可查找已发送（为其处理投放、通过宽泛日志进行记录）或计划发送的所有投放（有资格接收投放的收件人，通过预测日志进行记录）的所有投放。

在压力规则定义的时间段内列出所有已发送和潜在投放后，Adobe Campaign会按权重对它们进行排序，权重最高的排在前。 达到压力规则中设置的阈值后（同一周内不超过2封电子邮件），将从投放中排除收件人。
