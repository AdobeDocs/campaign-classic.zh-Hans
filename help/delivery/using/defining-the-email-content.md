---
solution: Campaign Classic
product: campaign
title: 定义Adobe Campaign Classic的电子邮件内容
description: 了解如何使用Adobe Campaign Classic时定义电子邮件内容。
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2887'
ht-degree: 1%

---


# 定义电子邮件内容{#defining-the-email-content}

## 发件人 {#sender}

要定义将显示在所发送邮件标题中的发件人姓名和地址，请单击链 **[!UICONTROL From]** 接。

![](assets/s_ncs_user_wizard_email02.png)

在此窗口中，您可以输入创建电子邮件标头所需的所有信息。 此信息可以个性化。为此，请使用输入字段右侧的按钮插入个性化字段。

要了解如何插入和使用个性化字段，请参阅关于 [个性化](../../delivery/using/about-personalization.md) 部分。

>[!NOTE]
>
>* 默认情况下，发件人地址将用于回复。
>* 标题参数不得为空。 默认情况下，它们包含配置部署向导时输入的值。 有关详细信息，请参阅《安 [装指南》](../../installation/using/deploying-an-instance.md)。
>* 发送者的地址是允许发送电子邮件的必填地址（RFC标准）。
>* Adobe Campaign检查输入的电子邮件地址的语法。


>[!IMPORTANT]
>
>在Internet访问提供商(ISP)为打击未经请求的电子邮件（垃圾邮件）而实施的检查环境中，Adobe建议创建与为投放和回复指定的地址对应的电子邮件帐户。 请咨询邮件系统管理员。

## 邮件主题 {#message-subject}

消息主题在相应字段中配置。 您可以直接在字段中输入脚本，也可 **[!UICONTROL Subject]** 以单击链接以输入脚本。 个性化链接允许您在主题中插入数据库字段。

>[!IMPORTANT]
>
>邮件主题是必填的。

![](assets/s_ncs_user_wizard_email_object.png)

发送消息时，字段内容将替换为收件人用户档案中的值。

例如，在以上消息中，每个收件人的消息主题都是个性化的，其中包含来自用户档案的数据。

>[!NOTE]
>
>个性化字段的使用在“关于个 [性化”中](../../delivery/using/about-personalization.md)。

您还可以在弹出窗口中将表情图标插 **[!UICONTROL Insert emoticon]** 入到主题行。

## 消息内容 {#message-content}

>[!IMPORTANT]
>
>出于隐私考虑，我们建议对所有外部资源使用HTTPS。

消息内容在投放配置窗口的下半部分中定义。

