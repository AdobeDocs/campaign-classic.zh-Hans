---
solution: Campaign Classic
product: campaign
title: 同步 Web 应用程序
description: 同步 Web 应用程序
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 1%

---


# 同步 Web 应用程序{#synchronizing-web-applications}

在此用例中，我们将使用Campaign Standard发送通信，其中包括指向活动v7 Web应用程序的链接。 当收件人单击电子邮件中的链接时，Web应用程序会显示一个表单，其中包含预加载了收件人数据的多个字段，以及指向新闻稿的订阅链接。 收件人可以更新其数据并订阅服务。 他的用户档案将在v7活动更新，信息将以Campaign Standard复制。

如果您在v7活动中有许多服务和Web应用程序，您可以选择不在Campaign Standard中重新创建它们。 ACS连接器允许您使用所有现有活动v7 Web应用程序和服务，并将它们链接到Campaign Standard发送的投放。

## 先决条件{#prerequisites}

要实现此目标，您需要：

* 收件人存储在活动v7数据库中并与Campaign Standard同步。 请参阅同 [步用户档案](../../integrations/using/synchronizing-profiles.md) 部分。
* 在v7活动创建和发布的服务和Web应用程序。
* web应用程序必须包含使 **[!UICONTROL Pre-loading]** 用标识方法 **[!UICONTROL Adobe Campaign encryption]** 的活动。

## 创建Web应用程序和服务 {#creating-the-web-application-and-service}

在活动v7中，您可以创建允许收件人订阅服务的Web应用程序。 Web应用程序和服务以活动v7设计并存储，您可以通过Campaign Standard通信更新此服务。 要进一步了解v7活动中的Web应用程序，请参 [阅本节](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)。

在活动v7中，已创建以下对象：

* 新闻稿服务
* 包含、 **[!UICONTROL Pre-loading]**&#x200B;和活动 **[!UICONTROL Page]** 的web应 **[!UICONTROL Storage]** 用程序

1. 转到并 **[!UICONTROL Resources > Online > Web applications]** 选择现有的Web应用程序。

   ![](assets/acs_connect_lp_2.png)

1. 编辑 **[!UICONTROL Preloading]** 活动。 选 **[!UICONTROL Auto-load data referenced in the form]** 中该框并选 **[!UICONTROL Adobe Campaign encryption]** 择识别方法。 这将允许Web应用程序预载表单的字段，其中数据存储在Adobe Campaign库中。 查看 [此文档](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

   ![](assets/acs_connect_lp_4.png)

1. 编辑 **[!UICONTROL Page]**。 已包含三个字段（名称、电子邮件和电话），还包含一个复选框以邀请收件人订阅新闻稿(**[!UICONTROL Newsletter]** 服务)。

   ![](assets/acs_connect_lp_3.png)

1. 转到并 **[!UICONTROL Profiles and Target > Services and subscriptions]** 打开服 **[!UICONTROL Newsletter]** 务。 这是将从Campaign Standard通信更新的服务。 您可以看到收件人尚未订阅此服务。

   ![](assets/acs_connect_lp_5.png)

1. 转到并 **[!UICONTROL Profiles and Targets > Recipient]** 选择一个收件人。 你可以看到他还没有订阅这项服务。

   ![](assets/acs_connect_lp_6.png)

## 复制数据 {#replicating-the-data}

为了在活动v7和Campaign Standard之间复制所需的数据，可以使用多个复制工作流模板。 该工 **[!UICONTROL Profiles replication]** 作流自动将所有活动v7收件人复制到Campaign Standard。 请参 [阅技术和复制工作流](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows)。 该工 **[!UICONTROL Landing pages replication]** 作流支持复制我们希望在Campaign Standard中使用的Web应用程序。

![](assets/acs_connect_lp_1.png)

要检查数据是否已正确复制，请在Campaign Standard中执行以下步骤：

1. 在主屏幕中，单击 **[!UICONTROL Customer profiles]**。

   ![](assets/acs_connect_lp_7.png)

1. 搜索您的活动v7收件人并检查他是否以Campaign Standard显示。

   ![](assets/acs_connect_lp_8.png)

1. 从顶部栏中，单 **[!UICONTROL Marketing activities]**&#x200B;击并搜索活动v7 Web应用程序。 它在Campaign Standard中显示为登陆页。

   ![](assets/acs_connect_lp_9.png)

1. 单击左 **[!UICONTROL Adobe Campaign]** 上角的标志，然后选择 **用户档案和受众>服务** ，并检查新闻稿服务是否也在此处。

   ![](assets/acs_connect_lp_10.png)

## 设计和发送电子邮件 {#designing-and-sending-the-email}

在此部分，我们将了解如何在Campaign Standard电子邮件中包含从活动v7 Web应用程序复制的登陆页的链接。

创建、设计和发送电子邮件的步骤与创建经典电子邮件的步骤相同。 请参阅 [Adobe Campaign Standard](https://helpx.adobe.com/support/campaign/standard.html) 文档。

1. 创建新电子邮件，并选择一个或多个复制用户档案作为受众。
1. 编辑内容并插入 **[!UICONTROL Link to a landing page]**。

   ![](assets/acs_connect_lp_12.png)

1. 选择从活动v7 Web应用程序复制的登陆页。

   ![](assets/acs_connect_lp_13.png)

1. 准备电子邮件、发送验证和发送最终电子邮件。
1. 其中一个收件人会打开电子邮件并单击指向新闻稿订阅的链接。

   ![](assets/acs_connect_lp_14.png)

1. 他添加一个电话号码并检查新闻稿订阅框。

   ![](assets/acs_connect_lp_15.png)

## 检索更新的信息 {#retrieving-the-updated-information}

当收件人通过Web应用程序更新其Adobe Campaign时，v7会同步检索更新的信息。 然后将其从活动v7复制到Campaign Standard。

1. 在活动v7中，转 **[!UICONTROL Profiles and Target > Services and subscriptions]** 到并打开服 **[!UICONTROL Newsletter]** 务。 您可以看到收件人现在显示在订阅者列表中。

   ![](assets/acs_connect_lp_16.png)

1. 转到并 **[!UICONTROL Profiles and Targets > Recipient]** 选择收件人。 您可以看到电话号码已存储。

   ![](assets/acs_connect_lp_17.png)

1. 在选项卡 **[!UICONTROL Subscriptions]** 中，我们还可以看到他订阅了新闻稿服务。

   ![](assets/acs_connect_lp_18.png)

1. 等待几分钟，用户档案复制工作流程才能运行。
1. 在Campaign Standard中，访问收件人用户档案，检查是否已正确从活动v7复制更新的数据。

   ![](assets/acs_connect_lp_19.png)

1. 编辑用户档案。 您可以看到电话号码已更新。

   ![](assets/acs_connect_lp_20.png)

1. Click on the **[!UICONTROL Subscriptions]** tab. 现在会显示新闻稿服务。

   ![](assets/acs_connect_lp_21.png)

