---
product: campaign
title: 推送疑难解答
description: 推送疑难解答
feature: Push, Troubleshooting
role: User
hide: true
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
TQID: 'https://experienceleague.adobe.com/3T6eC52Edyai-8Bn-ioDxvB5C04iDqBNmlZzuxVturE'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: a4657621-810c-498b-8a27-7ced9c176dda
    internal-label: Push notifications
  - id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875f
    internal-label: Troubleshooting
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%
---
# 故障排除{#troubleshooting}

如果移动设备已连接到Wi-Fi并且未收到通知，请检查防火墙是否未阻止FCM/APNs端口。

**Android**：移动设备连接到端口5228到5230上的FCM服务器。 因此，必须配置防火墙以授权与FCM的连接。 要打开的端口为：5228（最常用）、5229和5230。

**iOS**：

HTTP/2连接器：必须允许与以下服务器之间的通信：

* api.push.apple.com：端口443
* api.development.push.apple.com：端口443

>[!NOTE]
>
>有关这两个连接器的更多信息，请参阅[在Adobe Campaign中配置移动应用程序](configuring-the-mobile-application.md)。
