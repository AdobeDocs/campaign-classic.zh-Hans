---
title: 向Adobe Campaign Classic发送电子邮件
description: 了解Adobe Campaign Classic电子邮件发送的特定参数。
page-status-flag: never-activated
uuid: 791f7a54-3225-46ca-ad6f-6c32e9c62d75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: e2dd8161-fe38-48bf-a288-8ec328b2660e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 9%

---


# 发送电子邮件{#sending-an-email}

要批准您的电子邮件并将其发送给要创建的投放的收件人，请单击 **[!UICONTROL Send]**。

验证和发送投放时的详细过程将在以下各节中介绍：

* [验证投放](../../delivery/using/steps-validating-the-delivery.md)
* [发送投放](../../delivery/using/steps-sending-the-delivery.md)

以下各节详细介绍了特定于电子邮件发送的参数。

## 存档电子邮件 {#archiving-emails}

Adobe Campaign允许您通过密送将密送电子邮件地址添加到邮件目标，从而将电子邮件存储在外部系统上。 激活该选项后，将为此投放保留所有已发送消息的确切副本。

有关配置电子邮件密送的详细信息，请参 [阅此部分](../../installation/using/email-archiving.md)。

>[!NOTE]
>
>此功能属于可选功能。请核实您的许可协议并联系您的帐户管理员以将其激活。

创建新投放或投放模板时，默认情况下不启用电子邮件密送，即使已购买该选项也是如此。 您必须在要使用它的每个投放或模板中手动启用它。

为此请执行以下操作步骤：

1. 转到 **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** 或 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**。
1. 选择您选择的投放或重复现成的电子邮件 **投放模板** ，然后选择复制的模板。
1. Click the **Properties** button.
1. 选择 **[!UICONTROL Delivery]** 选项卡。
1. 选中“ **存档电子邮件** ”框，保留此投放或每个基于此模板投放的所有已发送邮件的副本。

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >如果打开并点击发送到密送地址的电子邮件，则在发送分析和发送中 **[!UICONTROL Total opens]****[!UICONTROL Clicks]** 会考虑这一情况，这可能会导致一些错误计算。

## 生成镜像页面 {#generating-the-mirror-page}

镜像页面是可通过Web浏览器在线访问的HTML页面。 其内容与电子邮件内容相同。

默认情况下，如果链接插入到邮件内容中，则会生成镜像页面。 有关个性化块插入的详细信息，请参阅 [个性化块](../../delivery/using/personalization-blocks.md)。

在投放属性中，选 **[!UICONTROL Mode]** 项卡的字 **[!UICONTROL Validity]** 段允许您修改此页面的生成模式。

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>必须为要创建投放的镜像页面定义HTML内容。

除了默认模式之外，还提供以下选项：

* **[!UICONTROL Force the generation of the mirror page]** :即使镜像页面中未插入指向该投放的链接，也会创建镜像页面。
* **[!UICONTROL Do not generate the mirror page]** :不生成镜像页面，即使投放中存在链接也是如此。
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** :通过此选项，您可以在镜像页面日志窗口中访问包含个性化信息的投放内容。 为此，在投放结束后，单击标 **[!UICONTROL Delivery]** 签并选择要镜像页面的收件人的行。 单击链 **[!UICONTROL Display the mirror page for this message...]** 接。

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## 管理弹回电子邮件 {#managing-bounce-emails}

投放 **[!UICONTROL SMTP]** 参数的选项卡允许您配置弹回邮件的管理。

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

默认情况下，退回电子邮件会在平台的默认错误框中接收，但您可以为投放定义特定错误地址。

您还可以从此屏幕定义特定地址，以调查在应用程序无法自动限定弹出邮件的原因。 对于每个字段，“添加个性化字段”图标允许您添加个性化参数。

## 字符编码 {#character-encoding}

在投放 **[!UICONTROL SMTP]** 参数的选项卡中，该 **[!UICONTROL Character encoding]** 部分允许您设置特定编码。

默认编码为UTF-8。 如果某些收件人的电子邮件提供者不支持UTF-8标准编码，您可能希望设置特定编码以向电子邮件的收件人正确显示特殊字符。

例如，您要发送包含日文字符的电子邮件。 为确保所有字符都能正确显示给日本的收件人，您可能希望使用支持日语字符的编码，而不是标准UTF-8。

为此，请选择部 **[!UICONTROL Force the encoding used for messages]** 分中的选 **[!UICONTROL Character encoding]** 项，并从显示的下拉列表中选择编码。

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## 添加SMTP头 {#adding-smtp-headers}

可以向投放添加SMTP头。 为此，请使用投放中选项卡 **[!UICONTROL SMTP]** 的相关部分。

The script entered in this window must reference one header per line in the following form: **name:value**.

如有必要，将自动对值进行编码。

>[!CAUTION]
>
>高级用户可随时添加脚本以插入其他 SMTP 标头。
>
>此脚本的语法必须符合此内容类型的要求：没有未使用的空格，没有空行等。
