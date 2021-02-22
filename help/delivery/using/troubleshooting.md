---
solution: Campaign Classic
product: campaign
title: 故障排除
description: 故障排除
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 22f44f5723ab35e95caa438583fe06314c763ba1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 4%

---


# 故障排除{#troubleshooting}

如果您的移动设备已连接到Wi-Fi且您未收到通知，请检查您的防火墙是否未阻止FCM/APNs端口。

**Android**:移动设备连接到端口5228到5230上的FCM服务器。因此，您必须配置防火墙，以便它授权与FCM的连接。 要打开的端口有：5228（最常用的）、5229和5230。

**iOS**:

HTTP/2连接器：您必须允许与以下服务器进行通信：

* api.push.apple.com:端口443
* api.development.push.apple.com:端口443

>[!NOTE]
>
>有关两个连接器的详细信息，请参阅[在Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md)中配置移动应用程序。
