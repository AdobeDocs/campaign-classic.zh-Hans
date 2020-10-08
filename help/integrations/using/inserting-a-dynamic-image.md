---
title: 插入动态图像
seo-title: 插入动态图像
description: 插入动态图像
seo-description: null
page-status-flag: never-activated
uuid: 4acc905e-625c-45aa-bb70-7dde22911aa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: f6e4d22b-4ad3-4a1e-8a6f-3bdfc1da0535
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 3%

---


# 插入目标动态内容 {#inserting-a-dynamic-image}

在本指南中，我们将介绍如何将动态优惠从目标整合到Adobe Campaign电子邮件中。

我们希望创建一个投放，其中包含一个图像块，该图像块会根据收件人所在的国家／地区动态更改。 数据随每个mbox请求一起发送，并取决于访客的IP地址。

在此电子邮件中，我们希望其中一幅图像根据以下用户体验动态变化：

* 电子邮件在法国打开。
* 电子邮件在美国打开。
* 如果这些条件均不适用，则显示默认图像。

![](assets/target_4.png)

要使此功能正常工作，我们需要在Adobe Campaign和目标中执行以下步骤：

1. [在电子邮件中插入动态优惠](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [创建重定向优惠](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [创建受众](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [创建体验定位活动](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [预览和发送电子邮件](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## 在电子邮件中插入动态优惠 {#inserting-dynamic-offer}

在Adobe Campaign中，定义完电子邮件的目标和内容后，即可插入来自目标的动态图像。

为此，请指定默认图像的URL、位置名称以及要传输到目标的字段。

在Adobe Campaign中，有两种方法可将动态图像从目标插入电子邮件：

* 如果您使用的是数字内容编辑器，请选择现有图像，然后从工 **[!UICONTROL Insert]** 具栏 **[!UICONTROL Dynamic image served by Adobe Target]** 中选择>。

   ![](assets/target_5.png)

* 如果您使用的是标准编辑器，请将光标放在要插入图像的位置，并从个 **[!UICONTROL Include]** 性 **[!UICONTROL Dynamic image served by Adobe Target...]** 化下拉菜单中选择>。

   ![](assets/target_12.png)

### 定义图像参数 {#defining-image-parameters}

* **[!UICONTROL Default image]** URL:当未满足任何条件时将显示的图像。 您还可以从资产库中选择图像。
* 以下 **[!UICONTROL Target location]**&#x200B;项：输入动态优惠位置的名称。 您必须在目标活动中选择此位置。
* 以下 **[!UICONTROL Landing Page]**&#x200B;项：如果希望默认图像重定向到默认登陆页。 此URL仅适用于在最终电子邮件中显示默认图像且是可选的情况。
* 以下 **[!UICONTROL Additional decision parameters]**&#x200B;项：指定在Adobe Target区段中定义的字段与Adobe Campaign字段之间的映射。 使用的Adobe Campaign字段必须已在rawbox中指定。 在我们的示例中，我们添加了“国家”字段。

如果您在Adobe Target的设置中使用“企业”权限，请在此字段中添加相应的属性。 在本页中进一步了解目标 [企业权限](https://docs.adobe.com/content/help/en/target/using/administer/manage-users/enterprise/properties-overview.html)。

![](assets/target_13.png)

## 创建重定向优惠 {#create-redirect-offers}

在目标中，您可以创建不同版本的优惠。 根据每个用户体验，可以创建重定向优惠，并指定将显示的图像。

在我们的情况下，我们需要两个重定向优惠，第三个重定向Adobe Campaign（默认的）将在中定义。

1. 要在Target Standard中创建新的重定向优惠，请在选项 **[!UICONTROL Content]** 卡中单击 **[!UICONTROL Code offers]**。

1. 单击 **[!UICONTROL Create]**，然后单击 **[!UICONTROL Redirect Offer]**。

   ![](assets/target_9.png)

1. 输入优惠的名称和图像的URL。

   ![](assets/target_6.png)

1. 对于剩余的重定向优惠，请按照相同的过程操作。 有关详细信息，请参见此 [ 页面](https://docs.adobe.com/help/en/target/using/experiences/offers/offer-redirect.html)。

## 创建受众 {#audiences-target}

在目标中，您需要创建两个受众，访问您优惠的人员将根据要交付的不同内容进行分类。 对于每个受众，添加一个规则以定义谁将能够查看优惠。

1. 要在目标中创建新受众，请在选项卡 **[!UICONTROL Audiences]** 中单击 **[!UICONTROL Create Audience]**。

   ![](assets/audiences_1.png)

1. 为受众添加名称。

   ![](assets/audiences_2.png)

1. 单击 **[!UICONTROL Add a rule]** 并选择类别。 规则使用特定条件目标访客。 您可以通过添加条件或在其他类别创建新规则来优化规则。

1. 对其余受众按照相同的过程操作。

## 创建体验定位活动 {#creating-targeting-activity}

在目标中，我们需要创建体验定位活动，定义不同的体验，并将它们与相应的优惠关联。

### 定义受众 {#defining-the-audience}

1. 要创建体验定位活动，请在选项卡 **[!UICONTROL Activities]** 中单击，然 **[!UICONTROL Create Activity]** 后单 **[!UICONTROL Experience Targeting]**&#x200B;击。

   ![](assets/target_10.png)

1. 选择 **[!UICONTROL Form]** 为 **[!UICONTROL Experience Composer]**。

1. 通过单击按钮选择 **[!UICONTROL Change audience]** 受众。

   ![](assets/target_10_2.png)

1. 选择在前面的步骤中创建的受众。

   ![](assets/target_10_3.png)

1. 通过单击创建其他体验 **[!UICONTROL Add Experience Targeting]**。

### 定义位置和内容 {#defining-location-content}

为每个受众添加内容：

1. 选择在Adobe Campaign中插入动态优惠时选择的位置名称。

   ![](assets/target_15.png)

1. 单击下拉按钮并选择 **[!UICONTROL Change Redirect Offer]**。

   ![](assets/target_content.png)

1. 选择您之前创建的重定向优惠。

   ![](assets/target_content_2.png)

1. 按照相同步骤进行第二次体验。

### 定义活动 {#defining-activity}

该窗 **[!UICONTROL Target]** 口汇总您的活动。 如有必要，您可以添加其他体验。

![](assets/target_experience.png)

窗口 **[!UICONTROL Goal & Settings]** 允许您通过设置优先级、目标或持续时间来个性化您的活动。

通过 **[!UICONTROL Reporting Settings]** 此部分，您可以选择一个操作并编辑将决定何时实现目标的参数。

![](assets/target_experience_2.png)

## 以Campaign Classic预览和发送电子邮件 {#preview-send-email}

在Adobe Campaign中，您现在可以预览电子邮件并在不同的收件人上测试其呈现效果。 您会注意到图像会根据创建的不同体验而发生变化。 To learn more on email creation, refer to this [page](../../delivery/using/defining-the-email-content.md).

您现在可以发送电子邮件，包括来自目标的动态优惠。

![](assets/target_20.png)
