---
title: 订阅服务
seo-title: 订阅服务
description: 订阅服务
seo-description: null
page-status-flag: never-activated
uuid: f8c05f8a-0791-4294-8aa3-69b7325e4d43
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 940bec7e-e3f0-4251-b7fe-72bf188743a7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 订阅服务{#subscription-services}

订阅 **服务类型**，允许您为过渡中指定的人群创建或删除信息服务的订阅。

要配置活动，请编辑活动并输入其标签，然后选择要执行的操作（订阅或取消订阅）和相关服务，如下例所示：

![](assets/edit_service_inscription.png)

1. 输入活动的标签。
1. 如果 **[!UICONTROL Generate an outbound transition]** 您希望在执行结束时创建过渡，请选择此选项。

   通常，目标对信息服务的订阅会标记定位工作流的结束，这就是默认情况下未激活此选项的原因。

1. 单 **[!UICONTROL Subscription]** 击或 **[!UICONTROL Unsubscription]** 者，如果您希望将指定人群订阅或取消订阅选定的信息服务。
1. 选择 **[!UICONTROL Send a confirmation message]** 以通知收件人他们已订阅或从服务中取消订阅。

   该消息的内容在与信息服务相关的分发模板中指定。 For more on this, refer to this [section](../../delivery/using/managing-subscriptions.md).

## 示例：将收件人列表订阅到新闻稿 {#example--subscribe-a-list-of-recipients-to-a-newsletter}

在单个操作中，以下工作流旨在列出有资格获得新闻稿的收件人列表，这些收件人面向居住在巴黎的工作人员，以便让他们订阅。

为此，您还必须排除已订阅的收件人。

>[!CAUTION]
>
>在手动将收件人订阅到服务之前，请验证这些收件人是否接受接收您发送的通信。

![](assets/subscription_services_example.png)

1. 添加以下三个查询：

   * 1个针对18到60岁的收件人。
   * 第二个目标是住在巴黎的收件人。
   * 当前未订阅新闻稿的第三个定位收件人。

1. 添加交叉活动以交叉引用不同的结果。
1. 如果需要，插入列表更新以使最新订阅者列表保持最新。
1. 插入订阅服务活动，然后双击此活动进行配置。
1. 输入活动标签并选择 **[!UICONTROL Subscription]**。

   如果需要，可选中该框以通知收件人订阅新闻稿 **[!UICONTROL Send a confirmation message]** 。

1. 选择新闻稿所在的文件夹，然后从显示的列表中选择新闻稿。
1. 保持未选 **[!UICONTROL Generate outbound transition]** 中状态，这样此活动将标记工作流的结束，然后单击 **[!UICONTROL Ok]**。

在工作流执行过程中，与所有三个查询相对应的收件人将添加到列表中并订阅新闻稿。

您可以转到收件人的选项卡来检查订 **[!UICONTROL Subscription]** 阅是否成功。

## 输入参数 {#input-parameters}

* tableName
* 架构

每个入站事件都必须指定由这些参数定义的目标。
