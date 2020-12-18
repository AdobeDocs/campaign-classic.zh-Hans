---
solution: Campaign Classic
product: campaign
title: 如何使用工作流数据
description: 了解如何使用工作流数据
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 3%

---


# 如何使用工作流数据{#how-to-use-workflow-data}

## 更新数据库{#updating-the-database}

所有收集的数据都可用于更新数据库或投放。 例如，您可以丰富消息内容个性化的可能性（包括消息中的合同数、指定去年的平均购物车等） 或详细定位人群(向合同合同持有人发送消息，向1,000名最佳订阅者目标在线服务等)。 此数据也可以在列表中导出或存档。

### 列表和直接更新{#lists-and-direct-updates}

Adobe Campaign库和现有列表的数据可以使用两个专用活动进行更新：

* **[!UICONTROL List update]**&#x200B;活动允许您将工作表存储在数据列表中。

   您可以选择现有列表或创建它。 在这种情况下，将计算名称和可能的记录文件夹。

   ![](assets/s_user_create_list.png)

   请参阅[列表更新](../../workflow/using/list-update.md)。

* **[!UICONTROL Update data]**&#x200B;活动对数据库中的字段执行大量更新。

   有关详细信息，请参阅[更新数据](../../workflow/using/update-data.md)。

### 订阅/退订管理{#subscription-unsubscription-management}

要了解如何通过工作流订阅和取消订阅收件人信息服务，请参阅[订阅服务](../../workflow/using/subscription-services.md)。

## 通过工作流{#sending-via-a-workflow}发送

### 投放活动{#delivery-activity}

投放活动详见[投放](../../workflow/using/delivery.md)。

### 丰富和定向投放{#enriching-and-targeting-deliveries}

投放可以处理来自工作流的数据，以便自定义内容或在目标群体选择框架内。

例如，在直接邮件投放的框架中，您可以在提取文件中包含从工作流中执行的数据操作获取的附加数据：

![](assets/s_advuser_add_data_postal_mail.png)

除了常见的个性化字段之外，您还可以将工作流阶段的个性化字段添加到投放内容。 可以在投放向导中保留和访问工作流活动中定义的其他数据，如以下示例所示，以在直邮投放框架中定义输出文件的名称：

![](assets/s_advuser_using_additional_data.png)

工作流表中包含的数据由其名称标识：它始终由&#x200B;**targetData**&#x200B;链接组成。 有关详细信息，请参阅[目标数据](../../workflow/using/data-life-cycle.md#target-data)。

在电子邮件投放框架中，个性化字段还可以使用来自在定位工作流阶段执行的目标扩展的数据，如下例所示：

![](assets/s_advuser_add_data_email.png)

如果在定位段代码中指定了活动，则会将其添加到工作流表的特定列，并将提供该个性化字段。 要显示所有个性化字段，请单击可通过个性化按钮访问的&#x200B;**[!UICONTROL Target extension > Other...]**&#x200B;链接。

![](assets/s_advuser_segment_code_select.png)

## 导出数据 {#exporting-data}

### 压缩或加密文件{#zipping-or-encrypting-a-file}

Adobe Campaign允许您导出压缩或加密文件。 通过&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活动定义导出时，可以定义后处理以压缩文件或加密文件。

要做到这一点，请执行以下操作：

1. 使用[控制面板](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)为实例安装GPG密钥对。

   >[!NOTE]
   >
   >控制面板适用于在AWS上托管的所有客户（预先托管其营销实例的客户除外）。

1. 如果Adobe Campaign安装由Adobe托管，请与Adobe客户服务部门联系，在服务器上安装必要的实用程序。
1. 如果您的Adobe Campaign安装是事先安装的，请安装您要使用的实用程序(例如：GPG、GZIP)以及应用程序服务器上必需的密钥（加密密钥）。

然后，您可以在活动的&#x200B;**[!UICONTROL Script]**&#x200B;选项卡或&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动中使用命令或代码。 在下面的用例中给出一个示例。

**相关主题：**

* [在处理文件之前解压缩或解密文件](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)
* [提取（文件）活动](../../workflow/using/extraction--file-.md)。

### 用例：使用安装在{#use-case-gpg-encrypt}控制面板上的密钥加密和导出数据

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

### 教程视频{#video}

此视频还介绍了如何使用GPG密钥加密数据

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

此处[提供其他Campaign Classic操作方法视频。](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)
