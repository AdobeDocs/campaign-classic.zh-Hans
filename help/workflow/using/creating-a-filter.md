---
title: 创建过滤器
description: 了解如何在执行查询时创建过滤器
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 创建过滤器 {#creating-a-filter}

Adobe Campaign中可用的过滤器是通过使用与查询相同的操作模式创建的过滤条件来定义的。

>[!NOTE]
>
>For more on creating filters, refer to [this section](../../platform/using/filtering-options.md).

该节 **[!UICONTROL Administration > Configuration > Predefined filters]** 点包含列表和概述中使用的所有过滤器。

例如，可以按以下方式筛选运算符列表 **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

匹配筛选器包含对架构 **[!UICONTROL Account disabled]** 值的查询 **[!UICONTROL Operators]** :

![](assets/query_editor_filter_sample_2.png)

对于同一列表，通过 **[!UICONTROL By login or label]** 筛选器，您可以根据在筛选器字段中输入的值筛选列表中的数据：

![](assets/query_editor_filter_sample_3.png)

其构建如下：

![](assets/query_editor_filter_sample_4.png)

要匹配筛选条件，操作符帐户必须检查以下条件之一：

* 其标签包含输入字段中输入的字符，
* 运算符名称包含输入字段中输入的字符，
* 描述区域的内容包含在输入字段中输入的字符。

>[!NOTE]
>
>该函 **[!UICONTROL Upper]** 数允许您取消激活区分大小写的函数。

该列 **[!UICONTROL Taken into account if]** 允许您为这些筛选条件定义应用程序条件。 此处， **$(/tmp/@text)** 字符表示链接到筛选器的输入字段的内容：

![](assets/query_editor_filter_sample_5.png)

这里， **$(/tmp/@text)=&#39;agency&#39;**

**$(/tmp/@text)!=&quot;** expression在输入字段不为空时应用每个条件。
