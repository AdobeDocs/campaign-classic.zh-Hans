---
product: campaign
title: 故障排除
description: 故障排除
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 4%

---

# 故障排除{#troubleshooting}

![](../../assets/common.svg)

如果移动设备已连接到Wi-Fi，并且您未收到通知，请检查您的防火墙是否未阻止FCM/APNs端口。

**Android**:移动设备连接到端口5228到5230上的FCM服务器。 因此，必须配置防火墙，以便它授权与FCM的连接。 要打开的端口包括：5228（最常用的）、5229和5230。

**iOS**:

HTTP/2连接器：您必须允许与以下服务器进行通信：

* api.push.apple.com:端口443
* api.development.push.apple.com:端口443

>[!NOTE]
>
>有关两个连接器的详细信息，请参阅 [在Adobe Campaign中配置移动应用程序](configuring-the-mobile-application.md).
