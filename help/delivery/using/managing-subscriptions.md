---
product: campaign
title: 管理订阅
description: 管理订阅
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
exl-id: 16dddd4a-2e1a-4c78-8168-f656657bb9b8
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 2%

---

# 管理订阅{#managing-subscriptions}

![](../../assets/common.svg)

## 关于信息服务 {#about-information-services}

一种信息服务包括：

* 注册和订阅（选择加入）、
* 取消注册、自愿退订（选择退订）或自动退订（限时服务，例如试用版）、
* 订阅和退订确认机制（带有确认的简单机制、双重选择加入等）、
* 跟踪订阅者历史记录。

作为标准功能，这些服务包括特定的统计报告：订阅者跟踪、忠诚度级别、退订趋势等。

对于电子邮件，强制退订链接会自动生成，整个选择启用/选择禁用过程都会完全自动进行，历史记录跟踪可确保完全遵守现行法规。

有三种服务订阅/退订模式：

1. 手动
1. 通过导入（仅限订阅）、
1. 通过Web窗体

>[!NOTE]
>
>[此部分](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)中详细介绍了创建具有双重选择加入的订阅表单的示例。

## 创建信息服务 {#creating-an-information-service}

您可以使用关联的确认消息或向订阅者自动投放信息服务，创建和管理信息服务订阅。

要访问信息服务映射，请打开&#x200B;**[!UICONTROL Profiles and Targets]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Services and Subscriptions]**&#x200B;链接。

![](assets/s_ncs_user_services_new.png)

要编辑现有服务，请单击其名称。 要创建服务，请单击位于列表上方的&#x200B;**[!UICONTROL Create]**&#x200B;按钮。

![](assets/s_ncs_user_services_add.png)

* 在&#x200B;**[!UICONTROL Label]**&#x200B;字段中输入服务的名称，然后选择投放渠道：电子邮件、移动设备、Facebook、Twitter或移动设备应用程序。

   >[!NOTE]
   >
   >[此部分](../../social/using/about-social-marketing.md)中详细介绍了facebook和Twitter订阅。 [关于移动应用程序渠道](about-mobile-app-channel.md)中详细介绍了移动应用程序订阅。

* 对于电子邮件类型服务，选择&#x200B;**投放模式**。 可能的模式包括：**[!UICONTROL Newsletter]**&#x200B;或&#x200B;**[!UICONTROL Viral]**。
* 您可以发送&#x200B;**确认消息**，用于订阅或退订。 为此，请从&#x200B;**[!UICONTROL Subscription]**&#x200B;和&#x200B;**[!UICONTROL Unsubscription]**&#x200B;字段中选择要用于创建相应投放的投放模板。 这些模板必须配置为&#x200B;**[!UICONTROL Subscription]**&#x200B;类型的目标映射，而没有定义的目标。 请参阅[关于电子邮件渠道](about-email-channel.md)一节。
* 默认情况下，订阅是无限的。 您可以取消选择&#x200B;**[!UICONTROL Unlimited]**&#x200B;选项以定义服务的有效期。 持续时间可以以天(**[!UICONTROL d]**)或月(**[!UICONTROL m]**)指定。

保存服务后，该服务会添加到“服务和订阅”列表：单击其名称以对其进行编辑。 提供了多个选项卡。 使用&#x200B;**[!UICONTROL Subscriptions]**&#x200B;选项卡可查看信息服务订阅者列表（**[!UICONTROL Active subscriptions]**&#x200B;选项卡）或订阅/退订历史记录（**[!UICONTROL History]**&#x200B;选项卡）。 您还可以在此选项卡中添加和删除订阅者。 请参阅[添加和删除订阅者](#adding-and-deleting-subscribers)。

![](assets/s_ncs_user_services_subscriptions.png)

通过&#x200B;**[!UICONTROL Detail...]**&#x200B;按钮可查看选定收件人的订阅属性。

您可以修改收件人的订阅属性。

![](assets/s_ncs_user_services_modify.png)

在功能板上，单击&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡以跟踪订阅：订阅级别、订阅者总数等的更改。 您可以在此选项卡中存档报表并查看历史记录。

## 添加和删除订阅者 {#adding-and-deleting-subscribers}

在信息服务的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;选项卡中，单击&#x200B;**[!UICONTROL Add]**&#x200B;以添加订阅者。 您还可以右键单击订阅者列表并选择&#x200B;**[!UICONTROL Add]**。 选择要订阅的用户档案存储在其中的文件夹，然后选择要订阅的用户档案并单击&#x200B;**[!UICONTROL OK]**&#x200B;进行验证。

要删除订阅者，请选择他们并单击&#x200B;**[!UICONTROL Delete]**。 也可以右键单击订阅者列表并选择&#x200B;**[!UICONTROL Delete]**。

