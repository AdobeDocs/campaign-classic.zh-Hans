---
product: campaign
title: 添加种子地址
description: 添加种子地址
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Seed Address
role: User
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 5%

---

# 添加种子地址{#adding-seed-addresses}

## 投放中的种子地址 {#seed-addresses-in-a-delivery}

要为投放添加特定的种子地址，请单击&#x200B;**[!UICONTROL To]**&#x200B;链接，然后选择&#x200B;**[!UICONTROL Seed addresses]**&#x200B;选项卡。

![](assets/s_ncs_user_edit_del_addresses_tab.png)

有三种可能的插入模式：

1. 输入单个种子地址。

   为此，请单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并定义地址字段的内容。 对每个地址重复此操作。

1. 导入地址模板并根据您的需求对其进行调整。

   为此，请单击&#x200B;**[!UICONTROL Import seed templates...]**&#x200B;链接，然后选择包含地址模板的文件夹。 如需详细信息，请参阅[此小节](creating-seed-addresses.md#creating-seed-address-templates)。

   如有必要，在添加地址后，您可以双击它们或单击&#x200B;**[!UICONTROL Detail...]**&#x200B;按钮以调整每个地址的内容。

1. 创建条件以动态选择要插入的控制地址。

   为此，请单击&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;链接，然后输入种子地址选择参数。 例如，您可以包括特定文件夹中包含的所有种子地址，或属于贵组织特定部门的种子地址。

   此部分中显示了一个示例：[用例：根据条件](use-case-selecting-seed-addresses-on-criteria.md)选择种子地址。

>[!NOTE]
>
>当使用的收件人表不是默认的&#x200B;**nms：recipient**&#x200B;表，并且您使用的是Adobe Campaign **[!UICONTROL Deliverability]**&#x200B;模块提供的收件箱呈现功能时，将使用此选项。
>
>有关详细信息，请参阅[使用外部收件人表](using-an-external-recipient-table.md)和有关[收件箱呈现](inbox-rendering.md)的文档。

对于投放，您还可以自定义将地址插入到提取文件中的方式。 默认情况下，会按输出文件的排序顺序插入陷阱，但您可以选择在文件末尾或开头插入陷阱，或者在主目标的收件人中随机插入。

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## 营销活动中的种子地址 {#seed-addresses-in-a-campaign}

要将种子地址添加到营销活动的目标，请选择操作，然后单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡。

单击&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Seed addresses]**&#x200B;选项卡，如下所示：

![](assets/s_ncs_user_edit_op_addresses_tab.png)

从营销活动中插入的种子地址将添加到营销活动中每个投放的目标。
