---
product: campaign
title: 不支持的短信连接器迁移
description: 将不支持的SMS连接器迁移到扩展通用SMPP连接器
feature: SMS, Upgrade
hidefromtoc: true
exl-id: 60acf80c-8506-410b-ab2c-4f67a5677b43
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 1%

---

# 将不支持的SMS连接器迁移到扩展通用SMPP连接器{#unsupported-connector-migration}



从版本20.2开始，弃用旧版连接器。 本文档将帮助您将在旧系统上仍在运行的连接器迁移到推荐的SMPP连接器。

>[!CAUTION]
>
>此迁移不是强制性的，但由Adobe推荐，它将确保您在受支持的最新软件版本上运行。

## 关于SMS连接器 {#about-sms-connectors}

以下连接器自版本20.2起已弃用：

* **[!UICONTROL Generic SMPP]** （支持二进制模式的SMPP版本3.4）
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

已弃用的功能仍然可用并受支持，但不会进一步增强它们。 我们建议使用&#x200B;**[!UICONTROL Extended generic SMPP]**&#x200B;连接器。

有关已弃用和已删除功能的详细信息，请参阅此[页面](../../rn/using/deprecated-features.md)。

旧的SMS连接器使用的Java SMS连接器会重载Web进程。 迁移到新&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;连接器会将此负载移动到可以支持它的MTA。

## 迁移到扩展的通用SMPP连接器 {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>即使您可以转换参数，配置&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;连接器也需要与提供商联系，提供商将为您提供填写其余参数所需的信息。 有关详细信息，请参见此 [ 页面](sms-protocol.md)。

首先，您需要创建一个新的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;外部帐户，然后您可能能够转置某些参数。 您可以在此[页面](sms-set-up.md#creating-an-smpp-external-account)中找到详细步骤。

现在，您需要从新创建的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;外部帐户的&#x200B;**[!UICONTROL Mobile]**&#x200B;选项卡中填写参数，具体取决于您之前的连接器。

### 从通用连接器 {#from-generic-connector}

选择&#x200B;**[!UICONTROL Generic]**&#x200B;连接器时，您应该具有适应各种情况的自定义JavaScript连接器。

如果您知道此连接器已在使用SMPP协议，则可以迁移到&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;连接器。 如果不支持，请与您的提供商联系，了解他们是否支持SMPP协议，并在顾问的帮助下设置新连接器。

通过您的&#x200B;**[!UICONTROL Generic]**&#x200B;连接器，您可以转接到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

![](assets/smpp_generic.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;选项卡中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### 来自通用SMPP连接器 {#from-generic-smpp-connector}

通过您的&#x200B;**[!UICONTROL Generic SMPP]**&#x200B;连接器，您可以转接到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

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

* **[!UICONTROL Coding when sending]**&#x200B;对应于&#x200B;**[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]**&#x200B;对应于&#x200B;**[!UICONTROL ID Format in the SR]**

### 从Sybase365连接器 {#from-sybase}

通过您的&#x200B;**[!UICONTROL Sybase365]**&#x200B;连接器，您可以转接到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

![](assets/smpp_3.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;选项卡中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### 来自CLX连接器 {#from-clx}

通过您的&#x200B;**[!UICONTROL CLX]**&#x200B;连接器，您可以转接到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

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

* **[!UICONTROL Coding when sending]**&#x200B;对应于&#x200B;**[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]**&#x200B;对应于&#x200B;**[!UICONTROL ID Format in the SR]**

### 从Tele2连接器 {#from-tele2}

通过您的&#x200B;**[!UICONTROL Tele2]**&#x200B;连接器，您可以转接到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

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

### 从O2连接器 {#from-O2}

通过您的&#x200B;**[!UICONTROL O2]**&#x200B;连接器，您可以转接到新创建的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帐户：

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
