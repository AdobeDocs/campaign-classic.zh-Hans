---
solution: Campaign Classic
product: campaign
title: 解压或解密文件
description: 了解如何在处理之前以Campaign Classic解压缩或解密文件。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 2%

---


# 解压或解密文件{#unzipping-or-decrypting-a-file-before-processing}

Adobe Campaign允许您导入压缩或加密文件。 在[数据加载（文件）](../../workflow/using/data-loading--file-.md)活动中读取它们之前，您可以定义预处理以解压缩或解密文件。

要做到这一点，请执行以下操作：

1. 使用[控制面板](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)生成公钥／私钥对。

   >[!NOTE]
   >
   >控制面板适用于在AWS上托管的所有客户（预先托管其营销实例的客户除外）。

1. 如果Adobe Campaign安装由Adobe托管，请与[Adobe客户服务中心](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)联系，在服务器上安装必要的实用程序。
1. 如果您的Adobe Campaign安装是事先安装的，请安装您要使用的实用程序(例如：GPG、GZIP)以及应用程序服务器上必需的密钥（加密密钥）。

然后，您可以在工作流中使用所需的预处理命令：

1. 在工作流中添加和配置&#x200B;**[!UICONTROL File transfer]**&#x200B;活动。
1. 添加&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活动并定义文件格式。
1. 勾选 **[!UICONTROL Pre-process the file]** 选项。
1. 指定要应用的预处理命令。
1. 添加其他活动以管理来自文件的数据。
1. 保存并执行您的工作流。

在下面的用例中给出一个示例。

**相关主题：**

* [数据加载（文件）活动](../../workflow/using/data-loading--file-.md)。
* [压缩或加密文件](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

## 用例：导入使用控制面板{#use-case-gpg-decrypt}生成的密钥加密的数据

在此用例中，我们将构建一个工作流，以便使用在控制面板中生成的密钥导入外部系统中已加密的数据。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#video)

执行此用例的步骤如下：

1. 使用控制面板生成密钥对（公共／私有）。 在[控制面板文档](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)中提供了详细步骤。

   * 公钥将与外部系统共享，外部系统将使用公钥加密要发送给活动的数据。
   * Campaign Classic将使用私钥解密传入的加密数据。

   ![](assets/gpg_generate.png)

1. 在外部系统中，使用从控制面板下载的公钥加密要导入到Campaign Classic的数据。

1. 在Campaign Classic中，构建一个工作流以导入加密数据，并使用通过控制面板安装的私钥对其进行解密。 为此，我们将按如下方式构建工作流：

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** 活动:将文件从外部源传输到Campaign Classic。在此示例中，我们希望从SFTP服务器传输文件。
   * **[!UICONTROL Data loading (file)]** 活动:将文件中的数据加载到控制面板库，然后使用在数据库中生成的私钥进行解密。

1. 打开&#x200B;**[!UICONTROL File transfer]**&#x200B;活动，然后指定要从中导入加密的。gpg文件的外部帐户。

   ![](assets/gpg_key_transfer.png)

   有关如何配置活动的全局概念在[此部分](../../workflow/using/file-transfer.md)中可用。

1. 打开&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活动，然后根据您的需要配置它。 有关如何配置活动的全局概念在[此部分](../../workflow/using/data-loading--file-.md)中可用。

   为活动添加预处理阶段，以解密传入数据。 为此，请选择&#x200B;**[!UICONTROL Pre-process the file]**&#x200B;选项，然后在&#x200B;**[!UICONTROL Command]**&#x200B;字段中复制并粘贴此解密命令：

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >在本示例中，我们使用控制面板默认使用的密码短语，即“密码短语”。
   >
   >如果您过去通过客户关怀请求在实例上安装了GPG密钥，则该密码可能已更改，并且默认情况下与该密码不同。

1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;以确认活动配置。

1. 您现在可以运行工作流。 一旦执行，您就可以检入已执行解密的工作流日志以及已导入文件中的数据。

   ![](assets/gpg_run.png)

## 教程视频{#video}

此视频演示如何使用GPG密钥解密数据。

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供其他Campaign Classic操作方法视频。[
