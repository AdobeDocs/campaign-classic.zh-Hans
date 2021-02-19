---
solution: Campaign Classic
product: campaign
title: 创建过滤器
description: 了解如何在执行查询时创建过滤器
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---


# 创建过滤器 {#creating-a-filter}

在Adobe Campaign中可用的过滤器是通过使用与查询相同的操作模式创建的过滤条件来定义的。

>[!NOTE]
>
>有关创建过滤器的详细信息，请参阅[本节](../../platform/using/filtering-options.md)。

**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;节点包含列表和概述中使用的所有过滤器。

例如，可以通过&#x200B;**[!UICONTROL Active accounts]**&#x200B;筛选运算符的列表:

![](assets/query_editor_filter_sample_1.png)

匹配筛选器包含&#x200B;**[!UICONTROL Operators]**&#x200B;查询&#x200B;**[!UICONTROL Account disabled]**&#x200B;值上的模式:

![](assets/query_editor_filter_sample_2.png)

对于同一列表,**[!UICONTROL By login or label]**&#x200B;过滤器允许您根据在过滤器字段中输入的值在列表上过滤数据：

![](assets/query_editor_filter_sample_3.png)

其构建方式如下：

![](assets/query_editor_filter_sample_4.png)

要匹配筛选条件，运算符帐户必须检查以下条件之一：

* 它的标签包含输入字段中输入的字符，
* 运算符名称包含在输入字段中输入的字符，
* 描述区域的内容包含在输入字段中输入的字符。

>[!NOTE]
>
>使用&#x200B;**[!UICONTROL Upper]**&#x200B;函数可以取消激活区分大小写的函数。

通过&#x200B;**[!UICONTROL Taken into account if]**&#x200B;列可定义这些筛选条件的应用程序条件。 此处，**$(/tmp/@text)**&#x200B;字符表示链接到筛选器的输入字段的内容：

![](assets/query_editor_filter_sample_5.png)

此处，**$(/tmp/@text)=&#39;agency&#39;**

**$(/tmp/@text)!=&quot;**&#x200B;当输入字段不为空时，表达式将应用每个条件。
