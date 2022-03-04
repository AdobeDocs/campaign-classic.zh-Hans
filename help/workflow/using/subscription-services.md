---
product: campaign
title: 订阅服务
description: 了解有关订阅服务工作流活动的更多信息
feature: Workflows, Targeting Activity, Subscription Services Activity
exl-id: 1b526d1c-4a33-45a1-98f4-dcb803c8d228
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# 订阅服务{#subscription-services}

![](../../assets/common.svg)

A **订阅服务**-type活动允许您为过渡中指定的群体创建或删除信息服务订阅。

要配置活动，请编辑活动并输入其标签，然后选择要执行的操作（订阅或退订）和相关服务，如以下示例所示：

![](assets/edit_service_inscription.png)

1. 输入活动的标签。
1. 选择 **[!UICONTROL Generate an outbound transition]** 如果希望在执行结束时创建过渡。

   通常，Target对信息服务的订阅会标记定位工作流的结尾，这也是默认情况下未激活选项的原因。

1. 单击 **[!UICONTROL Subscription]** 或 **[!UICONTROL Unsubscription]** 如果您希望订阅或退订选定信息服务的指定群体，则。
1. 选择 **[!UICONTROL Send a confirmation message]** 通知收件人他们已订阅或退订了服务。

   该消息的内容在与信息服务相关的投放模板中指定。 有关更多信息，请参阅此](../../delivery/using/managing-subscriptions.md)章节[。

## 示例：订阅新闻稿的收件人列表 {#example--subscribe-a-list-of-recipients-to-a-newsletter}

在单个操作中，以下工作流旨在为符合新闻通讯条件的收件人列表，这些收件人面向居住在巴黎的工作人员，以便让他们订阅。

要实现此目的，还必须排除已订阅的收件人。

>[!CAUTION]
>
>在手动为收件人订阅服务之前，请确认这些收件人接受您的通信。

![](assets/subscription_services_example.png)

1. 添加以下三个查询：

   * 1个针对18至60岁的收件人。
   * 第二个目标是住在巴黎的收件人。
   * 第三个定向收件人，当前未订阅新闻稿。

1. 添加交集活动以交叉引用不同的结果。
1. 如果需要，请插入列表更新以保持最新订阅者列表为最新。
1. 插入订阅服务活动，然后双击该活动以对其进行配置。
1. 输入活动标签并选择 **[!UICONTROL Subscription]**.

   如果需要，可通过选中 **[!UICONTROL Send a confirmation message]** 框中。

1. 选择新闻稿所在的文件夹，然后从显示的列表中选择新闻稿。
1. 离开 **[!UICONTROL Generate outbound transition]** 取消选中，以便此活动将标记工作流的结尾，然后单击 **[!UICONTROL Ok]**.

在工作流执行期间，与所有三个查询对应的收件人将添加到列表并订阅新闻稿。

您可以转到 **[!UICONTROL Subscription]** 选项卡。

## 输入参数 {#input-parameters}

* tableName
* 模式

每个集客事件必须指定由这些参数定义的目标。
