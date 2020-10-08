---
title: 创建种子地址
seo-title: 创建种子地址
description: 创建种子地址
seo-description: null
page-status-flag: never-activated
uuid: 0dae107a-7b53-4096-93c3-9517b402cbc9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 6dad49af-4818-471b-9df1-057cc6b9a68a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 2%

---


# 创建种子地址{#creating-seed-addresses}

种子地址不是通过标准用户档案和目标进行管理的，而是在Adobe Campaign层次结构的专用节点中管理的 **[!UICONTROL Resources > Campaign management > Seed addresses]**。

您可以创建子文件夹来组织种子地址。 为此，请右键单击该节 **[!UICONTROL Seed addresses]** 点并选择 **[!UICONTROL Create a new 'Seed addresses' folder]**。 命名子文件夹，然后按 **[!UICONTROL Enter]** 验证。 您现在可以创建种子地址或将其复制到此子文件夹。 For more on this, refer to [Defining addresses](#defining-addresses).

Adobe Campaign还允许您创建种子地址模板，这些模板导入投放或活动，并根据相关投放和活动的特定需求进行调整。 请参阅创 [建种子地址模板](#creating-seed-address-templates)。

## 定义地址 {#defining-addresses}

要创建种子地址，请按照以下步骤操作：

1. 单击 **[!UICONTROL New]** 种子地址列表上方的按钮。
1. 在选项卡的匹配字段中输入链接到地址的 **[!UICONTROL Recipient]** 数据。 可用字段与投放收件人用户档案中的标准字段(nms:收件人表)相对应：姓名、名字、电子邮件等。

   >[!NOTE]
   >
   >地址的标签会自动填写您定义的姓氏和名字。
   >
   >创建种子地址时，不必输入每个选项卡的所有字段。 任何缺失的个性化元素在投放期间随机输入。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在选 **[!UICONTROL Seed fields]** 项卡中，输入在分析阶段（在表中）将插入投放日志中 **[!UICONTROL nms:broadLog]** 的值。

1. 在选 **[!UICONTROL Additional data]** 项卡中，输入在投放工作流中创建的要为其分配特定值的数据管理所使用的个性化数据。

   >[!NOTE]
   >
   >确保已使用目标中以“@”开头的别名定义其他活动数 **[!UICONTROL Enrichment]** 据。 否则，您将无法在投放活动中与种子地址正确使用它们。

## 创建种子地址模板 {#creating-seed-address-templates}

要创建将导入并可修改每个投放的地址模板，该过程与定义新种子地址时的过程相同。 唯一的区别是种子地址模板地址必须存储在“Template”类型文件夹中。

要定义模板文件夹，请应用以下流程：

1. 创建新的 **[!UICONTROL Seed addresses]** 类型文件夹，右键单击该文件夹，然后选择 **[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 单击选 **[!UICONTROL Restriction]** 项卡并添加以下过滤条件： **@isModel = true**。

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   存储在此文件夹中的地址现在可用作地址模板。 您可以将它们导入投放或活动，并根据相关投放和活动的特定需求调整它们(请参 [阅添加种子地址](../../delivery/using/adding-seed-addresses.md))。
