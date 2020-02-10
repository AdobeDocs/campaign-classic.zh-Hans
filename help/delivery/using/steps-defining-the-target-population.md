---
title: 定义目标人群
seo-title: 定义目标人群
description: 定义目标人群
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 62e6537ba306956cac3bf6e1dd18567bc1414917

---


# 定义目标人群 {#defining-the-target-population}

## 关于目标人群 {#about-target-populations}

对于每个交付，您可以定义几种类型的目标人群。 以下部分提供了有关如何选择的更多信息：

* **递送的主要收件人**。 [阅读更多](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target)。
* **校样消息的接收方**，以设置验证周期。 [阅读更多](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)。

此外，您还可以定义种 [子地址](../../delivery/using/about-seed-addresses.md), [以及控制组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。 如果交付包含在营销活动中。

## 选择分发的主收件人 {#selecting-the-main-target}

在大多数情况下，主目标会从营销活动数据库中提取（默认模式）。

收件人也可以存储在外部文件中。 选择外部收件人中显示了此类交 [付的配置](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)。

要选择要创建的分发的收件人，请执行以下步骤：

1. 单击链 **[!UICONTROL To]** 接。
1. 如果收件人存储在数据库中，请选择第一个选项。

   ![](assets/s_ncs_user_wizard_email02a.png)

1. 在下拉列表中选 **[!UICONTROL Target mapping]** 择目标映射。 Adobe Campaign默认目标映射为 **[!UICONTROL Recipients]**。

   其他目标映射可用，某些映射可能与您的特定配置相关。 有关目标映射的详细信息，请参阅 [选择目标映射](../../delivery/using/selecting-a-target-mapping.md)。

1. 单击该按 **[!UICONTROL Add]** 钮可定义限制过滤器。

   然后，您可以选择要应用的筛选类型：

   ![](assets/s_ncs_user_wizard_email02b.png)

   您可以使用数据库中定义的定位类型选择收件人。 要使用目标类型，请选择该类型，然后单击 **[!UICONTROL Next]**。 对于每个目标，您可以通过单击选项卡来显示相关的收 **[!UICONTROL Preview]** 件人。 对于某些类型的目标，该按 **[!UICONTROL Refine target]** 钮允许您组合多个定位条件。

   默认情况下提供以下目标类型：

   * **[!UICONTROL Filtering conditions]** :此选项允许您定义查询并显示结果。 本节介绍了定义查询 [的方法](../../platform/using/creating-filters.md#creating-an-advanced-filter)。
   * **[!UICONTROL Subscribers of an information service]** :此选项允许您选择新闻稿，收件人必须订阅才能被创建的分发定位到该新闻稿。

      ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** :此选项允许您将现有分发的收件人定义为定位标准。 然后，您必须在列表中选择传送：

      ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** :通过此选项，您可以选择传送文件夹并定位该文件夹中传送的收件人。

      ![](assets/s_ncs_user_wizard_email02e.png)

      您可以从下拉列表中选择以下内容，以过滤收件人的行为：

      ![](assets/s_ncs_user_wizard_email02f.png)

      >[!NOTE]
      >
      >该选 **[!UICONTROL Include sub-folders]** 项还允许您定位包含在选定节点下树结构中的文件夹中的分发。

   * **[!UICONTROL Recipients included in a folder]** :通过此选项，您可以定位树中特定文件夹中包含的配置文件。
   * **[!UICONTROL A recipient]** :此选项允许您从数据库中的配置文件中选择特定收件人。
   * **[!UICONTROL A list of recipients]** :通过此选项，可以定位收件人列表。 此部分中显示 [列表](../../platform/using/creating-and-managing-lists.md)。
   * **[!UICONTROL User filters]** :此选项允许您访问预配置的过滤器，以将其用作数据库中配置文件的过滤条件。 本节将介绍预配置的 [过滤器](../../platform/using/creating-filters.md#saving-a-filter)。
   * 通过该选 **[!UICONTROL Exclude recipients corresponding to this segment]** 项，您可以定位不满足定义的目标标准的收件人。 要使用此选项，请选择相应的框，然后应用定位（如前面所定义）以排除生成的配置文件。

      ![](assets/s_ncs_user_wizard_email02g.png)

1. 在字段中输入此定位的名 **[!UICONTROL Label]** 称。 默认情况下，该标签将作为第一个定位标准的标签。 对于组合，最好使用显式名称。
1. 单击 **[!UICONTROL Finish]** 以验证所配置的定位。

   定义的定位条件汇总在主目标配置选项卡的中央部分。 单击某个标准可查看其内容（配置和预览）。 要删除标准，请单击其标签后的叉号。

   ![](assets/s_ncs_user_wizard_email02h.png)

### 选择外部收件人 {#selecting-external-recipients}

您可以对未保存在数据库中但存储在外部文件中的收件人启动分发。 例如，我们将在此处向从文本文件导入的收件人发送分发。

操作步骤：

1. 单击链 **[!UICONTROL To]** 接以选择您的分发的收件人。
1. 选择选 **[!UICONTROL Defined in an external file]** 项。

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. 默认情况下，收件人导入数据库中。 必须选择 **[!UICONTROL Target mapping]**。 有关目标映射的详细信息，请参阅 [选择目标映射](../../delivery/using/selecting-a-target-mapping.md)

   您还可以选择 **[!UICONTROL Do not import the recipients into the database]**。

1. 导入收件人时，单击链 **[!UICONTROL File format definition...]** 接以选择和配置外部文件。

   For more information on data import, refer to [this section](../../platform/using/importing-data.md#step-2---source-file-selection).

1. 单击 **[!UICONTROL Finish]** 并将您的交付配置为标准交付。

>[!CAUTION]
>
>在定义邮件内容时，不要包含指向镜像页面的链接；无法在此传送模式下生成它。

### 设置排除设置 {#customizing-exclusion-settings}

地址错误和质量等级由服务提供商(IAP)提供。 此信息会在发送操作之后在收件人配置文件中自动更新，并且会与服务提供商返回的文件一起更新。 可在配置文件中以只读方式查看它。

您可以选择排除已达到特定数量连续错误或质量等级低于此窗口中指定阈值的地址。 您还可以选择是否对尚未返回任何数据的未限定地址授权。

>[!NOTE]
>
>如果直接邮寄中的两个收件人的名字、姓氏、邮寄代码和城市都相同，则会出现双重错误，并且不会考虑重复项。

该 **[!UICONTROL Exclusions]** 选项卡用于限制消息数。

>[!NOTE]
>
>建议使用默认参数，但您可以根据需要调整设置。 但是，这些选项只应由专家用户更改，以避免任何使用错误和错误。

单击链 **[!UICONTROL Edit...]** 接以修改默认配置。

![](assets/s_ncs_user_wizard_email02i.png)

可以使用以下选项：

* **[!UICONTROL Exclude duplicate addresses during delivery]**. 此选项默认处于活动状态：它可让您在发送过程中消除重复的电子邮件地址。 所应用的策略可能因Adobe Campaign的使用方式和数据库中的数据类型而异。

   可以为每个分发模板配置选项的默认值。

   例如：

   * 交付新闻稿或电子文档交付。 在某些情况下，如果数据没有本机副本，则不排除重复项。 订阅同一电子邮件地址的夫妇可能会收到两条特定的个性化电子邮件：一个按姓名发给每个人。 在这种情况下，可以取消选择此选项。
   * 营销活动的交付：重复排除是避免向同一收件人发送过多消息的关键。 在这种情况下，可以选择此选项。

      如果取消选择此选项，则可访问其他选项： **[!UICONTROL Keep duplicate records (same identifier)]**. 它允许您授权向满足多个定位条件的收件人进行多个分发。

      ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** ，即电子邮件地址在黑名单中的收件人（“选择退出”）。 为遵守电子营销的职业道德和电子商务法律，必须继续选择此选项。
* **[!UICONTROL Exclude quarantined recipients]**. 此选项允许您从目标中排除任何地址没有响应的配置文件。 我们强烈建议保持选中此选项。

   >[!NOTE]
   >
   >有关隔离管理的详细信息，请参阅了解隔 [离管理](../../delivery/using/understanding-quarantine-management.md)。

* **[!UICONTROL Limit delivery]** 到给定数量的消息。 此选项允许您输入要发送的消息的最大数量。 如果目标的内容超过所指示的消息数，则随机选择被应用到目标。

### 缩小目标人群的规模 {#reducing-the-size-of-the-target-population}

您可以减小目标人口的大小。 为此，请在字段中指定要导出的收件人 **[!UICONTROL Requested quantity]** 数。

![](assets/s_ncs_user_edit_del_exe_tab.png)

## 选择校样消息的收件人 {#selecting-the-proof-target}

证明是一条特殊消息，允许您在将传送发送到主目标之前测试传送。 证明收件人负责批准邮件的表单和内容。

要选择校样的目标，请执行以下步骤：

1. 单击链 **[!UICONTROL To]** 接。
1. 单击选 **[!UICONTROL Target of the proofs]** 项卡。
1. 单击字 **[!UICONTROL Targeting mode]** 段以选择要应用的方法： **[!UICONTROL Definition of a specific proof target]** 、 **[!UICONTROL Substitution of the address]****[!UICONTROL Seed addresses]** 或 **[!UICONTROL Specific target and seed addresses]**。

>[!NOTE]
>
>通常，证明的目标可以添加到主目标。 为此，请在选项卡的下半部分选择相应的选 **[!UICONTROL Main target]** 项。

## 定义特定证明目标 {#defining-a-specific-proof-target}

在选择校样目标时，可 **[!UICONTROL Definition of a specific proof target]** 以通过此选项从数据库中的配置文件中选择校样收件人。

选择此选项可使用按钮选 **[!UICONTROL Add]** 择收件人，如定义主目标一样。 请参 [阅选择主目标](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target)。

![](assets/s_ncs_user_wizard_email01_143.png)

For more on proof sending, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### 在校样中使用地址替换 {#using-address-substitution-in-proof}

您可以使用此选项，而不是在数据库中选择专用收 **[!UICONTROL Substitution of the address]** 件人。

通过此选项，您可以使用递送的收件人配置文件，并将其电子邮件地址替换为一个或多个将接收证明的其他地址。

选择此选项后，将通过特殊编辑器填写证明地址，该编辑器允许您配置替换。

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

配置的执行方式如下：

1. 单击图 **[!UICONTROL Add]** 标以定义替代。
1. 输入要使用的收件人地址，或从列表中选择它。
1. 选择要在校样中使用的配置文件：将值保 **[!UICONTROL Random]** 存在列中， **[!UICONTROL Profile to use]** 以使用校样中目标配置文件的数据。

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. 单击 **[!UICONTROL Detail]** 该图标以从主目标中选择配置文件，如下例所示：

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   您可以根据需要定义任意数量的替换地址。

## 以种子地址为证明 {#using-seed-addresses-as-proof}

您可以 **[!UICONTROL Seed addresses]** 用作校样的目标：此选项允许您使用或导入现有种子地址列表。

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>种子地址显示在“关于 [种子地址”中](../../delivery/using/about-seed-addresses.md)。

您可以使用此选项将特定证明目标的定义和种子地址的使用结合 **[!UICONTROL Specific target and Seed addresses]** 起来。 相关配置随后在两个单独的子标签中定义。
