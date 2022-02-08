---
product: campaign
title: 不支持的SMS连接器迁移
description: 将不支持的SMS连接器迁移到扩展通用SMPP连接器
hidefromtoc: true
exl-id: 60acf80c-8506-410b-ab2c-4f67a5677b43
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---

# 将不支持的SMS连接器迁移到扩展通用SMPP连接器{#unsupported-connector-migration}

![](../../assets/v7-only.svg)

自20.2版起，弃用旧版连接器。 本文档将帮助您将仍在旧系统上运行的连接器迁移到推荐的SMPP连接器。

>[!CAUTION]
>
>此迁移并非强制性的，但是Adobe建议进行此迁移，并将确保您运行的软件是受支持的最新版本。

## 关于SMS连接器 {#about-sms-connectors}

以下连接器自20.2版起已弃用：

* **[!UICONTROL Generic SMPP]** （支持二进制模式的SMPP版本3.4）
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

已弃用的功能仍然可用且受支持，但将不会进一步增强这些功能。 我们建议使用 **[!UICONTROL Extended generic SMPP]** 连接器。

有关已弃用和已删除功能的更多信息，请参阅此 [页面](../../rn/using/deprecated-features.md).

旧的SMS连接器使用的Java SMS连接器会过载Web进程。 迁移到新 **[!UICONTROL Extended Generic SMPP]** 连接器会将此负载移至可支持此负载的MTA。

## 迁移到扩展的通用SMPP连接器 {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>即使您可以转换参数，也需配置 **[!UICONTROL Extended Generic SMPP]** 连接器要求您与提供商沟通，提供商将为您提供填充其余参数所需的信息。 有关详细信息，请参见此 [ 页面](sms-protocol.md)。

首先，您需要创建一个 **[!UICONTROL Extended Generic SMPP]** 外部帐户，然后您可能能够转换一些参数。 您可以在此中找到详细步骤 [页面](sms-set-up.md#creating-an-smpp-external-account).

现在，您需要填充 **[!UICONTROL Mobile]** 选项卡 **[!UICONTROL Extended Generic SMPP]** 外部帐户，具体取决于您之前的连接器。

### 从通用连接器 {#from-generic-connector}

选择 **[!UICONTROL Generic]** 连接器中，您应该有一个自定义JavaScript连接器，该连接器将适应每种情况。

如果您知道此连接器已在使用SMPP协议，则可以迁移到 **[!UICONTROL Extended Generic SMPP]** 连接器。 如果不支持，请咨询您的提供商（如果支持SMPP协议），并在顾问的帮助下设置新连接器。

从 **[!UICONTROL Generic]** 连接器，可以转换到新创建的 **[!UICONTROL Extended SMPP]** 帐户：

![](assets/smpp_generic.png)

在 **[!UICONTROL Connection Settings]** 选项卡：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### 从通用SMPP连接器 {#from-generic-smpp-connector}

从 **[!UICONTROL Generic SMPP]** 连接器，可以转换到新创建的 **[!UICONTROL Extended SMPP]** 帐户：

![](assets/smpp_generic_2.png)

在 **[!UICONTROL Connection Settings]** 选项卡：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在 **[!UICONTROL SMPP Channel Settings]** 选项卡：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

在 **[!UICONTROL Mapping of Encoding]** 选项卡：

* **[!UICONTROL Outbound SMS coding]**

在 **[!UICONTROL SMSC specificities]** 选项卡：

* **[!UICONTROL Coding when sending]** 对应于 **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 对应于 **[!UICONTROL ID Format in the SR]**

### 从Sybase365连接器 {#from-sybase}

从 **[!UICONTROL Sybase365]** 连接器，可以转换到新创建的 **[!UICONTROL Extended SMPP]** 帐户：

![](assets/smpp_3.png)

在 **[!UICONTROL Connection Settings]** 选项卡：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### 从CLX连接器 {#from-clx}

从 **[!UICONTROL CLX]** 连接器，可以转换到新创建的 **[!UICONTROL Extended SMPP]** 帐户：

![](assets/smpp_4.png)

在 **[!UICONTROL Connection Settings]** 选项卡：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在 **[!UICONTROL SMPP Channel Settings]** 选项卡：

* **[!UICONTROL Source number]**

在 **[!UICONTROL SMSC specificities]** 选项卡：

* **[!UICONTROL Coding when sending]** 对应于 **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 对应于 **[!UICONTROL ID Format in the SR]**

### 从Tele2连接器 {#from-tele2}

从 **[!UICONTROL Tele2]** 连接器，可以转换到新创建的 **[!UICONTROL Extended SMPP]** 帐户：

![](assets/smpp_6.png)

在 **[!UICONTROL Connection Settings]** 选项卡：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在 **[!UICONTROL SMPP Channel Settings]** 选项卡：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

在 **[!UICONTROL Mapping of Encoding]** 选项卡：

* **[!UICONTROL Outbound SMS coding]**

### 从O2连接器 {#from-O2}

从 **[!UICONTROL O2]** 连接器，可以转换到新创建的 **[!UICONTROL Extended SMPP]** 帐户：

![](assets/smpp_5.png)

在 **[!UICONTROL Connection Settings]** 选项卡：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在 **[!UICONTROL SMPP Channel Settings]** 选项卡：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**
