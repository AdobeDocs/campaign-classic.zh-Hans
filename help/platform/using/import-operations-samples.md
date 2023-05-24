---
product: campaign
title: 通用导入范例
description: 了解有关可以使用导入作业执行的常规导入的更多信息
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4582b524-2b6d-484c-bace-29d2e69f60e9
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 64%

---

# 通用导入范例 {#import-operations-samples}



## 从收件人清单导入 {#example--import-from-a-list-of-recipients}

要从清单概述创建和提供收件人清单，请应用以下步骤：

1. 创建清单

   * 单击 **[!UICONTROL Lists]** 中的链接 **[!UICONTROL Profiles and targets]** Adobe Campaign主页的菜单。
   * 单击 **[!UICONTROL Create]** 然后 **[!UICONTROL Import a list]** 按钮。

1. 选择要导入的文件

   单击右侧的文件夹 **[!UICONTROL Local file]** 字段并选择包含导入列表的文件。

   ![](assets/s_ncs_user_import_example00_01.png)

1. 清单名称和存储

   输入列表的名称，然后选择应保存的目录。

   ![](assets/s_ncs_user_import_example00_02.png)

1. 启动导入

   单击 **[!UICONTROL Next]** 然后 **[!UICONTROL Start]** 以开始导入列表。

   ![](assets/s_ncs_user_import_example00_03.png)

## 从文本文件导入新记录 {#example--import-new-records-from-a-text-file-}

要将存储在文本文件中的新收件人配置文件导入 Adobe Campaign 数据库，请使用以下步骤：

1. 选择模板

   * 从Adobe Campaign主页中，单击 **[!UICONTROL Profiles and targets]** 链接，然后 **[!UICONTROL Jobs]**. 在作业列表上方，单击 **[!UICONTROL New import]**.
   * 保留 **[!UICONTROL New text import]** 默认情况下选定的模板。
   * 更改标签和描述。
   * 选择 **[!UICONTROL Simple import]**。
   * 保留默认作业文件夹。
   * 单击 **[!UICONTROL Advanced parameters]** 并选择 **[!UICONTROL Tracking mode]** 选项，用于在执行期间查看导入的详细信息。

1. 选择要导入的文件

   单击右侧的文件夹 **[!UICONTROL Local file]** 字段并选择要导入的文件。

   ![](assets/s_ncs_user_import_example01_01.png)

1. 关联字段

   单击 **[!UICONTROL Guess the destination fields]** 图标以自动映射源架构和目标架构。 在单击之前检查此窗口中的信息 **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_import_example03_01.png)

1. 协调

   * 转到 **Recipients (nms:recipient)** 表。
   * 选择 **[!UICONTROL Insertion]** 操作，并将默认值保留在其他字段中。

      ![](assets/s_ncs_user_import_example04_01.png)

1. 导入收件人

   * 如有必要，请为要导入的记录指定一个文件夹。

      ![](assets/s_ncs_user_import_example05_01.png)

1. 启动导入

   * 单击 **[!UICONTROL Start]**。

      在编辑器的中心区域，您可以检查导入操作是否成功并查看已处理的记录数。

      ![](assets/s_ncs_user_import_example06_01.png)

      此 **[!UICONTROL Tracking]** 模式允许您跟踪源文件中每个记录的导入详细信息。 要实现此目的，请在主页中单击 **[!UICONTROL Profiles and Targets]** 则 **[!UICONTROL Processes]**，选择相关的导入，然后查找 **[!UICONTROL General]**， **[!UICONTROL Journal]** 和 **[!UICONTROL Rejects]** 选项卡。

      * 检查导入进度

         ![](assets/s_ncs_user_import_example07_01.png)

      * 处理每条记录的查看

         ![](assets/s_ncs_user_import_example07_02.png)

## 更新并插入收件人 {#example--update-and-insert-recipients}

我们希望更新数据库中的现有记录，并从文本文件中创建新记录。以下是该过程的示例：

1. 选择模板

   重复上面示例 2 中描述的步骤。

1. 要导入的文件

   选择要导入的文件。

   在我们的示例中，文件第一行的概述显示该文件包含三个记录的更新和一个记录的创建。

   ![](assets/s_ncs_user_import_example02_02.png)

1. 关联字段

   执行上面示例 2 中的过程。

