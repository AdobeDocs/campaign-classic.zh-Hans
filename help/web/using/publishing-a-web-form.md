---
product: campaign
title: 发布 Web 窗体
description: 发布 Web 窗体
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 2%

---

# 发布 Web 窗体{#publishing-a-web-form}

## 预加载表单数据{#pre-loading-the-form-data}

如果希望通过Web窗体更新存储在数据库中的用户档案，则可以使用预加载框。 利用预加载框，可指示如何在数据库中查找要更新的记录。

可以使用以下识别方法：

* **[!UICONTROL Adobe Campaign Encryption]**

   此加密方法使用加密的Adobe Campaign标识符(ID)。 此方法仅适用于Adobe Campaign对象，且加密的ID只能由Adobe Campaign平台生成。

   使用此方法时，您需要通过添加&#x200B;**`<%=escapeUrl(recipient.cryptedId) %>`**&#x200B;参数来调整表单的URL以将其投放到电子邮件地址。 有关更多信息，请参阅[通过电子邮件传送表单](#delivering-a-form-via-email)。

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   此加密方法使用外部提供的标识符(ID)，该标识符链接到由Adobe Campaign和外部提供商共享的密钥。 **[!UICONTROL Des key]**&#x200B;字段允许您输入此加密密钥。

* **[!UICONTROL List of fields]**

   此选项允许您从表单当前上下文中的字段进行选择，这些字段将用于在数据库中查找相应的用户档案。

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   可以通过&#x200B;**[!UICONTROL Parameters]**&#x200B;选项卡将字段添加到表单属性（请参阅[添加参数](../../web/using/defining-web-forms-properties.md#adding-parameters)）。 它们以URL或输入区域的形式放置。

   >[!CAUTION]
   >
   >所选字段中的数据未加密。 不得以加密形式提供它，因为如果选择&#x200B;**[!UICONTROL Field list]**&#x200B;选项，Adobe Campaign将无法解密它。

   在以下示例中，用户档案预加载基于电子邮件地址。

   该URL可以包含未加密的电子邮件地址，在这种情况下，用户可以直接访问与他们相关的页面。

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   否则，将要求他们输入密码。

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >如果列表中指定了多个字段，则&#x200B;**ALL FIELDS**&#x200B;的数据必须与数据库中存储的数据匹配，才能更新用户档案。 否则，将创建新用户档案。
   > 
   >此函数对Web应用程序特别有用，但不建议用于公共表单。 选定的访问控制选项必须是“启用访问控制”。

如果您不想更新用户档案，则必须选择&#x200B;**[!UICONTROL Skip preloading if no ID]**&#x200B;选项。 在这种情况下，输入的每个用户档案都将在表单获得批准后添加到数据库中。 例如，当表单发布到网站时，会使用此选项。

**[!UICONTROL Auto-load data referenced in the form]**&#x200B;选项允许您自动预载与表单中的输入和合并字段匹配的数据。 但是，在&#x200B;**[!UICONTROL Script]**&#x200B;和&#x200B;**[!UICONTROL Test]**&#x200B;活动中引用的数据并不相关。 如果未选择此选项，则需要使用&#x200B;**[!UICONTROL Load additional data]**&#x200B;选项定义字段。

**[!UICONTROL Load additional data]**&#x200B;选项允许您添加表单页面中未使用但仍将预加载的信息。

例如，您可以预加载收件人的性别，并通过测试框自动将其定向到相应的页面。

![](assets/s_ncs_admin_survey_preload_ex.png)

## 管理Web窗体投放和跟踪{#managing-web-forms-delivery-and-tracking}

创建、配置和发布表单后，您可以交付该表单并跟踪用户响应。

### 表单{#life-cycle-of-a-form}的生命周期

表单生命周期有三个阶段：

