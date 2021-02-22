---
solution: Campaign Classic
product: campaign
title: 关于Adobe Campaign Classic中的移动应用程序渠道
description: 本节提供特定于Adobe Campaign Classic中移动应用程序渠道的一般信息。
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 22f44f5723ab35e95caa438583fe06314c763ba1
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 1%

---


# 关于移动应用程序渠道{#about-mobile-app-channel}

>[!CAUTION]
>
>本文档详细介绍了将您的移动应用程序与Adobe Campaign平台集成的过程。 它不提供有关如何创建移动应用程序或如何配置它以管理通知的信息。 如果您想进一步了解此信息，请参阅官方的Apple [文档](https://developer.apple.com/)和Android [文档](https://developer.android.com/index.html)。

以下部分提供特定于移动应用程序渠道的信息。

有关如何创建投放的全局信息，请参阅[本节](../../delivery/using/steps-about-delivery-creation-steps.md)。

通过&#x200B;**移动应用程序渠道**，您可以使用Adobe Campaign平台通过应用程序向iOS和Android终端发送个性化通知。 有两种投放渠道:

* 一种iOS渠道，可让您向Apple移动设备发送通知。

   ![](assets/nmac_intro_2.png)

* 一种Android渠道，可让您向Android移动设备发送数据消息。

   ![](assets/nmac_intro_1.png)

与这两个渠道相对应，活动工作流中有两个投放活动:

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>还有两个事务性消息模板可用于事务消息传递。

您可以为用户激活通知以显示与应用程序上下文匹配的屏幕时定义应用程序行为。 例如：

* 通知客户其包裹已退仓。 激活通知后，将打开一个页面，其中包含与投放相关的信息。
* 用户已将商品添加到购物车，但未完成购买就离开了应用程序。 系统会发送通知，告诉他们购物车已被放弃。 当用户激活通知时，该项目将显示在屏幕上。

>[!CAUTION]
>
>* 您需要确保发送到移动应用程序的通知符合Apple（Apple推送通知服务）和Google(Firebase Cloud Messaging)指定的先决条件和条件。
>* 警告：在某些国家/地区，法律要求您将收集到的数据类型移动应用程序及其处理目的告知用户。 你必须检查立法。


**[!UICONTROL NMAC opt-out management]**(mobileAppOptOutMgt)工作流更新移动设备上的通知退订。 有关此工作流的详细信息，请参阅技术工作流](../../workflow/using/about-technical-workflows.md)的[列表。

Adobe Campaign与HTTP/2 APN兼容。 有关配置步骤的详细信息，请参阅[在Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md)中配置移动应用程序一节。

## 数据路径{#data-path}

以下模式详细介绍了使移动应用程序能够与Adobe Campaign交换数据的步骤。 此过程涉及三个实体：

* 移动应用程序
* 通知服务：适用于Apple的APNs（Apple推送通知服务）和适用于Android的FCM(Firebase Cloud Messaging)
* Adobe Campaign

通知过程的三个主要步骤是：在Adobe Campaign(订阅收集)、投放和跟踪中注册应用程序。

### 第1步：订阅集合{#step-1--subscription-collection}

用户从App Store或Google Play下载移动应用程序。 此应用程序包含连接设置（适用于Android的iOS证书和项目密钥）和集成密钥。 首次打开应用程序时（取决于配置），可要求用户输入注册信息(@userKey:电子邮件或帐户号)。 同时，应用程序会询问通知服务以收集通知ID（推送ID）。 所有此信息（连接设置、集成密钥、通知标识符、userKey）都将发送到Adobe Campaign。

![](assets/nmac_register_view.png)

### 第2步：投放{#step-2--delivery}

营销人员目标应用程序订阅者。 投放进程将连接设置发送到通知服务（iOS证书和Android项目密钥）、通知ID（推送ID）和通知内容。 通知服务向目标终端发送通知。

以下信息可在Adobe Campaign中使用：

* 仅限Android:显示通知（展示次数）的设备数
* Android和iOS:单击通知的次数

![](assets/nmac_delivery_view.png)

Adobe Campaign服务器必须能够与iOS HTTP/2连接器的443端口上的APNs服务器联系。

要检查其是否正常工作，请使用以下命令：

* 对于测试：

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* 在生产中：

   ```
   telnet gateway.push.apple.com
   ```

使用iOS HTTP/2连接器，MTA、Web服务器和工作流服务器必须能够与端口443上的APN联系。

