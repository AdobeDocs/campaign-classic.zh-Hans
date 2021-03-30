---
solution: Campaign Classic
product: campaign
title: 解压缩或解密文件
description: 了解如何在处理之前在Campaign Classic中解压缩或解密文件。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 2%

---


# 解压缩或解密文件{#unzipping-or-decrypting-a-file-before-processing}

Adobe Campaign允许您导入压缩或加密文件。 在[数据加载（文件）](../../workflow/using/data-loading--file-.md)活动中读取之前，您可以定义预处理以解压缩或解密文件。

要做到这一点：

1. 使用[控制面板](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)生成公钥/私钥对。

   >[!NOTE]
   >
   >控制面板可供所有管理员用户访问。 授予用户管理员访问权限的步骤详见[此页](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel)。
   >
   >请注意，您的实例必须托管在AWS上，并使用最新的[Gold Standard](../../rn/using/gs-overview.md)版本或最新的[ GA版本(21.1)](../../rn/using/latest-release.md)进行升级。 了解如何在[本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中检查您的版本。 要检查您的实例是否托管在AWS上，请按照[本页](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)中详细介绍的步骤操作。

1. 如果Adobe Campaign安装由Adobe托管，请联系[Adobe客户服务中心](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)，以在服务器上安装必要的实用程序。
1. 如果您的Adobe Campaign安装是预置的，请安装您要使用的实用程序(例如：GPG、GZIP)以及应用程序服务器上必需的密钥（加密密钥）。

然后，您可以在工作流中使用所需的预处理命令：

1. 在工作流中添加和配置&#x200B;**[!UICONTROL File transfer]**&#x200B;活动。
1. 添加&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活动并定义文件格式。
1. 勾选 **[!UICONTROL Pre-process the file]** 选项。
1. 指定要应用的预处理命令。
1. 添加其他活动以管理来自文件的数据。
1. 保存并执行您的工作流。

在下面的使用案例中给出了示例。

**相关主题：**

* [数据加载（文件）活动](../../workflow/using/data-loading--file-.md)。
* [压缩或加密文件](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

## 用例：导入使用由控制面板{#use-case-gpg-decrypt}生成的密钥加密的数据

在此用例中，我们将构建一个工作流，以便使用在控制面板中生成的密钥导入已在外部系统中加密的数据。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#video)

执行此用例的步骤如下：

1. 使用控制面板生成密钥对（公共/私有）。 在[控制面板文档](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)中提供了详细步骤。

   * 公钥将与外部系统共享，外部系统将使用公钥加密要发送到活动的数据。
   * Campaign Classic将使用私钥解密传入的加密数据。

   ![](assets/gpg_generate.png)

1. 在外部系统中，使用从控制面板下载的公钥对要导入到Campaign Classic的数据进行加密。

1. 在Campaign Classic中，构建一个工作流以导入加密数据并使用通过控制面板安装的私钥对其解密。 为此，我们将构建一个工作流，如下所示：

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** 活动:将文件从外部源传输到Campaign Classic。在此示例中，我们希望从SFTP服务器传输文件。
   * **[!UICONTROL Data loading (file)]** 活动:将文件中的数据加载到控制面板中，并使用在数据中生成的私钥对其进行解密。

1. 打开&#x200B;**[!UICONTROL File transfer]**&#x200B;活动，然后指定要从中导入加密.gpg文件的外部帐户。

   ![](assets/gpg_key_transfer.png)

   有关如何配置活动的全局概念在[本节](../../workflow/using/file-transfer.md)中可用。

1. 打开&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活动，然后根据需要配置它。 有关如何配置活动的全局概念在[本节](../../workflow/using/data-loading--file-.md)中可用。

   为活动添加预处理阶段以解密传入数据。 要执行此操作，请选择&#x200B;**[!UICONTROL Pre-process the file]**&#x200B;选项，然后在&#x200B;**[!UICONTROL Command]**&#x200B;字段中复制并粘贴此解密命令：

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >在此示例中，我们使用默认由控制面板使用的密码，即“密码短语”。
   >
   >如果您过去通过客户关怀请求在实例上安装了GPG密钥，则密码可能已更改，并且默认情况下与密码不同。

1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;确认活动配置。

1. 您现在可以运行工作流。 执行后，您可以签入工作流日志，确认已执行解密，且已导入文件中的数据。

   ![](assets/gpg_run.png)

## 教程视频{#video}

此视频演示如何使用GPG密钥解密数据。

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

其他Campaign Classic操作视频[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)可用。
