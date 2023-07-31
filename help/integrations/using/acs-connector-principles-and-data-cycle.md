---
product: campaign
title: ACS连接器入门
description: ACS Connector原则和数据周期
feature: ACS Connector
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
hide: true
hidefromtoc: true
exl-id: 689b6117-5143-4f85-8582-2c74cae72ca2
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '2045'
ht-degree: 2%

---

# ACS连接器入门{#acs-connector-gs}



ACS连接器用于连接Adobe Campaign v7和Adobe Campaign Standard。 它是Campaign v7中的一项集成功能，可自动将数据复制到Campaign Standard，将两个应用程序的优点结合起来。 Campaign v7具有管理主营销数据库的高级工具。 通过Campaign v7的数据复制，Campaign Standard可在用户友好的环境中利用丰富的数据。

![](assets/acs_connect_puzzle_link_01.png)

借助ACS Connector，数字营销人员继续使用Campaign Standard来设计、定位和执行营销活动，而Campaign v7则为数据导向用户（如数据库营销人员）量身定制。

>[!IMPORTANT]
>
>ACS连接器仅作为Adobe Campaign Prime产品的一部分提供。 有关如何许可Adobe Campaign Prime的更多信息，请联系您的客户经理。
>
>ACS连接器仅适用于托管架构和混合架构。 它不适用于完全的内部部署。
>
>要使用此功能，您必须使用Adobe ID (IMS)连接到Campaign。 请参阅 [通过Adobe ID连接](../../integrations/using/about-adobe-id.md).

本文档介绍ACS连接器功能。 以下各节提供有关该功能如何复制数据的信息，以及有关如何使用已复制的配置文件的说明。

