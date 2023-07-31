---
product: campaign
title: 连接到外部数据库
description: 了解如何连接到外部数据库
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 240d7e11-da3a-4d64-8986-1f1c8ebcea3c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 2%

---

# 连接到数据库 {#connecting-to-the-database}



要启用与外部数据库的连接，必须指示连接参数，即目标数据源和包含需要加载的数据的表的名称。

>[!CAUTION]
>
>Adobe Campaign用户需要外部数据库和Adobe Campaign应用程序服务器的特定权限，才能处理来自外部数据库的数据。 有关详细信息，请参见 [远程数据库访问权限](../../installation/using/remote-database-access-rights.md) 部分。
>
>为避免发生任何故障，访问远程共享数据的操作员必须在不同的空间工作。

## 创建共享连接 {#creating-a-shared-connection}

要启用到共享外部数据库的连接，只要此连接处于活动状态，就可以通过Adobe Campaign访问该数据库。

1. 配置必须预先通过 **[!UICONTROL Administration > Platform > External accounts]** 节点。
1. 单击 **[!UICONTROL New]** 按钮并选择 **[!UICONTROL External database]** 类型。
1. 定义 **[!UICONTROL Connection]** 外部数据库的参数。

   对于与的连接 **ODBC** 键入数据库 **[!UICONTROL Server]** 字段必须包含ODBC数据源的名称，而不是服务器名称。 此外，根据所使用的数据库，可能还需要某些其他配置。 请参阅 [按数据库类型列出的特定配置](../../installation/using/configure-fda.md) 部分。

1. 输入参数后，单击 **[!UICONTROL Test the connection]** 按钮以批准它们。

   ![](assets/wf-external-account-create.png)

1. 如有必要，请取消选中 **[!UICONTROL Enabled]** 选项禁用对此数据库的访问而不删除其配置。
1. 要允许Adobe Campaign访问此数据库，您必须部署SQL函数。 单击 **[!UICONTROL Parameters]** 选项卡，然后 **[!UICONTROL Deploy functions]** 按钮。

   ![](assets/wf-external-account-functions.png)

您可以在中为表和索引定义特定的工作表空间 **[!UICONTROL Parameters]** 选项卡。

## 创建临时连接 {#creating-a-temporary-connection}

可以从工作流活动直接定义与外部数据库的连接。 在这种情况下，它将被保存在本地外部数据库中，保留供当前工作流使用：它不会保存在外部帐户上。 这种类型的准时连接可以在工作流的不同活动上创建，特别是 **[!UICONTROL Query]**， **[!UICONTROL Data loading (RDBMS)]**， **[!UICONTROL Enrichment]** 活动或 **[!UICONTROL Split]** 活动。

>[!CAUTION]
>
>不建议使用此类型的配置，但可以定期使用它来收集数据。 但是，您应该创建一个外部帐户，如 [创建共享连接](#creating-a-shared-connection) 部分。

例如，在查询活动中，创建与外部数据库的定期连接的步骤如下所示：

1. 单击 **[!UICONTROL Add data...]** 并选择 **[!UICONTROL External data]** 选项。
1. 选择 **[!UICONTROL Locally defining the data source]** 选项。

   ![](assets/wf_add_data_local_external_data.png)

1. 在下拉列表中选择目标数据库引擎。 输入服务器的名称并提供身份验证参数。

   同时指定外部数据库的名称。

   ![](assets/wf_add_data_local_external_data_param.png)

   单击 **[!UICONTROL Next]** 按钮。

1. 选择存储数据的表。

   您可以直接在相应的字段中输入表的名称，也可以单击编辑图标来访问数据库表的列表。

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. 单击 **[!UICONTROL Add]** 按钮来定义外部数据库数据与Adobe Campaign数据库中的数据之间的一个或多个协调字段。 此 **[!UICONTROL Edit expression]** 的图标 **[!UICONTROL Remote field]** 和 **[!UICONTROL Local field]** 允许您访问每个表的字段列表。

   ![](assets/wf_add_data_local_external_data_join.png)

1. 如有必要，请指定筛选条件和数据排序模式。
1. 选择要在外部数据库中收集的其他数据。 要实现此目的，请双击要添加的字段，以在 **[!UICONTROL Output columns]**.

   ![](assets/wf_add_data_local_external_data_select.png)

   单击 **[!UICONTROL Finish]** 以确认此配置。

## 安全连接 {#secure-connection}

>[!NOTE]
>
>安全连接仅适用于PostgreSQL。

配置外部FDA帐户时，您可以保护对外部数据库的访问。

为此，请添加&quot;**：ssl**&#x200B;在服务器地址和使用的端口地址之后的&#39;&#39;。 例如： **192.168.0.52:4501:ssl**.

然后，将通过安全SSL协议发送数据。

## 其他配置 {#additional-configurations}

如有必要，您可以创建用于在外部数据库中处理数据的模式。 同样，您可以使用Adobe Campaign定义外部表中数据的映射。 这些配置是常规配置，不适用于专门的工作流。

>[!NOTE]
>
>有关在Adobe Campaign中创建架构和定义新数据映射的更多信息，请参阅 [此页面](../../configuration/using/about-schema-edition.md).
