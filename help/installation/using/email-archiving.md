---
product: campaign
title: 电子邮件存档
description: 电子邮件存档
feature: Installation, Instance Settings, Email
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 2%

---

# 配置电子邮件密送 {#email-archiving}



您可以配置Adobe Campaign以保留从您的平台发送的电子邮件副本。

但是，Adobe Campaign本身并不管理存档文件。 它使您能够将选择的消息发送到一个专用地址，可以从该地址使用外部系统处理和存档这些消息。

为此，将与所发送电子邮件相对应的.eml文件传输到远程服务器，如SMTP电子邮件服务器。 存档目标是您必须指定的密送电子邮件地址（投放收件人不可见）。

## Recommendations和限制 {#recommendations-and-limitations}

* 电子邮件密送功能是可选的。 请核实您的许可协议。
* 对于&#x200B;**托管架构和混合架构**，请与您的客户经理联系以激活它。 您选择的密件抄送电子邮件地址必须提供给将为您配置该地址的Adobe团队。
* 对于&#x200B;**内部部署**，请遵循以下准则来激活它 — 请参阅[激活电子邮件密件抄送（内部部署）](#activating-email-archiving--on-premise-)和[配置密件抄送电子邮件地址（内部部署）](#configuring-the-bcc-email-address--on-premise-)部分。
* 您只能使用一个密件抄送电子邮件地址。
* 配置电子邮件密送后，请确保在投放模板中或通过&#x200B;**[!UICONTROL Email BCC]**&#x200B;选项在投放中启用该功能。 有关更多信息，请参阅[此小节](../../delivery/using/sending-messages.md#archiving-emails)。
* 仅考虑成功发送的电子邮件，不考虑退回。
* 电子邮件归档系统随Adobe Campaign 17.2（内部版本8795）发生了更改。 如果您已经在使用电子邮件存档，则必须手动升级到新的电子邮件密件抄送系统。 有关此内容的更多信息，请参阅[移至新的电子邮件密送](#updated-email-archiving-system--bcc-)部分。

## 正在激活电子邮件密送（内部部署） {#activating-email-archiving--on-premise-}

[!BADGE 内部部署和混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"}


要在本地安装Adobe Campaign时激活密件抄送电子邮件归档，请执行以下步骤。

### 本地文件夹 {#local-folder}

要启用将已发送电子邮件传输到密件抄送电子邮件地址，必须首先将已发送电子邮件的精确原始副本另存为.eml文件并保存到本地文件夹中。

本地文件夹的路径必须在配置中的&#x200B;**config-`<instance>`.xml**&#x200B;文件中指定。 例如：

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>实施项目的团队负责确保安全设置允许访问通过&#x200B;**dataLogPath**&#x200B;参数定义的文件夹。

完整路径如下所示： **`<datalogpath>  YYYY-MM-DDHHh`**。 日期和时间根据MTA服务器的时钟(UTC)设置。 例如：

```
C:\emails\2018-12-02\13h
```

当电子邮件的状态不是&#x200B;**[!UICONTROL Sent]**&#x200B;时，存档文件名为&#x200B;**`<deliveryid>-<broadlogid>.eml`**。 一旦状态更改为&#x200B;**[!UICONTROL Sent]**，文件名将变为&#x200B;**`<deliveryid>-<broadlogid>-sent.eml`**。 例如：

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>在中间源实例中，密件抄送电子邮件的目录位于中间源服务器上。
>
>当电子邮件的状态未发送时，deliveryID和broadlogID来自中间源服务器。 一旦状态更改为&#x200B;**[!UICONTROL Sent]**，这些ID将来自营销服务器。

### 参数 {#parameters}

定义本地文件夹路径后，根据需要在&#x200B;**config-`<instance name>.xml`**&#x200B;文件中添加并编辑以下元素。 以下是默认值：

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="1" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**：压缩.eml文件时使用的格式。 可能的值包括：

  **0**：无压缩（默认值）

  **1**：压缩（.zip格式）

* **compressBatchSize**：添加到存档的.eml文件数（.zip文件）。


* **archivingType**：要使用的存档策略。 唯一可能的值为&#x200B;**1**。 已发送电子邮件的原始副本以.eml格式保存到&#x200B;**dataLogPath**&#x200B;文件夹，并通过SMTP发送到密件抄送电子邮件地址。 将电子邮件副本发送到密件抄送地址后，存档文件名将变为&#x200B;**`<deliveryid>-<broadlogid>-sent-archived.eml`**，并且文件将移至&#x200B;**dataLogPath/archives**&#x200B;文件夹。 已发送和密件抄送存档的电子邮件文件路径为&#x200B;**`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**。

  <!--
  **0**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder (default value). An archiving copy of the **`<deliveryid>-<broadlogid>-sent.eml`** file is saved to the **dataLogPath/archives** folder. The sent email file path becomes **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.-->

* **expirationDelay**： .eml文件保留存档的天数。 在此延迟之后，它们会自动移动到&#x200B;**dataLogPath/archives**&#x200B;文件夹以进行压缩。 默认情况下， .eml文件会在两天后过期。
* **purgeArchivesDelay**： **dataLogPath/`<archives>`**&#x200B;文件夹中保留的存档天数。 在此期限之后，它们将永久删除。 清除MTA启动时开始。 默认情况下，每7天执行一次。
* **pollDelay**：正在检查发往&#x200B;**dataLogPath**&#x200B;文件夹的新传入电子邮件的频率（以秒为单位）。 例如，如果此参数设置为60，则表示存档过程每分钟都会处理&#x200B;**dataLogPath/`<date and time>`**&#x200B;文件夹内的.eml文件，根据需要应用清除，并在需要时向BCC地址发送电子邮件副本和/或压缩存档文件。
* **acquireLimit**：在根据&#x200B;**pollDelay**&#x200B;参数再次应用存档进程之前一次处理的.eml文件数。 例如，如果您将&#x200B;**acquireLimit**&#x200B;参数设置为100，而&#x200B;**pollDelay**&#x200B;参数设置为60，则每分钟将处理100个.eml文件。
* **smtpNbConnection**：与BCC电子邮件地址的SMTP连接数。

确保根据电子邮件发送吞吐量调整这些参数。 例如，在MTA每小时发送30,000封电子邮件的配置中，您可以将&#x200B;**pollDelay**&#x200B;参数设置为600，将&#x200B;**acquireLimit**&#x200B;参数设置为5000，将&#x200B;**smtpNbConnection**&#x200B;参数设置为2。 这意味着如果使用2个SMTP连接，每10分钟会向BCC地址发送5,000封电子邮件。

## 配置密件抄送电子邮件地址（内部部署） {#configuring-the-bcc-email-address--on-premise-}

[!BADGE 内部部署和混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"}


>[!IMPORTANT]
>
>出于隐私原因，密件抄送电子邮件必须由能够安全存储个人身份信息(PII)的归档系统处理。

在&#x200B;**配置 —`<instance name>.xml`**&#x200B;文件中，使用以下参数定义存储文件将传输到的SMTP电子邮件服务器：

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**：存档目标目标
* **smtpEnableTLS**：使用安全的SMTP连接（TLS/SSL协议）
* **smtpRelayAddress**：要使用的中继地址
* **smtpRelayPort**：要使用的中继端口

>[!NOTE]
>
>如果您使用的是SMTP中继，则在归档过程中不会考虑中继对电子邮件所做的更改。
>
>此外，中继还为所有电子邮件（包括未发送的电子邮件）分配&#x200B;**[!UICONTROL Sent]**&#x200B;状态。 因此，所有消息都会被存档。

<!--
## Moving to the new Email BCC {#updated-email-archiving-system--bcc-}

[!BADGE On-premise & Hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="Applies to on-premise and hybrid deployments only"}

>[!IMPORTANT]
>
>The email archiving system (BCC) changed with Adobe Campaign 17.2 (build 8795). If you are upgrading from an older build and were already using email archiving capabilities, you must upgrade manually to the new email archiving system (BCC).

To do this, make the following changes to the **`config-<instance>.xml`** file:

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Set the **compressionFormat** parameter to **1** if needed.
1. Set the **archivingType** parameter to **1**.

Once email BCC is configured, make sure you select the **[!UICONTROL Email BCC]** option in the delivery template or the delivery. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
-->

## 电子邮件密送最佳实践 {#best-practices}

* **密件抄送地址邮箱**：确保它有足够的接收容量来存档MTA发送的所有电子邮件。
* **MTA池**： BCC存档功能在MTA级别工作。 它允许您复制MTA发送的每个电子邮件。 由于MTA可以跨多个实例（例如开发、测试或生产）甚至跨多个客户（在中间源环境中）进行池，因此设置此功能会影响安全性：

   * 如果您与多个客户端共享MTA，并且其中一个客户端激活了此选项，则此客户端将访问共享同一MTA的其他客户端的所有电子邮件。 要避免出现这种情况，请为每个客户端使用不同的MTA。
   * 如果您在单个客户端的多个实例（开发、测试、生产）中使用相同的MTA，则从所有三个实例发送的消息都将由dataLogPath选项复制。

* **每个连接的电子邮件**： BCC电子邮件存档操作方法是打开一个连接并尝试通过该连接发送所有电子邮件。 Adobe建议与您的内部技术联系人确认在给定连接上可接受的电子邮件数量。 增加此数量可能会对BCC吞吐量产生重大影响。
* **BCC发送IP**：当前，不通过普通MTA代理发送密件抄送电子邮件。 而是会打开从MTA服务器到目标电子邮件服务器的直接连接。 列入允许列表这意味着您可能需要向网络上的添加其他IP，具体取决于您的电子邮件服务器配置。

<!--## Email BCC with Enhanced MTA {#email-bcc-with-enhanced-mta}

For **hosted and hybrid architectures**, if you have the latest instance of Adobe Campaign, or if you have upgraded to the Enhanced MTA and using Adobe Campaign 19.2 or later, you can use Email BCC with Enhanced MTA, which is more reliable, efficient, and has lower latency.

### Activating Email BCC with Enhanced MTA

To activate this feature, you must contact your account executive to communicate the BCC email address to be used for archiving.

>[!NOTE]
>
>If you were already using BCC email archiving, you can provide the same address as you were using before or use a new one. If you keep the same, you still have to contact your account executive to set it up for you.

### Specificities and recommendations

Email BCC with Enhanced MTA is not activated at the delivery level: once this feature is enabled, **all sent deliveries** are sent to the BCC email address. There is no need to select the **[!UICONTROL Email BCC]** option in the delivery template or in the delivery.

If you were already using BCC and if you keep the same address, you could see a significant increase in the volumes sent to the BCC address.

Consequently, make sure:
* The BCC address has enough reception capacity to archive all the emails that are sent.
* You have the required MTA infrastructure capacity to receive 100% of your email volume delivered to a single address.

### Limitations

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->