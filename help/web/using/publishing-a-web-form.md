---
product: campaign
title: 发布 Web 窗体
description: 发布 Web 窗体
feature: Web Forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 1%

---

# 发布 Web 窗体{#publishing-a-web-form}

![](../../assets/common.svg)

## 预加载表单数据 {#pre-loading-the-form-data}

如果要通过Web窗体更新存储在数据库中的用户档案，可以使用预加载框。 通过预加载框，可指示如何查找要在数据库中更新的记录。

可以使用以下识别方法：

* **[!UICONTROL Adobe Campaign Encryption]**

   此加密方法使用加密的Adobe Campaign标识符(ID)。 此方法仅适用于Adobe Campaign对象，并且加密的ID只能由Adobe Campaign平台生成。

   使用此方法时，您需要通过添加 **`<%=escapeUrl(recipient.cryptedId) %>`** 参数。 有关更多信息，请参阅 [通过电子邮件投放表单](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   此加密方法使用外部提供的标识符(ID)，该ID链接到Adobe Campaign和外部提供商共享的密钥。 此 **[!UICONTROL Des key]** 字段可让您输入此加密密钥。

* **[!UICONTROL List of fields]**

   此选项允许您从表单的当前上下文中的字段中进行选择，这些字段将用于查找数据库中的相应概要文件。

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   字段可以通过添加到表单属性 **[!UICONTROL Parameters]** 选项卡(请参阅 [添加参数](defining-web-forms-properties.md#adding-parameters))。 它们以URL或输入区域的形式放置。

   >[!CAUTION]
   >
   >所选字段中的数据未加密。 不得以加密形式提供此密钥，因为Adobe Campaign在以下情况下无法对其进行解密： **[!UICONTROL Field list]** 选项。

   在以下示例中，用户档案预加载基于电子邮件地址。

   URL可以包含未加密的电子邮件地址，在这种情况下，用户可以直接访问与他们有关的页面。

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   否则，将要求他们提供密码。

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >如果列表中指定了多个字段，则数据为 **所有字段** 必须匹配数据库中存储的数据，才能更新用户档案。 否则，将创建一个新配置文件。
   > 
   >此函数对于Web应用程序特别有用，但不建议用于公共表单。 选定的访问控制选项必须是“启用访问控制”。

此 **[!UICONTROL Skip preloading if no ID]** 如果不希望更新用户档案，则必须选择选项。 在这种情况下，在批准表单后，输入的每个用户档案都将添加到数据库中。 例如，在网站上发布表单时，会使用此选项。

此 **[!UICONTROL Auto-load data referenced in the form]** 选项允许您自动预加载与表单中的输入和合并字段匹配的数据。 但是，中引用的数据 **[!UICONTROL Script]** 和 **[!UICONTROL Test]** 活动无关。 如果未选择此选项，您需要使用 **[!UICONTROL Load additional data]** 选项。

此 **[!UICONTROL Load additional data]** 选项允许您添加未在表单页面中使用，但将预加载的信息。

例如，您可以预先加载收件人的性别，并通过测试框自动将他们定向到相应的页面。

![](assets/s_ncs_admin_survey_preload_ex.png)

## 管理Web窗体交付和跟踪 {#managing-web-forms-delivery-and-tracking}

创建、配置和发布表单后，您可以交付表单并跟踪用户响应。

### 表单的生命周期 {#life-cycle-of-a-form}

表单的生命周期分为三个阶段：

1. **正在编辑的表单**

   这是初始设计阶段。 创建新表单时，它处于编辑阶段。 访问表单仅用于测试，因此需要参数 **[!UICONTROL __uuid]** 将在其URL中使用。 此URL可在 **[!UICONTROL Preview]** 子选项卡。 参见 [表单URL参数](defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >只要正在编辑表单，其访问URL就是特殊的URL。

1. **在线表单**

   设计阶段完成后，即可交付表单。 首先，它需要发表。 有关更多信息，请参阅 [发布表单](#publishing-a-form).

   表单将为 **[!UICONTROL Live]** 直到它过期。

   >[!CAUTION]
   >
   >要投放，调查的URL不得包含 **[!UICONTROL __uuid]** 参数。

1. **表单不可用**

   表单关闭后，投放阶段结束，表单不可用：用户无法再访问该表单。

   可在表单属性窗口中定义到期日期。 有关更多信息，请参阅 [在线提供表单](#making-a-form-available-online)

表单的发布状态会显示在表单列表中。

![](assets/s_ncs_admin_survey_status.png)

### 发布表单 {#publishing-a-form}

要更改表单的状态，您需要发布表单。 要执行此操作，请单击 **[!UICONTROL Publication]** 按钮，然后在下拉框中选择状态。

![](assets/webapp_publish_webform.png)

### 在线提供表单 {#making-a-form-available-online}

要使用户访问，表单必须处于生产状态并启动，即在其有效期内。 有效期通过以下方式输入： **[!UICONTROL Properties]** 表单的链接。

* 使用中的字段 **[!UICONTROL Project]** 输入表单的开始日期和结束日期。

   ![](assets/webapp_availability_date.png)

* 单击 **[!UICONTROL Personalize the message displayed if the form is closed...]** 定义用户试图在表单无效时访问表单时显示的错误消息的链接。

   参见 [表单的辅助功能](defining-web-forms-properties.md#accessibility-of-the-form).

### 通过电子邮件投放表单 {#delivering-a-form-via-email}

通过电子邮件发送邀请时，您可以使用 **[!UICONTROL Adobe Campaign Encryption]** 数据协调选项。 为此，请转到投放向导，并通过添加以下参数将链接调整为相应表单：

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

在这种情况下，数据存储的协调密钥必须是收件人的加密标识符。 有关更多信息，请参阅 [预加载表单数据](#pre-loading-the-form-data).

在这种情况下，您需要检查 **[!UICONTROL Update the preloaded record]** 选项。 有关更多信息，请参阅 [保存Web窗体答案](web-forms-answers.md#saving-web-forms-answers).

![](assets/s_ncs_admin_survey_save_box_option.png)

### 日志响应 {#log-responses}

可以在专用选项卡中激活响应跟踪，以监控Web表单的影响。 要执行此操作，请单击 **[!UICONTROL Advanced parameters...]** 链接，然后选择 **[!UICONTROL Log responses]** 选项。

![](assets/s_ncs_admin_survey_trace.png)

此 **[!UICONTROL Responses]** 选项卡显示，允许您查看受访者的身份。

![](assets/s_ncs_admin_survey_trace_tab.png)

选择一个收件人，然后单击 **[!UICONTROL Detail...]** 按钮以查看提供的响应。

![](assets/s_ncs_admin_survey_trace_edit.png)

您可以处理查询中提供的响应日志，例如，在发送提醒时仅定向非回应者，或仅向回应者提供特定通信。
