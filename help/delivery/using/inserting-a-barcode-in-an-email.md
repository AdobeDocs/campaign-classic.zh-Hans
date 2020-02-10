---
title: 在电子邮件中插入条形码
seo-title: 在电子邮件中插入条形码
description: 在电子邮件中插入条形码
seo-description: null
page-status-flag: never-activated
uuid: 61f9d8ea-38b0-46a5-8085-b6f34f8559f7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 679b9ae2-362c-483d-acb8-47bc01928541
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 在电子邮件中插入条形码{#inserting-a-barcode-in-an-email}

条形码生成模块允许您创建符合许多常见标准（包括2D条形码）的几种条形码。

可以使用使用客户标准定义的值动态地生成条形码作为位图。 个性化的条码可包含在电子邮件营销活动中。 收件人可以打印邮件并将其显示给发布公司进行扫描（例如，在注销时）。

要将条形码插入电子邮件，请将光标放在要显示它的内容中，然后单击个性化按钮。 Select **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

然后，配置以下元素以满足您的需求：

1. 选择条形码类型。

   * 对于1D格式，Adobe Campaign中提供以下类型：Codabar，代码128, GS1-128（以前称为EAN-128）, UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleand 2 of 5, POSTNET和Royal Mail(RM4SCC)。

      1D条形码示例：

      ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417类型涉及2D格式。

      2D条形码示例：

      ![](assets/barcode_insert_09.png)

   * 要插入QR码，请选择此类型并输入要应用的错误校正率。 该速率定义重复信息的数量和对恶化的容忍度。

      ![](assets/barcode_insert_06.png)

      QR码示例：

      ![](assets/barcode_insert_12.png)

1. 输入要插入电子邮件的条形码的大小：通过配置比例，您可以从x1增大或减小条形码的大小，从x1增大到x10。
1. 该 **[!UICONTROL Value]** 字段允许您定义条形码的值。 值可以与特价优惠匹配，也可以是标准的函数，也可以是链接到客户的数据库字段的值。

   此示例显示EAN-8类型条形码，该条形码已添加到收件人的帐号。 要添加此帐号，请单击字段右侧的个性化按钮并 **[!UICONTROL Value]** 选择 **[!UICONTROL Recipient > Account number]**。

   ![](assets/barcode_insert_15.png)

1. 通过 **[!UICONTROL Height]** 该字段，您可以通过更改每个条形之间的间距量，在不更改条形码宽度的情况下配置条形码的高度。

   根据条形码的类型，没有限制性的输入控件。 如果条形码值不正确，它将仅在“预览 **** ”模式下可见，在该模式下，条形码将以红色划出。

   >[!NOTE]
   >
   >分配给条形码的值取决于其类型。 例如，EAN-8类型应具有正好8个数字。
   >
   >通过字段右侧的个性化按 **[!UICONTROL Value]** 钮，除了值本身之外，您还可以添加数据。 这丰富了条形码，前提是条形码标准接受它。
   >
   >例如，如果您使用GS1-128类型的条形码，并且除了输入值之外还要输入收件人的帐号，请单击个性化按钮并选择 **[!UICONTROL Recipient > Account number]**。 如果正确输入了选定收件人的帐号，条形码会将其考虑在内。

配置这些元素后，您可以完成电子邮件并发送。 为避免出错，请务必在执行分发之前通过单击选项卡确保内容正确显 **[!UICONTROL Preview]** 示。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果条形码的值不正确，其位图将以红色划出。

![](assets/barcode_insert_11.png)
