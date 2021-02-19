---
solution: Campaign Classic
product: campaign
title: 分布式架构
description: 分布式架构
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 1%

---


# 分布式架构{#distributed-architectures}

## 原则{#principle}

为了能够支持可伸缩性并在入站渠道上提供24/7服务，您可以与分布式架构一起使用交互。 此类型的架构已与消息中心一起使用，由多个实例组成：

* 一个或多个控制实例专门用于出站渠道，并包含营销和环境设计基础
* 专用于入站执行实例的一个或多个渠道

![](assets/interaction_powerbooster_schema.png)

>[!NOTE]
>
>控制实例专用于入站渠道并包含目录的联机版本。 每个执行实例都是独立的，专门用于一个联系人细分(例如，每个国家/地区一个执行实例)。 优惠引擎调用必须在执行时直接执行(每个执行实例一个特定URL)。 由于实例之间的同步不是自动的，因此必须通过同一实例发送来自同一联系人的交互。

## 命题同步{#proposition-synchronization}

优惠同步是通过包实现的。 在执行实例上，所有目录对象都以外部帐户名称为前缀。 这意味着可以在同一个控制实例上支持多个执行实例（例如开发和生产实例）。

>[!IMPORTANT]
>
>我们建议您使用简明的内部名称。

优惠会自动部署，然后在执行和控制实例时发布。

在设计环境中删除的优惠在所有联机实例上都处于禁用状态。 在清除期（在每个实例的部署助手中指定）和滑动期(在传入命题的类型规则中指定)之后，将在所有实例上自动删除过时的命题和优惠。

![](assets/interaction_powerbooster_schema2.png)

将为每个环境和外部帐户创建一个工作流，以便进行命题同步。 可以针对每个环境和外部帐户调整同步频率。

## 限制{#limitations}

* 如果您使用从匿名环境到已识别环境的回退函数，则这两个环境必须位于同一执行实例。
* 多个执行实例之间的同步不会实时执行。 必须将同一联系人的交互发送给同一实例。 控制实例必须专用于出站渠道（无实时）。
* 营销数据库未自动同步。 权重和合格规则中使用的营销数据必须在执行实例上重复。 此过程不是标准的，您必须在集成期间进行开发。
* 命题同步只通过联合数据访问连接执行。
* 如果在同一实例上使用交互和消息中心，则两种情况下都将通过联合数据访问协议进行同步。

## 程序包配置{#packages-configuration}

直接链接到&#x200B;**Interaction**&#x200B;的任何模式扩展(优惠、陈述、收件人等) 必须部署在执行实例上。

必须在所有实例（控制和执行）上安装Interaction包。 还提供两个额外的包：一个包要安装在控制实例上，另一个包要安装在每个执行实例上。

>[!NOTE]
>
>安装包时，**nms:pomposition**&#x200B;表的&#x200B;**long**&#x200B;类型字段（如命题ID）将变为&#x200B;**int64**&#x200B;类型字段。 [本节](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data)中详细介绍了此类数据。

必须在每个实例上配置数据保留持续时间（通过部署向导中的&#x200B;**[!UICONTROL Data purge]**&#x200B;窗口）。 在执行实例上，此时段必须与要计算类型规则（滑动时段）和合格规则所需的历史深度相对应。

在控制实例上：

1. 按外部帐户创建执行实例:

   ![](assets/interaction_powerbooster1.png)

   * 填写标签并添加一个简短且明确的内部名称。
   * 选择 **[!UICONTROL Execution instance]**。
   * 勾选 **[!UICONTROL Enabled]** 选项。
   * 完成执行实例的连接参数。
   * 每个执行实例都必须链接到ID。 单击&#x200B;**[!UICONTROL Initialize connection]**&#x200B;按钮时，将分配此ID。
   * 检查所使用的应用程序类型：**[!UICONTROL Message Center]**、**[!UICONTROL Interaction]**&#x200B;或两者。
   * 输入所用的联合数据访问帐户。 必须在执行实例上创建运算符，并且必须对有关实例的数据库具有以下读写权限：

      ```
      grant SELECT ON nmspropositionrcp, nmsoffer, nmsofferspace, xtkoption, xtkfolder TO user;
      grant DELETE, INSERT, UPDATE ON nmspropositionrcp TO user;
      ```
   >[!NOTE]
   >
   >控制实例的IP地址必须在执行实例上授权。

1. 配置环境:

   ![](assets/interaction_powerbooster2.png)

   * 添加列表执行实例。
   * 对于每个同步周期，指定同步周期和筛选条件（例如，按国家/地区）。

      >[!NOTE]
      >
      >如果遇到错误，可以查阅同步工作流和优惠通知。 这些内容可在应用程序的技术工作流中找到。

由于优化原因，如果仅部分营销模式库在执行实例上重复，则可以指定链接到环境的受限执行实例，以允许用户仅使用上可用的数据。 您可以使用优惠中不可用的数据创建执行实例。 要执行此操作，您必须通过限制出站渠道（**[!UICONTROL Taken into account if]**&#x200B;字段）上的此规则来取消激活其他渠道上的规则。

![](assets/ita_filtering.png)

## 维护选项{#maintenance-options}

以下是该控制实例提供的维护选项列表:

>[!IMPORTANT]
>
>这些选项只能用于特定的维护案例。

* **`NmsInteraction_LastOfferEnvSynch_<offerEnvId>_<executionInstanceId>`**:环境在给定实例上同步的上次日期。
* **`NmsInteraction_LastPropositionSynch_<propositionSchema>_<executionInstanceIdSource>_<executionInstanceIdTarget>`**:给定模式中的建议从一个实例同步到另一个实例的最后日期。
* **`NmsInteraction_MapWorkflowId`**:一个选项，包含所有生成的同步工作流的列表。

以下选项适用于执行实例:

**NmsExecutionInstanceId**:选项。

## 程序包安装{#packages-installation}

如果您的实例之前没有Interaction包，则无需迁移。 默认情况下，命题表将在安装软件包后以64位为单位。

>[!IMPORTANT]
>
>根据实例中现有命题的数量，此操作可能需要一段时间。

* 如果您的实例很少或没有建议，则无需手动修改建议表。 安装包后将进行修改。
* 如果您的实例有许多建议，则最好在安装控制包并运行它们之前更改建议表的结构。 我们建议在低活动期内运行查询。

>[!NOTE]
>
>如果您已在提议表中执行了特定配置，请相应地调整查询。

### PostgreSQL {#postgresql}

有两种方法。 第一个（使用工作表）稍快。

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

编辑&#x200B;**Number**&#x200B;类型的大小不会导致值或索引被重写。 因此，它是立竿见影的。

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