1. 协调

   * 保留 **[!UICONTROL Update or insert]** 默认选中。
   * 保留选项 **[!UICONTROL Management of duplicates]** 在 **[!UICONTROL Update]** 模式，以便使用文本文件中的数据修改数据库中的现有记录。
   * 选择字段 **[!UICONTROL Birth date]**， **[!UICONTROL Name]** 和 **[!UICONTROL Company]** 并为其分配协调密钥。

      ![](assets/s_ncs_user_import_example04_02.png)

1. 启动导入

   * 单击 **[!UICONTROL Start]**。

      在追踪窗口中，您可以检查导入是否成功并查看已处理的记录数。

      ![](assets/s_ncs_user_import_example06_02.png)

   * 查看收件人表以检查此操作已修改记录。

      ![](assets/s_ncs_user_import_example06_03.png)

## 使用外部文件的值丰富该值 {#example--enrich-the-values-with-those-of-an-external-file}

我们希望通过文本文件修改数据库表中的某些字段，且优先考虑数据库中包含的值。

在此示例中，您可以看到文本文件中的某些字段具有值，而数据库中的相应字段为空。其他字段包含与数据库中包含的值不同的值。

* 要导入的文本文件的内容。

   ![](assets/s_ncs_user_import_example02_03.png)

* 导入前的数据库状态

   ![](assets/s_ncs_user_import_example06_04.png)

应用以下步骤：

1. 选择模板

   执行上面示例 2 中的过程。

1. 要导入的文件

   选择要导入的文件。

1. 关联字段

   执行上面示例 2 中的过程。

   在预览文件的第一行时，您可以看到该文件包含某些记录的更新。

1. 协调

   * 转到表并选择 **[!UICONTROL Update]** 操作。
   * 选择选项 **[!UICONTROL Reject entity]** 对于 **[!UICONTROL Management of doubles]** 字段。
   * 保留选项 **[!UICONTROL Management of duplicates]** 在 **[!UICONTROL Update]** 模式，以便使用文本文件中的数据修改数据库中的现有记录。
   * 将光标放在 **[!UICONTROL Last name (@lastName)]** 节点并选择 **[!UICONTROL Update only if destination is empty]** 选项。
   * 对重复此操作 **[!UICONTROL Company (@company)]** 节点。
   * 为字段分配协调密钥 **[!UICONTROL Birth date]**， **[!UICONTROL Email]** 和 **[!UICONTROL First name]**.

      ![](assets/s_ncs_user_import_example04_03.png)

1. 启动导入

   单击 **[!UICONTROL Start]**。

   查看收件人表以确认导入已修改记录。

   ![](assets/s_ncs_user_import_example06_05.png)

   只有空值被文本文件中的值替换，但数据库中的现有值未被导入文件中的值覆写。

## 使用外部文件更新并丰富值 {#example--update-and-enrich-the-values-from-those-in-an-external-file}

我们希望使用文本文件修改数据库表中的某些字段，优先套用文本文件中包含的值。

在此示例中，您将看到文本文件中的某些字段具有空值，而数据库中的相应字段不为空。其他字段包含与数据库中的值不同的值。

* 要导入的文本文件的内容。

   ![](assets/s_ncs_user_import_example02_04.png)

* 导入前的数据库状态

   ![](assets/s_ncs_user_import_example06_07.png)

1. 选择模板

   执行上面示例 2 中的过程。

1. 要导入的文件

   选择要导入的文件。

   在预览文件的第一行时，您可以看到该文件包含空字段和某些记录的更新。

1. 关联字段

   执行上面示例 2 中的过程。

1. 协调

   * 转到表并选择 **[!UICONTROL Update]**.
   * 选择选项 **[!UICONTROL Reject entity]** 对于 **[!UICONTROL Management of doubles]** 字段。
   * 保留选项 **[!UICONTROL Management of duplicates]** 在 **[!UICONTROL Update]** 使用文本文件中的数据修改数据库中现有记录的模式。
   * 将光标放在 **[!UICONTROL Account number (@account)]** 节点并选择选项 **[!UICONTROL Take empty values into account]**.
   * 选择字段 **[!UICONTROL Birth date]**， **[!UICONTROL Email]** 和 **[!UICONTROL First name]** 并为其分配协调密钥。

      ![](assets/s_ncs_user_import_example04_04.png)

1. 启动导入

   * 单击 **[!UICONTROL Start]**。
   * 查看收件人表以检查操作已修改的记录。

      ![](assets/s_ncs_user_import_example06_06.png)

      空文本文件的值已覆写数据库中的值。数据库中的现有值已更新为导入文件中的值，以与 **[!UICONTROL Update]** 为步骤4中的重复项选定的选项。
