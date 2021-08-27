---
product: campaign
title: 应用规则
description: 应用规则
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 09ec0fc0-76ed-4c73-8bdf-c931e2103aa9
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 9%

---

# 应用规则{#applying-rules}

![](../../assets/v7-only.svg)

## 对投放应用分类 {#applying-a-typology-to-a-delivery}

要应用您创建的分类规则，您需要将其与分类关联，然后在投放中引用此分类。 操作步骤：

1. 创建营销活动分类。

   可通过&#x200B;**[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**&#x200B;节点访问分类。

1. 转到&#x200B;**[!UICONTROL Rules]**&#x200B;选项卡，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并选择要与此分类一起应用的规则。

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 保存分类：是否会将其添加到现有分类列表。
1. 打开要将规则应用到的投放。
1. 打开投放属性并访问&#x200B;**[!UICONTROL Typology]**&#x200B;选项卡。
1. 在下拉列表中选择分类。

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >可以在投放模板中定义分类，以自动应用至使用此模板创建的所有投放。

## 定义应用程序条件 {#defining-application-conditions}

您可以根据需要限制规则的应用程序字段（控制规则除外）。

可以配置分类规则，以便它们仅与其链接的特定投放相关，或与投放目标中的特定收件人相关。

要定义规则的应用条件，请单击&#x200B;**[!UICONTROL General]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Edit the rule application conditions...]**&#x200B;链接。

然后，使用查询编辑器定义筛选条件。 在以下示例中，容量规则仅涉及标签中带有“offer”字样的投放，或2013年4月1日之前创建的投放。

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>对于筛选规则，您可以选择筛选条件的应用条件：它们可以依赖投放或投放大纲。 有关更多信息，请参阅[Conditioning a filtering rule](filtering-rules.md#conditioning-a-filtering-rule)。

## 调整计算频率 {#adjusting-calculation-frequency}

每天晚上，通过数据库清理工作流自动重新执行仲裁。 但是，值可以保存到此时段之后。

事实上，某些计算使用的值每天都不会更改。 因此，每天重新计算数据和使数据库无偿过载将无关紧要。 例如，如果某个流程通过每周客户倾向得分和购买信息来丰富营销数据库，则无需每天重新计算基于这些值的数据。

要实现此目的，可使用&#x200B;**[!UICONTROL General]**&#x200B;选项卡的&#x200B;**[!UICONTROL Frequency]**&#x200B;字段定义保存定位的最长时间段。 默认情况下，值&#x200B;**0**&#x200B;表示在下次执行每日重新仲裁之前，计算仍然有效。

要保存超出此时段的结果，请在&#x200B;**[!UICONTROL Frequency]**&#x200B;字段中输入大于12的值：此时间段过期后，将重新应用所有规则。

通过&#x200B;**[!UICONTROL Re-apply the rule at the start of personalization]**&#x200B;选项，您可以在个性化阶段自动应用规则，包括在&#x200B;**[!UICONTROL Frequency]**&#x200B;字段中所述的时段仍然有效时。

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
>如果您使用Campaign交互模块，则选件资格规则将与筛选规则（适用于在投放大纲中找到的选件）同时应用，或者在个性化阶段（在调用选件引擎期间）应用。

您可以使用规则&#x200B;**[!UICONTROL General]**&#x200B;选项卡中的相应字段来调整具有相同类型的规则的执行顺序。 在同一消息处理阶段执行多个规则时，您可以在&#x200B;**[!UICONTROL Execution sequence]**&#x200B;字段中配置其执行顺序。

例如，执行顺序为20的压力规则将在执行顺序为30的压力规则之前执行。

### 控制规则 {#control-rules}

对于&#x200B;**[!UICONTROL Control]**&#x200B;规则，您可以决定在投放生命周期的哪个时间点应用规则（在定位之前或之后、开始个性化时、分析结束时）。 在分类规则&#x200B;**[!UICONTROL General]**&#x200B;选项卡的&#x200B;**[!UICONTROL Phase]**&#x200B;字段的下拉列表中，选择要应用的值。

![](assets/campaign_opt_define_control_phase.png)

可能的值包括：

* **[!UICONTROL At the start of targeting]**

   要防止在发生错误时执行个性化步骤，您可以在此处应用控制规则。

* **[!UICONTROL After targeting]**

   如果您需要知道目标的音量以应用控制规则，请选择此阶段。

   例如， **[!UICONTROL Check proof size]**&#x200B;控制规则适用于每个定位阶段之后：如果校样收件人过多，此规则将阻止进行消息个性化。

* **[!UICONTROL At the start of personalization]**

   如果控件涉及邮件个性化的批准，则必须选择此阶段。 在分析阶段期间执行消息个性化。

* **[!UICONTROL At the end of the analysis]**

   当检查要求完成消息个性化时，请选择此阶段。

## 其他配置 {#additional-configurations}

### 控制传出SMTP流量 {#control-outgoing-smtp-traffic}

作为一个选项，您可以使用&#x200B;**[!UICONTROL Managing affinities with IP addresses]**&#x200B;字段将投放链接到此亲和度的投放服务器(MTA)。 这样，您就可以将特定投放的电子邮件数量限制到计算机或输出地址。

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>亲和度管理不适用于&#x200B;**[!UICONTROL Filtering]**&#x200B;分类。\
>相关性在Adobe Campaign服务器上的实例配置文件中定义。 如需详细信息，请参阅[此部分](../../installation/using/about-initial-configuration.md)。

### 营销活动优化和分布式营销 {#campaign-optimization-and-distributed-marketing}

通过&#x200B;**[!UICONTROL Distributed Marketing]**&#x200B;选项卡，可定义分类和/或规则的重新映射，在对共享营销活动进行排序和/或保留时，这些分类和/或规则会应用。 为本地实体定义的分类/规则（链接到为中央实体定义的分类）将替换链接到中央实体的规则/分类。 通过重新映射，您可以根据对营销活动进行排序的本地实体来调整中央实体规则。

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>在分类和分类规则中，如果您的许可证包含此选项，则会添加&#x200B;**[!UICONTROL Distributed Marketing]**&#x200B;选项卡：请查看许可协议。\
>有关分布式营销的更多信息，请参阅[关于分布式营销](../../distributed/using/about-distributed-marketing.md)。
