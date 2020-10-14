---
title: ACS连接器原理和数据周期
seo-title: ACS连接器原理和数据周期
description: ACS连接器原理和数据周期
seo-description: null
page-status-flag: never-activated
uuid: ea62ee69-042e-4c18-aaea-d65872d07dd9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 64d87bea-2376-4684-ac93-6ca56fe0f262
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 0%

---


# ACS Connector principles and data cycle{#acs-connector-principles-and-data-cycle}

## 简介 {#introduction}

ACS连接器桥Adobe Campaignv7和Adobe Campaign Standard。 它是v7活动中的一个集成功能，可自动将Campaign Standard复制到数据中，从而将两种应用程序的最佳结合起来。 活动v7具有用于管理主营销数据库的高级工具。 活动v7的数据复制使Campaign Standard能够在用户友好的环境中利用丰富数据。

![](assets/acs_connect_puzzle_link_01.png)

借助ACS Connector，数字营销人员继续使用Campaign Standard来设计、目标和执行活动，而活动v7为面向数据的用户（如数据库营销人员）量身定制。

>[!IMPORTANT]
>
>ACS连接器仅作为Adobe CampaignPrime产品的一部分提供。 有关如何许可Adobe CampaignPrime的更多信息，请与客户经理联系。
>
>ACS连接器仅适用于托管和混合架构。 它不适用于完整的内部部署安装。
>
>要使用此功能，您必须连接到Adobe ID(IMS)的活动。 See [Connecting via an Adobe ID](../../integrations/using/about-adobe-id.md).

此文档显示ACS连接器功能。 以下各节提供了有关该功能如何复制数据的信息以及有关如何使用复制用户档案的说明。

