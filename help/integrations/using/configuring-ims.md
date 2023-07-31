---
product: campaign
title: 配置IMS
description: 了解如何通过Adobe ID连接
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 5%

---

# 配置IMS{#configuring-ims}



>[!IMPORTANT]
>
>Adobe IMS实施严格保留给Adobe技术管理员。 请联系您的Adobe执行官，以开始实施流程。

## 先决条件 {#prerequisites}

要与IMS集成，请执行以下操作：

* 您必须具有Adobe Experience Cloud组织名称和ID。 要查找您的组织ID，请参阅 [此页面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hans){_blank}.
* 您必须在Experience Cloud中添加用户。 有关详细信息，请参见 [此页面](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>确保您的用户已链接到将与Adobe Campaign同步的Adobe Experience Cloud组。 [了解详情](#configuring-the-external-account)。

## 更新控制台 {#updating-the-console}

要使用此功能，必须安装最新版本的控制台。

## 安装包 {#installing-the-package}

您必须安装内置 **[!UICONTROL Integration with the Adobe Experience Cloud]** 包。 安装集成包与安装标准包相同，具体详见 [此页面](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## 配置外部帐户 {#configuring-the-external-account}

配置 **Adobe Experience Cloud** 外部帐户位于 **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>此配置是技术管理员保留的。

![](assets/ims_5.png)

输入以下信息：

* 使用的IMS服务器的连接信息（ID和密码）。 此信息由Adobe支持提供。 欲了解更多信息，请参见 [Adobe Experience Cloud管理员常见问题解答](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

  此 **[!UICONTROL Callback server]** 地址必须指定于 **https**. 此字段对应于Adobe Campaign实例的访问URL。

* 组织ID：要查找您的组织ID，请参阅 [此页面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hans){_blank}.
* 关联掩码：此字段允许您定义语法，以允许将Enterprise Dashboard中的配置名称与Adobe Campaign中的组同步。 如果您使用语法“Campaign - tenant_id - (.&#42;)”，则在Adobe Campaign中创建的安全组将链接到Enterprise Dashboard中的配置名称“Campaign - tenant_id - internal_name”。

  >[!CAUTION]
  >
  >关联掩码对于通过Adobe ID进行的连接正常运行至关重要。

* Adobe Experience Cloud连接信息，特别是Adobe Experience Cloud租户的名称。
