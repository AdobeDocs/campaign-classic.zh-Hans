---
title: 跟踪活动
seo-title: 跟踪活动
description: 跟踪活动
seo-description: null
page-status-flag: never-activated
uuid: 66919c81-b22c-4138-a654-ea53154ba718
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: e1f8958d-f036-4635-be6e-ebdbea6ac116
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 2%

---


# 跟踪活动{#tracking-a-campaign}

中央实体操作符可以跟踪活动包列表中的活动订单。

这使他们：

* [筛选包](#filter-packages),
* [编辑包](#edit-packages),
* [取消包](#cancel-a-package),
* [正在重新初始化包](#reinitializing-a-package)。

## 筛选包 {#filter-packages}

在中， **[!UICONTROL Campaigns universe]**&#x200B;您可以显示列表，该 **[!UICONTROL Campaign packages]** 重新分组所有现有分布式营销活动。 您可以过滤此列表，以便它仅显示已发布、延迟、待批准等的活动。 为此，请单击此视图上半部分的链接，或使用链接 **[!UICONTROL Filter list]** 并选择要显示的活动包状态。

![](assets/mkg_dist_catalog_filter.png)

## 编辑包 {#edit-packages}

通过 **[!UICONTROL Campaign packages]** 该页面，您可以视图每个包的摘要。

此摘要显示以下信息：标签、活动类型、创建活动的名称以及文件夹。

单击包名称以编辑它。 您还可以按本地实体和状态视图订单。

此信息也会在视图所 **[!UICONTROL Campaign orders]** 有订单的列表中提供。

![](assets/mkg_dist_catalog_op_command_details.png)

中心运算符可以编辑顺序。 有两种方法可以实现此目的：

1. 操作员可以单击订单名称进行编辑：这将显示订单详细信息。

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   通过 **[!UICONTROL Edit > General]** 选项卡，您可以在本地实体对活动进行排序时输入视图信息。

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 操作员可以单击活动包标签来编辑它并更改某些设置。

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 取消包 {#cancel-a-package}

中央实体可以随时取消活动包。

单击 **[!UICONTROL Cancel]** 活动包 **[!UICONTROL Dashboard]**&#x200B;中。

![](assets/mkg_dist_cancel_op_from_dashboard.png)

该字 **[!UICONTROL Comment]** 段允许您对取消进行说明。

对于 **本地活动**，取消包会将其从可用营销活动的列表中删除。

对于 **协作活动**，取消包会触发大量操作：

1. 与此包相关的任何订单均被取消，

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 引用活动被取消，所有活动进程(工作流、投放)都被停止，

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 通知将发送给所有相关本地实体。

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

如果需要，中央实体仍可以访问和重新初始化已取消的包（请参见下文）。 只有在本地实体获得批准并开始后，才会再次向他们提供。 包重新初始化过程如下所示。

## 重新初始化包 {#reinitializing-a-package}

已发布的活动包可以重新初始化、修改并可供本地实体使用。

1. 选择相关包。
1. 单击链 **[!UICONTROL Reinitialize the package to reuse it]** 接，然后单 **[!UICONTROL OK]**&#x200B;击。

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 单击按 **[!UICONTROL Save]** 钮以批准包重新初始化。

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 包状态将更改为 **[!UICONTROL Being edited]**。 重新修改、批准和发布它，将其恢复到活动包的列表。

>[!NOTE]
>
>您还可以重新初始化已取消的活动包。

