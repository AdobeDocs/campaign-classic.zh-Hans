---
product: campaign
title: 跟踪活动
description: 跟踪活动
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 2%

---

# 跟踪活动{#tracking-a-campaign}

![](../../assets/v7-only.svg)

中央实体运算符可以跟踪促销活动包列表中的促销活动订单。

这允许他们：

* [筛选包](#filter-packages),
* [编辑资源包](#edit-packages),
* [取消资源包](#cancel-a-package),
* [重新初始化包](#reinitializing-a-package).

## 筛选包 {#filter-packages}

从 **[!UICONTROL Campaigns]** 选项卡，则可以显示 **[!UICONTROL Campaign packages]** 可重组所有现有的分布式营销活动。 您可以过滤此列表，以便它仅显示已发布、延迟、待批准等的营销活动。 要实现此目的，请单击此视图上部分的链接，或使用 **[!UICONTROL Filter list]** 链接并选择要显示的营销活动包状态。

![](assets/mkg_dist_catalog_filter.png)

## 编辑资源包 {#edit-packages}

的 **[!UICONTROL Campaign packages]** 页面可查看每个包的摘要。

此摘要显示以下信息：标签、营销活动类型、创建该营销活动的营销活动名称以及文件夹。

单击包名称以对其进行编辑。 您还可以按其本地实体和状态查看订单。

此信息还可在 **[!UICONTROL Campaign orders]** 查看列出所有订单的。

![](assets/mkg_dist_catalog_op_command_details.png)

中心运算符可以编辑顺序。 可以通过两种方式来执行此操作：

1. 操作员可以单击顺序名称以对其进行编辑：这会显示订单详细信息。

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   的 **[!UICONTROL Edit > General]** 选项卡，用于查看本地实体在订购营销活动时输入的信息。

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 操作员可以单击营销活动包标签以对其进行编辑并更改某些设置。

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 取消资源包 {#cancel-a-package}

中央实体可以随时取消促销活动包。

单击 **[!UICONTROL Cancel]** 营销活动包中 **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

的 **[!UICONTROL Comment]** 字段中，您可以对取消进行说明。

对于 **本地营销活动**，取消某个资源包会将其从可用营销活动列表中删除。

对于 **协作营销**，取消资源包会触发多项操作：

1. 与此包相关的任何订单均被取消，

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 引用营销活动被取消，所有活动进程（工作流、投放）都停止，

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 向所有有关地方实体发送通知。

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

如果需要，中央实体仍可以访问和重新初始化已取消的包（请参阅下文）。 只有当地实体获得批准并启动后，才会再次向它们提供这些服务。 包重新初始化过程如下所示。

## 重新初始化包 {#reinitializing-a-package}

可以重新初始化、修改已发布的促销活动包，并将其提供给本地实体。

1. 选择相关的包。
1. 单击 **[!UICONTROL Reinitialize the package to reuse it]** 链接，单击 **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 单击 **[!UICONTROL Save]** 按钮以批准包重新初始化。

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 包状态将更改为 **[!UICONTROL Being edited]**. 再次修改、批准和发布该组件，以将其恢复到营销活动包的列表。

>[!NOTE]
>
>您还可以重新初始化已取消的营销活动包。
