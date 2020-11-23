---
solution: Campaign Classic
product: campaign
title: Facebook 应用程序示例
description: Facebook 应用程序示例
audience: social
content-type: reference
topic-tags: annexes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 1%

---


# Facebook 应用程序示例{#examples-of-facebook-apps}

当用户单击Facebook应用程序的选项卡时，该选项卡会显示在810像素宽的空间中。 Adobe Campaign使用Facebook类型的Web应用程序来定义和个性化Facebook应用程序中显示的内容，从而更轻松地获取用户档案。

>[!NOTE]
>
>还可以将Adobe Campaign与合作伙伴开发的Facebook应用程序集成。 在这种情况下，无需使用Adobe CampaignWeb应用程序来获取Facebook用户档案。 有关此内容的详细信息，请参阅 [配置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>请遵守创建Facebook应用程序 [中所述的配置步骤](../../social/using/creating-a-facebook-application.md)。

>[!NOTE]
>
>本节详细介绍链接到Facebook类型Web应用程序的元素。 与标准Web应用程序共享的所有元素在本节中 [有详细介绍](../../web/using/about-web-applications.md)。

Facebook类型的Web应用程序示例详见：

* 如何通过7个步骤创建Facebook应用程序。 请参阅 [快速开始:通过7个步骤创建Facebook应用程序](#quick-start--creating-a-facebook-application-in-7-steps)。
* 如何将设置转发到Facebook应用程序。 请参阅 [如何将设置转发到Facebook应用程序？](#how-to-forward-settings-to-a-facebook-application-)。
* 如何获取风扇数据。 请参阅 [如何获取风扇数据](#how-to-acquire-fan-data-)。

>[!IMPORTANT]
>
>这些简单的使用案例作为示例来说明Facebook类型的Web应用程序的功能。

## 建议{#recommendations}

以下限制直接链接到Facebook:

* 必须使用HTTPS构建所有Web应用程序。
* 通过选项卡显示的Facebook应用程序的宽度为810像素。

## 快速开始:通过7个步骤创建Facebook应用程序 {#quick-start--creating-a-facebook-application-in-7-steps}

此示例分步说明如何在Facebook中显示Adobe Campaign构建的应用程序。 在这种情况下，我们要创建一个应用程序，当用户单击应用程 **序选项卡** (App01)时，您可以显示欢&#x200B;**迎消息**。

要创建此应用程序，请应用以下步骤：

1. 在Facebook上创建应用程序( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))。 有关此内容的详细信息，请参阅： [创建Facebook应用程序](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)。

   ![](assets/social_create_facebook_app_002.png)

1. 创建类 **[!UICONTROL Facebook Connect]** 型外部帐户并输入Facebook应用程序的参数。 有关此内容的详细信息，请参阅： [配置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   ![](assets/social_quick_start_2.png)

1. 输入要 **[!UICONTROL Terms of service]** 在Facebook **[!UICONTROL Privacy policy]** 权限请求屏幕上显示的和链接。 有关此内容的详细信息，请参阅： [输入服务条款和隐私策略链接](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links)。

   ![](assets/social_quick_start_1.png)

1. 在Adobe Campaign中创建Facebook类型的Web应用程序。 有关此内容的详细信息，请参阅： [创建Facebook类型的Web应用程序](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)。

   ![](assets/social_webapp_005.png)

1. 编辑Web应用程序。 在此示例中，我们添加了 **[!UICONTROL Page]** 活动并为其定义了标题。

   ![](assets/social_quick_start_4.png)

1. 部署应用程序。

   ![](assets/social_webapp_004.png)

1. 配置Facebook应用程序，使其显示为Facebook页面上的一个选项卡。 有关此内容的详细信息，请参阅： [配置Facebook选项卡](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs)。

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

检查App01应用程 **序的选** 项卡是否显示在Facebook页面上。 单击它应调用欢迎 **消息** 。

![](assets/social_webapp_042.png)

## 如何将设置转发到Facebook应用程序？ {#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>遵守创建Facebook应用程序 [中详细的配置步骤](../../social/using/creating-a-facebook-application.md)。

在示例1中，我们根据字段中的值个性化Facebook页面的显 **[!UICONTROL Fan of the page]** 示。 也可以处理该字 **[!UICONTROL Application settings]** 段。 此字段允许您通过Facebook恢复由Adobe Campaign生成的链接中包含的数据。

让我们举一个决定发送电子邮件公司的活动。 在投放中，有指向Facebook应用程序的链接。 由于URL末尾添加了 **[!UICONTROL app_data]** 参数，此链接是个性化的。 此参数的值可以是反映客户重要性的指标。 在我们的示例中，参数的 **[!UICONTROL app_data]** 值是 **[!UICONTROL big]** （重要客户）和 **[!UICONTROL small]** （不重要客户）。

一旦个性化，URL将如下所示：

* `http://<path of the Facebook application>&app_data=big` （对于重要客户）
* `http://<path of the Facebook application>&app_data=small` （对于不太重要的客户）

在Facebook转发给Adobe Campaign的匿名数据中，收集该字段的值， **[!UICONTROL Application parameters]** 从而使Adobe Campaign能够基于此参数个性化应用显示。

如果用户是重要客户(参数的值 **[!UICONTROL app_data]** 为 **[!UICONTROL big]**)，则显示以下图像：

![](assets/social_webapp_017.png)

如果用户不是重要客户(参 **[!UICONTROL app_data]** 数值 **[!UICONTROL small]**&#x200B;为)，将显示以下图像：

![](assets/social_webapp_016.png)

要重新创建此用例，我们创建了一个由以下元素组成的Web应用程序：

* 基 **[!UICONTROL Test]** 于字段的 **[!UICONTROL Application parameter]** 活动。
* 包含要根据字段值显示的图像的两个页 **[!UICONTROL Application parameter]** 面。

![](assets/social_webapp_018.png)

## 如何获取风扇数据？ {#how-to-acquire-fan-data-}

>[!IMPORTANT]
>
>遵守创建Facebook应用程序 [中详细的配置步骤](../../social/using/creating-a-facebook-application.md)。

此示例向您展示如何联系Facebook用户和优惠，让他们共享其用户档案信息。 让我们举一个公司的例子，它想要赢取潜在客户并在其Facebook页面上组织竞赛来吸引他们。

每当用户单击选 **[!UICONTROL App03]** 项卡时，我们会询问他们是否想参加竞争。

![](assets/social_webapp_fb_000.png)

如果他们决定参加竞赛，我们会优惠他们共享用户档案信息。

![](assets/social_webapp_021.png)

如果用户同意共享其信息，将显示以下屏幕。

![](assets/social_webapp_022.png)

为了构建此用例，我们创建了一个Web应用程序，它包含以下元素：

* **[!UICONTROL Test]** 活动
* 三页
* an **[!UICONTROL Access control]** activity
* **[!UICONTROL Pre-loading]** 活动
* **[!UICONTROL Save]** 活动
* an **[!UICONTROL End]** activity

![](assets/social_webapp_019.png)

### 测试活动 {#test-activity}

活动 **[!UICONTROL Test]** 基于和字 **[!UICONTROL ID]** 段进 **[!UICONTROL Application parameters]** 行。

![](assets/social_webapp_023.png)

它由三个分支组成：

* **[!UICONTROL identifier (UID) is empty]** :仅当用户已同意共享其信息时，Facebook才会转发该标识符。 活动的第一个 **[!UICONTROL Test]** 分支允许您仅向从未输入过（即ID为空的用户）的用户提供竞争产品。
* **[!UICONTROL application parameter equals 'thanks']** :要避开链接到Facebook的显示错误，Web应用程序结束页面将指向Facebook应用程序的URL, **[!UICONTROL app_data]** 该URL将参数添加到该应用程序中，以 **[!UICONTROL thanks]** 便使用该值(有关详细信息，请参阅： [结束活动](#end-activity))。 第二个分支允许您查看用户是否来自第 **[!UICONTROL End]** 一个分支的活动（并且刚刚进入竞争对手），以显示感谢信。 有关使用其他URL参数的详细信息，请参阅： [如何将设置转发到Facebook应用程序？](#how-to-forward-settings-to-a-facebook-application-)。
* **[!UICONTROL Default branch]** :如果用户已在上一日期（应用程序参数不同于）输入竞赛信息（ID已输入），我们将显示一个页面，表 **[!UICONTROL thanks]**&#x200B;明他们已输入。

### 竞争页面 {#competition-page}

要避开链接到Facebook的显示错误，您还需要在竞 **[!UICONTROL Parent window]** 赛页 **[!UICONTROL In the top window]** 面的 **[!UICONTROL Window]** 字段中选择或选择。

![](assets/social_webapp_028.png)

### 访问控制活动 {#access-control-activity}

该活动 **[!UICONTROL Access control]** 允许您在用户进入竞争对手时显示Facebook权限请求页面。 如果他们同意共享其信息，则在预加载内恢复该信息。 For more on this, refer to: [Pre-loading activity](#pre-loading-activity).

如果您之前在创建Web应用程序时输入了外部帐户( [请参阅创建Facebook类型的Web应用程序](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application))，则无需编辑活动。 否则，转到字段 **[!UICONTROL Application]** 并选择链接到Facebook应用程序的外部帐户。

![](assets/social_webapp_024.png)

### 预加载活动 {#pre-loading-activity}

选择要用于预加载的数据源：

* **[!UICONTROL Marketing database]** :此选项允许您通过Adobe Campaign库预载数据。
* **[!UICONTROL Facebook]** :此选项允许您使用Facebook预加载数据。

![](assets/social_webapp_029.png)

**营销数据库**

通过此选项，可恢复用户档案表中存在的访客的数据。 验证基于用户单击Facebook应用程序选项卡时恢复的外部Facebook ID。 如果在活动后添加 **[!UICONTROL Pre-loading]** 表单，则预加载包含数据库中信息的字段。

![](assets/social_webapp_030.png)

>[!NOTE]
>
>有关通过预加载库Adobe Campaign数据的详细信息，请参 [阅本节](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

**Facebook**

此选项允许您定义要收集的Facebook用户档案信息（用户已同意共享的信息），以便保存该信息。

![](assets/social_webapp_025.png)

通过 **[!UICONTROL Database information]** 此选项可收集以下数据：

* **[!UICONTROL External ID]**:用户ID
* **[!UICONTROL Gender]**:用户性别
* **[!UICONTROL Verified]** :此字段指定用户是否具有经过验证的Facebook帐户。
* **[!UICONTROL Full name]**:用户全名
* **[!UICONTROL First name]**:用户名
* **[!UICONTROL Last name]**:用户姓氏
* **[!UICONTROL Language]**:用户语言

您还可以通过选中相应的复选框来收集用户档案照片、好友列表、电子邮件地址、出生日期、兴趣和位置。

在单击之 **[!UICONTROL Ok]**&#x200B;前，选中 **[!UICONTROL I agree to comply with Facebook conditions of use]** 该框。

>[!NOTE]
>
>如果选中该部分中的一个或多个 **[!UICONTROL Private information]** 框，Facebook权限请求屏幕将自动显示此数据的访问请求。
>
>要您收集所选信息，用户必须同意共享它。
>
>如果要同时添加两种预加载(通过Adobe Campaign和Facebook)，请逐个添加两个预加载框。

### 保存活动 {#save-activity}

活动 **[!UICONTROL Save]** 允许您在访客表中存储在之前阶段收集的信息。

如果用户档案已存在于访客表中，则会使用收集的新数据更新其数据。

如果用户档案库中不存在访客，且已收集Facebook用户的电子邮件地址，则将在访客表中创建该。

![](assets/social_webapp_026.png)

1. 在字 **[!UICONTROL Visitor creation folder]** 段中，选择将在其中创建用户档案的文件夹。 对于Facebook类型的Web应用程序，默认创建文件夹为 **[!UICONTROL Visitors]**。
1. 在字 **[!UICONTROL Reconciliation mode]** 段中，选择要使用的对帐模式：

   * **[!UICONTROL Automatic]** :对帐根据电子邮件、姓氏、名字和出生日期进行。
   * **[!UICONTROL Manual]** :请选择一个或多个合并关键项。
   * **[!UICONTROL None]** :不会和解。

1. 在字 **[!UICONTROL Mapping]** 段中，选择要进行对帐的模式。

   >[!IMPORTANT]
   >
   >确保在投放映射中 **[!UICONTROL Social networks]** 正确输入选项卡的字段。 投放映射通过节点 **[!UICONTROL Administration > Campaign management > Target mappings]** 访问。

1. 您可以选择要对帐的搜索文件夹和新用户档案的创建文件夹。 如果字段为空，则会搜索用户档案并在映射模式的默认文件夹中创建。

### 结束活动 {#end-activity}

要避开链接到Facebook的显示错误，您需要选 **[!UICONTROL Use an external URL]** 中该框并输入Facebook应用程序的URL，后跟参 **[!UICONTROL app_data]** 数和值。 此值将用在活动 **[!UICONTROL Test]** 中，以检测用户是否刚刚进入竞争对手，并显示感谢信（如果适用）。 For more on this, refer to: [Test activity](#test-activity).

在我们的例子中，所使用的值 **是感谢**。

![](assets/social_webapp_027.png)

### 访客的详细信息屏幕 {#details-screen-of-a-visitor}

与Twitter关注者类似(请参阅： [操作原则](../../social/using/publishing-on-twitter.md#operating-principle))，恢复的Facebook用户档案存储在访客表中。 要显示访客的列表，请转到节 **[!UICONTROL Profiles and Targets > Visitors]** 点。

同意共享其用户档案信息的每个Facebook潜在客户都会添加到访客列表。 如果框 **[!UICONTROL Friends]** 已在活动中 **[!UICONTROL Pre-load]** 选中(请参阅： [预加载](#pre-loading-activity)活动)。

![](assets/social_webapp_037.png)

在访客 **[!UICONTROL Summary]** 详细信息窗口的部分中，指标有两种可能的 **[!UICONTROL New Contact]** 状态：

![](assets/social_webapp_038.png)

如果显示绿色复选标记，则表示访客未与任何收件人协调。 在这种情况下，将在收件人的列表中创建新用户档案。

![](assets/social_webapp_039.png)

红十字表示访客与收件人和解。 单击字段右侧的放大镜可显 **[!UICONTROL Recipient]** 示匹配的收件人。

![](assets/social_webapp_040.png)

转至收件人的详细信息窗口以显示匹配的访客（如果适用）。 选择选 **[!UICONTROL Others]** 项卡，然后多次在部分中单击访客的 **[!UICONTROL Web identities]** 名称。

![](assets/social_webapp_041.png)

访客 **[!UICONTROL Activities]** 详细信息页面的屏幕包含以下信息：

* “Open Graph”类型风扇活动:播放的音乐、观看的视频、阅读的文章和安装的应用程序的不足（Deezer、Spotify、Dailymotion、Yahoo News等）

   ![](assets/social_facebook_activities.png)

* “喜欢”和粉丝根据Adobe Campaign发送的投放添加的评论
* 粉丝喜欢的页面
* 风扇的登记

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >为了Adobe Campaign收集风扇的登记，您需要单击服务配 **[!UICONTROL Subscribe]** 置屏幕上的按钮。 有关此内容的详细信息，请参阅 [配置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

## 如何使用Facebook用户档案数据预加载表单的字段 {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

该应 **[!UICONTROL Social Marketing]** 用程序还允许您向表单添加按钮，以使用Facebook预加载信息显示用户档案字段。 此选项在所有Web应用程序模板(类型活动&#x200B;**[!UICONTROL Page]** )中均可用，详细 [介绍本节](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)。

![](assets/social_webapp_035.png)

>[!NOTE]
>
>在使用此函数进行开始之前，您需要创建Facebook应用程序和类 **[!UICONTROL Facebook Connect]** 型外部帐户。 有关此内容的详细信息，请参阅 [配置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

