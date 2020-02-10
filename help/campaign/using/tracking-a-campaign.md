---
title: 跟踪营销活动
seo-title: 跟踪营销活动
description: 跟踪营销活动
seo-description: null
page-status-flag: never-activated
uuid: 66919c81-b22c-4138-a654-ea53154ba718
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: e1f8958d-f036-4635-be6e-ebdbea6ac116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 跟踪营销活动{#tracking-a-campaign}

中央实体运营商可以在营销活动包列表中跟踪营销活动订单。

这使他们：

* [过滤包](#filter-packages),
* [编辑包](#edit-packages),
* [取消包](#cancel-a-package),
* [重新初始化包](#reinitializing-a-package)。

## 过滤包 {#filter-packages}

在中， **[!UICONTROL Campaigns universe]**&#x200B;您可以显示重新分组所有现有 **[!UICONTROL Campaign packages]** 分布式营销活动的列表。 您可以过滤此列表，以便它仅显示已发布、延迟、待批准等营销活动。 为此，请单击此视图上半部分的链接，或使用链接并 **[!UICONTROL Filter list]** 选择要显示的营销活动包状态。

![](assets/mkg_dist_catalog_filter.png)

## 编辑包 {#edit-packages}

在该 **[!UICONTROL Campaign packages]** 页面中，您可以查看每个包的摘要。

此摘要显示以下信息：标签、系列活动的类型、从中创建该系列活动的系列活动的名称以及文件夹。

单击包名称以编辑它。 您还可以按其本地实体和状态查看订单。

此信息也会在列出所有订 **[!UICONTROL Campaign orders]** 单的视图中提供。

![](assets/mkg_dist_catalog_op_command_details.png)

中央运算符可以编辑顺序。 有两种方法可以实现此目的：

1. 操作员可以单击订单名称进行编辑：这会显示订单详细信息。

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   通过 **[!UICONTROL Edit > General]** 该选项卡，可以查看本地实体在对营销活动进行排序时输入的信息。

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 操作员可以单击营销活动包标签来编辑它并更改某些设置。

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 取消包 {#cancel-a-package}

中央实体可以随时取消营销活动包。

单击 **[!UICONTROL Cancel]** 营销活动包中的 **[!UICONTROL Dashboard]**。

![](assets/mkg_dist_cancel_op_from_dashboard.png)

该字 **[!UICONTROL Comment]** 段可让您对取消进行说明。

对于 **本地营销活动**，取消包会将其从可用营销活动列表中删除。

对于协 **作营销活动**，取消包会触发许多操作：

1. 与此包相关的所有订单均被取消，

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 引用营销活动已取消，所有活动流程（工作流、交付）都将停止，

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 通知将发送给所有相关的当地实体。

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

如果需要，中央实体仍可以访问和重新初始化已取消的包（请参阅下文）。 只有当地实体获得批准并开始后，才会再次向它们提供。 包重新初始化过程如下所示。

## 重新初始化包 {#reinitializing-a-package}

已发布的系列活动包可以重新初始化、修改并可供本地实体使用。

1. 选择相关包。
1. 单击链 **[!UICONTROL Reinitialize the package to reuse it]** 接，然后单击 **[!UICONTROL OK]**。

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 单击该 **[!UICONTROL Save]** 按钮可批准重新初始化包。

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 包状态将更改为 **[!UICONTROL Being edited]**。 再次修改、批准和发布它以将其恢复到营销活动包列表。

>[!NOTE]
>
>您还可以重新初始化已取消的营销活动包。

