---
product: campaign
title: 个性化块
description: 了解如何使用个性化块
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Personalization
role: User
exl-id: 8d155844-d18a-4165-9886-c3b144109f6e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 2%

---

# 个性化块{#personalization-blocks}

个性化块是动态的、个性化的，并包含您可以插入到投放中的特定渲染。 例如，您可以添加徽标、问候语消息或指向镜像页面的链接。 请参阅[插入个性化块](#inserting-personalization-blocks)。

![](assets/do-not-localize/how-to-video.png)在视频](#personalization-blocks-video)中发现此功能[

通过Adobe Campaign资源管理器的&#x200B;**[!UICONTROL Resources > Campaign Management > Personalization blocks]**&#x200B;节点访问个性化块。 默认情况下，有多个块可用（请参阅[现成的个性化块](#out-of-the-box-personalization-blocks)）。

您可以定义新块，以便优化投放个性化。 有关详细信息，请参阅[定义自定义个性化块](#defining-custom-personalization-blocks)。

>[!NOTE]
>
>**[!UICONTROL Digital Content Editor (DCE)]**&#x200B;中还提供了个性化块。 有关详细信息，请参见[此页面](../../web/using/editing-content.md#inserting-a-personalization-block)。

## 插入个性化块 {#inserting-personalization-blocks}

要在消息中插入个性化块，请执行以下步骤：

1. 在投放向导的内容编辑器中，单击个性化字段图标并选择&#x200B;**[!UICONTROL Include]**&#x200B;菜单。
1. 从列表中选择一个个性化块（该列表显示10个上次使用的块），或单击&#x200B;**[!UICONTROL Other...]**&#x200B;菜单访问完整列表。

   ![](assets/s_ncs_user_personalized_block01.png)

1. **[!UICONTROL Other...]**&#x200B;菜单可访问所有现成的和自定义的个性化块（请参阅[现成的个性化块](#out-of-the-box-personalization-blocks)和[定义自定义个性化块](#defining-custom-personalization-blocks)）。

   ![](assets/s_ncs_user_personalized_block02.png)

1. 个性化块随后将作为脚本插入。 当生成个性化时，它自动适应收件人用户档案。

   ![](assets/s_ncs_user_personalized_block03.png)

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡并选择收件人以查看个性化设置。

   ![](assets/s_ncs_user_personalized_block04.png)

您可以在投放内容中包含个性化块的源代码。 要执行此操作，请在选择&#x200B;**[!UICONTROL Include the HTML source code of the block]**&#x200B;时将其选定。

![](assets/s_ncs_user_personalized_block05.png)

HTML源代码将插入到投放内容中。 例如，**[!UICONTROL Greetings]**&#x200B;个性化块显示如下：

![](assets/s_ncs_user_personalized_block06.png)

## 个性化块示例 {#personalization-blocks-example}

在本例中，我们创建了一封电子邮件，其中使用个性化块让收件人能够查看镜像页面、在社交网络上共享新闻稿并取消订阅未来的投放。

为此，我们需要插入以下个性化块：

* **[!UICONTROL Link to mirror page]** 。
* **[!UICONTROL Social network sharing links]** 。
* **[!UICONTROL Unsubscription link]** 。

>[!NOTE]
>
>有关生成镜像页面的详细信息，请参阅[生成镜像页面](sending-messages.md#generating-the-mirror-page)。

1. 创建新投放或打开现有的电子邮件类型投放。
1. 在投放向导中，单击&#x200B;**[!UICONTROL Subject]**&#x200B;编辑邮件的主题并输入主题。
1. 在消息正文中插入个性化块。 为此，请单击邮件内容，单击个性化字段图标并选择&#x200B;**[!UICONTROL Include]**&#x200B;菜单。
1. 选择要插入的第一个块。 续订过程以包含其他两个块。

   ![](assets/s_ncs_user_personalized_block_example.png)

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以查看个性化结果。 您必须选择一个收件人以显示该收件人的消息。

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. 确认块内容已正确显示。

## 现成的个性化块 {#out-of-the-box-personalization-blocks}

默认情况下，提供个性化块列表以帮助您个性化消息的内容。

>[!NOTE]
>
>个性化块的列表取决于实例上已安装的模块和选项。

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** ：插入带有收件人名称的问候语。 示例：“Hello John Doe,”。
* **[!UICONTROL Insert logo]** ：插入在配置实例时定义的现成徽标。
* **[!UICONTROL Powered by Adobe Campaign]** ：插入“Powered by Adobe Campaign”徽标。
* **[!UICONTROL Mirror page URL]** ：插入镜像页面URL，使投放设计器能够检查链接。

  >[!NOTE]
  >
  >有关生成镜像页面的详细信息，请参阅[生成镜像页面](sending-messages.md#generating-the-mirror-page)。

* **[!UICONTROL Link to mirror page]** ：插入指向镜像页面的链接：“如果您无法正确查看此消息，请单击此处”。
* 列入阻止列表 **[!UICONTROL Unsubscription link]** ：插入链接以取消订阅所有投放（订阅）。
* **[!UICONTROL Formatting function for proper nouns]** ：生成&#x200B;**[!UICONTROL toSmartCase]** Javascript函数，该函数将每个单词的第一个字母更改为大写。
* **[!UICONTROL Registration page URL]** ：插入订阅URL（请参阅[关于服务和订阅](about-services-and-subscriptions.md)）。
* **[!UICONTROL Registration link]** ：插入订阅链接。 ，该参数在配置实例时定义。
* **[!UICONTROL Registration link (with referrer)]** ：插入订阅链接，以便识别访客和投放。 已在配置实例时定义链接。

  >[!NOTE]
  >
  >此块只能在仅针对访客的投放中使用。

* **[!UICONTROL Registration confirmation]** ：插入用于确认订阅的链接。
* **[!UICONTROL Social network sharing links]** ：插入一些按钮，这些按钮允许收件人与电子邮件客户端、Facebook、X(以前称为Twitter)和LinkedIn共享指向镜像页面内容的链接（请参阅[病毒式营销：转发给朋友](viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)）。
* **[!UICONTROL Style of content emails]**&#x200B;和&#x200B;**[!UICONTROL Notification style]** ：生成使用预定义的HTML样式设置电子邮件格式的代码。 这些块必须插入投放的源代码（在&#x200B;**[!UICONTROL ...]**&#x200B;部分中）的&#x200B;**`<style>...</style>`**&#x200B;标记中。
* **[!UICONTROL Offer acceptance URL in unitary mode]** ：插入一个URL，用于设置交互选件为&#x200B;**[!UICONTROL Accepted]**（请参阅[此部分](../../interaction/using/offer-analysis-report.md)）。

## 定义自定义个性化块 {#defining-custom-personalization-blocks}

您可以通过&#x200B;**[!UICONTROL Include...]**&#x200B;菜单定义要从个性化字段图标插入的新个性化字段。 这些字段在个性化块中定义。

要创建个性化块，请转到资源管理器并应用以下步骤：

1. 单击&#x200B;**[!UICONTROL Resources > Campaign Management > Personalization blocks]**&#x200B;节点。
1. 右键单击块列表并选择&#x200B;**[!UICONTROL New]** 。
1. 填写个性化块的设置：

   ![](assets/s_ncs_user_personalized_block.png)

   * 输入块的标签。 此标签将显示在个性化字段插入窗口中。
   * 选择&#x200B;**[!UICONTROL Visible in the customization menus]**&#x200B;以通过个性化字段插入图标访问此块。
   * 如有必要，请选择&#x200B;**[!UICONTROL The content of the personalization block depends upon the format]**&#x200B;以为HTML格式和文本格式的电子邮件定义两个单独的块。

     然后，此编辑器的下部分会显示两个选项卡(HTML内容和文本内容)以定义相应的内容。

     ![](assets/s_ncs_user_personalized_block_b.png)

   * 输入内容(在HTML、文本、JavaScript等) 个性化块的，然后单击&#x200B;**[!UICONTROL Save]**。

## 教程视频 {#personalization-blocks-video}

了解如何创建动态内容块以及如何使用动态内容块将电子邮件投放内容个性化。

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他Campaign Classic操作方法视频。
