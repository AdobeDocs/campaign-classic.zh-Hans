---
solution: Campaign Classic
product: campaign
title: 用例——创建电子邮件投放
description: 创建电子邮件投放用例
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 46aa896929c960abeb501642a5ffbbb56de4802e
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---


# 用例：创建电子邮件投放{#use-case-creating-an-email-delivery}

在此用例中，您将学习使用Adobe Campaign投放(数字内容编辑器)设计电子邮件数字内容编辑器的步骤。

我们的最终目标是使用包含以下内容的个性化模板创建投放:

* 收件人的直接地址（使用第一名和第二名）
* 指向外部URL的两种类型的链接
* 镜像页面
* 指向Web 应用程序的链接

>[!NOTE]
>
>在开始之前，必须至少配置一 **个HTML模板** ，以托管将来投放的内容。
>
>在投放 **[!UICONTROL Properties]**&#x200B;中，确保( **[!UICONTROL Content editing mode]** 在选项卡 **[!UICONTROL Advanced]** 中)设置为 **[!UICONTROL DCE]**。 要确保编辑器的最佳操作，请参阅内容 [编辑最佳实践](../../web/using/content-editing-best-practices.md)。

## 第1步——创建投放 {#step-1---creating-a-delivery}

要创建新投放，请将光标放在“活动” **选项卡** ，然后单击 **投放**。 然后，单击 **现有** 投放列表上方的“创建”按钮。 For more on creating deliveries, refer to [this page](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## 第2步——选择模板 {#step-2---selecting-a-template}

选择投放模板，然后命名投放。 此名称仅对Adobe Campaign控制台的用户可见，而对收件人不可见，但此标题将显示在您的投放列表中。 单击 **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## 第3步——选择内容 {#step-3---selecting-a-content}

该数字内容编辑器附带各种具有不同结构（列、文本区域等）的现成模板。

选择要使用的内容模板，然后单击按 **[!UICONTROL Start with the selected content]** 钮以在创建的投放中显示模板。

![](assets/dce_select_model.png)

还可以通过选择导入在Adobe Campaign之外创建的HTML内容 **[!UICONTROL From a file]**。

![](assets/dce_select_from_file_template.png)

您可以将此内容另存为模板供将来使用。 创建个性化内容模板后，您可以从模板的预览中对其进行列表。 For more on this, refer to [Template management](../../web/using/template-management.md).

>[!CAUTION]
>
>如果您使用的是 **Adobe CampaignWeb界面**，则必须导入一个。zip文件，其中包含HTML内容和相关图像。

## 第4步——设计消息 {#step-4---designing-the-message}

* 显示收件人的名字和姓名

   要将收件人的第一个和第二个名称插入投放的文本字段中，请单击所选文本字段，然后将光标放在要显示它们的位置。 单击弹出工具栏中的第一个图标，然后单击 **[!UICONTROL Personalization block]**。 选择 **[!UICONTROL Greetings]**，然后单击 **[!UICONTROL OK]**。

   ![](assets/dce_personalizationblock_greetings.png)

* 在图像中插入链接

   要通过图像将投放收件人转换为外部地址，请单击相关图像以显示弹出工具栏，将光标放在第一个图标上，然后单击 **[!UICONTROL Link to an external URL]**。 有关此内容的详细信息，请参 [阅添加链接](../../web/using/editing-content.md#adding-a-link)。

   ![](assets/dce_externalpage.png)

   在URL字段中输入链接的 **URL** ，格式 **为** https://www.myURL.com，然后确认。

   可随时使用窗口右侧的部分更改链接。

* 在文本中插入链接

   要将外部链接集成到投放中的文本中，请选择一些文本或文本块，然后单击弹出工具栏中的第一个图标。 单 **[!UICONTROL Link to an external URL]**&#x200B;击，在字段中输入链接 **[!UICONTROL URL]** 地址。 有关此内容的详细信息，请参 [阅添加链接](../../web/using/editing-content.md#adding-a-link)。

   可随时使用窗口右侧的部分更改链接。

   >[!CAUTION]
   >
   >在字段中输入的文 **[!UICONTROL Label]** 本将替换原始文本。

* 添加镜像页面

   要允许收件人在Web浏览器中视图投放内容，您可以将指向镜像页面的链接集成到投放中。

   单击要在其中查看已发布链接的文本字段。 单击弹出工具栏中的第一个图标，然 **[!UICONTROL Personalization block]**&#x200B;后选择 **[!UICONTROL Link to Mirror Page (MirrorPage)]**。 Click **[!UICONTROL Save]** to confirm.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >个性化区块标签会自动替换您投放中的原始文本。

* 将链接集成到Web 应用程序

   数字内容编辑器允许您从Adobe Campaign控制台(如登陆页或表单页面)集成指向Web 应用程序的链接。 有关详细信息，请参 [阅链接到Web 应用程序](../../web/using/editing-content.md#link-to-a-web-application)。

   为指向Web 应用程序的链接选择一个文本字段，然后单击第一个图标。 选 **[!UICONTROL Link to a Web application]**&#x200B;择，然后单击Web 应用程序字段末尾的图标以选择所需的应 **用** 。

   ![](assets/dce_webapp.png)

   单击 **保存** ，以确认。

   >[!NOTE]
   >
   >此步骤要求您至少提前保存一个Web 应用程序。 这些组件可在控制台 **[!UICONTROL Campaigns > Web applications]** 的选项卡中找到。

## 第5步——保存投放 {#step-5---saving-the-delivery}

集成内容后，单击保存以保存 **投放**。 它现在将显示在投放列表中，位于选项卡 **[!UICONTROL Campaigns > Deliveries]** 中。
