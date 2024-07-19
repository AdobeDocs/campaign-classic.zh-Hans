---
product: campaign
title: 用例 — 创建电子邮件投放
description: 用例 — 创建电子邮件投放
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# 用例：创建电子邮件投放{#use-case-creating-an-email-delivery}



在此使用案例中，您将了解使用Adobe Campaign数字内容编辑器(DCE)设计电子邮件投放的步骤。

我们的最终目标是使用个性化模板创建投放，该模板包含：

* 收件人的直接地址（使用第一和第二名称）
* 外部URL的两种链接类型
* 镜像页面
* 指向Web应用程序的链接

>[!NOTE]
>
>在开始之前，您必须至少配置一个&#x200B;**HTML模板**&#x200B;来承载未来投放的内容。
>
>在投放&#x200B;**[!UICONTROL Properties]**&#x200B;中，确保&#x200B;**[!UICONTROL Content editing mode]**（在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中）设置为&#x200B;**[!UICONTROL DCE]**。 要确保编辑器的最佳操作，请参阅[内容编辑最佳实践](content-editing-best-practices.md)。

## 步骤1 — 创建投放 {#step-1---creating-a-delivery}

要创建新投放，请将光标置于&#x200B;**促销活动**&#x200B;选项卡中，然后单击&#x200B;**投放**。 接下来，单击现有投放列表上方的&#x200B;**创建**&#x200B;按钮。 有关创建投放的详细信息，请参阅[此页面](../../delivery/using/about-email-channel.md)。

![](assets/delivery_step_1.png)

## 第2步 — 选择模板 {#step-2---selecting-a-template}

选择投放模板，然后命名您的投放。 此名称仅对Adobe Campaign控制台的用户可见，收件人不可见，不过此标题将显示在投放列表中。 单击 **[!UICONTROL Continue]**。

![](assets/dce_delivery_model.png)

## 步骤3 — 选择内容 {#step-3---selecting-a-content}

数字内容编辑器附带各种现成的模板，这些模板具有不同的结构（列、文本区域等）。

选择要使用的内容模板，然后单击&#x200B;**[!UICONTROL Start with the selected content]**&#x200B;按钮以在创建的投放中显示模板。

![](assets/dce_select_model.png)

您还可以通过选择&#x200B;**[!UICONTROL From a file]**&#x200B;导入在Adobe Campaign之外创建的HTML内容。

![](assets/dce_select_from_file_template.png)

您可以将此内容另存为模板，以供将来使用。 创建个性化内容模板后，您可以从模板列表中预览该模板。 有关详细信息，请参阅[模板管理](template-management.md)。

>[!CAUTION]
>
>如果您使用的是&#x200B;**Adobe Campaign Web界面**，则必须导入包含HTML内容和相关图像的.zip文件。

## 第4步 — 设计报文 {#step-4---designing-the-message}

* 显示收件人的名字和第二个名字

  要将收件人的名字和第二个名字插入到投放的文本字段中，请单击您选择的文本字段，然后将光标放在要显示它们的位置。 单击弹出式工具栏中的第一个图标，然后单击&#x200B;**[!UICONTROL Personalization block]**。 选择&#x200B;**[!UICONTROL Greetings]**，然后单击&#x200B;**[!UICONTROL OK]**。

  ![](assets/dce_personalizationblock_greetings.png)

* 将链接插入图像

  若要通过图像将投放收件人转至外部地址，请单击相关图像以显示弹出工具栏，将光标放在第一个图标上，然后单击&#x200B;**[!UICONTROL Link to an external URL]**。 有关详情，请参阅[添加链接](editing-content.md#adding-a-link)。

  ![](assets/dce_externalpage.png)

  使用以下格式&#x200B;**https://www.myURL.com**&#x200B;在&#x200B;**URL**&#x200B;字段中输入链接的URL，然后确认。

  可以随时使用窗口右侧的部分更改链接。

* 在文本中插入链接

  要将外部链接集成到投放的文本中，请选择一些文本或文本块，然后单击弹出工具栏中的第一个图标。 单击&#x200B;**[!UICONTROL Link to an external URL]**，在&#x200B;**[!UICONTROL URL]**&#x200B;字段中输入链接地址。 有关详情，请参阅[添加链接](editing-content.md#adding-a-link)。

  可以随时使用窗口右侧的部分更改链接。

  >[!CAUTION]
  >
  >在&#x200B;**[!UICONTROL Label]**&#x200B;字段中输入的文本将替换原始文本。

* 添加镜像页面

  要允许收件人在Web浏览器中查看投放内容，您可以将指向镜像页面的链接集成到投放中。

  单击您希望在其中发布链接的文本字段。 单击弹出式工具栏中的第一个图标，选择&#x200B;**[!UICONTROL Personalization block]**，然后选择&#x200B;**[!UICONTROL Link to Mirror Page (MirrorPage)]**。 单击 **[!UICONTROL Save]** 确认。

  ![](assets/dce_mirrorpage.png)

  >[!CAUTION]
  >
  >个性化块标签会自动替换投放中的原始文本。

* 将链接集成到Web应用程序

  数字内容编辑器允许您从Adobe Campaign控制台集成指向Web应用程序的链接，如登陆页或表单页。 有关详细信息，请参阅[链接到Web应用程序](editing-content.md#link-to-a-web-application)。

  为指向Web应用程序的链接选择一个文本字段，然后单击第一个图标。 选择&#x200B;**[!UICONTROL Link to a Web application]**，然后单击&#x200B;**Web应用程序**&#x200B;字段末尾的图标以选择所需的应用程序。

  ![](assets/dce_webapp.png)

  单击&#x200B;**保存**&#x200B;确认。

  >[!NOTE]
  >
  >此步骤要求您事先至少保存一个Web应用程序。 可在控制台的&#x200B;**[!UICONTROL Campaigns > Web applications]**&#x200B;选项卡中找到这些页面。

## 步骤5 — 保存投放 {#step-5---saving-the-delivery}

集成内容后，单击&#x200B;**保存**&#x200B;以保存投放。 它现在将显示在&#x200B;**[!UICONTROL Campaigns > Deliveries]**&#x200B;选项卡中的投放列表中。
