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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 扩展示例{#extension-example}

如果是入站联系人（呼叫中心或网站），则使用一组资格规则向给定联系人建议最相关的优惠。 要丰富选件的资格标准，请扩展 **nms:interaction** 架构。

* 要添加新的交互上下文，请扩展 **nms:interaction** schema，并在 **schema中创建所需数量的属性元素** 。

   在以下示例中，添加的条件是国家／地区代码和上次访问的页面。

   ![](assets/s_ncs_configuration_offer_schemas.png)

* 然后，您可以使用之前在定义资格条件定义时创建的属性。

   在以下示例中，我们可以创建资格标准，以根据用户所在的国家／地区或他们查看的最后一个网页显示选件。

   ![](assets/s_ncs_configuration_offer_context.png)

* 配置SOAP调用时，插入 **context** XML元素以引用在交互架构中添加的上下文信息。 有关详细信息，请参 [阅通过SOAP进行集成（服务器端）](../../interaction/using/integration-via-soap--server-side-.md)。

