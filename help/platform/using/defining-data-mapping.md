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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---


# 定义数据映射 {#defining-data-mapping}

Adobe Campaign允许您定义外部表中数据的映射。

为此，在创建外部表的模式后，您需要创建新的投放映射，以将此表中的数据用作投放目标。

为此，请应用以下步骤：

1. 创建新投放映射并选择定位维度，例如您刚刚创建的模式。

   ![](assets/wf_new_mapping_create_fda.png)

1. 指示存储投放信息的字段（姓、名、电子邮件、地址等）。

   ![](assets/wf_new_mapping_define_join.png)

1. 指定信息存储的参数，包括扩展模式的后缀，以便它们能够轻松识别。

   ![](assets/wf_new_mapping_define_names.png)

   您可以选择是存储包含消&#x200B;**息**(broadlog)的排除&#x200B;**项(excludelog**)，还是存储在单独的表中。

   您还可以选择是否管理此投放映射的跟踪(**跟踪日**&#x200B;志)。

1. 然后，选择要考虑的扩展。 扩展类型取决于平台的参数和选项(视图许可证合同)。

   ![](assets/wf_new_mapping_define_extensions.png)

   单击按 **[!UICONTROL Save]** 钮以启动投放映射创建：所有链接表都会根据所选参数自动创建。
