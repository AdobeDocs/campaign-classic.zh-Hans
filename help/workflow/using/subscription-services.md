---
product: campaign
title: 订阅服务
description: 了解有关订阅服务工作流活动的更多信息
feature: Workflows, Targeting Activity, Subscription Services Activity
hide: true
hidefromtoc: true
exl-id: 1b526d1c-4a33-45a1-98f4-dcb803c8d228
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 3%

---

# 订阅服务{#subscription-services}



**订阅服务**&#x200B;类型活动允许您为过渡中指定的群体创建或删除对信息服务的订阅。

要对其进行配置，请编辑活动并输入其标签，然后选择要执行的操作（订阅或退订）以及相关的服务，如以下示例所示：

![](assets/edit_service_inscription.png)

1. 输入活动的标签。
1. 如果希望在执行结束时创建过渡，请选择&#x200B;**[!UICONTROL Generate an outbound transition]**。

   通常，目标对信息服务的订阅会标记定位工作流的结尾，这也是默认情况下不激活该选项的原因。

1. 如果要订阅或取消订阅选定信息服务的指定群体，请单击&#x200B;**[!UICONTROL Subscription]**&#x200B;或&#x200B;**[!UICONTROL Unsubscription]**。
1. 选择&#x200B;**[!UICONTROL Send a confirmation message]**&#x200B;以通知收件人已订阅或取消订阅服务。

   在与信息服务相关的投放模板中指定此消息的内容。 有关更多信息，请参阅此[&#128279;](../../delivery/using/managing-subscriptions.md)章节。

## 示例：为新闻稿订阅收件人列表 {#example--subscribe-a-list-of-recipients-to-a-newsletter}

在一次操作中，以下工作流旨在列出符合新闻通讯条件的收件人列表，以居住在巴黎的工人为目标，以便让他们订阅。

要实现此目的，还必须排除已订阅的收件人。

>[!CAUTION]
>
>在手动为收件人订阅服务之前，请验证这些收件人是否接受来自您的通信。

![](assets/subscription_services_example.png)

1. 添加以下三个查询：

   * 一个对象是18至60岁的收件人。
   * 第二个目标是居住在巴黎的收件人。
   * 第三个定向是当前未订阅新闻稿的收件人。

1. 添加交叉引用不同结果的交叉点活动。
1. 如果需要，可插入列表更新，以使最新订阅者的列表保持最新。
1. 插入订阅服务活动，然后双击此项进行配置。
1. 输入活动标签并选择&#x200B;**[!UICONTROL Subscription]**。

   如果您愿意，可以通过选中&#x200B;**[!UICONTROL Send a confirmation message]**&#x200B;框将订阅的新闻稿通知收件人。

1. 选择新闻稿所在的文件夹，然后从显示的列表中选择新闻稿。
1. 取消选中&#x200B;**[!UICONTROL Generate outbound transition]**，以便此活动将标记工作流结尾，然后单击&#x200B;**[!UICONTROL Ok]**。

在执行工作流期间，与所有三个查询相对应的收件人将添加到列表并订阅新闻稿。

您可以通过转到收件人的&#x200B;**[!UICONTROL Subscription]**&#x200B;选项卡来检查订阅是否成功。

## 输入参数 {#input-parameters}

* 表名
* 架构

每个入站事件必须指定由这些参数定义的目标。