* [进程](#process)：ACS Connector概述以及如何管理数据复制。
* [实现](#implementation)：概述如何开始使用ACS Connector，以及如何复制基本数据和高级数据。
* [同步用户档案](../../integrations/using/synchronizing-profiles.md)：有关如何复制用户档案以及如何使用它们创建投放的说明。
* [同步受众](../../integrations/using/synchronizing-audiences.md)：有关如何在Campaign v7中定位收件人列表，然后将该列表作为受众复制到Campaign Standard的说明。
* [同步Web应用程序](../../integrations/using/synchronizing-web-applications.md)：有关如何将Campaign v7 Web应用程序链接到Campaign Standard的说明。
* [ACS连接器故障排除](../../integrations/using/troubleshooting-the-acs-connector.md)：查看常见问题的答案。

>[!NOTE]
>
>ACS Connector根据许可协议包含在Campaign v7中。 要使用ACS Connector，请确保可在Campaign v7和Campaign Standard之间切换。 如果您不确定您的版本及其包含的功能，请联系您的管理员。

## 印刷色 {#process}

### 数据复制 {#data-replication}

![](assets/acs_connect_flows_01.png)

ACS Connector会定期将以下项目从Campaign v7复制到Campaign Standard：

* **收件人**
* **订阅**
* **服务**
* **登陆页面**

默认情况下，ACS Connector的定期复制是每15分钟一次。 可以根据需要调整定期复制的跨度。 如果需要更改，请与您的顾问联系。

收件人、订阅、服务和登陆页面的数据复制是增量式的，这意味着只有新的收件人以及对现有收件人的修改才会从Campaign v7复制到Campaign Standard。 但是，受众的复制只发生在单个实例中。 您可以在Campaign v7中创建受众，然后将其复制一次以Campaign Standard。 复制是立即进行的，无法进行定期更新。 有关说明，请参阅 [同步受众](../../integrations/using/synchronizing-audiences.md).

>[!NOTE]
>
>请耐心等待大型数据库的初始复制，因为它可能需要几个小时。 但是，后续复制是增量式的，而且速度要快得多。

ACS Connector会定期将以下项目从Campaign Standard复制到Campaign v7：

* **[!UICONTROL Delivery IDs]**
* **[!UICONTROL Email broad logs]**
* **[!UICONTROL Email tracking logs]**

通过复制投放ID和电子邮件日志，可以从Campaign v7访问v7收件人的投放历史记录和跟踪数据。

>[!IMPORTANT]
>
>只有电子邮件broadlog和跟踪日志才会从Campaign Standard复制到Campaign v7。

### 数据同步 {#data-synchronization}

![](assets/acs_connect_flows_02.png)

ACS Connector在Campaign v7和Campaign Standard之间同步隔离。

例如，从Campaign v7复制到Campaign Standard的用户档案包括电子邮件地址。 如果Campaign Standard隔离了电子邮件地址，则数据将在下次同步期间传递到Campaign v7。 有关隔离的更多信息，请参阅 [隔离管理](../../delivery/using/understanding-quarantine-management.md) 和 [Campaign Standard隔离](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

### 使用已复制的用户档案 {#using-replicated-profiles}

Campaign Standard和Campaign v7可以使用复制的用户档案来定位营销活动中的工作流程。

有关如何使用复制的用户档案在Campaign Standard中发送投放的说明，请参阅 [同步用户档案](../../integrations/using/synchronizing-profiles.md). 提供了有关在Campaign v7和Campaign Standard之间共享退订数据的其他说明。

### 限制 {#limitations}

复制的用户档案可用于交付，但Campaign Standard存在某些限制。 请查看以下项目以了解如何最好地管理这些项目。

* **Campaign Standard的只读配置文件**：复制的用户档案Campaign Standard为只读。 但是，您可以在Campaign v7中编辑收件人，并且修改将由ACS Connector在Campaign Standard中自动更新。
* **在Campaign Standard中创建的配置文件**： ACS Connector会从一个方向复制收件人数据，从Campaign v7复制到Campaign Standard。 因此，源自Campaign Standard的用户档案不会复制到Campaign v7。
* **用于Campaign Standard的基本收件人数据**：ACS Connector会复制适用于Campaign Standard的收件人数据。 它包括收件人的姓名、地址、电子邮件地址、手机号码、家庭电话号码以及其他相关联系信息。 如果Campaign v7中可用的其他收件人字段和自定义定位表对您的工作流至关重要，请与您的顾问联系。
* **导入隔离的用户档案**：可以将不想被联系的用户档案列表作为隔离的用户档案导入到Campaign v7或Campaign Standard中。 配置文件的状态包含在应用程序之间的隔离同步中，并且不会在投放中使用。
* **取消订阅Campaign Standard中的服务**：取消订阅投放的选择不会从Campaign Standard同步到Campaign v7。 但是，您可以配置Campaign Standard交付，以将其退订链接定向到Campaign v7。 点击退订链接的收件人的配置文件将在Campaign v7中更新，并且数据会复制到Campaign Standard。 请参阅 [更改退订链接](../../integrations/using/synchronizing-profiles.md#changing-the-unsubscription-link).
* 只有电子邮件broadlog和跟踪日志才会从Campaign Standard复制到Campaign v7。

### 计费 {#billing}

您选择的发送投放应用程序、Campaign v7或Campaign Standard不影响计费。 计费信息在Campaign v7和Campaign Standard之间进行协调。 因此，如果您使用两个应用程序将投放内容发送给同一收件人，则仍会将其计为一个活动用户档案。

## 实施 {#implementation}

ACS连接器存在两种类型的实施。 这两项工作始终由Adobe Campaign咨询团队执行。

>[!IMPORTANT]
>
>本节仅供专家用户使用，以向他们提供实施流程及其主要步骤的全面视图。
>
>切勿尝试自行执行任何此类实施。 严格限定由Adobe Campaign顾问使用。

此 **基本实施** 用于复制收件人（现成字段）、服务和订阅、Web应用程序和受众。 这是从Campaign v7到Campaign Standard的单向复制。

此 **高级实施** 将允许您执行更复杂的用例，例如，如果您有额外的收件人字段或自定义收件人表（例如，事务表）。 请参阅 [高级实施](#advanced-implementation).

### 安装包 {#installing-the-package}

要使用该功能，请 **[!UICONTROL ACS Connector]** 需要安装软件包。 此操作始终由Adobe技术管理员或顾问执行。

所有与ACS Connector相关的技术元素均可在 **[!UICONTROL Administration > ACS Connector]** 资源管理器节点。

### 技术和复制工作流 {#technical-and-replication-workflows}

安装包后，下提供了两个技术工作流 **[!UICONTROL Administration > ACS Connector > Process]**.

>[!IMPORTANT]
>
>切勿尝试修改这些工作流。 它们绝不应该出错或暂停。 如果发生这种情况，请联系您的Adobe Campaign顾问。

![](assets/acs_connect_implementation_3.png)

* **[!UICONTROL `[ACS] Quarantine synchronization`]** (quarantineSync)：此工作流会同步所有隔离信息。 Campaign v7中的所有新隔离都会复制到Campaign Standard中。 Campaign Standard中的所有新隔离都会复制到Campaign v7。 这可确保所有排除规则在Campaign v7和Campaign Standard之间同步。
* **[!UICONTROL `[ACS] Security group synchronization`]** (securityGroupSync)：此工作流用于权限转换。 请参阅 [权限转换](#rights-conversion).

以下复制工作流可用作“准备使用”模板。 这些指标需要由您的Adobe Campaign顾问实施。

![](assets/acs_connect_implementation_2.png)

* **[!UICONTROL `[ACS] Profile replication`]** (newProfileReplication)：此增量工作流会将收件人复制到Campaign Standard。 默认情况下，它会复制所有现成的收件人字段。 请参阅 [默认收件人字段](#default-recipient-fields).
* **[!UICONTROL `[ACS] Service replication`]** (newServiceReplication)：此增量工作流会将所选服务复制到Campaign Standard。 请参阅用例 [同步Web应用程序](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] Landing pages replication`]** (newLandingPageReplication)：此增量工作流会将选定的Web应用程序复制到Campaign Standard。 Campaign v7 Web应用程序将显示为Campaign Standard中的登录页。 请参阅用例 [同步Web应用程序](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] New replication`]** (newReplication)：此增量工作流是用于复制自定义表的示例。 请参阅 [高级实施](#advanced-implementation).
* **[!UICONTROL `[ACS] Delivery-message replication`]** (newDlvMsgQualification)：此增量工作流可将投放消息从Campaign Standard复制到Campaign v7。
* **[!UICONTROL `[ACS] Profile delivery log replication`]** (newRcpDeliveryLogReplication)：此增量工作流可将投放ID、电子邮件概要日志和电子邮件跟踪日志从Campaign Standard复制到Campaign v7。 它只考虑从Campaign Standard发送到属于Campaign v7的nms：recipients表一部分的用户档案的投放。

  >[!NOTE]
  >
  > 如果使用Campaign Classic和Campaign Standard实例发送包含跟踪URL的电子邮件，则同步期间可能会出现与重复URL tagId有关的问题。 要防止这种情况发生，请更新 **更新跟踪URL** (writerTrackingUrls)活动，并将“ACS”前缀添加到@tagId源表达式中。

* **[!UICONTROL `[ACS] New delivery log replication`]** (newRcpDeliveryLogReplication)：此增量工作流可将投放ID、电子邮件概要日志和电子邮件跟踪日志从Campaign Standard复制到Campaign v7。 它只考虑从Campaign Standard发送到用户档案的投放，这些用户档案是Campaign v7的特定表（用于定义nms：recipients以外的表）的一部分。

### 默认收件人字段 {#default-recipient-fields}

如果您有任何其他字段或自定义表（例如，事务表），则默认不会复制它们。 需要执行高级配置。 请参阅 [高级实施](#advanced-implementation).

下面是随基本实施复制的收件人字段列表。 以下是现成的字段：

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 源 Id<br /> </td> 
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
   <td> @电子邮件<br /> </td> 
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
   <td> 致敬<br /> </td> 
   <td> @salutation<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再联系（通过任何渠道）<br /> </td> 
   <td> @blackList<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再电子邮件联系<br /> </td> 
   <td> @blackListEmail<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再通过短信联系<br /> </td> 
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
   <td> 地址 1（公寓）<br /> </td> 
   <td> [location/@address1]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址 2<br /> </td> 
   <td> [location/@address2]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址 3（号码和街道）<br /> </td> 
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
   <td> 省/市/自治区代码<br /> </td> 
   <td> [location/@stateCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> 国家/地区代码<br /> </td> 
   <td> [location/@countryCode]<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 权限转换 {#rights-conversion}

权限在Campaign v7和Campaign Standard中的处理方式不同。 在Campaign v7中，权限管理基于文件夹，而在Campaign Standard中则基于单位访问权限（组织/地理单位）。 Campaign Standard用户属于包含限制上下文的安全组。 因此，需要转换Campaign v7权限体系以匹配Campaign Standard的权限体系。 有多种方法可执行权限转换。 您将在下面找到实施的示例。

1. 下 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**，使用 **[!UICONTROL Synchronize]** 按钮以检索所有Campaign Standard安全组。 现成的Campaign Standard组被排除在外。

   ![](assets/acs_connect_implementation_4.png)

1. 如果您的权限管理是基于文件夹的，请转到 **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** 并将每个所需的文件夹映射到一个安全组。

   ![](assets/acs_connect_implementation_5.png)

1. 然后，复制工作流将使用此信息并将相应的组织/地理单位添加到要复制的每个对象。

### 高级实施 {#advanced-implementation}

本节介绍了一些高级实施方面的可能性。

>[!IMPORTANT]
>
>此信息只能用作一般准则。 请联系您的Adobe Campaign顾问来进行实施。

高级实施将根据客户的需求添加自定义复制工作流。 下面是一些示例：

* 投放复制
* Campaign复制
* 项目复制
* 种子成员复制
* 事务复制
* 等等。

**对收件人复制扩展字段**

通过基本实施，可以复制现成的收件人字段。 如果要复制添加到收件人模式的自定义字段，您需要标识它们。

1. 下 **[!UICONTROL Administration > ACS Connector > Data mapping]**，在上创建定位映射 **[!UICONTROL nms:recipient]** 表格。

   ![](assets/acs_connect_implementation_6.png)

1. 选择要复制的其他字段以及其他所需信息（索引、链接、标识键）。

   ![](assets/acs_connect_implementation_7.png)

1. 打开专用的配置文件复制工作流（不是模板，而是工作流实例本身）。 修改 **[!UICONTROL Query]** 和 **[!UICONTROL Update data]** 活动以包含这些字段。 请参阅 [技术和复制工作流](#technical-and-replication-workflows).

   ![](assets/acs_connect_implementation_8.png)

   ![](assets/acs_connect_implementation_9.png)

**复制自定义配置文件表**

通过基本实施，可以复制现成的收件人表。 如果您添加了自定义收件人表，则可通过以下方式识别他们。

1. 下 **[!UICONTROL Administration > ACS Connector > Data mapping]**，在自定义用户档案表上创建定位映射。

   ![](assets/acs_connect_implementation_10.png)

1. 定义要复制的标识数据、索引、链接和字段。

   ![](assets/acs_connect_implementation_10.png)

1. 如果您的权限管理是基于文件夹的，请转到 **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]**，并为链接到自定义表的文件夹定义安全组。 请参阅 [权限转换](#rights-conversion).
1. 使用 **[!UICONTROL New replication]** 工作流（不是模板，而是工作流实例本身）来包含自定义表和要复制的字段。 请参阅 [技术和复制工作流](#technical-and-replication-workflows).
