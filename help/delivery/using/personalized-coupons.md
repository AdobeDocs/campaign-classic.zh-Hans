---
product: campaign
title: 个性化优惠券
description: 了解如何创建和插入个性化优惠券
feature: Personalization
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 1%

---

# 个性化优惠券{#personalized-coupons}

![](../../assets/v7-only.svg)

向投放添加优惠券可为收件人提供更高的产品和服务价值。 您可以使用促销活动优惠券模块创建一组要添加到即将推出的营销选件的优惠券。 准备好创建投放时，分配适用的优惠券。 由于优惠券在选定时段内有效，因此分配的优惠券将唯一地链接到其投放消息。 此外，Campaign会确认在发送投放之前有足够的优惠券接收消息数量。

>[!NOTE]
>
>优惠券管理是必须安装的包。 要确认您具有优惠券管理，请勾选 **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>优惠券数据可以使用CSV和XML格式导入和导出。 有关导入和导出的详细信息，请参阅 [此部分](../../platform/using/get-started-data-import-export.md).

## 创建优惠券 {#creating-a-coupon}

在创建优惠券时，优惠券模块为您提供两个选项：

* **匿名**:选定收件人或收件人列表的通用优惠券。
* **个人**:针对选定收件人的个性化优惠券。

在执行以下步骤之前，请确保您知道要创建的优惠券类型。

