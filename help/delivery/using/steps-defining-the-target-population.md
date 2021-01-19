---
solution: Campaign Classic
product: campaign
title: 定义目标群体
description: 定义目标群体
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '1579'
ht-degree: 2%

---


# 定义目标群体 {#defining-the-target-population}

## 关于目标群{#about-target-populations}

对于每个投放，您可以定义几种类型的目标群体。 以下部分提供有关如何选择的更多信息：

* 投放的主要收件人。 [阅读更多](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target)
* 收件人验证消息，以设置验证周期。 [阅读更多](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)

此外，如果投放包含在营销活动中，您还可以定义[种子地址](../../delivery/using/about-seed-addresses.md)和[对照组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

## 选择投放{#selecting-the-main-target}的主要收件人

在大多数情况下，主目标会从Adobe Campaign数据库中提取（默认模式）。 但是，收件人也可以存储在外部文件中。 请阅读[本节](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)了解更多信息。

要选择收件人，请按照以下步骤操作：

1. 在投放编辑器中，选择&#x200B;**[!UICONTROL To]**。
1. 如果收件人存储在数据库中，请选择第一个选项。

   ![](assets/s_ncs_user_wizard_email02a.png)

1. 在&#x200B;**[!UICONTROL Target mapping]**&#x200B;下拉目标映射中选择列表。 Adobe Campaign默认目标映射为&#x200B;**[!UICONTROL Recipients]**，基于&#x200B;**nms:收件人**&#x200B;模式。

   其他目标映射可用，有些可能与您的特定配置相关。 有关目标映射的详细信息，请参阅[选择目标映射](../../delivery/using/selecting-a-target-mapping.md)。

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮定义限制过滤器。

   然后，您可以选择要应用的筛选类型：

   ![](assets/s_ncs_user_wizard_email02b.png)

   您可以使用收件人库中定义的定位类型选择定位。 要使用目标类型，请选择该类型，然后单击&#x200B;**[!UICONTROL Next]**。 对于每个目标，可以单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡来显示相关收件人。 对于某些类型的目标,**[!UICONTROL Refine target]**&#x200B;按钮允许您组合多个定位条件。

   默认情况下，提供以下目标类型：

   * **[!UICONTROL Filtering conditions]** :此选项允许您定义查询并显示结果。定义查询的方法在[本节](../../platform/using/creating-filters.md#creating-an-advanced-filter)中介绍。
   * **[!UICONTROL Subscribers of an information service]** :通过此选项，您可以选择收件人必须订阅到的新闻稿，以便由创建的投放定位。

      ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** :此选项允许您将现有收件人的投放定义为定位标准。然后，您必须在投放中选择列表:

      ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** :通过此选项，您可以选择投放文件夹，并目标该文件夹中的投放的收件人。

      ![](assets/s_ncs_user_wizard_email02e.png)

      您可以通过从下拉收件人中进行选择来筛选列表的行为：

      ![](assets/s_ncs_user_wizard_email02f.png)

      >[!NOTE]
      >
      >**[!UICONTROL Include sub-folders]**&#x200B;选项还允许您目标包含在选定节点下树结构中文件夹中的投放。

   * **[!UICONTROL Recipients included in a folder]** :通过此选项，可以目标树的特定文件夹中包含的用户档案。
   * **[!UICONTROL A recipient]** :通过此选项，您可以从收件人库的用户档案中选择特定的数据。
   * **[!UICONTROL A list of recipients]** :此选项允许您目标一列表收件人。列表显示在[此部分](../../platform/using/creating-and-managing-lists.md)中。
   * **[!UICONTROL User filters]** :通过此选项，您可以访问预配置的过滤器，将其用作用户档案库中的筛选条件。预配置的过滤器显示在[此部分](../../platform/using/creating-filters.md#saving-a-filter)中。
   * 通过选项&#x200B;**[!UICONTROL Exclude recipients corresponding to this segment]**&#x200B;可以目标不满足定义的目标条件的收件人。 要使用此选项，请选择相应的框，然后应用定位（如前面所定义）以排除生成的用户档案。

      ![](assets/s_ncs_user_wizard_email02g.png)

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;字段中输入此定位的名称。 默认情况下，该标签将是第一个定位标准的标签。 对于组合，最好使用显式名称。
1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;验证所配置的定位。

   定义的定位条件在主目标配置选项卡的中央部分进行汇总。 单击一个标准以视图其内容(配置和预览)。 要删除标准，请单击其标签后的叉。

   ![](assets/s_ncs_user_wizard_email02h.png)

### 选择外部收件人{#selecting-external-recipients}

可以对未保存在收件人库中但存储在外部文件中的启动投放。 例如，我们将在此处向从文本文件导入的投放发送一个收件人。

操作步骤：

1. 单击&#x200B;**[!UICONTROL To]**&#x200B;链接以选择您的收件人。
1. 选择&#x200B;**[!UICONTROL Defined in an external file]**&#x200B;选项。

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. 默认情况下，收件人会导入数据库。 必须选择&#x200B;**[!UICONTROL Target mapping]**。 有关目标映射的详细信息，请参阅[选择目标映射](../../delivery/using/selecting-a-target-mapping.md)

   您也可以选择&#x200B;**[!UICONTROL Do not import the recipients into the database]**。

1. 导入收件人时，单击&#x200B;**[!UICONTROL File format definition...]**&#x200B;链接以选择和配置外部文件。

   有关数据导入的详细信息，请参阅[本节](../../platform/using/executing-import-jobs.md#step-2---source-file-selection)。

1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;并将投放配置为标准投放。

>[!CAUTION]
>
>在为电子邮件投放定义邮件内容时，不要包含指向镜像页面的链接；无法在此投放模式下生成。

### 设置排除设置{#customizing-exclusion-settings}

地址错误和质量等级由服务提供商(IAP)提供。 此信息会在收件人用户档案中根据投放操作和服务提供商返回的文件自动更新。 可以在用户档案中以只读方式查看。

您可以选择排除已达到特定数量连续错误或质量等级低于此窗口中指定阈值的地址。 您还可以选择是否对尚未返回数据的未限定地址授权。

>[!NOTE]
>
>如果两个收件人在直接邮件投放中具有相同的名字、姓氏、邮戳和城市，则将发生多次错误，并且不会考虑重复。

**[!UICONTROL Exclusions]**&#x200B;选项卡用于限制消息数。

>[!NOTE]
>
>建议使用默认参数，但您可以根据需要调整设置。 但是，这些选项只应由专家用户更改，以避免任何误用和错误。

单击&#x200B;**[!UICONTROL Edit...]**&#x200B;链接以修改默认配置。

![](assets/s_ncs_user_wizard_email02i.png)

可以使用以下选项：

* **[!UICONTROL Exclude duplicate addresses during delivery]**.此选项默认处于活动状态：它允许您在投放期间删除重复电子邮件地址。 所应用的策略可能因Adobe Campaign的使用方式和数据库中数据的类型而异。

   可以为每个投放模板配置选项的默认值。

   例如：

   * 投放新闻稿或电子文档投放。 在某些情况下，如果重复没有本机重复，则不排除该数据。 订阅同一电子邮件地址的夫妇可能会收到两条特定的个性化电子邮件：每个人的姓名。 在这种情况下，可以取消选择此选项。
   * 营销投放活动:重复排除对于避免向同一收件人发送过多消息至关重要。 在这种情况下，可以选择此选项。

      如果取消选择此选项，则可以访问其他选项：**[!UICONTROL Keep duplicate records (same identifier)]**。 它允许您为满足多个定位标准的投放授权多个收件人。

      ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** ，即其电子邮件地址在收件人阻止列表(&#39;选择退出&#39;)的为了遵守电子营销的职业道德和电子商务法律，必须继续选择此选项。
* **[!UICONTROL Exclude quarantined recipients]**.此选项允许您从目标中排除任何地址没有响应的用户档案。 我们强烈建议保持选中此选项。

   >[!NOTE]
   >
   >有关隔离管理的详细信息，请参阅[了解隔离管理](../../delivery/using/understanding-quarantine-management.md)。

* **[!UICONTROL Limit delivery]** 到给定数量的消息。通过此选项，可输入要发送的消息的最大数量。 如果目标的内容超过所指示的消息数，则随机选择被应用到目标。

### 缩小目标群{#reducing-the-size-of-the-target-population}

你可以缩小目标群。 为此，请在&#x200B;**[!UICONTROL Requested quantity]**&#x200B;字段中指定要导出的收件人数。

![](assets/s_ncs_user_edit_del_exe_tab.png)

## 选择收件人验证消息{#selecting-the-proof-target}

验证是一条特殊消息，允许您在将投放发送到主目标之前测试该。 验证收件人负责批准邮件的表单和内容。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#seeds-and-proofs-video)


要选择目标，请按照以下步骤操作：

1. 单击&#x200B;**[!UICONTROL To]**&#x200B;链接。
1. 单击&#x200B;**[!UICONTROL Target of the proofs]**&#x200B;选项卡。
1. 单击&#x200B;**[!UICONTROL Targeting mode]**&#x200B;字段以选择要应用的方法：**[!UICONTROL Definition of a specific proof target]**、**[!UICONTROL Substitution of the address]**、**[!UICONTROL Seed addresses]**&#x200B;或&#x200B;**[!UICONTROL Specific target and seed addresses]**。

>[!NOTE]
>
>通常，验证的目标可以添加到主目标。 为此，请在&#x200B;**[!UICONTROL Main target]**&#x200B;选项卡的下半部分选择相应的选项。

## 定义特定验证目标{#defining-a-specific-proof-target}

选择验证目标时，**[!UICONTROL Definition of a specific proof target]**&#x200B;选项允许您从数据库中的用户档案中选择验证收件人。

选择此选项可使用&#x200B;**[!UICONTROL Add]**&#x200B;按钮选择收件人，如定义主目标。 请参阅[选择主目标](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target)。

![](assets/s_ncs_user_wizard_email01_143.png)

有关验证发送的详细信息，请参阅[此部分](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 在验证{#using-address-substitution-in-proof}中使用地址替换

您可以使用&#x200B;**[!UICONTROL Substitution of the address]**&#x200B;选项，而不是在收件人库中选择专用的。

此选项允许您使用收件人的用户档案，并将其电子邮件地址替换为一个或多个将接收验证的其他地址。

选择此选项后，将通过一个特殊编辑器填写验证地址，该编辑器允许您配置替代。

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

配置的执行方式如下：

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;图标以定义替代。
1. 输入要使用的收件人地址，或从列表中选择它。
1. 选择要在用户档案中使用的验证:在&#x200B;**[!UICONTROL Profile to use]**&#x200B;列中保存&#x200B;**[!UICONTROL Random]**&#x200B;值，以使用验证中用户档案的任何目标的数据。

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. 单击&#x200B;**[!UICONTROL Detail]**&#x200B;图标以从主用户档案中选择目标，如以下示例所示：

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   您可以根据需要定义任意数量的替换地址。

## 将种子地址用作验证{#using-seed-addresses-as-proof}

可以使用&#x200B;**[!UICONTROL Seed addresses]**&#x200B;作为目标验证:此选项允许您使用或导入现有列表的种子地址。

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>种子地址显示在[关于种子地址](../../delivery/using/about-seed-addresses.md)中。

您可以使用&#x200B;**[!UICONTROL Specific target and Seed addresses]**&#x200B;选项组合特定验证目标的定义和种子地址的使用。 相关配置随后在两个单独的子标签中定义。

另请参阅：

* [选择验证目标](#selecting-the-proof-target)
* [关于种子地址](../../delivery/using/about-seed-addresses.md)
* [用例：根据条件选择种子地址](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

## 教程视频{#seeds-and-proofs-video}

在此视频中，您将学习如何在现有电子邮件中添加种子和验证，以及如何发送。

>[!VIDEO](https://video.tv.adobe.com/v/25606?quality=12)

此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供其他Campaign Classic操作方法视频。[
