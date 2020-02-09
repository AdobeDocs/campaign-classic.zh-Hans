---
title: 跨渠道交付工作流
seo-title: 跨渠道交付工作流
description: 跨渠道交付工作流
seo-description: null
page-status-flag: never-activated
uuid: 02d51b13-656f-48f3-b744-5968ffa94b3e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 2fe907da-ef37-46e2-a8fb-6ad4e18be486
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 跨渠道交付工作流{#cross-channel-delivery-workflow}

此用例展示了一个涉及跨渠道交付工作流的示例。 本节介绍了跨渠道交付的一 [般概念](../../workflow/using/cross-channel-deliveries.md)。

目标是将来自数据库收件人的受众细分为不同的用户组，以向用户组发送电子邮件，向另一个用户组发送SMS消息。

此用例的主要实施步骤如下：

1. 创建活 **[!UICONTROL Query]** 动以定位受众。
1. 创建包含 **[!UICONTROL Email delivery]** 选件链接的活动。
1. 使用活 **[!UICONTROL Split]** 动可：

   * 向未打开第一封电子邮件的收件人发送另一封电子邮件。
   * 向打开电子邮件但未点击选件链接的收件人发送SMS。
   * 将打开电子邮件并单击链接的收件人添加到数据库。

![](assets/wkf_cross-channel_7.png)

## 第1步：定位受众 {#step-1--targeting-the-audience}

要定义目标，请创建查询以标识收件人。

1. 创建营销活动。 如需详细信息，请参阅[此部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在营销 **[!UICONTROL Targeting and workflows]** 活动的选项卡中，将查询 **** 活动添加到工作流中。 For more on using this activity, refer to [this section](../../workflow/using/query.md).
1. 定义接收您的分发的收件人。 例如，选择“黄金”成员作为目标维。
1. 为查询添加筛选条件。 在此示例中，选择具有电子邮件地址和移动号码的收件人。

   ![](assets/wkf_cross-channel_3.png)

1. 保存更改。

## 第2步：创建包含选件的电子邮件 {#step-2--creating-an-email-including-an-offer}

1. 创建活 **[!UICONTROL Email delivery]** 动，然后在工作流中双击它以对其进行编辑。 有关创建电子邮件的详细信息，请参 [阅此部分](../../delivery/using/about-email-channel.md)。
1. 设计消息并在内容中插入包含选件的链接。

   ![](assets/wkf_cross-channel_1.png)

   有关将选件集成到消息正文中的详细信息，请参 [阅本节](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine)。

1. 保存更改。
1. 右键单击活 **[!UICONTROL Email delivery]** 动可将其打开。
1. 选择 **[!UICONTROL Generate an outbound transition]** 选项以恢复人口和跟踪日志。

   ![](assets/wkf_cross-channel_2.png)

   这样，您就可以根据收件人在收到第一封电子邮件时的行为，使用此信息发送另一封电子邮件。

1. 添加一 **[!UICONTROL Wait]** 个活动，让收件人在几天内打开电子邮件。

   ![](assets/wkf_cross-channel_4.png)

## 第3步：细分最终受众 {#step-3--segmenting-the-resulting-audience}

在识别目标并创建第一个交付后，您需要使用过滤条件将目标细分为不同人群。

1. 向工作 **流中添加** “拆分”活动并将其打开。 For more on using this activity, refer to [this section](../../workflow/using/split.md).
1. 从查询中上游计算的人群创建三个区段。

   ![](assets/wkf_cross-channel_6.png)

1. 对于第一个子集，选择选 **[!UICONTROL Add a filtering condition on the inbound population]** 项并单击 **[!UICONTROL Edit]**。

   ![](assets/wkf_cross-channel_8.png)

1. 选择 **[!UICONTROL Recipients of a delivery]** 作为限制过滤器并单击 **[!UICONTROL Next]**。

   ![](assets/wkf_cross-channel_9.png)

1. 在筛选器设置中，从 **[!UICONTROL Recipients who have not opened or clicked (email)]** 下拉列 **[!UICONTROL Behavior]** 表中选择，然后选择电子邮件，其中包括您要从分发列表发送的选件。 单击 **[!UICONTROL Finish]**.

   ![](assets/wkf_cross-channel_10.png)

1. 以同样方式继续第二个子集， **[!UICONTROL Recipients who have not clicked (email)]** 然后从 **[!UICONTROL Behavior]** 下拉列表中选择。

   ![](assets/wkf_cross-channel_11.png)

1. 对于第三个子集，在选择并单 **[!UICONTROL Add a filtering condition on the inbound population]** 击后 **[!UICONTROL Edit]**，选择 **[!UICONTROL Use a specific filtering dimension]** 选项。
1. 从下 **[!UICONTROL Recipient tracking log]** 拉列 **[!UICONTROL Filtering dimension]** 表中选择，从中高 **[!UICONTROL Filtering conditions]** 亮显示并 **[!UICONTROL List of restriction filters]** 单击 **[!UICONTROL Next]**。

   ![](assets/wkf_cross-channel_12.png)

1. 按如下方式选择筛选条件：

   ![](assets/wkf_cross-channel_13.png)

1. 单击 **[!UICONTROL Finish]** 以保存更改。

## 第4步：最终确定工作流 {#step-4--finalizing-the-workflow}

1. 将相关活动添加到由活动产生的三个子集之后的工作流 **[!UICONTROL Split]** 中：

   * 添加活 **[!UICONTROL Email delivery]** 动以向第一个子集发送提醒电子邮件。
   * 添加一 **[!UICONTROL Mobile delivery]** 个活动以向第二子集发送SMS消息。
   * 添加一 **[!UICONTROL List update]** 个活动，将相应的收件人添加到数据库。

1. 双击工作流中的交付活动以对其进行编辑。 有关创建电子邮件和SMS的详细信息，请参 [阅电子邮件](../../delivery/using/about-email-channel.md)[渠道和SMS渠道](../../delivery/using/sms-channel.md)。
1. 双击活动 **[!UICONTROL List update]** 并选择选 **[!UICONTROL Generate an outbound transition]** 项。

   然后，您可以将生成的收件人从Adobe Campaign导出到Adobe Experience Cloud。 例如，您可以通过向工作流中添加活动来在Adobe Target **[!UICONTROL Update shared audience]** 中使用受众。 有关此内容的详细信息，请参 [阅导出受众](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience)。

1. 单击操 **作栏中** 的“开始”按钮以执行工作流。

查询活动所针对的 **** 人群将被分段，以根据收件人的行为接收电子邮件或SMS发送。 剩余人口将使用活动添加到数据 **[!UICONTROL List update]** 库。
