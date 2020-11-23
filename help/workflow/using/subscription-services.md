---
solution: Campaign Classic
product: campaign
title: 订阅服务
description: 进一步了解订阅服务工作流活动
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---


# 订阅服务{#subscription-services}

订阅服务 **类**&#x200B;型活动允许您为过渡中指定的人口创建或删除信息服务订阅。

要进行配置，请编辑活动并输入其标签，然后选择要执行的操作(订阅或退订)以及相关服务，如以下示例所示：

![](assets/edit_service_inscription.png)

1. 输入活动的标签。
1. 如 **[!UICONTROL Generate an outbound transition]** 果要在执行结束时创建过渡，请选择。

   通常，目标对信息服务的订阅标记定位工作流的结束，这就是默认情况下未激活该选项的原因。

1. 单 **[!UICONTROL Subscription]** 击或 **[!UICONTROL Unsubscription]** 者，如果要订阅或取消订阅指定的人口，或者退订选定的信息服务。
1. 选 **[!UICONTROL Send a confirmation message]** 择以通知收件人已订阅或从服务取消订阅。

   此消息的内容在与投放模板相关的信息服务中指定。 有关更多信息，请参阅此](../../delivery/using/managing-subscriptions.md)章节[。

## 示例：订阅列表收件人新闻稿 {#example--subscribe-a-list-of-recipients-to-a-newsletter}

在单个操作中，以下工作流旨在使列表收件人有资格获得新闻稿，该新闻稿旨在让居住在巴黎的工作人员订阅。

为此，还必须排除已订阅的收件人。

>[!CAUTION]
>
>在手动订阅收件人到服务之前，请验证这些收件人是否接受您的通信。

![](assets/subscription_services_example.png)

1. 添加以下三个查询:

   * 一个针对18到60岁收件人。
   * 第二个目标是住在巴黎的收件人。
   * 当前未订阅新闻稿的第三个定位收件人。

1. 添加交叉活动以交叉引用不同的结果。
1. 如果您喜欢，请插入列表更新以使最新订阅者的列表保持最新。
1. 插入订阅服务活动，然后多次单击此选项进行配置。
1. 输入活动标签并选择 **[!UICONTROL Subscription]**。

   如果您愿意，可以通过选中该框通知收件人其新闻稿订阅 **[!UICONTROL Send a confirmation message]** 情况。

1. 选择新闻稿所在的文件夹，然后从显示的列表中选择新闻稿。
1. 保持未选 **[!UICONTROL Generate outbound transition]** 中状态，以便此活动将标记工作流的结尾，然后单击 **[!UICONTROL Ok]**。

在工作流执行过程中，与所有三个查询对应的收件人会添加到列表并订阅新闻稿。

您可以转到订阅的选项卡，检查 **[!UICONTROL Subscription]** 收件人是否成功。

## 输入参数 {#input-parameters}

* tableName
* 模式

每个入站事件必须指定由这些参数定义的目标。
