---
product: campaign
title: 创建种子地址
description: 了解如何创建和使用种子地址
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 创建种子地址{#creating-seed-addresses}

种子地址不是通过标准配置文件和目标进行管理，而是通过Adobe Campaign层级&#x200B;**[!UICONTROL Resources > Campaign management > Seed addresses]**&#x200B;的专用节点进行管理。

您可以创建子文件夹来组织种子地址。 要执行此操作，请右键单击&#x200B;**[!UICONTROL Seed addresses]**&#x200B;节点并选择&#x200B;**[!UICONTROL Create a new 'Seed addresses' folder]**。 命名子文件夹，然后按&#x200B;**[!UICONTROL Enter]**&#x200B;进行验证。 您现在可以创建种子地址或将种子地址复制到此子文件夹。 有关更多信息，请参阅[定义地址](#defining-addresses)。

Adobe Campaign还允许您创建种子地址模板，这些模板可导入投放或营销策划中，并根据相关投放和营销策划的特定需求进行修改。 请参阅[创建种子地址模板](#creating-seed-address-templates)。

## 定义地址 {#defining-addresses}

要创建种子地址，请执行以下步骤：

1. 单击种子地址列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮。
1. 在&#x200B;**[!UICONTROL Recipient]**&#x200B;选项卡的匹配字段中输入链接到地址的数据。 可用字段对应于投放收件人用户档案中的标准字段（nms:recipient表）：名称、名字、电子邮件等

   >[!NOTE]
   >
   >地址的标签会自动填写您定义的姓氏和名字。
   >
   >创建种子地址时，无需输入每个选项卡的所有字段。 投放期间会随机输入任何缺失的个性化元素。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在&#x200B;**[!UICONTROL Seed fields]**&#x200B;选项卡中，输入将在分析阶段（在&#x200B;**[!UICONTROL nms:broadLog]**&#x200B;表中）插入投放日志的值。

1. 在&#x200B;**[!UICONTROL Additional data]**&#x200B;选项卡中，输入在数据管理工作流中创建的要为其分配特定值的投放所使用的个性化数据。

   >[!NOTE]
   >
   >确保在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动中已使用以“@”开头的别名定义了其他目标数据。 否则，您将无法在投放活动中将它们与种子地址一起正确使用。

## 创建种子地址模板 {#creating-seed-address-templates}

要创建要导入的地址模板，并且可针对每次投放进行修改，该过程与定义新种子地址时的过程相同。 唯一的区别是种子地址模板地址必须存储在“Template”类型文件夹中。

要定义模板文件夹，请应用以下流程：

1. 创建新的&#x200B;**[!UICONTROL Seed addresses]**&#x200B;类型文件夹，右键单击该文件夹，然后选择&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 单击&#x200B;**[!UICONTROL Restriction]**&#x200B;选项卡并添加以下筛选条件：**@isModel = true**。

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   现在，存储在此文件夹中的地址可用作地址模板。 您可以将种子地址导入投放或营销策划中，并根据相关投放和营销策划的特定需求对其进行调整（请参阅[添加种子地址](adding-seed-addresses.md)）。
