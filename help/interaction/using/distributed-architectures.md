---
title: 分布式架构
seo-title: 分布式架构
description: 分布式架构
seo-description: null
page-status-flag: never-activated
uuid: f672446f-18e6-4fff-81a1-01ee22792755
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 811a42a4-552c-49cb-bffd-7e124ef83735
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# 分布式架构{#distributed-architectures}

## 原则 {#principle}

为了能够支持可伸缩性并在入站渠道上提供24/7服务，您可以使用与分布式架构的交互。 此类架构已与消息中心一起使用，由多个实例组成：

* 专用于出站渠道并包含营销和环境设计基础的一个或多个控制实例
* 专用于入站渠道的一个或多个执行实例

![](assets/interaction_powerbooster_schema.png)

>[!NOTE]
>
>控制实例专用于入站渠道并包含目录的联机版本。 每个执行实例都是独立的，并专用于一个联系人区段（例如，每个国家／地区一个执行实例）。 必须在执行时直接执行选件引擎调用（每个执行实例一个特定URL）。 由于实例之间的同步不是自动的，因此必须通过同一实例发送来自同一联系人的交互。

## 命题同步 {#proposition-synchronization}

选件同步是通过包实现的。 在执行实例中，所有目录对象都以外部帐户名为前缀。 这意味着可以在一个同一执行实例上支持多个控制实例（例如开发和生产实例）。

>[!CAUTION]
>
>我们建议您使用简明的内部名称。

选件会自动部署，然后在执行和控制实例时发布。

在设计环境中删除的选件在所有联机实例上都处于禁用状态。 在清除期（在每个实例的部署助手中指定）和滑动期（在传入命题的排版规则中指定）之后，将在所有实例上自动删除废弃的命题和选件。

![](assets/interaction_powerbooster_schema2.png)

为每个环境和外部帐户创建一个工作流，以便进行命题同步。 可以针对每个环境和外部帐户调整同步频率。

## 限制 {#limitations}

* 如果您使用从匿名环境到已识别环境的回退功能，这两个环境必须位于同一执行实例上。
* 多个执行实例之间的同步不会实时执行。 必须将同一联系人的交互发送到同一实例。 控制实例必须专用于出站渠道（无实时）。
* 营销数据库不会自动同步。 权重和资格规则中使用的营销数据必须在执行实例上重复。 此过程不是标准的，您必须在集成期间开发它。
* 命题同步只由FDA连接执行。
* 如果在同一实例上使用交互和消息中心，则两种情况下都将通过FDA协议进行同步。

## 包配置 {#packages-configuration}

直接链接到交互的任 **何架构扩展** （选件、建议、收件人等）必须部署在执行实例上。

交互包必须安装在所有实例上（控制和执行）。 还提供两个附加包：一个要安装在控件实例上的包，另一个要安装在每个执行实例上。

>[!NOTE]
>
>安装包时， **nms:postition** 表的长类型字段（如命名ID）将变为 **int64****** 类型字段。 此部分详细介绍了此类 [数据](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data)。

必须在每个实例上配置数据保留持续时间(通过部 **[!UICONTROL Data purge]** 署向导中的窗口)。 在执行实例中，此期间必须与要计算的排版规则（滑动期间）和资格规则所需的历史深度相对应。

在控件实例上：

1. 按执行实例创建外部帐户：

   ![](assets/interaction_powerbooster1.png)

   * 填写标签并添加一个简短且明确的内部名称。
   * 选择 **[!UICONTROL Execution instance]**。
   * 选中该 **[!UICONTROL Enabled]** 选项。
   * 完成执行实例的连接参数。
   * 每个执行实例都必须链接到一个ID。 单击该按钮时，将分配此ID。 **[!UICONTROL Initialize connection]**
   * 检查所使用的应用程序类型： **[!UICONTROL Message Center]**&#x200B;或 **[!UICONTROL Interaction]**&#x200B;两者。
   * 输入使用的FDA帐户。 必须在执行实例上创建运算符，并且必须对相关实例的数据库具有以下读写权限：

      ```
      grant SELECT ON nmspropositionrcp, nmsoffer, nmsofferspace, xtkoption, xtkfolder TO user;
      grant DELETE, INSERT, UPDATE ON nmspropositionrcp TO user;
      ```
   >[!NOTE]
   >
   >必须对执行实例授权控制实例的IP地址。

1. 配置环境：

   ![](assets/interaction_powerbooster2.png)

   * 添加执行实例列表。
   * 对于每个同步周期，指定同步周期和筛选条件（例如，按国家／地区）。

      >[!NOTE]
      >
      >如果遇到错误，您可以参考同步工作流和选件通知。 可以在应用程序的技术工作流程中找到这些功能。

由于优化原因，如果执行实例上仅复制部分营销数据库，则可指定链接到该环境的受限架构，以允许用户仅使用执行实例上可用的数据。 您可以使用执行实例中不可用的数据创建选件。 为此，您必须通过限制出站渠道（字段）上的此规则来取消激活其他渠道&#x200B;**[!UICONTROL Taken into account if]** 上的规则。

![](assets/ita_filtering.png)

## 维护选项 {#maintenance-options}

以下是控件实例上可用的维护选项列表：

>[!CAUTION]
>
>这些选项只能用于特定的维护案例。

* **`NmsInteraction_LastOfferEnvSynch_<offerEnvId>_<executionInstanceId>`**:环境在给定实例上同步的上次日期。
* **`NmsInteraction_LastPropositionSynch_<propositionSchema>_<executionInstanceIdSource>_<executionInstanceIdTarget>`**:给定架构中的命题从一个实例同步到另一个实例的上次日期。
* **`NmsInteraction_MapWorkflowId`**:一个选项，其中包含生成的所有同步工作流的列表。

执行实例中提供以下选项：

**NmsExecutionInstanceId**:选项。

## 包安装 {#packages-installation}

如果您的实例之前没有交互包，则无需迁移。 默认情况下，命题表将在安装软件包后以64位为单位。

>[!CAUTION]
>
>根据实例中现有命题的数量，此操作可能需要一段时间。

* 如果您的实例很少或没有命题，则无需手动修改命题表。 在安装包时，将进行修改。
* 如果实例有许多命题，则最好在安装控制包并运行它们之前更改命题表的结构。 我们建议在低活动期间运行查询。

>[!NOTE]
>
>如果您已经在命题表中执行了特定配置，请相应地调整查询。

### PostgreSQL {#postgresql}

有两种方法。 第一个（使用工作表）稍快一些。

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

编辑 **Number** 类型的大小不会导致值或索引被重写。 因此，它是立竿见影的。

要执行的查询如下：

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

