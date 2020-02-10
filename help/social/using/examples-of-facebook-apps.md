---
title: Facebook应用程序示例
seo-title: Facebook应用程序示例
description: Facebook应用程序示例
seo-description: null
page-status-flag: never-activated
uuid: 336f4006-3545-4b04-959d-61cd0446af27
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: annexes
discoiquuid: 07be1d3c-b038-48ca-be37-a33adb8e0fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7f03e1fbb94bbd5b00fa0094a0b5e9be45629ec7

---


# Facebook应用程序示例{#examples-of-facebook-apps}

当用户单击Facebook应用程序的选项卡时，该选项卡将显示在810像素宽的空间中。 Adobe Campaign使用Facebook类型的Web应用程序来定义和个性化Facebook应用程序中显示的内容，从而更轻松地获取配置文件。

>[!NOTE]
>
>还可以将Adobe Campaign与合作伙伴开发的Facebook应用程序集成。 在这种情况下，无需使用Adobe Campaign web应用程序获取Facebook配置文件。 有关详细信息，请参阅配 [置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

![](assets/social_webapp_fb_000.png)

>[!CAUTION]
>
>请遵循创建Facebook应用程序中所述 [的配置步骤](../../social/using/creating-a-facebook-application.md)。

>[!NOTE]
>
>本节详细介绍了链接到Facebook类型Web应用程序的元素。 与标准Web应用程序共享的所有元素在本节中有 [详细介绍](../../web/using/about-web-applications.md)。

此处详细介绍的Facebook类型Web应用程序示例有：

* 如何通过7个步骤创建Facebook应用程序。 请参阅快 [速入门：通过7个步骤创建Facebook应用程序](#quick-start--creating-a-facebook-application-in-7-steps)。
* 如何将设置转发到Facebook应用程序。 请参阅 [如何将设置转发到Facebook应用程序？](#how-to-forward-settings-to-a-facebook-application-)。
* 如何获取风扇数据。 请参阅 [如何获取风扇数据？](#how-to-acquire-fan-data-)。

>[!CAUTION]
>
>这些简单的用例作为示例来说明Facebook类型Web应用程序的功能。

## 建议 {#recommendations}

以下限制直接链接到Facebook:

* 必须使用HTTPS构建所有Web应用程序。
* 通过选项卡显示的Facebook应用程序的宽度为810像素。

## 快速入门：通过7个步骤创建Facebook应用程序 {#quick-start--creating-a-facebook-application-in-7-steps}

此示例提供了如何在Facebook中显示Adobe Campaign构建的应用程序的分步过程。 在这种情况下，我们要创建一个应用程序，当用户单击应用程序选项卡( **App01******)时，您可以显示“欢迎”消息。

要创建此应用程序，请应用以下步骤：

1. 在Facebook上创建应用程序( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))。 有关详细信息，请参阅：创 [建Facebook应用程序](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)。

   ![](assets/social_create_facebook_app_002.png)

1. 创建一 **[!UICONTROL Facebook Connect]** 个类型外部帐户并输入Facebook应用程序的参数。 有关详细信息，请参阅：配 [置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   ![](assets/social_quick_start_2.png)

1. 输入要 **[!UICONTROL Terms of service]** 在Facebook权 **[!UICONTROL Privacy policy]** 限请求屏幕上显示的和链接。 有关详细信息，请参阅：输 [入服务条款和隐私策略链接](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links)。

   ![](assets/social_quick_start_1.png)

1. 在Adobe Campaign中创建Facebook类型的Web应用程序。 有关详细信息，请参阅：创 [建Facebook类型Web应用程序](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)。

   ![](assets/social_webapp_005.png)

1. 编辑Web应用程序。 在此示例中，我们添加了一 **[!UICONTROL Page]** 个活动并为其定义了标题。

   ![](assets/social_quick_start_4.png)

1. 部署应用程序。

   ![](assets/social_webapp_004.png)

1. 配置Facebook应用程序，使其显示为Facebook页面上的一个选项卡。 有关详细信息，请参阅：配 [置Facebook选项卡](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs)。

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

检查 **App01应用程序的选** 项卡，该选项卡显示在您的Facebook页面上。 单击它应该会调用欢 **迎消息** 。

![](assets/social_webapp_042.png)

## 如何将设置转发到Facebook应用程序？ {#how-to-forward-settings-to-a-facebook-application-}

>[!CAUTION]
>
>遵守创建Facebook应用程序中 [详细的配置步骤](../../social/using/creating-a-facebook-application.md)。

在示例1中，我们根据字段中的值个性化Facebook页面的显 **[!UICONTROL Fan of the page]** 示。 也可以处理该字 **[!UICONTROL Application settings]** 段。 通过此字段，您可以恢复由Adobe Campaign通过Facebook生成的链接中包含的数据。

让我们举一个决定发送电子邮件营销活动的公司的例子。 在分发中，将有一个指向Facebook应用程序的链接。 由于URL末尾添加了 **[!UICONTROL app_data]** 参数，因此此链接是个性化的。 此参数的值可以是反映客户重要性的指标。 在我们的示例中，参数的值 **[!UICONTROL app_data]** 为( **[!UICONTROL big]** 重要客户)和 **[!UICONTROL small]** （不重要客户）。

一旦个性化，URL将如下所示：

* `http://<path of the Facebook application>&app_data=big` （对于重要客户）
* `http://<path of the Facebook application>&app_data=small` （对于不太重要的客户）

在由Facebook转发到Adobe Campaign的匿名数据中，会收集字段的值，从而使 **[!UICONTROL Application parameters]** Adobe Campaign能够根据此参数个性化应用程序显示。

如果用户是重要客户(参数的值 **[!UICONTROL app_data]** 为 **[!UICONTROL big]**)，将显示以下图像：

![](assets/social_webapp_017.png)

如果用户不是重要客户(参数的值 **[!UICONTROL app_data]** 为 **[!UICONTROL small]**)，则显示以下图像：

![](assets/social_webapp_016.png)

要重新创建此用例，我们创建了由以下元素组成的Web应用程序：

* 基 **[!UICONTROL Test]** 于字段的活 **[!UICONTROL Application parameter]** 动。
* 包含要根据字段值显示的图像的两个页 **[!UICONTROL Application parameter]** 面。

![](assets/social_webapp_018.png)

## 如何获取风扇数据？ {#how-to-acquire-fan-data-}

>[!CAUTION]
>
>遵守创建Facebook应用程序中 [详细的配置步骤](../../social/using/creating-a-facebook-application.md)。

此示例向您展示如何与Facebook用户联系并向他们提供共享其个人资料信息的服务。 让我们举一个公司想要收购潜在客户的例子，在其Facebook页面上组织竞争以吸引他们。

每当用户单击该选 **[!UICONTROL App03]** 项卡时，我们都会询问他们是否希望参加竞争。

![](assets/social_webapp_fb_000.png)

如果他们决定参加竞赛，我们会向他们提供个人信息。

![](assets/social_webapp_021.png)

如果他们同意共享其信息，将显示以下屏幕。

![](assets/social_webapp_022.png)

为构建此用例，我们创建了一个Web应用程序，其中包含以下元素：

* 活 **[!UICONTROL Test]** 动
* 三页
* 活 **[!UICONTROL Access control]** 动
* 活 **[!UICONTROL Pre-loading]** 动
* 活 **[!UICONTROL Save]** 动
* 活 **[!UICONTROL End]** 动

![](assets/social_webapp_019.png)

### 测试活动 {#test-activity}

活动 **[!UICONTROL Test]** 基于和字 **[!UICONTROL ID]** 段进 **[!UICONTROL Application parameters]** 行。

![](assets/social_webapp_023.png)

它由三个分支组成：

* **[!UICONTROL identifier (UID) is empty]** :仅当用户已同意共享其信息时，Facebook才会转发该标识符。 通过活动的第一 **[!UICONTROL Test]** 个分支，您只能向从未输入过的用户（即ID为空的用户）提供竞赛。
* **[!UICONTROL application parameter equals 'thanks']** :要绕过链接到Facebook的显示错误，Web应用程序结束页面会指向Facebook应用程序的URL, **[!UICONTROL app_data]** 该URL将参数添加到该应用程序中，以使用该值(有关详细信息，请参阅 **[!UICONTROL thanks]** :结 [束活动](#end-activity))。 第二个分支允许您了解用户是否来自第一个分支的活动( **[!UICONTROL End]** 并且刚刚进入竞争对手)，以显示感谢消息。 有关使用其他URL参数的详细信息，请参阅：如 [何将设置转发到Facebook应用程序？](#how-to-forward-settings-to-a-facebook-application-)。
* **[!UICONTROL Default branch]** :如果用户已在上一日期(应用程序参数不同于 **[!UICONTROL thanks]**)输入竞争对手（ID已输入），我们将显示一个页面，表示他们已输入。

### 竞争页面 {#competition-page}

要绕过链接到Facebook的显示错误，您还需要在竞 **[!UICONTROL Parent window]** 赛页 **[!UICONTROL In the top window]** 面 **[!UICONTROL Window]** 的字段中选择或。

![](assets/social_webapp_028.png)

### 访问控制活动 {#access-control-activity}

通过 **[!UICONTROL Access control]** 该活动，您可以在用户进入竞争对手时显示Facebook权限请求页。 如果他们同意共享其信息，则会在预加载期间恢复该信息。 For more on this, refer to: [Pre-loading activity](#pre-loading-activity).

如果您之前在创建Web应用程序时输入了外部帐户(请参阅 [Creating a Facebook type web application](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application))，则无需编辑活动。 否则，转到字段， **[!UICONTROL Application]** 然后选择链接到Facebook应用程序的外部帐户。

![](assets/social_webapp_024.png)

### 预加载活动 {#pre-loading-activity}

选择要用于预加载的数据源：

* **[!UICONTROL Marketing database]** :此选项允许您通过Adobe Campaign数据库预载数据。
* **[!UICONTROL Facebook]** :此选项允许您使用Facebook预加载数据。

![](assets/social_webapp_029.png)

**营销数据库**

通过此选项，可以恢复访客表中存在的配置文件的数据。 验证基于用户单击Facebook应用程序选项卡时恢复的外部Facebook ID。 如果在活动后面添加 **[!UICONTROL Pre-loading]** 表单，则预加载包含数据库中信息的字段。

![](assets/social_webapp_030.png)

>[!NOTE]
>
>有关通过Adobe Campaign数据库预加载数据的详细信息，请参阅 [本节](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

**Facebook**

此选项允许您定义要收集的Facebook个人资料信息（其中包括用户同意共享的信息），以便保存该信息。

![](assets/social_webapp_025.png)

通过 **[!UICONTROL Database information]** 此选项可收集以下数据：

* **[!UICONTROL External ID]**:用户ID
* **[!UICONTROL Gender]**:用户性别
* **[!UICONTROL Verified]** :此字段指定用户是否具有经过验证的Facebook帐户。
* **[!UICONTROL Full name]**:用户全名
* **[!UICONTROL First name]**:用户名
* **[!UICONTROL Last name]**:用户姓
* **[!UICONTROL Language]**:用户语言

您还可以通过选中相应的复选框来收集个人资料照片、好友列表、电子邮件地址、出生日期、兴趣和位置。

在单击之 **[!UICONTROL Ok]**&#x200B;前，请选中 **[!UICONTROL I agree to comply with Facebook conditions of use]** 该框。

>[!NOTE]
>
>如果选中该部分中的一个或多个框， **[!UICONTROL Private information]** 则Facebook权限请求屏幕将自动显示对此数据的访问请求。
>
>要您收集选定的信息，用户必须同意共享该信息。
>
>如果您希望两种预加载类型（通过Adobe Campaign和Facebook）都添加两个逐个预加载框。

### 保存活动 {#save-activity}

通过 **[!UICONTROL Save]** 该活动，您可以将在访客表中先前阶段收集到的信息存储起来。

如果访客表中已存在配置文件，则其数据将更新为所收集的新数据。

如果数据库中不存在配置文件，且已收集Facebook用户的电子邮件地址，则访客表中将创建访客。

![](assets/social_webapp_026.png)

1. 在字段 **[!UICONTROL Visitor creation folder]** 中，选择将在其中创建配置文件的文件夹。 对于Facebook类型的Web应用程序，默认创建文件夹为 **[!UICONTROL Visitors]**。
1. 在字 **[!UICONTROL Reconciliation mode]** 段中，选择要使用的对帐模式：

   * **[!UICONTROL Automatic]** :对帐根据电子邮件、姓氏、名字和出生日期进行。
   * **[!UICONTROL Manual]** :请选择一个或多个对帐密钥。
   * **[!UICONTROL None]** :不会和解。

1. 在字 **[!UICONTROL Mapping]** 段中，选择要执行对帐的架构。

   >[!CAUTION]
   >
   >确保在分发映射中 **[!UICONTROL Social networks]** 正确输入了选项卡的字段。 通过节点访问传送 **[!UICONTROL Administration > Campaign management > Target mappings]** 映射。

1. 您可以为对帐选择搜索文件夹，为新配置文件选择创建文件夹。 如果字段为空，则会在映射架构的默认文件夹中搜索并创建配置文件。

### 结束活动 {#end-activity}

要绕过链接到Facebook的显示错误，您需要选中该框并输入Facebook应用程序的 **[!UICONTROL Use an external URL]** URL，后跟参数 **[!UICONTROL app_data]** 和值。 此值将用在活动中，以检 **[!UICONTROL Test]** 测用户是否刚刚进入竞赛，并显示感谢信（如果适用）。 For more on this, refer to: [Test activity](#test-activity).

在我们的示例中，使用的值是 **感谢**。

![](assets/social_webapp_027.png)

### 访客的详细信息屏幕 {#details-screen-of-a-visitor}

与Twitter关注者类似(请参阅：操作 [原则](../../social/using/publishing-on-twitter.md#operating-principle))，恢复的Facebook配置文件存储在访客表中。 要显示访客列表，请转到该节 **[!UICONTROL Profiles and Targets > Visitors]** 点。

同意共享其个人资料信息的每个Facebook潜在客户都会添加到访客列表中。 如果选 **[!UICONTROL Friends]** 中了该框， **[!UICONTROL Pre-load]** 请参阅：预 [加载活动](#pre-loading-activity))，还会添加朋友。

![](assets/social_webapp_037.png)

在访客 **[!UICONTROL Summary]** 详细信息窗口的部分中，该指示符有两种可能的状 **[!UICONTROL New Contact]** 态：

![](assets/social_webapp_038.png)

如果显示绿色复选标记，则表示访客未与任何收件人协调。 在这种情况下，将在收件人列表中创建新的配置文件。

![](assets/social_webapp_039.png)

红叉表示访客已与收件人协调。 您可以单击字段右侧的放大镜以 **[!UICONTROL Recipient]** 显示匹配的收件人。

![](assets/social_webapp_040.png)

转到收件人的详细信息窗口以显示匹配的访客（如果适用）。 选择 **[!UICONTROL Others]** 选项卡，然后在部分中双击访客的名 **[!UICONTROL Web identities]** 称。

![](assets/social_webapp_041.png)

访 **[!UICONTROL Activities]** 客详细信息页面的屏幕包含以下信息：

* “Open Graph”类型的粉丝活动：播放的音乐、观看的视频、阅读的文章和安装的应用程序的不足（Deezer、Spotify、Dailymotion、Yahoo News等）

   ![](assets/social_facebook_activities.png)

* “赞”和粉丝在Adobe Campaign发送的投递后添加的评论
* 粉丝喜欢的页面
* 风扇的登记

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >为了使Adobe Campaign收集风扇登记，您需要单击服务配 **[!UICONTROL Subscribe]** 置屏幕上的按钮。 有关详细信息，请参阅配 [置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

## 如何使用Facebook配置文件数据预加载表单的字段 {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

该应 **[!UICONTROL Social Marketing]** 用程序还允许您向表单中添加按钮，以便使用Facebook配置文件信息预加载字段。 此选项在所有Web应用程序模板（类型活动）中&#x200B;**[!UICONTROL Page]** 均可用，本节将详细介绍该 [选项](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)。

![](assets/social_webapp_035.png)

>[!NOTE]
>
>在开始使用此函数之前，您需要创建Facebook应用程序和类型外 **[!UICONTROL Facebook Connect]** 部帐户。 有关详细信息，请参阅配 [置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

