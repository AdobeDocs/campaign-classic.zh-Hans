---
solution: Campaign Classic
product: campaign
title: ACS连接器原理和数据周期
description: ACS连接器原理和数据周期
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1990'
ht-degree: 0%

---


# ACS连接器原理和数据循环{#acs-connector-principles-and-data-cycle}

## 简介 {#introduction}

ACS连接器桥接Adobe Campaignv7和Adobe Campaign Standard。 它是活动 v7中的一个集成功能，可将数据自动复制到Campaign Standard，将两个应用程序的最佳功能结合在一起。 活动 v7具有用于管理主营销数据库的高级工具。 活动 v7中的Campaign Standard复制使能够以用户友好的环境利用丰富数据。

![](assets/acs_connect_puzzle_link_01.png)

借助ACS Connector，数字营销人员继续使用Campaign Standard设计、目标和执行活动，而活动 v7为面向数据的用户（如数据库营销人员）量身定制。

>[!IMPORTANT]
>
>ACS连接器仅作为Adobe CampaignPrime产品的一部分提供。 有关如何许可Adobe Campaign Prime的更多信息，请与您的客户经理联系。
>
>ACS连接器仅适用于托管和混合架构。 它不适用于完整的内部部署安装。
>
>要使用此功能，您必须连接到活动与Adobe ID(IMS)。 请参阅[通过Adobe ID](../../integrations/using/about-adobe-id.md)连接。

此文档显示ACS连接器功能。 以下各节提供了有关此功能如何复制数据的信息以及有关如何使用复制用户档案的说明。

