---
product: campaign
title: 个性化优惠券
description: 了解如何创建和插入个性化优惠券
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 1%

---

# 个性化优惠券{#personalized-coupons}



向投放添加优惠券可增强收件人对产品和服务的价值。 您可以使用Campaign优惠券模块创建一组优惠券，并预计将其添加到即将推出的营销活动中。 准备创建投放时，请分配适用的优惠券。 由于优惠券在特定时段内有效，因此分配的优惠券将唯一链接到其投放消息。 此外，Campaign会确认在发送投放之前有足够的消息数优惠券。

>[!NOTE]
>
>优惠券管理是必须安装的包。 要确认您有优惠券管理，请选中 **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>优惠券数据可以使用CSV和XML格式导入和导出。 有关导入和导出的详细信息，请参阅 [本节](../../platform/using/get-started-data-import-export.md).

## 创建优惠券 {#creating-a-coupon}

创建优惠券时，优惠券模块为您提供了两个选项：

* **匿名**：用于选择收件人或收件人列表的通用优惠券。
* **个人**：为选定的收件人提供的个性化优惠券。

在执行以下步骤之前，请确保您知道要创建的优惠券类型。

1. 在Campaign树中，转到 **[!UICONTROL Resources > Campaign management > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. 单击 **[!UICONTROL New]** 按钮。
1. 在中输入优惠券的名称 **[!UICONTROL Label]** 字段。 已自动输入唯一代码 **[!UICONTROL Coupon code]**. 您可以保留代码或输入新代码。

   ![](assets/deliv_coup_02.png)

1. 选择 **[!UICONTROL Start date]** 和 **[!UICONTROL End date]** 以设置优惠券的有效期限。
1. In **[!UICONTROL Coupon type]**，选择“匿名”或“个人”。

   **[!UICONTROL Anonymous coupons]** ：所有收件人的匿名优惠券都相同。 确认在 **优惠券类型** 菜单并单击 **保存** 以生成优惠券。

   **[!UICONTROL Individual coupons]** ：可以使用其他优惠券代码进一步个性化单个优惠券。 例如，为体育器材商店的销售创建单个优惠券。 然而，获奖者名单很长，他们对于一项体育运动的热情并不相同。 您可以根据运动（例如足球、足球、棒球等）为各个优惠券添加代码名称 并将每个代码发送给适用的收件人。

   1. 选择“单个”时，左下方会显示一个新选项卡“优惠券”。 转到 **[!UICONTROL Coupons]** 选项卡，然后单击 **[!UICONTROL Add]**.
   1. 在弹出窗口提示时，为各个优惠券输入唯一代码。
   1. 单击 **[!UICONTROL Save]** 以生成优惠券。

   有关“优惠券”选项卡的更多详细信息，请参阅 [配置单个优惠券](#configuring-individual-coupons).

   >[!NOTE]
   >
   >可以批量导入各个优惠券。 有关导入和导出的详细信息，请参阅 [本节](../../platform/using/get-started-data-import-export.md).

### 配置单个优惠券 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

“优惠券”选项卡仅适用于单个优惠券。 将优惠券与投放关联后，“优惠券”选项卡会提供以下详细信息：

* **[!UICONTROL Status]** ：优惠券的可用性。
* **[!UICONTROL Redeemed on]** ：兑换优惠券的日期。
* **[!UICONTROL Channel]** ：用于发送优惠券的渠道。
* **[!UICONTROL Address]** ：收件人的电子邮件地址。

值 **[!UICONTROL status]**， **[!UICONTROL channel]**、和 **[!UICONTROL address]** 将自动完成。 但是，值 **[!UICONTROL redeemed on]** 不会由Campaign恢复。 可以通过导入包含优惠券兑换详细信息的文件来完成这些操作。

## 在电子邮件投放中插入优惠券 {#inserting-a-coupon-into-an-email-delivery}

在以下示例中，投放是从主页创建的。 有关如何创建投放的详细说明，请参阅 [本节](about-email-channel.md). 您还可以在工作流中为投放添加优惠券。

1. 转到 **[!UICONTROL Campaigns]** 并选择 **[!UICONTROL Deliveries]**.
1. 单击 **[!UICONTROL Create]**。

   ![](assets/deliv_coup_04.png)

1. 在中输入名称 **[!UICONTROL Label]** 并单击 **[!UICONTROL Continue]**.
1. 单击 **[!UICONTROL To]** 以添加收件人。
1. 单击 **[!UICONTROL Add]** 选择投放的收件人。 选择收件人后，单击 **[!UICONTROL Ok]** 以返回投放。

   ![](assets/deliv_coup_05.png)

1. 输入主题并向消息中添加内容。

   ![](assets/deliv_coup_06.png)

1. 在工具栏中，单击 **[!UICONTROL Properties]** 并选择 **[!UICONTROL Advanced]** 选项卡。
1. 单击文件夹图标 **[!UICONTROL Coupon management]**.

   ![](assets/deliv_coup_07.png)

1. 选择优惠券并单击 **[!UICONTROL Ok]**. 单击 **[!UICONTROL Ok]** 再来一次。

   ![](assets/deliv_coup_08.png)

1. 单击消息以选择要放置优惠券的位置。

   ![](assets/deliv_coup_09.png)

1. 单击个性化图标，根据优惠券类型选择以下选项之一：

   * 匿名优惠券： **[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * 个人优惠券： **[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      优惠券作为代码插入消息中，而不是作为您指定的名称插入。 该代码在Campaign ootb数据模型中使用。
   ![](assets/deliv_coup_12.png)

1. 运行测试以确认您分配给优惠券的名称。 转到 **[!UICONTROL Preview]** 选项卡，然后单击 **[!UICONTROL Test personalization]**. 选择测试的收件人。

   ![](assets/deliv_coup_13.png)

   测试后，优惠券应显示为分配的名称，而不是代码。

   ![](assets/deliv_coup_14.png)

1. 在工具栏中，单击 **[!UICONTROL Send]** （左上角）并选择您希望如何发送投放。

   ![](assets/deliv_coup_15.png)

1. 单击 **[!UICONTROL Analyze]**。如果分析日志确认有足够的赠券用于所有收件人，请单击 **[!UICONTROL Confirm delivery]** 以发送它。

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>有关如何管理投放优惠券不足的说明，请参阅 [管理优惠券不足](#managing-insufficient-coupons)

要确认投放是否成功，请执行以下操作：

1. 转到 **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**.
1. 单击 **[!UICONTROL Deliveries]** 选项卡。

   ![](assets/deliv_coup_17.png)

   状态显示为 **[!UICONTROL Finished]** 成功投放。

>[!NOTE]
>
>默认情况下，优惠券管理模块使用 **nms：recipient** 表格。 [了解详情](../../configuration/using/about-data-model.md#default-recipient-table)。
>
>了解如何使用自定义收件人表 [本页内容](../../configuration/using/about-custom-recipient-table.md).

## 管理优惠券不足 {#managing-insufficient-coupons}

如果优惠券少于消息，则投放分析将停止。 在这种情况下，您可以导入更多优惠券或限制消息数量。 如果要限制消息数量，请按照下面的说明操作。

1. 转到电子邮件投放窗口。
1. 单击 **[!UICONTROL To]**。
1. In **[!UICONTROL Select target]**，转到 **[!UICONTROL Exclusions]** 选项卡。

   ![](assets/deliv_coup_18.png)

1. 在排除设置部分，单击 **[!UICONTROL Edit]**.
1. 输入要发送的邮件数 **[!UICONTROL Limit delivery to...messages]** 并单击 **[!UICONTROL Ok]**. 您可以发送投放。

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>在管理有限数量的优惠券时，可通过投放工作流根据您的条件拆分投放。 如果要向选定的群体发送优惠券而不限制目标，这是一个很好的选项。
