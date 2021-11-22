---
product: campaign
title: 添加种子地址
description: 添加种子地址
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 5%

---

# 添加种子地址{#adding-seed-addresses}

![](../../assets/common.svg)

## 投放中的种子地址 {#seed-addresses-in-a-delivery}

要为投放添加特定种子地址，请单击 **[!UICONTROL To]** 链接，然后选择 **[!UICONTROL Seed addresses]** 选项卡。

![](assets/s_ncs_user_edit_del_addresses_tab.png)

有三种可能的插入模式：

1. 输入单个种子地址。

   为此，请单击 **[!UICONTROL Add]** 按钮并定义地址字段的内容。 对每个地址重复。

1. 导入地址模板并调整它们以满足您的需求。

   为此，请单击 **[!UICONTROL Import seed templates...]** 链接并选择包含地址模板的文件夹。 如需详细信息，请参阅[此部分](creating-seed-addresses.md#creating-seed-address-templates)。

   如有必要，在添加这些组件后，您可以双击它们或单击 **[!UICONTROL Detail...]** 按钮以调整每个地址的内容。

1. 创建条件以动态选择要插入的控制地址。

   为此，请单击 **[!UICONTROL Edit the dynamic condition...]** 链接，然后输入种子地址选择参数。 例如，您可以包含特定文件夹中包含的所有种子地址，或者包含属于贵组织特定部门的种子地址。

   此部分提供了一个示例： [用例：根据条件选择种子地址](use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>如果使用的收件人表不是默认表，则使用此选项 **nms:recipient** 表格，则您将使用随Adobe Campaign **[!UICONTROL Deliverability]** 模块。
>
>有关更多信息，请参阅 [使用外部收件人表](using-an-external-recipient-table.md) 以及 [收件箱呈现](inbox-rendering.md).

对于投放，您还可以自定义地址在提取文件中的插入方式。 默认情况下，会按输出文件的排序顺序插入它们，但您可以选择在文件末尾或开头插入它们，或在主目标收件人之间随机插入它们。

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## 营销活动中的种子地址 {#seed-addresses-in-a-campaign}

要向营销活动的目标添加种子地址，请选择操作并单击 **[!UICONTROL Edit]** 选项卡。

单击 **[!UICONTROL Advanced campaign settings...]** 链接，然后 **[!UICONTROL Seed addresses]** 选项卡，如下所示：

![](assets/s_ncs_user_edit_op_addresses_tab.png)

从营销策划插入的种子地址将添加到营销策划中每个投放的目标。
