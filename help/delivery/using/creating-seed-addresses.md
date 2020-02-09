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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 创建种子地址{#creating-seed-addresses}

种子地址不是通过标准配置文件和目标进行管理的，而是在Adobe Campaign层次结构的专用节点中 **[!UICONTROL Resources > Campaign management > Seed addresses]**。

您可以创建子文件夹以组织种子地址。 为此，请右键单击该节 **[!UICONTROL Seed addresses]** 点并选择 **[!UICONTROL Create a new 'Seed addresses' folder]**。 命名子文件夹，然后按 **[!UICONTROL Enter]** 验证。 您现在可以创建种子地址或将种子地址复制到此子文件夹。 For more on this, refer to [Defining addresses](#defining-addresses).

Adobe Campaign还允许您创建种子地址模板，这些模板会导入到分发或营销活动中，并根据相关分发和营销活动的特定需求进行调整。 请参阅创 [建种子地址模板](#creating-seed-address-templates)。

## 定义地址 {#defining-addresses}

要创建种子地址，请执行以下步骤：

1. 单击 **[!UICONTROL New]** 种子地址列表上方的按钮。
1. 在选项卡的匹配字段中输入链接到地址的数 **[!UICONTROL Recipient]** 据。 可用字段与交付收件人配置文件中的标准字段(nms:recipient table)相对应：姓名、名字、电子邮件等

   >[!NOTE]
   >
   >地址的标签会自动填写您定义的姓和名。
   >
   >创建种子地址时，不必输入每个选项卡的所有字段。 任何缺失的个性化元素在交付过程中会随机输入。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在选 **[!UICONTROL Seed fields]** 项卡中，输入将在分析阶段（在表中）期间插入到交付日志中的 **[!UICONTROL nms:broadLog]** 值。
1. 在选项卡 **[!UICONTROL Additional data]** 中，输入用于在数据管理工作流中创建的要向其分配特定值的传送的个性化数据。

## 创建种子地址模板 {#creating-seed-address-templates}

要创建要导入并可针对每个传送修改的地址模板，该过程与定义新种子地址时的过程相同。 唯一的区别是种子地址模板地址必须存储在“Template”类型文件夹中。

要定义模板文件夹，请应用以下流程：

1. 创建新的类 **[!UICONTROL Seed addresses]** 型文件夹，右键单击该文件夹，然后选择 **[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 单击该选 **[!UICONTROL Restriction]** 项卡并添加以下筛选条件： **@isModel = true**。

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   存储在此文件夹中的地址现在可用作地址模板。 您可以将它们导入交货或营销活动中，并根据相关交货和营销活动的特定需求调整它们(请参阅添 [加种子地址](../../delivery/using/adding-seed-addresses.md))。
