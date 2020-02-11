---
title: 电子邮件存档
seo-title: 电子邮件存档
description: 电子邮件存档
seo-description: null
page-status-flag: never-activated
uuid: a5ed0659-be61-4d73-98e7-db3da24d92f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: d6467875-949b-4b47-940f-620efd4db5e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5b9c57b3cba0e8c24300396c2abac613f6e1193a

---


# 电子邮件存档{#email-archiving}

您可以配置Adobe Campaign以保留从您的平台发送的电子邮件副本。

但是，Adobe Campaign本身不管理存档的文件。 它确实允许您将您选择的消息发送到专用地址，从中可以使用外部系统处理和存档消息。

为此，与已发送电子邮件相对应的。eml文件将传输到远程服务器，如SMTP电子邮件服务器。 存档目标是您必须指定的密件抄送电子邮件地址（对传送收件人不可见）。

## 建议和限制 {#recommendations-and-limitations}

* 电子邮件存档功能是可选的。 请检查您的许可协议。
* 对于 **托管和混合架构**，请联系您的客户经理以激活它。 您选择的密件抄送地址必须提供给Adobe团队，由团队为您配置。
* 对于 **内部部署安装**，请按照以下准则激活它——请参阅激活电子邮件归档（内部部署） [和配置密送电子邮件地址(内部部](#activating-email-archiving--on-premise-) 署)部分 [](#configuring-the-bcc-email-address--on-premise-) 。
* 您只能使用一个密送电子邮件地址。
* 配置电子邮件密送后，请确保在分发模板中或通过选项在分发中启用该功 **[!UICONTROL Archive emails]** 能。 For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
* 只有成功发送的电子邮件才会被考虑在内，而弹回则不会被考虑在内。
* 电子邮件归档系统随Adobe Campaign 17.2（内部版本8795）而发生更改。 如果您已经在使用电子邮件归档，则必须手动升级到新的电子邮件归档系统（密件抄送）。 有关详细信息，请参阅更 [新的电子邮件归档系统（密送）部分](#updated-email-archiving-system--bcc-) 。

## 激活电子邮件存档（内部部署） {#activating-email-archiving--on-premise-}

要在事先安装Adobe Campaign时激活密送电子邮件存档，请执行以下步骤。

### 本地文件夹 {#local-folder}

要启用将已发送电子邮件传输到密送电子邮件地址的功能，必须首先将已发送电子邮件的精确原始副本另存为。eml文件到本地文件夹。

必须从配置中在 **config-`<instance>`.xml文件中指定本地文件夹的路径** 。 例如：

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>实施项目的团队有责任确保安全设置允许访问通过dataLogPath参数定义的 **文件夹** 。

完整路径如下： **`<datalogpath>  YYYY-MM-DDHHh`**. 日期和时间根据MTA服务器的时钟(UTC)设置。 例如：

```
C:\emails\2018-12-02\13h
```

当电子邮件的状 **`<deliveryid>-<broadlogid>.eml`** 态不是时，会显示存档文件名 **[!UICONTROL Sent]**。 状态更改为后， **[!UICONTROL Sent]**&#x200B;文件名变为 **`<deliveryid>-<broadlogid>-sent.eml`**。 例如：

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>在中间采购实例中，归档电子邮件的目录位于中间采购服务器上。
>
>当未发送电子邮件的状态时，deliveryID和broadlogID来自中间采购服务器。 状态更改为后， **[!UICONTROL Sent]**&#x200B;这些ID来自营销服务器。

### 参数 {#parameters}

定义本地文件夹路径后，根据配置文件中的需要添加和编辑 **以下元`<instance name>.xml`**素。 以下是默认值：

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**:压缩。eml文件时使用的格式。 可能的值有：

   **0**:无压缩（默认值）

   **1**:压缩（.zip格式）

* **compressBatchSize**:添加到存档（.zip文件）的。eml文件数。
* **archivingType**:存档战略。 可能的值有：

   **0**:已发送电子邮件的原始副本以。eml格式保存到 **dataLogPath文件夹** （默认值）。 文件的存档副 **`<deliveryid>-<broadlogid>-sent.eml`** 本将保存到 **dataLogPath/archives文件夹** 。 发送的电子邮件文件路径将变 **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**&#x200B;为。

   **1**:已发送电子邮件的原始副本以。eml格式保存到 **dataLogPath文件夹中** ，并通过SMTP发送到密送电子邮件地址。 将电子邮件副本发送到密送地址后，归档文件名将变 **`<deliveryid>-<broadlogid>-sent-archived.eml`** 为并且文件将移至 **dataLogPath/archives文件夹** 。 然后，发送和密送归档的电子邮件文件路径即为 **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**。

* **expirationDelay**:保存。eml文件以进行存档的天数。 在延迟后，它们会自动移至 **dataLogPath/archives文件夹进行压缩** 。 默认情况下，.eml文件在两天后过期。
* **purgeArchivesDelay**:dataLogPath/文件夹中存 **档的天数`<archives>`**。 在此期间后，这些文件将被永久删除。 MTA启动后，清除开始。 默认情况下，每七天执行一次。
* **pollDelay**:检查发送到dataLogPath文件夹的新传入电子邮件的频率(以 **秒为单位** )。 例如，如果此参数设置为60，则表示每分钟归档过程都会通过 **`<date and time>`**dataLogPath/文件夹内的。eml文件，根据需要应用清除，然后将电子邮件副本发送到密送地址和／或在需要时压缩存档的文件。
* **acquireLimit**:根据pollDelay参数，再次应用存档进程之前一次处理的。eml文件 **数** 。 例如，如果将acquireLimit **参数设置为100，而** pollDelay **** 参数设置为60，则每分钟将处理100个。eml文件。
* **smtpNbConnection**:密送电子邮件地址的SMTP连接数。

确保根据电子邮件发送吞吐量调整这些参数。 例如，在MTA每小时发送30,000封电子邮件的配置中，您可以将 **pollDelay** 参数设置为600，将acquireLimit **参数设置为5000，将** smtpNbConnection参数设置为 **** 2。 这意味着，使用2个SMTP连接时，每10分钟将向密送地址发送5,000封电子邮件。

## 配置密送电子邮件地址（内部部署） {#configuring-the-bcc-email-address--on-premise-}

>[!CAUTION]
>
>出于隐私原因，密件抄送电子邮件必须由能够安全地存储个人身份信息(PII)的存档系统处理。

在config- **文件`<instance name>.xml`**中，使用以下参数定义要将存储的文件传输到的SMTP电子邮件服务器：

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**:存档目标目标目标
* **smtpEnableTLS**:使用安全的SMTP连接（TLS/SSL协议）
* **smtpRelayAddress**:中继地址
* **smtpRelayPort**:中继端口

>[!NOTE]
>
>如果您使用SMTP中继，则在存档过程中不会考虑中继对电子邮件所做的更改。
>
>此外，中继器会为所有电 **[!UICONTROL Sent]** 子邮件（包括未发送的电子邮件）分配状态。 因此，将存档所有消息。

## 更新的电子邮件存档系统（密送） {#updated-email-archiving-system--bcc-}

>[!CAUTION]
>
>电子邮件归档系统（密件抄送）随Adobe Campaign 17.2而发生更改（内部版本8795）。 如果您是从旧版本升级并且已经使用电子邮件归档功能，则必须手动升级到新的电子邮件归档系统（密件抄送）。

为此，请对文件进行以下更 **`config-<instance>.xml`** 改：

1. 从节 **点中删除** zipPath **`<archiving>`** 参数。
1. 根据需要 **将compressionFormat** 参数设 **置为** 1。
1. 将archivingType **参数设置** 为 **1**。

配置电子邮件密送后，请确保在分发模 **[!UICONTROL Archive emails]** 板或分发中选择相应选项。 For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).

## 最佳实践 {#best-practices}

* **密送地址邮箱**:确保它具有足够的接收能力来存档MTA发送的所有电子邮件。
* **MTA共同化**:密件抄送归档功能在MTA级别工作。 它允许您复制MTA发送的每封电子邮件。 由于MTA可以跨多个实例（例如开发、测试或生产）或甚至跨多个客户端（在中部采购环境中）共同化，因此设置此功能会影响安全性：

   * 如果您与多个客户端共享MTA，并且其中一个客户端激活了此选项，则此客户端将访问共享相同MTA的其他客户端的所有电子邮件。 要避免这种情况，请为每个客户端使用不同的MTA。
   * 如果对单个客户端的多个实例（开发、测试、prod）使用相同的MTA，则从所有三个实例发送的消息将被dataLogPath选项复制。

* **每连接的电子邮件**:密件抄送电子邮件存档通过打开连接并尝试通过该连接发送所有电子邮件来操作。 Adobe建议与内部技术联系人核对在给定连接上接受的电子邮件数量。 增加此数量会对密送吞吐量产生很大影响。
* **密送发送IP**:目前，密送电子邮件不会通过正常的MTA代理发送。 而是会打开从MTA服务器到目标电子邮件服务器的直接连接。 这意味着，根据您的电子邮件服务器配置，您可能需要将网络上的其他IP列入白名单。

