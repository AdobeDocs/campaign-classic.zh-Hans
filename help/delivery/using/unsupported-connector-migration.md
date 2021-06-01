---
product: campaign
title: 不支持的SMS连接器迁移
description: 将不支持的SMS连接器迁移到扩展通用SMPP连接器
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
hidefromtoc: true
exl-id: 60acf80c-8506-410b-ab2c-4f67a5677b43
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---

# 将不支持的SMS连接器迁移到扩展通用SMPP连接器{#unsupported-connector-migration}

自20.2版起，弃用旧版连接器。 本文档将帮助您将仍在旧系统上运行的连接器迁移到推荐的SMPP连接器。

>[!CAUTION]
>
>此迁移并非强制性的，但是Adobe建议进行此迁移，并将确保您运行的软件是受支持的最新版本。

## 关于SMS连接器{#about-sms-connectors}

以下连接器自20.2版起已弃用：

* **[!UICONTROL Generic SMPP]** （支持二进制模式的SMPP版本3.4）
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

已弃用的功能仍然可用且受支持，但将不会进一步增强这些功能。 我们建议使用&#x200B;**[!UICONTROL Extended generic SMPP]**&#x200B;连接器。

有关已弃用和已删除功能的更多信息，请参阅此[page](../../rn/using/deprecated-features.md)。

旧的SMS连接器使用的Java SMS连接器会过载Web进程。 迁移到新的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;连接器会将此负载移至MTA，MTA可支持此负载。

## 迁移到扩展的通用SMPP连接器{#migrating-extended-generic-smpp}

>[!CAUTION]
>
>即使您能够转置参数，配置&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;连接器也要求您与提供商进行沟通，提供商将为您提供填充其余参数所需的信息。 有关详细信息，请参见此 [ 页面](../../delivery/using/sms-protocol.md)。

首先，您需要创建一个新的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;外部帐户，然后才能转换某些参数。 您可以在此[page](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)中找到详细步骤。

现在，您需要从新创建的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;外部帐户的&#x200B;**[!UICONTROL Mobile]**&#x200B;选项卡中填写参数，具体取决于您之前的连接器。

### 从通用连接器{#from-generic-connector}

选择&#x200B;**[!UICONTROL Generic]**&#x200B;连接器时，您应该有一个自定义JavaScript连接器，该连接器将适应每种情况。

如果您知道此连接器已在使用SMPP协议，则可以迁移到&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;连接器。 如果不支持，请咨询您的提供商（如果支持SMPP协议），并在顾问的帮助下设置新连接器。

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

* **[!UICONTROL Coding when sending]** 对应于  **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 对应于  **[!UICONTROL ID Format in the SR]**

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

* **[!UICONTROL Coding when sending]** 对应于  **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 对应于  **[!UICONTROL ID Format in the SR]**

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
