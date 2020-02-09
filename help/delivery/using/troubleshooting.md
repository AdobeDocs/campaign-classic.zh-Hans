---
title: 故障排除
seo-title: 故障排除
description: 故障排除
seo-description: null
page-status-flag: never-activated
uuid: 02bd48cf-3928-4817-97b0-1e64cc8ad8ef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: b64c9729-cfe2-4d02-8c59-9e53efd34a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 故障排除{#troubleshooting}

如果移动设备已连接到Wi-Fi且您未收到通知，请检查FCM/APNS端口是否未被防火墙阻止。

**Android**:移动设备连接到端口5228到5230上的FCM服务器。 因此，必须配置防火墙，以便它授权与FCM连接。 要打开的端口包括：5228（最常用的）、5229和5230。

**iOS**:

二进制连接器：要发送通知，必须对端口2195上的入站和出站TCP通信进行授权。 连接到推送服务的设备必须授权端口5223上的入站和出站TCP通信。

HTTP/2连接器：您必须允许与以下服务器进行通信：

* api.push.apple.com:端口443
* api.development.push.apple.com:端口443

>[!NOTE]
>
>有关两个连接器的详细信息，请参阅 [连接器](../../delivery/using/setting-up-mobile-app-channel.md#connectors)。