默认情况下，消息以HTML或文本格式发送，这取决于收件人首选项。 我们建议创建两种格式的内容，以确保消息能够在任何邮件系统中正确显示。 有关此内容的详细信息，请参阅 [选择消息格式](#selecting-message-formats)。

* 要导入HTML内容，请使用 **[!UICONTROL Open]** 按钮。 您还可以将源代码直接粘贴到 **[!UICONTROL Source]** 子选项卡中。

   如果您使用的是 [数字内容编辑器](../../web/using/about-campaign-html-editor.md) (数字内容编辑器)，请参 [阅选择内容模板](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content)。

   >[!IMPORTANT]
   >
   >必须事先创建HTML内容，然后将其导入Adobe Campaign。 HTML编辑器不是为创建内容而设计的。

   通过 **[!UICONTROL Preview]** 子选项卡，您可以视图每个内容的呈现，以便收件人。 个性化字段和内容的条件元素被替换为所选用户档案的相应信息。

   工具栏按钮提供对HTML页面的标准操作和格式参数的访问。

   ![](assets/s_ncs_user_wizard_email01_138.png)

   您可以在消息中插入来自本地文件或图像库的Adobe Campaign图像。 为此，请单击图 **[!UICONTROL Image]** 标并选择相应的选项。

   ![](assets/s_ncs_user_wizard_email01_18.png)

   库图像可通过文件夹树 **[!UICONTROL Resources>Online>Public resources]** 中的文件夹进行访问。 另请参阅 [添加图像](#adding-images)。

   工具栏中的最后一个按钮允许您插入个性化字段。

   >[!NOTE]
   >
   >个性化字段的使用在“关于个 [性化”中](../../delivery/using/about-personalization.md)。

   页面底部的选项卡允许您显示所创建页面的HTML代码，并将消息的呈现与其个性化视图。 要启动此显示屏，请单 **[!UICONTROL Preview]** 击并使用工具栏中的按 **[!UICONTROL Test personalization]** 钮选择收件人。 您可以从定义的收件人中选择一个目标或选择其他收件人。

   ![](assets/s_ncs_user_wizard_email01_139.png)

   您可以验证HTML消息。 您还可以视图电子邮件标题的内容。

   ![](assets/s_ncs_user_wizard_email01_140.png)

* 要导入文本内容，请 **[!UICONTROL Open]** 使用按钮或选 **[!UICONTROL Text Content]** 项卡在以文本格式显示时输入消息的内容。 使用工具栏按钮访问内容上的操作。 最后一个按钮允许您插入个性化字段。

   ![](assets/s_ncs_user_wizard_email01_141.png)

   对于HTML格式，请单 **[!UICONTROL Preview]** 击页面底部的选项卡，将消息呈现与其个性化视图。

   ![](assets/s_ncs_user_wizard_email01_142.png)

### 在电子邮件中插入表情图标 {#inserting-emoticons}

您可以在电子邮件内容中插入表情图标。

1. 单击该 **[!UICONTROL Insert emoticon]** 图标。
1. 从弹出窗口中选择一个表情图标。

   ![](assets/emoticon_4.png)

1. 完成后 **[!UICONTROL Close]** 单击按钮。

要自定义表情图标列表，请参阅 [此页](../../delivery/using/customizing-emoticon-list.md)。

## 选择消息格式 {#selecting-message-formats}

您可以更改发送电子邮件的格式。 为此，请编辑投放属性，然后单击选 **[!UICONTROL Delivery]** 项卡。

![](assets/s_ncs_user_wizard_email_param.png)

在窗口的下半部分选择电子邮件的格式：

* **[!UICONTROL Use recipient preferences]** （默认模式）

   The message format is defined according to the data stored in the recipient profile and stored by default in the **[!UICONTROL email format]** field (@emailFormat). 如果收件人希望以特定格式接收消息，则会将该格式用于发送的邮件。如果未填写字段，则会发送复合-可选消息（请参阅下文）。

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   消息包含两种格式：文本和HTML。 接收时显示的格式取决于收件人邮件软件(复合-可选)的配置。

   >[!IMPORTANT]
   >
   >此选项包括两个版本的文档。 因此，它会影响投放率，因为消息大小更大。

* **[!UICONTROL Send all messages in text format]**

   消息以文本格式发送。 不会发送HTML格式，但仅当镜像页面单击消息时，才会将其用于收件人。

## 定义互动内容 {#amp-for-email-format}

Adobe Campaign使您能够试用新的交 [互式AMP for Email](https://amp.dev/about/email/) ，该格式允许在特定条件下发送动态电子邮件。

有关更多信息，请参阅[此章节](../../delivery/using/defining-interactive-content.md)。

## 使用内容管理 {#using-content-management}

您可以直接在投放中使用内容管理表单定义投放向导的内容。 为此，您必须在发布模板属性的选项卡中引用要使用 **[!UICONTROL Advanced]** 的内容管理的投放。

![](assets/s_ncs_content_in_delivery.png)

您还可以使用其他选项卡输入内容，这些内容将根据内容管理规则自动进行集成和格式化。

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>有关Adobe Campaign内容管理的详细信息，请参 [阅本节](../../delivery/using/about-content-management.md)。

## 添加图像 {#adding-images}

HTML格式的电子邮件投放可以包含图像。 在该投放向导中，您可以导入包含图像的HTML页面，或直接使用HTML编辑器通过图标插入 **[!UICONTROL Image]** 图像。

图像可以：

* 本地映像或从服务器调用的映像
* 存储在Adobe Campaign公共资源库中的图像

   公共资源可通过Adobe Campaign **[!UICONTROL Resources > Online]** 层次结构的节点访问。 它们被分组在库中，并可以包含在电子邮件中，但也可用于活动或任务或内容管理。

* 与Adobe Experience Cloud共享的资产。 请参阅[此章节](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md) 。

>[!IMPORTANT]
>
>要使用投放向导将图像包含在电子邮件中，必须配置Adobe Campaign实例以启用公共资源管理。 此过程可从部署向导中执行。 有关配置 [的更多信息](../../installation/using/deploying-an-instance.md) ，请参阅本节。

该投放向导允许您向消息内容中添加本地图像或库中存储的图像。 To do this, click the **[!UICONTROL Image]** button in the HTML content toolbar.

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>为了使收件人能够视图他们收到的消息中包含的图像，这些消息必须在可从外部访问的服务器上可用。

要通过投放向导管理图像，请执行以下操作：

1. 单击工 **[!UICONTROL Tracking & Images]** 具栏中的图标。
   ![](assets/s_ncs_user_email_del_img_param.png)

1. 在选 **[!UICONTROL Upload images]** 项卡中 **[!UICONTROL Images]** 选择。
1. 然后，您可以选择是否要在电子邮件中包含图像。
   ![](assets/s_ncs_user_email_del_img_upload.png)

* 您可以手动上传图像，无需等待投放分析阶段。 为此，请单击链 **[!UICONTROL Upload the images straightaway...]** 接。
* 您可以指定另一个路径以访问跟踪服务器上的图像。 为此，请在字段中输入 **[!UICONTROL Images URL]** 它。 此值将覆盖在安装向导的参数中定义的值。

在投放向导中打开包含图像的HTML内容时，系统会显示一条消息，提示您根据投放参数立即上传图像。

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
>在手动上传或发送消息时，会修改图像访问路径。

### 发送包含图像的消息 {#sending-a-message-with-images}

>[!NOTE]
>
>为避免性能问题，如果您将通过个性化URL动态下载的图像 [作为附件](../../delivery/using/attaching-files.md)，则默认情况下，每个图像大小不应超过100,000字节。 此推荐阈值可以通过 [列表Campaign Classic选项配置](../../installation/using/configuring-campaign-options.md#delivery)。

以下是包含四个图像的投放的示例：

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

这些图像来自本地目录或网站，您可以通过选项卡进行 **[!UICONTROL Source]** 验证。

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

单击图 **[!UICONTROL Tracking & Images]** 标，然后单击选 **[!UICONTROL Images]** 项卡以开始检测消息中的图像。

对于检测到的每个图像，您可以视图其状态：

* 如果图像存储在本地或位于另一台服务器上，即使此服务器从外部（例如，在Internet站点上）可见，也会检测为 **[!UICONTROL Not yet online]**。
* 在创建其他投放时， **[!UICONTROL Already online]** 会检测到图像，就像之前上传过一样。
* 在部署向导中，您可以定义未启用图像检测的URL:上传这些图像将 **[!UICONTROL Skipped]**&#x200B;是。

>[!NOTE]
>
>图像由其内容而非访问路径来标识。 这意味着之前以不同名称或不同目录上载的图像将检测为 **[!UICONTROL Already online]**。

在分析阶段，图像会自动上传到服务器，以便从外部访问它们，但本地图像必须预先上传。

您可以继续工作并上传图像，以便其他Adobe Campaign操作员查看它们。 如果您能相互协作，您会发现这一点很有用。 为此，请单 **[!UICONTROL Upload the images straightaway...]** 击将图像上传到服务器。

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>然后，将修改电子邮件中图像的URL，特别是其名称。

图像联机后，您可以从消息的选项卡中视图对其名称 **[!UICONTROL Source]** 和路径的更改。

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

如果您选 **[!UICONTROL Include the images in the email]**&#x200B;择，则可以选择要包含在相应列中的图像。

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>如果消息中包含本地图像，则必须确认对消息源代码所做的更改。

## 在电子邮件中插入条形码{#inserting-a-barcode-in-an-email}

条形码生成模块允许您创建符合许多常见标准的几种条形码，包括2D条形码。

可以使用使用客户条件定义的值动态生成条形码作为位图。 个性化条码可包含在电子邮件活动中。 收件人可以打印消息并将其显示给发布公司进行扫描（例如，在签出时）。

要在电子邮件中插入条形码，请将光标放在要显示它的内容中，然后单击个性化按钮。 选择 **[!UICONTROL Include > Barcode...]**。

![](assets/barcode_insert_14.png)

然后，配置以下元素以满足您的需求：

1. 选择条形码类型。

   * 对于1D格式，Adobe Campaign中提供以下类型：Codabar，代码128, GS1-128（以前称为EAN-128）, UPC-A, UPC-E, ISBN, EAN-8，代码39，隔行2，共5个，邮递网和皇家邮政(RM4SCC)。

      1D条形码示例：

      ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417类型涉及2D格式。

      2D条形码示例：

      ![](assets/barcode_insert_09.png)

   * 要插入QR码，请选择此类型并输入要应用的错误校正率。 此比率定义重复信息的数量和退化的容限。

      ![](assets/barcode_insert_06.png)

      QR码示例：

      ![](assets/barcode_insert_12.png)

1. 输入要插入到电子邮件中的条形码的大小：通过配置比例，您可以增加或减少条形码的大小，从x1到x10。
1. 字 **[!UICONTROL Value]** 段允许您定义条形码的值。 值可以与特殊优惠匹配，也可以是标准的函数，也可以是链接到客户的数据库字段的值。

   此示例显示EAN-8类型条形码，其中添加了收件人的帐号。 要添加此帐号，请单击字段右侧的个性化按 **[!UICONTROL Value]** 钮并选择 **[!UICONTROL Recipient > Account number]**。

   ![](assets/barcode_insert_15.png)

1. 通过 **[!UICONTROL Height]** 该字段，您可以通过更改每个条形之间的间距量，配置条形码的高度，而不更改其宽度。

   根据条形码的类型，没有限制条目控件。 如果条形码值不正确，它将仅在预览模式 **下可见** ，在该模式下，条形码将以红色划出。

   >[!NOTE]
   >
   >分配给条形码的值取决于其类型。 例如，EAN-8类型应具有恰好8个数字。
   >
   >通过字段右侧的个性化按 **[!UICONTROL Value]** 钮，除了值本身之外，您还可以添加数据。 这丰富了条形码，前提是条形码标准接受它。
   >
   >例如，如果您使用GS1-128类型条形码，并且要输入收件人的帐号以及该值，请单击个性化按钮并选择 **[!UICONTROL Recipient > Account number]**。 如果正确输入了选定收件人的帐号，条形码会将其考虑在内。

配置这些元素后，您可以完成电子邮件并发送。 为避免出现错误，请务必在执行投放之前，通过单击选项卡，确保内容正确 **[!UICONTROL Preview]** 显示。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果条形码的值不正确，其位图将用红色划出。

![](assets/barcode_insert_11.png)

## 在日本手机上发送电子邮件 {#sending-emails-on-japanese-mobiles}

### 日本手机电子邮件格式 {#email-formats-for-japanese-mobiles}

Adobe Campaign管理手机上电子邮件的三种特定日文格式： **Deco-mail** (DoCoMo mobile **)、Decore** Mail **(Softbank mobile)和Decoration Mail** (KDDI AU mobile)。 这些格式会施加特定的编码、结构和大小限制。 了解本节中有关限制和建议的 [更多信息](#limitations-and-recommendations)。

为了让收件人正确接收这些格式之一的消息，我们建议选 **[!UICONTROL Deco-mail (DoCoMo)]**&#x200B;择 **[!UICONTROL Decore Mail (Softbank)]** 相应 **[!UICONTROL Decoration Mail (KDDI AU)]** 的用户档案:

![](assets/deco-mail_03.png)

但是，如果您将选 **[!UICONTROL Email format]** 项保留 **[!UICONTROL Unknown]**&#x200B;为， **[!UICONTROL HTML]****[!UICONTROL Text]**&#x200B;或者，Adobe Campaign将自动检测（发送电子邮件时）要使用的日文格式，以便正确显示消息。

该自动检测系统基于在邮件规则集中定义的预定义域 **[!UICONTROL Management of Email Formats]** 的列表。 For more on managing email formats, refer to [this page](../../installation/using/email-deliverability.md#managing-email-formats).

### 限制和建议 {#limitations-and-recommendations}

发送将在日本提供商(Softbank、DoCoMo、KDDI AU)所运营的移动设备上读取的电子邮件时，会遇到一些限制。

因此，您必须：

* 仅使用JPEG或GIF格式的图像
* 创建文本和HTML部分严格低于10 000字节的投放（对于KDDI AU和DoCoMo）
* 使用大小（编码前）小于100 KB的图像
* 每封邮件使用的图像不超过20张
* 使用缩小的HTML格式（每个操作员可以使用有限数量的标记）

>[!NOTE]
>
>创建邮件时，应考虑每个操作员的特定限制。 请参阅:
>
>* 有关DoCoMo，请参 [阅本页](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* 有关KDDI AU，请参 [阅本页](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* 有关软件库，请参 [阅本页](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


### 测试电子邮件内容 {#testing-the-email-content}

#### Previewing the message {#previewing-the-message}

Adobe Campaign允许您检查消息格式是否适用于发送到日文手机。

定义内容并输入电子邮件主题后，可以检查消息创建时的显示和格式。

在内容 **[!UICONTROL Preview]** 编辑窗口的选项卡中，单击 **[!UICONTROL More... > Deco-mail diagnostic]** 可以：

* 检查HTML内容标记是否符合日文格式限制
* 检查邮件中的图像数量是否不超过格式规定的限制（20张图像）
* 检查邮件总大小（小于100kB）

   ![](assets/deco-mail_06.png)

#### 运行类型规则 {#running-typology-rule}

除了预览诊断之外，在发送验证或投放时还执行第二检查：特定类型规则 **[!UICONTROL Deco-mail check]**&#x200B;在分析期间启动。

>[!IMPORTANT]
>
>仅当至少一个类型规则被配置为以或格式接收电子邮件时，才 **[!UICONTROL Deco-mail (DoCoMo)]**&#x200B;执 **[!UICONTROL Decore Mail (Softbank)]** 行此 **[!UICONTROL Decoration Mail (KDDI AU)]** 收件人。

此类型规则允许您确保投放遵守日文运 [算符](#limitations-and-recommendations) （尤其是与电子邮件总大小、HTML和文本部分的大小、消息中的图像数以及HTML内容中的标记相关）定义的格式限制。

#### 发送校样{#sending-proofs}

您可以发送验证来测试投放。 当您发送验证时，如果您使用的是替代地址，请输入与所使用用户档案的电子邮件格式对应的地址。

例如，如果事先在上定义了用户档案的电子邮件格式，则可以用test@softbank.ne.jp替换用户档案的地址 **[!UICONTROL Decore Mail (Softbank)]**。

![](assets/deco-mail_05.png)

### 发送消息 {#sending-messages}

要向具有活动的日本电子邮件格式发送电子邮件至收件人，可以使用以下两种方式：

* 创建两个投放:一个仅适用于日语收件人，另一个适用于其他收件人-请参 [阅本节](#designing-a-specific-delivery-for-japanese-formats)。
* 创建单个投放,Adobe Campaign将自动检测要使用的格式——请参 [阅本节](#designing-a-delivery-for-all-formats)。

#### 为日文格式设计特定投放 {#designing-a-specific-delivery-for-japanese-formats}

您可以创建包含两个投放的工作流：一个在日本手机上阅读，另一个在标准电子邮件格式收件人上阅读。

为此，请在工作流 **[!UICONTROL Split]** 中使用活动，并将日文电子邮件格式（Deco邮件、装饰邮件和Decore邮件）定义为筛选条件。

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

#### 为所有格式设计投放 {#designing-a-delivery-for-all-formats}

当Adobe Campaign根据域(用户档案定义为、或的电子邮件格式)动 **[!UICONTROL Unknown]**&#x200B;态 **[!UICONTROL HTML]** 管理格式 **[!UICONTROL Text]** 时，您可以向所有收件人发送相同的投放。

与标准收件人一样，消息联系人将正确显示给日本手机上的用户。

>[!IMPORTANT]
>
>确保尊重与每个日文电子邮件格式（Deco邮件、装饰邮件和Decore邮件）相关的特殊功能。 For more information on limitations, refer to [this section](#limitations-and-recommendations).
