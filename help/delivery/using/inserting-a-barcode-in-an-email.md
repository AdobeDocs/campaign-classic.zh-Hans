---
product: campaign
title: 在电子邮件中插入条形码
description: 在电子邮件中插入条形码
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Email Design
role: User
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# 在电子邮件中插入条形码{#insert-a-barcode-in-an-email}

条形码生成模块允许您创建符合许多常见标准的多种条形码，包括2D条形码。

可以使用使用客户条件定义的值动态地生成条形码作为位图。 电子邮件营销活动中可包含个性化的条形码。 收件人可以打印邮件并向发行公司显示以供扫描（例如，在结帐时）。

要在电子邮件中插入条形码，请将光标置于要显示条码的内容中，然后单击个性化按钮。 选择 **[!UICONTROL Include > Barcode...]**。

![](assets/barcode_insert_14.png)

然后，根据您的需求配置以下元素：

1. 选择条形码类型。

   * 对于1D格式，Adobe Campaign提供以下类型：Codabar、代码128、GS1-128（以前称为EAN-128）、UPC-A、UPC-E、ISBN、EAN-8、代码39、交错式2（共5个）、POSTNET和皇家邮件(RM4SCC)。

     1D条形码示例：

     ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417类型涉及2D格式。

     2D条形码示例：

     ![](assets/barcode_insert_09.png)

   * 要插入QR码，请选择此类型并输入要应用的纠错率。 此比率定义重复的信息量以及对恶化的容差。

     ![](assets/barcode_insert_06.png)

     QR代码示例：

     ![](assets/barcode_insert_12.png)

1. 输入要插入到电子邮件中的条形码大小：通过配置小数位数，可以将条形码的大小从x1增大到x10。
1. **[!UICONTROL Value]**&#x200B;字段允许您定义条形码的值。 值可以匹配特殊选件，可以是标准的函数，也可以是链接到客户的数据库字段的值。

   此示例显示了一个EAN-8类型的条形码，其中添加了收件人的帐号。 若要添加此帐号，请单击&#x200B;**[!UICONTROL Value]**&#x200B;字段右侧的个性化按钮，然后选择&#x200B;**[!UICONTROL Recipient > Account number]**。

   ![](assets/barcode_insert_15.png)

1. **[!UICONTROL Height]**&#x200B;字段允许您通过更改条形码之间的间距来配置条形码的高度，而不更改条形码的宽度。

   根据条形码的类型，没有限制性条目控制。 如果条码值不正确，它将仅在&#x200B;**预览**&#x200B;模式下可见，在此模式下，条码将以红色划出。

   >[!NOTE]
   >
   >分配给条码的值取决于其类型。 例如，EAN-8类型应恰好有8个数字。
   >
   >**[!UICONTROL Value]**&#x200B;字段右侧的个性化按钮允许您在值本身之外添加数据。 只要条码标准接受它，这就会丰富条码。
   >
   >例如，如果您使用GS1-128类型条形码，并且希望输入除值之外的收件人帐号，请单击个性化按钮并选择&#x200B;**[!UICONTROL Recipient > Account number]**。 如果正确输入了所选收件人的帐号，则条码会考虑该帐号。

配置这些元素后，即可最终确定电子邮件并将其发送。 为避免出现错误，请始终确保内容显示正确，然后再通过单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡执行投放。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果条形码的值不正确，其位图将以红色划掉。

![](assets/barcode_insert_11.png)
