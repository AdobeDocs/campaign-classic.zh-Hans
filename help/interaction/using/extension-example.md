---
product: campaign
title: 扩展示例
description: 扩展示例
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 07a5742c6f142c786ad8ba2f8774e7e90e8cd191
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# 扩展示例{#extension-example}

![](../../assets/common.svg)

对于集客联系人（呼叫中心或网站），使用一组资格规则向给定联系人建议最相关的选件。 要扩充优惠的资格标准，请将 **nms:interaction** 架构。

* 要添加新的交互上下文，请扩展 **nms:interaction** 架构和创建尽可能多的 **属性** 元素（根据需要）。

   在以下示例中，添加的标准是国家/地区代码和上次访问的页面。

   ![](assets/s_ncs_configuration_offer_schemas.png)

* 然后，您可以使用之前在定义资格标准定义时创建的属性。

   在以下示例中，我们可以创建资格标准，以根据用户的国家/地区或他们查看的最后一个网页来显示选件。

   ![](assets/s_ncs_configuration_offer_context.png)

* 配置SOAP调用时，插入 **上下文** 用于引用在交互架构中添加的上下文信息的XML元素。 有关详细信息，请参阅 [通过SOAP（服务器端）进行集成](../../interaction/using/integration-via-soap--server-side-.md).
