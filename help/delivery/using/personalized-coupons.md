---
solution: Campaign Classic
product: campaign
title: 个性化优惠券
description: 个性化优惠券
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 1%

---


# 个性化优惠券{#personalized-coupons}

向投放添加优惠券可以为收件人提供更高的产品和服务价值。 您可以使用活动优惠券模块创建一组优惠券，您希望将这些优惠券添加到即将到来的营销优惠。 准备好创建投放时，请分配适用的优惠券。 由于优惠券在选择的时间段内有效，所分配的优惠券将唯一链接到其投放消息。 此外，活动确认在发送投放之前有足够的优惠券来存储邮件数。

>[!NOTE]
>
>优惠券管理是一个必须安装的包。 要确认您有优惠券管理，请检查 **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>优惠券数据可以使用CSV和XML格式导入和导出。 有关导入和导出的详细信息，请参 [阅本节](../../platform/using/generic-imports-and-exports.md)。

## 创建优惠券 {#creating-a-coupon}

优惠券模块在创建优惠券时为您提供两个选项：

* **匿名**:用于选定收件人或列表收件人的通用优惠券。
* **个人**:针对特定收件人的个性化优惠券。

在执行以下步骤之前，请确保您知道要创建的优惠券类型。

1. 在活动树中，转到 **[!UICONTROL Resources > Campaign management > Coupons]**。

   ![](assets/deliv_coup_01.png)

1. 单击 **[!UICONTROL New]** 按钮。
1. 在字段中输入优惠券的 **[!UICONTROL Label]** 名称。 已在中自动输入唯一代码 **[!UICONTROL Coupon code]**。 您可以保留代码或输入新代码。

   ![](assets/deliv_coup_02.png)

