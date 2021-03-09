---
solution: Campaign Classic
product: campaign
title: 不支持的SMS连接器迁移
description: 将不支持的SMS连接器迁移到扩展通用SMPP连接器
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 584c11cc46d3a0cea3dcbbaef2700200fbdb8201
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---


# 将不支持的SMS连接器迁移到扩展通用SMPP连接器{#unsupported-connector-migration}

从20.2版开始，已弃用旧版连接器。 此文档将帮助您将仍在旧系统上运行的连接器迁移到建议的SMPP连接器。

>[!CAUTION]
>
>此迁移不是强制性的，但由Adobe建议，将确保您运行的软件是支持的最新版本。

## 关于SMS连接器{#about-sms-connectors}

从20.2版开始，已弃用以下连接器：

* **[!UICONTROL Generic SMPP]** （支持二进制模式的SMPP 3.4版）
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

已弃用的功能仍然可用且受支持，但不会进一步增强。 建议使用&#x200B;**[!UICONTROL Extended generic SMPP]**&#x200B;连接器。

有关已弃用和已删除功能的详细信息，请参阅此[页面](../../rn/using/deprecated-features.md)。

旧的SMS连接器使用Java SMS连接器，该连接器会过载Web进程。 迁移到新的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;连接器会将此负载移至可支持它的MTA。

## 迁移到扩展通用SMPP连接器{#migrating-extended-generic-smpp}

>[!CAUTION]
>
>即使您可以转换参数，配置&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;连接器也需要与提供者交谈，后者将为您提供填充其余参数所需的信息。 有关详细信息，请参见此 [ 页面](../../delivery/using/sms-protocol.md)。

首先，您需要创建一个新的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;外部帐户，然后您可能可以转换某些参数。 您可以在此[页面](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)中找到详细步骤。

现在，您需要根据您之前的连接器，从新创建的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;外部帐户的&#x200B;**[!UICONTROL Mobile]**&#x200B;选项卡中填充参数。

### 从通用连接器{#from-generic-connector}

选择&#x200B;**[!UICONTROL Generic]**&#x200B;连接器时，您应该有一个自定义JavaScript连接器，它将适应每种情况。

如果您知道此连接器已使用SMPP协议，则可以迁移到&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;连接器。 如果不支持，请咨询您的提供商，了解他们是否支持SMPP协议并在顾问的帮助下设置新连接器。

在&#x200B;**[!UICONTROL Generic]**&#x200B;连接器中，您可以转换到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

![](assets/smpp_generic.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;选项卡中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### 从通用SMPP连接器{#from-generic-smpp-connector}

在&#x200B;**[!UICONTROL Generic SMPP]**&#x200B;连接器中，您可以转换到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

![](assets/smpp_generic_2.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;选项卡中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;选项卡中：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

在&#x200B;**[!UICONTROL Mapping of Encoding]**&#x200B;选项卡中：

* **[!UICONTROL Outbound SMS coding]**

在&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;选项卡中：

* **[!UICONTROL Coding when sending]** 对应  **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 对应  **[!UICONTROL ID Format in the SR]**

### 从Sybase365连接器{#from-sybase}

在&#x200B;**[!UICONTROL Sybase365]**&#x200B;连接器中，您可以转换到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

![](assets/smpp_3.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;选项卡中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### 从CLX连接器{#from-clx}

在&#x200B;**[!UICONTROL CLX]**&#x200B;连接器中，您可以转换到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

![](assets/smpp_4.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;选项卡中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;选项卡中：

* **[!UICONTROL Source number]**

在&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;选项卡中：

* **[!UICONTROL Coding when sending]** 对应  **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 对应  **[!UICONTROL ID Format in the SR]**

### 从Tele2连接器{#from-tele2}

在&#x200B;**[!UICONTROL Tele2]**&#x200B;连接器中，您可以转换到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

![](assets/smpp_6.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;选项卡中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;选项卡中：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

在&#x200B;**[!UICONTROL Mapping of Encoding]**&#x200B;选项卡中：

* **[!UICONTROL Outbound SMS coding]**

### 从O2连接器{#from-O2}

在&#x200B;**[!UICONTROL O2]**&#x200B;连接器中，您可以转换到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

![](assets/smpp_5.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;选项卡中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;选项卡中：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**