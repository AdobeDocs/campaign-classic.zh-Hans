---
title: 如何使用工作流数据
seo-title: 如何使用工作流数据
description: 如何使用工作流数据
seo-description: null
page-status-flag: never-activated
uuid: ed03f14b-1b53-426e-9213-22cb2f3deb19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: ec3844ca-8d80-4ddc-b08c-f18a6919bb28
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---


# 如何使用工作流数据{#how-to-use-workflow-data}

## 更新数据库 {#updating-the-database}

所有收集的数据都可用于更新数据库或投放。 例如，您可以丰富消息内容个性化的可能性（包括消息中的合同数、指定去年的平均购物车等） 或详细定位人群(向合同合同持有人发送消息，向1,000名最佳订阅者目标在线服务等)。 此数据也可以在列表中导出或存档。

### 列表和直接更新 {#lists-and-direct-updates}

Adobe Campaign库和现有列表的数据可以使用两个专用活动进行更新：

* 该活动 **[!UICONTROL List update]** 允许您将工作表存储在数据列表中。

   您可以选择现有列表或创建它。 在这种情况下，将计算名称和可能的记录文件夹。

   ![](assets/s_user_create_list.png)

   请参阅 [列表更新](../../workflow/using/list-update.md)。

* 活动 **[!UICONTROL Update data]** 将对数据库中的字段执行大量更新。

   For more on this, refer to [Update data](../../workflow/using/update-data.md).

### 订阅/退订管理 {#subscription-unsubscription-management}

要了解如何通过工作流向收件人订阅和取消订阅信息服务，请参阅 [订阅服务](../../workflow/using/subscription-services.md)。

## 通过工作流发送 {#sending-via-a-workflow}

### 投放活动 {#delivery-activity}

投放活动详见 [投放](../../workflow/using/delivery.md)。

### 丰富和定位投放 {#enriching-and-targeting-deliveries}

投放可以处理来自工作流的数据，以便自定义内容或在目标群体选择框架内。

例如，在直接邮件投放的框架中，您可以在提取文件中包含从工作流中执行的数据操作获取的附加数据：

![](assets/s_advuser_add_data_postal_mail.png)

除了常见的个性化字段之外，您还可以将工作流阶段的个性化字段添加到投放内容。 可以在投放向导中保留和访问工作流活动中定义的其他数据，如以下示例所示，以在直邮投放框架中定义输出文件的名称：

![](assets/s_advuser_using_additional_data.png)

工作流表中包含的数据由其名称标识： 它始终由targetData链 **接组成** 。 For more on this, refer to [Target data](../../workflow/using/data-life-cycle.md#target-data).

在电子邮件投放框架中，个性化字段还可以使用来自在定位工作流阶段执行的目标扩展的数据，如下例所示：

![](assets/s_advuser_add_data_email.png)

如果在定位段代码中指定了活动，则会将其添加到工作流表的特定列，并将提供该个性化字段。 要显示所有个性化字段，请单击可 **[!UICONTROL Target extension > Other...]** 通过个性化按钮访问的链接。

![](assets/s_advuser_segment_code_select.png)

## 导出数据 {#exporting-data}

### 压缩或加密文件 {#zipping-or-encrypting-a-file}

Adobe Campaign允许您导出压缩或加密文件。 在通过活动定义导 **[!UICONTROL Data extraction (file)]** 出时，您可以定义后处理以压缩或加密文件。

要做到这一点，请执行以下操作：

* 如果您的Adobe Campaign安装由Adobe托管： 向支持部 [门发](https://support.neolane.net) 送请求，要求在服务器上安装必要的实用程序。
* 如果您的Adobe Campaign安装是事先安装的： 安装要使用的实用程序(例如： GPG、GZIP)以及应用程序服务器上必需的密钥（加密密钥）。

然后，您可以使用命令或代码，如：

```
function encryptFile(file) {  
  var systemCommand = “gpg --encrypt --recipient  recipientToEncryptTo ” + file;  
  var result = execCommand(systemCommand, true); 
}
```

导入文件时，还可以解压缩或解密文件。 请参 [阅在处理之前解压或解密文件](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)。
