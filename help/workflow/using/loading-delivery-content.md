---
title: 加载交付内容
seo-title: 加载交付内容
description: 加载交付内容
seo-description: null
page-status-flag: never-activated
uuid: f2004fb0-9beb-463f-9903-10f291b3663e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 3667da3d-4940-4128-8878-f1ee67216f56
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 加载交付内容{#loading-delivery-content}

如果您的交付内容位于Amazon S3、FTP或SFTP服务器上的HTML文件中，则可以轻松将此内容加载到Adobe Campaign交付中。

操作步骤：

1. 如果您尚未在Adobe Campaign和承载内容文件的(S)FTP服务器之间定义连接，请在 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** >中新建一个S3、FTP或SFTP外部帐户 **[!UICONTROL External Accounts]**。 在此外部帐户中指定用于建立与S3或(S)FTP服务器连接的地址和凭据。

   以下是S3外部帐户的示例：

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. 创建新工作流，例如，从 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**。
1. 将活动 **[!UICONTROL File transfer]** 添加到工作流中，并通过指定

   * 用于连接到S3或(S)FTP服务器的外部帐户。
   * 文件在S3或(S)FTP服务器上的路径。
   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. 添加活 **[!UICONTROL Delivery]** 动并将其连接到活动的出站转 **[!UICONTROL File transfer]** 换。 配置如下：

   * 交付：根据您的需求，它可以是系统中已创建的特定交付，也可以是基于现有模板的新交付。
   * 收件人：在本例中，将目标视为在交付本身中指定。
   * 内容：即使内容已导入上一个活动，也可选择 **[!UICONTROL Specified in the delivery]**。 由于内容直接从位于远程服务器上的文件导入，因此当工作流处理时，它没有标识符，并且不能标识为来自入站事件。
   * 要执行的操作：选择 **[!UICONTROL Save]** 以保存传送，并在执行工作流后，从 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** 访问它。
   ![](assets/delivery_loadcontent_activityexample.png)

1. 在活动 **[!UICONTROL Script]** 的选项卡中，添 **[!UICONTROL Delivery]** 加以下命令，以在分发中加载导入的文件的内容：

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. 保存并执行工作流。 将在 **[!UICONTROL Campaign management]** >下创建包含加载内容的新分发 **[!UICONTROL Deliveries]**。

>[!NOTE]
>
>有关SFTP服务器使用的最佳实践和疑难解答， [请参阅本页](../../platform/using/sftp-server-usage.md)。

