---
product: campaign
title: 创建种子地址
description: 了解如何创建和使用种子地址
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 创建种子地址{#creating-seed-addresses}



种子地址不是通过标准配置文件和目标进行管理，而是在Adobe Campaign层次结构的专用节点中进行管理 **[!UICONTROL Resources > Campaign management > Seed addresses]**.

您可以创建子文件夹以组织种子地址。 要执行此操作，请右键单击 **[!UICONTROL Seed addresses]** 节点并选择 **[!UICONTROL Create a new 'Seed addresses' folder]**. 命名子文件夹，然后按 **[!UICONTROL Enter]** 进行验证。 您现在可以创建种子地址或将种子地址复制到此子文件夹。 有关更多信息，请参阅 [定义地址](#defining-addresses).

Adobe Campaign还允许您创建种子地址模板，这些模板将导入投放或营销活动中，并根据相关投放和营销活动的特定需求进行调整。 请参阅 [创建种子地址模板](#creating-seed-address-templates).

## 定义地址 {#defining-addresses}

要创建种子地址，请执行以下步骤：

1. 单击 **[!UICONTROL New]** 按钮进行标记。
1. 在的匹配字段中输入链接到地址的数据 **[!UICONTROL Recipient]** 选项卡。 可用字段对应于投放收件人用户档案（nms：recipient表）中的标准字段：姓名、名字、电子邮件等。

   >[!NOTE]
   >
   >地址的标签会自动填入您定义的姓氏和名字。
   >
   >创建种子地址时，无需输入每个选项卡的所有字段。 在投放分析期间随机输入缺少的个性化元素。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在 **[!UICONTROL Address fields]** 选项卡，输入将在分析阶段插入投放日志的值(在 **[!UICONTROL nms:broadLog]** 表)。

1. 在 **[!UICONTROL Additional data]** 选项卡，输入用于在Data Management工作流中创建的投放以及要为其分配特定值的个性化数据。

   >[!NOTE]
   >
   >确保已定义其他目标数据，且别名以“@”开头 **[!UICONTROL Enrichment]** 活动。 否则，您将无法在投放活动中正确地将它们与种子地址一起使用。

## 创建种子地址模板 {#creating-seed-address-templates}

要创建将导入的地址模板，并且可能会针对每次投放进行修改，该过程与定义新种子地址时的过程相同。 唯一的区别是种子地址模板地址必须存储在“模板”类型文件夹中。

要定义模板文件夹，请应用以下流程：

1. 新建 **[!UICONTROL Seed addresses]** 键入文件夹，右键单击该文件夹，然后选择 **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 单击 **[!UICONTROL Restriction]** 选项卡并添加以下筛选条件： **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   存储在此文件夹中的地址现在可用作地址模板。 您可以将它们导入投放或营销活动，并根据相关投放和营销活动的特定需求进行调整(请参阅 [添加种子地址](adding-seed-addresses.md))。
