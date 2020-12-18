---
solution: Campaign Classic
product: campaign
title: 扩展示例
description: 扩展示例
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# 扩展示例{#extension-example}

在入站联系人（呼叫中心或网站）的情况下，使用一组优惠向给定联系人建议最相关的合格规则。 要丰富您的优惠的资格标准，请扩展&#x200B;**nms:interaction**&#x200B;模式。

* 要添加新的交互上下文，请扩展&#x200B;**nms:interaction**&#x200B;模式，并在模式中创建所需数量的&#x200B;**属性**&#x200B;元素。

   在以下示例中，添加的条件是国家／地区代码和上次访问的页面。

   ![](assets/s_ncs_configuration_offer_schemas.png)

* 然后，您可以使用之前在定义资格条件定义时创建的属性。

   在以下示例中，我们可以创建资格标准，根据用户所在的国家／地区或他们查看的最后一个网页显示优惠。

   ![](assets/s_ncs_configuration_offer_context.png)

* 配置SOAP调用时，插入&#x200B;**context** XML元素以引用在交互模式中添加的上下文信息。 有关详细信息，请参阅[通过SOAP进行集成（服务器端）](../../interaction/using/integration-via-soap--server-side-.md)。

