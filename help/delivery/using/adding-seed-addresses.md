---
title: 添加种子地址
seo-title: 添加种子地址
description: 添加种子地址
seo-description: null
page-status-flag: never-activated
uuid: e94ddd46-bed6-4505-91b7-7e17abb0e9c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 0b9b53bf-4dd2-416c-894e-393aded489f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 添加种子地址{#adding-seed-addresses}

## 交付中的种子地址 {#seed-addresses-in-a-delivery}

要为分发添加特定种子地址，请单击链 **[!UICONTROL To]** 接，然后选择选 **[!UICONTROL Seed addresses]** 项卡。

![](assets/s_ncs_user_edit_del_addresses_tab.png)

有三种可能的插入模式：

1. 输入单个种子地址。

   为此，请单击按 **[!UICONTROL Add]** 钮并定义地址字段的内容。 对每个地址重复上述步骤。 如需详细信息，请参阅[此部分](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address)。

1. 导入地址模板，并根据您的需求调整它们。

   要执行此操作，请单击链 **[!UICONTROL Import seed templates...]** 接，然后选择包含地址模板的文件夹。 有关详细信息，请参阅创 [建种子地址模板](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates)。

   如有必要，添加这些地址后，您可以双击它们或单击按 **[!UICONTROL Detail...]** 钮以调整每个地址的内容。

1. 创建条件以动态选择要插入的控件地址。

   要执行此操作，请单击链 **[!UICONTROL Edit the dynamic condition...]** 接，然后输入种子地址选择参数。 例如，您可以包含特定文件夹中包含的所有种子地址，或包含您组织中属于特定部门的种子地址。

   本节中介绍了此示例：用 [例：根据条件选择种子地址](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)。

>[!NOTE]
>
>当使用的收件人表不是默认的 **nms:recipient** 表，并且您使用Adobe Campaign模块提供的收件箱渲染功能时，将使用此选 **[!UICONTROL Deliverability]** 项。
>
>有关详细信息，请参 [阅使用外部收件人表](../../delivery/using/using-an-external-recipient-table.md) ，以及收件箱渲 [染的相关文档](../../delivery/using/inbox-rendering.md)。

对于提交，您还可以自定义地址插入提取文件的方式。 默认情况下，它们按输出文件的排序顺序插入，但您可以选择在文件的结尾或开头插入，或在主目标收件人之间随机插入。

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## 营销活动中的种子地址 {#seed-addresses-in-a-campaign}

要向营销活动的目标添加种子地址，请选择操作，然后单击选 **[!UICONTROL Edit]** 项卡。

单击链 **[!UICONTROL Advanced campaign settings...]** 接，然后单击 **[!UICONTROL Seed addresses]** 选项卡，如下所示：

![](assets/s_ncs_user_edit_op_addresses_tab.png)

从营销活动插入的种子地址将添加到营销活动中每个分发的目标。
