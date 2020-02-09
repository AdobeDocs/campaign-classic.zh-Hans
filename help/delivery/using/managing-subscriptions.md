---
title: 管理订阅
seo-title: 管理订阅
description: 管理订阅
seo-description: null
page-status-flag: never-activated
uuid: a2c526fa-3080-4dd5-9628-f0e7040f93cd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 9a61fe74-f779-4f23-be25-3d9a8e95704a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 管理订阅{#managing-subscriptions}

## 关于信息服务 {#about-information-services}

一种信息服务包括：

* 注册和订阅（选择加入）,
* 取消注册、自愿取消订阅（退出）或自动取消订阅（限时服务，例如试用版）、
* 订阅和取消订阅确认机制（简单的确认机制、双选等）,
* 跟踪订户历史记录。

作为标准功能，这些服务包括特定的统计报告：订阅者跟踪、忠诚度级别、取消订阅趋势等。

对于电子邮件，强制取消订阅链接会自动生成，整个选择加入／退出流程将完全自动化，并通过历史记录跟踪来确保完全遵守现行的法规。

有三种服务订阅／取消订阅模式：

1. 手动
1. 通过导入（仅限订阅）,
1. 通过Web表单

>[!NOTE]
>
>本节详细介绍了创建双选择加入订阅表单 [的示例](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)。

## 创建信息服务 {#creating-an-information-service}

您可以创建和管理信息服务的订阅，这些订阅具有关联的确认消息或向订阅者自动发送。

要访问信息服务地图，请转到范 **[!UICONTROL Profiles and Targets]** 围并单击链 **[!UICONTROL Services and Subscriptions]** 接。

![](assets/s_ncs_user_services_new.png)

要编辑现有服务，请单击其名称。 要创建服务，请单击列 **[!UICONTROL Create]** 表上方的按钮。

![](assets/s_ncs_user_services_add.png)

* 在字段中输入服务的名称， **[!UICONTROL Label]** 然后选择传送渠道：电子邮件、移动、Facebook、Twitter或移动应用程序。

   >[!NOTE]
   >
   >此部分详细介绍了Facebook和Twitter [订阅](../../social/using/about-social-marketing.md)。 移动应用程序订阅详见“关于 [移动应用程序渠道”](../../delivery/using/about-mobile-app-channel.md)。

* 对于电子邮件类型服务，选择“交 **付”模式**。 可能的模式包括：或 **[!UICONTROL Newsletter]** 者 **[!UICONTROL Viral]**。
* 您可以发送订 **阅或取消订阅的确** 认消息。 为此，请选择要用于从和字段创建相应提交的提交模 **[!UICONTROL Subscription]** 板 **[!UICONTROL Unsubscription]** 。 这些模板必须配置有类型目 **[!UICONTROL Subscription]** 标映射，但不能定义目标。 请参阅关 [于电子邮件渠道](../../delivery/using/about-email-channel.md)。
* 默认情况下，订阅是无限制的。 您可以取消选 **[!UICONTROL Unlimited]** 择此选项来定义服务的有效期。 持续时间可以以天(**[!UICONTROL d]** )或月(**[!UICONTROL m]** )为单位。

保存服务后，该服务将添加到“服务和订阅”列表：单击其名称可编辑它。 可使用多个选项卡。 通过 **[!UICONTROL Subscriptions]** 该选项卡可查看信息服务（选项卡）或订阅／取消订阅历史&#x200B;**[!UICONTROL Active subscriptions]** 记录（选项卡）的订&#x200B;**[!UICONTROL History]** 阅者列表。 您还可以从此选项卡中添加和删除订阅者。 请参阅 [添加和删除订阅者](#adding-and-deleting-subscribers)。

![](assets/s_ncs_user_services_subscriptions.png)

通过 **[!UICONTROL Detail...]** 该按钮可查看选定收件人的订阅属性。

您可以修改收件人的订阅属性。

![](assets/s_ncs_user_services_modify.png)

在功能板上，单击选 **[!UICONTROL Reports]** 项卡以跟踪订阅：订阅级别的更改、订阅者总数等。 您可以在此选项卡中存档报告并查看历史记录。

## 添加和删除订阅者 {#adding-and-deleting-subscribers}

在信息 **[!UICONTROL Subscriptions]** 服务的选项卡中，单击以 **[!UICONTROL Add]** 添加订阅者。 您还可以右键单击订阅者列表并选择 **[!UICONTROL Add]**。 选择存储要订阅的配置文件的文件夹，然后选择要订阅的配置文件并单击以 **[!UICONTROL OK]** 验证。

要删除订阅者，请选择他们并单击 **[!UICONTROL Delete]**。 您还可以右键单击订阅者列表并选择 **[!UICONTROL Delete]**。

在这两种情况下，如果取消订阅的分发模板已附加到服务，则可以向相关用户发送确认消息(请参阅 [创建信息服务](#creating-an-information-service))。 警告允许您验证或不验证此交付：

![](assets/s_ncs_user_services_update.png)

请参阅 [订阅和取消订阅机制](#subscription-and-unsubscription-mechanisms)。

## 交付给服务的订阅者 {#delivering-to-the-subscribers-of-a-service}

要向信息服务的订阅者传送信息，您可以将相关信息服务的订阅者定位到相应的订阅者，如下例所示：

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>目标映射必须为 **[!UICONTROL Subscriptions]**。

选择 **[!UICONTROL Subscribers of an information service]** 并单击 **[!UICONTROL Next]**。

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

选择目标信息服务并单击 **[!UICONTROL Finish]**。

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

该选 **[!UICONTROL Preview]** 项卡允许您查看选定信息服务的订阅者列表。

## 订阅和取消订阅机制 {#subscription-and-unsubscription-mechanisms}

您可以设置订阅和取消订阅机制以自动化流程和订阅者管理。

>[!NOTE]
>
>可以向新订阅者发送确认消息。\
>此消息的内容通过或字段在信息服务配置中 **[!UICONTROL Subscription]** 定 **[!UICONTROL Unsubscription]** 义。
>
>通过这些字段中指定的传送模板创建确认消息。 这些目标映射必须 **[!UICONTROL Subscriptions]**&#x200B;是。

![](assets/s_ncs_user_subscribe_confirmation.png)

### 将收件人订阅到服务 {#subscribing-a-recipient-to-a-service}

要注册信息服务的收件人，您可以：

* 手动添加服务：要执行此操作，请在其配置文 **[!UICONTROL Subscriptions]** 件的选项卡中，单击并 **[!UICONTROL Add]** 选择相关的信息服务。

   有关此部分的详细信息，请参阅此部分中有关配置文件编 [辑的部分](../../platform/using/editing-a-profile.md)。

* 自动订阅一组收件人到此服务。 收件人列表可以来自使用鼠标的筛选操作、组、文件夹、导入或直接选择。 要订阅这些收件人，请选择配置文件并右键单击。 选 **[!UICONTROL Actions > Subscribe selection to a service...]**&#x200B;择相关服务，然后启动操作。
* 导入收件人并自动将其订阅到信息服务。 为此，请在导入向导的最后一步中选择相关服务。

   如需详细信息，请参阅[此部分](../../platform/using/importing-data.md#import-wizard)。

* 使用Web表单，以便收件人可以订阅服务。

   如需详细信息，请参阅[此部分](../../web/using/about-web-applications.md)。

* 创建定位工作流并使用 **[!UICONTROL Subscription service]** 框。

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   本节详细介绍了工作流及其使 [用方法](../../workflow/using/about-workflows.md)。

### 从服务中取消订阅收件人 {#unsubscribing-a-recipient-from-a-service}

#### 手动取消订阅 {#manual-unsubscribing}

根据法律，电子邮件发送必须包含取消订阅链接。 收件人可以单击此链接以更新其配置文件，并将其排除在将来提交的目标之外。

默认的取消订阅链接通过交付向导中提供的内容编辑器工具栏中的最后一个按钮插入(请参 [阅关于个性化](../../delivery/using/about-personalization.md))。 当收件人单击此链接时，配置文件将列入黑名单（选择退出），这意味着此收件人将不再被任何交付操作定位。

但是，收件人可以选择取消订阅服务而不取消订阅所有服务。 要实现此目的，您可以使用Web表单(请参 [阅本节](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes))或插入个性化的取消订阅链接(请参阅个 [性化基块](../../delivery/using/personalization-blocks.md))。

您还可以手动从收件人配置文件中取消订阅收件人。 为此，请单击相 **[!UICONTROL Subscriptions]** 关收件人的选项卡，选择相关信息服务，然后单击 **[!UICONTROL Delete]**。

您最终可以通过相关的信息服务取消订阅一个或多个收件人。 为此，请单击服务 **[!UICONTROL Subscriptions]** 的选项卡，选择相关收件人并单击 **[!UICONTROL Delete]**。

#### 自动取消订阅 {#automatic-unsubscription}

信息服务的持续时间可以有限。 有效期到期后，收件人将自动取消订阅。 此期间在服务属性 **[!UICONTROL Edit]** 的选项卡中指定。 以天数表示。

![](assets/s_ncs_user_services_delay.png)

您还可以为人群设置取消订阅工作流。 为此，请按照与订阅工作流相同的步骤操作，但选择该选 **[!UICONTROL Unsubscription]** 项。 请参 [阅将收件人订阅到服务](#subscribing-a-recipient-to-a-service)。

### 订阅者跟踪 {#subscriber-tracking}

您可以使用功能板上的链接跟踪信息服务订 **[!UICONTROL Reports]** 阅中的更改。

![](assets/s_ncs_user_services_report.png)
