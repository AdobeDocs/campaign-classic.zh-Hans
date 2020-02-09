---
title: “用例：创建电子邮件发送”
seo-title: “用例：创建电子邮件发送”
description: “用例：创建电子邮件发送”
seo-description: null
page-status-flag: never-activated
uuid: 7cd6329c-63d5-4cf0-9451-f0b4c2eaf0dd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 4ec34980-62a2-47b9-b103-de4290925624
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# 用例：创建电子邮件发送{#use-case-creating-an-email-delivery}

在此用例中，您将学习使用Adobe Campaign数字内容编辑器(DCE)设计电子邮件发送的步骤。

我们的最终目标是创建包含以下内容的个性化模板的交付内容：

* 收件人的直接地址（使用第一名和第二名）
* 指向外部URL的两种类型的链接
* 镜像页面
* 指向Web应用程序的链接

>[!NOTE]
>
>在开始之前，您必须至少配置一个 **HTML模板** ，以托管将来的分发内容。
>
>在传送 **[!UICONTROL Properties]** 中，确保(在 **[!UICONTROL Content editing mode]** 选项卡 **[!UICONTROL Advanced]** 中)设置为 **[!UICONTROL DCE]**。 要确保编辑器的最佳操作，请参阅内容编 [辑最佳实践](../../web/using/content-editing-best-practices.md)。

## 第1步——创建分发 {#step-1---creating-a-delivery}

要创建新分发，请将光标放在“营销活动”选 **项卡中** ，然后单击 **分发**。 然后，单击 **现有** “提交”列表上方的“创建”按钮。 For more on creating deliveries, refer to [this page](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## 第2步——选择模板 {#step-2---selecting-a-template}

选择传送模板，然后命名传送。 此名称仅对Adobe Campaign控制台的用户可见，而不对收件人可见，但此标题将显示在您的分发列表中。 单击 **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## 第3步——选择内容 {#step-3---selecting-a-content}

数字内容编辑器附带各种现成模板，这些模板具有不同的结构（列、文本区域等）。

选择要使用的内容模板，然后单击按 **[!UICONTROL Start with the selected content]** 钮以在创建的分发中显示模板。

![](assets/dce_select_model.png)

您还可以通过选择来导入在Adobe Campaign之外创建的HTML内容 **[!UICONTROL From a file]**。

![](assets/dce_select_from_file_template.png)

您可以将此内容另存为模板以供将来使用。 创建个性化内容模板后，您便可以从模板列表中预览它。 For more on this, refer to [Template management](../../web/using/template-management.md).

>[!CAUTION]
>
>如果您使用 **Adobe Campaign web界面**，则必须导入包含HTML内容和相关图像的。zip文件。

## 第4步——设计消息 {#step-4---designing-the-message}

* 显示收件人的名字和姓名

   要将收件人的第一名和第二名插入分发中的文本字段中，请单击您选择的文本字段，然后将光标放在要显示它们的位置。 单击弹出工具栏中的第一个图标，然后单击 **[!UICONTROL Personalization block]**。 选择 **[!UICONTROL Greetings]**，然后单击 **[!UICONTROL OK]**。

   ![](assets/dce_personalizationblock_greetings.png)

* 在图像中插入链接

   要将传送收件人通过图像转至外部地址，请单击相关图像以显示弹出工具栏，将光标放在第一个图标上，然后单击 **[!UICONTROL Link to an external URL]**。 有关详细信息，请参阅 [添加链接](../../web/using/editing-content.md#adding-a-link)。

   ![](assets/dce_externalpage.png)

   在 **URL字段中输入链接的URL** ，格式为 **https://www.myURL.com**，然后确认。

   可随时使用窗口右侧的部分更改链接。

* 在文本中插入链接

   要将外部链接集成到交付中的文本中，请选择一些文本或文本块，然后单击弹出工具栏中的第一个图标。 单 **[!UICONTROL Link to an external URL]**&#x200B;击，在字段中输入链接 **[!UICONTROL URL]** 地址。 有关详细信息，请参阅 [添加链接](../../web/using/editing-content.md#adding-a-link)。

   可随时使用窗口右侧的部分更改链接。

   >[!CAUTION]
   >
   >在字段中输入的文 **[!UICONTROL Label]** 本将替换原始文本。

* 添加镜像页面

   要允许收件人在Web浏览器中查看您的分发内容，您可以将指向镜像页面的链接集成到您的分发中。

   单击要在其中查看已发布链接的文本字段。 单击弹出工具栏中的第一个图标，选择， **[!UICONTROL Personalization block]**&#x200B;然后选择 **[!UICONTROL Link to Mirror Page (MirrorPage)]**。 Click **[!UICONTROL Save]** to confirm.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >个性化区块标签会自动替换交付中的原始文本。

* 集成指向Web应用程序的链接

   通过数字内容编辑器，您可以集成Adobe Campaign控制台（如登录页面或表单页面）中指向Web应用程序的链接。 有关详细信息，请参 [阅链接到Web应用程序](../../web/using/editing-content.md#link-to-a-web-application)。

   为指向Web应用程序的链接选择一个文本字段，然后单击第一个图标。 选 **[!UICONTROL Link to a Web application]**&#x200B;择，然后单击“Web应用程序”字段末尾的图标以选择所需 **的应用程序** 。

   ![](assets/dce_webapp.png)

   单击 **保存** ，以确认。

   >[!NOTE]
   >
   >此步骤要求您至少提前保存一个Web应用程序。 这些组件位于控制台 **[!UICONTROL Campaigns > Web applications]** 的选项卡中。

## 第5步——保存交付 {#step-5---saving-the-delivery}

集成内容后，单击保存以保存交 **付**。 它现在将显示在您的分发列表中，该列表位于选项卡 **[!UICONTROL Campaigns > Deliveries]** 中。
