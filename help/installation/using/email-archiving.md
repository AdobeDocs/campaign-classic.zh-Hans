---
product: campaign
title: 电子邮件存档
description: 电子邮件存档
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: dccf72b200cad9ba160a496cdd13ba39c5599008
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 3%

---

# 配置电子邮件密送 {#email-archiving}

![](../../assets/v7-only.svg)

您可以配置Adobe Campaign以保留从您的平台发送的电子邮件副本。

但是，Adobe Campaign本身不会管理已存档的文件。 它确实允许您将您选择的消息发送到专用地址，从中可以使用外部系统处理和存档这些消息。

为此，与已发送电子邮件对应的.eml文件会被传输到远程服务器，如SMTP电子邮件服务器。 存档目标是您必须指定的密件抄送电子邮件地址（投放收件人不可见）。

## Recommendations和限制 {#recommendations-and-limitations}

* 电子邮件密送功能是可选的。 请核实您的许可协议。
* 对于&#x200B;**托管和混合架构**，请联系您的客户经理以将其激活。 您选择的密件抄送电子邮件地址必须提供给Adobe团队，由团队为您进行配置。
* 对于&#x200B;**本地安装**，请按照以下准则激活它 — 请参阅[激活电子邮件密送（本地）](#activating-email-archiving--on-premise-)和[配置密送电子邮件地址（本地）](#configuring-the-bcc-email-address--on-premise-)部分。
* 您只能使用一个密件抄送电子邮件地址。
* 配置电子邮件密件抄送后，请确保在投放模板或通过&#x200B;**[!UICONTROL Email BCC]**&#x200B;选项的投放中启用该功能。 有关更多信息，请参阅[此章节](../../delivery/using/sending-messages.md#archiving-emails)。
* 只有成功发送的电子邮件才会被考虑在内，而退回则不会。
* 电子邮件存档系统已随Adobe Campaign 17.2（版本8795）发生更改。 如果您已经使用电子邮件存档，则必须手动升级到新的电子邮件密送系统。 有关更多信息，请参阅[移动到新电子邮件密送](#updated-email-archiving-system--bcc-)部分。

## 激活电子邮件密送（内部部署） {#activating-email-archiving--on-premise-}

要在内部部署安装Adobe Campaign时激活密送电子邮件存档，请执行以下步骤。

### 本地文件夹 {#local-folder}

要启用将已发送电子邮件传输到密送电子邮件地址的功能，已发送电子邮件的确切原始副本必须首先另存为.eml文件到本地文件夹。

必须在配置的&#x200B;**config-`<instance>`.xml**&#x200B;文件中指定本地文件夹的路径。 例如：

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>实施项目的团队有责任确保安全设置允许访问通过&#x200B;**dataLogPath**&#x200B;参数定义的文件夹。

完整路径如下：**`<datalogpath>  YYYY-MM-DDHHh`**。 日期和时间根据MTA服务器的时钟(UTC)进行设置。 例如：

```
C:\emails\2018-12-02\13h
```

当电子邮件的状态不是&#x200B;**[!UICONTROL Sent]**&#x200B;时，存档文件名为&#x200B;**`<deliveryid>-<broadlogid>.eml`**。 状态更改为&#x200B;**[!UICONTROL Sent]**&#x200B;后，文件名将变为&#x200B;**`<deliveryid>-<broadlogid>-sent.eml`**。 例如：

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>在中间源实例中，密送电子邮件的目录位于中间源服务器上。
>
>如果未发送电子邮件的状态，则deliveryID和broadlogID来自中间源服务器。 状态更改为&#x200B;**[!UICONTROL Sent]**&#x200B;后，这些ID来自营销服务器。

### 参数 {#parameters}

定义本地文件夹路径后，根据需要在&#x200B;**config-`<instance name>.xml`**&#x200B;文件中添加和编辑以下元素。 以下是默认值：

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**:压缩.eml文件时使用的格式。可能的值包括：

   **0**:无压缩（默认值）

   **1**:压缩（.zip格式）

* **compressBatchSize**:添加到存档的.eml文件数（.zip文件）。
* **archivingType**:存档策略。可能的值包括：

   **0**:已发送电子邮件的原始副本以.eml格式保存到 **** dataLogPathfolder（默认值）。**`<deliveryid>-<broadlogid>-sent.eml`**&#x200B;文件的存档副本将保存到&#x200B;**dataLogPath/archives**&#x200B;文件夹中。 已发送的电子邮件文件路径将变为&#x200B;**`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**。

   **1**:已发送电子邮件的原始副本以.eml格式保存到dataLogPath **** 文件夹中，并通过SMTP发送到密送电子邮件地址。将电子邮件副本发送到密送地址后，存档文件名称将变为&#x200B;**`<deliveryid>-<broadlogid>-sent-archived.eml`**，并将文件移动到&#x200B;**dataLogPath/archives**&#x200B;文件夹。 然后，已发送和密送存档的电子邮件文件路径为&#x200B;**`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**。

* **expirationDelay**:保留.eml文件以进行存档的天数。延迟后，它们会自动移至&#x200B;**dataLogPath/archives**&#x200B;文件夹进行压缩。 默认情况下， .eml文件会在两天后过期。
* **purgeArchivesDelay**:dataLogPath/文件夹中存 **档的天`<archives>`** 数。在此期间之后，这些文件将被永久删除。 清除在MTA启动时开始。 默认情况下，每七天执行一次。
* **pollDelay**:正在检查频率（以秒为单位），以确定新传入的已发送到dataLogPath文件夹的电 **** 子邮件。例如，如果此参数设置为60，则意味着每分钟，归档过程都会完成&#x200B;**dataLogPath/`<date and time>`**&#x200B;文件夹内的.eml文件，根据需要应用清除，并向密送地址发送电子邮件副本和/或在需要时压缩已归档文件。
* **acquireLimit**:根据pollDelay参数再次应用存档过程之前一次处理的.eml文 **** 件数。例如，如果将&#x200B;**acquireLimit**&#x200B;参数设置为100，而将&#x200B;**pollDelay**&#x200B;参数设置为60，则每分钟将处理100个.eml文件。
* **smtpNbConnection**:与密送电子邮件地址的SMTP连接数。

确保根据电子邮件发送吞吐量调整这些参数。 例如，在MTA每小时发送30,000封电子邮件的配置中，您可以将&#x200B;**pollDelay**&#x200B;参数设置为600，将&#x200B;**acquireLimit**&#x200B;参数设置为5000，将&#x200B;**smtpNbConnection**&#x200B;参数设置为2。 这意味着使用2个SMTP连接时，每10分钟向密送地址发送5,000封电子邮件。

## 配置密送电子邮件地址（内部部署） {#configuring-the-bcc-email-address--on-premise-}

>[!IMPORTANT]
>
>出于隐私原因，密件抄送电子邮件必须由能够存储安全的个人身份信息(PII)的存档系统处理。

在&#x200B;**config-`<instance name>.xml`**&#x200B;文件中，使用以下参数定义存储文件要传输到的SMTP电子邮件服务器：

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**:存档目标目标
* **smtpEnableTLS**:使用安全SMTP连接（TLS/SSL协议）
* **smtpRelayAddress**:中继地址
* **smtpRelayPort**:中继端口

>[!NOTE]
>
>如果您使用的是SMTP中继，则归档过程中不会考虑中继对电子邮件所做的更改。
>
>此外，中继器会为所有电子邮件（包括未发送的电子邮件）分配&#x200B;**[!UICONTROL Sent]**&#x200B;状态。 因此，所有消息都会被存档。

## 转到新的电子邮件密件抄送 {#updated-email-archiving-system--bcc-}

>[!IMPORTANT]
>
>电子邮件归档系统（密送）已随Adobe Campaign 17.2（内部版本8795）发生更改。 如果您从旧版本进行升级，并且已经使用电子邮件存档功能，则必须手动升级到新的电子邮件存档系统（密送）。

为此，请对&#x200B;**`config-<instance>.xml`**&#x200B;文件进行以下更改：

1. 从&#x200B;**`<archiving>`**&#x200B;节点中删除&#x200B;**zipPath**&#x200B;参数。
1. 如果需要，可将&#x200B;**compressionFormat**&#x200B;参数设置为&#x200B;**1**。
1. 将&#x200B;**archivingType**&#x200B;参数设置为&#x200B;**1**。

配置电子邮件密送后，请确保在投放模板或投放中选择&#x200B;**[!UICONTROL Email BCC]**&#x200B;选项。 有关更多信息，请参阅[此章节](../../delivery/using/sending-messages.md#archiving-emails)。

## 电子邮件密送最佳实践 {#best-practices}

* **密送地址邮箱**:确保具有足够的接收容量，以存档MTA发送的所有电子邮件。
* **MTA共同化**:密送归档功能在MTA级别起作用。它允许您复制MTA发送的每封电子邮件。 由于MTA可以跨多个实例（例如开发、测试或生产）或甚至跨多个客户端（在中间源环境中）进行共同化，因此设置此功能会影响安全性：

   * 如果您与多个客户共享MTA，并且其中一个客户已激活此选项，则此客户将访问共享相同MTA的其他客户的所有电子邮件。 要避免出现这种情况，请为每个客户端使用不同的MTA。
   * 如果在单个客户端的多个实例（开发、测试和生产）中使用相同的MTA，则从所有三个实例发送的消息将被dataLogPath选项复制。

* **每个连接的电子邮件数**:密件抄送电子邮件存档通过打开连接并尝试通过该连接发送所有电子邮件来执行。Adobe建议与内部技术联系人核实在给定连接上接受的电子邮件数量。 增加此数量会对密送吞吐量产生很大影响。
* **密送IP**:目前，密送电子邮件不会通过常规MTA代理发送。而是会从MTA服务器打开到目标电子邮件服务器的直接连接。 这意味着您可能需要根据您的电子邮件服允许列表务器配置，向网络上的添加其他IP。

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