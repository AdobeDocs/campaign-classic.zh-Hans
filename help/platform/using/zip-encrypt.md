---
solution: Campaign Classic
product: campaign
title: 压缩或加密文件
description: 在处理之前，了解如何以Campaign Classic压缩或加密文件。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---


# 压缩或加密文件{#zipping-or-encrypting-a-file}

Adobe Campaign允许您导出压缩或加密文件。 通过&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活动定义导出时，可以定义后处理以压缩文件或加密文件。

要做到这一点，请执行以下操作：

1. 使用[控制面板](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)为实例安装GPG密钥对。

   >[!NOTE]
   >
   >控制面板适用于在AWS上托管的所有客户（预先托管其营销实例的客户除外）。

1. 如果Adobe Campaign安装由Adobe托管，请与[Adobe客户服务中心](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)联系，在服务器上安装必要的实用程序。
1. 如果您的Adobe Campaign安装是事先安装的，请安装您要使用的实用程序(例如：GPG、GZIP)以及应用程序服务器上必需的密钥（加密密钥）。

然后，您可以在活动的&#x200B;**[!UICONTROL Script]**&#x200B;选项卡或&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动中使用命令或代码。 在下面的用例中给出一个示例。

**相关主题：**

* [在处理文件之前解压缩或解密文件](../../platform/using/unzip-decrypt.md)
* [提取（文件）活动](../../workflow/using/extraction--file-.md)。

## 用例：使用安装在{#use-case-gpg-encrypt}控制面板上的密钥加密和导出数据

在此用例中，我们将构建一个工作流，以便使用控制面板上安装的密钥加密和导出数据。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#video)

执行此用例的步骤如下：

1. 使用GPG实用程序生成GPG密钥对（公共／私有），然后将公钥安装到控制面板上。 在[控制面板文档](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)中提供了详细步骤。

1. 在Campaign Classic中，构建一个工作流以导出数据，并使用通过控制面板安装的私钥对其加密。 为此，我们将按如下方式构建工作流：

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** 活动:在此示例中，我们要执行一个查询来目标要导出的数据库中的数据。
   * **[!UICONTROL Data extraction (file)]** 活动:将数据提取到文件中。
   * **[!UICONTROL JavaScript code]** 活动:加密要提取的数据。
   * **[!UICONTROL File transfer]** 活动:将数据发送到外部源（在本例中为SFTP服务器）。

1. 配置&#x200B;**[!UICONTROL Query]**&#x200B;活动以目标数据库中的所需数据。 如需详细信息，请参阅[此部分](../../workflow/using/query.md)。

1. 打开&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活动，然后根据您的需要配置它。 有关如何配置活动的全局概念在[此部分](../../workflow/using/extraction--file-.md)中可用。

   ![](assets/gpg-data-extraction.png)

1. 打开&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动，然后复制并粘贴下面的命令以加密要提取的数据。

   >[!IMPORTANT]
   >
   >确保将命令中的&#x200B;**指纹**&#x200B;值替换为控制面板上安装的公钥的指纹。

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch --yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. 打开&#x200B;**[!UICONTROL File transfer]**&#x200B;活动，然后指定要将文件发送到的SFTP服务器。 有关如何配置活动的全局概念在[此部分](../../workflow/using/file-transfer.md)中可用。

   ![](assets/gpg-file-transfer.png)

1. 您现在可以运行工作流。 执行目标后，查询的数据将导出到SFTP服务器中，生成加密的。gpg文件。

## 教程视频{#video}

此视频还介绍了如何使用GPG密钥加密数据

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供其他Campaign Classic操作方法视频。[
