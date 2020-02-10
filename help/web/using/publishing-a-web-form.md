---
title: 发布Web表单
seo-title: 发布Web表单
description: 发布Web表单
seo-description: null
page-status-flag: never-activated
uuid: 37222829-1d56-438c-a4ca-878925debcb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: f4322902-c72d-4443-9c30-09add4c615a3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 发布Web表单{#publishing-a-web-form}

## 预加载表单数据 {#pre-loading-the-form-data}

如果您希望通过Web表单更新存储在数据库中的配置文件，则可以使用预加载框。 通过预加载框，可以指示如何查找要在数据库中更新的记录。

可以使用以下识别方法：

* **[!UICONTROL Adobe Campaign Encryption]**

   此加密方法使用加密的Adobe Campaign标识符(ID)。 此方法仅适用于Adobe Campaign对象，且加密ID只能由Adobe Campaign平台生成。

   使用此方法时，您需要调整表单的URL，以通过添加参数来传送到电子邮件地 **`<%=escapeUrl(recipient.cryptedId) %>`** 址。 有关此问题的详细信息，请参 [阅通过电子邮件传送表单](#delivering-a-form-via-email)。

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   此加密方法使用外部提供的标识符(ID)，该标识符与Adobe Campaign和外部提供者共享的密钥相关联。 该字 **[!UICONTROL Des key]** 段允许您输入此加密密钥。

* **[!UICONTROL List of fields]**

   此选项允许您从表单当前上下文中的字段中进行选择，这些字段将用于在数据库中查找相应的配置文件。

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   可以通过选项卡将字段添加到表单 **[!UICONTROL Parameters]** 属性中(请参阅 [添加参数](../../web/using/defining-web-forms-properties.md#adding-parameters))。 它们位于表单URL或输入区域中。

   >[!CAUTION]
   >
   >所选字段中的数据未加密。 不得以加密的形式提供它，因为如果选择了该选项，Adobe Campaign将无法解 **[!UICONTROL Field list]** 密它。

   在以下示例中，配置文件预加载基于电子邮件地址。

   该URL可以包含未加密的电子邮件地址，在这种情况下，用户可以直接访问与他们相关的页面。

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   否则，将要求他们输入密码。

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >如果列表中指定了多个字段，则 **ALL FIELDS** （所有字段）的数据必须与存储在数据库中的数据匹配，才能更新配置文件。 否则，将创建新配置文件。
   > 
   >此函数对于Web应用程序特别有用，但对于公共表单不建议使用。 选定的访问控制选项必须为“启用访问控制”。

如果 **[!UICONTROL Skip preloading if identification is empty]** 您不想更新配置文件，则必须选择此选项。 在这种情况下，输入的每个配置文件都将在批准表单后添加到数据库。 例如，在网站上发布表单时，会使用此选项。

通过 **[!UICONTROL Auto-load data referenced in the form]** 此选项，可自动预载与表单中的输入和合并字段相匹配的数据。 但是，在活动中引用 **[!UICONTROL Script]** 的数 **[!UICONTROL Test]** 据并不令人关注。 如果未选择此选项，则需要使用该选项定义字 **[!UICONTROL Load additional data]** 段。

通过 **[!UICONTROL Load additional data]** 此选项，您可以添加表单页面中未使用的信息，但仍将预加载这些信息。

例如，您可以预加载收件人的性别，并通过测试框将其自动引导到相应的页面。

![](assets/s_ncs_admin_survey_preload_ex.png)

## 管理Web表单交付和跟踪 {#managing-web-forms-delivery-and-tracking}

创建、配置和发布表单后，您便可以提交并跟踪用户答复。

### 表单的生命周期 {#life-cycle-of-a-form}

表单的生命周期有三个阶段：

1. **正在编辑的表单**

   这是最初的设计阶段。 创建新表单时，该表单处于编辑阶段。 访问表单仅用于测试目的，然后要求在其URL **[!UICONTROL __uuid]** 中使用该参数。 此URL可在子选项卡 **[!UICONTROL Preview]** 中访问。 请参 [阅表单URL参数](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

   >[!CAUTION]
   >
   >只要正在编辑表单，其访问URL就是一个特殊URL。

1. **在线表单**

   设计阶段完成后，可以提交表单。 首先，它需要发布。 有关此内容的详细信息，请参 [阅发布表单](#publishing-a-form)。

   表单将一直保 **[!UICONTROL Live]** 持到期。

   >[!CAUTION]
   >
   >要传送，调查的URL不得包含该参 **[!UICONTROL __uuid]** 数。

1. **表单不可用**

   关闭表单后，交付阶段即结束，表单将变得不可用：用户不再可以访问它。

   到期日期可在表单属性窗口中定义。 有关此内容的详细信息，请参 [阅联机提供表单](#making-a-form-available-online)

表单的发布状态显示在表单列表中。

![](assets/s_ncs_admin_survey_status.png)

### 发布表单 {#publishing-a-form}

要更改表单的状态，您需要发布它。 为此，请单击Web **[!UICONTROL Publication]** 表单列表上方的按钮，然后在下拉框中选择状态。

![](assets/webapp_publish_webform.png)

### 联机提供表单 {#making-a-form-available-online}

要供用户访问，表单必须在生产中并开始，即在有效期内。 有效日期通过表单的 **[!UICONTROL Properties]** 链接输入。

* 使用部分中的字 **[!UICONTROL Project]** 段输入表单的开始日期和结束日期。

   ![](assets/webapp_availability_date.png)

* 单击链 **[!UICONTROL Personalize the message displayed if the form is closed...]** 接以定义当用户尝试访问表单无效时要显示的错误消息。

   请参 [阅表单的辅助功能](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form)。

### 通过电子邮件传送表单 {#delivering-a-form-via-email}

通过电子邮件发送邀请时，您可以使用 **[!UICONTROL Adobe Campaign Encryption]** 数据协调选项。 为此，请转到交付向导，并通过添加以下参数来调整表单的链接：

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

在这种情况下，数据存储的对帐密钥必须是接收方的加密标识符。 有关详细信息，请参 [阅预加载表单数据](#pre-loading-the-form-data)。

在这种情况下，您需要选中记录 **[!UICONTROL Update the preloaded record]** 框中的选项。 有关详细信息，请参阅保 [存Web表单答案](../../web/using/web-forms-answers.md#saving-web-forms-answers)。

![](assets/s_ncs_admin_survey_save_box_option.png)

### 日志响应 {#log-responses}

可以在专用选项卡中激活响应跟踪，以监控Web表单的影响。 为此，请单击表单属 **[!UICONTROL Advanced parameters...]** 性窗口中的链接，然后选择 **[!UICONTROL Log responses]** 选项。

![](assets/s_ncs_admin_survey_trace.png)

该选 **[!UICONTROL Responses]** 项卡显示为允许您查看受访者的身份。

![](assets/s_ncs_admin_survey_trace_tab.png)

选择收件人，然后单击 **[!UICONTROL Detail...]** 按钮以查看提供的答复。

![](assets/s_ncs_admin_survey_trace_edit.png)

您可以处理查询中提供的响应日志，例如，在发送提醒时，仅将目标定向为非应答者，或仅向应答者提供特定通信。

>[!NOTE]
>
>要完整跟踪提供的响应，请导出响应并查看或创建专用报告，请使用可选的 **Survey** 模块。 如需详细信息，请参阅[此部分](../../web/using/about-surveys.md)。