1. **正在编辑的表单**

   这是最初的设计阶段。 创建新表单后，该表单将处于编辑阶段。 出于测试目的，访问表单时，需要在其URL中使用参数&#x200B;**[!UICONTROL __uuid]**。 此URL可在&#x200B;**[!UICONTROL Preview]**&#x200B;子选项卡中访问。 请参阅[表单URL参数](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

   >[!CAUTION]
   >
   >只要对表单进行编辑，其访问URL就是特殊的URL。

1. **联机表单**

   设计阶段完成后，即可提交表单。 首先，它需要发布。 有关更多信息，请参阅[发布表单](#publishing-a-form)。

   表单将为&#x200B;**[!UICONTROL Live]**，直到其过期。

   >[!CAUTION]
   >
   >要传送，调查的URL不得包含&#x200B;**[!UICONTROL __uuid]**&#x200B;参数。

1. **表单不可用**

   表单关闭后，投放阶段即告结束，表单将变得不可用：用户无法再访问该库。

   到期日期可在表单属性窗口中定义。 有关更多信息，请参阅[使表单联机可用](#making-a-form-available-online)

表单的发布状态显示在表单列表中。

![](assets/s_ncs_admin_survey_status.png)

### 发布表单{#publishing-a-form}

要更改表单的状态，您需要发布它。 为此，请单击Web窗体列表上方的&#x200B;**[!UICONTROL Publication]**&#x200B;按钮，然后在下拉框中选择状态。

![](assets/webapp_publish_webform.png)

### 联机提供表单{#making-a-form-available-online}

要供用户访问，表单必须在生产中并启动，即在其有效期内。 有效日期通过表单的&#x200B;**[!UICONTROL Properties]**&#x200B;链接输入。

* 使用&#x200B;**[!UICONTROL Project]**&#x200B;部分中的字段输入表单的开始日期和结束日期。

   ![](assets/webapp_availability_date.png)

* 单击&#x200B;**[!UICONTROL Personalize the message displayed if the form is closed...]**&#x200B;链接，以定义用户在表单无效时尝试访问该表单时要显示的错误消息。

   请参阅[表单](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form)的辅助功能。

### 通过电子邮件{#delivering-a-form-via-email}传送表单

通过电子邮件发送邀请时，可以使用&#x200B;**[!UICONTROL Adobe Campaign Encryption]**&#x200B;选项进行数据协调。 为此，请转到投放向导，并通过添加以下参数来调整表单的链接：

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

在这种情况下，数据存储的协调密钥必须是收件人的加密标识符。 有关更多信息，请参阅[预加载表单数据](#pre-loading-the-form-data)。

在这种情况下，您需要选中记录框中的&#x200B;**[!UICONTROL Update the preloaded record]**&#x200B;选项。 有关更多信息，请参阅[保存Web窗体答案](../../web/using/web-forms-answers.md#saving-web-forms-answers)。

![](assets/s_ncs_admin_survey_save_box_option.png)

### 日志响应{#log-responses}

可以在专用选项卡中激活响应跟踪，以监控Web表单的影响。 要执行此操作，请单击表单属性窗口中的&#x200B;**[!UICONTROL Advanced parameters...]**&#x200B;链接，然后选择&#x200B;**[!UICONTROL Log responses]**&#x200B;选项。

![](assets/s_ncs_admin_survey_trace.png)

此时会显示&#x200B;**[!UICONTROL Responses]**&#x200B;选项卡，用于查看答复者的身份。

![](assets/s_ncs_admin_survey_trace_tab.png)

选择收件人并单击&#x200B;**[!UICONTROL Detail...]**&#x200B;按钮以查看提供的响应。

![](assets/s_ncs_admin_survey_trace_edit.png)

您可以处理查询中提供的响应日志，例如，在发送提醒时仅定向非应答者，或仅向应答者提供特定通信。

>[!NOTE]
>
>要完整跟踪提供的响应，请导出响应并查看或创建专用报告，请使用可选的&#x200B;**Survey**&#x200B;模块。 如需详细信息，请参阅[此部分](../../web/using/about-surveys.md)。
