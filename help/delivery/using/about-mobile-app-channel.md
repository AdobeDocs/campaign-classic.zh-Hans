---
product: campaign
title: '移动应用程序渠道入门 '
description: 移动应用程序渠道快速入门，Adobe Campaign Classic
feature: Push
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---

# 移动应用程序渠道入门{#about-mobile-app-channel}

![](../../assets/common.svg)

的 **移动设备应用程序渠道** 允许您使用Adobe Campaign平台通过应用程序向iOS和Android终端发送个性化推送通知。

>[!CAUTION]
>
>本文档详细介绍了将移动应用程序与Adobe Campaign平台集成的过程。 它不提供有关如何创建移动设备应用程序或如何配置移动设备应用程序以管理通知的信息。 如果您想进一步了解此信息，请参阅官方的Apple [文档](https://developer.apple.com/) 和Android [文档](https://developer.android.com/index.html).

提供了两个投放渠道：

* 一种iOS渠道，用于向Apple移动设备发送通知。

   ![](assets/nmac_intro_2.png)

* 一种Android渠道，可让您向Android移动设备发送数据消息。

   ![](assets/nmac_intro_1.png)

营销活动工作流中有两个投放活动，对应于这两个渠道：

![](assets/nmac_intro_3.png)


>[!NOTE]
>
>事务型消息模板还可用于事务型消息传递。

当用户激活通知以显示与应用程序上下文匹配的屏幕时，您可以定义应用程序行为。 例如：

* 系统会向客户发送通知，告知其包裹已退出仓库。 激活通知会打开一个页面，其中包含与投放相关的信息。
* 用户已将项目添加到购物车，但未完成购买就离开了应用程序。 系统会发送通知，告知他们购物车已被放弃。 激活通知时，屏幕上会显示项目。

>[!CAUTION]
>
>* 您需要确保发送到移动应用程序的通知符合Apple(Apple推送通知服务)和Google(Firebase Cloud Messaging)指定的先决条件和条件。
>* 警告：在某些国家/地区，法律要求您将收集的数据类型移动设备应用程序及其处理目的告知用户。 你必须检查立法。


的 **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt)工作流在移动设备上更新通知取消订阅。 有关此工作流的更多信息，请参阅 [技术工作流列表](../../workflow/using/about-technical-workflows.md).

Adobe Campaign与HTTP/2 APNs兼容。 有关配置步骤的更多详细信息，请参阅 [此部分](configuring-the-mobile-application.md) 中。

有关如何创建投放的全局信息，请参阅 [此部分](steps-about-delivery-creation-steps.md).

## 数据路径 {#data-path}

以下架构详细介绍了使移动应用程序能够与Adobe Campaign交换数据的步骤。 此过程涉及三个实体：

* 移动应用程序
* 通知服务：适用于Apple的APNs(Apple推送通知服务)和适用于Android的FCM(Firebase Cloud Messaging)
* Adobe Campaign

通知流程的三个主要步骤是：在Adobe Campaign中注册应用程序（订阅收集）、投放和跟踪。

### 步骤1:订阅集合 {#step-1--subscription-collection}

用户从App Store或Google Play下载移动应用程序。 此应用程序包含连接设置(适用于Android的iOS证书和项目密钥)和集成密钥。 首次打开应用程序时（取决于配置），系统会要求用户输入注册信息(@userKey:电子邮件或帐号)。 同时，应用程序向通知服务提出问题以收集通知ID（推送ID）。 所有这些信息（连接设置、集成密钥、通知标识符、userKey）都将发送到Adobe Campaign。

![](assets/nmac_register_view.png)

### 步骤2:投放 {#step-2--delivery}

营销人员定位应用程序订阅者。 投放过程会将连接设置发送到通知服务(适用于Android的iOS证书和项目密钥)、通知ID（推送ID）和通知内容。 通知服务向目标终端发送通知。

以下信息可在Adobe Campaign中获取：

* 仅限Android:显示通知（展示次数）的设备数量
* Android和iOS:通知的点击次数

![](assets/nmac_delivery_view.png)

Adobe Campaign服务器必须能够在iOS HTTP/2连接器的443端口上联系APNs服务器。

要检查它是否正常工作，请使用以下命令：

* 对于测试：

   ```
   api.development.push.apple.com:443
   ```

* 在生产中：

   ```
   api.push.apple.com:443
   ```

使用iOS HTTP/2连接器，MTA和Web服务器必须能够在端口443上联系APN。

如果需要通过代理使用iOS HTTP/2连接器，请参阅 [页面](../../installation/using/file-res-management.md#proxy-connection-configuration).
