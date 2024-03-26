---
product: campaign
title: 跟踪活动
description: 了解如何使用Campaign分布式营销跟踪营销活动
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Distributed Marketing
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 3%

---

# 跟踪活动{#tracking-a-campaign}



中央实体运算符可以跟踪营销活动包列表中的营销活动订单。

这允许他们：

* [筛选包](#filter-packages)，
* [编辑包](#edit-packages)，
* [取消包](#cancel-a-package)，
* [重新初始化包](#reinitializing-a-package).

## 筛选包 {#filter-packages}

从 **[!UICONTROL Campaigns]** 选项卡上，您可以显示 **[!UICONTROL Campaign packages]** ，可重组所有现有的分布式营销活动。 您可以筛选此列表，使其仅显示已发布、延迟、未决批准等的营销活动。 要执行此操作，请单击此视图上部的链接，或使用 **[!UICONTROL Filter list]** 链接并选择要显示的营销活动包状态。

![](assets/mkg_dist_catalog_filter.png)

## 编辑包 {#edit-packages}

此 **[!UICONTROL Campaign packages]** 页面允许您查看每个包的摘要。

此摘要显示以下信息：标签、促销活动类型、创建促销活动的名称以及文件夹。

单击包名称可对其进行编辑。 您还可以按其本地实体和状态查看订单。

此信息还可参见 **[!UICONTROL Campaign orders]** 查看其中列出了所有订单的信息。

![](assets/mkg_dist_catalog_op_command_details.png)

中央操作员可以编辑顺序。 可通过两种方式来做到这一点：

1. 操作员可以单击订单名称对其进行编辑：这将显示订单详细信息。

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   此 **[!UICONTROL Edit > General]** 选项卡允许您查看本地实体在订购营销活动时输入的信息。

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 操作员可以单击营销活动包标签以编辑它并更改某些设置。

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 取消包 {#cancel-a-package}

中央实体可随时取消营销活动包。

单击 **[!UICONTROL Cancel]** 在营销活动包中 **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

此 **[!UICONTROL Comment]** 字段允许您论证取消的合理性。

对象 **本地营销活动**，取消资源包会将其从可用营销活动列表中删除。

对象 **协作活动**，取消资源包会触发许多操作：

1. 与此包相关的任何订单都将被取消，

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 引用营销活动已取消，所有活动进程（工作流、投放）已停止，

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 向所有有关的本地实体发送通知。

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

如有必要，中央实体仍可以访问和重新初始化已取消的包（请参阅下文）。 它们仅在获得批准并启动后，才会再次提供给本地实体。 软件包重新初始化过程如下所示。

## 重新初始化包 {#reinitializing-a-package}

已发布的营销活动包可以重新初始化、修改并提供给本地实体。

1. 选择相关的包。
1. 单击 **[!UICONTROL Reinitialize the package to reuse it]** 链接并单击 **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 单击 **[!UICONTROL Save]** 按钮批准包重新初始化。

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 程序包状态将更改为 **[!UICONTROL Being edited]**. 再次修改、批准并发布它，以将其恢复到Campaign包的列表。

>[!NOTE]
>
>您还可以重新初始化已取消的营销活动包。
