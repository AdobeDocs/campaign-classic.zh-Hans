---
product: campaign
title: 创建过滤器
description: 了解如何在执行查询时创建过滤器
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---

# 创建过滤器 {#creating-a-filter}

Adobe Campaign中可用的过滤器是通过过滤条件定义的，这些条件是使用与查询相同的操作模式创建的。

>[!NOTE]
>
>有关创建过滤器的更多信息，请参阅[此部分](../../platform/using/filtering-options.md)。

**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;节点包含列表和概述中使用的所有过滤器。

例如，运算符列表可按&#x200B;**[!UICONTROL Active accounts]**&#x200B;过滤：

![](assets/query_editor_filter_sample_1.png)

匹配筛选器包含对&#x200B;**[!UICONTROL Operators]**&#x200B;架构&#x200B;**[!UICONTROL Account disabled]**&#x200B;值的查询：

![](assets/query_editor_filter_sample_2.png)

对于同一列表，使用&#x200B;**[!UICONTROL By login or label]**&#x200B;筛选器可以根据在筛选器字段中输入的值筛选列表中的数据：

![](assets/query_editor_filter_sample_3.png)

其构建如下：

![](assets/query_editor_filter_sample_4.png)

要匹配筛选条件，运算符帐户必须检查以下条件之一：

* 其标签包含在输入字段中输入的字符，
* 运算符名称包含在输入字段中输入的字符，
* 描述区域的内容包含在输入字段中输入的字符。

>[!NOTE]
>
>**[!UICONTROL Upper]**&#x200B;函数允许您停用区分大小写的函数。

**[!UICONTROL Taken into account if]**&#x200B;列允许您为这些筛选条件定义应用程序条件。 在此， **$(/tmp/@text)**&#x200B;字符表示链接到过滤器的输入字段的内容：

![](assets/query_editor_filter_sample_5.png)

此处， **$(/tmp/@text)=&#39;agency&#39;**

**$(/tmp/@text)!=&quot;**&#x200B;表达式在输入字段不为空时应用每个条件。
