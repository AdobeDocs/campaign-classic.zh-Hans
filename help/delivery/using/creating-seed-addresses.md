---
solution: Campaign Classic
product: campaign
title: 创建种子地址
description: 了解如何创建和使用种子地址
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---


# 创建种子地址{#creating-seed-addresses}

种子地址不是通过标准用户档案和目标管理的，而是在Adobe Campaign层级&#x200B;**[!UICONTROL Resources > Campaign management > Seed addresses]**&#x200B;的专用节点中。

您可以创建子文件夹来组织种子地址。 要执行此操作，请右键单击&#x200B;**[!UICONTROL Seed addresses]**&#x200B;节点并选择&#x200B;**[!UICONTROL Create a new 'Seed addresses' folder]**。 命名子文件夹，然后按&#x200B;**[!UICONTROL Enter]**&#x200B;进行验证。 您现在可以创建种子地址或将其复制到此子文件夹。 有关详细信息，请参阅[定义地址](#defining-addresses)。

Adobe Campaign还允许您创建种子地址模板，这些模板导入投放或活动中并根据相关投放和活动的特定需求进行调整。 请参阅[创建种子地址模板](#creating-seed-address-templates)。

## 定义地址{#defining-addresses}

要创建种子地址，请执行以下步骤：

1. 单击种子地址列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮。
1. 在&#x200B;**[!UICONTROL Recipient]**&#x200B;选项卡的匹配字段中输入链接到地址的数据。 可用字段与投放收件人用户档案(nms:收件人表)中的标准字段相对应：姓名、名字、电子邮件等

   >[!NOTE]
   >
   >地址的标签会自动填写您定义的姓氏和名字。
   >
   >创建种子地址时，不必输入每个选项卡的所有字段。 任何缺失的个性化元素在投放期间随机输入。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在&#x200B;**[!UICONTROL Seed fields]**&#x200B;选项卡中，输入在分析阶段（在&#x200B;**[!UICONTROL nms:broadLog]**&#x200B;表中）将插入投放日志的值。

1. 在&#x200B;**[!UICONTROL Additional data]**&#x200B;选项卡中，输入用于在数据管理工作流中创建的投放以及要为其分配特定值的个性化数据。

   >[!NOTE]
   >
   >确保已在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动中使用以“@”开头的别名定义其他目标数据。 否则，您将无法在投放活动中与种子地址正确使用它们。

## 创建种子地址模板{#creating-seed-address-templates}

要创建将导入的地址模板，并且可以修改每个投放的地址模板，该过程与定义新种子地址时相同。 唯一的区别是种子地址模板地址必须存储在“Template”类型文件夹中。

要定义模板文件夹，请应用以下流程：

1. 新建一个&#x200B;**[!UICONTROL Seed addresses]**&#x200B;类型文件夹，右键单击该文件夹，然后选择&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 单击&#x200B;**[!UICONTROL Restriction]**&#x200B;选项卡并添加以下过滤条件：**@isModel = true**。

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   存储在此文件夹中的地址现在可用作地址模板。 您可以将它们导入投放或活动，并根据相关投放和活动的特定需求调整它们(请参阅[添加种子地址](../../delivery/using/adding-seed-addresses.md))。
