---
product: campaign
title: 丰富数据
description: 进一步了解扩充工作流活动
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: ab786cf1-74a4-4185-a63d-84e776a2f776
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# 丰富数据{#enriching-data}

![](../../assets/common.svg)

## 关于扩充数据 {#about-enriching-data}

此用例详细说明了&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动在定位工作流中可能的用途。 有关使用&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动的更多信息，请参阅：[扩充](enrichment.md)。

[此部分](email-enrichment-with-custom-date-fields.md)中还提供了有关如何使用自定义日期扩充电子邮件投放的用例。

通过Web应用程序向营销数据库中的联系人发送参加比赛的邀请。 竞争结果在&#x200B;**[!UICONTROL Competition results]**&#x200B;表中恢复。 此表链接到联系人表(**[!UICONTROL Recipients]**)。 **[!UICONTROL Competition results]**&#x200B;表包含以下字段：

* 竞争名称(@game)
* 试用号(@trial)
* 得分(@score)

![](assets/uc1_enrich_1.png)

在&#x200B;**[!UICONTROL Recipients]**&#x200B;表中找到的联系人可以链接到&#x200B;**[!UICONTROL Competition results]**&#x200B;表中的几行。 这两个表之间的关系为1-n类型。 以下是收件人的结果日志示例：

![](assets/uc1_enrich_2.png)

此用例的用途是：根据参与最新竞争的人员的最高得分，向他们发送个性化投放。 得分最高的受奖人获得第一名，得分第二名的受奖人获得安慰奖，其他所有人都得到一个信息，希望下次能更好运。

要设置此用例，我们创建了以下定位工作流：

![](assets/uc1_enrich_3.png)

要创建工作流，请应用以下步骤：

1. 将添加两个&#x200B;**[!UICONTROL Query]**&#x200B;活动和一个&#x200B;**[!UICONTROL Intersection]**&#x200B;活动，以定向最后进入竞争的新订阅者。
1. 通过&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动，我们可以添加存储在&#x200B;**[!UICONTROL Competition results]**&#x200B;表中的数据。 将进行投放个性化的&#x200B;**[!UICONTROL Score]**&#x200B;字段添加到工作流的工作表中。
1. 通过&#x200B;**[!UICONTROL Split]**&#x200B;类型活动，我们可以根据得分创建收件人子集。
1. 对于每个子集，将添加&#x200B;**[!UICONTROL Delivery]**&#x200B;类型活动。

## 步骤1:定位 {#step-1--targeting}

通过第一个查询，我们可以定位过去六个月内添加到数据库的收件人。

![](assets/uc1_enrich_4.png)

第二个查询使我们能够定位参加上次比赛的收件人。

![](assets/uc1_enrich_5.png)

然后，会添加&#x200B;**[!UICONTROL Intersection]**&#x200B;类型活动，以定位在过去六个月内添加到数据库的收件人以及参加上次竞争的收件人。

## 步骤2:扩充 {#step-2--enrichment}

在此示例中，我们希望根据存储在&#x200B;**[!UICONTROL Competition results]**&#x200B;表中的&#x200B;**[!UICONTROL Score]**&#x200B;字段对投放进行个性化。 此表与收件人表具有1-n类型关系。 通过&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动，我们可以将链接到过滤维度的表中的数据添加到工作流的工作表。

1. 在扩充活动的编辑屏幕中，选择&#x200B;**[!UICONTROL Add data]**，然后选择&#x200B;**[!UICONTROL Data linked to the filtering dimension]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_6.png)

1. 然后选择&#x200B;**[!UICONTROL Data linked to the filtering dimension]**&#x200B;选项，选择&#x200B;**[!UICONTROL Competition results]**&#x200B;表并单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_7.png)

1. 输入ID和标签，然后在&#x200B;**[!UICONTROL Data collected]**&#x200B;字段中选择&#x200B;**[!UICONTROL Limit the line count]**&#x200B;选项。 在&#x200B;**[!UICONTROL Lines to retrieve]**&#x200B;字段中，选择“1”作为值。 对于每个收件人，扩充活动将从&#x200B;**[!UICONTROL Competition results]**&#x200B;表添加一行到工作流的工作表。 单击 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_8.png)

1. 在此示例中，我们希望恢复收件人的最高分数，但仅用于上一次竞争。 为此，请在&#x200B;**[!UICONTROL Competition name]**&#x200B;字段中添加一个过滤器，以排除与先前比赛相关的所有行。 单击 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_9.png)

1. 转到&#x200B;**[!UICONTROL Sort]**&#x200B;屏幕并单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮，选择&#x200B;**[!UICONTROL Score]**&#x200B;字段，然后选中&#x200B;**[!UICONTROL descending]**&#x200B;列中的框，以降序方式对&#x200B;**[!UICONTROL Score]**&#x200B;字段的项目进行排序。 对于每个收件人，扩充活动会添加一条与上一个游戏的最高得分匹配的线。 单击 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_10.png)

1. 在&#x200B;**[!UICONTROL Data to add]**&#x200B;窗口中，双击&#x200B;**[!UICONTROL Score]**&#x200B;字段。 对于每个收件人，扩充活动将仅添加&#x200B;**[!UICONTROL Score]**&#x200B;字段。 单击 **[!UICONTROL Finish]**。

   ![](assets/uc1_enrich_11.png)

右键单击扩充活动的集客过渡，然后选择&#x200B;**[!UICONTROL Display the target]**。 工作表包含以下数据：

![](assets/uc1_enrich_13.png)

链接的架构为：

![](assets/uc1_enrich_15.png)

在扩充活动的叫客过渡上续订此操作。 我们可以看到已添加与收件人得分关联的数据。 已恢复每个收件人的最高分数。

![](assets/uc1_enrich_12.png)

匹配模式也已进行扩充。

![](assets/uc1_enrich_14.png)

## 步骤3:拆分和交付 {#step-3--split-and-delivery}

要根据收件人的得分对收件人进行排序，将在扩充后添加&#x200B;**[!UICONTROL Split]**&#x200B;活动。

![](assets/uc1_enrich_18.png)

1. 已定义第一个（**入选者**）子集，以包含得分最高的收件人。 为此，请定义记录数的限制，对分数应用降序排序，并将记录数限制为1。

   ![](assets/uc1_enrich_16.png)

1. 第二（**第二位置**）子集包括具有第二最高分数的收件人。 配置与第一个子集的配置相同。

   ![](assets/uc1_enrich_17.png)

1. 第三个（**失败者**）子集包含所有其他收件人。 转到&#x200B;**[!UICONTROL General]**&#x200B;选项卡并选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;框，以定向未达到最高分的所有收件人。

   ![](assets/uc1_enrich_19.png)

1. 为每个子集添加&#x200B;**[!UICONTROL Delivery]**&#x200B;类型活动，为每个子集使用不同的投放模板。

   ![](assets/uc1_enrich_20.png)
