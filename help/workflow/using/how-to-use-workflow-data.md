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
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 如何使用工作流数据{#how-to-use-workflow-data}

## 更新数据库 {#updating-the-database}

所有收集的数据都可用于更新数据库或提交中。 例如，您可以丰富消息内容个性化的可能性（包括消息中的合同数、指定去年的平均购物车等）或详细定位人口（向合同合同持有人发送消息，瞄准在线服务的1,000个最佳订阅者，等等）。 此数据也可以导出或存档在列表中。

### 列表和直接更新 {#lists-and-direct-updates}

Adobe Campaign数据库和现有列表的数据可以使用两个专用活动进行更新：

* 该活 **[!UICONTROL List update]** 动允许您将工作表存储在数据列表中。

   您可以选择现有列表或创建它。 在这种情况下，将计算名称和可能的记录文件夹。

   ![](assets/s_user_create_list.png)

   请参阅 [列表更新](../../workflow/using/list-update.md)。

* 活 **[!UICONTROL Update data]** 动会对数据库中的字段执行成批更新。

   For more on this, refer to [Update data](../../workflow/using/update-data.md).

### 订阅／取消订阅管理 {#subscription-unsubscription-management}

要了解如何通过工作流向信息服务订阅和取消订阅收件人，请参阅订 [阅服务](../../workflow/using/subscription-services.md)。

## 通过工作流发送 {#sending-via-a-workflow}

### 交付活动 {#delivery-activity}

交付活动在交付中详 [细介绍](../../workflow/using/delivery.md)。

### 丰富和定向递送 {#enriching-and-targeting-deliveries}

提交可以处理来自工作流的数据，以便自定义内容或在目标人口选择框架内。

例如，在直邮递送的框架内，您可以在提取文件中包含从工作流中执行的数据操作中获取的附加数据：

![](assets/s_advuser_add_data_postal_mail.png)

除了通常的个性化字段之外，您还可以将个性化字段从工作流阶段添加到交付内容。 可以在传送向导中保留和访问工作流活动中定义的其他数据，如下例所示，以便在直接邮件传送框架中定义输出文件的名称：

![](assets/s_advuser_using_additional_data.png)

工作流表中包含的数据由其名称标识：它始终由targetData链接 **组成** 。 For more on this, refer to [Target data](../../workflow/using/executing-a-workflow.md#target-data).

在电子邮件交付框架中，个性化字段还可以使用在定位工作流程阶段执行的目标扩展中的数据，如下例所示：

![](assets/s_advuser_add_data_email.png)

如果在定位活动中指定了区段代码，则会将其添加到工作流表的特定列，并将提供区段代码和个性化字段。 要显示所有个性化字段，请单击可 **[!UICONTROL Target extension > Other...]** 通过个性化按钮访问的链接。

![](assets/s_advuser_segment_code_select.png)

## 导出数据 {#exporting-data}

### 压缩或加密文件 {#zipping-or-encrypting-a-file}

Adobe Campaign允许您导出压缩或加密文件。 在通过活动定义导出 **[!UICONTROL Data extraction (file)]** 时，您可以定义后处理以压缩或加密文件。

要做到这一点，请执行以下操作：

* 如果您的Adobe Campaign安装由Adobe托管：向支持部门发 [送请求](https://support.neolane.net) ，要求在服务器上安装必要的实用程序。
* 如果您安装的Adobe Campaign是内部部署：安装要使用的实用程序(例如：GPG、GZIP)以及应用程序服务器上必需的密钥（加密密钥）。

然后，您可以使用命令或代码，例如：

```
function encryptFile(file) {  
  var systemCommand = “gpg --encrypt --recipient  recipientToEncryptTo ” + file;  
  var result = execCommand(systemCommand, true); 
}
```

导入文件时，您还可以解压缩或解密文件。 请参 [阅在处理之前解压缩或解密文件](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)。
