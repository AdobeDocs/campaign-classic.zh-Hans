---
title: 扩展示例
seo-title: 扩展示例
description: 扩展示例
seo-description: null
page-status-flag: never-activated
uuid: 6703b6e8-4eac-4a94-a80a-a7cd71b25cdf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 990b6cbc-9b7b-4278-a635-653d5abafe87
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 5%

---


# 扩展示例{#extension-example}

在入站联系人（呼叫中心或网站）的情况下，使用一组优惠向给定联系人建议最相关的合格规则。 要丰富优惠的资格标准，请扩展 **nms:interaction** 模式。

* 要添加新的交互上下文，请扩 **展nms:interaction** 模式，并在 **模式中创建所需** 数量的属性元素。

   在以下示例中，添加的条件是国家／地区代码和上次访问的页面。

   ![](assets/s_ncs_configuration_offer_schemas.png)

* 然后，您可以使用之前在定义资格条件定义时创建的属性。

   在以下示例中，我们可以创建资格标准，根据用户所在的国家／地区或他们查看的最后一个网页显示优惠。

   ![](assets/s_ncs_configuration_offer_context.png)

* 配置SOAP调用时，插入 **上下文** XML元素以引用在交互模式中添加的上下文信息。 有关详细信息，请参 [阅通过SOAP进行集成（服务器端）](../../interaction/using/integration-via-soap--server-side-.md)。

