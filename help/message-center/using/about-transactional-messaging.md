---
title: 关于事务型消息传递
description: '根据从信息系统生成的事件发送触发消息。 '
page-status-flag: never-activated
uuid: c854daac-8756-44f3-a4e2-be31177ab9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 97df4bd5-a8e3-48f4-87c8-fa090ea3f771
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# 关于事务型消息传递{#about-transactional-messaging}

事务消息（消息中心）是用于管理触发消息的活动模块。 这些消息是从信息系统触发的事件生成的，可以是：例如，发票、订单确认、发运确认、密码更改、产品不可用性通知、帐户对帐单或网站帐户创建。

>[!IMPORTANT]
>
>交易消息传递需要特定许可证。 请检查您的许可协议。

Adobe Campaign消息中心模块被集成到一个信息系统中，该系统将要更改的事件返回到个性化事务性消息。 这些消息可以单独发送，也可以通过电子邮件、短信或推送通知分批发送。

在此特定架构中，执行单元与控制实例分离，这确保更高的可用性和更好的负载管理。

>[!NOTE]
>
>要为托管在Adobe云上的消息中心执行实例创建新用户，您需要联系Adobe客户服务。 消息中心用户是需要专用权限才能访问“实时事件”(nmsRtEvent)文件夹的特定操作员。
