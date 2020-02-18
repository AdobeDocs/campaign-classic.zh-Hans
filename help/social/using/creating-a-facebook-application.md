---
title: 创建Facebook应用程序
seo-title: 创建Facebook应用程序
description: 创建Facebook应用程序
seo-description: null
page-status-flag: never-activated
uuid: f02129b9-6f64-41ee-8b56-d85211a58f69
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: c1d880bb-256e-451c-8c52-198711907f8e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# 创建Facebook应用程序{#creating-a-facebook-application}

借助Web应用程序，社交营销可让您在Facebook应用程序中显示个性化内容，从而更轻松地通过此社交网络获取潜在客户。 有关Facebook类型Web应用程序的更多示例，请参 [阅Facebook应用程序示例](../../social/using/examples-of-facebook-apps.md)。

>[!NOTE]
>
>还可以将Adobe Campaign与合作伙伴开发的Facebook应用程序集成。 在这种情况下，无需使用Adobe Campaign web应用程序获取Facebook配置文件。 有关详细信息，请参阅配 [置外部帐户](#configuring-external-accounts)。

![](assets/social_webapp_fb_000.png)

应用以下配置步骤：

1. 创建一个或多个Facebook应用程序。 有关详细信息，请参阅：创 [建Facebook应用程序](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)。
1. 输入要 **[!UICONTROL terms of service]** 在Facebook权 **[!UICONTROL Privacy policy]** 限请求屏幕上显示的和链接。 有关详细信息，请参阅：输 [入服务条款和隐私策略链接](#entering-the-terms-of-service-and-privacy-policy-links)。
1. 对于每个Facebook应用程序，创建一个类 **[!UICONTROL Facebook Connect]** 型外部帐户。 有关详细信息，请参阅：配 [置外部帐户](#configuring-external-accounts)。
1. 对于每个Facebook应用程序，在Adobe Campaign中创建一个Facebook类型的Web应用程序。 有关详细信息，请参阅：创 [建Facebook类型Web应用程序](#creating-a-facebook-type-web-application)。
1. 配置Facebook应用程序，使其以选项卡的形式显示在您的Facebook页面上。 有关详细信息，请参阅：配 [置Facebook选项卡](#configuring-facebook-tabs)。

## 配置外部帐户 {#configuring-external-accounts}

对于每个Facebook应用程序，您需要创建一个类 **[!UICONTROL Facebook Connect]** 型外部帐户。

此步骤需要访问您的Adobe Campaign控制台和登录到您用于页面管理的Facebook帐户的因特网浏览器：

* **Facebook**:选择之前创建的应用程序( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然后选择 **[!UICONTROL Settings]** >选项 **[!UICONTROL Basic]** 卡。

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Facebook Web Games]** 未显示该部分，请单 **[!UICONTROL Add Platform]** 击页面底部的按钮，然后选择 **[!UICONTROL Facebook Web Games]**。

* **Adobe Campaign**:转到树 **[!UICONTROL Administration > Platform > External accounts]** 的节点并单击 **[!UICONTROL New]**。

   ![](assets/social_webapp_fb_005.png)

1. 输入标签和内部名称，然后选择类 **[!UICONTROL Facebook Connect]** 型。

   ![](assets/social_webapp_fb_006.png)

1. 为应用程序选择托管模式：或 **[!UICONTROL hosted by a partner]** 者 **[!UICONTROL hosted by this instance]**。

   ![](assets/social_webapp_fb_012.png)

   **由合作伙伴托管的应用程序**

   可以将Adobe Campaign与合作伙伴开发的Facebook应用程序集成。 在这种情况下，无需使用Adobe Campaign web应用程序获取Facebook配置文件。 当Facebook用户安装应用程序时，将生成密钥（访问令牌）。 合作伙伴通过调用Web服务将此访问令牌转发到Adobe Campaign。 然后，Adobe Campaign使用此令牌登录到Facebook数据库并收集用户通过应用程序共享的数据。

   >[!NOTE]
   >
   >Web服务的参数在以下WSDL文件中详细介绍： **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   要将第三方应用程序集成到Adobe Campaign中，您需要复制和 **[!UICONTROL App ID]****[!UICONTROL App Secret]** Facebook字段的内容，并将其粘贴到控制台的 **[!UICONTROL Application ID]** 和 **[!UICONTROL Application secret]** 字段中。

   ![](assets/social_facebook_external_account_013.png)

   **由此实例托管的应用程序**

   如果要在此实例上托管应用程序（如果您没有第三方应用程序），则需要使用Adobe Campaign web应用程序来获取Facebook配置文件。 有关详细信息，请参阅Facebook [应用程序示例](../../social/using/examples-of-facebook-apps.md)。

   在Adobe Campaign控制台中，复制字段中包含的地 **[!UICONTROL Secure Canvas URL]** 址，并将其粘贴到Facebook上的 **[!UICONTROL Facebook Web games (https)]** 字段(在部分 **[!UICONTROL Facebook Web Games]** 中)。

   ![](assets/social_facebook_external_account_009.png)

   >[!IMPORTANT]
   >
   >在任何情况下均不得使用不安全的URL。

   在Facebook上，复制和字段的内 **[!UICONTROL App ID]** 容并 **[!UICONTROL App Secret]** 将其粘贴到控制台 **[!UICONTROL Application ID]** 中的和 **[!UICONTROL Application secret]** 字段中。

   ![](assets/social_facebook_external_account_008.png)

1. 在Facebook上，单 **[!UICONTROL Save Changes]** 击页面底部的按钮。
1. 在Adobe Campaign控制台中，单击 **[!UICONTROL Subscribe]** 按钮以启用Adobe Campaign以在粉丝每次通过此应用程序签入时实时恢复数据。 有关详细信息，请参阅：Facebook [应用程序示例](../../social/using/examples-of-facebook-apps.md)。

   ![](assets/social_webapp_fb_013.png)

## 输入服务条款和隐私策略链接 {#entering-the-terms-of-service-and-privacy-policy-links}

我们强烈建议添加 **[!UICONTROL Terms of service]** 要在 **[!UICONTROL Privacy policy]** Facebook权限请求屏幕上显示的和链接。

![](assets/social_fb_terms_of_services_001.png)

配置阶段如下：

1. 输入以下地址： [https://developers.facebook.com/apps](https://developers.facebook.com/apps)，然后选择Facebook应用程序。
1. 选择选 **[!UICONTROL Settings > Basic]** 项卡并输入 **[!UICONTROL Privacy Policy URL]** 和字 **[!UICONTROL Terms of Service URL]** 段。

   ![](assets/social_fb_terms_of_services.png)

## 创建Facebook类型Web应用程序 {#creating-a-facebook-type-web-application}

通过Adobe Campaign facebook应用程序，您可以在Facebook应用程序中显示个性化内容。 对于每个Facebook应用程序，您需要在Adobe Campaign中创建Web应用程序。 要创建Facebook web应用程序，请按如下步骤继续：

1. 转到宇宙 **[!UICONTROL Social networks]** ，单击链接， **[!UICONTROL Applications]** 然后单击按 **[!UICONTROL Create]** 钮。

   ![](assets/social_webapp_001.png)

1. 从列表中选择一个Facebook web应用程序模板并输入标签。

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >默认情况下，提供四个Facebook web应用程序模板：
   >
   >* **[!UICONTROL New Facebook application]**:如果要从空白应用程序开始，请选择此模板。
   >* **[!UICONTROL Pre-entered form]**:Facebook应用程序带有一个表单和一个“Facebook登录”按钮，用户可以使用个人资料中的数据自动填写表单的字段。 这使用户能够更快地完成表单，并使品牌获得更优质的信息。
   >* **[!UICONTROL "Canvas page" competition]**:屏幕上显示的Facebook应用程序，为用户提供更好的视觉体验。
   >* **[!UICONTROL "Page Tab" competition]**:Facebook应用程序完全集成到品牌页面选项卡中。


1. 在字段 **[!UICONTROL Application]** 中，输入链接到Facebook应用程序的外部帐户。 有关详细信息，请参阅：配 [置外部帐户](#configuring-external-accounts)。

   ![](assets/social_webapp_005.png)

1. 选择选 **[!UICONTROL Edit]** 项卡，然后编辑Web应用程序。 有关详细信息，请参阅：Facebook [应用程序示例](../../social/using/examples-of-facebook-apps.md)。

   ![](assets/social_webapp_003.png)

1. Web应用程序完成后，选择该选 **[!UICONTROL Dashboard]** 项卡，然后单击 **[!UICONTROL Publish]** 以联机发布。

   ![](assets/social_webapp_004.png)

## 配置Facebook选项卡 {#configuring-facebook-tabs}

您可以配置Facebook应用程序，使其在您的Facebook页面上显示为选项卡。 为此，请应用以下步骤：

1. 选择Facebook应用程序([https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然后选择选 **[!UICONTROL Settings > Basic]** 项卡。

   ![](assets/social_webapp_fb_008.png)

1. 在页面底部，单击按 **[!UICONTROL Add Platform]** 钮，然后选择 **[!UICONTROL Page Tab]**。

   ![](assets/social_webapp_fb_008bis.png)

1. 在部 **[!UICONTROL Page Tab Name]** 分的字 **[!UICONTROL Page Tab]** 段中，输入您希望该标签显示在Facebook页面上的标签。

   ![](assets/social_webapp_fb_001.png)

1. 在字 **[!UICONTROL Secure Page Tab URL]** 段中，输入Web应用程序的公共URL，可通过Web应用程序的选 **[!UICONTROL Dashboard]** 项卡访问该URL。 有关创建Facebook类型Web应用程序的详细信息，请参 [阅创建Facebook类型Web应用程序](#creating-a-facebook-type-web-application)。

   ![](assets/social_webapp_fb_002.png)

1. 在Web应 **[!UICONTROL Dashboard]** 用程序上，单击该链 **[!UICONTROL Add a page tab]** 接。

   ![](assets/social_webapp_fb_0010.png)

1. 选择要添加选项卡的Facebook页面，然后单击 **[!UICONTROL Add Page Tab]**。

   ![](assets/social_webapp_fb_0011.png)

