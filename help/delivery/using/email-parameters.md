---
product: campaign
title: 电子邮件参数
description: 了解特定于电子邮件投放的选项和设置
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Email
role: User, Developer, Data Engineer
exl-id: 1bb36e71-9f1a-4553-b266-eca3f48688e2
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 14%

---

# 电子邮件参数 {#email-parameters}

本节介绍特定于电子邮件投放的选项和参数。

## 电子邮件密件抄送 {#email-bcc}

通过Adobe Campaign，您只需将密件抄送电子邮件地址添加到消息目标，即可通过密件抄送在外部系统上存储电子邮件。

激活该选项后，将为此投放保留所有已发送消息的精确副本。

有关电子邮件密送配置和最佳实践的更多信息，请参阅 [本节](../../installation/using/email-archiving.md).

>[!NOTE]
>
>电子邮件密送是一项可选功能。 请核实您的许可协议并联系您的帐户管理员以将其激活。

创建新投放或投放模板时，默认情况下不启用电子邮件密送。 您需要在电子邮件投放或投放模板级别手动启用它。

>[!NOTE]
>
>如果您使用具有增强MTA的电子邮件密送，则会为所有投放自动启用此选项。

要为电子邮件投放模板启用电子邮件密送，请执行以下步骤：

1. 转到 **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** 或 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. 选择您选择的投放或复制现成的投放内容 **电子邮件投放** 模板，然后选择复制的模板。
1. 单击 **属性** 按钮。
1. 选择 **[!UICONTROL Delivery]** 选项卡。
1. 查看 **电子邮件密送** 选项。 基于此模板每次投放的所有已发送消息的副本将发送到已配置的电子邮件密件抄送地址。

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>如果发送到密件抄送地址的电子邮件被打开并单击通过，则中会考虑这一点 **[!UICONTROL Total opens]** 和 **[!UICONTROL Clicks]** ，这可能会导致某些计算错误。

## 选择消息格式 {#selecting-message-formats}

您可以更改已发送电子邮件的格式。 为此，请编辑投放属性并单击 **[!UICONTROL Delivery]** 选项卡。

![](assets/s_ncs_user_wizard_email_param.png)

在窗口的下半部分选择电子邮件的格式：

* **[!UICONTROL Use recipient preferences]** （默认模式）

  根据收件人用户档案中存储的数据(默认存储在 **[!UICONTROL email format]** 字段(@emailFormat)。 如果收件人希望以特定格式接收消息，则会将该格式用于发送的邮件。如果未填写该字段，则会发送multipart-alternative消息（请参阅下文）。

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

  该消息包含两种格式：文本和HTML。 接收时显示的格式取决于收件人邮件软件的配置(multipart-alternative)。

  >[!IMPORTANT]
  >
  >此选项包括文档的两个版本。 因此，它会影响投放率，因为邮件大小更大。

* **[!UICONTROL Send all messages in text format]**

  消息以文本格式发送。 不会发送HTML格式，但仅当收件人单击消息时，才会将其用于镜像页面。

>[!NOTE]
>
>有关定义电子邮件内容的更多信息，请参阅 [本节](defining-the-email-content.md).

## 生成镜像页面 {#generating-mirror-page}

镜像页面是可通过 Web 浏览器在线访问的 HTML 页面。其内容与电子邮件的内容相同。

默认情况下，如果将链接插入到电子邮件内容中，则会生成镜像页面。有关个性化块插入的更多信息，请参阅 [个性化块](personalization-blocks.md).

在投放属性中， **[!UICONTROL Mode]** 字段 **[!UICONTROL Validity]** 选项卡用于修改此页面的生成模式。

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>必须为要创建的镜像页面的投放定义HTML内容。

除默认模式外，还提供了以下选项：

* **[!UICONTROL Force the generation of the mirror page]**：即使投放中未插入指向镜像页面的链接，也会创建镜像页面。
* **[!UICONTROL Do not generate the mirror page]**：即使投放中存在链接，也不生成镜像页面。
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**：利用此选项可在投放日志窗口中访问带有个性化信息的镜像页面内容。 为此，在投放结束后，单击 **[!UICONTROL Delivery]** 选项卡，然后选择要查看其镜像页面的收件人的行。 单击 **[!UICONTROL Display the mirror page for this message...]** 链接。

  ![](assets/s_ncs_user_wizard_miror_page_link.png)

## 字符编码 {#character-encoding}

在 **[!UICONTROL SMTP]** 选项卡中， **[!UICONTROL Character encoding]** 部分允许您设置特定的编码。

默认编码为UTF-8。 如果某些收件人的电子邮件提供商不支持UTF-8标准编码，您可能需要设置特定编码以正确向电子邮件的收件人显示特殊字符。

例如，您希望发送包含日语字符的电子邮件。 为确保向日本的收件人正确显示所有字符，您可能需要使用支持日语字符的编码而不是标准UTF-8。

要执行此操作，请选择 **[!UICONTROL Force the encoding used for messages]** 中的选项 **[!UICONTROL Character encoding]** 部分，并从显示的下拉列表中选择编码。

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## 管理退回电子邮件 {#managing-bounce-emails}

此 **[!UICONTROL SMTP]** 通过投放参数的选项卡，可以配置退回邮件的管理。

默认情况下，退回的电子邮件会收于 [平台的默认错误框](../../installation/using/deploying-an-instance.md#parameters-for-delivered-emails-parameters-for-delivered-emails)，但您可以为投放定义特定的错误地址。

您还可以从此屏幕定义特定地址，以便调查应用程序无法自动限定这些邮件时退回邮件的原因。 对于每个字段， **添加个性化字段** 图标允许您添加个性化参数。

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

有关退回邮件管理的更多信息，请参阅 [本节](understanding-delivery-failures.md#bounce-mail-management).

## 添加SMTP标头 {#adding-smtp-headers}

可以将SMTP标头添加到投放。 要实现此目的，请使用 **[!UICONTROL SMTP]** 选项卡。

在此窗口中输入的脚本必须引用以下格式中每行一个标头： **name：value**.

如有必要，将自动对值进行编码。

>[!IMPORTANT]
>
>高级用户可随时添加脚本以插入其他 SMTP 标头。
>
>此脚本的语法必须符合此内容类型的要求：没有未使用的空格，没有空行等。
