---
product: campaign
title: 具有自定义日期字段的电子邮件扩充
description: 了解如何使用自定义日期字段丰富电子邮件
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows
exl-id: 85e0ec2a-b7cb-4d0b-a281-9ad72594403a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 4%

---

# 具有自定义日期字段的电子邮件扩充{#email-enrichment-with-custom-date-fields}



在本例中，我们希望向本月即将过生日的收件人发送一封包含自定义数据字段的电子邮件。 电子邮件将包含优惠券，有效期限为他们生日前后一周。

我们需要使用定位列表中的收件人，这些收件人将在本月庆祝生日 **[!UICONTROL Split]** 活动。 然后，使用 **[!UICONTROL Enrichment]** 活动，自定义数据字段将在电子邮件中用作客户特殊优惠的有效期。

![](assets/uc_enrichment.png)

要创建此示例，请应用以下步骤：

1. 在 **[!UICONTROL Targeting and workflows]** 选项卡，拖放 **[!UICONTROL Read list]** 用于定向收件人列表的活动。
1. 要处理的列表可以显式指定、由脚本计算或根据此处定义的选项和参数进行动态本地化。

   ![](assets/uc_enrichment_1.png)

1. 添加 **[!UICONTROL Split]** 此活动用于将本月即将过生日的收件人与其他收件人区分开来。
1. 若要拆分列表，请在以下位置输入： **[!UICONTROL Filtering of selected records]** 类别，选择 **[!UICONTROL Add a filtering condition on the inbound population]**. 然后，单击 **[!UICONTROL Edit]**.

   ![](assets/uc_enrichment_2.png)

1. 选择 **[!UICONTROL Filtering conditions]** 然后单击 **[!UICONTROL Edit expression]** 按钮，用于筛选收件人生日的月份。

   ![](assets/uc_enrichment_3.png)

1. 单击 **[!UICONTROL Advanced Selection]** 则 **[!UICONTROL Edit the formula using an expression]** 并添加以下表达式： Month(@birthDate)。
1. 在 **[!UICONTROL Operator]** 列中，选择 **[!UICONTROL equal to]**.
1. 通过添加 **[!UICONTROL Value]** 当前日期的月份： Month(GetDate())。

   这将查询其生日月份对应于当月的收件人。

   ![](assets/uc_enrichment_4.png)

1. 单击 **[!UICONTROL Finish]**。然后，在 **[!UICONTROL General]** 选项卡 **[!UICONTROL Split]** 活动，请单击 **[!UICONTROL Generate complement]** 在 **[!UICONTROL Results]** 类别。

   使用 **[!UICONTROL Complement]** 结果，您可以添加投放活动或更新列表。 在此，我们刚刚添加了一个 **[!UICONTROL End]** 活动。

   ![](assets/uc_enrichment_6.png)

您现在需要配置 **[!UICONTROL Enrichment]** 活动：

1. 添加 **[!UICONTROL Enrichment]** 在子集后添加活动，以添加自定义日期字段。

   ![](assets/uc_enrichment_7.png)

1. 打开您的 **[!UICONTROL Enrichment]** 活动。 在 **[!UICONTROL Complementary information]** 类别，单击 **[!UICONTROL Add data]**.

   ![](assets/uc_enrichment_8.png)

1. 选择 **[!UICONTROL Data linked to the filtering dimension]** 则 **[!UICONTROL Data of the filtering dimension]**.
1. 单击 **[!UICONTROL Add]** 按钮。

   ![](assets/uc_enrichment_9.png)

1. 添加 **[!UICONTROL Label]**. 然后，在 **[!UICONTROL Expression]** 列，单击 **[!UICONTROL Edit expression]**.

   ![](assets/uc_enrichment_10.png)

1. 首先，我们需要将出生日期前一周作为 **有效期开始日期** 具有以下属性 **[!UICONTROL Expression]**： `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. 然后，创建自定义日期字段 **有效期结束日期** ，以出生日期后的一周为目标，您需要添加 **[!UICONTROL Expression]**： `AddDays([target/@birthDate], 7)`.

   您可以在表达式中添加标签。

   ![](assets/uc_enrichment_12.png)

1. 单击 **[!UICONTROL Ok]**。您的扩充现已准备就绪。

在您的 **[!UICONTROL Enrichment]** 活动，则可以添加投放。 在本例中，我们添加了电子邮件投放，以向收件人发送包含有效日期的特殊优惠，供本月庆祝其生日的客户使用。

1. 拖放 **[!UICONTROL Email delivery]** 活动之后 **[!UICONTROL Enrichment]** 活动。

   ![](assets/uc_enrichment_15.png)

1. 双击 **[!UICONTROL Email delivery]** 活动，以开始个性化您的投放。
1. 添加 **[!UICONTROL Label]** 到您的投放，然后单击 **[!UICONTROL Continue]**.
1. 单击 **[!UICONTROL Save]** 以创建您的电子邮件投放。
1. 签入 **[!UICONTROL Approval]** 电子邮件投放的选项卡 **[!UICONTROL Properties]** 该 **[!UICONTROL Confirm delivery before sending option]** 已选中。

   然后，启动工作流以使用定向信息扩充叫客过渡。

   ![](assets/uc_enrichment_18.png)

您现在可以使用在中创建的自定义日期字段开始设计电子邮件投放 **[!UICONTROL Enrichment]** 活动。

1. 双击 **[!UICONTROL Email delivery]** 活动。
1. 将您的Target扩展添加到电子邮件中。 它应位于以下表达式内，以便配置有效日期的格式：

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. 单击 ![](assets/uc_enrichment_16.png) . 选择 **[!UICONTROL Target extension]** 随后，之前创建的自定义有效日期将使用 **[!UICONTROL Enrichment]** 活动，以将扩展添加到formatDate表达式中。

   ![](assets/uc_enrichment_19.png)

1. 根据需要配置电子邮件内容。

   ![](assets/uc_enrichment_17.png)

1. 预览电子邮件以检查自定义日期字段是否已正确配置

   ![](assets/uc_enrichment_20.png)

您的电子邮件现已准备就绪。 您可以开始发送校样并确认您的投放以发送生日电子邮件。
