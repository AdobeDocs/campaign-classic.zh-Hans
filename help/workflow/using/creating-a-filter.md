---
product: campaign
title: 创建筛选
description: 了解如何在执行查询时创建过滤器
feature: Query Editor, Workflows
hide: true
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
TQID: https://experienceleague.adobe.com/zbo80k37hd1N8jpdy-kQqLAl06B6sbsjKfQ-iyC8-1A
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 211
ht-degree: 2%

---

# 创建筛选 {#creating-a-filter}



Adobe Campaign中可用的过滤器是通过使用与查询相同的操作模式创建的过滤条件来定义的。

>[!NOTE]
>
>有关创建筛选器的更多信息，请参阅[此章节](../../platform/using/filtering-options.md)。

**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;节点包含列表和概述中使用的所有筛选器。

例如，运算符列表可按&#x200B;**[!UICONTROL Active accounts]**&#x200B;筛选：

![](assets/query_editor_filter_sample_1.png)

匹配筛选器包含对&#x200B;**[!UICONTROL Operators]**&#x200B;架构的&#x200B;**[!UICONTROL Account disabled]**&#x200B;值的查询：

![](assets/query_editor_filter_sample_2.png)

对于同一列表，**[!UICONTROL By login or label]**&#x200B;筛选器允许您根据在筛选器字段中输入的值筛选列表上的数据：

![](assets/query_editor_filter_sample_3.png)

其构建方式如下：

![](assets/query_editor_filter_sample_4.png)

要匹配筛选条件，操作员帐户必须检查以下条件之一：

* 其标签包含输入字段中输入的字符，
* 操作员名称包含输入字段中输入的字符，
* 描述区域的内容包含在输入字段中输入的字符。

>[!NOTE]
>
>**[!UICONTROL Upper]**&#x200B;函数允许您停用区分大小写的函数。

**[!UICONTROL Taken into account if]**&#x200B;列允许您为这些筛选条件定义应用条件。 此处，**$(/tmp/@text)**&#x200B;字符表示链接到筛选器的输入字段的内容：

![](assets/query_editor_filter_sample_5.png)

此处，**$(/tmp/@text)=&#39;代理&#39;**

当输入字段不为空时，**$(/tmp/@text)!=“**”表达式应用每个条件。
