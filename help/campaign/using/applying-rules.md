---
solution: Campaign Classic
product: campaign
title: 应用规则
description: 应用规则
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 9%

---


# 应用规则{#applying-rules}

## 对投放{#applying-a-typology-to-a-delivery}应用类型学

要应用您创建的类型规则，您需要将其与类型学关联，然后在投放中引用此类型学。 操作步骤：

1. 创建活动类型。

   通过&#x200B;**[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**&#x200B;节点访问类型。

1. 转至&#x200B;**[!UICONTROL Rules]**&#x200B;选项卡，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并选择要应用于此类型学的规则。

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 保存类型学：是否将其添加到现有字体的列表。
1. 打开要应用规则的投放。
1. 打开投放属性并访问&#x200B;**[!UICONTROL Typology]**&#x200B;选项卡。
1. 在下拉列表中选择类型。

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >可以在投放模板中定义分类，以自动应用至使用此模板创建的所有投放。

## 定义应用程序条件{#defining-application-conditions}

您可以根据需要限制规则的应用程序字段（控制规则除外）。

可以配置类型规则，使其只关注与其链接的特定投放，或投放目标中的特定收件人。

要定义规则的应用条件，请单击&#x200B;**[!UICONTROL General]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Edit the rule application conditions...]**&#x200B;链接。

然后使用查询编辑器定义筛选条件。 在以下示例中，容量规则仅涉及标签中带有“优惠”字样的投放或2013年4月1日之前创建的投放。

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>对于筛选规则，您可以选择筛选条件的应用条件：他们可以依赖投放或投放概要。 有关详细信息，请参阅[调整过滤规则](../../campaign/using/filtering-rules.md#conditioning-a-filtering-rule)。

## 调整计算频率{#adjusting-calculation-frequency}

仲裁通过数据库清理工作流程在每天晚上自动执行。 但是，值可以保存到此期间之后。

事实上，一些计算使用的值不会每天发生变化。 因此，每天重新计算数据并免费使数据库过载将无关紧要。 例如，如果某个流程以每周的客户倾向得分和购买信息丰富了营销数据库，则无需每天重新计算基于这些值的数据。

为此，**[!UICONTROL General]**&#x200B;选项卡的&#x200B;**[!UICONTROL Frequency]**&#x200B;字段允许您定义保存定位的最长时间段。 默认情况下，值&#x200B;**0**&#x200B;表示计算在下次执行每日重新仲裁之前仍然有效。

要保存超过此期间的结果，请在&#x200B;**[!UICONTROL Frequency]**&#x200B;字段中输入大于12的值：此期间到期后，将重新应用所有规则。

使用&#x200B;**[!UICONTROL Re-apply the rule at the start of personalization]**&#x200B;选项，您可以在个性化阶段自动应用规则，包括在&#x200B;**[!UICONTROL Frequency]**&#x200B;字段中所述的期间仍然有效时。

## 选择规则应用程序阶段{#selecting-the-rule-application-phase}

类型规则在其所关注的投放的定位、分析和个性化阶段按特定顺序应用。

### 执行顺序{#execution-order}

在标准操作模式下，按以下顺序应用规则：

1. 控制规则（如果在开始定向时应用）。
1. 筛选规则：

   * 地址资格的本机应用规则：已定义的地址／未验证的地址/阻止列表地址／隔离地址／地址质量。
   * 筛选用户定义的规则。
   * 外部重复数据删除地址或标识符规则（如有必要，应用）。

1. 压力规则.
1. 容量规则。
1. 控制规则（如果在定向结束时应用）。
1. 控制规则（如果在开始个性化时应用）。如果用户规则（过滤／压力／电容性）已过期，需要重新计算，则将在此步骤中应用这些规则。
1. 控制规则（如果在个性化结束时适用）。

>[!NOTE]
>
>如果您使用活动交互模块，则在调用优惠引擎的过程中，优惠合格规则会与过滤规则(针对在投放概要中找到的优惠)同时应用，或者在个性化阶段应用。

您可以使用规则&#x200B;**[!UICONTROL General]**&#x200B;选项卡中的相应字段调整具有相同类型的规则的执行顺序。 当在同一消息处理阶段执行多个规则时，您可以在&#x200B;**[!UICONTROL Execution sequence]**&#x200B;字段中配置其执行顺序。

例如，执行顺序为20的压力规则将在执行顺序为30的压力规则之前执行。

### 控制规则 {#control-rules}

对于&#x200B;**[!UICONTROL Control]**&#x200B;规则，您可以决定在投放生命周期的哪个点应用规则(在定位之前或之后，在个性化开始，在分析结束时)。 在&#x200B;**[!UICONTROL Phase]**&#x200B;字段的下拉列表中，选择要应用的值，该类型规则的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中。

![](assets/campaign_opt_define_control_phase.png)

可能的值有：

* **[!UICONTROL At the start of targeting]**

   要防止在出现错误时执行个性化步骤，您可以在此处应用控制规则。

* **[!UICONTROL After targeting]**

   如果您需要了解目标的音量以应用控制规则，请选择此阶段。

   例如，**[!UICONTROL Check proof size]**&#x200B;控制规则在每个定位阶段之后应用：如果验证收件人过多，此规则将阻止消息个性化。

* **[!UICONTROL At the start of personalization]**

   如果控件与消息个性化的批准有关，则必须选择此阶段。 消息个性化在分析阶段执行。

* **[!UICONTROL At the end of the analysis]**

   当检查需要完成消息个性化时，请选择此阶段。

## 其他配置 {#additional-configurations}

### 控制传出的SMTP通信{#control-outgoing-smtp-traffic}

作为选项，您可以使用&#x200B;**[!UICONTROL Managing affinities with IP addresses]**&#x200B;字段将投放链接到投放服务器(MTA)此关联。 这样，您就可以将特定投放的电子邮件数量限制到计算机或输出地址。

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>关联管理不适用于&#x200B;**[!UICONTROL Filtering]**&#x200B;类型。\
>关联在实例配置文件中的Adobe Campaign服务器上定义。 如需详细信息，请参阅[此部分](../../installation/using/about-initial-configuration.md)。

### 活动优化和分布式营销{#campaign-optimization-and-distributed-marketing}

使用&#x200B;**[!UICONTROL Distributed Marketing]**&#x200B;选项卡可定义在对共享活动进行排序和／或保留时应用的类型和／或规则的重新映射。 为本地实体定义的类型／规则(与为中央实体定义的类型链接)替换与中央实体链接的规则／类型。 通过重新映射，您可以根据中央实体的订购本地实体调整活动规则。

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>在类型和类型规则中，如果许可证包含以下选项，则会添加&#x200B;**[!UICONTROL Distributed Marketing]**&#x200B;选项卡：请检查您的许可协议。\
>有关分布式营销的详细信息，请参阅[关于分布式营销](../../campaign/using/about-distributed-marketing.md)。