1. 在营销活动树中，转到 **[!UICONTROL Resources > Campaign management > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. 单击 **[!UICONTROL New]** 按钮。
1. 在 **[!UICONTROL Label]** 字段。 已自动在 **[!UICONTROL Coupon code]**. 您可以保留代码或输入新代码。

   ![](assets/deliv_coup_02.png)

1. 选择 **[!UICONTROL Start date]** 和 **[!UICONTROL End date]** 设置优惠券有效的期限。
1. 在 **[!UICONTROL Coupon type]**，请选择“匿名”或“个人”。

   **[!UICONTROL Anonymous coupons]** :所有收件人的匿名优惠券都相同。 确认在 **优惠券类型** 菜单，单击 **保存** 以生成优惠券。

   **[!UICONTROL Individual coupons]** :单个优惠券可以进一步使用附加优惠券代码进行个性化。 例如，在体育用品商店为销售创建单个优惠券。 然而，受训者名单很长，他们对一项体育运动的热情并不相同。 您可以根据体育运动（例如足球、足球、棒球等）为单个优惠券添加代码名称 并将每个代码发送给适用的收件人。

   1. 选择“个人”时，左下角会显示一个新选项卡“优惠券”。 转到 **[!UICONTROL Coupons]** 选项卡，单击 **[!UICONTROL Add]**.
   1. 在弹出窗口提示时，为单个优惠券输入唯一代码。
   1. 单击 **[!UICONTROL Save]** 以生成优惠券。

   有关“优惠券”选项卡的更多详细信息，请参阅 [配置单个优惠券](#configuring-individual-coupons).

   >[!NOTE]
   >
   >可以批量导入单个优惠券。 有关导入和导出的详细信息，请参阅 [此部分](../../platform/using/get-started-data-import-export.md).

### 配置单个优惠券 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

“优惠券”选项卡仅可用于“单个优惠券”。 将优惠券与投放关联后，“优惠券”选项卡提供以下详细信息：

* **[!UICONTROL Status]** :优惠券的可用性。
* **[!UICONTROL Redeemed on]** :票息兑换日期。
* **[!UICONTROL Channel]** :用于发送优惠券的渠道。
* **[!UICONTROL Address]** :收件人的电子邮件地址。

的值 **[!UICONTROL status]**, **[!UICONTROL channel]**&#x200B;和 **[!UICONTROL address]** 自动完成。 但是， **[!UICONTROL redeemed on]** Campaign未恢复。 可通过导入包含优惠券兑换详细信息的文件来完成这些操作。

## 在电子邮件投放中插入优惠券 {#inserting-a-coupon-into-an-email-delivery}

在以下示例中，从主页创建投放。 有关如何创建投放的详细说明，请参阅 [此部分](about-email-channel.md). 您还可以在工作流中向投放添加优惠券。

1. 转到 **[!UICONTROL Campaigns]** 选择 **[!UICONTROL Deliveries]**.
1. 单击 **[!UICONTROL Create]**。

   ![](assets/deliv_coup_04.png)

1. 在中输入名称 **[!UICONTROL Label]** 单击 **[!UICONTROL Continue]**.
1. 单击 **[!UICONTROL To]** 添加收件人。
1. 单击 **[!UICONTROL Add]** 来选择投放的收件人。 选择收件人后，单击 **[!UICONTROL Ok]** 返回投放。

   ![](assets/deliv_coup_05.png)

1. 输入主题并向消息中添加内容。

   ![](assets/deliv_coup_06.png)

1. 在工具栏中，单击 **[!UICONTROL Properties]** 然后选择 **[!UICONTROL Advanced]** 选项卡。
1. 单击的文件夹图标 **[!UICONTROL Coupon management]**.

   ![](assets/deliv_coup_07.png)

1. 选择优惠券并单击 **[!UICONTROL Ok]**. 单击 **[!UICONTROL Ok]** 再次。

   ![](assets/deliv_coup_08.png)

1. 单击消息以选择要将优惠券放置到的位置。

   ![](assets/deliv_coup_09.png)

1. 单击个性化图标，根据优惠券类型选择以下选项之一：

   * 匿名优惠券： **[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * 单个优惠券： **[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      优惠券将作为代码而不是您指定的名称插入到消息中。 该代码在Campaign Ootb数据模型中使用。
   ![](assets/deliv_coup_12.png)

1. 运行测试以确认您分配给优惠券的名称。 转到 **[!UICONTROL Preview]** 选项卡，单击 **[!UICONTROL Test personalization]**. 选择测试的收件人。

   ![](assets/deliv_coup_13.png)

   测试后，优惠券应显示为分配的名称，而不是代码。

   ![](assets/deliv_coup_14.png)

1. 在工具栏中，单击 **[!UICONTROL Send]** （左上方），然后选择发送投放的方式。

   ![](assets/deliv_coup_15.png)

1. 单击 **[!UICONTROL Analyze]**。如果分析日志确认所有收件人的优惠券都足够，请单击 **[!UICONTROL Confirm delivery]** 来发送。

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>有关如何管理投放的优惠券不足的说明，请参阅 [管理优惠券不足](#managing-insufficient-coupons)

确认投放成功：

1. 转到 **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**.
1. 单击 **[!UICONTROL Deliveries]** 选项卡。

   ![](assets/deliv_coup_17.png)

   状态显示为 **[!UICONTROL Finished]** 成功投放。

>[!NOTE]
>
>默认情况下，优惠券管理模块使用 **nms:recipient** 表。 [了解详情](../../configuration/using/about-data-model.md#default-recipient-table)。
>
>了解如何使用自定义收件人表 [本页](../../configuration/using/about-custom-recipient-table.md).

## 管理优惠券不足 {#managing-insufficient-coupons}

如果优惠券数少于消息数，投放分析会停止。 在这种情况下，您可以导入更多优惠券或限制消息数量。 如果要限制消息数量，请按照以下说明操作。

1. 转到电子邮件投放窗口。
1. 单击 **[!UICONTROL To]**。
1. 在 **[!UICONTROL Select target]**，转到 **[!UICONTROL Exclusions]** 选项卡。

   ![](assets/deliv_coup_18.png)

1. 在排除设置部分中，单击 **[!UICONTROL Edit]**.
1. 输入要发送的消息数 **[!UICONTROL Limit delivery to...messages]** 单击 **[!UICONTROL Ok]**. 您可以发送投放。

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>在管理有限数量的优惠券时，通过投放工作流，您可以根据标准对投放进行拆分。 如果要向选定的群体发送优惠券而不限制目标，则此选项是一个不错的选项。
