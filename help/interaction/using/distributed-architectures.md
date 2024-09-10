---
product: campaign
title: 分布式架构
description: 分布式架构
feature: Interaction, Offers, Architecture
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 083be073-aad4-4c81-aff2-77f5ef3e80db
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1014'
ht-degree: 1%

---

# 分布式架构{#distributed-architectures}



## 原则 {#principle}

为了能够支持可扩展性并在入站渠道上提供全天候服务，您可以使用与分布式架构的交互。 此类型的架构已与Message Center一起使用，并且由多个实例组成：

* 一个或多个专用于出站渠道并包含营销和环境设计基础的控制实例
* 专用于入站渠道的一个或多个执行实例

![](assets/interaction_powerbooster_schema.png)

>[!NOTE]
>
>控制实例专用于集客渠道，并包含目录的在线版本。 每个执行实例都是独立的，并且专用于一个联系区段（例如，每个国家/地区一个执行实例）。 必须直接在执行上执行优惠引擎调用（每个执行实例一个特定URL）。 由于实例之间的同步不是自动的，来自同一联系人的交互必须通过同一实例发送。

## 建议同步 {#proposition-synchronization}

通过包执行选件同步。 在执行实例上，所有目录对象都使用外部帐户名称作为前缀。 这意味着可以在一个执行实例上支持多个控制实例（例如开发和生产实例）。

>[!IMPORTANT]
>
>我们建议您使用简短的显式内部名称。

选件会自动部署，然后在执行和控制实例上发布。

在所有联机实例上，将禁用在设计环境中删除的选件。 在清除时段（在每个实例的部署向导中指定）和滑动时段（在传入命题的类型规则中指定）之后，将自动删除所有实例上过时的命题和选件。

![](assets/interaction_powerbooster_schema2.png)

将为每个环境和外部帐户创建工作流，以进行建议同步。 可以为每个环境和外部帐户调整同步频率。

## 限制 {#limitations}

* 如果您使用从匿名环境到已识别环境的回退函数，则这两个环境必须位于同一执行实例上。
* 多个执行实例之间的同步不会实时执行。 同一联系人的交互必须发送到同一实例。 控制实例必须专用于出站渠道（非实时）。
* 营销数据库不会自动同步。 在执行实例上，必须在权重和资格规则中使用的营销数据重复。 此过程不符合标准，您必须在集成期间对其进行开发。
* 建议同步仅通过FDA连接执行。
* 如果您在同一实例上使用交互和消息中心，则在这两种情况下都将通过FDA协议进行同步。

## 包配置 {#packages-configuration}

直接链接到&#x200B;**交互**&#x200B;的任何架构扩展（优惠、建议、收件人等） 必须在执行实例上部署。

必须在所有实例（控制和执行）上安装交互包。 另外提供了两个软件包：一个软件包将安装在控制实例上，另一个软件包将安装在每个执行实例上。

>[!NOTE]
>
>在安装包时，**nms：proposition**&#x200B;表的&#x200B;**long**&#x200B;类型字段（如建议ID）将变为&#x200B;**int64**&#x200B;类型字段。 此类型的数据在[此部分](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data)中有详细说明。

必须在每个实例上配置数据保留持续时间（通过部署向导中的&#x200B;**[!UICONTROL Data purge]**&#x200B;窗口）。 在执行实例上，此期间必须对应于要计算的分类规则（滑动期间）和资格规则所需的历史深度。

在控制实例上：

1. 按执行实例创建外部帐户：

   ![](assets/interaction_powerbooster1.png)

   * 填写标签并添加一个简短且明确的内部名称。
   * 选择 **[!UICONTROL Execution instance]**。
   * 勾选 **[!UICONTROL Enabled]** 选项。
   * 完成执行实例的连接参数。
   * 每个执行实例都必须链接到一个ID。 此ID是在您单击&#x200B;**[!UICONTROL Initialize connection]**&#x200B;按钮时分配的。
   * 检查使用的应用程序类型： **[!UICONTROL Message Center]**、**[!UICONTROL Interaction]**&#x200B;或两者。
   * 输入使用的FDA帐户。 必须在执行实例上创建运算符，并且必须对相关实例的数据库具有以下读写权限：

     ```
     grant SELECT ON nmspropositionrcp, nmsoffer, nmsofferspace, xtkoption, xtkfolder TO user;
     grant DELETE, INSERT, UPDATE ON nmspropositionrcp TO user;
     ```

   >[!NOTE]
   >
   >必须在执行实例上授权控制实例的IP地址。

1. 配置环境：

   ![](assets/interaction_powerbooster2.png)

   * 添加执行实例列表。
   * 对于每个事件，指定同步周期和过滤条件（例如，按国家/地区）。

     >[!NOTE]
     >
     >如果遇到错误，您可以查阅同步工作流和选件通知。 您可以在应用程序的技术工作流中找到这些内容。

