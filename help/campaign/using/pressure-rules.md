---
solution: Campaign Classic
product: campaign
title: 压力规则
description: 压力规则
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '3253'
ht-degree: 4%

---


# 压力规则{#pressure-rules}

## 关于营销疲劳 {#about-marketing-fatigue}

实施销售压力管理可以避免在数据库中过多地招募人员，也称为营销疲劳。 为此，您可以为每个收件人定义最大消息数。 它还允许您在活动之间执行仲裁规则，以便向目标受众发送最佳消息。

**压力** 规则，管理营销疲劳，例如，将要发送给人群的信件数量限制为2个，选择最符合用户群利益的通信，避免向不满的客户发送短信等。

活动根据定义的阈值和消息权重来选择。

* 阈值是指定收件人在指定时间段内授权的最多投放数。 它可以是设置的，也可以是变量。 它是在类型规则设置中设置或计算的。 请参阅 [最大消息数](#maximum-number-of-messages)。
* 投放权重使您能够在压力管理框架内确定最优先的投放。 具有最高权重的消息具有优先级。 请参阅 [消息权重](#message-weight)。

仲裁包括确保权重大于进行中活动的计划活动不会导致过度用户档案请求：如果是，则用户档案将从投放中排除。

仲裁标准(消息权重和／或阈值)可能因以下两种信息而异：

* 收件人首选项，即声明性信息：新闻稿订阅,收件人状态(客户或潜在客户),
* 收件人行为：购买、访问的链接等。

在分析阶段，将应用用于定义合格消息的仲裁规则。 对于每个收件人和相关期间，如果以下公式为真，则将发送消息： **（已发送的消息数）+(权重较大的消息数)&lt;阈值**。

否则，收件人将为 **[!UICONTROL Excluded by arbitration]**。 有关此问题的详细信息，请参 [阅仲裁后排除](#exclusion-after-arbitration)。

## Creating a pressure rule {#creating-a-pressure-rule}

要使用Adobe Campaign在活动之间建立仲裁，请通过创建活动类型并定义链接的类型规则(压&#x200B;**力规** 则)进行开始。

要创建和配置 **[!UICONTROL Pressure]** 分类规则，请应用以下步骤：

1. 在列表规则活动类型中，单击 **[!UICONTROL New]** 列表上方的图标。

   ![](assets/campaign_opt_create_a_rule_01.png)

1. 在新规 **[!UICONTROL General]** 则的选项卡中，选择压力类 **型规** 则，并为其输入名称和说明。

   ![](assets/campaign_opt_create_a_rule_02.png)

1. 根据需要更改执行顺序。 当多个类型规则作为集应 **[!UICONTROL Typology]** 用时，首先应用顺序较低的规则。 For more on this, refer to [Execution order](../../campaign/using/applying-rules.md#execution-order).
1. 在该部 **[!UICONTROL Calculation parameters]** 分中，如果您希望在下次每日重新仲裁执行之后保存目标，请定义一个频率。 有关此问题的详细信息，请参 [阅调整计算频率](../../campaign/using/applying-rules.md#adjusting-calculation-frequency)。
1. 单击标 **[!UICONTROL Pressure]** 签，然后选择应用类型规则的日历期间。

   ![](assets/campaign_opt_create_a_rule_03.png)

   该规则将适用于其联系日期已包括在相关期间的投放。

   >[!NOTE]
   >
   >只有在选中该选项时，才会考 **[!UICONTROL Take the deliveries into account in the provisional calendar]** 虑计划投放。 For more on this, refer to [Setting the period](#setting-the-period).

1. 定义计算最大消息数的方法。

   阈值表示在相关期间可发送到收件人的最大消息数。

   默认情况下，阈值为常量，您需要指定规则授权的消息数量上限。

   ![](assets/campaign_opt_create_a_rule_03b.png)

   要定义变量阈值，请在字 **[!UICONTROL Depends on the recipient]** 段中选 **[!UICONTROL Type of threshold]** 择值，然后使用右侧的图标打开表达式编辑器。

   ![](assets/campaign_opt_create_a_rule_04.png)

   有关详细信息，请参 [阅最大消息数](#maximum-number-of-messages)。

1. 指定计算投放权重的方法。

   每个投放都有一个权重，即表示其优先级的值：这允许活动之间进行仲裁。 权重使用在类型规则和／或其属性中定义的公式计算。 For more on this, refer to [Message weight](#message-weight).

1. 默认情况下，所有消息都会考虑阈值计算式。通过 **[!UICONTROL Restriction]** 该选项卡可以过滤与类型规则相关的消息：

   * 在此选项卡的上半部分，您可以限制相关收件人。
   * 通过此选项卡的下半部分，可以过滤要计数的消息。

      在以下示例中，只考虑保存在NewContacts文 **件夹中的收件人** ，并且会考虑以Newsletter开头 **的投放** 。
   ![](assets/campaign_opt_create_a_rule_05.png)

1. 通过 **[!UICONTROL Typologies]** 该选项卡可视图应用此规则或将规则链接到一个或多个现有类型的活动类型。 For more on this, refer to [Applying typologies](../../campaign/using/about-campaign-typologies.md#applying-typologies).

## 定义阈值和权重 {#defining-thresholds-and-weights}

### 最大消息数 {#maximum-number-of-messages}

每个压力规则定义一个阈值，即在给定的时间段内可以发送到一个收件人的最大消息数。 达到此阈值后，只有在所考虑的时段结束后，才会再进行投放。此过程允许您在消息超过设置的阈值时自动从投放中排除收件人，从而避免过度请求。

阈值可以是常量，也可以是由具有变量的公式计算。 这意味着在给定的时间段内，阈值可能因收件人而异，甚至对于同一收件人也可能不同。

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>输入 **0** 作为阈值可阻止在所考虑的期间内目标群的所有投放。

**示例:**

您可以根据收件人所属的段索引授权消息数。 这意味着属于Web区段的收件人可能会收到比其他收件人更多的消息。 类型 **[!UICONTROL Iif (@origin='Web', 5, 3)]** 公式可授权将5条消息投放给收件人，将3条消息分配给其他区段。 配置将如下：

![](assets/campaign_opt_pressure_sample.png)

要定义阈值，您可以使用链接到定位维度的维：例如，要包含传递给存储在收件人表中的访客用户档案的消息(有关详细信息，请参阅此部分 [](../../web/using/use-case--creating-a-refer-a-friend-form.md))，或避免每周向与收件人关联的维度中标识的同一家庭发送多条消息（可能指多个电子邮件地址）。

要这样做，请选 **[!UICONTROL Count messages on a linked dimension]** 择选项，然后选择访客或联系人表。

### 消息权重 {#message-weight}

每个投放都有一个权重，它代表其优先级。 默认情况下，投放的权重设置为5。 压力规则允许您定义要应用压力规则的投放的权重。

权重可以通过公式设置或计算，以适合收件人。 例如，您可以根据权重兴趣定义投放的收件人。

>[!CAUTION]
>
>在类型规则中定义的权重可以针对每个投放在选项卡中单独重载 **[!UICONTROL Properties]** 。 单击选 **[!UICONTROL Typology]** 项卡以选择活动类型，并根据需要指定要应用的权重。\
>但是，在A权重中声明的类型规则不会用于计算B类型规则:此权重仅涉及使用A规则的投放。

**示例:**

在以下示例中，我们要将音乐新闻稿的权重与其收件人的倾向得分相关联。 操作步骤：

1. 创建新字段以存储收件人倾向得分。 这个字 **段@Music** ，将丰富调查和在线投票的答案、收集的跟踪数据等。
1. 创建类型规则以根据此字段计算消息权重。

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. 将此规则应用于包含以下主题的消息：新闻稿、特殊优惠等。 这些投放的权重，因此其优先级取决于每个收件人的倾向得分。

## Setting the period {#setting-the-period}

压力规则在 **n**-day轧制期间定义。

该期间在规则的选 **[!UICONTROL Pressure]** 项卡中配置。 您可以指定天数，并根据需要选择要应用的分组类型（天、周、月、季度等）。

分组类型允许您将字段 **[!UICONTROL Period considered]** 扩展到该期间日期的整天、日历周、日历月或日历年。

例如，压力规则定义每周2条消息的阈值，每个日历月分组，将阻止在同一周内投放多于2条消息，而在同一日历月内。 警告，如果期间与两个月重叠，则计算阈值将考虑这两个日历月的投放，因此可能阻止第二个月内的所有新投放。

>[!NOTE]
>
>默认情况下，在计算阈值时只考虑已发送的投放。 如果 **[!UICONTROL Take the deliveries into account in the provisional calendar]** 您还要考虑在相关期间计划的投放，请选中此选项。 在这种情况下，将审议期加倍，使未来投放和以前的能够融为一体。\
>要将考虑的投放限制为2周，您可以：
>
>* 在 **字段中** ，输入 **[!UICONTROL Concerned period]** 15d:在计算时，将考虑在适用规则的投放之日前两周前发送的投放,
>
>  
或者
>
>* 在 **字段中输入** 7d **[!UICONTROL Period considered]** 并检查 **[!UICONTROL Take the deliveries into account in the provisional calendar]**\
   >选项：在计算中将考虑在投放日期前7天以及在应用规则的投放日期后7天以前计划的投放。
>
>
期间开始日期取决于数据库的配置方式。

例如，如果对日期为12/11的投放应用15天压力规则而不对其分组，则在11/27和12/12之间将考虑投放。 如果压力规则考虑临时日历中的投放，则将考虑11/27至12/27之间安排的所有投放。 最后，如果在规则中按日历月配置分组，则在计算阈值时（从11月1日到12月31日）将考虑11月和12月的所有投放。

>[!CAUTION]
>
>**常见案例**
>要确保不考虑当前日历周的投放，也不考虑计算阈值上周的，请指定“0”，然后选择“按日历周分组”作为 **[!UICONTROL Period considered]****[!UICONTROL Period type]**。
> 
>当期间大于0（例如1）时，计算阈值可以考虑前一天的投放。 因此，如果前一天与上一日历周对应，并且所选期间类型为“按日历周分组”，则将考虑计算阈值中所有上一周。

**示例:**

我们希望创建一个压力规则，该规则将每两周的请求限制为3条消息，并将分组限制为日历月。

![](assets/campaign_opt_pressure_period_sample_1a.png)

我们使用同一权重接收6个新闻稿，计划于05/30、06/3、06/8、06/12、06/22和06/30。

![](assets/campaign_opt_pressure_period_sample_0.png)

原定于6月12日和30日的投放将不发送：06/12投放将超过每两周3条消息的阈值，第30个投放将超过每个日历月授权通信的阈值。

![](assets/campaign_opt_pressure_period_sample_1.png)

在分析阶段，仲裁会排除这些投放的所有收件人:

![](assets/campaign_opt_pressure_period_sample_2.png)

对于同一规则，如果按季度对投放进行分组， **则也将排除第5号新闻稿的** ，并且不会发送该收件人。

最后，如果未选择分组，则只 **发送第4号新闻稿** ，因为它与前三个新闻稿安排在相同的2周时间段内。

>[!NOTE]
>
>更改类型规则定义时，可以创建 **模拟** ，以控制其对所应用投放的影响并监视投放对彼此的影响。 For more on this, refer to [Campaign simulations](../../campaign/using/campaign-simulations.md).

## 仲裁后排除 {#exclusion-after-arbitration}

仲裁通过技术工作流和工作流 **[!UICONTROL Forecasting]** 每晚重新应 **[!UICONTROL Campaign jobs]** 用。

工 **[!UICONTROL Forecasting]** 作流会预先计算进行中期间(从开始日期到当前日期)的数据，允许在分析期间应用类型规则。 它还重新计算每晚仲裁的排除计数器。

因此，对于每个收件人,Adobe Campaign检查要发送的消息数是否未超过阈值，同时考虑到在相关期间已发送的消息数。 此信息是一个 **指标**，因为所有计算都在投放时更新。

如果此数量超过阈值，则应用活动类型中定义的仲裁规则，并将收件人从权重较低的活动中排除。

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>如果多个投放的得分相等，则将发送计划在最早日期的活动。

## 压力规则的使用案例 {#use-cases-on-pressure-rules}

### 基于准则调整阈值 {#adapting-the-threshold-based-on-criterion}

我们希望创建一个类型规则，防止每周向客户投放4条以上邮件，每周向潜在客户发送2条邮件。

要识别客户和潜在客户，请使 **[!UICONTROL Status]** 用字段，该字段包含0(对于潜在客户)和1（对于客户）。

要创建规则，请应用以下步骤：

1. Create a new **Pressure** type typology rule.
1. Edit the **[!UICONTROL Pressure]** tab: in the **[!UICONTROL Maximum number of messages]** section, we want to create a formula to calculate the threshold depending on each recipient. 在字 **[!UICONTROL Depends on the recipient]** 段中选 **[!UICONTROL Threshold type]** 择值，然 **[!UICONTROL Edit expression]** 后单击字段右 **[!UICONTROL Formula]** 侧。

   单击按 **[!UICONTROL Advanced parameters]** 钮以定义计算公式。

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. Select the **[!UICONTROL Edit the formula using an expression]** option and click **[!UICONTROL Next]**.

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. In the list of functions, double-click the **Iif** function in the **[!UICONTROL Others]** node.

   Then select the recipients&#39; **Status** in the **[!UICONTROL Available fields]** section.

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   输入以下公式： **Iif(@status=0,2,4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   使用此公式后，如果 Status 等于 0，则分配值“2”；对于所有其他 Status，则分配值“4”。

   单击 **[!UICONTROL Finish]** 以批准公式。

1. 指示应用规则的期间：在此情况下为计数每周的邮件数，需要7天。

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. 保存规则以批准创建。

现在将您刚刚创建的规则链接到类型学，以将其应用于投放。 操作步骤：

1. 创建活动类型。
1. 转到选 **[!UICONTROL Rules]** 项卡，单 **[!UICONTROL Add]** 击按钮并选择刚刚创建的规则。

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 保存类型学：是否将其添加到现有字体的列表。

要在投放中使用此类型，请在投放属性的选项卡中选择它，如 **[!UICONTROL Typology]** 下所示：

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>可以在投放模板中定义分类，以自动应用至使用此模板创建的所有投放。

在投放分析期间，投放收件人会根据已发送给投放的投放数量从中排除（如果适用）。 要视图此信息，您可以：

* 视图分析结果：

   ![](assets/campaign_opt_pressure_sample_1_8.png)

* 编辑投放，然后单 **[!UICONTROL Delivery]** 击选项卡和 **[!UICONTROL Exclusions]** 子选项卡：

   ![](assets/campaign_opt_pressure_sample_1_9.png)

* 单击选 **[!UICONTROL Audit]** 项卡，然 **[!UICONTROL Causes of exclusions]** 后单击子选项卡以显示排除数和应用的类型规则:

   ![](assets/campaign_opt_pressure_sample_1_10.png)

### 基于行为计算投放权重 {#calculating-the-delivery-weight-based-on-behavior}

您可以根据收件人行为定义压力规则：因此，权重的投放可以适应不同收件人的标准。 例如，您可以决定根据收件人是否访问过您的Internet站点、是否点击了上一份新闻稿的特定部分、订阅了信息服务，甚至基于调查的答案、在线游戏等，发送消息。

在以下示例中，我们要创建一个投放,权重为5。 此权重丰富了基于收件人行为的倾向得分：已从此站点订购的客户的得分为5，而从未在线订购的客户的得分为4。

要执行此类配置，您需要使用公式来定义消息权重。 倾向得分和调查答案的信息必须在数据模型中访问。 在我们的示例中， **已添加** “倾向”字段。

应用以下配置步骤：

1. Create a new **Pressure** type typology rule.
1. 编辑选 **[!UICONTROL Pressure]** 项卡。 我们希望创建一个阈值公式，该公式将基于每个收件人:单击 **[!UICONTROL Edit expression]** 字段右侧的图 **[!UICONTROL Weight formula]** 标。

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. 默认情况 **下** ，值5显示在表达式编辑器的上半部分。 我们要将每个收件人的倾向得分添加到此权重:将光标放在5的右侧，输入+字 **符** ，然后选择 **倾向字段** 。

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. 然后为已购买的收件人增加更高的价值。 对他们来说，投放的权重必须增加5，而对其他人来说，只增加4。

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. 单击 **[!UICONTROL Finish]** 以保存此规则。
1. 将规则链接到活动类型，并在投放中引用此类型以批准它。

### 仅发送加权最高的消息 {#sending-only-the-highest-weighted-messages}

您希望在同一周内向每个收件人发送不超过2条消息（每天最多2条消息），并且您只希望向其发送权重较高的消息。

为此，您需要为同一收件人计划具有不同权重的多个投放，并应用压力规则以排除具有较低权重的投放。

首先，配置压力规则。

1. 创建压力规则。 有关此问题的详细信息，请 [参阅创建压力规则](#creating-a-pressure-rule)。
1. In the **[!UICONTROL General]** tab, select the **[!UICONTROL Re-apply the rule at the start of personalization]** option.

   ![](assets/campaign_opt_pressure_example_5.png)

   此选项会覆盖字段中定义的 **[!UICONTROL Frequency]** 值，并在个性化阶段自动应用规则。 有关此问题的详细信息，请参 [阅调整计算频率](../../campaign/using/applying-rules.md#adjusting-calculation-frequency)。

1. In the **[!UICONTROL Pressure]** tab, select **[!UICONTROL 7d]** as the **[!UICONTROL Period considered]** and **[!UICONTROL Grouping per day]** as the **[!UICONTROL Period type]**.
1. 选择选 **[!UICONTROL Take the deliveries into account in the provisional calendar]** 项以包含计划投放。

   ![](assets/campaign_opt_pressure_example_1.png)

   在计算中，将考虑在投放日期之前7天以及在投放日期之后7天之前计划的投放。 For more on this, refer to [Setting the period](#setting-the-period).

1. 在选项卡 **[!UICONTROL Typologies]** 中，将规则链接到活动类型。
1. 保存更改。

现在，为要应用压力规则的每个投放创建并配置一个工作流。

1. 创建营销策划. 如需详细信息，请参阅[此部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在活动 **[!UICONTROL Targeting and workflows]** 的选项卡中，将查询 **活动** 添加到工作流。 For more on using this activity, refer to [this section](../../workflow/using/query.md).
1. 向工作 **[!UICONTROL Email delivery]** 流中添加活动并将其打开。 For more on using this activity, refer to [this section](../../workflow/using/delivery.md).
1. 转到选项 **[!UICONTROL Approvals]** 卡并禁 **[!UICONTROL Delivery properties]** 用所有批准。

   ![](assets/campaign_opt_pressure_example_2.png)

1. 在的选 **[!UICONTROL Typology]** 项卡中， **[!UICONTROL Delivery properties]**&#x200B;引用要应用规则的活动类型。 定义权重。

   ![](assets/campaign_opt_pressure_example_3.png)

1. 在投放中，单击 **[!UICONTROL Scheduling]** 并选择 **[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]**。 在此示例中，选择选 **[!UICONTROL Use a calculation formula]** 项。
1. 将提取日期设置为10分钟（当前日期+ 10分钟）。
1. 将联系日期设置为下一天（当前日期+ 1天）。

   ![](assets/campaign_opt_pressure_example_4.png)

   要成功实施压力规则排除，请确保在联系日期和时间之前以及重新应用晚间仲裁之前设置提取日期和时间。 有关此问题的详细信息，请参 [阅仲裁后排除](#exclusion-after-arbitration)。

1. 取消选 **[!UICONTROL Confirm the delivery before sending]** 择选项并保存更改。
1. 对于要发送的每个投放，以同样方式继续。 确保为每个权重设置所需的投放。
1. 运行相关工作流以准备和发送投放。

在应用晚间仲裁时，对于同一收件人具有较低权重的投放将被排除。 只有具有最高权重的投放才会被考虑发送。 For more on this, refer to [Message weight](#message-weight).

考虑到本周早些时候已经向相关收件人发送了电子邮件，下表显示了可再应用于两个投放的配置示例。

<table> 
 <thead> 
  <tr> 
   <th> 投放<br /> </th> 
   <th> 批准<br /> </th> 
   <th> 权重<br /> </th> 
   <th> 提取日期／时间<br /> </th> 
   <th> 联系日期<br /> </th> 
   <th> 投放开始日期／时间<br /> </th> 
   <th> 仲裁工作流执行日期／时间<br /> </th> 
   <th> 投放状态<br /> </th> 
   <th> 投放发送（日期／时间）<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivery 1<br /> </td> 
   <td> 已禁用<br /> </td> 
   <td> 5<br /> </td> 
   <td> 3pm<br /> </td> 
   <td> 早8点（次日）<br /> </td> 
   <td> 2pm<br /> </td> 
   <td> 每晚<br /> </td> 
   <td> 已排除<br /> </td> 
   <td> 已排除<br /> </td> 
  </tr> 
  <tr> 
   <td> Delivery 2<br /> </td> 
   <td> 已禁用<br /> </td> 
   <td> 10<br /> </td> 
   <td> 4pm<br /> </td> 
   <td> 上午9点（次日）<br /> </td> 
   <td> 2pm<br /> </td> 
   <td> 每晚<br /> </td> 
   <td> 已发送<br /> </td> 
   <td> 上午9点（次日）<br /> </td> 
  </tr> 
 </tbody> 
</table>

在两个提取的投放日期过后，在两个投放的联系日期之前重新应用晚间仲裁。 这允许查找所有已发送的投放(对其处理投放、通过广泛日志记录的收件人)或计划发送的(有资格接收投放的收件人，通过预测日志记录)。

一旦所有投放都已发送，并且可能的Adobe Campaign已列在压力规则定义的时间段内，将按权重对它们进行排序，其中加权最高优先。 当达到压力规则中设置的阈值（在同一周内不超过2封电子邮件）时，收件人将从投放中排除。
