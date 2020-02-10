---
title: 个性化基块
seo-title: 个性化基块
description: 个性化基块
seo-description: null
page-status-flag: never-activated
uuid: f9867f8d-f6ce-4a5f-b6b4-fd8056d28576
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: e68d1435-70e6-479e-a347-9ff9f9f11b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 个性化基块{#personalization-blocks}

个性化基块是动态的、个性化的，并包含可插入交付的特定呈现。 例如，可以添加标志、问候语消息或指向镜像页面的链接。 请参阅 [插入个性化基块](#inserting-personalization-blocks)。

>[!NOTE]
>
>个性化基块也可从中获取 **[!UICONTROL Digital Content Editor (DCE)]** 。 有关详细信息，请参见[此页面](../../web/using/editing-content.md#inserting-a-personalization-block)。

个性化基块可通过Adobe Campaign浏 **[!UICONTROL Resources > Campaign Management > Personalization blocks]** 览器的节点访问。 默认情况下，有几个基 [块可用(请参阅现成的个性化基块](#out-of-the-box-personalization-blocks))。

您能够定义新的基块，以便优化投放个性化。 有关此方面的详细信息，请参阅定 [义自定义个性化基块](#defining-custom-personalization-blocks)。

## 插入个性化基块 {#inserting-personalization-blocks}

要在消息中插入个性化块，请执行以下步骤：

1. 在分发向导的内容编辑器中，单击个性化字段图标，然后选择菜 **[!UICONTROL Include]** 单。
1. 从列表中选择一个个性化区块（列表显示10个最近使用的区块），或单击菜 **[!UICONTROL Other...]** 单以访问完整列表。

   ![](assets/s_ncs_user_personalized_block01.png)

1. 通 **[!UICONTROL Other...]** 过菜单可以访问所有现成的和自定义个性化基块(请参阅 [现成的个性化基块和定](#out-of-the-box-personalization-blocks) 义自定义个性化基块 [](#defining-custom-personalization-blocks))。

   ![](assets/s_ncs_user_personalized_block02.png)

1. 然后，个性化块作为脚本插入。 在生成个性化时，它自动适应于接收者配置文件。

   ![](assets/s_ncs_user_personalized_block03.png)

1. 单击选 **[!UICONTROL Preview]** 项卡，然后选择收件人以查看个性化。

   ![](assets/s_ncs_user_personalized_block04.png)

您可以在分发内容中包含个性化块的源代码。 要执行此操作，请在选 **[!UICONTROL Include the HTML source code of the block]** 择时选择它。

![](assets/s_ncs_user_personalized_block05.png)

HTML源代码将插入到交付内容中。 例如，个性化 **[!UICONTROL Greetings]** 区块显示如下：

![](assets/s_ncs_user_personalized_block06.png)

## 个性化基块示例 {#personalization-blocks-example}

在此示例中，我们创建了一封电子邮件，其中我们使用个性化区块使收件人能够查看镜像页面、在社交网络上共享新闻稿以及取消订阅将来的分发。

为此，我们需要插入以下个性化基块：

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>有关镜像页面生成的详细信息，请参阅 [生成镜像页面](../../delivery/using/sending-messages.md#generating-the-mirror-page)。

1. 创建新的分发或打开现有电子邮件类型的分发。
1. 在传送向导中，单 **[!UICONTROL Subject]** 击以编辑邮件的主题并输入主题。
1. 在邮件正文中插入个性化基块。 为此，请单击消息内容中的个性化字段图标，然后选择菜 **[!UICONTROL Include]** 单。
1. 选择要插入的第一个块。 续订该过程以包括另外两个区块。

   ![](assets/s_ncs_user_personalized_block_example.png)

1. 单击选 **[!UICONTROL Preview]** 项卡以查看个性化结果。 您必须选择一个收件人才能显示该收件人的消息。

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. 确认正确显示块内容。

## 开箱即用的个性化基块 {#out-of-the-box-personalization-blocks}

默认情况下，提供个性化基块列表，帮助您个性化消息内容。

>[!NOTE]
>
>个性化基块列表取决于实例中已安装的模块和选项。

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** :插入带收件人姓名的问候语。 示例：“你好，John Doe,”
* **[!UICONTROL Insert logo]** :插入在配置实例时定义的现成徽标。
* **[!UICONTROL Powered by Adobe Campaign]** :插入“Powered by Adobe Campaign”徽标。
* **[!UICONTROL Mirror page URL]** :插入镜像页面URL，使交付设计人员能够检查链接。

   >[!NOTE]
   >
   >有关镜像页面生成的详细信息，请参阅 [生成镜像页面](../../delivery/using/sending-messages.md#generating-the-mirror-page)。

* **[!UICONTROL Link to mirror page]** :插入指向镜像页面的链接：“如果您无法正确查看此消息，请单击此处”。
* **[!UICONTROL Unsubscription link]** :插入一个链接，允许取消订阅所有分发（黑名单）。
* **[!UICONTROL Formatting function for proper nouns]** :生成 **[!UICONTROL toSmartCase]** Javascript函数，该函数将每个单词的第一个字母更改为大写。 此块必须插入到交付的源代码中，并插入到标 **`<script>...</script>`** 记中。

   在以下示例中，该函数用于将元素“My header”替换为“My new header”，并在每个单词处使用大写字母：

   ```
   <h1 id="sample">My header</h1>
   <script><%@ include view='toSmartCase'%>;
   document.getElementById("sample").innerHTML = toSmartCase("My new header");
   </script>
   ```

   ![](assets/s_ncs_user_personalized_block_uppercasefunction.png)

* **[!UICONTROL Registration page URL]** :插入订阅URL(请参阅 [关于服务和订阅](../../delivery/using/about-services-and-subscriptions.md))。
* **[!UICONTROL Registration link]** :插入订阅链接。 在配置实例时定义。
* **[!UICONTROL Registration link (with referrer)]** :插入订阅链接，启用该链接可识别访客和分发。 配置实例时已定义链接。

   >[!NOTE]
   >
   >此区块仅可用于面向访客的分发。

* **[!UICONTROL Registration confirmation]** :插入一个允许确认订阅的链接。
* **[!UICONTROL Social network sharing links]** :插入一些按钮，使收件人能够与电子邮件客户端、Facebook、Twitter、Google +和LinkedIn共享指向镜像页面内容的链接(请参 [阅病毒式营销：转给朋友](../../delivery/using/viral-and-social-marketing.md#viral-marketing--forward-to-a-friend))。
* **[!UICONTROL Style of content emails]** 和 **[!UICONTROL Notification style]** :生成使用预定义HTML样式设置电子邮件格式的代码。 这些块必须插入到交付的源代码中的部分中的 **[!UICONTROL ...]** 标签中 **`<style>...</style>`** 。
* **[!UICONTROL Offer acceptance URL in unitary mode]** :插入一个URL，用于将交互选件设置 **[!UICONTROL Accepted]** 为(请参 [阅此部分](../../interaction/using/offer-analysis-report.md))。

## 定义自定义个性化基块 {#defining-custom-personalization-blocks}

您可以通过菜单从个性化字段图标定义要插入的新个性化 **[!UICONTROL Include...]** 字段。 这些字段在个性化基块中定义。

要创建个性化区块，请转至资源管理器并应用以下步骤：

1. 单击节 **[!UICONTROL Resources > Campaign Management > Personalization blocks]** 点。
1. 右键单击块列表并选择 **[!UICONTROL New]** 。
1. 填写个性化区块的设置：

   ![](assets/s_ncs_user_personalized_block.png)

   * 输入块的标签。 此标签将显示在个性化字段插入窗口中。
   * 选择 **[!UICONTROL Visible in the customization menus]** 以使此块可从个性化字段插入图标访问。
   * 如有必要，选 **[!UICONTROL The content of the personalization block depends upon the format]** 择为HTML格式和文本格式的电子邮件定义两个单独的块。

      然后，在此编辑器的下半部分（HTML内容和文本内容）中显示两个选项卡以定义相应的内容。

      ![](assets/s_ncs_user_personalized_block_b.png)

   * 输入内容（HTML、文本、JavaScript等）并单击 **[!UICONTROL Save]** 。
