---
solution: Campaign Classic
product: campaign
title: 数据生命周期
description: 进一步了解工作流中的数据生命周期
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 5%

---


# 数据生命周期 {#data-life-cycle}

## 工作表{#work-table}

在工作流中，从一个活动传输到另一个数据被存储在临时工作表中。

可通过右键单击相应的过渡来显示和分析此数据。

![](assets/wf-right-click-analyze.png)

为此，请选择相关菜单：

* 显示目标

   此菜单显示有关目标群的可用数据以及工作表（**[!UICONTROL Schema]**&#x200B;选项卡）的结构。

   ![](assets/wf-right-click-display.png)

   有关详细信息，请参阅[工作表和工作流模式](../../workflow/using/monitoring-workflow-execution.md#worktables-and-workflow-schema)。

* 分析目标

   通过此菜单，您可以访问描述性分析向导，该向导可以生成有关过渡数据的统计信息和报告。

   有关更多信息，请参阅此](../../reporting/using/using-the-descriptive-analysis-wizard.md)章节[。

执行工作流时将清除目标数据。 只有最后一个工作表可供访问。 您可以配置工作流，以便所有工作表仍可访问：选中工作流属性中的&#x200B;**[!UICONTROL Keep the result of interim populations between two executions]**&#x200B;选项。

但是，我们建议您在出现大量数据时避免激活此选项。

![](assets/wf-purge-data-option.png)

## 目标数据{#target-data}

可以在个性化字段中访问存储在工作流工作表中的数据。

这样，您就可以使用通过列表收集或基于投放中调查答案的数据。 为此，请使用以下语法：

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData)类型个性化元素不适用于定位工作流。投放目标必须在工作流中构建并在投放的入站过渡中指定。

如果要创建投放验证，则需要基于&#x200B;**[!UICONTROL Address substitution]**&#x200B;模式构建验证目标，以便输入个性化数据。 有关更多信息，请参阅此](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof)章节[。

在以下示例中，我们将收集一列表有关客户的信息，并在个性化的电子邮件中使用。

应用以下步骤：

1. 创建一个工作流以收集信息，将其与数据库中已有的数据协调，然后开始投放。

   ![](assets/wf-targetdata-sample-1.png)

   在我们的示例中，文件内容如下所示：

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   要加载文件，请应用以下步骤：

   ![](assets/wf-targetdata-sample-2.png)

1. 配置&#x200B;**[!UICONTROL Enrichment]**&#x200B;类型活动以协调所收集的Adobe Campaign与已在数据库中的数据。

   此处，合并关键项是帐号：

   ![](assets/wf-targetdata-sample-3.png)

1. 然后配置&#x200B;**[!UICONTROL Delivery]**:它基于模板创建，收件人由入站过渡指定。

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >只能使用过渡中包含的数据来个性化投放。 **** targetDatatype个性化字段只适用于活动的入站 **[!UICONTROL Delivery]** 人口。

1. 在投放模板中，使用在工作流中收集的字段。

   为此，请插入&#x200B;**[!UICONTROL Target extension]**&#x200B;类型个性化字段。

   ![](assets/wf-targetdata-sample-5.png)

   在此，我们希望按工作流收集的文件中所述插入客户最喜爱的音乐流派和媒体类型（CD或DVD）。

   作为一个加号，我们将为忠诚卡持有者添加优惠券，即“卡”值等于1的收件人。

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** (targetData)类型的数据会使用与所有投放相同的特性插入到个性化字段中。它们也可用于主题、链接标签或链接本身。

   发送给收集的收件人的邮件将包含以下数据：

   ![](assets/wf-targetdata-sample-7.png)
