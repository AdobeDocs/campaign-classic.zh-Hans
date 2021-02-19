---
solution: Campaign Classic
product: campaign
title: 在电子邮件中插入条形码
description: 在电子邮件中插入条形码
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---


# 在电子邮件中插入条形码{#inserting-a-barcode-in-an-email}

条形码生成模块允许您创建符合许多常见标准（包括2D条码）的几种条形码。

可以使用使用客户标准定义的值动态地将条形码生成为位图。 个性化的条码可以包含在电子邮件活动中。 收件人可以打印消息并将其显示给发布公司以进行扫描（例如，当签出时）。

要在电子邮件中插入条形码，请将光标置于要显示它的内容中，然后单击个性化按钮。 选择 **[!UICONTROL Include > Barcode...]**。

![](assets/barcode_insert_14.png)

然后，配置以下元素以满足您的需求：

1. 选择条形码类型。

   * 对于1D格式，以下类型在Adobe Campaign中可用：Codabar， Code 128, GS1-128（以前称为EAN-128）， UPC-A， UPC-E， ISBN， EAN-8, Code39, Interleved 2 of 5, POSTNET和Royal Mail(RM4SCC)。

      1D条形码示例：

      ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417类型涉及2D格式。

      2D条形码示例：

      ![](assets/barcode_insert_09.png)

   * 要插入QR码，请选择此类型并输入要应用的纠错率。 此比率定义重复信息的数量和对恶化的容差。

      ![](assets/barcode_insert_06.png)

      QR码示例：

      ![](assets/barcode_insert_12.png)

1. 输入要插入电子邮件的条形码的大小：通过配置缩放，您可以增加或减小条形码的大小，从x1到x10。
1. **[!UICONTROL Value]**&#x200B;字段允许您定义条形码的值。 值可以与特定优惠匹配，也可以是标准的函数，也可以是链接到客户的数据库字段的值。

   此示例显示EAN-8类型的条形码，其中添加了收件人的帐号。 要添加此帐号，请单击&#x200B;**[!UICONTROL Value]**&#x200B;字段右侧的个性化按钮并选择&#x200B;**[!UICONTROL Recipient > Account number]**。

   ![](assets/barcode_insert_15.png)

1. 通过&#x200B;**[!UICONTROL Height]**&#x200B;字段，您可以通过更改每个条形之间的空间量，配置条形码的高度，而不更改其宽度。

   没有根据条形码类型进行的限制性输入控件。 如果条形码值不正确，则只能在&#x200B;**预览**&#x200B;模式下显示该条形码，在该模式下，条形码将以红色划出。

   >[!NOTE]
   >
   >分配给条形码的值取决于其类型。 例如，EAN-8类型应具有正8个数字。
   >
   >通过&#x200B;**[!UICONTROL Value]**&#x200B;字段右侧的个性化按钮，除了值本身之外，还可以添加数据。 这会丰富条形码，前提是条形码标准接受它。
   >
   >例如，如果您使用GS1-128类型条形码，并且要输入收件人的帐号以及值，请单击个性化按钮并选择&#x200B;**[!UICONTROL Recipient > Account number]**。 如果正确输入所选收件人的帐号，条形码会将其考虑在内。

配置这些元素后，您可以完成电子邮件并发送。 为避免出现错误，请务必在执行投放之前单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡，确保正确显示您的内容。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果条形码的值不正确，其位图将用红色划出。

![](assets/barcode_insert_11.png)
