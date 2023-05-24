---
product: campaign
title: 添加种子地址
description: 添加种子地址
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 5%

---

# 添加种子地址{#adding-seed-addresses}



## 投放中的种子地址 {#seed-addresses-in-a-delivery}

要为投放添加特定的种子地址，请单击 **[!UICONTROL To]** 链接，然后选择 **[!UICONTROL Seed addresses]** 选项卡。

![](assets/s_ncs_user_edit_del_addresses_tab.png)

有三种可能的插入模式：

1. 输入单个种子地址。

   要执行此操作，请单击 **[!UICONTROL Add]** 按钮并定义地址字段的内容。 对每个地址重复此操作。

1. 导入地址模板，并根据您的需求对其进行调整。

   要执行此操作，请单击 **[!UICONTROL Import seed templates...]** 链接并选择包含地址模板的文件夹。 如需详细信息，请参阅[此部分](creating-seed-addresses.md#creating-seed-address-templates)。

   如有必要，在添加之后，您可以双击它们或单击 **[!UICONTROL Detail...]** 按钮以调整每个地址的内容。

1. 创建条件以动态选择要插入的控制地址。

   要执行此操作，请单击 **[!UICONTROL Edit the dynamic condition...]** 链接，然后输入种子地址选择参数。 例如，您可以包含特定文件夹中包含的所有种子地址，或属于贵组织特定部门的种子地址。

   此部分的示例如下： [用例：根据条件选择种子地址](use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>当使用的收件人表不是默认表时，将使用此选项 **nms：recipient** 您使用的是Adobe Campaign提供的收件箱呈现功能。 **[!UICONTROL Deliverability]** 模块。
>
>有关更多信息，请参阅 [使用外部收件人表](using-an-external-recipient-table.md) 以及有关的文档 [收件箱呈现](inbox-rendering.md).

对于投放，您还可以自定义将地址插入到提取文件中的方式。 默认情况下，会按输出文件的排序顺序插入它们，但您可以选择在文件的结尾或开头插入它们，或者在主目标的收件人中随机插入它们。

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## 营销活动中的种子地址 {#seed-addresses-in-a-campaign}

要将种子地址添加到促销活动的目标，请选择操作，然后单击 **[!UICONTROL Edit]** 选项卡。

单击 **[!UICONTROL Advanced campaign settings...]** 链接，然后 **[!UICONTROL Seed addresses]** 选项卡，如下所示：

![](assets/s_ncs_user_edit_op_addresses_tab.png)

从营销活动中插入的种子地址将添加到营销活动中每个投放的目标。
