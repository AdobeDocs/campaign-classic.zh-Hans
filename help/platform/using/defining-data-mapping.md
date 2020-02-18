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
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# 定义数据映射 {#defining-data-mapping}

Adobe Campaign允许您定义外部表中数据的映射。

为此，在创建外部表的架构后，您需要创建新的交付映射以将此表中的数据用作交付目标。

为此，请应用以下步骤：

1. 创建新的交付映射并选择定位维，例如您刚创建的架构。

   ![](assets/wf_new_mapping_create_fda.png)

1. 指示存储传送信息的字段（姓、名、电子邮件、地址等）。

   ![](assets/wf_new_mapping_define_join.png)

1. 指定信息存储的参数，包括扩展架构的后缀，以便它们能够轻松识别。

   ![](assets/wf_new_mapping_define_names.png)

   您可以选择是将排除(**excludelog**)、消息(**broadlog**)存储在单独的表中。

   您还可以选择是否管理此交付映射的跟踪(跟&#x200B;**踪日志**)。

1. 然后选择要考虑的扩展。 扩展类型取决于平台的参数和选项（查看许可证合同）。

   ![](assets/wf_new_mapping_define_extensions.png)

   单击按 **[!UICONTROL Save]** 钮以启动交付映射创建：所有链接的表都会根据选定参数自动创建。