如果出于优化原因，在执行实例上仅复制部分营销数据库，则可以指定链接到环境的受限架构，以允许用户仅使用执行实例上可用的数据。 您可以使用执行实例上不可用的数据创建选件。 为此，您必须通过在出站频道（**[!UICONTROL Taken into account if]**&#x200B;字段）上限制此规则，在其他频道上取消激活该规则。

![](assets/ita_filtering.png)

## 维护选项 {#maintenance-options}

以下是控制实例上可用的维护选项列表：

>[!IMPORTANT]
>
>这些选项只能用于特定的维护案例。

* **`NmsInteraction_LastOfferEnvSynch_<offerEnvId>_<executionInstanceId>`**：在给定实例上同步环境的上次日期。
* **`NmsInteraction_LastPropositionSynch_<propositionSchema>_<executionInstanceIdSource>_<executionInstanceIdTarget>`**：给定架构中的建议从一个实例同步到另一个实例的上次日期。
* **`NmsInteraction_MapWorkflowId`**：包含生成的所有同步工作流的列表的选项。

以下选项在执行实例上可用：

**NmsExecutionInstanceId**：选项包含实例ID。

## 软件包安装 {#packages-installation}

如果您的实例之前没有交互包，则无需迁移。 默认情况下，安装包后，建议表将为64位。

>[!IMPORTANT]
>
>根据实例中现有建议的数量，此操作可能需要花费一些时间。

* 如果您的实例只有少量建议或没有建议，则无需手动修改建议表。 修改将在安装包时完成。
* 如果您的实例有很多建议，则最好在安装控制包并运行它们之前更改建议表的结构。 我们建议在低活动期间运行查询。

>[!NOTE]
>
>如果您在建议表中执行了特定配置，请相应地调整查询。

### PostgreSQL {#postgresql}

有两种方法。 第一个（使用工作表）的速度稍快。

**工作表**

```
CREATE TABLE NmsPropositionRcp_tmp AS SELECT * FROM nmspropositionrcp WHERE 0=1;
ALTER TABLE nmspropositionrcp_tmp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
INSERT INTO nmspropositionrcp_tmp SELECT * FROM nmspropositionrcp;
DROP TABLE nmspropositionrcp;
CREATE INDEX proposition_id ON NmsPropositionRcp (ipropositionid);
CREATE INDEX nmspropositionrcp_deliveryid ON NmsPropositionRcp (ideliveryid);
CREATE INDEX nmspropositionrcp_lastmodified ON NmsPropositionRcp (tslastmodified);
CREATE INDEX nmspropositionrcp_offerid ON NmsPropositionRcp (iofferid);
CREATE INDEX nmspropositionrcp_offerspaceid ON NmsPropositionRcp (iofferspaceid);
CREATE INDEX nmspropositionrcp_recipientidid ON NmsPropositionRcp (irecipientid);
ALTER TABLE nmspropositionrcp_tmp RENAME TO nmspropositionrcp;
```

**更改表**

```
ALTER TABLE nmspropositionrcp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
```

### Oracle {#oracle}

编辑&#x200B;**Number**&#x200B;类型的大小不会导致值或索引被重写。 因此，这是当务之急。

要执行的查询如下所示：

```
ALTER TABLE nmspropositionrcp MODIFY (
ipropositionid NUMBER(19, 0),
iinteractionid NUMBER(19, 0)
);
```

### MSSQL {#mssql}

要执行的查询如下：

```
SELECT * INTO NmsPropositionRcp_tmp FROM NmsPropositionRcp WHERE 1 = 0;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN ipropositionid BIGINT;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN iinteractionid BIGINT;
GO
INSERT INTO NmsPropositionRcp_tmp SELECT * FROM NmsPropositionRcp;
GO
DROP TABLE NmsPropositionRcp;
GO
sp_rename 'NmsPropositionRcp_tmp', NmsPropositionRcp
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR dWeight
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iDeliveryId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iEngineType
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iInteractionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferSpaceId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iPropositionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRank
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRecipientId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iStatus
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_deliveryId ON NmsPropositionRcp (iDeliveryId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_eventDate ON NmsPropositionRcp (tsEvent)
GO
CREATE UNIQUE NONCLUSTERED INDEX NmsPropositionRcp_id ON NmsPropositionRcp (iPropositionId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_lastModified ON NmsPropositionRcp (tsLastModified)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerId ON NmsPropositionRcp (iOfferId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerSpaceI ON NmsPropositionRcp (iOfferSpaceId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_recipientId ON NmsPropositionRcp (iRecipientId)
GO
```
