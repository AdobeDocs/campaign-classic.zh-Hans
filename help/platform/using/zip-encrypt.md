---
product: campaign
title: 压缩或加密文件
description: 了解在处理之前如何在Campaign中压缩或加密文件
feature: Data Management, Encryption
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: 58998fa2480a33776507a434ed846541ac19e58b
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 5%

---

# 压缩或加密文件 {#zipping-or-encrypting-a-file}

Adobe Campaign允许您导出压缩或加密文件。 通过定义导出时 **[!UICONTROL Data extraction (file)]** 活动，您可以将后处理定义为zip或加密文件。

要做到这一点，请执行以下操作：

1. 使用为您的实例安装GPG密钥对 [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >控制面板仅限管理员用户使用，并且仅适用于某些Campaign版本。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hans)
   >

1. 如果您安装的Adobe Campaign由Adobe托管，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 在服务器上安装必要的实用程序。
1. 如果内部部署了Adobe Campaign，请在应用程序服务器上安装要使用的实用程序（例如：GPG、GZIP）以及必需的密钥（加密密钥）。

然后，您可以在以下位置使用命令或代码 **[!UICONTROL Script]** 选项卡中或在 **[!UICONTROL JavaScript code]** 活动。 以下用例中将显示一个示例。

**相关主题：**

* [在处理之前解压缩或解密文件](../../platform/using/unzip-decrypt.md)
* [数据提取（文件）活动](../../workflow/using/extraction--file-.md).

## 用例：使用安装在控制面板上的密钥加密和导出数据 {#use-case-gpg-encrypt}

在此使用案例中，我们将构建一个工作流，以便使用安装在控制面板上的密钥加密和导出数据。

![](assets/do-not-localize/how-to-video.png) [通过观看视频了解此功能](#video)

执行此用例的步骤如下：

1. 使用GPG实用程序生成GPG密钥对（公共/私有），然后将公共密钥安装到控制面板上。 有关详细步骤，请参阅 [控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

1. 在Campaign Classic中，构建一个工作流以导出数据，并使用已通过控制面板安装的私钥对其进行加密。 为此，我们将构建一个工作流，如下所示：

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** 活动：在本例中，我们要执行查询以定向要导出的数据库中的数据。
   * **[!UICONTROL Data extraction (file)]** 活动：将数据提取到文件中。
   * **[!UICONTROL JavaScript code]** 活动：加密要提取的数据。
   * **[!UICONTROL File transfer]** 活动：将数据发送到外部源（在本例中为SFTP服务器）。

1. 配置 **[!UICONTROL Query]** 活动，从数据库中定位所需的数据。 如需详细信息，请参阅[此小节](../../workflow/using/query.md)。

1. 打开 **[!UICONTROL Data extraction (file)]** 活动，然后根据需要进行配置。 有关如何配置活动的全局概念，请参见 [本节](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. 打开 **[!UICONTROL JavaScript code]** 活动，然后复制并粘贴以下命令以加密要提取的数据。

   >[!IMPORTANT]
   >
   >确保更换 **指纹** 值，该值来自在控制面板上安装了公钥的指纹。

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

1. 打开 **[!UICONTROL File transfer]** 活动，然后指定要将文件发送到的SFTP服务器。 有关如何配置活动的全局概念，请参见 [本节](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. 您现在可以运行工作流。 执行查询后，查询的数据目标将导出到SFTP服务器中，并转换为加密的.gpg文件。

## 教程视频 {#video}

以下视频介绍了如何使用GPG密钥加密数据，该视频还包含以下内容

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