* [流程](#process):ACS连接器概述以及数据复制的管理方式。
* [实施](#implementation):如何开始使用ACS Connector的概述以及如何复制基本和高级数据的说明。
* [同步用户档案](../../integrations/using/synchronizing-profiles.md):关于如何复制用户档案以及如何使用投放的说明。
* [同步受众](../../integrations/using/synchronizing-audiences.md):关于如何在活动 v7中目标列表收件人，然后将列表作为受众复制到Campaign Standard的说明。
* [同步Web应用程序](../../integrations/using/synchronizing-web-applications.md):有关如何将活动 v7 Web应用程序链接到Campaign Standard的说明。
* [ACS连接器故障诊断](../../integrations/using/troubleshooting-the-acs-connector.md):查看常见问题的答案。

>[!NOTE]
>
>根据许可协议，ACS Connector随活动 v7提供。 要使用ACS连接器，请确保可以在活动 v7和Campaign Standard之间切换。 如果您不确定您的版本及其包含的功能，请与管理员联系。

## 印刷色 {#process}

### 数据复制{#data-replication}

![](assets/acs_connect_flows_01.png)

ACS Connector会定期将以下项目从活动 v7复制到Campaign Standard:

* **收件人**
* **订阅**
* **服务**
* **登陆页面**

默认情况下，ACS连接器的定期复制每15分钟一次。 可以根据您的需要调整周期复制的范围。 如果需要更改，请与顾问联系。

收件人、订阅、服务和登陆页的数据复制是增量的，这意味着只有新收件人和对现有收件人的修改从活动 v7复制到Campaign Standard。 但是，受众复制发生在单个实例中。 您可以在活动 v7中创建受众，然后将其复制一次到Campaign Standard。 复制是即时的，无法为常规更新配置。 有关说明，请参阅[同步受众](../../integrations/using/synchronizing-audiences.md)。

>[!NOTE]
>
>请耐心等待大型数据库的初始复制，因为它可能需要几个小时的时间。 但是，后续复制是增量的，而且速度要快得多。

ACS Connector会定期将以下项目从Campaign Standard复制到活动 v7:

* **[!UICONTROL Delivery IDs]**
* **[!UICONTROL Email broad logs]**
* **[!UICONTROL Email tracking logs]**

通过复制投放ID和电子邮件日志，可以从活动 v7访问v7收件人的投放历史记录和跟踪数据。

>[!IMPORTANT]
>
>只有电子邮件广播和跟踪日志从Campaign Standard复制到活动 v7。

### 数据同步{#data-synchronization}

![](assets/acs_connect_flows_02.png)

ACS连接器在活动 v7和Campaign Standard之间同步隔离。

例如，已从活动 v7复制到Campaign Standard的用户档案包括电子邮件地址。 如果电子邮件地址被Campaign Standard隔离，则在下次同步期间数据将传递到活动 v7。 有关隔离的详细信息，请参阅[隔离管理](../../delivery/using/understanding-quarantine-management.md)和[Campaign Standard隔离](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)。

### 使用复制的用户档案{#using-replicated-profiles}

Campaign Standard和活动 v7可以使用复制用户档案来定位营销活动中的工作流。

有关如何使用复制用户档案在Campaign Standard中发送投放的说明，请参阅[同步用户档案](../../integrations/using/synchronizing-profiles.md)。 还提供了在活动 v7和Campaign Standard之间共享退订数据的其他说明。

### 限制{#limitations}

复制用户档案可供投放使用，但在Campaign Standard方面有某些限制。 查看以下项目，了解如何最好地管理它们。

* **Campaign Standard的只读用户档案**:复制的用户档案在Campaign Standard中为只读。但是，您可以在活动 v7中编辑收件人，并且修改会由ACS连接器在Campaign Standard中自动更新。
* **用户档案在Campaign Standard中创建**:ACS连接器将收件人数据从活动 v7复制到Campaign Standard。因此，源于Campaign Standard的用户档案不会复制到活动 v7。
* **用于收件人的基本Campaign Standard数据**:ACS连接器复制适合收件人的Campaign Standard数据。它包括收件人姓名、地址、电子邮件地址、手机号码、家庭电话号码和其他相关的联系信息。 如果活动 v7中提供的其他收件人字段和自定义定位表对您的工作流至关重要，请咨询您的顾问。
* **导入隔离用户档案**:不希望与列表联系的用户档案可以作为隔离用户档案导入活动 v7或Campaign Standard。用户档案的状态包含在应用程序之间的隔离同步中，不会在投放中使用。
* **取消订阅Campaign Standard中的服务**:取消订阅投放的选项未从Campaign Standard同步到活动 v7。但是，您可以配置Campaign Standard投放，以将其退订链接定向到活动 v7。 单击退订链接的收件人的用户档案将在活动 v7中更新，并将数据复制到Campaign Standard。 请参阅[更改退订链接](../../integrations/using/synchronizing-profiles.md#changing-the-unsubscription-link)。
* 只有电子邮件广播和跟踪日志从Campaign Standard复制到活动 v7。

### 付费 {#billing}

您选择发送投放、活动v7或Campaign Standard时，帐单不会受到影响。 帐单信息可在活动v7和Campaign Standard之间协调。 因此，如果您使用这两个应用程序将投放发送到同一收件人，它仍计为一个活动用户档案。

## 实现{#implementation}

ACS连接器有两种实现类型。 这两个任务始终由Adobe Campaign咨询团队执行。

>[!IMPORTANT]
>
>本节仅面向专家用户，为他们提供实施过程及其主要步骤的全球视图。
>
>请勿尝试通过任何方式自己执行任何这些实施。 它仅由Adobe Campaign顾问负责。

**基本实现**&#x200B;允许您复制收件人（现成字段）、服务和订阅、Web应用程序和受众。 这是从活动 v7到Campaign Standard的单向复制。

**高级实现**&#x200B;将允许您执行更复杂的用例，例如，如果您有其他收件人字段或自定义收件人表（例如，事务表）。 请参阅[高级实现](#advanced-implementation)。

### 安装程序包{#installing-the-package}

要使用该功能，需要安装&#x200B;**[!UICONTROL ACS Connector]**&#x200B;包。 这始终由Adobe技术管理员或顾问执行。

与ACS连接器相关的所有技术元素都在资源管理器的&#x200B;**[!UICONTROL Administration > ACS Connector]**&#x200B;节点中可用。

### 技术和复制工作流{#technical-and-replication-workflows}

安装软件包后，**[!UICONTROL Administration > ACS Connector > Process]**&#x200B;下有两个技术工作流可用。

>[!IMPORTANT]
>
>切勿尝试修改这些工作流。 它们绝不应出错或暂停。 如果发生这种情况，请联系您的Adobe Campaign顾问。

![](assets/acs_connect_implementation_3.png)

* **[!UICONTROL `[ACS] Quarantine synchronization`]** (quarantineSync):此工作流将同步所有隔离信息。活动 v7中的所有新隔离都被复制到Campaign Standard中。 所有来自Campaign Standard的新隔离都被复制到活动 v7中。 这保证所有排除规则都在活动 v7和Campaign Standard之间同步。
* **[!UICONTROL `[ACS] Security group synchronization`]** (securityGroupSync):此工作流用于权限转换。请参阅[权限转换](#rights-conversion)。

以下复制工作流可作为“准备使用”模板使用。 它们需要由您的Adobe Campaign顾问实施。

![](assets/acs_connect_implementation_2.png)

* **[!UICONTROL `[ACS] Profile replication`]** (newProfileReplication):此增量式工作流将收件人复制到Campaign Standard。默认情况下，它会复制所有现成的收件人字段。 请参阅[默认收件人字段](#default-recipient-fields)。
* **[!UICONTROL `[ACS] Service replication`]** (newServiceReplication):此增量式工作流会将所选服务复制到Campaign Standard。请参见用例[同步Web应用程序](../../integrations/using/synchronizing-web-applications.md)。
* **[!UICONTROL `[ACS] Landing pages replication`]** (newLandingPageReplication):此增量式工作流将所选的Web应用程序复制到Campaign Standard。活动 v7 Web应用程序将显示为Campaign Standard中的登陆页。 请参见用例[同步Web应用程序](../../integrations/using/synchronizing-web-applications.md)。
* **[!UICONTROL `[ACS] New replication`]** （新复制）：此增量式工作流是可用于复制自定义表的示例。请参阅[高级实现](#advanced-implementation)。
* **[!UICONTROL `[ACS] Delivery-mesage replication`]** (newDlvMsgAcelification):此增量式工作流将投放消息从Campaign Standard复制到活动 v7。
* **[!UICONTROL `[ACS] Profile delivery log replication`]** (newRcpDeliveryLogReplication):此增量式工作流程将投放ID、电子邮件广泛日志和电子邮件跟踪日志从Campaign Standard复制到活动 v7。它只考虑从Campaign Standard发送到作为活动 v7的nms:收件人表一部分的用户档案的投放。
* **[!UICONTROL `[ACS] New delivery log replication`]** (newRcpDeliveryLogReplication):此增量式工作流程将投放ID、电子邮件广泛日志和电子邮件跟踪日志从Campaign Standard复制到活动 v7。它只考虑从Campaign Standard发送到作为活动 v7特定表(定义nms:收件人除外)一部分的用户档案的投放。

### 默认收件人字段{#default-recipient-fields}

如果您有任何其他字段或自定义表（例如，事务处理表），则默认情况下不会复制这些字段或表。 需要执行高级配置。 请参阅[高级实现](#advanced-implementation)。

您将在下面的收件人字段列表中找到与基本实施一起复制的内容。 这些是现成的字段：

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 源Id<br /> </td> 
   <td> @sourceId<br /> </td> 
  </tr> 
  <tr> 
   <td> 创建日期<br /> </td> 
   <td> @created<br /> </td> 
  </tr> 
  <tr> 
   <td> 修改日期<br /> </td> 
   <td> @lastModified<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @email<br /> </td> 
  </tr> 
  <tr> 
   <td> 姓氏<br /> </td> 
   <td> @lastName<br /> </td> 
  </tr> 
  <tr> 
   <td> 名字<br /> </td> 
   <td> @firstName<br /> </td> 
  </tr> 
  <tr> 
   <td> 中间名<br /> </td> 
   <td> @middleName<br /> </td> 
  </tr> 
  <tr> 
   <td> 手机<br /> </td> 
   <td> @mobilePhone<br /> </td> 
  </tr> 
  <tr> 
   <td> 出生日期<br /> </td> 
   <td> @birthDate<br /> </td> 
  </tr> 
  <tr> 
   <td> 性别<br /> </td> 
   <td> @gender<br /> </td> 
  </tr> 
  <tr> 
   <td> Salutation<br /> </td> 
   <td> @salutation<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再联系(由任何渠道)<br /> </td> 
   <td> @blackList<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再通过电子邮件联系<br /> </td> 
   <td> @blackListEmail<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再通过SMS<br />联系 </td> 
   <td> @blackListMobile<br /> </td> 
  </tr> 
  <tr> 
   <td> 电话<br /> </td> 
   <td> @phone<br /> </td> 
  </tr> 
  <tr> 
   <td> 传真<br /> </td> 
   <td> @fax<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址1(apartment)<br /> </td> 
   <td> [location/@address1]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址2<br /> </td> 
   <td> [location/@address2]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址3（数字和街道）<br /> </td> 
   <td> [location/@address3]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址4（县）<br /> </td> 
   <td> [location/@address4]<br /> </td> 
  </tr> 
  <tr> 
   <td> 邮政编码<br /> </td> 
   <td> [location/@zipCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> 城市<br /> </td> 
   <td> [location/@city]<br /> </td> 
  </tr> 
  <tr> 
   <td> 州/省代码<br /> </td> 
   <td> [location/@stateCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> 国家/地区代码<br /> </td> 
   <td> [location/@countryCode]<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 权限转换{#rights-conversion}

在活动 v7和Campaign Standard中，权限处理方式不同。 在活动 v7中，权限管理基于文件夹，而在Campaign Standard中，权限管理基于单位访问（组织/地理单位）。 Campaign Standard用户属于包含限制上下文的安全组。 因此，需要转换活动 v7权限系统以匹配Campaign Standard。 可通过多种方式执行权限转换。 您将在下面找到一个实施示例。

1. 在&#x200B;**[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**&#x200B;下，使用&#x200B;**[!UICONTROL Synchronize]**&#x200B;按钮检索所有Campaign Standard安全组。 不包括现成的Campaign Standard组。

   ![](assets/acs_connect_implementation_4.png)

1. 如果您的权限管理是基于文件夹的，请转到&#x200B;**[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]**，然后将每个需要的文件夹与一个安全组映射。

   ![](assets/acs_connect_implementation_5.png)

1. 然后，复制工作流将使用此信息，并向每个要复制的对象添加相应的组织/地理单位。

### 高级实现{#advanced-implementation}

本节介绍在高级实施方面的一些可能性。

>[!IMPORTANT]
>
>此信息只能用作一般准则。 请联系您的Adobe Campaign顾问以了解实施。

高级实施将根据客户的需要添加自定义复制工作流。 以下是几个示例：

* 投放复制
* 活动复制
* 项目复制
* 种子成员复制
* 事务复制
* 等。

**在收件人上复制扩展字段**

在基本实现中，即装即用的收件人字段被复制。 如果要复制添加到收件人模式的自定义字段，您需要识别这些字段。

1. 在&#x200B;**[!UICONTROL Administration > ACS Connector > Data mapping]**&#x200B;下，在&#x200B;**[!UICONTROL nms:recipient]**&#x200B;表上创建定位映射。

   ![](assets/acs_connect_implementation_6.png)

1. 选择要复制的其他字段和其他所需信息（索引、链接、标识键）。

   ![](assets/acs_connect_implementation_7.png)

1. 打开专用的用户档案复制工作流（不是模板，而是工作流实例本身）。 修改&#x200B;**[!UICONTROL Query]**&#x200B;和&#x200B;**[!UICONTROL Update data]**&#x200B;活动以包括这些字段。 请参阅[技术和复制工作流](#technical-and-replication-workflows)。

   ![](assets/acs_connect_implementation_8.png)

   ![](assets/acs_connect_implementation_9.png)

**复制自定义用户档案表**

通过基本实现，可复制现成的收件人表。 如果您添加了自定义收件人表，则可以通过以下方式识别这些表。

1. 在&#x200B;**[!UICONTROL Administration > ACS Connector > Data mapping]**&#x200B;下，在自定义用户档案表上创建定位映射。

   ![](assets/acs_connect_implementation_10.png)

1. 定义要复制的标识数据、索引、链接和字段。

   ![](assets/acs_connect_implementation_10.png)

1. 如果您的权限管理基于文件夹，请转到&#x200B;**[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]**，然后为链接到自定义表的文件夹定义一个安全组。 请参阅[权限转换](#rights-conversion)。
1. 使用&#x200B;**[!UICONTROL New replication]**&#x200B;工作流（不是模板，而是工作流实例本身）包括自定义表和要复制的字段。 请参阅[技术和复制工作流](#technical-and-replication-workflows)。

