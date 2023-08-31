---
product: campaign
title: 管理订阅
description: 了解如何在Adobe Campaign中管理订阅
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Subscriptions
role: User
exl-id: 16dddd4a-2e1a-4c78-8168-f656657bb9b8
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 2%

---

# 管理订阅{#managing-subscriptions}

## 关于信息服务 {#about-information-services}

信息服务包括：

* 注册和订阅（选择加入），
* 取消注册、自愿退订（选择退出）或自动退订（限时服务，例如作为试用方案），
* 订阅和退订确认机制（具有确认、双重选择加入等的简单机制），
* 订阅者历史记录的跟踪。

作为一项标准功能，这些服务包括特定的统计报表：订阅者跟踪、忠诚度级别、退订趋势等。

对于电子邮件，会自动生成强制退订链接，并且整个选择加入/选择退出流程都将完全自动化，同时还会进行历史记录跟踪，以确保完全遵守生效的法规。

有三种服务订阅/退订模式：

1. 手动
1. 通过导入（仅限订阅），
1. 通过Web窗体

>[!NOTE]
>
>有关创建包含双重选择加入的订阅表单的示例，请参见 [本节](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

## 创建信息服务 {#creating-an-information-service}

您可以创建和管理信息服务订阅及关联的确认消息或自动发送给订阅者的投放。

要访问信息服务图，请打开 **[!UICONTROL Profiles and Targets]** 选项卡，然后单击 **[!UICONTROL Services and Subscriptions]** 链接。

![](assets/s_ncs_user_services_new.png)

要编辑现有服务，请单击其名称。 要创建服务，请单击 **[!UICONTROL Create]** 按钮的位置。

![](assets/s_ncs_user_services_add.png)

* 在中输入服务的名称 **[!UICONTROL Label]** 字段并选择投放渠道：电子邮件、移动设备、Facebook、Twitter或移动应用程序。

  >[!NOTE]
  >
  >facebook和Twitter订阅详情，请参见 [本节](../../social/using/about-social-marketing.md). 有关移动应用程序订阅的详情，请参见 [关于移动应用程序渠道](about-mobile-app-channel.md).

* 对于电子邮件类型服务，选择 **投放模式**. 可能的模式包括： **[!UICONTROL Newsletter]** 或 **[!UICONTROL Viral]**.
* 您可以发送 **确认消息** 用于订阅或退订。 要实现此目的，请选择投放模板，以从中创建相应的投放 **[!UICONTROL Subscription]** 和 **[!UICONTROL Unsubscription]** 字段。 这些模板必须配置有 **[!UICONTROL Subscription]** 键入目标映射，但未定义目标。 请参阅部分 [关于电子邮件渠道](about-email-channel.md).
* 默认情况下，订阅无限制。 您可以取消选择 **[!UICONTROL Unlimited]** 用于定义服务的有效期的选项。 持续时间以天为单位指定(**[!UICONTROL d]** )或月(**[!UICONTROL m]** )。

保存服务后，该服务将添加到“服务和订阅”列表中：单击其名称可进行编辑。 提供了多个选项卡。 此 **[!UICONTROL Subscriptions]** 选项卡允许您查看信息服务的订阅者列表(**[!UICONTROL Active subscriptions]** 选项卡)或订阅/退订历史记录(**[!UICONTROL History]** 选项卡)。 您还可以从此选项卡添加和删除订阅者。 请参阅 [添加和删除订阅者](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

此 **[!UICONTROL Detail...]** 按钮允许您查看选定收件人的订阅属性。

您可以修改收件人的订阅属性。

![](assets/s_ncs_user_services_modify.png)

在操控板上，单击 **[!UICONTROL Reports]** 选项卡以跟踪订阅：订阅级别的变化、订阅者总数等。 您可以存档报告并查看此选项卡中的历史记录。

## 添加和删除订阅者 {#adding-and-deleting-subscribers}

从 **[!UICONTROL Subscriptions]** 信息服务的选项卡 **[!UICONTROL Add]** 以添加订阅者。 您还可以右键单击订阅者列表并选择 **[!UICONTROL Add]**. 选择要订阅的配置文件存储所在的文件夹，然后选择要订阅的配置文件并单击 **[!UICONTROL OK]** 进行验证。

要删除订阅者，请选择订阅者并单击 **[!UICONTROL Delete]**. 您还可以右键单击订户列表并选择 **[!UICONTROL Delete]**.

在这两种情况下，如果服务附有取消订阅的投放模板，您都可以向相关用户发送确认消息(请参阅 [创建信息服务](#creating-an-information-service))。 出现警告时，您可以验证或不验证此投放：

![](assets/s_ncs_user_services_update.png)

请参阅 [订阅和退订机制](#subscription-and-unsubscription-mechanisms).

## 向服务的订户投放 {#delivering-to-the-subscribers-of-a-service}

要向信息服务的订户投放，您可以定位相关信息服务的订户，如以下示例所示：

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>目标映射必须为 **[!UICONTROL Subscriptions]**.

选择 **[!UICONTROL Subscribers of an information service]** 并单击 **[!UICONTROL Next]**。

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

选择目标信息服务，然后单击 **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

此 **[!UICONTROL Preview]** 选项卡用于查看所选信息服务的订户列表。

## 订阅和退订机制 {#subscription-and-unsubscription-mechanisms}

您可以设置订阅和退订机制以自动执行流程和订阅者管理。

>[!NOTE]
>
>您可以向新订阅者发送确认消息。\
>此消息的内容在信息服务配置中通过 **[!UICONTROL Subscription]** 或 **[!UICONTROL Unsubscription]** 字段。
>
>确认消息是通过这些字段中指定的投放模板创建的。 这些目标映射必须 **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### 为收件人订阅服务 {#subscribing-a-recipient-to-a-service}

要注册信息服务的收件人，您可以：

* 手动添加服务：为此，请从 **[!UICONTROL Subscriptions]** 的选项卡，单击 **[!UICONTROL Add]** 选择相关的信息服务。

  有关更多信息，请参阅中有关用户档案编辑的章节。 [本节](../../platform/using/editing-a-profile.md).

* 自动为一组收件人订阅此服务。 收件人列表可以来自筛选操作、组、文件夹、导入或使用鼠标直接选择。 要订阅这些收件人，请选择用户档案并右键单击。 选择 **[!UICONTROL Actions > Subscribe selection to a service...]**，选择相关的服务，然后启动操作。
* 导入收件人并自动为其订阅信息服务。 要执行此操作，请在导入向导的最后一步中选择相关的服务。

  如需详细信息，请参阅[此部分](../../platform/using/executing-import-jobs.md)。

* 使用Web窗体，以便收件人可以订阅服务。

  如需详细信息，请参阅[此部分](../../web/using/about-web-applications.md)。

* 创建定位工作流并使用 **[!UICONTROL Subscription service]** 盒子。

  ![](assets/s_ncs_user_subscribe_from_wf.png)

  有关工作流及其使用方式的详情，请参见 [本节](../../workflow/using/about-workflows.md).

### 从服务取消订阅收件人 {#unsubscribing-a-recipient-from-a-service}

#### 手动取消订阅 {#manual-unsubscribing}

根据法律，电子邮件投放必须包含退订链接。 收件人可以单击此链接以更新其用户档案，并将其从未来投放的目标中排除。

默认退订链接通过投放向导中提供的内容编辑器工具栏中的最后一个按钮插入(请参阅 [关于个性化](about-personalization.md))。 当收件人单击此链接时，会将用户档案添加到（选择退出）阻止列表，这意味着任何投放操作都将不再以该收件人为目标。

但是，收件人可以选择取消订阅服务而不取消订阅所有服务。 要允许此操作，您可以使用Web表单(请参阅 [本节](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes))或插入个性化的退订链接(请参阅 [个性化块](personalization-blocks.md))。

您还可以从收件人用户档案手动取消订阅收件人。 要执行此操作，请单击 **[!UICONTROL Subscriptions]** 收件人选项卡，选择相关的信息服务，然后单击 **[!UICONTROL Delete]**.

您最终可以通过相关信息服务取消订阅一个或多个收件人。 要执行此操作，请单击 **[!UICONTROL Subscriptions]** 选项卡中，选择相关的收件人，然后单击 **[!UICONTROL Delete]**.

#### 自动退订 {#automatic-unsubscription}

信息服务可以具有有限的持续时间。 有效期到期后，收件人将自动取消订阅。 此期限指定于 **[!UICONTROL Edit]** 服务属性的选项卡。 以天为单位表示。

![](assets/s_ncs_user_services_delay.png)

您还可以为群体设置退订工作流。 要执行此操作，请遵循与订阅工作流相同的过程，但请选择 **[!UICONTROL Unsubscription]** 选项。 请参阅 [为收件人订阅服务](#subscribing-a-recipient-to-a-service).

### 订阅者跟踪 {#subscriber-tracking}

您可以使用以下工具跟踪信息服务订阅中的更改 **[!UICONTROL Reports]** 功能板上的链接。

![](assets/s_ncs_user_services_report.png)
