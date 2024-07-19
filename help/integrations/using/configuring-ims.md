---
product: campaign
title: 配置IMS
description: 了解如何通过Adobe ID连接
feature: Configuration
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---

# 配置IMS{#configuring-ims}

>[!IMPORTANT]
>
>作为Campaign托管或托管服务用户，您的Adobe IMS实施归Adobe所有。 下面描述的步骤仅适用于内部部署和混合型客户。
> Adobe IMS实施必须仅由Adobe技术管理员执行。 请联系您的Adobe代表以开始实施流程。

## 先决条件 {#prerequisites}

* 您必须具有Adobe Experience Cloud组织名称和ID。 要查找您的组织ID，请参阅[此页面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hans){_blank}。
* 您必须在Experience Cloud中添加用户。 有关详细信息，请参阅[此页面](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}。

>[!NOTE]
>
>确保您的用户已链接到将与Adobe Campaign同步的Adobe Experience Cloud组。 [了解详情](#configuring-the-external-account)。

## 更新控制台 {#updating-the-console}

要使用此功能，必须安装最新版本的客户端控制台。

## 安装包 {#installing-the-package}

您必须安装内置&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;包。 安装集成包与安装标准包相同，[此页面](../../installation/using/installing-campaign-standard-packages.md)中对此进行了详细介绍。

![](assets/ims_6.png)

## 配置外部帐户 {#configuring-the-external-account}

在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中配置&#x200B;**Adobe Experience Cloud**&#x200B;外部帐户。

![](assets/ims_5.png)

输入以下信息：

* 使用的IMS服务器的连接信息（ID和密码）。 此信息由Adobe客户关怀团队提供。 有关详细信息，请参阅[Adobe Experience Cloud管理员常见问题解答](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html)。

  必须在&#x200B;**https**&#x200B;中指定&#x200B;**[!UICONTROL Callback server]**&#x200B;地址。 此字段对应于Adobe Campaign实例的访问URL。

* 组织ID：要查找您的组织ID，请参阅[此页面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hans){_blank}。

* 关联掩码：此字段允许您定义语法，以允许将Enterprise Dashboard中的配置名称与Adobe Campaign中的组同步。 如果您使用语法“Campaign - tenant_id - (.&#42;)”，则在Adobe Campaign中创建的安全组将链接到Enterprise Dashboard中的配置名称“Campaign - tenant_id - internal_name”。

* Adobe Experience Cloud连接信息，即Adobe Experience Cloud租户的名称。
