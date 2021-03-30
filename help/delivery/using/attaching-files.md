---
solution: Campaign Classic
product: campaign
title: 附加文件
description: 附加文件
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 9237e11edec4114b2bd0932e6128775f36aad27c
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 1%

---


# 将文件附加到电子邮件{#attaching-files}

## 关于电子邮件附件{#about-email-attachments}

您可以将一个或多个文件附加到电子邮件投放。

>[!NOTE]
>
>为避免出现性能问题，建议在每封电子邮件中不要包含多个附件。 建议的阈值可以从[Campaign Classic选项的列表](../../installation/using/configuring-campaign-options.md#delivery)配置。

有两种可能的情况：

* 选择一个文件，并按原样将其附加到投放。
* 为每个收件人个性化附件内容。 在这种情况下，您需要创建&#x200B;**计算附件**:在投放时，将根据收件人计算每个消息的附件名称。 如果您具有&#x200B;**可变数字打印**&#x200B;选项，则内容也可在投放时进行个性化并转换为PDF格式。

>[!NOTE]
>
>此类配置通常在投放模板中执行。 有关详细信息，请参阅[关于模板](../../delivery/using/about-templates.md)。

## 附加本地文件{#attaching-a-local-file}

要将本地文件附加到投放，请执行以下步骤。

>[!NOTE]
>
>可以向投放附加多个文件。 附件可以采用任何格式，包括压缩格式。

1. 单击&#x200B;**[!UICONTROL Attachments]**&#x200B;链接。
1. 单击 **[!UICONTROL Add]** 按钮。
1. 单击&#x200B;**[!UICONTROL File...]**&#x200B;以选择要附加到投放的文件。

   ![](assets/s_ncs_user_wizard_email_attachement.png)

您还可以直接将文件拖放到投放&#x200B;**[!UICONTROL Attachments]**&#x200B;字段中，或使用投放向导工具栏中的&#x200B;**[!UICONTROL Attach]**&#x200B;图标。

![](assets/s_ncs_user_wizard_add_file_ico.png)

选择文件后，该文件将立即上传到服务器，以便在投放时可用。 它列在&#x200B;**[!UICONTROL Attachments]**&#x200B;字段中。

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## 创建计算附件{#creating-a-calculated-attachment}

创建计算的附件时，附件的名称可以在分析或投放每条消息时计算，并取决于收件人。 还可以个性化并转换为PDF。

![](assets/s_ncs_user_wizard_attachment.png)

要创建个性化附件，请执行以下步骤：

1. 单击&#x200B;**[!UICONTROL Attachments]**&#x200B;链接。
1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮，然后选择&#x200B;**[!UICONTROL Calculated attachment]**。
1. 从&#x200B;**[!UICONTROL Type]**&#x200B;下拉列表中选择计算类型：

![](assets/s_ncs_user_wizard_email01_136.png)

可以使用以下选项：

* **创建投放模板时指定文件名**
* **在投放每条消息时，文件内容会进行个性化并转换为PDF**
* **文件名是在投放分析期间计算的(它不能取决于收件人用户档案)**
* **在投放时计算每个收件人的文件名(它取决于收件人)**

### 附加本地文件{#attach-a-local-file}

如果附件是本地文件，请选择以下选项：**[!UICONTROL File name is specified when creating the delivery template]**。 将在本地选择文件并上传到服务器。 按照下面的步骤进行操作：

1. 在&#x200B;**[!UICONTROL Local file]**&#x200B;字段中选择要上载的文件。
1. 根据需要指定标签。 在消息系统中查看时，标签将替换文件名。 如果未指定任何内容，则默认情况下使用文件名。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. 如有必要，选择&#x200B;**[!UICONTROL Upload file on the server]**，然后单击&#x200B;**[!UICONTROL Update on server]**&#x200B;以开始传输。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

随后，该文件可在服务器上用于附加到从此模板创建的不同投放。

### 附加个性化消息{#attach-a-personalized-message}

选项&#x200B;**[!UICONTROL The file content is personalized and converted into PDF format at the time of delivery for each message]**&#x200B;允许您选择包含个性化字段的文件，如预期收件人的姓和名。

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

对于此类附件，应用以下配置步骤：

1. 选择要上载的文件。
1. 根据需要指定标签。
1. 选择&#x200B;**[!UICONTROL Upload file on the server]**，然后单击&#x200B;**[!UICONTROL Update on server]**&#x200B;以开始传输。
1. 您可以显示预览。 要执行此操作，请选择收件人。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. 分析您的投放，然后开始它。

   每个收件人都会收到附加到投放的个性化PDF。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)

>[!NOTE]
>
>为避免性能问题，如果您将动态下载的图像作为附件包含在个性化URL中，则默认情况下，每个图像大小不应超过100,000字节。 可以从[Campaign Classic选项的列表](../../installation/using/configuring-campaign-options.md#delivery)配置此推荐阈值。

### 附加计算文件{#attach-a-calculated-file}

您可以在准备投放时计算附件名称。 要执行此操作，请选择选项&#x200B;**[!UICONTROL The file name is calculated during delivery analysis (it cannot depend on the recipient)]**。

>[!NOTE]
>
>此选项仅在外部进程或工作流发送投放时使用。

1. 指定要应用于附件的标签。
1. 在定义窗口中指定文件的访问路径及其确切名称。

   >[!IMPORTANT]
   >
   >服务器上必须存在该文件。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. 分析然后开始投放。

   文件名计算可在分析日志中查看。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### 附加个性化文件{#attach-a-personalized-file}

选择附件时，可以选择选项&#x200B;**[!UICONTROL The file name is calculated during delivery for each recipient (it can depend on the recipient)]**。 然后，您可以将收件人个性化数据与要发送的文件的名称进行映射。

>[!NOTE]
>
>此选项仅在外部进程或工作流发送投放时使用。

1. 指定要应用于附件的标签。
1. 在定义窗口中指定文件的访问路径及其确切名称。 如果文件名是个性化的，则可以使用个性化字段作为相关值。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!IMPORTANT]
   >
   >服务器上必须存在该文件。

1. 分析然后开始投放。

   在以下示例中，根据使用合并字段定义的文件名称选择附加文件。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### 附件设置{#attachment-settings}

对于前两个选项，您可以通过选择相应的选项来选择&#x200B;**[!UICONTROL Upload file on the server]**。 **[!UICONTROL Update the file on the server]**&#x200B;链接允许您开始上传。

![](assets/s_ncs_user_wizard_email01_137.png)

将显示一条消息，告诉您文件已上载到服务器：

![](assets/s_ncs_user_wizard_email01_1371.png)

对于文件更改，将显示一条警告消息：

![](assets/s_ncs_user_wizard_email01_1372.png)

使用&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡可以定义附加文件的高级选项：

* 您可以定义筛选器选项以避免将附加的文件发送到所有收件人。 选项&#x200B;**[!UICONTROL Enable filtering of recipients who will receive the attachment]**&#x200B;激活用于定义收件人选择脚本的输入字段，该脚本必须在JavaScript中输入。
* 您可以编写文件名称的脚本，以便对其进行个性化设置。

   在窗口中输入文本，然后使用下拉式列表中提供的个性化字段。 在以下示例中，文件名是个性化的，以包含今天的日期和收件人的名称。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
