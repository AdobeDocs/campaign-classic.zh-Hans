---
product: campaign
title: 在Adobe Campaign Classic中定义电子邮件内容
description: 了解如何在使用Adobe Campaign时定义电子邮件内容
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Email Design
role: User
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1958'
ht-degree: 1%

---

# 定义电子邮件的内容 {#defining-the-email-content}

## 发件人 {#sender}

要定义将出现在已发送邮件标题中的发件人姓名和地址，请单击 **[!UICONTROL From]** 链接。

![](assets/s_ncs_user_wizard_email02.png)

在此窗口中，您可以输入创建电子邮件标头所需的所有信息。 此信息可以个性化。 要实现此目的，请使用输入字段右侧的按钮插入个性化字段。

要了解如何插入和使用个性化字段，请参阅 [关于个性化](about-personalization.md) 部分。

>[!NOTE]
>
>* 默认情况下，使用发件人的地址进行回复。
>* 标头参数不能为空。 默认情况下，它们包含配置部署向导时输入的值。 可在[此部分](../../installation/using/deploying-an-instance.md)中了解详情。
>* 发件人的地址是允许发送电子邮件的必备项（RFC标准）。
>* Adobe Campaign检查所输入电子邮件地址的语法。

>[!CAUTION]
>
>为了避免出现可投放性问题，必须存在与为投放和回复指定的地址对应的电子邮件帐户，并且必须对其进行监控。 请与系统管理员核实。

## 消息主题 {#message-subject}

消息的主题在相应字段中配置。 您可以直接在字段中输入或单击 **[!UICONTROL Subject]** 用于输入脚本的链接。 利用个性化链接，可在主题中插入数据库字段。

>[!IMPORTANT]
>
>消息主题为必填项。

![](assets/s_ncs_user_wizard_email_object.png)

发送消息时，字段内容将由收件人用户档案中的值替换。

例如，在上面的消息中，使用来自每个收件人的用户档案的数据，为每个收件人个性化消息主题。

>[!NOTE]
>
>中介绍了个性化字段的使用 [关于个性化](about-personalization.md).

您还可以在主题行中插入表情符号 **[!UICONTROL Insert emoticon]** 弹出窗口。

## 消息内容 {#message-content}

>[!IMPORTANT]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

消息的内容在投放配置窗口的下半部分中定义。

