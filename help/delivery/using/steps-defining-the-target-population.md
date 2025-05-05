---
product: campaign
title: 定义目标群体
description: 了解如何定义目标群体
feature: Audiences, Proofs
role: User
exl-id: d0ed7be7-3147-4cb8-9ce7-ea51602e9048
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1729'
ht-degree: 23%

---

# 定义目标群体 {#defining-the-target-population}

对于每个投放，您可以定义几种类型的目标群体：

* **主要受众**：将接收消息的用户档案。 [了解详情](steps-defining-the-target-population.md#selecting-the-main-target)
* **验证**：验证周期中涉及的验证消息的收件人。 [了解详情](steps-defining-the-target-population.md#defining-a-specific-proof-target)
* **种子地址**：不在投放目标但将接收投放的收件人（仅在营销活动上下文中）。 [了解详情](about-seed-addresses.md)
* **对照组**：不会接收投放的群体，用于跟踪行为和营销活动影响（仅在营销活动上下文中）。 [了解详情](../../campaign/using/marketing-campaign-target.md#defining-a-control-group)。

## 选择投放的主要收件人 {#selecting-the-main-target}

在大多数情况下，会从 Adobe Campaign 数据库中提取主要目标（默认模式）。但是，收件人也可以存储在外部文件中。 可在[此部分](steps-defining-the-target-population.md#selecting-external-recipients)中了解详情。

要选择投放的收件人，请执行以下步骤：

1. 在投放编辑器中，选择 **[!UICONTROL To]**。
1. 如果收件人存储在数据库中，请选择第一个选项。

   ![](assets/s_ncs_user_wizard_email02a.png)

1. 在&#x200B;**[!UICONTROL Target mapping]**&#x200B;下拉列表中选择目标映射。 Adobe Campaign默认目标映射为&#x200B;**[!UICONTROL Recipients]**，基于&#x200B;**nms：recipient**&#x200B;架构。

   可以使用其他目标映射，其中一些映射可能与您的特定配置相关。[了解详情](#select-a-target-mapping)。

1. 单击 **[!UICONTROL Add]** 按钮以定义限制筛选条件。

   然后，您可以选择要应用的筛选类型：

   ![](assets/s_ncs_user_wizard_email02b.png)

   您可以使用数据库中定义的定向类型选择收件人。 要使用目标类型，请选择它并单击&#x200B;**[!UICONTROL Next]**。 对于每个目标，您可以通过单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡来显示相关的收件人。 对于特定类型的目标，**[!UICONTROL Refine target]**&#x200B;按钮允许您组合多个定位条件。

   默认情况下，提供以下目标类型：

   * **[!UICONTROL Filtering conditions]** ：利用此选项可定义查询并显示结果。 [此部分](../../platform/using/creating-filters.md#creating-an-advanced-filter)中介绍了定义查询的方法。
   * **[!UICONTROL Subscribers of an information service]**：通过此选项，可选择新闻稿，收件人必须订阅新闻稿才能成为所创建投放的目标。

     ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** ：利用此选项可将现有投放的收件人定义为定位条件。 然后，您必须在列表中选择投放：

     ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** ：通过此选项，您可以选择投放文件夹，并定位该文件夹中投放的收件人。

     ![](assets/s_ncs_user_wizard_email02e.png)

     您可以从下拉列表中进行选择，以筛选收件人的行为：

     ![](assets/s_ncs_user_wizard_email02f.png)

     >[!NOTE]
     >
     >通过 **[!UICONTROL Include sub-folders]** 选项，还可以锁定所选节点下树结构中文件夹包含的投放。

   * **[!UICONTROL Recipients included in a folder]** ：利用此选项可定向树的特定文件夹中包含的配置文件。
   * **[!UICONTROL A recipient]** ：通过此选项，您可以从数据库中的用户档案中选择特定收件人。
   * **[!UICONTROL A list of recipients]** ：通过此选项可定向收件人列表。 列表显示在[此部分](../../platform/using/creating-and-managing-lists.md)中。
   * **[!UICONTROL User filters]** ：利用此选项可访问预配置的筛选器，以将其用作数据库中用户档案的筛选条件。 要查看预配置的筛选条件，请参阅[此部分](../../platform/using/creating-filters.md#saving-a-filter)。
   * 利用选项&#x200B;**[!UICONTROL Exclude recipients corresponding to this segment]**，可定向不符合所定义的目标条件的收件人。 要使用此选项，请选择相应的框，然后按照之前所述应用目标选择，以排除生成的用户档案。

     ![](assets/s_ncs_user_wizard_email02g.png)

1. 在 **[!UICONTROL Label]** 字段中输入此目标的名称。 默认情况下，标签将是第一个定位标准的标签。 对于组合，最好使用显式名称。
1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;以验证配置的定位。

   在“主要目标配置”选项卡的中心部分中概述了定义的目标选择标准。单击标准可查看其内容（配置和预览）。要删除某个标准，请单击其标签后面的十字线。

   ![](assets/s_ncs_user_wizard_email02h.png)

### 选择外部收件人 {#selecting-external-recipients}

您可以对未保存在数据库中、但存储在外部文件中的收件人启动投放。 例如，我们将在此处向从文本文件导入的收件人发送投放。

操作步骤：

1. 单击 **[!UICONTROL To]** 链接以选择投放的收件人。
1. 选择 **[!UICONTROL Defined in an external file]** 选项。

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. 默认情况下，会在数据库中导入收件人。 您必须选择&#x200B;**[!UICONTROL Target mapping]**。 [了解详情](#select-a-target-mapping)

   您还可以选择&#x200B;**[!UICONTROL Do not import the recipients into the database]**。

1. 导入收件人时，单击 **[!UICONTROL File format definition...]** 链接以选择和配置外部文件。

   有关数据导入的详细信息，请参阅[此部分](../../platform/using/executing-import-jobs.md#step-2---source-file-selection)。

1. 单击 **[!UICONTROL Finish]** 并将您的投放配置为标准投放。

>[!CAUTION]
>
>定义电子邮件投放的邮件内容时，不要包含指向镜像页面的链接；此投放模式无法生成该链接。

### 定义排除设置 {#define-exclusion-settings}

地址错误和质量等级由服务提供商(IAP)提供。 此信息会在投放操作后自动更新到收件人配置文件中，并会更新服务提供商返回的文件。 可以在配置文件中只读查看它。

您可以选择排除已达到一定数量的连续错误或其质量等级低于此窗口中指定的阈值的地址。 您还可以选择是否授权未返回数据的不符合条件的地址。

>[!NOTE]
>
>如果直邮投放中两个收件人的名字、姓氏、邮政编码和城市相同，则会出现双重错误，并且不会考虑重复项。

**[!UICONTROL Exclusions]**&#x200B;选项卡用于限制消息数量。

>[!NOTE]
>
>建议使用默认参数，但您可以根据需要调整设置。但是，这些选项只应由专家用户更改，以避免误用和错误。

单击&#x200B;**[!UICONTROL Edit...]**&#x200B;链接以修改默认配置。

![](assets/s_ncs_user_wizard_email02i.png)

可以使用以下选项：

* **[!UICONTROL Exclude duplicate addresses during delivery]**。 此选项默认处于活动状态：它允许您在投放期间消除重复的电子邮件地址。 所应用的策略可能会因如何使用Adobe Campaign以及数据库中的数据类型而有所不同。

  可以为每个投放模板配置选项的默认值。

  例如：

   * 新闻稿或电子文档投放。 如果数据没有本机重复项，则在某些情况下不排除重复项。 使用同一电子邮件地址订阅的一对夫妇可能会收到两封特定的个性化电子邮件：一封按姓名发送给每个人。 在这种情况下，可取消选择此选项。
   * 营销活动的投放：重复排除对于避免向同一收件人发送过多消息至关重要。 在这种情况下，可选中此选项。

     如果取消选择此选项，则可以访问其他选项： **[!UICONTROL Keep duplicate records (same identifier)]**。 它可让您授权向满足多个定位标准的收件人进行多次投放。

     ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]**，即电子邮件地址处于拒绝列表状态（选择退出）的收件人。必须继续选择这一选项，以遵守电子营销的职业道德和电子商务相关法律。
* **[!UICONTROL Exclude quarantined recipients]**。 利用此选项，可从目标中排除其地址未响应的任何用户档案。 我们强烈建议保持选中此选项。

  >[!NOTE]
  >
  >有关隔离管理的详细信息，请参阅[了解隔离管理](understanding-quarantine-management.md)。

* 给定消息数的 **[!UICONTROL Limit delivery]**。使用此选项可输入要发送的最大消息数。如果目标的内容超过指示的消息数，则随机选择将应用于目标。

### 缩小目标群体大小 {#reducing-the-size-of-the-target-population}

您可以减小目标群体的大小。 为此，请在&#x200B;**[!UICONTROL Requested quantity]**&#x200B;字段中指定要导出的收件人数量。

![](assets/s_ncs_user_edit_del_exe_tab.png)

## 选择校样消息的收件人 {#selecting-the-proof-target}

校样是一种特殊消息，允许您在将投放发送到主目标之前对其进行测试。 校样收件人负责审批消息的表单和内容。

![](assets/do-not-localize/how-to-video.png) [通过观看视频了解此功能](#seeds-and-proofs-video)


要选择校样目标，请执行以下步骤：

1. 单击 **[!UICONTROL To]** 链接。
1. 单击&#x200B;**[!UICONTROL Target of the proofs]**&#x200B;选项卡。
1. 单击&#x200B;**[!UICONTROL Targeting mode]**&#x200B;字段以选择要应用的方法： **[!UICONTROL Definition of a specific proof target]** 、 **[!UICONTROL Substitution of the address]** 、 **[!UICONTROL Seed addresses]**&#x200B;或&#x200B;**[!UICONTROL Specific target and seed addresses]**。

>[!NOTE]
>
>通常，验证的目标可以添加到主目标。 为此，请在&#x200B;**[!UICONTROL Main target]**&#x200B;选项卡的下半部分选择相应的选项。

## 定义特定验证目标 {#defining-a-specific-proof-target}

选择验证目标时，**[!UICONTROL Definition of a specific proof target]**&#x200B;选项允许您从数据库中的用户档案中选择验证收件人。

选择此选项可使用&#x200B;**[!UICONTROL Add]**&#x200B;按钮选择收件人，如定义主目标时那样。 请参阅[选择主目标](steps-defining-the-target-population.md#selecting-the-main-target)。

![](assets/s_ncs_user_wizard_email01_143.png)

有关校样发送的更多信息，请参阅[此章节](steps-validating-the-delivery.md#sending-a-proof)。

### 在验证中使用地址替换 {#using-address-substitution-in-proof}

您可以使用&#x200B;**[!UICONTROL Substitution of the address]**&#x200B;选项，而不是在数据库中选择专用收件人。

此选项允许您使用投放的收件人用户档案，并将其电子邮件地址替换为一个或多个将接收验证的其他地址。

选择此选项后，验证地址将通过允许您配置替换的特殊编辑器填充。

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

按如下方式执行配置：

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;图标以定义替换。
1. 输入要使用的收件人地址，或从列表中选择此地址。
1. 选择要在验证中使用的配置文件：保存&#x200B;**[!UICONTROL Profile to use]**&#x200B;列中的&#x200B;**[!UICONTROL Random]**&#x200B;值以使用验证中目标的任意配置文件的数据。

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. 单击&#x200B;**[!UICONTROL Detail]**&#x200B;图标可从主目标中选择配置文件，如以下示例所示：

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   您可以根据需要定义任意数量的替代地址。

## 使用种子地址作为证明 {#using-seed-addresses-as-proof}

您可以使用&#x200B;**[!UICONTROL Seed addresses]**&#x200B;作为验证的目标：此选项允许您使用或导入现有种子地址的列表。

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>种子地址在[关于种子地址](about-seed-addresses.md)中显示。

您可以使用&#x200B;**[!UICONTROL Specific target and Seed addresses]**&#x200B;选项将特定验证目标的定义和种子地址的使用结合使用。 随后，将在两个单独的子选项卡中定义相关配置。

另请参阅：

* [选择验证目标](#selecting-the-proof-target)
* [关于种子地址](about-seed-addresses.md)
* [用例：根据条件选择种子地址](use-case-selecting-seed-addresses-on-criteria.md)

## 选择目标映射 {#select-a-target-mapping}

默认情况下，投放模板以&#x200B;**[!UICONTROL Recipients]**&#x200B;为目标。 因此，它们的目标映射使用&#x200B;**nms：recipient**&#x200B;表的字段。 Adobe Campaign为您的投放提供了其他目标映射，可根据您的需求使用。

![](assets/delivery_select_mapping.png)

这些映射如下所示：

| 名称 | 使用 | 标准架构 |
|---|---|---|
| 收件人 | 投放给Adobe Campaign数据库的收件人 | nms：recipient |
| 访客 | 向通过反向链接（病毒式营销）或社交网络(例如Facebook， X — 以前称为Twitter)收集用户档案的访客投放。 | mns：visitor |
| 订阅 | 发送给订阅了新闻稿等信息服务的收件人 | nms：subscription |
| 访客订阅 | 向订阅了信息服务的访客投放 | nms：visitorSub |
| 服务 | Publish到X帐户或Facebook页面 | nms：service |
| 运算符 | 交付给Adobe Campaign操作员 | nms：operator |
| 外部文件 | 通过包含投放所需所有信息的文件投放 | 无链接架构，未输入目标 |


## 教程视频 {#seeds-and-proofs-video}

在本视频中，您将了解如何向现有电子邮件添加种子和校样，以及如何进行发送。

>[!VIDEO](https://video.tv.adobe.com/v/35508?quality=12&captions=chi_hans)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他 Campaign Classic 操作方法视频。
