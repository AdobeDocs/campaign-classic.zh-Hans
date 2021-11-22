---
product: campaign
title: 用例 — 创建电子邮件投放
description: 创建电子邮件投放用例
audience: web
content-type: reference
topic-tags: editing-html-content
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# 用例：创建电子邮件投放{#use-case-creating-an-email-delivery}

![](../../assets/common.svg)

在此用例中，您将学习使用Adobe Campaign数字内容编辑器(DCE)设计电子邮件投放的步骤。

我们的最终目标是使用包含以下内容的个性化模板创建投放：

* 收件人的直接地址（使用第一个和第二个名称）
* 外部URL的两种链接类型
* 镜像页面
* 指向Web应用程序的链接

>[!NOTE]
>
>在开始之前，您必须至少拥有一个 **HTML模板** 已配置为托管将来投放的内容。
>
>在投放中 **[!UICONTROL Properties]**，请确保 **[!UICONTROL Content editing mode]** (在 **[!UICONTROL Advanced]** 选项卡) **[!UICONTROL DCE]**. 要确保编辑器的最佳操作，请参阅 [内容编辑最佳实践](content-editing-best-practices.md).

## 步骤1 — 创建投放 {#step-1---creating-a-delivery}

要创建新投放，请将光标放在 **促销活动** 选项卡，单击 **投放**. 接下来，单击 **创建** 按钮。 有关创建投放的更多信息，请参阅 [本页](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## 第2步 — 选择模板 {#step-2---selecting-a-template}

选择投放模板，然后命名投放。 此名称仅对Adobe Campaign控制台的用户可见，对收件人则不可见，但此标题将显示在投放列表中。 单击 **[!UICONTROL Continue]**。

![](assets/dce_delivery_model.png)

## 步骤3 — 选择内容 {#step-3---selecting-a-content}

数字内容编辑器附带各种现成的模板，这些模板具有不同的结构（列、文本区域等）。

选择要使用的内容模板，然后单击 **[!UICONTROL Start with the selected content]** 按钮以显示创建投放中的模板。

![](assets/dce_select_model.png)

您还可以通过选择 **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

您可以将此内容另存为模板以供将来使用。 创建个性化内容模板后，即可从模板列表中预览该模板。 有关更多信息，请参阅 [模板管理](template-management.md).

>[!CAUTION]
>
>如果您使用 **Adobe Campaign Web界面**，则必须导入包含HTML内容和相关图像的.zip文件。

## 第4步 — 设计消息 {#step-4---designing-the-message}

* 显示收件人的名字和姓氏

   要将收件人的第一个和第二个名称插入到投放的文本字段中，请单击您选择的文本字段，然后将光标放在要显示它们的位置。 单击弹出工具栏中的第一个图标，然后单击 **[!UICONTROL Personalization block]**. 选择 **[!UICONTROL Greetings]**，然后单击 **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* 在图像中插入链接

   要通过图像将投放收件人定向到外部地址，请单击相关图像以显示弹出工具栏，将光标放在第一个图标上，然后单击 **[!UICONTROL Link to an external URL]**. 有关更多信息，请参阅 [添加链接](editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   在 **URL** 字段 **https://www.myURL.com**，然后确认。

   可以随时使用窗口右侧的部分更改链接。

* 将链接插入文本

   要将外部链接集成到投放中的文本中，请选择一些文本或一个文本块，然后单击弹出工具栏中的第一个图标。 单击 **[!UICONTROL Link to an external URL]**，在 **[!UICONTROL URL]** 字段。 有关更多信息，请参阅 [添加链接](editing-content.md#adding-a-link).

   可以随时使用窗口右侧的部分更改链接。

   >[!CAUTION]
   >
   >在 **[!UICONTROL Label]** 字段替换原始文本。

* 添加镜像页面

   要允许收件人在Web浏览器中查看您的投放内容，您可以将指向镜像页面的链接集成到您的投放中。

   单击您希望在其中看到已发布链接的文本字段。 单击弹出工具栏中的第一个图标，选择 **[!UICONTROL Personalization block]**，则 **[!UICONTROL Link to Mirror Page (MirrorPage)]**. 单击 **[!UICONTROL Save]** 确认。

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >个性化块标签会自动替换投放中的原始文本。

* 集成指向Web应用程序的链接

   使用数字内容编辑器，您可以从Adobe Campaign控制台中集成指向Web应用程序的链接，如登陆页面或表单页面。 有关更多信息，请参阅 [链接到Web应用程序](editing-content.md#link-to-a-web-application).

   为指向Web应用程序的链接选择文本字段，然后单击第一个图标。 选择 **[!UICONTROL Link to a Web application]**，然后单击 **Web应用程序** 字段。

   ![](assets/dce_webapp.png)

   单击 **保存** 确认。

   >[!NOTE]
   >
   >此步骤要求您事先至少保存一个Web应用程序。 这些参数可在 **[!UICONTROL Campaigns > Web applications]** 选项卡。

## 步骤5 — 保存投放 {#step-5---saving-the-delivery}

集成内容后，单击 **保存**. 现在，它将显示在投放列表中(位于 **[!UICONTROL Campaigns > Deliveries]** 选项卡。
