---
product: campaign
title: 推送疑难解答
description: 推送疑难解答
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
feature: Push, Troubleshooting
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 2%

---

# 故障排除{#troubleshooting}



如果移动设备已连接到Wi-Fi并且未收到通知，请检查防火墙是否未阻止FCM/APNs端口。

**Android**：移动设备连接到端口5228到5230上的FCM服务器。 因此，必须配置防火墙以授权与FCM的连接。 要打开的端口为：5228（最常用）、5229和5230。

**iOS**:

HTTP/2连接器：必须允许与以下服务器之间的通信：

* api.push.apple.com：端口443
* api.development.push.apple.com：端口443

>[!NOTE]
>
>有关两个连接器的详细信息，请参阅 [在Adobe Campaign中配置移动应用程序](configuring-the-mobile-application.md).
