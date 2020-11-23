---
solution: Campaign Classic
product: campaign
title: 创建 Facebook 应用程序
description: 创建 Facebook 应用程序
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 1%

---


# 创建 Facebook 应用程序{#creating-a-facebook-application}

得益于Web应用程序，社交营销可让您在Facebook应用程序中显示个性化内容，从而更轻松地通过此社交网络获取潜在客户。 有关Facebook类型Web应用程序的更多示例，请参 [阅Facebook应用程序示例](../../social/using/examples-of-facebook-apps.md)。

>[!NOTE]
>
>还可以将Adobe Campaign与合作伙伴开发的Facebook应用程序集成。 在这种情况下，无需使用Adobe CampaignWeb应用程序来获取Facebook用户档案。 有关此内容的详细信息，请参阅 [配置外部帐户](#configuring-external-accounts)。

![](assets/social_webapp_fb_000.png)

应用以下配置步骤：

1. 创建一个或多个Facebook应用程序。 有关此内容的详细信息，请参阅： [创建Facebook应用程序](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)。
1. 输入要 **[!UICONTROL terms of service]** 在Facebook **[!UICONTROL Privacy policy]** 权限请求屏幕上显示的和链接。 有关此内容的详细信息，请参阅： [输入服务条款和隐私策略链接](#entering-the-terms-of-service-and-privacy-policy-links)。
1. 对于每个Facebook应用程序，创建一个 **[!UICONTROL Facebook Connect]** 类型外部帐户。 有关此内容的详细信息，请参阅： [配置外部帐户](#configuring-external-accounts)。
1. 对于每个Facebook应用程序，在Adobe Campaign中创建Facebook类型的Web应用程序。 有关此内容的详细信息，请参阅： [创建Facebook类型的Web应用程序](#creating-a-facebook-type-web-application)。
1. 配置Facebook应用程序，使其以选项卡的形式显示在Facebook页面上。 有关此内容的详细信息，请参阅： [配置Facebook选项卡](#configuring-facebook-tabs)。

## 配置外部帐户 {#configuring-external-accounts}

对于每个Facebook应用程序，您需要创建一个类 **[!UICONTROL Facebook Connect]** 型外部帐户。

此步骤要求访问您的Adobe Campaign控制台和登录到用于页面管理的Facebook帐户的Internet浏览器：

* **Facebook**:选择之前创建的应用程序( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然后选择 **[!UICONTROL Settings]** >选 **[!UICONTROL Basic]** 项卡。

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Facebook Web Games]** 未显示章节，请单 **[!UICONTROL Add Platform]** 击页面底部的按钮，然后选择 **[!UICONTROL Facebook Web Games]**。

* **Adobe Campaign**:转到树 **[!UICONTROL Administration > Platform > External accounts]** 的节点并单击 **[!UICONTROL New]**。

   ![](assets/social_webapp_fb_005.png)

1. 输入标签和内部名称并选择 **[!UICONTROL Facebook Connect]** 类型。

   ![](assets/social_webapp_fb_006.png)

1. 为应用程序选择托管模式： **[!UICONTROL hosted by a partner]** 或 **[!UICONTROL hosted by this instance]**&#x200B;者

   ![](assets/social_webapp_fb_012.png)

   **由合作伙伴托管的应用程序**

   可以将Adobe Campaign与合作伙伴开发的Facebook应用程序集成。 在这种情况下，无需使用Adobe CampaignWeb应用程序来获取Facebook用户档案。 当Facebook用户安装应用程序时，将生成一个密钥(访问令牌)。 合作伙伴通过调用Web服务将此访问令牌转发给Adobe Campaign。 Adobe Campaign随后使用此令牌登录到Facebook数据库并收集用户通过应用程序共享的数据。

   >[!NOTE]
   >
   >WSDL文件中详细介绍了web服务的参数： **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   要将第三方应用程序集成到Adobe Campaign中，您需要复制和Facebook字段 **[!UICONTROL App ID]** 的 **[!UICONTROL App Secret]** 内容，并将其粘贴到控制台 **[!UICONTROL Application ID]** 的和 **[!UICONTROL Application secret]** 字段中。

   ![](assets/social_facebook_external_account_013.png)

   **由此实例托管的应用程序**

   如果要在此实例上托管应用程序（如果您没有第三方应用程序），则需要使用Adobe CampaignWeb应用程序来获取Facebook用户档案。 有关此内容的详细信息，请参 [阅Facebook应用程序示例](../../social/using/examples-of-facebook-apps.md)。

   在Adobe Campaign控制台中，复制字段中包含的地 **[!UICONTROL Secure Canvas URL]** 址，并将其粘贴 **[!UICONTROL Facebook Web games (https)]** 到Facebook上的字段(在 **[!UICONTROL Facebook Web Games]** 部分)。

   ![](assets/social_facebook_external_account_009.png)

   >[!IMPORTANT]
   >
   >在任何情况下均不得使用不安全的URL。

   在Facebook上，复制和字段的 **[!UICONTROL App ID]** 内 **[!UICONTROL App Secret]** 容并将其粘贴到控制台 **[!UICONTROL Application ID]** 中的和 **[!UICONTROL Application secret]** 字段中。

   ![](assets/social_facebook_external_account_008.png)

1. 在Facebook上，单 **[!UICONTROL Save Changes]** 击页面底部的按钮。
1. 在Adobe Campaign控制台中，单击 **[!UICONTROL Subscribe]** 按钮以启用Adobe Campaign，以在每次风扇通过此应用程序签入时实时恢复数据。 有关此内容的详细信息，请参阅： [Facebook应用程序示例](../../social/using/examples-of-facebook-apps.md)。

   ![](assets/social_webapp_fb_013.png)

## 输入服务条款和隐私策略链接 {#entering-the-terms-of-service-and-privacy-policy-links}

我们强烈建议添加 **[!UICONTROL Terms of service]** 要 **[!UICONTROL Privacy policy]** 在Facebook权限请求屏幕上显示的链接和链接。

![](assets/social_fb_terms_of_services_001.png)

配置阶段如下：

1. 输入以下地址： [https://developers.facebook.com/apps](https://developers.facebook.com/apps)，然后选择Facebook应用程序。
1. 选择选 **[!UICONTROL Settings > Basic]** 项卡并输入 **[!UICONTROL Privacy Policy URL]** 和字 **[!UICONTROL Terms of Service URL]** 段。

   ![](assets/social_fb_terms_of_services.png)

## 创建Facebook类型Web应用程序 {#creating-a-facebook-type-web-application}

Adobe CampaignFacebook应用程序可让您在Facebook应用程序中显示个性化内容。 对于每个Facebook应用程序，您需要创建一个Adobe Campaign的Web应用程序。 要创建Facebook Web应用程序，请按如下步骤继续：

1. 转到宇宙 **[!UICONTROL Social networks]** ，单击链 **[!UICONTROL Applications]** 接，然后单击 **[!UICONTROL Create]** 按钮。

   ![](assets/social_webapp_001.png)

1. 从列表中选择Facebook Web应用程序模板并输入标签。

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >默认情况下提供四个Facebook Web应用程序模板：
   >
   >* **[!UICONTROL New Facebook application]**:如果要从空白应用程序进行开始，请选择此模板。
   >* **[!UICONTROL Pre-entered form]**:Facebook应用程序带有一个表单和一个“Facebook登录”按钮，用户可使用其用户档案中的数据自动填写表单的字段。 这样，用户可以更快地填写表单，使品牌获得更优质的信息。
   >* **[!UICONTROL "Canvas page" competition]**:在屏幕上显示的Facebook应用程序，为用户提供更好的视觉体验。
   >* **[!UICONTROL "Page Tab" competition]**:Facebook应用程序完全集成到品牌页面选项卡中。


1. 在字 **[!UICONTROL Application]** 段中，输入链接到Facebook应用程序的外部帐户。 有关此内容的详细信息，请参阅： [配置外部帐户](#configuring-external-accounts)。

   ![](assets/social_webapp_005.png)

1. 选择选 **[!UICONTROL Edit]** 项卡，然后编辑Web应用程序。 有关此内容的详细信息，请参阅： [Facebook应用程序示例](../../social/using/examples-of-facebook-apps.md)。

   ![](assets/social_webapp_003.png)

1. 完成Web应用程序后，选择选 **[!UICONTROL Dashboard]** 项卡，然后单 **[!UICONTROL Publish]** 击以联机发布。

   ![](assets/social_webapp_004.png)

## 配置Facebook选项卡 {#configuring-facebook-tabs}

您可以配置Facebook应用程序，使其在Facebook页面上显示为选项卡。 为此，请应用以下步骤：

1. 选择Facebook应用程序([https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然后选择选 **[!UICONTROL Settings > Basic]** 项卡。

   ![](assets/social_webapp_fb_008.png)

1. 在页面底部，单击按 **[!UICONTROL Add Platform]** 钮，然后选择 **[!UICONTROL Page Tab]**。

   ![](assets/social_webapp_fb_008bis.png)

1. 在部 **[!UICONTROL Page Tab Name]** 分的字 **[!UICONTROL Page Tab]** 段中，输入您希望该标签显示在Facebook页面上的方式。

   ![](assets/social_webapp_fb_001.png)

1. 在字 **[!UICONTROL Secure Page Tab URL]** 段中，输入Web应用程序的公共URL，可通过Web应用程 **[!UICONTROL Dashboard]** 序的选项卡访问。 有关创建Facebook类型Web应用程序的详细信息，请参 [阅创建Facebook类型Web应用程序](#creating-a-facebook-type-web-application)。

   ![](assets/social_webapp_fb_002.png)

1. 在Web应 **[!UICONTROL Dashboard]** 用程序上，单击链 **[!UICONTROL Add a page tab]** 接。

   ![](assets/social_webapp_fb_0010.png)

1. 选择要将选项卡添加到的Facebook页面，然后单击 **[!UICONTROL Add Page Tab]**。

   ![](assets/social_webapp_fb_0011.png)

