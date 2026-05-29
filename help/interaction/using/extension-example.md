---
product: campaign
title: 扩展示例
description: 扩展示例
feature: Interaction, Offers
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
TQID: https://experienceleague.adobe.com/TQZaYrJop03HAw47XPFqgmoxb073iC-xztTp-f-5dEk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2:
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 160
ht-degree: 3%

---

# 扩展示例{#extension-example}



对于入站联系人（呼叫中心或网站），可使用一组资格规则向给定联系人建议最相关的选件。 要扩充优惠的资格标准，请扩展&#x200B;**nms:interaction**&#x200B;架构。

* 要添加新交互上下文，请扩展&#x200B;**nms:interaction**&#x200B;架构并在该架构中创建所需数量的&#x200B;**attribute**&#x200B;元素。

  在以下示例中，添加的标准是国家/地区代码和上次访问的页面。

  ![](assets/s_ncs_configuration_offer_schemas.png)

* 然后，您可以在定义资格标准定义时使用之前创建的属性。

  在以下示例中，我们可以创建资格标准，以根据用户所在的国家/地区或他们查看的上一个网页来显示选件。

  ![](assets/s_ncs_configuration_offer_context.png)

* 配置SOAP调用时，插入&#x200B;**上下文** XML元素以引用在交互架构中添加的上下文信息。 有关详细信息，请参阅[通过SOAP集成（服务器端）](../../interaction/using/integration-via-soap-server-side.md)。
