---
solution: Campaign Classic
product: campaign
title: 跟踪活动
description: 跟踪活动
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---


# 跟踪活动{#tracking-a-campaign}

中央实体操作符可以跟踪活动包列表中的活动订单。

这使他们：

* [筛选包](#filter-packages),
* [编辑包](#edit-packages),
* [取消包](#cancel-a-package),
* [正在重新初始化包](#reinitializing-a-package)。

## 筛选程序包{#filter-packages}

在&#x200B;**[!UICONTROL Campaigns universe]**&#x200B;中，可显示&#x200B;**[!UICONTROL Campaign packages]**&#x200B;的列表，它重新分组所有现有分布式营销活动。 您可以过滤此列表，以便它仅显示已发布、延迟、待批准等的活动。 为此，请单击此视图上半部分的链接，或使用&#x200B;**[!UICONTROL Filter list]**&#x200B;链接并选择要显示的活动包状态。

![](assets/mkg_dist_catalog_filter.png)

## 编辑包{#edit-packages}

在&#x200B;**[!UICONTROL Campaign packages]**&#x200B;页面中，您可以视图每个包的摘要。

此摘要显示以下信息：标签、活动类型、创建活动的名称以及文件夹。

单击包名称以编辑它。 您还可以按本地实体和状态视图订单。

此信息还在&#x200B;**[!UICONTROL Campaign orders]**&#x200B;视图中提供，该列表所有订单。

![](assets/mkg_dist_catalog_op_command_details.png)

中心运算符可以编辑顺序。 有两种方法可以实现此目的：

1. 操作员可以单击订单名称进行编辑：这将显示订单详细信息。

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   使用&#x200B;**[!UICONTROL Edit > General]**&#x200B;选项卡，可以视图本地实体在订购活动时输入的信息。

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 操作员可以单击活动包标签来编辑它并更改某些设置。

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 取消包{#cancel-a-package}

中央实体可以随时取消活动包。

单击活动包&#x200B;**[!UICONTROL Dashboard]**&#x200B;中的&#x200B;**[!UICONTROL Cancel]**。

![](assets/mkg_dist_cancel_op_from_dashboard.png)

使用&#x200B;**[!UICONTROL Comment]**&#x200B;字段可以证明取消的合理性。

对于&#x200B;**本地活动**，取消包会将其从可用营销活动的列表中删除。

对于&#x200B;**协作活动**，取消包会触发许多操作：

1. 与此包相关的任何订单均被取消，

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 引用活动被取消，所有活动进程(工作流、投放)都被停止，

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 通知将发送给所有相关本地实体。

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

如果需要，中央实体仍可以访问和重新初始化已取消的包（请参见下文）。 只有在本地实体获得批准并开始后，才会再次向他们提供。 包重新初始化过程如下所示。

## 重新初始化包{#reinitializing-a-package}

已发布的活动包可以重新初始化、修改并可供本地实体使用。

1. 选择相关包。
1. 单击&#x200B;**[!UICONTROL Reinitialize the package to reuse it]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL OK]**。

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;按钮以批准程序包重新初始化。

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 包状态将更改为&#x200B;**[!UICONTROL Being edited]**。 重新修改、批准和发布它，将其恢复到活动包的列表。

>[!NOTE]
>
>您还可以重新初始化已取消的活动包。

