---
title: 附加文件
seo-title: 附加文件
description: 附加文件
seo-description: null
page-status-flag: never-activated
uuid: a4dc1908-a6ef-4bc8-a310-605fc80c34ca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: f3666c12-5e6f-452e-b1d6-b69a7e9f6f6e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 06f2106c7c37fd5f115d15f3530997571f1f8e70

---


# 附加文件{#attaching-files}

## 关于电子邮件附件 {#about-email-attachments}

您可以将一个或多个文件附加到电子邮件分发中。 有两种可能的情况：

* 选择一个文件，然后按原样将其附加到交付中。
* 为每个收件人个性化附件的内容。 在这种情况下，您需要创建计算 **出的附件**:根据收件人，在发送每条消息时计算附件的名称。 如果您有“可变数字打印”选项，则内容也可在交付时进行个性化并转 **换为PDF格式** 。

>[!NOTE]
>
>此类配置通常在交付模板中执行。 For more on this, refer to [About templates](../../delivery/using/about-templates.md).

## 附加本地文件 {#attaching-a-local-file}

要将本地文件附加到分发，请执行以下步骤。

>[!NOTE]
>
>可以将多个文件附加到分发。 附件可以采用任何格式，包括压缩格式。

1. 单击链 **[!UICONTROL Attachments]** 接。
1. 单击 **[!UICONTROL Add]** 按钮，然后单 **[!UICONTROL File...]** 击以选择要附加到交付的文件。

![](assets/s_ncs_user_wizard_email_attachement.png)

您还可以直接将文件拖放到分发字段中， **[!UICONTROL Attachments]** 或使用分发向导工具 **[!UICONTROL Attach]** 栏中的图标，

![](assets/s_ncs_user_wizard_add_file_ico.png)

1. 选择文件后，该文件将立即上传到服务器，以便在发送时可用。 它列在字段 **[!UICONTROL Attachments]** 中。

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## 创建计算的附件 {#creating-a-calculated-attachment}

在创建计算出的附件时，附件的名称可以在分析或发送每条消息时计算，并且取决于收件人。 还可以个性化并转换为PDF。

![](assets/s_ncs_user_wizard_attachment.png)

要创建个性化的附件，请执行以下步骤：

1. 单击链 **[!UICONTROL Attachments]** 接。
1. 单击按 **[!UICONTROL Add]** 钮，然后选择 **[!UICONTROL Calculated attachment]**。
1. 从下拉列表中选择 **[!UICONTROL Type]** 计算类型：

![](assets/s_ncs_user_wizard_email01_136.png)

可以使用以下选项：

* **在创建交付模板时指定文件名**
* **在发送每条消息时，文件内容会进行个性化并转换为PDF**
* **文件名称在分发分析过程中计算（它不能取决于收件人配置文件）**
* **文件名在每个收件人的发送时计算（取决于收件人）**

### 附加本地文件 {#attach-a-local-file}

如果附件是本地文件，请选择以下选项： **[!UICONTROL File name is specified when creating the delivery template]**. 该文件将在本地选中并上传到服务器。 按照以下步骤操作：

1. 在字段中选择要上传的 **[!UICONTROL Local file]** 文件。
1. 根据需要指定标签。 在消息传递系统中查看时，标签将替换文件名。 如果未指定任何内容，则默认情况下使用文件名。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. 如有必要，请选 **[!UICONTROL Upload file on the server]**&#x200B;择，然后单击以 **[!UICONTROL Update on server]** 开始传输。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

   然后，该文件在服务器上可用，以附加到从此模板创建的不同提交。

### 附加个性化信息 {#attach-a-personalized-message}

通过该选 **[!UICONTROL The file content is personalized and converted into PDF format at the time of delivery for each message]** 项，您可以选择带有个性化字段的细分，如预期收件人的姓和名。

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

对于此类型的附件，应用以下配置步骤：

1. 选择要上传的文件。

   >[!NOTE]
   >
   >必须在LibreOffice中创建源文件。 必须根据本节中详细介绍的先决条件配置 [实例](../../installation/using/before-starting.md)。

1. 根据需要指定标签。
1. 选 **[!UICONTROL Upload file on the server]**&#x200B;择，然后单击以 **[!UICONTROL Update on server]** 开始传输。
1. 可显示预览。 为此，请选择收件人。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. 分析您的交付，然后开始。

   每个收件人都会收到附于分发的个性化PDF。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)

### 附加计算文件 {#attach-a-calculated-file}

您可以在准备交付时计算附件名称。 为此，请选择选项 **[!UICONTROL The file name is calculated during delivery analysis (it cannot depend on the recipient)]**。

>[!NOTE]
>
>仅当由外部进程或工作流发送交付时，才使用此选项。

1. 指定要应用于附件的标签。
1. 在定义窗口中指定文件的访问路径及其确切名称。

   >[!CAUTION]
   >
   >服务器上必须存在该文件。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. 分析，然后开始交付。

   文件名计算可在分析日志中查看。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### 附加个性化文件 {#attach-a-personalized-file}

在选择附件时，您可以选择相应选项 **[!UICONTROL The file name is calculated during delivery for each recipient (it can depend on the recipient)]**。 然后，您可以将收件人个性化数据与要发送的文件名称进行映射。

>[!NOTE]
>
>仅当由外部进程或工作流发送交付时，才使用此选项。

1. 指定要应用于附件的标签。
1. 在定义窗口中指定文件的访问路径及其确切名称。 如果文件名是个性化的，您可以使用个性化字段作为相关值。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!CAUTION]
   >
   >服务器上必须存在该文件。

1. 分析，然后开始交付。

   在以下示例中，根据使用合并字段定义的附加文件名称选择了该附加文件。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### 附件设置 {#attachment-settings}

对于前两个选项，您可以选 **[!UICONTROL Upload file on the server]** 择相应的选项进行选择。 通过 **[!UICONTROL Update the file on the server]** 该链接可开始上传。

![](assets/s_ncs_user_wizard_email01_137.png)

将显示一条消息，告诉您文件已上传到服务器：

![](assets/s_ncs_user_wizard_email01_1371.png)

对于文件更改，将显示一条警告消息：

![](assets/s_ncs_user_wizard_email01_1372.png)

在该 **[!UICONTROL Advanced]** 选项卡中，您可以定义附加文件的高级选项：

* 您可以定义过滤器选项，以避免将附加文件发送到所有收件人。 该选项 **[!UICONTROL Enable filtering of recipients who will receive the attachment]** 激活用于定义收件人选择脚本的输入字段，该脚本必须在JavaScript中输入。
* 您可以编写文件名称的脚本，以便对其进行个性化设置。

   在窗口中输入文本，然后使用下拉列表中提供的个性化字段。 在以下示例中，文件名经过个性化设置，可包含当天的日期和收件人的姓名。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