1. 选 **[!UICONTROL Start date]** 择 **[!UICONTROL End date]** 并设置优惠券有效的期间。
1. 在中， **[!UICONTROL Coupon type]**&#x200B;选择“匿名”或“个人”。

   **[!UICONTROL Anonymous coupons]** :匿名优惠券对于所有收件人都是相同的。 确认在“优惠券类型”菜单中 **选择了** “匿名”, **然后单击“** 保存”以生成优惠券。

   **[!UICONTROL Individual coupons]** :单个优惠券可通过附加优惠券代码进一步个性化。 例如，在体育设备商店为销售创建单独的优惠券。 然而，收件人的列表时间很长，他们对单项运动的热情也不一样。 您可以根据一项运动（如足球、足球、棒球等）为单个优惠券添加代码名称。 并将每个代码发送给适用的收件人。

   1. 选择“个人”时，左下角会显示一个新的选项卡“优惠券”。 转到选项卡 **[!UICONTROL Coupons]** 并单击 **[!UICONTROL Add]**。
   1. 在弹出窗口提示时，为单个优惠券输入唯一代码。
   1. 单击 **[!UICONTROL Save]** 以生成优惠券。

   有关“优惠券”选项卡的详细信息，请参 [阅配置单个优惠券](#configuring-individual-coupons)。

   >[!NOTE]
   >
   >可以批量导入单个优惠券。 有关导入和导出的详细信息，请参 [阅本节](../../platform/using/generic-imports-and-exports.md)。

### 配置单个优惠券 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

“优惠券”标签仅适用于单个优惠券。 在优惠券与投放关联后，优惠券选项卡提供以下详细信息：

* **[!UICONTROL Status]** :优惠券可用性。
* **[!UICONTROL Redeemed on]** :优惠券的兑换日期。
* **[!UICONTROL Channel]** :用于发送优惠券的渠道。
* **[!UICONTROL Address]** :收件人的电子邮件地址。

、 **[!UICONTROL status]**&#x200B;和 **[!UICONTROL channel]**&#x200B;的 **[!UICONTROL address]** 值将自动完成。 但是，活动 **[!UICONTROL redeemed on]** 不会恢复值。 可以通过导入包含优惠券兑换详细信息的文件来完成这些操作。

## 将优惠券插入电子邮件投放 {#inserting-a-coupon-into-an-email-delivery}

在以下示例中，投放是从主页创建的。 有关如何创建投放的详细说明，请参 [阅此部分](../../delivery/using/about-email-channel.md)。 您还可以在工作流中向投放添加优惠券。

1. 转到并 **[!UICONTROL Campaigns]** 选择 **[!UICONTROL Deliveries]**。
1. 单击 **[!UICONTROL Create]**.

   ![](assets/deliv_coup_04.png)

1. 在中输入名称 **[!UICONTROL Label]** 并单击 **[!UICONTROL Continue]**。
1. 单击 **[!UICONTROL To]** 以添加收件人。
1. 单 **[!UICONTROL Add]** 击以选择投放。 选择收件人后，单击 **[!UICONTROL Ok]** 以返回投放。

   ![](assets/deliv_coup_05.png)

1. 输入主题并向邮件中添加内容。

   ![](assets/deliv_coup_06.png)

1. 在工具栏中，单 **[!UICONTROL Properties]** 击并选择选 **[!UICONTROL Advanced]** 项卡。
1. 单击的文件夹图 **[!UICONTROL Coupon management]**&#x200B;标。

   ![](assets/deliv_coup_07.png)

1. 选择优惠券并单击 **[!UICONTROL Ok]**。 再次 **[!UICONTROL Ok]** 单击。

   ![](assets/deliv_coup_08.png)

1. 单击消息以选择要放置优惠券的位置。

   ![](assets/deliv_coup_09.png)

1. 单击个性化图标，根据优惠券类型选择以下选项之一：

   * 匿名优惠券： **[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * 个人优惠券： **[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      优惠券将作为代码而不是您指定的名称插入到消息中。 代码在活动标准数据模型中使用。
   ![](assets/deliv_coup_12.png)

1. 运行测试以确认您分配给优惠券的名称。 转到选项卡 **[!UICONTROL Preview]** 并单击 **[!UICONTROL Test personalization]**。 选择测试收件人。

   ![](assets/deliv_coup_13.png)

   测试后，优惠券应显示为指定的名称，而不是代码。

   ![](assets/deliv_coup_14.png)

1. 在工具栏中，单 **[!UICONTROL Send]** 击（左上方）并选择要发送投放的方式。

   ![](assets/deliv_coup_15.png)

1. 单击 **[!UICONTROL Analyze]**。如果分析日志确认所有收件人有足够的优惠券，请单 **[!UICONTROL Confirm delivery]** 击以发送。

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>有关如何管理投放票据不足的说明，请参阅管 [理票据不足](#managing-insufficient-coupons)

确认投放成功：

1. 转到 **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**。
1. 单击选 **[!UICONTROL Deliveries]** 项卡。

   ![](assets/deliv_coup_17.png)

   状态将显示为 **[!UICONTROL Finished]** 成功投放。

>[!NOTE]
>
>默认情况下，优惠券管理模块使用 **nms:收件人** 表。 有关如何使用其他表的说明，请参阅编 [辑模式](../../configuration/using/data-schemas.md)。

## 管理票据不足 {#managing-insufficient-coupons}

如果优惠券数少于消息数，投放分析将停止。 在这种情况下，您可以导入更多优惠券或限制消息数。 如果要限制消息数，请按照以下说明操作。

1. 转到电子邮件投放窗口。
1. 单击 **[!UICONTROL To]**.
1. In **[!UICONTROL Select target]**, go to the **[!UICONTROL Exclusions]** tab.

   ![](assets/deliv_coup_18.png)

1. 在排除设置部分，单击 **[!UICONTROL Edit]**。
1. 输入要发送的邮件数，然 **[!UICONTROL Limit delivery to...messages]** 后单击 **[!UICONTROL Ok]**。 您可以发送投放。

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>在管理有限数量的优惠券时，投放工作流允许您根据条件分割投放。 如果您希望将优惠券发送给选定人群而不限制目标，这是一个不错的选择。
