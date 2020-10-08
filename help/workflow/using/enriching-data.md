---
title: 丰富数据
seo-title: 丰富数据
description: 丰富数据
seo-description: null
page-status-flag: never-activated
uuid: 3f65a8a2-b3e1-4c4c-9653-b8a7c4d7557a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: f87da08f-68b9-4e2b-821f-b3ff20e390f1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 1%

---


# 扩充数据{#enriching-data}

## 关于丰富数据 {#about-enriching-data}

此用例详细信息可能用于定位 **[!UICONTROL Enrichment]** 工作流中的活动。 有关使用活动的详 **[!UICONTROL Enrichment]** 细信息，请参阅： [扩充](../../workflow/using/enrichment.md)。

本节还提供如何使用自定义日期丰富电子邮件投放的 [用例](../../workflow/using/email-enrichment-with-custom-date-fields.md)。

营销数据库中的联系人通过网络应用程序被发送参加比赛的邀请。 比赛结果在表格中复 **[!UICONTROL Competition results]** 原。 此表链接到联系表(**[!UICONTROL Recipients]**)。 该 **[!UICONTROL Competition results]** 表包含以下字段：

* 竞赛名称(@game)
* 试用号(@trial)
* 得分(@score)

![](assets/uc1_enrich_1.png)

表中的联系人 **[!UICONTROL Recipients]** 可以链接到表中的几 **[!UICONTROL Competition results]** 行。 这两个表之间的关系为1-n类型。 以下是收件人的结果日志示例：

![](assets/uc1_enrich_2.png)

此用例的用途是根据最高分将个性化投放发送给参加最新竞赛的人。 得分最高的收件人获得第一名，得分第二高的收件人获得安慰奖，其他所有人都得到一个信息，希望他们下次好运。

要设置此用例，我们创建了以下定位工作流：

![](assets/uc1_enrich_3.png)

要创建工作流，请应用以下步骤：

1. 在最 **[!UICONTROL Query]** 后一次竞 **[!UICONTROL Intersection]** 赛的目标新订户中增加两个活动和一个活动。
1. 该活动 **[!UICONTROL Enrichment]** 允许我们添加存储在表中的 **[!UICONTROL Competition results]** 数据。 我们 **[!UICONTROL Score]** 将进行投放个性化的字段将添加到工作流的工作表中。
1. 类 **[!UICONTROL Split]** 型活动允许我们根据得分创建收件人子集。
1. 对于每个子集， **[!UICONTROL Delivery]** 都添加类型活动。

## 第1步：定位 {#step-1--targeting}

第一个查询使我们能够目标过去六个月内添加到数据库的收件人。

![](assets/uc1_enrich_4.png)

第二个查询使我们能够目标参加上个比赛的收件人。

![](assets/uc1_enrich_5.png)

然 **[!UICONTROL Intersection]** 后，会添加一个类型活动，以目标在过去六个月内添加到数据库的收件人以及参加最后一场比赛的。

## 第2步：扩充 {#step-2--enrichment}

在此示例中，我们希望根据存储在表中 **[!UICONTROL Score]** 的字段个性化 **[!UICONTROL Competition results]** 投放。 此表与收件人表具有1-n类型关系。 该 **[!UICONTROL Enrichment]** 活动允许我们从链接到过滤维度的表添加数据到工作流的工作表。

1. 在扩充活动的编辑屏幕中，选择， **[!UICONTROL Add data]**&#x200B;然后 **[!UICONTROL Data linked to the filtering dimension]** 单击 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_6.png)

1. 然后选择 **[!UICONTROL Data linked to the filtering dimension]** 选项，选择表 **[!UICONTROL Competition results]** 并单击 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_7.png)

1. 输入ID和标签，然后在字 **[!UICONTROL Limit the line count]** 段中选择 **[!UICONTROL Data collected]** 选项。 在字 **[!UICONTROL Lines to retrieve]** 段中，选择“1”作为值。 对于每个收件人,扩充活动将从表中添 **[!UICONTROL Competition results]** 加一行到工作流的工作表。 单击 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. 在此示例中，我们希望恢复收件人的最高分，但仅恢复上一次比赛。 为此，请向字段添加一个筛选 **[!UICONTROL Competition name]** 器，以排除与先前比赛相关的所有行。 单击 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. 转到屏 **[!UICONTROL Sort]** 幕并单击按 **[!UICONTROL Add]** 钮，选择字段并选中列中的 **[!UICONTROL Score]** 框，以按降序 **[!UICONTROL descending]** 对字段的项 **[!UICONTROL Score]** 目进行排序。 对于每个收件人,扩充活动会添加一行，该行与上一个游戏的最高得分相匹配。 单击 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. 在窗 **[!UICONTROL Data to add]** 口中，多次单击 **[!UICONTROL Score]** 字段。 对于每个收件人,扩充活动将仅添加字 **[!UICONTROL Score]** 段。 单击 **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

右键单击扩充过渡的入站活动并选择 **[!UICONTROL Display the target]**。 工作表包含以下数据：

![](assets/uc1_enrich_13.png)

链接的模式是：

![](assets/uc1_enrich_15.png)

在扩充活动的出站过渡续订此操作。 我们可以看到链接到收件人分数的数据已经添加。 已恢复每个收件人的最高得分。

![](assets/uc1_enrich_12.png)

匹配模式也丰富了。

![](assets/uc1_enrich_14.png)

## 第3步：拆分和投放 {#step-3--split-and-delivery}

要根据收件人的得分对进行排序， **[!UICONTROL Split]** 将在扩充后添加一个活动。

![](assets/uc1_enrich_18.png)

1. 已定义第&#x200B;**一个**（入选方）子集，以包含得分最高的收件人。 为此，请定义记录数的限制，对得分应用降序排序，并将记录数限制为1。

   ![](assets/uc1_enrich_16.png)

1. 第二(第&#x200B;**二位**)子集包括具有第二最高得分的收件人。 配置与第一个子集的配置相同。

   ![](assets/uc1_enrich_17.png)

1. 第三个(输&#x200B;**出**)子集包含所有其他收件人。 转到选 **[!UICONTROL General]** 项卡并选中该 **[!UICONTROL Generate complement]** 复选框，以目标未达到两个最高分的所有收件人。

   ![](assets/uc1_enrich_19.png)

1. 为每个 **[!UICONTROL Delivery]** 子集添加一个类型活动，为每个子集使用不同的投放模板。

   ![](assets/uc1_enrich_20.png)

