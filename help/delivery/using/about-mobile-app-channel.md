---
title: 关于Adobe Campaign Classic的移动应用渠道
description: 本节提供特定于Adobe Campaign Classic移动应用程序渠道的一般信息。
page-status-flag: never-activated
uuid: e8d26b33-dc7c-4abd-956a-92f419a117e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 6b3fe8b9-dae6-4f8e-83e1-3376c0fe72a5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 1%

---


# 关于移动应用程序渠道{#about-mobile-app-channel}

>[!CAUTION]
>
>此文档详细介绍了将您的移动应用程序与Adobe Campaign平台集成的过程。 它不提供有关如何创建移动应用程序或如何配置它以管理通知的信息。 如果您想要进一步了解此信息，请参阅官方的Apple [文档](https://developer.apple.com/) 和Android [文档](https://developer.android.com/index.html)。

以下各节提供特定于移动应用程序渠道的信息。

有关如何创建投放的全局信息，请参[阅此部分](../../delivery/using/steps-about-delivery-creation-steps.md)。

通过 **移动应用渠道** ，您可以使用Adobe Campaign平台通过应用程序向iOS和Android终端发送个性化通知。 提供两个投放渠道:

* 一种iOS渠道，允许您向Apple移动设备发送通知。

   ![](assets/nmac_intro_2.png)

* 一种Android渠道，允许您向Android移动设备发送数据消息。

   ![](assets/nmac_intro_1.png)

与这两个渠道相对应，在活动工作流中有两个投放活动:

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>还有两个事务性消息模板可用于事务消息传递。

您可以为用户激活通知以显示与应用程序上下文匹配的屏幕时定义应用程序行为。 例如：

* 通知客户其包裹已退出仓库。 激活通知后将打开一个页面，其中包含与投放相关的信息。
* 用户已将项目添加到购物车，但未完成购买而离开了应用程序。 系统会发送通知，告知他们已放弃购物车。 当用户激活通知时，该项目将显示在屏幕上。

>[!CAUTION]
>
>* 您需要确保发送到移动应用程序的通知符合Apple（Apple推送通知服务）和Google(Firebase Cloud Messaging)指定的先决条件和条件。
>* 警告：在某些国家／地区，法律要求您将收集到的数据类型移动应用程序及其处理目的告知用户。 你必须检查立法。


( **[!UICONTROL NMAC opt-out management]** mobileAppOptOutMgt)工作流程可更新移动设备上的通知退订。 For more information on this workflow, refer to the [Workflows guide](../../workflow/using/mobile-app-channel.md).

Adobe Campaign兼容二进制和HTTP/2 APNS。 有关配置步骤的详细信息，请参阅在 [Adobe Campaign中配置移动应用程序](../../delivery/using/configuring-the-mobile-application.md) 。

## 数据路径 {#data-path}

以下模式详细介绍了使移动应用程序能够与Adobe Campaign交换数据的步骤。 此过程涉及三个实体：

* 移动应用程序
* 通知服务：适用于Apple的APNS（Apple推送通知服务）和适用于Android的FCM(Firebase Cloud Messaging)
* Adobe Campaign

通知过程的三个主要步骤是：在Adobe Campaign(订阅收集)、投放和跟踪中注册应用程序。

### 第1步：订阅集合 {#step-1--subscription-collection}

用户从App Store或Google Play下载移动应用程序。 此应用程序包含连接设置（适用于Android的iOS证书和项目密钥）和集成密钥。 首次打开应用程序时（取决于配置），可要求用户输入注册信息(@userKey:电子邮件或帐号)。 同时，应用程序询问通知服务以收集通知ID（推送ID）。 所有这些信息（连接设置、集成密钥、通知标识符、用户密钥）都将发送给Adobe Campaign。

![](assets/nmac_register_view.png)

### 第2步：投放 {#step-2--delivery}

营销人员目标应用程序订阅者。 投放进程将连接设置发送到通知服务（iOS证书和Android项目密钥）、通知ID（推送ID）和通知内容。 通知服务向目标终端发送通知。

Adobe Campaign中提供以下信息：

* 仅限Android:已显示通知的设备数（展示次数）
* Android和iOS:单击通知的次数

![](assets/nmac_delivery_view.png)

Adobe Campaign服务器必须能够通过以下端口与APNS服务器联系：

* 适用于iOS二进制连接器的2195（发送）和2186（反馈服务）
* 443 for iOS HTTP/2连接器

要检查它是否正常工作，请使用以下命令：

* 对于测试：

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* 在生产中：

   ```
   telnet gateway.push.apple.com
   ```

如果使用iOS二进制连接器，则MTA和Web服务器必须能够在端口2195（发送）上与APNS联系，工作流服务器必须能够在端口2196上与APNS联系（反馈服务）。

如果使用iOS HTTP/2连接器，则MTA、Web服务器和工作流服务器必须能够在端口443上与APNS联系。

