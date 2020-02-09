---
title: 假设模板
seo-title: 假设模板
description: 假设模板
seo-description: null
page-status-flag: never-activated
uuid: 080417c2-1c45-4404-961e-2e660d8f0436
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: addfc395-7a85-4be1-a757-a719ed34bb33
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 假设模板{#hypothesis-templates}

## 创建假设模型 {#creating-a-hypothesis-model}

通过配置假设模板，您可以定义用于测量反应的上下文，无论是投递还是选件。 这里引用了各种测量表，包括那些用于定义个人、假设和事务表之间关系的表。

要创建假设模板，请应用以下步骤：

1. 在Adobe Campaign资源管理器中，单击 **[!UICONTROL Resources>Templates>Hypothesis templates]**。

   ![](assets/response_hypothesis_model_creation_001.png)

1. 单 **[!UICONTROL New]** 击或右键单击模板列表，然后在 **[!UICONTROL New]** 下拉列表中选择。
1. 输入假设标签。
1. 指定模板是用于通过提供的假设还是交付 **[!UICONTROL Hypothesis type]**。
1. 对于 **[!UICONTROL Delivery]** 类型模板，指定是否应使用控件组进行测量(有关详细信息，请参阅假设模 [板的属性](#properties-of-a-hypothesis-template))。
1. 对于 **[!UICONTROL Delivery]** 类型模板，您可以选择特定渠道，或决定使用下拉列表将模板应用到Adobe Campaign中的所有可用渠道(有关详细信息，请参阅假设模板的 **[!UICONTROL Channel]** 属性 [](#properties-of-a-hypothesis-template))。
1. 选择要 **[!UICONTROL Execution folder]** 在其中创建并自动执行将从此模板创建的假设。
1. 选择执行设置(有关详细信息，请参阅假设模 [板执行设置](#hypothesis-template-execution-settings))。
1. 指定假设计算周期(有关详细信息，请参阅假设模 [板执行设置](#hypothesis-template-execution-settings))。

   >[!CAUTION]
   >
   >此期间由联系日期确定。

1. 在标签 **[!UICONTROL Transactions]** 中，指定假设计算所需的表和字段(有关详细信息，请参阅 [事务](#transactions))。
1. 如果您的模板已针对类 **[!UICONTROL Offer]** 型假设进行配置，则可以启用以下 **[!UICONTROL Update offer proposition status]** 选项：在这种情况下，请选择要更改的选件提案的状态。
1. 指定假设应用的范围(有关详细信息，请参阅假 [设周长](#hypothesis-perimeter))。
1. 如有必要，请使用脚本完成筛选(有关详细信息，请参阅 [Hexposition perimer](#hypothesis-perimeter))。

### 假设模板的性质 {#properties-of-a-hypothesis-template}

在模板的选项卡 **[!UICONTROL General]** 中，可以指定常规模板选项。 可用字段包括：

* **[!UICONTROL Hypothesis type]**:允许您确定模板是否应用于有关交付或选件的假设。

   您还可以选择创建适用于分发和选件的假设。

   >[!NOTE]
   >
   >如果模板应用于选件，则选 **[!UICONTROL Update offer proposition status]** 项卡中会显示该 **[!UICONTROL Transactions]** 选项。

* **[!UICONTROL Measurement with control group]**:允许您声明是否已为分发或营销活动定义控制组，并将其包含在度量指标中。 控制组（不接收交付）允许您通过将营销活动与收到交付的目标人群进行比较来评估投放后营销活动的影响。

   >[!NOTE]
   >
   >如果将模板配置为考虑控制组，但在假设所关注的交付中未定义组，则结果将仅基于目标接收者。

   有关定义和配置控制组的详细信息，请参阅 [定义控制组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

* **[!UICONTROL Channel]**:您可以选择特定渠道，或通过从下拉列表中进行选择，使假设模板可用于Adobe Campaign控制 **[!UICONTROL All channels]** 台中的所有渠道。 如果为特定渠道配置模板，则允许您在创建假设时自动过滤每个渠道的分发(请参阅创 [建假设](../../campaign/using/creating-hypotheses.md))。

   ![](assets/response_properties_001.png)

* **[!UICONTROL Execution folder]**:允许您为假设指定执行文件夹。
* **[!UICONTROL Taken into account in campaign ROI calculation]**:在计算相关营销活动的ROI时，会考虑假设结果。

### 假设模板执行设置 {#hypothesis-template-execution-settings}

通过模板的选 **[!UICONTROL General]** 项卡还可以指定假设执行参数。 可用选项如下：

* **[!UICONTROL Schedule execution for a time of low activity]**:允许您计划假设启动以优化Adobe Campaign绩效。 选中此选项后，营销活动的处理工作流会在停机期间执行假设计算。

   ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priority]**:在假设中应用的级别，以在同时执行的情况下排除假设计算顺序。

   ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatic execution]**:如有必要，可安排假设重新计算（例如，如果您要定期更新指标直到交付结束）。

   ![](assets/response_exec_settings_001.png)

   要指定计划，请应用以下流程：

   1. 单击链 **[!UICONTROL Frequency of execution...]** 接，然后单击按 **[!UICONTROL Change...]** 钮。

      ![](assets/response_frequency_execution_001.png)

   1. 配置频率、相关事件和有效期。

      ![](assets/response_frequency_execution_002.png)

   1. 单击 **[!UICONTROL Finish]** 以保存计划。

      ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL Log SQL queries in journal]**:此函数为专家用户保留。 它允许您向测量假设审计添加一个选项卡以显示SQL查询。 这使得能够在模拟完成错误时检测可能的故障。
* **[!UICONTROL Keep execution workflow]**:允许您保留在假设计算开始时自动生成的工作流。 在通过选中此选项的模板创建的假设中，可以使用生成的工作流来跟踪该过程。

   >[!CAUTION]
   >
   >仅当运行假设时出错时，才能出于调试目的激活此选项。\
   >此外，不得修改自动生成的工作流。 在以后的计算中，任何最终的修改都不会计入其他地方。\
   >如果已选中此选项，请在执行该工作流后将其删除。

### 交易 {#transactions}

此选项卡包含各种字段和表，允许您根据事务保存收件人反应的历史记录。 有关专用于响 [应管理的表的详细信息](../../configuration/using/about-schema-reference.md) ，请参阅配置指南。

* **[!UICONTROL Schema (reaction log storage)]**:选择收件人反应表。 Adobe Campaign中的现成表是 **NmsRemaMatchRcp**。
* **[!UICONTROL Transaction schema]**:选择假设将涉及的表，即交易或购买表。
* **[!UICONTROL Querying schema]**:选择过滤假设的标准。
* **[!UICONTROL Link to individuals]**:选择个人与用作事务架构的表之间的链接。
* **[!UICONTROL Link to the household]**:如果您希望将某个家庭的所有成员包含在假设中，请在交易架构中选择指向该家庭的链接。 此字段为可选字段。
* **[!UICONTROL Transaction date]**:此字段为可选字段，但建议使用此字段可定义假设计算的范围。
* **[!UICONTROL Measurement period]**:允许您配置开始和结束日期，在此期间执行假设并恢复购买行。

   当假设链接到分发时，在直接邮件发送的联系日期之后几天或电子邮件或短信发送的发送日期之后自动触发测量。

   ![](assets/response_measurement_001.png)

   如果假设是在匆忙中发起的，那么如果想立即触发，就可以强迫它。 否则，它根据配置的计算日期结束自动触发，该计算日期基于假设创建日期(请参阅 [Creating a hextions on a delivery](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery))。

* **[!UICONTROL Transaction/Margin amount]**:这些字段是可选的，允许您自动计算周转指示符(请参阅“指 [示符](../../campaign/using/hypothesis-tracking.md#indicators)”)。
* **[!UICONTROL Unit amount]**:允许您设置计算收入的金额(请参阅 [指标](../../campaign/using/hypothesis-tracking.md#indicators))。

   ![](assets/response_transactions_001.png)

* **[!UICONTROL Additional measures and data]**:允许您从不同表中的字段指定其他报告度量或轴。
* **[!UICONTROL Update offer proposition status]**:允许您在假设确定选件收件人时更改选件主张的状态。

   ![](assets/response_offer_status_001.png)

### 假设周长 {#hypothesis-perimeter}

在定义了事务表和假设所涉及的字段后，您可以使用过滤器指定目标事务和提交来细化假设的范围。 您还可以使用JavaScript脚本显式指向事务表中引用的产品。

* **筛选事务**:在该选 **[!UICONTROL Scope]** 项卡中，您可以配置假设的过滤器。 操作步骤：

   1. 单击链 **[!UICONTROL Edit query]** 接。

      ![](assets/response_scope_filtering_001.png)

   1. 指定筛选条件。

      ![](assets/response_scope_filtering_002.png)

   1. 选择假设所涉及的事务。

      ![](assets/response_scope_filtering_003.png)

* **收件人过滤**:在该选 **[!UICONTROL Scope]** 项卡中，您可以将假设限制为与消息（传送、收件人、电子邮件地址、服务等）链接的任何信息：

   1. 单击链 **[!UICONTROL Add a filter]** 接，然后 **[!UICONTROL Edit query]**。

      ![](assets/response_scope_filtering_004.png)

   1. 指定筛选条件。

      ![](assets/response_scope_filtering_005.png)

   1. 单击 **[!UICONTROL Finish]** 以保存查询。

      ![](assets/response_scope_filtering_006.png)

* **脚本**:您可以使用JavaScript脚本在假设设置执行过程中动态过载。

   为此，请单击链接， **[!UICONTROL Advanced settings]** 然后输入所需的脚本。

   >[!NOTE]
   >
   >此选项适用于专家用户。

   ![](assets/response_hypothesis_model_creation_011.png)

## 示例：在交货上创建假设模板 {#example--creating-a-hypothesis-template-on-a-delivery}

在此示例中，我们将在直接邮寄类型发送上创建一个假设模板。 假设所基于的事务处理表(**示例中的购买** )包含链接到文章或产品的购买行。 我们要配置我们的模型，以在购买表中为文章或产品创建假设。

1. 在Adobe Campaign资源管理器中，转到节 **[!UICONTROL Resources > Templates > Hypothesis templates]** 点。
1. 单击 **[!UICONTROL New]** 以创建模板。

   ![](assets/response_hypothesis_model_example_001.png)

1. 更改模板标签。

   ![](assets/response_hypothesis_model_example_002.png)

1. 选择 **[!UICONTROL Deliveries]** 为假设类型。
1. 通过选中相关框，指定交付可包含控件组。
1. 选择渠 **[!UICONTROL Direct mail]** 道。

   >[!NOTE]
   >
   >由于模板特定于直邮递送，因此使用此模型创建的假设可能不会链接到任何其他递送类型。

1. 在选项卡 **[!UICONTROL Transactions]** 中，选择收件人反应表。

   ![](assets/response_hypothesis_model_example_006.png)

1. 在字段 **[!UICONTROL Transactions schema]** 中，选择购买表。

   ![](assets/response_hypothesis_model_example_007.png)

1. 在字段中选择购买 **[!UICONTROL Querying schema]** 行。

   ![](assets/response_hypothesis_model_example_008.png)

1. 选择链接到购买表的收件人。

   ![](assets/response_hypothesis_model_example_009.png)

1. 选择链接到购买日期的字段。

   这允许您定义假设的时间范围。 此阶段不是强制性的，但建议这样做。

   ![](assets/response_hypothesis_model_example_010.png)

1. 配置5到25天的计算期。

   ![](assets/response_hypothesis_model_example_005.png)

1. 在选项 **[!UICONTROL Scope]** 卡中，单 **[!UICONTROL Edit query]** 击以创建假设的过滤器。

   ![](assets/response_hypothesis_model_example_011.png)

   这样创建的模板使您能够对购买表中的产品或文章运行假设。

1. 单击 **[!UICONTROL Save]** 以记录您的模板。

