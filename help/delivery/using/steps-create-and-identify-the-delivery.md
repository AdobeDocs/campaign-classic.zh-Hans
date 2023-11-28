---
product: campaign
title: 创建和识别投放
description: 创建和识别投放
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Channel Configuration
role: User
exl-id: 6e37bc14-b1a9-42af-8c28-ae4b5bcaa055
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 5%

---

# 创建和识别投放 {#create-and-identify-the-delivery}

## 创建投放 {#creating-the-delivery}

您可以通过概述或通过 **[!UICONTROL Create > Delivery]** 菜单。


要创建投放，请单击 **[!UICONTROL Create]** 在投放列表上方。 创建新投放时，必须指示使用的投放渠道。 要实现此目的，请从 **[!UICONTROL Delivery template]** 字段。

![](assets/s_ncs_user_wizard_email01_1.png)

为您安装的每个渠道提供了一个默认模板：直邮、电子邮件、传真、电话、移动渠道(SMS)、Facebook、X(以前称为Twitter)等。

>[!NOTE]
>
>列表中提供的渠道取决于您的许可协议。

您可以创建新的投放模板，以预配置特定参数以满足您的需求。 有关模板的更多信息，请参阅 [本节](about-templates.md).

## 识别投放 {#identifying-the-delivery}

您需要完成参数以标识投放。 操作步骤：

1. 在中输入交货的名称 **[!UICONTROL Label]** 字段。

   您还可以为投放分配投放代码。 投放的名称及其代码会显示在投放列表中，但收件人无法看到。

1. 在中添加描述 **[!UICONTROL Description]** 字段。
1. 在相关字段中选择投放性质。 此信息对于投放跟踪很有用：您可以在投放列表中根据此标准进行筛选，或使用此选择标准构建查询。

   ![](assets/s_ncs_user_email_del_nature.png)

1. 单击 **[!UICONTROL Continue]** 以确认此信息并显示消息配置窗口。

投放内容已准备好进行配置。 投放内容定义特定于每个渠道。 有关更多信息，请参阅专述章节：

* [定义电子邮件的内容](defining-the-email-content.md)
* [定义短信内容](sms-create.md#defining-the-sms-content)
* [定义直邮内容](defining-the-direct-mail-content.md)
* [推送通知](about-mobile-app-channel.md)
