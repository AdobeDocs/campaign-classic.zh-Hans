---
title: 配置IMS
seo-title: 配置IMS
description: 配置IMS
seo-description: null
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0a4272ae13b469c7c17b8c3afa9748cbfbcf07ff

---


# 配置IMS{#configuring-ims}

## 先决条件 {#prerequisites}

要使用与IMS的集成，请执行以下操作：

* 您必须拥有Adobe Experience Cloud组织和IMS ID（在您首次连接到Adobe Experience Cloud时提供）。
* 您必须在Experience Cloud中添加用户。 有关详细信息，请参见[此页面](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)。

>[!NOTE]
>
>确保您的用户已链接到将与Adobe Campaign同步的Adobe Experience Cloud组。 请参阅 [配置外部帐户](#configuring-the-external-account)。

## 更新控制台 {#updating-the-console}

要使用此功能，必须安装最新版本的控制台。

## 安装包 {#installing-the-package}

必须安装该 **[!UICONTROL Integration with the Adobe Experience Cloud]** 包。 安装集成包与安装标准包相同，本页详细介绍了 [这一点](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/ims_6.png)

## 配置外部帐户 {#configuring-the-external-account}

在中配 **置Adobe Experience Cloud** 外部帐户 **[!UICONTROL Administration > Platform > External accounts]**。

>[!CAUTION]
>
>此配置为技术管理员保留。

![](assets/ims_5.png)

输入以下信息：

* 使用的IMS服务器的连接信息（ID和机密）。 此信息由Adobe支持提供。 有关详细信息，请参阅Adobe Experience Cloud管 [理员常见问题解答](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html)。

   必须 **[!UICONTROL Callback server]** 在https中指定地 **址**。 此字段与您的Adobe Campaign实例的访问URL相对应。

* IMS组织ID:此信息可在Experience Cloud(在中 **[!UICONTROL Administration > Experience Cloud Details]** )上获取，并在您首次连接到Adobe Experience Cloud时提供。
* 关联蒙版：此字段允许您定义语法，该语法将允许企业仪表板中的配置名称与Adobe Campaign中的组同步。 如果使用语法“活动- tenant_id -(.*)”，则在Adobe Campaign中创建的安全组将链接到企业仪表板中的配置名称“活动- tenant_id - internal_name”。

   >[!CAUTION]
   >
   >关联蒙版是通过Adobe ID进行连接的必备选项，以便正常工作。

* Adobe Experience Cloud连接信息，特别是Adobe Experience Cloud租户的名称。

