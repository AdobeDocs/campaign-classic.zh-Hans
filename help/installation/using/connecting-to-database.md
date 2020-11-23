---
solution: Campaign Classic
product: campaign
title: 访问外部数据库
description: 了解如何连接到外部数据库
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---


# 连接到数据库 {#connecting-to-the-database}

要启用与外部数据库的连接，必须指示连接参数，即目标数据源和需要加载数据的表的名称。

>[!CAUTION]
>
>Adobe Campaign用户需要外部Adobe Campaign库和应用程序服务器的特定权限才能处理来自外部数据库的数据。 有关此内容的详细信息，请参 [阅远程数据库访问权限](../../installation/using/remote-database-access-rights.md) 部分。
>
>要避免任何故障，访问远程共享数据的操作员必须从不同的空间工作。

## 创建共享连接 {#creating-a-shared-connection}

要启用与共享外部数据库的连接，只要此连接处于活动状态，就可以通过Adobe Campaign访问数据库。

1. 配置必须事先通过节点进 **[!UICONTROL Administration > Platform > External accounts]** 行定义。
1. 单击按 **[!UICONTROL New]** 钮并选择 **[!UICONTROL External database]** 类型。
1. 定义外 **[!UICONTROL Connection]** 部数据库的参数。

   对于与ODBC类 **型** 数据库的连 **[!UICONTROL Server]** 接，字段必须包含ODBC数据源的名称，而不是服务器名称。 此外，可能需要某些附加配置，具体取决于所使用的数据库。 请参阅按数 [据库类型列出的特定配置](../../installation/using/configure-fda.md) 。

1. 输入参数后，单击按钮 **[!UICONTROL Test the connection]** 进行批准。

   ![](assets/wf-external-account-create.png)

1. 如有必要，请取消选 **[!UICONTROL Enabled]** 中此选项，以禁用对此数据库的访问，而不删除其配置。
1. 要允许Adobe Campaign访问此数据库，必须部署SQL函数。 单击选 **[!UICONTROL Parameters]** 项卡，然后单 **[!UICONTROL Deploy functions]** 击按钮。

   ![](assets/wf-external-account-functions.png)

您可以在选项卡中为表和索引定义特定工作表 **[!UICONTROL Parameters]** 空间。

## 创建临时连接 {#creating-a-temporary-connection}

您可以直接从工作流活动定义到外部数据库的连接。 在这种情况下，它将位于本地外部数据库上，保留用于当前工作流：它不会保存在外部帐户上。 此类型的准时连接可以在工作流的不同活动上创建， **[!UICONTROL Query]**&#x200B;尤其是 **[!UICONTROL Data loading (RDBMS)]**、、 **[!UICONTROL Enrichment]** 活动或 **[!UICONTROL Split]** 活动。

>[!CAUTION]
>
>不建议使用此类型的配置，但可定期用于收集数据。 但是，您应创建外部帐户，如创建共 [享连接部分所示](#creating-a-shared-connection) 。

例如，在查询活动中，创建与外部数据库的定期连接的步骤如下：

1. 单击 **[!UICONTROL Add data...]** 并选择 **[!UICONTROL External data]** 选项。
1. 选择选 **[!UICONTROL Locally defining the data source]** 项。

   ![](assets/wf_add_data_local_external_data.png)

1. 在下拉目标卡中选择列表库引擎。 输入服务器的名称并提供身份验证参数。

   还指定外部数据库的名称。

   ![](assets/wf_add_data_local_external_data_param.png)

   单击 **[!UICONTROL Next]** 按钮。

1. 选择存储数据的表。

   您可以直接在相应字段中输入表的名称，或单击编辑图标以访问列表库表。

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. 单击按 **[!UICONTROL Add]** 钮可定义外部数据库数据与Adobe Campaign库中数据之间的一个或多个对帐字段。 和 **[!UICONTROL Edit expression]** 的图 **[!UICONTROL Remote field]** 标 **[!UICONTROL Local field]** 允许您访问每个表的字段列表。

   ![](assets/wf_add_data_local_external_data_join.png)

1. 如有必要，请指定过滤条件和数据排序模式。
1. 选择要在外部数据库中收集的其他数据。 为此，多次单击要添加的字段，以在中显示这些字段 **[!UICONTROL Output columns]**。

   ![](assets/wf_add_data_local_external_data_select.png)

   单击 **[!UICONTROL Finish]** 以确认此配置。

## 安全连接 {#secure-connection}

>[!NOTE]
>
>安全连接仅对PostgreSQL可用。

在配置外部联合数据访问帐户时，可以保护对外部数据库的访问。

为此，请在使用的端&#x200B;**口的服务器**&#x200B;地址和地址后添加“:ssl”。 例如： **192.168.0.52:4501:ssl**。

数据随后将通过安全SSL协议发送。

## 其他配置 {#additional-configurations}

如有必要，您可以创建用于处理外部模式库中数据的。 同样，Adobe Campaign允许您定义外部表中数据的映射。 这些配置是常规配置，不仅适用于工作流。

>[!NOTE]
>
>有关在Adobe Campaign中创建模式和定义新数据映射的详细信息，请 [参阅此页](../../configuration/using/about-schema-edition.md)。