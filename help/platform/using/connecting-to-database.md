---
title: 访问外部数据库
seo-title: 访问外部数据库
description: 访问外部数据库
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4969c5e56f1911b3abfd770ca4f8f5ed25784a52

---


# 连接到数据库 {#connecting-to-the-database}

要启用与外部数据库的连接，必须指示连接参数，即目标数据源和需要加载数据的表的名称。

>[!CAUTION]
>
>Adobe Campaign用户需要外部数据库和Adobe Campaign应用程序服务器的特定权限才能处理来自外部数据库的数据。 有关详细信息，请参阅远程数 [据库访问权限部分](#remote-database-access-rights) 。
>
>要避免任何故障，访问远程共享数据的操作员必须从不同的空间工作。

## 创建共享连接 {#creating-a-shared-connection}

要启用与共享外部数据库的连接，只要此连接处于活动状态，就可以通过Adobe Campaign访问该数据库。

1. 配置必须通过节点预先定 **[!UICONTROL Administration > Platform > External accounts]** 义。
1. 单击按 **[!UICONTROL New]** 钮并选择类 **[!UICONTROL External database]** 型。
1. 定义外 **[!UICONTROL Connection]** 部数据库的参数。

   对于与 **ODBC** **[!UICONTROL Server]** type数据库的连接，字段必须包含ODBC数据源的名称，而不包含服务器名称。 此外，可能需要某些附加配置，具体取决于所使用的数据库。 请参阅“按数 [据库类型的特定配置](#specific-configurations-by-database-type) ”部分。

1. 输入参数后，单击按钮 **[!UICONTROL Test the connection]** 以批准这些参数。

   ![](assets/wf-external-account-create.png)

1. 如有必要，请取消选 **[!UICONTROL Enabled]** 中此选项，以禁用对此数据库的访问，而不删除其配置。
1. 要允许Adobe Campaign访问此数据库，必须部署SQL函数。 单击选 **[!UICONTROL Parameters]** 项卡，然后单击 **[!UICONTROL Deploy functions]** 按钮。

   ![](assets/wf-external-account-functions.png)

您可以在选项卡中为表和索引定义特定的工作表空间 **[!UICONTROL Parameters]** 空间。

## 创建临时连接 {#creating-a-temporary-connection}

您可以从工作流活动直接定义到外部数据库的连接。 在这种情况下，它将位于本地外部数据库上，保留该数据库以用于当前工作流：它不会保存在外部帐户中。 可以在工作流的不同活动（尤其是、活动或活动）上创 **[!UICONTROL Query]**&#x200B;建此类 **[!UICONTROL Data loading (RDBMS)]**&#x200B;型的 **[!UICONTROL Enrichment]** 准时连接 **[!UICONTROL Split]** 。

>[!CAUTION]
>
>不建议使用此类配置，但可定期用于收集数据。 但是，您应创建外部帐户，如创建共 [享连接部分中所示](#creating-a-shared-connection) 。

例如，在查询活动中，创建到外部数据库的定期连接的步骤如下：

1. 单击该 **[!UICONTROL Add data...]** 选项，然后选 **[!UICONTROL External data]** 择选项。
1. 选择选 **[!UICONTROL Locally defining the data source]** 项。

   ![](assets/wf_add_data_local_external_data.png)

1. 在下拉列表中选择目标数据库引擎。 输入服务器的名称并提供身份验证参数。

   还指定外部数据库的名称。

   ![](assets/wf_add_data_local_external_data_param.png)

   Click the **[!UICONTROL Next]** button.

1. 选择存储数据的表。

   您可以直接在相应的字段中输入表的名称，或单击编辑图标以访问数据库表的列表。

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. 单击按 **[!UICONTROL Add]** 钮可定义外部数据库数据与Adobe Campaign数据库中数据之间的一个或多个对帐字段。 和 **[!UICONTROL Edit expression]** 的图 **[!UICONTROL Remote field]** 标 **[!UICONTROL Local field]** 允许您访问每个表的字段列表。

   ![](assets/wf_add_data_local_external_data_join.png)

1. 如果需要，请指定过滤条件和数据排序模式。
1. 选择要在外部数据库中收集的其他数据。 为此，请双击要添加的字段，以在中显示这些字段 **[!UICONTROL Output columns]**。

   ![](assets/wf_add_data_local_external_data_select.png)

   单击 **[!UICONTROL Finish]** 以确认此配置。

## 安全连接 {#secure-connection}

>[!NOTE]
>
>安全连接仅对PostgreSQL可用。

在配置外部FDA帐户时，您可以安全地访问外部数据库。

为此，请在使用的端口的服务&#x200B;**器地址和地址后添加“:ssl**”。 例如： **192.168.0.52:4501:ssl**。

数据随后将通过安全SSL协议发送。

## 其他配置 {#additional-configurations}

如有必要，您可以创建用于处理外部数据库中数据的架构。 同样，Adobe Campaign允许您定义外部表中数据的映射。 这些配置是常规的，不仅适用于工作流。

>[!NOTE]
>
>有关在Adobe Campaign中创建架构和定义新数据映射的详细信息，请参 [阅此页](../../configuration/using/about-schema-edition.md)。