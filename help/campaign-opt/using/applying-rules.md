---
product: campaign
title: 应用规则
description: 应用规则
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 09ec0fc0-76ed-4c73-8bdf-c931e2103aa9
source-git-commit: 5806690f764d2e5dfb5651597ff68b33bb399b44
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 9%

---

# 应用规则{#applying-rules}

![](../../assets/common.svg)

## 对投放应用分类 {#applying-a-typology-to-a-delivery}

要应用您创建的分类规则，您需要将其与分类关联，然后在投放中引用此分类。 操作步骤：

1. Create a campaign typology.

   Typologies are accessed via the **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** node.

1. 转到 **[!UICONTROL Rules]** ，单击 **[!UICONTROL Add]** 按钮，然后选择要应用于此分类的规则。

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 保存分类：是否会将其添加到现有分类列表。
1. 打开要将规则应用到的投放。
1. 打开投放属性并访问 **[!UICONTROL Typology]** 选项卡。
1. 在下拉列表中选择分类。

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >可以在投放模板中定义分类，以自动应用至使用此模板创建的所有投放。

## 定义应用程序条件 {#defining-application-conditions}

您可以根据需要限制规则的应用程序字段（控制规则除外）。

可以配置分类规则，以便它们仅与其链接的特定投放相关，或与投放目标中的特定收件人相关。

To define the application conditions of a rule, click the **[!UICONTROL Edit the rule application conditions...]** link in the **[!UICONTROL General]** tab.

然后，使用查询编辑器定义筛选条件。 In the following example, the capacity rule concerns only deliveries with the word &#39;offer&#39; in their label or deliveries created before April 1st 2013.

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>对于筛选规则，您可以选择筛选条件的应用条件：它们可以依赖投放或投放大纲。 For more on this, refer to [Conditioning a filtering rule](filtering-rules.md#conditioning-a-filtering-rule).

## 调整计算频率 {#adjusting-calculation-frequency}

每天晚上，通过数据库清理工作流自动重新执行仲裁。 However, values can be saved beyond this period.

事实上，某些计算使用的值每天都不会更改。 因此，每天重新计算数据和使数据库无偿过载将无关紧要。 例如，如果某个流程通过每周客户倾向得分和购买信息来丰富营销数据库，则无需每天重新计算基于这些值的数据。

To do this, the **[!UICONTROL Frequency]** field of the **[!UICONTROL General]** tab lets you define a maximum period during which targeting is saved. 默认情况下，该值为 **0** 表示在下次执行每日重新仲裁之前，计算仍然有效。

要保存超出此时段的结果，请在 **[!UICONTROL Frequency]** 字段：此时间段过期后，将重新应用所有规则。

的 **[!UICONTROL Re-apply the rule at the start of personalization]** 选项允许您在个性化阶段自动应用规则，包括在 **[!UICONTROL Frequency]** 字段，则此变量将仍然有效。

## 选择规则应用程序阶段 {#selecting-the-rule-application-phase}

在相关投放的定位、分析和个性化阶段，会按特定顺序应用分类规则。

### 执行顺序 {#execution-order}

在标准操作模式下，按以下顺序应用规则：

1. 控制规则（如果在开始定向时应用）。
1. 筛选规则：

   * 地址鉴别的本机应用程序规则：/隔离地址/地址质量上的已定义地阻止列表址/未验证地址/地址。
   * 筛选用户定义的规则。
   * 地址或标识符上的重复数据删除规则（如有必要，可应用）。

1. 压力规则.
1. 容量规则。
1. 控制规则（如果在定向结束时应用）。
1. 控制规则（如果在开始个性化时应用）。如果用户规则（过滤/压力/容性）已过期，需要重新计算，则会在此步骤中应用这些规则。
1. 控制规则（如果在个性化结束时应用）。

>[!NOTE]
>
>If you are working with Campaign Interaction module, offer eligibility rules are applied at the same time as filtering rules (for offers found in the delivery outlines) or during the personalization phase, during the call to the offer engine.

您可以使用 **[!UICONTROL General]** 选项卡。 When several rules are executed during the same message processing phase, you can configure their execution sequence in the **[!UICONTROL Execution sequence]** field.

例如，执行顺序为20的压力规则将在执行顺序为30的压力规则之前执行。

### 控制规则 {#control-rules}

对于 **[!UICONTROL Control]** 规则时，您可以决定在投放生命周期的哪个时间点应用规则（在定位之前或之后、开始个性化时、分析结束时）。 Select the value to apply in the drop-down list of the **[!UICONTROL Phase]** field, in the **[!UICONTROL General]** tab of the typology rule.

![](assets/campaign_opt_define_control_phase.png)

可能的值包括：

* **[!UICONTROL At the start of targeting]**

   要防止在发生错误时执行个性化步骤，您可以在此处应用控制规则。

* **[!UICONTROL After targeting]**

   如果您需要知道目标的音量以应用控制规则，请选择此阶段。

   例如， **[!UICONTROL Check proof size]** 控制规则应用于每个定位阶段之后：如果校样收件人过多，此规则将阻止进行消息个性化。

* **[!UICONTROL At the start of personalization]**

   如果控件涉及邮件个性化的批准，则必须选择此阶段。 在分析阶段期间执行消息个性化。

* **[!UICONTROL At the end of the analysis]**

   当检查要求完成消息个性化时，请选择此阶段。

## 其他配置 {#additional-configurations}

### 控制传出SMTP流量 {#control-outgoing-smtp-traffic}

As an option, you can use the **[!UICONTROL Managing affinities with IP addresses]** field to link deliveries to the delivery server (MTA) this affinity. 这样，您就可以将特定投放的电子邮件数量限制到计算机或输出地址。

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>Affinity management does not apply for **[!UICONTROL Filtering]** typologies.\
>相关性在Adobe Campaign服务器上的实例配置文件中定义。 如需详细信息，请参阅[此部分](../../installation/using/about-initial-configuration.md)。

### 营销活动优化和分布式营销 {#campaign-optimization-and-distributed-marketing}

The **[!UICONTROL Distributed Marketing]** tab lets you define the re-mapping of typologies and/or rules which applies when a shared campaign is ordered and/or reserved. 为本地实体定义的分类/规则（链接到为中央实体定义的分类）将替换链接到中央实体的规则/分类。 通过重新映射，您可以根据对营销活动进行排序的本地实体来调整中央实体规则。

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>在分类和分类规则中， **[!UICONTROL Distributed Marketing]** 选项卡（如果您的许可证包含此选项）。请查看许可协议。\
>有关分布式营销的更多信息，请参阅 [关于分布式营销](../../distributed/using/about-distributed-marketing.md).