* [流程](#process):ACS连接器概述以及如何管理数据复制。
* [实施](#implementation):如何开始使用ACS连接器的概述以及如何复制基本和高级数据的说明。
* [同步用户档案](../../integrations/using/synchronizing-profiles.md):有关如何复制用户档案以及如何使用投放的说明。
* [同步受众](../../integrations/using/synchronizing-audiences.md):关于如何在活动v7中目标列表收件人，然后将列表复制到Campaign Standard作为受众的说明。
* [同步Web应用程序](../../integrations/using/synchronizing-web-applications.md):有关如何将活动v7 Web应用程序链接到Campaign Standard的说明。
* [ACS连接器故障诊断](../../integrations/using/troubleshooting-the-acs-connector.md):查看常见问题的答案。

>[!NOTE]
>
>ACS Connector包含在许可协议中的活动v7中。 要使用ACS连接器，请确保可以在活动v7和Campaign Standard之间切换。 如果您不确定您的版本及其附带的功能，请与管理员联系。

## 印刷色 {#process}

### 数据复制 {#data-replication}

![](assets/acs_connect_flows_01.png)

ACS连接器将定期从活动v7复制到Campaign Standard:

* **收件人**
* **订阅**
* **服务**
* **登陆页面**

默认情况下，ACS连接器的定期复制每15分钟一次。 可以调整定期复制的范围以满足您的需求。 如果需要更改，请与顾问联系。

收件人、订阅、服务和登陆页的数据复制是增量复制，这意味着只有新收件人和对现有收件人的修改从活动v7复制到Campaign Standard。 但是，受众复制发生在单个实例中。 您可以在活动v7中创建受众，然后将其复制一次到Campaign Standard。 复制是即时的，无法为常规更新配置。 有关说明，请参 [阅同步受众](../../integrations/using/synchronizing-audiences.md)。

>[!NOTE]
>
>请耐心等待大型数据库的初始复制，因为它可能需要几个小时。 但是，后续复制是增量的，而且速度要快得多。

ACS连接器将以下项目定期从Campaign Standard复制到活动v7:

* **[!UICONTROL Delivery IDs]**
* **[!UICONTROL Email broad logs]**
* **[!UICONTROL Email tracking logs]**

通过复制投放ID和电子邮件日志，可以访问v7收件人的投放历史记录和跟踪v7活动的数据。

>[!IMPORTANT]
>
>只有电子邮件广告和跟踪日志从Campaign Standard复制到活动v7。

### 数据同步 {#data-synchronization}

![](assets/acs_connect_flows_02.png)

ACS连接器在活动v7和Campaign Standard之间同步隔离。

例如，已从活动v7复制到Campaign Standard的用户档案包含电子邮件地址。 如果Campaign Standard隔离了电子邮件地址，则在下次同步过程中，数据将传递到活动v7。 有关隔离的详细信息，请参 [阅隔离](../../delivery/using/understanding-quarantine-management.md) 管理 [和Campaign Standard隔离](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)。

### 使用复制用户档案 {#using-replicated-profiles}

复制用户档案可由Campaign Standard和活动v7用于定位营销活动中的工作流。

有关如何使用复制投放在Campaign Standard中发送用户档案的说明，请参阅同 [步用户档案](../../integrations/using/synchronizing-profiles.md)。 还提供了在退订v7和Campaign Standard之间共享活动数据的其他说明。

### 限制{#limitations}

复制用户档案可供投放使用，但在Campaign Standard方面有某些限制。 查看以下项目，了解如何最好地管理它们。

* **Campaign Standard的只读用户档案**:复制的用户档案在Campaign Standard中为只读。 但是，您可以在活动v7中编辑收件人，并且修改会由ACS连接器以Campaign Standard自动更新。
* **用户档案在Campaign Standard中创建**:ACS连接器将收件人数据从活动v7复制到Campaign Standard。 因此，源自Campaign Standard的用户档案不会复制到活动v7。
* **收件人的基本Campaign Standard数据**:ACS连接器复制适合收件人的Campaign Standard数据。 它包括收件人的姓名、地址、电子邮件地址、移动电话号码、家庭电话号码和其他相关的联系信息。 如果活动v7中提供的其他收件人字段和自定义定位表对您的工作流至关重要，请咨询您的顾问。
* **导入隔离的用户档案**:不希望与列表联系的用户档案可以作为隔离的用户档案导入活动v7或Campaign Standard。 用户档案的状态包括在应用程序之间的隔离同步中，不会在投放中使用。
* **取消订阅Campaign Standard中的服务**:取消订阅投放的选项未从Campaign Standard同步到活动v7。 但是，您可以配置Campaign Standard投放，将其退订链接定向到活动v7。 单击退订链接的收件人的用户档案在活动v7中更新，并将数据复制到Campaign Standard。 请参 [阅更改退订链接](../../integrations/using/synchronizing-profiles.md#changing-the-unsubscription-link)。
* 只有电子邮件广告和跟踪日志从Campaign Standard复制到活动v7。

### 付费 {#billing}

您选择发送投放、活动v7或Campaign Standard，不会影响计费。 在活动v7和Campaign Standard之间对帐单信息进行协调。 因此，如果您使用两个应用程序将投放发送到同一收件人，它仍计为一个活动用户档案。

## 实施 {#implementation}

ACS连接器有两种实现类型。 这两个任务始终由Adobe Campaign咨询团队执行。

>[!IMPORTANT]
>
>本节仅面向专家用户，为他们提供实施过程及其主要步骤的全球视图。
>
>请勿尝试通过任何方式自己执行任何这些实施。 它严格由Adobe Campaign顾问负责。

基 **本实施** 允许您复制收件人（现成字段）、服务和订阅、Web应用程序和受众。 这是从活动v7到Campaign Standard的单向复制。

高级 **实施** 将允许您执行更复杂的用例，例如，如果您有其他收件人字段或自定义收件人表（例如，事务表）。 请参 [阅高级实施](#advanced-implementation)。

### 安装包 {#installing-the-package}

要使用该功能， **[!UICONTROL ACS Connector]** 需要安装该包。 这始终由Adobe技术管理员或顾问执行。

与ACS连接器相关的所有技术元素都可在资 **[!UICONTROL Administration > ACS Connector]** 源管理器的节点中使用。

### 技术和复制工作流 {#technical-and-replication-workflows}

安装软件包后，可在下面找到两个技术工作流 **[!UICONTROL Administration > ACS Connector > Process]**。

>[!IMPORTANT]
>
>切勿尝试修改这些工作流。 它们不应出错或暂停。 如果发生这种情况，请联系您的Adobe Campaign顾问。

![](assets/acs_connect_implementation_3.png)

* **[!UICONTROL `[ACS] Quarantine synchronization`]** (quarantineSync):此工作流将同步所有隔离信息。 活动v7中的所有新隔离都被复制到Campaign Standard。 所有来自Campaign Standard的新隔离都被复制到活动v7。 这保证所有排除规则在活动v7和Campaign Standard之间同步。
* **[!UICONTROL `[ACS] Security group synchronization`]** (securityGroupSync):此工作流用于权限转换。 请参阅 [权限转换](#rights-conversion)。

以下复制工作流可作为“准备使用”模板使用。 它们需要由您的Adobe Campaign顾问实施。

![](assets/acs_connect_implementation_2.png)

* **[!UICONTROL `[ACS] Profile replication`]** (newProfileReplication):此增量工作流将收件人复制到Campaign Standard。 默认情况下，它复制所有现成的收件人字段。 请参阅 [默认收件人字段](#default-recipient-fields)。
* **[!UICONTROL `[ACS] Service replication`]** (newServiceReplication):此增量式工作流将所选服务复制到Campaign Standard。 请参阅同步Web应 [用程序的用例](../../integrations/using/synchronizing-web-applications.md)。
* **[!UICONTROL `[ACS] Landing pages replication`]** (newLandingPageReplication):此增量式工作流程将选定的Web应用程序复制到Campaign Standard。 活动v7 Web应用程序将显示为Campaign Standard中的登陆页。 请参阅同步Web应 [用程序的用例](../../integrations/using/synchronizing-web-applications.md)。
* **[!UICONTROL `[ACS] New replication`]** (newReplication):此增量式工作流是一个可用于复制自定义表的示例。 请参 [阅高级实施](#advanced-implementation)。
* **[!UICONTROL `[ACS] Delivery-mesage replication`]** (newDlvMsgEqualition):此增量工作流将投放消息从Campaign Standard复制到活动v7。
* **[!UICONTROL `[ACS] Profile delivery log replication`]** (newRcpDeliveryLogReplication):此增量式工作流程将投放ID、电子邮件广泛日志和电子邮件跟踪日志从Campaign Standard复制到活动v7。 它只考虑从Campaign Standard发送到属于收件人v7的nms:投放表的用户档案的活动。
* **[!UICONTROL `[ACS] New delivery log replication`]** (newRcpDeliveryLogReplication):此增量式工作流程将投放ID、电子邮件广泛日志和电子邮件跟踪日志从Campaign Standard复制到活动v7。 它只考虑从Campaign Standard发送到作为活动v7特定表(定义nms:收件人除外)的用户档案的投放。

### 默认收件人字段 {#default-recipient-fields}

如果您有任何其他字段或自定义表（例如，事务表），则默认情况下不会复制这些字段或表。 需要执行高级配置。 请参 [阅高级实施](#advanced-implementation)。

您将在与基本实施一起复制的收件人字段列表下找到。 这些是现成的字段：

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 源ID<br /> </td> 
   <td> @sourceId<br /> </td> 
  </tr> 
  <tr> 
   <td> 创建日期<br /> </td> 
   <td> 已创建<br /> </td> 
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
   <td> 问候<br /> </td> 
   <td> @salution<br /> </td> 
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
   <td> 不再通过SMS联系<br /> </td> 
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
   <td> 地址1（公寓）<br /> </td> 
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
   <td> [位置/@city]<br /> </td> 
  </tr> 
  <tr> 
   <td> 州／省代码<br /> </td> 
   <td> [location/@stateCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> 国家／地区代码<br /> </td> 
   <td> [location/@countryCode]<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 权限转换 {#rights-conversion}

在活动v7和Campaign Standard中，权限处理方式不同。 在活动v7中，权限管理基于文件夹，而在Campaign Standard中，权限管理基于单位访问（组织／地理单位）。 Campaign Standard用户属于包含限制上下文的安全组。 因此，活动v7权限系统需要转换为与Campaign Standardv7权限系统匹配。 有几种方法可执行权限转换。 您将在下面找到一个实施示例。

1. 在下 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**&#x200B;面，使 **[!UICONTROL Synchronize]** 用按钮检索所有Campaign Standard安全组。 现成Campaign Standard组被排除。

   ![](assets/acs_connect_implementation_4.png)

1. 如果您的权限管理是基于文件夹的，请转 **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** 到并将每个需要的文件夹与一个安全组映射。

   ![](assets/acs_connect_implementation_5.png)

1. 然后，复制工作流将使用此信息，并将相应的组织／地理单元添加到每个要复制的对象。

### 高级实施 {#advanced-implementation}

本节介绍高级实施方面的一些可能性。

>[!IMPORTANT]
>
>此信息只能用作一般准则。 与Adobe Campaign顾问联系以了解实施。

高级实施将根据客户的需要添加自定义复制工作流。 以下是几个示例：

* 投放复制
* 活动复制
* 项目复制
* 种子成员复制
* 事务复制
* 等等。

**在收件人上复制扩展字段**

在基本实现中，将复制现成的收件人字段。 如果要复制已添加到收件人模式的自定义字段，您需要识别这些字段。

1. 在 **[!UICONTROL Administration > ACS Connector > Data mapping]**&#x200B;下，在表上创建定位 **[!UICONTROL nms:recipient]** 映射。

   ![](assets/acs_connect_implementation_6.png)

1. 选择要复制的其他字段和其他所需信息（索引、链接、标识键）。

   ![](assets/acs_connect_implementation_7.png)

1. 打开专用的用户档案复制工作流（不是模板，而是工作流实例本身）。 修改和 **[!UICONTROL Query]** 活动 **[!UICONTROL Update data]** 以包含这些字段。 请参 [阅技术和复制工作流](#technical-and-replication-workflows)。

   ![](assets/acs_connect_implementation_8.png)

   ![](assets/acs_connect_implementation_9.png)

**复制自定义用户档案表**

通过基本实现，可复制现成的收件人表。 如果您添加了自定义收件人表，则您可以通过以下方式识别这些表。

1. 在 **[!UICONTROL Administration > ACS Connector > Data mapping]**&#x200B;下，在自定义用户档案表上创建定位映射。

   ![](assets/acs_connect_implementation_10.png)

1. 定义要复制的标识数据、索引、链接和字段。

   ![](assets/acs_connect_implementation_10.png)

1. 如果您的权限管理基于文件夹，请转 **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]**&#x200B;到并为链接到自定义表的文件夹定义安全组。 请参阅 [权限转换](#rights-conversion)。
1. 使用工 **[!UICONTROL New replication]** 作流（不是模板，而是工作流实例本身）来包含自定义表和要复制的字段。 请参 [阅技术和复制工作流](#technical-and-replication-workflows)。

