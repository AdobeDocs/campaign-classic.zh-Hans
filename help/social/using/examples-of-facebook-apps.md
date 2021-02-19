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

当用户单击Facebook应用程序的选项卡时，该选项卡会显示在810像素宽的空间中。 Adobe Campaign使用Facebook类型的Web应用程序，让您定义和个性化Facebook应用程序中显示的内容，从而更轻松地获取用户档案。

>[!NOTE]
>
>还可以将Adobe Campaign与合作伙伴开发的Facebook应用程序集成。 在这种情况下，无需使用Adobe Campaign Web应用程序来获取Facebook用户档案。 有关详细信息，请参阅[配置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>请遵循[创建Facebook应用程序](../../social/using/creating-a-facebook-application.md)中描述的配置步骤。

>[!NOTE]
>
>本节详细介绍链接到Facebook类型Web应用程序的元素。 与标准Web应用程序共享的所有元素在[本节](../../web/using/about-web-applications.md)中有详细说明。

此处详细介绍的Facebook类型Web应用程序示例有：

* 如何通过7个步骤创建Facebook应用程序。 请参阅[快速开始:按7个步骤](#quick-start--creating-a-facebook-application-in-7-steps)创建Facebook应用程序。
* 如何将设置转发到Facebook应用程序。 请参阅[如何将设置转发到Facebook应用程序？](#how-to-forward-settings-to-a-facebook-application-)。
* 如何获取风扇数据。 请参阅[如何获取风扇数据？](#how-to-acquire-fan-data-)。

>[!IMPORTANT]
>
>这些简单的使用案例以示例说明Facebook类型的Web应用程序的功能。

## 建议{#recommendations}

以下限制直接链接到Facebook:

* 必须使用HTTPS构建所有Web应用程序。
* 通过选项卡显示的Facebook应用程序的宽度为810像素。

## 快速开始:按7个步骤创建Facebook应用程序{#quick-start--creating-a-facebook-application-in-7-steps}

此示例提供了如何在Facebook中显示Adobe Campaign构建的应用程序的分步过程。 在这种情况下，我们希望创建一个应用程序，当用户单击应用程序选项卡(**App01**)时，您可以显示&#x200B;**欢迎**&#x200B;消息。

要创建此应用程序，请应用以下步骤：

1. 在Facebook上创建应用程序([https://developers.facebook.com/apps](https://developers.facebook.com/apps))。 有关详细信息，请参阅：[创建Facebook应用程序](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)。

   ![](assets/social_create_facebook_app_002.png)

1. 创建&#x200B;**[!UICONTROL Facebook Connect]**&#x200B;类型外部帐户并输入Facebook应用程序的参数。 有关详细信息，请参阅：[配置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   ![](assets/social_quick_start_2.png)

1. 输入要在Facebook权限请求屏幕上显示的&#x200B;**[!UICONTROL Terms of service]**&#x200B;和&#x200B;**[!UICONTROL Privacy policy]**&#x200B;链接。 有关详细信息，请参阅：[输入服务条款和隐私策略链接](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links)。

   ![](assets/social_quick_start_1.png)

1. 在Adobe Campaign中创建Facebook类型的Web应用程序。 有关详细信息，请参阅：[创建Facebook类型的Web应用程序](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)。

   ![](assets/social_webapp_005.png)

1. 编辑您的Web应用程序。 在此示例中，我们添加了&#x200B;**[!UICONTROL Page]**&#x200B;活动并为其定义了标题。

   ![](assets/social_quick_start_4.png)

1. 部署应用程序。

   ![](assets/social_webapp_004.png)

1. 配置您的Facebook应用程序，使其显示为Facebook页面上的一个选项卡。 有关详细信息，请参阅：[配置Facebook选项卡](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs)。

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

检查&#x200B;**App01**&#x200B;应用程序的选项卡是否显示在您的Facebook页面上。 单击它应调用&#x200B;**欢迎**&#x200B;消息。

![](assets/social_webapp_042.png)

## 如何将设置转发到Facebook应用程序？{#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>符合[创建Facebook应用程序](../../social/using/creating-a-facebook-application.md)中详细的配置步骤。

在示例1中，我们根据&#x200B;**[!UICONTROL Fan of the page]**&#x200B;字段中的值个性化了Facebook页面的显示。 也可以处理&#x200B;**[!UICONTROL Application settings]**&#x200B;字段。 此字段允许您通过Facebook恢复由Adobe Campaign生成的链接中包含的数据。

让我们举一个决定发送电子邮件公司的活动。 在该投放中，有指向Facebook应用程序的链接。 由于在URL末尾添加了&#x200B;**[!UICONTROL app_data]**&#x200B;参数，此链接是个性化的。 此参数的值可以是反映客户重要性的指标。 在我们的示例中，**[!UICONTROL app_data]**&#x200B;参数的值为&#x200B;**[!UICONTROL big]**（重要客户）和&#x200B;**[!UICONTROL small]**（不重要客户）。

一旦个性化，URL将如下所示：

* `http://<path of the Facebook application>&app_data=big` （对于重要客户）
* `http://<path of the Facebook application>&app_data=small` （对于不太重要的客户）

在Facebook转发给Adobe Campaign的匿名数据中，收集&#x200B;**[!UICONTROL Application parameters]**&#x200B;字段的值，使Adobe Campaign能够基于此参数个性化应用程序显示。

如果用户是重要客户（**[!UICONTROL app_data]**&#x200B;参数的值为&#x200B;**[!UICONTROL big]**），将显示以下图像：

![](assets/social_webapp_017.png)

如果用户不是重要客户（**[!UICONTROL app_data]**&#x200B;参数的值为&#x200B;**[!UICONTROL small]**），则显示以下图像：

![](assets/social_webapp_016.png)

要重新创建此用例，我们创建了一个由以下元素组成的Web应用程序：

* 基于&#x200B;**[!UICONTROL Application parameter]**&#x200B;字段的&#x200B;**[!UICONTROL Test]**&#x200B;活动。
* 包含要根据&#x200B;**[!UICONTROL Application parameter]**&#x200B;字段的值显示的图像的两页。

![](assets/social_webapp_018.png)

## 如何获取风扇数据？{#how-to-acquire-fan-data-}

>[!IMPORTANT]
>
>符合[创建Facebook应用程序](../../social/using/creating-a-facebook-application.md)中详细的配置步骤。

此示例向您展示如何联系Facebook用户和优惠，让他们共享其用户档案信息。 让我们举一个公司的例子，它想要获取潜在客户，并在其Facebook页面上组织竞赛以吸引他们。

每当用户单击&#x200B;**[!UICONTROL App03]**&#x200B;选项卡时，我们会询问他们是否希望参加比赛。

![](assets/social_webapp_fb_000.png)

如果他们决定参加竞赛，我们会优惠他们共享其用户档案信息。

![](assets/social_webapp_021.png)

如果用户同意共享其信息，将显示以下屏幕。

![](assets/social_webapp_022.png)

要构建此用例，我们创建了一个包含以下元素的Web应用程序：

* **[!UICONTROL Test]** 活动
* 三页
* **[!UICONTROL Access control]**&#x200B;活动
* **[!UICONTROL Pre-loading]** 活动
* **[!UICONTROL Save]** 活动
* **[!UICONTROL End]**&#x200B;活动

![](assets/social_webapp_019.png)

### 测试活动{#test-activity}

**[!UICONTROL Test]**&#x200B;活动基于&#x200B;**[!UICONTROL ID]**&#x200B;和&#x200B;**[!UICONTROL Application parameters]**&#x200B;字段。

![](assets/social_webapp_023.png)

它由三个分支组成：

* **[!UICONTROL identifier (UID) is empty]** :只有当用户已同意共享其信息时，Facebook才会转发该标识符。通过&#x200B;**[!UICONTROL Test]**&#x200B;活动的第一个分支，您只能向从未输入过（即ID为空的）用户提供竞赛。
* **[!UICONTROL application parameter equals 'thanks']** :要避开链接到Facebook的显示错误，Web应用程序结束页面会指向Facebook应用程序的URL， **[!UICONTROL app_data]** 该应用程序的URL将参 **[!UICONTROL thanks]** 数添加到该值中(有关详细信息，请参阅： [结束活动](#end-activity))。第二个分支可让您了解用户是否来自第一个分支的&#x200B;**[!UICONTROL End]**&#x200B;活动（并且刚刚进入竞争对手），以显示感谢信。 有关使用其他URL参数的详细信息，请参阅：[如何将设置转发到Facebook应用程序？](#how-to-forward-settings-to-a-facebook-application-)。
* **[!UICONTROL Default branch]** :如果用户已在上一日期（应用程序参数不同于）输入竞赛信息（ID已输入），则我们将显示一个页面， **[!UICONTROL thanks]**&#x200B;表示他们已输入。

### 竞赛页面{#competition-page}

要避开链接到Facebook的显示错误，您还需要在竞争页面的&#x200B;**[!UICONTROL Window]**&#x200B;字段中选择&#x200B;**[!UICONTROL Parent window]**&#x200B;或&#x200B;**[!UICONTROL In the top window]**。

![](assets/social_webapp_028.png)

### 访问控制活动{#access-control-activity}

**[!UICONTROL Access control]**&#x200B;活动允许您在用户进入竞争时显示Facebook权限请求页。 如果他们同意共享其信息，则会在预加载中恢复该信息。 有关详细信息，请参阅：[预加载活动](#pre-loading-activity)。

如果您之前在创建Web应用程序时输入了外部帐户（请参阅[创建Facebook类型的Web应用程序](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)），则无需编辑活动。 否则，转到&#x200B;**[!UICONTROL Application]**&#x200B;字段，并选择链接到Facebook应用程序的外部帐户。

![](assets/social_webapp_024.png)

### 预加载活动{#pre-loading-activity}

选择要用于预加载的数据源：

* **[!UICONTROL Marketing database]** :此选项允许您通过Adobe Campaign数据库预载数据。
* **[!UICONTROL Facebook]** :此选项允许您使用Facebook预加载数据。

![](assets/social_webapp_029.png)

**营销数据库**

通过此选项，可以恢复用户档案表中存在的访客的数据。 验证基于用户单击Facebook应用程序选项卡时恢复的外部Facebook ID。 如果在&#x200B;**[!UICONTROL Pre-loading]**&#x200B;活动后添加表单，则预加载包含数据库中信息的字段。

![](assets/social_webapp_030.png)

>[!NOTE]
>
>有关通过预加载库访问Adobe Campaign数据的详细信息，请参阅[本节](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

**Facebook**

此选项允许您定义要收集的Facebook用户档案信息（用户同意共享的信息），以便保存该信息。

![](assets/social_webapp_025.png)

使用&#x200B;**[!UICONTROL Database information]**&#x200B;选项可以收集以下数据：

* **[!UICONTROL External ID]**:用户ID
* **[!UICONTROL Gender]**:用户性别
* **[!UICONTROL Verified]** :此字段指定用户是否具有经过验证的Facebook帐户。
* **[!UICONTROL Full name]**:用户全名
* **[!UICONTROL First name]**:用户名
* **[!UICONTROL Last name]**:用户姓
* **[!UICONTROL Language]**:用户语言

您还可以通过选中相应的复选框来收集用户档案照片、好友的列表、电子邮件地址、出生日期、兴趣和位置。

单击&#x200B;**[!UICONTROL Ok]**&#x200B;前，选中&#x200B;**[!UICONTROL I agree to comply with Facebook conditions of use]**&#x200B;框。

>[!NOTE]
>
>如果在&#x200B;**[!UICONTROL Private information]**&#x200B;部分选中一个或多个框，则Facebook权限请求屏幕将自动显示此数据的访问请求。
>
>为了您收集所选信息，用户必须同意共享它。
>
>如果您希望两种预加载类型(通过Adobe Campaign和通过Facebook)都添加两个预加载框。

### 保存活动{#save-activity}

**[!UICONTROL Save]**&#x200B;活动允许您将在访客表的上一阶段收集到的信息存储在其中。

如果用户档案已存在于访客表中，则其数据将使用收集的新数据进行更新。

如果用户档案库中不存在访客，且已收集Facebook用户的电子邮件地址，则将在访客表中创建该数据。

![](assets/social_webapp_026.png)

1. 在&#x200B;**[!UICONTROL Visitor creation folder]**&#x200B;字段中，选择将在其中创建用户档案的文件夹。 如果是Facebook类型的Web应用程序，则默认的创建文件夹为&#x200B;**[!UICONTROL Visitors]**。
1. 在&#x200B;**[!UICONTROL Reconciliation mode]**&#x200B;字段中，选择要使用的对帐模式：

   * **[!UICONTROL Automatic]** :对帐基于电子邮件、姓氏、名字和出生日期进行。
   * **[!UICONTROL Manual]** :请选择一个或多个合并关键项。
   * **[!UICONTROL None]** :不会进行和解。

1. 在&#x200B;**[!UICONTROL Mapping]**&#x200B;字段中，选择要执行对帐的模式。

   >[!IMPORTANT]
   >
   >确保在投放映射中正确输入&#x200B;**[!UICONTROL Social networks]**&#x200B;选项卡的字段。 投放映射通过&#x200B;**[!UICONTROL Administration > Campaign management > Target mappings]**&#x200B;节点访问。

1. 您可以选择要对帐的搜索文件夹和新用户档案的创建文件夹。 如果字段为空，则在映射模式的默认文件夹中搜索并创建用户档案。

### 结束活动 {#end-activity}

要避开链接到Facebook的显示错误，您需要选中&#x200B;**[!UICONTROL Use an external URL]**&#x200B;框并输入Facebook应用程序的URL，后跟&#x200B;**[!UICONTROL app_data]**&#x200B;参数和值。 此值将用在&#x200B;**[!UICONTROL Test]**&#x200B;活动中，以检测用户是否刚刚进入竞争对手，并显示感谢信（如果适用）。 有关详细信息，请参阅：[测试活动](#test-activity)。

在我们的示例中，使用的值为&#x200B;**thanks**。

![](assets/social_webapp_027.png)

### 访客{#details-screen-of-a-visitor}的详细信息屏幕

就像Twitter关注者一样(请参阅：[操作原则](../../social/using/publishing-on-twitter.md#operating-principle))，恢复的Facebook用户档案存储在访客表中。 要显示访客的列表，请转到&#x200B;**[!UICONTROL Profiles and Targets > Visitors]**&#x200B;节点。

同意共享其用户档案信息的每位Facebook潜在客户都会添加到访客列表。 如果在&#x200B;**[!UICONTROL Pre-load]**&#x200B;活动中选中&#x200B;**[!UICONTROL Friends]**&#x200B;框(请参阅：[预加载活动](#pre-loading-activity))，还会添加好友。

![](assets/social_webapp_037.png)

在“访客详细信息”窗口的&#x200B;**[!UICONTROL Summary]**&#x200B;部分，**[!UICONTROL New Contact]**&#x200B;指示器有两个可能的状态：

![](assets/social_webapp_038.png)

如果显示绿色复选标记，则表示访客未与任何收件人协调。 在这种情况下，将在收件人的列表中创建新用户档案。

![](assets/social_webapp_039.png)

红十字表示访客与收件人和解。 单击&#x200B;**[!UICONTROL Recipient]**&#x200B;字段右侧的放大镜可显示匹配的收件人。

![](assets/social_webapp_040.png)

转到收件人的详细信息窗口以显示匹配访客（如果适用）。 选择&#x200B;**[!UICONTROL Others]**&#x200B;选项卡，然后在&#x200B;**[!UICONTROL Web identities]**&#x200B;部分中按住多次并单击访客的名称。

![](assets/social_webapp_041.png)

访客详细信息页面的&#x200B;**[!UICONTROL Activities]**&#x200B;屏幕包含以下信息：

* “Open Graph”类型风扇活动:播放的音乐、观看的视频、阅读的文章以及安装的应用程序的不足（Deezer、Spotify、Dailymotion、Yahoo News等）

   ![](assets/social_facebook_activities.png)

* “赞”和粉丝根据Adobe Campaign发送的投放添加的评论
* 粉丝喜欢的页
* 风扇的登记

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >为了Adobe Campaign收集风扇的登记，您需要单击服务配置屏幕上的&#x200B;**[!UICONTROL Subscribe]**&#x200B;按钮。 有关详细信息，请参阅[配置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

## 如何使用Facebook用户档案数据{#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}预加载表单的字段

**[!UICONTROL Social Marketing]**&#x200B;应用程序还允许您向表单中添加按钮，以使用Facebook预加载信息显示用户档案字段。 此选项在所有Web应用程序模板(**[!UICONTROL Page]**&#x200B;类型活动)中都有详细说明，请参阅[本节](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)。

![](assets/social_webapp_035.png)

>[!NOTE]
>
>在使用此函数进行开始之前，您需要创建一个Facebook应用程序和一个&#x200B;**[!UICONTROL Facebook Connect]**&#x200B;类型外部帐户。 有关详细信息，请参阅[配置外部帐户](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

