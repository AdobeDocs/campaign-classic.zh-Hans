---
title: 关于交易消息传递
seo-title: 关于交易消息传递
description: 关于交易消息传递
seo-description: null
page-status-flag: never-activated
uuid: c854daac-8756-44f3-a4e2-be31177ab9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 97df4bd5-a8e3-48f4-87c8-fa090ea3f771
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 833907c7a7b84b94a00b131738c73ff54a744a40

---


# 关于交易消息传递{#about-transactional-messaging}

交易消息（消息中心）是用于管理触发消息的营销活动模块。 这些消息是从信息系统触发的事件生成的，可以是：例如，发票、订单确认、发运确认、密码更改、产品不可用通知、帐户对帐单或网站帐户创建。

>[!CAUTION]
>
>交易消息传递需要特定的许可证。 请检查您的许可协议。

Adobe Campaign消息中心模块集成到一个信息系统中，该系统会将要更改的事件返回到个性化的交易消息中。 这些消息可以单独发送或通过电子邮件、短信或推送通知批量发送。

在该特定架构中，执行单元与控制实例分开，这确保了更高的可用性和更好的负载管理。

>[!NOTE]
>
>要为Adobe cloud上托管的消息中心执行实例创建新用户，您需要联系Adobe客户关怀。 消息中心用户是特定的运营商，需要专用权限才能访问“实时事件”(nmsRtEvent)文件夹。