在这两种情况下，如果用于退订的投放模板已附加到服务，则可以向相关用户发送确认消息（请参阅[创建信息服务](#creating-an-information-service)）。 警告允许您验证或不验证此投放：

![](assets/s_ncs_user_services_update.png)

请参阅[订阅和退订机制](#subscription-and-unsubscription-mechanisms)。

## 向服务的订阅者发送 {#delivering-to-the-subscribers-of-a-service}

要向信息服务的订阅者提供信息服务，您可以将订阅者定位到相关信息服务，如以下示例所示：

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>目标映射必须为&#x200B;**[!UICONTROL Subscriptions]**。

选择 **[!UICONTROL Subscribers of an information service]** 并单击 **[!UICONTROL Next]**。

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

选择目标信息服务并单击&#x200B;**[!UICONTROL Finish]**。

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

使用&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡可以查看选定信息服务的订阅者列表。

## 订阅和退订机制 {#subscription-and-unsubscription-mechanisms}

您可以设置订阅和退订机制，以自动执行流程和订阅者管理。

>[!NOTE]
>
>您可以向新订阅者发送确认消息。\
>此消息的内容通过&#x200B;**[!UICONTROL Subscription]**&#x200B;或&#x200B;**[!UICONTROL Unsubscription]**&#x200B;字段在信息服务配置中定义。
>
>确认消息通过这些字段中指定的投放模板创建。 这些目标映射必须是&#x200B;**[!UICONTROL Subscriptions]**。

![](assets/s_ncs_user_subscribe_confirmation.png)

### 为收件人订阅服务 {#subscribing-a-recipient-to-a-service}

要注册信息服务的收件人，您可以：

* 手动添加服务：为此，请从其配置文件的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;选项卡中，单击&#x200B;**[!UICONTROL Add]**&#x200B;并选择相关的信息服务。

   有关更多信息，请参阅[此部分](../../platform/using/editing-a-profile.md)中关于配置文件编辑的章节。

* 自动订阅此服务的一组收件人。 收件人列表可以来自筛选操作、组、文件夹、导入或使用鼠标进行的直接选择。 要订阅这些收件人，请选择用户档案并右键单击。 选择&#x200B;**[!UICONTROL Actions > Subscribe selection to a service...]**，选择相关服务并启动操作。
* 导入收件人并自动订阅信息服务。 要执行此操作，请在导入向导的最后一步中选择相关服务。

   如需详细信息，请参阅[此部分](../../platform/using/executing-import-jobs.md)。

* 使用Web窗体，以便收件人订阅服务。

   如需详细信息，请参阅[此部分](../../web/using/about-web-applications.md)。

* 创建定位工作流并使用&#x200B;**[!UICONTROL Subscription service]**&#x200B;框。

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   [此部分](../../workflow/using/about-workflows.md)中详细介绍了工作流及其使用方法。

### 从服务取消订阅收件人 {#unsubscribing-a-recipient-from-a-service}

#### 手动取消订阅 {#manual-unsubscribing}

依法，电子邮件投放必须包含退订链接。 收件人可单击此链接以更新其用户档案，并被排除在将来投放的目标之外。

默认的退订链接通过投放向导中提供的内容编辑器工具栏中的最后一个按钮插入（请参阅[关于个性化](about-personalization.md)）。 当收件人单击此链接时，用户档案将添加到阻止列表（选择退出），这意味着任何投放操作将不再定向此收件人。

但是，收件人可以选择从服务取消订阅，而不取消订阅所有服务。 要实现此目的，您可以使用Web窗体（请参阅[此部分](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)）或插入个性化退订链接（请参阅[个性化块](personalization-blocks.md)）。

您还可以手动从收件人用户档案取消收件人订阅。 要执行此操作，请单击相关收件人的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;选项卡，选择相关信息服务，然后单击&#x200B;**[!UICONTROL Delete]**。

您最终可以通过相关的信息服务取消一个或多个收件人的订阅。 要执行此操作，请单击服务的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;选项卡，选择相关收件人，然后单击&#x200B;**[!UICONTROL Delete]**。

#### 自动退订 {#automatic-unsubscription}

信息服务的持续时间可以有限。 有效期届满后，收件人将自动取消订阅。 此时段在服务属性的&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡中指定。 以天表示。

![](assets/s_ncs_user_services_delay.png)

您还可以为群体设置退订工作流。 要实现此目的，请按照与订阅工作流相同的步骤操作，但选择&#x200B;**[!UICONTROL Unsubscription]**&#x200B;选项。 请参阅[为收件人订阅服务](#subscribing-a-recipient-to-a-service)。

### 订阅者跟踪 {#subscriber-tracking}

您可以使用功能板上的&#x200B;**[!UICONTROL Reports]**&#x200B;链接跟踪订阅信息服务的更改。

![](assets/s_ncs_user_services_report.png)
