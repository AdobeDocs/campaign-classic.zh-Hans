---
solution: Campaign Classic
product: campaign
title: 向Adobe Campaign Classic发送电子邮件
description: 了解电子邮件投放参数
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 8%

---


# 发送电子邮件{#sending-an-email}

要批准您的电子邮件并将其发送给要创建的收件人，请单击&#x200B;**[!UICONTROL Send]**。

验证和发送投放时的详细过程将在以下各节中介绍：

* [验证投放](../../delivery/using/steps-validating-the-delivery.md)
* [发送投放](../../delivery/using/steps-sending-the-delivery.md)

以下各节详细介绍了特定于电子邮件发送的参数。

## 密件抄送{#archiving-emails}

Adobe Campaign允许您通过密送将密送电子邮件地址添加到邮件目标，从而将电子邮件存储在外部系统上。 激活该选项后，将为此投放保留所有已发送消息的确切副本。

有关电子邮件密件抄送配置和最佳实践的详细信息，请参阅[本节](../../installation/using/email-archiving.md)。

>[!NOTE]
>
>密送电子邮件是可选功能。 请核实您的许可协议并联系您的帐户管理员以将其激活。

创建新投放或投放模板时，默认情况下不启用电子邮件密送。 您需要在电子邮件投放或投放模板级别手动启用它。

要为电子邮件投放模板启用电子邮件密送，请执行以下步骤：

1. 转到&#x200B;**[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]**&#x200B;或&#x200B;**[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**。
1. 选择您选择的投放或重复现成的&#x200B;**电子邮件投放**&#x200B;模板，然后选择复制的模板。
1. 单击&#x200B;**属性**&#x200B;按钮。
1. 选择 **[!UICONTROL Delivery]** 选项卡。
1. 选中&#x200B;**电子邮件密送**&#x200B;选项。 每个投放基于此模板发送的所有邮件的副本将发送到已配置的电子邮件密送地址。

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >如果打开并点击发送到密送地址的电子邮件，则在发送分析的&#x200B;**[!UICONTROL Total opens]**&#x200B;和&#x200B;**[!UICONTROL Clicks]**&#x200B;中会考虑这一情况，这可能会导致一些错误计算。

## 生成镜像页面{#generating-the-mirror-page}

镜像页面是可通过Web浏览器在线访问的HTML页面。 其内容与电子邮件内容相同。

默认情况下，如果链接插入到邮件内容中，则会生成镜像页面。 有关个性化块插入的详细信息，请参阅[个性化块](../../delivery/using/personalization-blocks.md)。

在投放属性中，使用&#x200B;**[!UICONTROL Validity]**&#x200B;选项卡的&#x200B;**[!UICONTROL Mode]**&#x200B;字段可以修改此页面的生成模式。

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>必须为要创建投放的镜像页面定义HTML内容。

除了默认模式之外，还提供以下选项：

* **[!UICONTROL Force the generation of the mirror page]** :即使镜像页面中未插入指向该投放的链接，也会创建镜像页面。
* **[!UICONTROL Do not generate the mirror page]** :不生成镜像页面，即使投放中存在链接也是如此。
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** :通过此选项，您可以在镜像页面日志窗口中访问包含个性化信息的投放内容。为此，在投放结束后，单击&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡，并选择要视图其镜像页面的收件人行。 单击&#x200B;**[!UICONTROL Display the mirror page for this message...]**&#x200B;链接。

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## 管理弹回电子邮件{#managing-bounce-emails}

投放参数的&#x200B;**[!UICONTROL SMTP]**&#x200B;选项卡允许您配置弹回邮件的管理。

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

默认情况下，退回电子邮件会在平台的默认错误框中接收，但您可以为投放定义特定错误地址。

您还可以从此屏幕定义特定地址，以调查在应用程序无法自动限定弹出邮件的原因。 对于每个字段，“添加个性化字段”图标允许您添加个性化参数。

## 字符编码{#character-encoding}

在投放参数的&#x200B;**[!UICONTROL SMTP]**&#x200B;选项卡中，**[!UICONTROL Character encoding]**&#x200B;部分允许您设置特定编码。

默认编码为UTF-8。 如果某些收件人的电子邮件提供者不支持UTF-8标准编码，您可能希望设置特定编码以向电子邮件的收件人正确显示特殊字符。

例如，您要发送包含日文字符的电子邮件。 为确保所有字符都能正确显示给日本的收件人，您可能希望使用支持日语字符的编码，而不是标准UTF-8。

为此，请在&#x200B;**[!UICONTROL Character encoding]**&#x200B;部分选择&#x200B;**[!UICONTROL Force the encoding used for messages]**&#x200B;选项，并从显示的下拉列表中选择编码。

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## 添加SMTP头{#adding-smtp-headers}

可以向投放添加SMTP头。 为此，请使用投放中&#x200B;**[!UICONTROL SMTP]**&#x200B;选项卡的相关部分。

在此窗口中输入的脚本必须在以下表单中引用每行一个标题：**name:value**。

如有必要，将自动对值进行编码。

>[!CAUTION]
>
>高级用户可随时添加脚本以插入其他 SMTP 标头。
>
>此脚本的语法必须符合此内容类型的要求：没有未使用的空格，没有空行等。
