---
product: campaign
title: 扩展示例
description: 扩展示例
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 4%

---

# 扩展示例{#extension-example}



对于入站联系人（呼叫中心或网站），可使用一组资格规则向给定联系人建议最相关的选件。 要丰富优惠的资格标准，请扩展 **nms：interaction** 架构。

* 要添加新交互上下文，请扩展 **nms：interaction** 架构并创建尽可能多的 **属性** 架构中所需的元素。

  在以下示例中，添加的标准是国家/地区代码和上次访问的页面。

  ![](assets/s_ncs_configuration_offer_schemas.png)

* 然后，您可以在定义资格标准定义时使用之前创建的属性。

  在以下示例中，我们可以创建资格标准，以根据用户所在的国家/地区或他们查看的上一个网页来显示选件。

  ![](assets/s_ncs_configuration_offer_context.png)

* 配置SOAP调用时，插入 **上下文** 用于引用在交互架构中添加的上下文信息的XML元素。 欲知更多信息，请参见 [通过SOAP（服务器端）进行集成](../../interaction/using/integration-via-soap--server-side-.md).
