---
solution: Campaign Classic
product: campaign
title: 跟踪活动
description: 跟踪活动
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 2%

---


# 跟踪活动{#tracking-a-campaign}

中央实体运算符可以在活动包的列表中跟踪活动订单。

这让他们：

* [过滤包](#filter-packages),
* [编辑包](#edit-packages),
* [取消包](#cancel-a-package),
* [正在重新初始化包](#reinitializing-a-package)。

## 筛选器包{#filter-packages}

在&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡中，可显示&#x200B;**[!UICONTROL Campaign packages]**&#x200B;的列表，该活动会重新分组所有现有的分布式营销。 您可以过滤此列表，以便它仅显示已发布、延迟、待批准等活动。 要执行此操作，请单击此视图上半部分的链接，或使用&#x200B;**[!UICONTROL Filter list]**&#x200B;链接并选择要显示的活动包状态。

![](assets/mkg_dist_catalog_filter.png)

## 编辑包{#edit-packages}

在&#x200B;**[!UICONTROL Campaign packages]**&#x200B;页中，您可以视图每个包的摘要。

此摘要显示以下信息：标签、活动类型、创建活动的名称以及文件夹。

单击包名称以对其进行编辑。 您还可以按订单的本地实体和状态视图订单。

此信息也会在&#x200B;**[!UICONTROL Campaign orders]**&#x200B;视图中提供，该列表会所有订单。

![](assets/mkg_dist_catalog_op_command_details.png)

中心运算符可以编辑顺序。 有两种方法可以实现：

1. 操作员可以单击订单名称进行编辑：这将显示订单详细信息。

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   使用&#x200B;**[!UICONTROL Edit > General]**&#x200B;选项卡，可以视图本地实体在订购活动时输入的信息。

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 操作员可以单击活动包标签来编辑它并更改某些设置。

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 取消{#cancel-a-package}包

中央实体可以随时取消活动包。

单击活动包&#x200B;**[!UICONTROL Dashboard]**&#x200B;中的&#x200B;**[!UICONTROL Cancel]**。

![](assets/mkg_dist_cancel_op_from_dashboard.png)

**[!UICONTROL Comment]**&#x200B;字段允许您对取消进行说明。

对于&#x200B;**本地活动**，取消包会从可用营销活动的列表中删除它。

对于&#x200B;**协作活动**，取消包会触发许多操作：

1. 与此包相关的任何订单均被取消，

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 将取消引用活动，并停止所有活动进程(工作流、投放),

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 通知将发送给所有相关本地实体。

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

如果需要，中央实体仍可以访问和重新初始化已取消的包（见下文）。 只有在本地实体获得批准并开始后，才会再次向他们提供。 程序包重新初始化过程如下所示。

## 正在重新初始化包{#reinitializing-a-package}

已发布的活动包可以重新初始化、修改并可供本地实体使用。

1. 选择相关包。
1. 单击&#x200B;**[!UICONTROL Reinitialize the package to reuse it]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL OK]**。

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;按钮批准程序包重新初始化。

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 包状态将更改为&#x200B;**[!UICONTROL Being edited]**。 重新修改、批准和发布它以将其恢复到活动包的列表。

>[!NOTE]
>
>您还可以重新初始化已取消的活动包。

