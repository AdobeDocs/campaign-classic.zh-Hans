---
solution: Campaign Classic
product: campaign
title: 电子邮件存档
description: 电子邮件存档
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 5fa848d86f951cb9dc40eb7981abea29c1092291
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 2%

---


# 密件抄送{#email-archiving}

您可以配置Adobe Campaign以保留从平台发送的电子邮件副本。

但是，Adobe Campaign本身不管理存档的文件。 它确实允许您将您选择的邮件发送到专用地址，从那里，可以使用外部系统处理和存档邮件。

为此，与已发送电子邮件对应的。eml文件将传输到远程服务器，如SMTP电子邮件服务器。 存档目标是必须指定的密件抄送电子邮件地址(对投放收件人不可见)。

## Recommendations和限制{#recommendations-and-limitations}

* 密件抄送功能是可选的。 请核实您的许可协议。
* 对于&#x200B;**托管和混合架构**，请联系您的客户经理以激活它。 您选择的密件抄送电子邮件地址必须提供给将为您配置该地址的Adobe团队。
* 对于&#x200B;**内部部署安装**，请按照以下准则激活它——请参阅[激活电子邮件密送（内部部署）](#activating-email-archiving--on-premise-)和[配置密送电子邮件地址（内部部署）](#configuring-the-bcc-email-address--on-premise-)部分。
* 只能使用一个密送电子邮件地址。
* 配置电子邮件密送后，请通过&#x200B;**[!UICONTROL Email BCC]**&#x200B;选项确保在投放模板或投放中启用该功能。 有关更多信息，请参阅[此章节](../../delivery/using/sending-messages.md#archiving-emails)。
* 只会考虑成功发送的电子邮件，而不会考虑弹回。
* 电子邮件归档系统因Adobe Campaign17.2（内部版本8795）而发生更改。 如果您已在使用电子邮件存档，则必须手动升级到新的电子邮件密送系统。 有关详细信息，请参阅[移至新的电子邮件密送](#updated-email-archiving-system--bcc-)部分。

## 激活电子邮件密送（内部部署）{#activating-email-archiving--on-premise-}

要在事先安装Adobe Campaign时激活密送电子邮件归档，请执行以下步骤。

### 本地文件夹{#local-folder}

要启用将已发送电子邮件传输到密送电子邮件地址，必须先将已发送电子邮件的精确原始副本另存为。eml文件并保存到本地文件夹。

必须在配置的&#x200B;**config-`<instance>`.xml**&#x200B;文件中指定本地文件夹的路径。 例如：

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>实施项目的团队有责任确保安全设置允许访问通过&#x200B;**dataLogPath**&#x200B;参数定义的文件夹。

完整路径如下：**`<datalogpath>  YYYY-MM-DDHHh`**。 日期和时间根据MTA服务器的时钟(UTC)设置。 例如：

```
C:\emails\2018-12-02\13h
```

当电子邮件的状态不是&#x200B;**[!UICONTROL Sent]**&#x200B;时，存档文件名为&#x200B;**`<deliveryid>-<broadlogid>.eml`**。 状态更改为&#x200B;**[!UICONTROL Sent]**&#x200B;后，文件名变为&#x200B;**`<deliveryid>-<broadlogid>-sent.eml`**。 例如：

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>在中间源实例中，密送电子邮件的目录位于中间源服务器上。
>
>当未发送电子邮件的状态时，deliveryID和broadlogID来自中间源服务器。 状态更改为&#x200B;**[!UICONTROL Sent]**&#x200B;后，这些ID来自营销服务器。

### 参数 {#parameters}

定义本地文件夹路径后，根据&#x200B;**config-`<instance name>.xml`**&#x200B;文件中的需要添加和编辑以下元素。 以下是默认值：

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**:压缩。eml文件时使用的格式。可能的值包括：

   **0**:无压缩（默认值）

   **1**:压缩（.zip格式）

* **compressBatchSize**:添加到存档的。eml文件数（.zip文件）。
* **archivingType**:存档战略。可能的值包括：

   **0**:已发送电子邮件的原始副本以。eml格式保存到 **** dataLogPath文件夹（默认值）。将&#x200B;**`<deliveryid>-<broadlogid>-sent.eml`**&#x200B;文件的存档副本保存到&#x200B;**dataLogPath/archives**&#x200B;文件夹。 已发送的电子邮件文件路径变为&#x200B;**`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**。

   **1**:已发送电子邮件的原始副本以。eml格式保存到 **** dataLogPath文件夹，并通过SMTP发送到密送电子邮件地址。将电子邮件副本发送到密送地址后，归档文件名将变为&#x200B;**`<deliveryid>-<broadlogid>-sent-archived.eml`**，文件将移至&#x200B;**dataLogPath/archives**&#x200B;文件夹。 发送和密送归档的电子邮件文件路径随后为&#x200B;**`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**。

* **expirationDelay**:保存。eml文件以进行存档的天数。延迟后，它们会自动移至&#x200B;**dataLogPath/archives**&#x200B;文件夹进行压缩。 默认情况下，.eml文件在两天后过期。
* **purgeArchivesDelay**:dataLogPath/文件夹中存 **储的天`<archives>`** 数。在此期间后，它们将被永久删除。 MTA启动后，清除开始。 默认情况下，每七天执行一次。
* **pollDelay**:正在检查发送到dataLogPath文件夹的新电子邮件的频率(以 **** 秒为单位)。例如，如果此参数设置为60，则表示每分钟归档过程都会通过&#x200B;**dataLogPath/`<date and time>`**&#x200B;文件夹内的。eml文件，根据需要应用清除，并将电子邮件副本发送到密送地址和／或在需要时压缩归档文件。
* **acquireLimit**:根据pollDelay参数，再次应用存档过程之前一次处理的。eml文 **** 件数。例如，如果将&#x200B;**acquireLimit**&#x200B;参数设置为100，而将&#x200B;**pollDelay**&#x200B;参数设置为60，则每分钟将处理100个。eml文件。
* **smtpNbConnection**:密送电子邮件地址的SMTP连接数。

确保根据电子邮件发送吞吐量调整这些参数。 例如，在MTA每小时发送30,000封电子邮件的配置中，您可以将&#x200B;**pollDelay**&#x200B;参数设置为600，将&#x200B;**acquireLimit**&#x200B;参数设置为5000，将&#x200B;**smtpNbConnection**&#x200B;参数设置为2. 这意味着，使用2个SMTP连接时，每10分钟将向密送地址发送5,000封电子邮件。

## 配置密送电子邮件地址（内部部署）{#configuring-the-bcc-email-address--on-premise-}

>[!IMPORTANT]
>
>出于隐私原因，密件抄送电子邮件必须由能够安全地存储个人身份信息(PII)的存档系统处理。

在&#x200B;**config-`<instance name>.xml`**&#x200B;文件中，使用以下参数定义要将存储文件传输到的SMTP电子邮件服务器：

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**:归档目标目标
* **smtpEnableTLS**:使用安全的SMTP连接（TLS/SSL协议）
* **smtpRelayAddress**:中继地址
* **smtpRelayPort**:中继端口

>[!NOTE]
>
>如果您使用SMTP中继，则在存档过程中不会考虑中继对电子邮件所做的更改。
>
>此外，中继会为所有电子邮件（包括未发送的电子邮件）分配&#x200B;**[!UICONTROL Sent]**&#x200B;状态。 因此，所有邮件都会存档。

## 正在移至新的电子邮件密送{#updated-email-archiving-system--bcc-}

>[!IMPORTANT]
>
>电子邮件归档系统(BCC)随Adobe Campaign17.2（内部版本8795）而发生更改。 如果您从旧版本升级并且已经使用电子邮件归档功能，则必须手动升级到新的电子邮件归档系统(BCC)。

为此，请对&#x200B;**`config-<instance>.xml`**&#x200B;文件进行以下更改：

1. 从&#x200B;**`<archiving>`**&#x200B;节点中删除&#x200B;**zipPath**&#x200B;参数。
1. 根据需要将&#x200B;**compressionFormat**&#x200B;参数设置为&#x200B;**1**。
1. 将&#x200B;**archivingType**&#x200B;参数设置为&#x200B;**1**。

配置电子邮件密送后，请确保在投放模板或投放中选择&#x200B;**[!UICONTROL Email BCC]**&#x200B;选项。 有关更多信息，请参阅[此章节](../../delivery/using/sending-messages.md#archiving-emails)。

## 密件抄送最佳实践{#best-practices}

* **密送地址邮箱**:确保它具有足够的接收能力来存档MTA发送的所有电子邮件。
* **MTA共同化**:密送归档功能在MTA级别有效。它允许您重复MTA发送的每封电子邮件。 由于MTA可以跨多个实例（例如开发、测试或生产）或甚至跨多个客户端(在中间源环境中)实现共同化，因此设置此功能会影响安全性：

   * 如果您与多个客户端共享MTA，并且其中一个客户端激活了此选项，则此客户端将访问共享同一MTA的其他客户端的所有电子邮件。 要避免出现这种情况，请对每个客户端使用不同的MTA。
   * 如果在单个客户端的多个实例（开发、测试、生产）中使用相同的MTA，则从所有三个实例发送的消息将被dataLogPath选项复制。

* **每个连接的电子邮件**:密件抄送电子邮件存档通过打开连接并尝试通过该连接发送所有电子邮件来操作。Adobe建议与内部技术联系人核实在给定连接上接受的电子邮件数。 增加此数量会对密送吞吐量产生很大影响。
* **密送发送IP**:目前，密送电子邮件不会通过普通MTA代理发送。而是会打开从MTA服务器到目标电子邮件服务器的直接连接。 这意味着您可能需要根据电子邮件服务允许列表器配置向网络上的添加其他IP。

