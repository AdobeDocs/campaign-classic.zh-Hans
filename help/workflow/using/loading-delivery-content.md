---
solution: Campaign Classic
product: campaign
title: 加载投放内容
description: 加载投放内容
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 3%

---


# 加载投放内容{#loading-delivery-content}

如果您的投放内容位于AmazonS3、FTP或SFTP服务器上的HTML文件中，则可以轻松将此内容加载到Adobe Campaign投放中。

操作步骤：

1. 如果您尚未在Adobe Campaign与托管内容文件的(S)FTP服务器之间定义连接，请在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**&#x200B;中新建一个S3、FTP或SFTP外部帐户。 在此外部帐户中指定用于建立与S3或(S)FTP服务器连接的地址和凭据。

   以下是S3外部帐户的示例：

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. 新建一个工作流，例如从&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**&#x200B;创建。
1. 将&#x200B;**[!UICONTROL File transfer]**&#x200B;活动添加到工作流中，并通过指定

   * 用于连接到S3或(S)FTP服务器的外部帐户。
   * 文件在S3或(S)FTP服务器上的路径。

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. 添加&#x200B;**[!UICONTROL Delivery]**&#x200B;活动并将其连接到&#x200B;**[!UICONTROL File transfer]**&#x200B;活动的出站过渡。 按如下方式配置它：

   * 投放:根据您的需要，它可以是系统中已创建的特定投放，也可以是基于现有模板的新投放。
   * 收件人:在此示例中，会考虑在目标本身中指定投放。
   * 内容：即使内容是在上一个活动中导入的，请选择&#x200B;**[!UICONTROL Specified in the delivery]**。 由于内容直接从位于远程服务器上的文件导入，因此当工作流处理时，它没有标识符，无法标识为来自入站事件。
   * 要执行的操作：选择&#x200B;**[!UICONTROL Save]**&#x200B;以保存投放，并在执行工作流后能够从&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**&#x200B;访问它。

   ![](assets/delivery_loadcontent_activityexample.png)

1. 在&#x200B;**[!UICONTROL Delivery]**&#x200B;活动的&#x200B;**[!UICONTROL Script]**&#x200B;选项卡中，添加以下命令以加载投放中导入的文件的内容：

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. 保存并执行工作流。 在&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**&#x200B;下创建包含已加载内容的新投放。

>[!NOTE]
>
>有关SFTP服务器使用情况的最佳实践和疑难解答，请参阅本页](../../platform/using/sftp-server-usage.md)中的[。
