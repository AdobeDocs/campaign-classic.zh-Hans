---
product: campaign
title: 编辑用户档案
description: 编辑用户档案
feature: Profiles
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: 0f3a5582-5c90-4393-bee8-d9e2f07e5982
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 85%

---

# 编辑用户档案{#editing-a-profile}



要查看与用户档案相关的信息，请在用户档案列表中单击其名称。

用户档案详细信息会出现在新的选项卡中。

![](assets/s_user_recipient_edit.png)

用户档案相关数据被分组放在多个选项卡中。

选项卡及其內容取决于您的配置及已安裝的软件包。

>[!CAUTION]
>
>可通过 Adobe Campaign 树状结构中的 **[!UICONTROL Administration > Configuration > Data schemas]** 节点访问用户档案表中各字段相关的 XML 模式和表单。只有专家用户才能改变这些模式。
>
>如需详细信息，请参阅[此页面](../../configuration/using/about-schema-edition.md)。

## “一般”选项卡 {#general-tab}

此界面中包含有关所选用户档案的全部一般数据。特別是其中包含姓氏、名字、电子邮件地址、电子邮件接收格式等。它看起来如下所示：

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>当 **[!UICONTROL No longer contact (by any channel)]** 列入阻止列表选项，这意味着用户档案处于订阅状态，即用户档案已表示不希望被联系（例如，通过单击新闻稿中的退订链接）。 通过任何渠道（电子邮件、直邮广告等）投放时都不会定位这些顾客。有关详细信息，请参见[此页面](../../delivery/using/understanding-quarantine-management.md)。

## “联系人信息”选项卡 {#contact-information-tab}

此界面包含所选用户档案的直邮地址。它看起来如下所示：

![](assets/s_ncs_user_profile_details_tab.png)

此界面显示地址的质量指标，以及地址中包含的错误数目。邮递方根据先前投放过程中所找到的错误数量直接使用此信息，且无法手动修改。

## “其他”选项卡 {#other-tab}

此界面包含用户定义字段，可根据需求对其进行个性化设置。您还可以更改字段的名称并定义其格式，方法是 **[!UICONTROL Field properties...]**，如下所示：

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>如需有关字段属性和添加字段的详细信息，请参阅[此页面](../../configuration/using/new-field-wizard.md)。

## “列表”选项卡 {#lists-tab}

此界面显示所选的用户档案属于哪个组。单击 **[!UICONTROL Add]** 将用户档案订阅添加到列表中。单击 **[!UICONTROL Detail]** 显示所选列表中的描述和用户档案列表。

![](assets/s_ncs_user_profile_groups_tab_details.png)

有关详细信息，请参见 [创建和管理列表](../../platform/using/creating-and-managing-lists.md).

## “订阅”选项卡 {#subscriptions-tab}

此界面包含用户档案所订阅的信息服务。

![](assets/s_ncs_user_profile_subscript_tab_details.png)

**[!UICONTROL Detail]** 按钮可显示所选订阅的属性。可使用 **[!UICONTROL Add]** 按钮手动添加新的订阅。

有关详细信息，请参见[此页面](../../delivery/using/managing-subscriptions.md)。

## “投放”选项卡 {#deliveries-tab}

此界面显示所选用户档案的投放日志。您也可以显示通过所有渠道投放至用户档案的投放动作的标签、日期和状态。

![](assets/s_ncs_user_profile_delivery_tab.png)

## “跟踪”选项卡 {#tracking-tab}

您可以使用此界面查看所选用户档案的跟踪日志。此信息用于跟踪投放后用户档案的行为。

![](assets/s_ncs_user_profile_tracking_tab.png)

此选项卡显示在投放中所有被跟踪的 URL 累积数目。

可配置列表的内容，通常包含：所点击的 URL、点击日期与时间，以及包含 URL 的文档。

>[!NOTE]
>
>如需有关跟踪功能的详细信息，请参阅[此页面](../../delivery/using/delivery-dashboard.md)。
