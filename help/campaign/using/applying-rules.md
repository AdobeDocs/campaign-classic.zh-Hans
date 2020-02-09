---
title: 应用规则
seo-title: 应用规则
description: 应用规则
seo-description: null
page-status-flag: never-activated
uuid: 4472fc0d-d717-4603-8472-bdaf2835a02a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: a0e76d27-bedd-4f81-b4d2-1221444e670e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 应用规则{#applying-rules}

## 将类型学应用于交付 {#applying-a-typology-to-a-delivery}

要应用您创建的排版规则，您需要将其关联到排版，然后在交付中引用此排版。 操作步骤：

1. 创建营销活动类型学。

   可通过 **[!UICONTROL Administration > Campaign Management > Typology management]** >节点访 **[!UICONTROL Typologies]** 问类型。

1. 转到选项卡 **[!UICONTROL Rules]** ，单击按钮并 **[!UICONTROL Add]** 选择要应用于此排版的规则。

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 保存类型学：是否已添加到现有类型列表。
1. 打开要将规则应用到的交付。
1. 打开交付属性并访问选 **[!UICONTROL Typology]** 项卡。
1. 在下拉列表中选择类型学。

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >可以在分发模板中定义类型，以自动应用到使用此模板创建的所有分发。

## 定义应用条件 {#defining-application-conditions}

您可以根据自己的需求限制规则的应用程序字段（控制规则除外）。

可以配置排版规则，使其仅涉及与其链接的特定交付，或者涉及交付目标中的特定收件人。

要定义规则的应用程序条件，请单击选 **[!UICONTROL Edit the rule application conditions...]** 项卡中的链 **[!UICONTROL General]** 接。

然后使用查询编辑器定义筛选条件。 在以下示例中，容量规则仅涉及在标签中带有“选件”字样的交货或在2013年4月1日之前创建的交货。

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>对于筛选规则，您可以选择筛选条件的应用条件：它们可以取决于交付或交付大纲。 有关详细信息，请参阅 [调整过滤规则](../../campaign/using/filtering-rules.md#conditioning-a-filtering-rule)。

## 调整计算频率 {#adjusting-calculation-frequency}

仲裁通过数据库清理工作流程在每晚自动执行。 但是，值可以保存到此时间段之后。

事实上，一些计算使用的值不会每天发生变化。 因此，每天重新计算数据并使数据库无所谓地过载，这将无关紧要。 例如，如果某个流程每周都通过客户倾向得分和购买信息丰富了营销数据库，那么基于这些值的数据就无需每天重新计算。

为此，选项卡 **[!UICONTROL Frequency]** 的字段允许您 **[!UICONTROL General]** 定义保存定位的最长时间段。 默认情况下，值 **0** 表示计算在下次执行每日重新仲裁之前仍然有效。

要保存超过此期间的结果，请在字段中输入大于12的 **[!UICONTROL Frequency]** 值：此期间到期后，将重新应用所有规则。

该选 **[!UICONTROL Re-apply the rule at the start of personalization]** 项允许您在个性化阶段自动应用规则，包括字段中所述的期间 **[!UICONTROL Frequency]** 是否仍然有效。

## 选择规则应用程序阶段 {#selecting-the-rule-application-phase}

在其所关注的递送的定位、分析和个性化阶段，在特定序列中应用排版规则。

### 执行顺序 {#execution-order}

在标准操作模式下，这些规则按以下顺序应用：

1. 控制规则（如果在定位开始时应用它们）。
1. 筛选规则:

   * 地址资格的本机应用程序规则：定义的地址／未验证的地址／列入黑名单的地址／隔离地址／地址质量。
   * 过滤用户定义的规则。
   * 地址或标识符上的重复数据删除规则（如有必要，应用）。

1. 压力规则。
1. 容量规则。
1. 控制规则（如果在定位结束时应用它们）。
1. 控制规则（如果在个性化开始时应用它们）。 如果用户规则（过滤／压力／电容性）已过期，需要重新计算，则将在此步骤中应用这些规则。
1. 控制规则（如果在个性化结束时适用）。

>[!NOTE]
>
>如果您使用“营销活动交互”模块，则在调用选件引擎期间，会在筛选规则（在交付大纲中找到的选件）或个性化阶段同时应用选件资格规则。

您可以使用规则选项卡中的相应字段调整具有相同类型的规则 **[!UICONTROL General]** 的执行顺序。 当在同一消息处理阶段执行多个规则时，您可以在字段中配置其执行 **[!UICONTROL Execution sequence]** 顺序。

例如，执行顺序为20的压力规则将在执行顺序为30的压力规则之前执行。

### 控制规则 {#control-rules}

对于 **[!UICONTROL Control]** 规则，您可以决定在交付生命周期的哪个点应用规则（在定位之前或之后，在个性化开始时，在分析结束时）。 在字段的下拉列表中，选择要应用的 **[!UICONTROL Phase]** 值，该字段位于 **[!UICONTROL General]** 排版规则的选项卡中。

![](assets/campaign_opt_define_control_phase.png)

可能的值包括：

* **[!UICONTROL At the start of targeting]**

   要防止出现错误时执行个性化步骤，您可以在此处应用控制规则。

* **[!UICONTROL After targeting]**

   如果您需要了解目标的音量以应用控制规则，请选择此阶段。

   例如，控制规 **[!UICONTROL Check proof size]** 则在每个定位阶段之后应用：如果证明收件人太多，此规则将阻止消息个性化。

* **[!UICONTROL At the start of personalization]**

   如果控件与消息个性化的批准有关，则必须选择此阶段。 消息个性化在分析阶段执行。

* **[!UICONTROL At the end of the analysis]**

   当检查要求消息个性化完成时，请选择此阶段。

## 其他配置 {#additional-configurations}

### 控制传出SMTP流量 {#control-outgoing-smtp-traffic}

作为选项，您可以使用该字 **[!UICONTROL Managing affinities with IP addresses]** 段将分发关联到分发服务器(MTA)此关联。 这样，您就可以限制向计算机或输出地址发送特定电子邮件的数量。

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>亲和力管理不适用于 **[!UICONTROL Filtering]** 类型。\
>相似性在Adobe Campaign服务器上的实例配置文件中定义。 如需详细信息，请参阅[此部分](../../installation/using/about-initial-configuration.md)。

### 营销活动优化和分布式营销 {#campaign-optimization-and-distributed-marketing}

通过 **[!UICONTROL Distributed Marketing]** 该选项卡，可定义在对共享营销活动进行排序和／或保留时应用的类型和／或规则的重新映射。 为本地实体定义的类型／规则（与为中央实体定义的类型链接）替换与中央实体链接的规则／类型。 通过重新映射，您可以根据对营销活动进行排序的本地实体调整中央实体规则。

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>在类型和类型规则中，如果您的许 **[!UICONTROL Distributed Marketing]** 可证包含以下选项，则会添加该选项卡：请检查您的许可协议。\
>有关“分布式营销”的详细信息，请参阅“关于 [分布式营销”](../../campaign/using/about-distributed-marketing.md)。