默认情况下，将根据收件人偏好设置，以HTML或文本格式发送消息。 我们建议创建两种格式的内容，以确保在任何邮件系统中均可正确显示消息。 有关详细信息，请参见 [选择消息格式](email-parameters.md#selecting-message-formats).

* 要导入HTML内容，请使用 **[!UICONTROL Open]** 按钮。 您还可以将源代码直接粘贴到 **[!UICONTROL Source]** 子选项卡。

  如果您使用 [数字内容编辑器](../../web/using/about-campaign-html-editor.md) (DCE)，请参阅 [选择内容模板](../../web/using/use-case-creating-an-email-delivery.md#step-3---selecting-a-content).

  >[!IMPORTANT]
  >
  >必须预先创建HTML内容，然后将其导入Adobe Campaign。 HTML编辑器不是为创建内容而设计的。

  此 **[!UICONTROL Preview]** 通过子选项卡，可以查看收件人的每个内容的呈现。 将内容的个性化字段和条件元素替换为所选用户档案的相应信息。

  通过工具栏按钮可访问“HTML”页面的标准操作和格式参数。

  ![](assets/s_ncs_user_wizard_email01_138.png)

  您可以在来自本地文件或Adobe Campaign中图像库的消息中插入图像。 要执行此操作，请单击 **[!UICONTROL Image]** 图标并选择相应的选项。

  ![](assets/s_ncs_user_wizard_email01_18.png)

  库图像可通过 **[!UICONTROL Resources>Online>Public resources]** 文件夹树中的文件夹。 另请参阅 [添加图像](#adding-images).

  使用工具栏中的最后一个按钮，可插入个性化字段。

  >[!NOTE]
  >
  >中介绍了个性化字段的使用 [关于个性化](about-personalization.md).

  通过页面底部的选项卡，可显示正在创建的页面的HTML代码，并查看消息及其个性化呈现。 要启动此显示，请单击 **[!UICONTROL Preview]** 并使用选择收件人 **[!UICONTROL Test personalization]** 工具栏中的按钮。 您可以从定义的目标中选择收件人，也可以选择其他收件人。

  ![](assets/s_ncs_user_wizard_email01_139.png)

  您可以验证HTML消息。 您还可以查看电子邮件标头的内容。

  ![](assets/s_ncs_user_wizard_email01_140.png)

* 要导入文本内容，请使用 **[!UICONTROL Open]** 按钮，或 **[!UICONTROL Text Content]** 选项卡，以文本格式显示时输入消息的内容。 使用工具栏按钮访问对内容的操作。 利用最后一个按钮，可插入个性化字段。

  ![](assets/s_ncs_user_wizard_email01_141.png)

  对于HTML格式，单击 **[!UICONTROL Preview]** 选项卡以查看消息的呈现及其个性化设置。

  ![](assets/s_ncs_user_wizard_email01_142.png)


## 定义交互式内容 {#amp-for-email-format}

Adobe Campaign允许您尝试新的交互式 [电子邮件AMP](https://amp.dev/about/email/) 格式，允许在特定条件下发送动态电子邮件。

有关更多信息，请参阅[此小节](defining-interactive-content.md)。

## 使用内容管理 {#using-content-management}

您可以使用内容管理表单，直接在投放向导中定义投放的内容。 要实现此目的，您必须引用要在中使用的内容管理的发布模板，在 **[!UICONTROL Advanced]** 投放属性的选项卡。

![](assets/s_ncs_content_in_delivery.png)

通过附加选项卡，可输入将根据内容管理规则自动集成和设置格式的内容。

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>有关Adobe Campaign中内容管理的更多信息，请参阅 [本节](about-content-management.md).

## 插入表情符号 {#inserting-emoticons}

您可以在电子邮件内容中插入表情符号。

1. 单击 **[!UICONTROL Insert emoticon]** 图标。
1. 从弹出窗口中选择表情符号。

   ![](assets/emoticon_4.png)

1. 单击 **[!UICONTROL Close]** 按钮。

要自定义表情符号列表，请参阅此 [页面](customizing-emoticon-list.md).

## 添加图像 {#adding-images}

HTML格式的电子邮件投放可以包含图像。 在投放向导中，您可以通过，导入包含图像的HTML页面或直接使用HTML编辑器插入图像 **[!UICONTROL Image]** 图标。


### 护栏 {#img-guardrails}

为避免性能问题，电子邮件中包含的图像不能超过100 KB。 默认设置的此限制可以从 `NmsDelivery_MaxDownloadedImageSize` 选项。 但是，Adobe强烈建议避免在电子邮件投放中使用大型图像。

了解详情，请参阅 [Campaign Classic选项列表](../../installation/using/configuring-campaign-options.md#delivery).

### 图像类型 {#img-types}

图像可以是：

* 本地映像或从服务器调用的映像
* 存储在Adobe Campaign公共资源库中的图像

  公共资源可通过 **[!UICONTROL Resources > Online]** Adobe Campaign层级的节点。 它们分组在库中，可以包含在电子邮件中，但也可以用于营销活动或任务，或者用于内容管理。

* 与Adobe Experience Cloud共享的资源。 请参阅[此小节](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md)。

### 插入和管理图像 {#manage-images}

利用投放向导，可将本地图像或存储在库中的图像添加到消息的内容中。 要执行此操作，请单击 **[!UICONTROL Image]** HTML按钮。

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>为了使收件人能够查看他们收到的邮件中包含的图像，这些邮件必须在可从外部访问的服务器上可用。

要通过投放向导管理图像，请执行以下操作：

1. 单击 **[!UICONTROL Tracking & Images]** 图标。
   ![](assets/s_ncs_user_email_del_img_param.png)

1. 选择 **[!UICONTROL Upload images]** 在 **[!UICONTROL Images]** 选项卡。
1. 然后，您可以选择是否希望在电子邮件中包含图像。
   ![](assets/s_ncs_user_email_del_img_upload.png)

* 您可以手动上传图像，而无需等待投放分析阶段。 要执行此操作，请单击 **[!UICONTROL Upload the images straightaway...]** 链接。
* 您可以指定其他路径来访问跟踪服务器上的图像。 要执行此操作，请在 **[!UICONTROL Images URL]** 字段。 此值将覆盖安装向导的参数中定义的值。

在投放向导中打开包含图像的HTML内容时，将会显示一条消息，根据投放参数，为您提供立即上传图像的选项。

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
> 在手动上传或发送消息期间会修改图像URL。
> 

### 用例：发送包含图像的消息 {#uc-images}

以下是包含四个图像的投放示例：

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

这些图像来自本地目录或网站，您可以从 **[!UICONTROL Source]** 选项卡。

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

单击 **[!UICONTROL Tracking & Images]** 图标，然后 **[!UICONTROL Images]** 选项卡，开始检测消息中的图像。

对于每个检测到的图像，可以查看其状态：

* 如果图像存储在本地或位于其他服务器上，即使从外部可以看到该服务器（例如在Internet网站上），也会将其检测为 **[!UICONTROL Not yet online]**.
* 图像被检测为 **[!UICONTROL Already online]** 如果在创建其他投放时提前上传，则为。
* 在部署向导中，您可以定义未启用图像检测的URL：上传这些图像将 **[!UICONTROL Skipped]**.

>[!NOTE]
>
>图像根据其内容而不是其访问路径进行标识。 这意味着之前以不同名称或不同目录上传的映像将被检测为 **[!UICONTROL Already online]**.

在分析阶段，图像会自动上传到服务器，以便从外部访问，但必须预先上传的本地图像除外。

您可以继续工作并上传图像，以便其他Adobe Campaign操作员能够查看这些图像。 如果您与他人协作，可能会发现此工具非常有用。 为此，请单击 **[!UICONTROL Upload the images straightaway...]** 将图像上传到服务器。

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>然后修改电子邮件中图像的URL，特别是其名称。

图像联机后，您可以从 **[!UICONTROL Source]** 的选项卡。

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

如果您选择 **[!UICONTROL Include the images in the email]**&#x200B;中，您可以选择要包含在相应列中的图像。

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>如果消息中包含本地图像，则必须确认对消息源代码的更改。

## 插入个性化条形码{#insert-a-barcode}

条形码生成模块允许您创建符合许多常见标准的多种条形码，包括2D条形码。

可以使用使用客户条件定义的值动态地生成条形码作为位图。 电子邮件营销活动中可包含个性化的条形码。 收件人可以打印邮件并向发行公司显示以供扫描（例如，在结帐时）。

要在电子邮件中插入条形码，请将光标置于要显示条码的内容中，然后单击个性化按钮。 选择 **[!UICONTROL Include > Barcode...]**。

![](assets/barcode_insert_14.png)

然后，根据您的需求配置以下元素：

1. 选择条形码类型。

   * 对于1D格式，Adobe Campaign提供以下类型：Codabar、代码128、GS1-128（以前称为EAN-128）、UPC-A、UPC-E、ISBN、EAN-8、代码39、交错码2（共5个）、POSTNET和皇家邮件(RM4SCC)。

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
1. 此 **[!UICONTROL Value]** 字段用于定义条形码的值。 值可以匹配特殊选件，可以是标准的函数，也可以是链接到客户的数据库字段的值。

   此示例显示了一个EAN-8类型的条形码，其中添加了收件人的帐号。 要添加此帐号，请单击 **[!UICONTROL Value]** 字段并选择 **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. 此 **[!UICONTROL Height]** 字段允许您通过更改条之间的间距来配置条形码的高度，而不更改条形码的宽度。

   根据条形码的类型，没有限制性条目控制。 如果条形码值不正确，则它仅在 **预览** 将条形码以红色划掉的模式。

   >[!NOTE]
   >
   >分配给条码的值取决于其类型。 例如，EAN-8类型应恰好有8个数字。
   >
   >右侧的个性化按钮 **[!UICONTROL Value]** 字段允许您在值本身之外添加数据。 只要条码标准接受它，这就会丰富条码。
   >
   >例如，如果您使用GS1-128类型条形码，并且希望输入除值之外的收件人帐号，请单击个性化按钮并选择 **[!UICONTROL Recipient > Account number]**. 如果正确输入了所选收件人的帐号，则条码会考虑该帐号。

配置这些元素后，即可最终确定电子邮件并将其发送。 为避免出现错误，请始终确保内容显示正确，然后再通过单击 **[!UICONTROL Preview]** 选项卡。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果条形码的值不正确，其位图将以红色划掉。

![](assets/barcode_insert_11.png)
