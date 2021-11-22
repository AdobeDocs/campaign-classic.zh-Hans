---
product: campaign
title: 压缩或加密文件
description: 了解如何在处理之前在Campaign Classic中压缩或加密文件。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 8%

---

# Zip或加密文件 {#zipping-or-encrypting-a-file}

![](../../assets/common.svg)

Adobe Campaign允许您导出压缩或加密文件。 在定义通过 **[!UICONTROL Data extraction (file)]** 活动时，您可以定义后处理以压缩文件或加密文件。

要实现此目的，请执行以下操作：

1. 使用 [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=en#encrypting-data).

   >[!NOTE]
   >
   >控制面板仅限管理员用户，并且仅适用于某些Campaign版本。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hans)

1. 如果Adobe Campaign安装由Adobe托管，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 以在服务器上安装必要的实用程序。
1. 如果您在内部部署安装Adobe Campaign，请安装您要使用的实用程序(例如：GPG、GZIP)以及应用程序服务器上必需的密钥（加密密钥）。

然后，您可以在 **[!UICONTROL Script]** 选项卡，或 **[!UICONTROL JavaScript code]** 活动。 下面的用例中提供了一个示例。

**相关主题：**

* [在处理之前解压缩或解密文件](../../platform/using/unzip-decrypt.md)
* [数据提取（文件）活动](../../workflow/using/extraction--file-.md).

## 用例：使用安装在控制面板上的密钥加密和导出数据 {#use-case-gpg-encrypt}

在此用例中，我们将构建一个工作流，以便使用安装在控制面板上的密钥加密和导出数据。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#video)

执行此用例的步骤如下：

1. 使用GPG实用程序生成GPG密钥对（公钥/私钥），然后将公钥安装到控制面板上。 有关详细步骤，请参阅 [控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=en#encrypting-data).

1. 在Campaign Classic中，构建用于导出数据的工作流，并使用通过控制面板安装的私钥对其加密。 为此，我们将构建一个工作流，如下所示：

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** 活动：在本例中，我们要执行查询以定向要导出的数据库中的数据。
   * **[!UICONTROL Data extraction (file)]** 活动：将数据提取到文件中。
   * **[!UICONTROL JavaScript code]** 活动：加密要提取的数据。
   * **[!UICONTROL File transfer]** 活动：将数据发送到外部源（在本例中为SFTP服务器）。

1. 配置 **[!UICONTROL Query]** 活动来定位数据库中的所需数据。 如需详细信息，请参阅[此部分](../../workflow/using/query.md)。

1. 打开 **[!UICONTROL Data extraction (file)]** 活动，然后根据您的需求对其进行配置。 有关如何配置活动的全局概念可在 [此部分](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. 打开 **[!UICONTROL JavaScript code]** 活动，然后复制并粘贴以下命令以加密要提取的数据。

   >[!IMPORTANT]
   >
   >确保将 **指纹** 值，其中包含控制面板上安装的公钥的指纹。

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

1. 打开 **[!UICONTROL File transfer]** 活动，然后指定要将文件发送到的SFTP服务器。 有关如何配置活动的全局概念可在 [此部分](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. 您现在可以运行工作流。 执行该请求后，查询所定向的数据将导出到SFTP服务器中，并生成一个加密的.gpg文件。

## 教程视频 {#video}

此视频还介绍了如何使用GPG密钥加密数据，该密钥在

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
