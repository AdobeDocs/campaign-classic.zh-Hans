---
title: 关于Adobe Campaign Classic中的移动应用程序渠道
description: 本节提供Adobe Campaign Classic中特定于移动应用程序渠道的一般信息。
page-status-flag: never-activated
uuid: e8d26b33-dc7c-4abd-956a-92f419a117e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 6b3fe8b9-dae6-4f8e-83e1-3376c0fe72a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c581f22261af7e083f6bd47e603d17d2d71e7ce6

---


# 关于移动应用程序渠道{#about-mobile-app-channel}

>[!CAUTION]
>
>本文档详细介绍了将移动应用程序与Adobe Campaign平台集成的过程。 它不提供有关如何创建移动应用程序或如何配置它以管理通知的信息。 如果您想要进一步了解此信息，请参阅官方的Apple([https://developer.apple.com/](https://developer.apple.com/))和Android([https://developer.android.com/index.html](https://developer.android.com/index.html))文档。

以下部分提供特定于移动应用程序渠道的信息。 有关如何创建交付的全局信息，请参阅[此部分](../../delivery/using/steps-about-delivery-creation-steps.md)。

通过 **移动应用渠道** ，您可以使用Adobe Campaign平台通过应用程序向iOS和Android终端发送个性化通知。 提供两个交付渠道：

* iOS渠道，允许您向Apple移动设备发送通知。

   ![](assets/nmac_intro_2.png)

* 允许您向Android移动设备发送数据消息的Android渠道。

   ![](assets/nmac_intro_1.png)

与这两个渠道相对应，营销活动工作流中有两个交付活动：

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>还有两个事务消息模板可用于事务消息传递。

您可以为用户激活通知以显示与应用程序上下文匹配的屏幕时定义应用程序行为。 例如：

* 客户将收到通知，告知其包裹已退出仓库。 激活通知后，将打开一个页面，其中包含与传送相关的信息。
* 用户已将商品添加到购物车，但未完成购买而离开了应用程序。 系统会发送通知，告知他们已放弃购物车。 当他们激活通知时，该项目会显示在屏幕上。

>[!CAUTION]
>
>* 您需要确保发送到移动应用程序的通知符合Apple（Apple推送通知服务）和Google（Google云消息传递）指定的先决条件和条件。
>* 警告：在某些国家／地区，法律要求您告知用户所收集的数据类型移动应用程序及其处理目的。 你必须检查立法。


(mobileAppOptOutMgt) **[!UICONTROL NMAC opt-out management]** 工作流可更新移动设备上取消订阅的通知。 有关此工作流程的详细信息，请参阅工作 [流指南](../../workflow/using/mobile-app-channel.md)。

Adobe Campaign兼容二进制和HTTP/2 APNS。 有关配置步骤的更多详细信息，请参阅“连接 [器](../../delivery/using/setting-up-mobile-app-channel.md#connectors) ”部分。
