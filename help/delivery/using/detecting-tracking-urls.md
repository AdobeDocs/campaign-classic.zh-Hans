---
product: campaign
title: 检测跟踪URL
description: 详细了解推荐的跟踪URL模式
feature: Monitoring
role: User, Developer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
TQID: 'https://experienceleague.adobe.com/F63e0G1uyp-tXDiBk9cau5P-HBHttCkiFD2yw657RBw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 3%
---
# 检测跟踪 URL

Adobe Campaign会在投放分析期间检测要跟踪内容的URL。

作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解如何检测URL以及要使用哪些模式，请参阅[Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}

## 不安全的模式

向内容添加个性化链接时，请始终避免在URL的主机名部分进行任何个性化设置，以避免潜在的安全缺口。 请参阅[此页面](../../installation/using/privacy.md#url-personalization)以了解详情。

例如，`<a href="http://<%=myURL%>">`语法是&#x200B;**不安全的**，必须避免。

* 如果Adobe Campaign生成的链接包含一个或多个参数，则使用此语法可能会导致安全问题。
* Tidy可能会错误地修补某些链接，这可能会随机发生。 典型症状是一段HTML，可在电子邮件验证中看到，但在预览中不可见。
* URL的转义存在问题，URL中的某些字符可能会导致问题。
* 名为ID的参数不能与重定向URL中的参数冲突。
* 然后，跟踪兴趣仅限于投放统计信息，因为Adobe Campaign会以不一样的方式跟踪“myURL”的所有可能值。
