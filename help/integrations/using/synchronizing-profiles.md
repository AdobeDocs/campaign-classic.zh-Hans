---
title: 同步用户档案
seo-title: 同步用户档案
description: 同步用户档案
seo-description: null
page-status-flag: never-activated
uuid: 3d5f0fd4-dfe7-4b34-a75f-8cf36fb7c91d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 91115d4f-0cb6-4bce-b28d-17f15e9f9a0a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 56212b320d5077f9b66952e7c11eb8bdcea9e3b4
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 0%

---


# 同步用户档案{#synchronizing-profiles}

ACS连接器将活动v7复制到Campaign Standard。 从活动v7接收的数据可用于Campaign Standard以创建投放。 您可以通过执行下面列出的操作，了解用户档案的同步方式。

* **添加新收件人**: 在活动v7中新建一个收件人，并确认相应用户档案已复制到Campaign Standard。 请参 [阅创建新收件人](#creating-a-new-recipient)。
* **更新收件人**: 在活动v7中编辑新收件人，在Campaign Standard中视图相应用户档案，以确认已复制更新。 请参 [阅编辑收件人](#editing-a-recipient)。
* **在Campaign Standard中构建工作流**: 在Campaign Standard中创建一个工作流，其中包括一个查询，该受众或用户档案从活动v7复制。 请参 [阅创建工作流](#creating-a-workflow)。
* **在Campaign Standard中创建投放**: 按照工作流完成以发送投放。 请参 [阅创建投放](#creating-a-delivery)。
* **验证退订链接**: 使用活动v7 Web应用程序确保收件人选择取消订阅服务会发送到活动v7数据库。 停止接收服务的选项被复制到Campaign Standard。 请参 [阅更改退订链接](#changing-the-unsubscription-link)。

## 先决条件 {#prerequisites}

以下各节介绍ACS连接器如何帮助您在活动v7中添加和编辑收件人，然后在Campaign Standard投放中使用它们。 ACS连接器要求：

* 活动v7中的收件人已复制到Campaign Standard。
* 在活动v7和Campaign Standard中执行工作流的用户权限。
* 用户在Campaign Standard中创建和执行投放的权限。

## 更改退订链接 {#changing-the-unsubscription-link}

当收件人单击Campaign Standard发送的电子邮件中的退订链接时，Campaign Standard中的相应用户档案会更新。 要确保复制用户档案包括用户取消订阅服务的选择，必须将该信息发送到活动v7，而不是Campaign Standard。 要执行更改，退订服务链接到活动v7 Web应用程序，而不是Campaign Standard。

>[!NOTE]
>
>请咨询顾问为退订服务配置Web应用程序，然后执行以下步骤。

## Creating a new recipient {#creating-a-new-recipient}

1. 在活动v7中创建新收件人，以复制到Campaign Standard。 输入尽可能多的信息，包括收件人的姓、名、电子邮件地址和邮政地址。 但是，不要选择 **[!UICONTROL Salutation]** ，因为它将添加到下一节编辑 [收件人中](#editing-a-recipient)。 有关详细信息，请参 [阅添加收件人](../../platform/using/adding-profiles.md)。

   ![](assets/acs_connect_profile_sync_01.png)

1. 确认已将新收件人添加到Campaign Standard。 在查看用户档案时，请确保您在活动v7中输入的数据也在Campaign Standard中可用。 要了解在Campaign Standard中查找用户档案的位置，请参阅导 [航基础](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_02.png)

   默认情况下，ACS连接器的定期复制每15分钟一次。 有关详细信息，请参 [阅数据复制](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)。

## 编辑收件人 {#editing-a-recipient}

以下用于更改单点优惠的步骤是活动v7在使用数据复制时如何成为Campaign Standard的主数据库的一个简单示例。 在活动v7中修改或删除复制的数据对Campaign Standard中的相应数据具有相同的影响。

1. 从“创建新收件人” [中选择新创建的收件人](#creating-a-new-recipient) ，然后编辑收件人的名称。 例如，为收件人 **[!UICONTROL Salutation]** （例如，“先生”或“太太”）选择一个。 有关详细信息，请参 [阅编辑用户档案](../../platform/using/editing-a-profile.md)。

   ![](assets/acs_connect_profile_sync_03.png)

1. 确认收件人的名称已在Campaign Standard中更新。 要了解在Campaign Standard中查找用户档案的位置，请参阅导 [航基础](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_04.png)

   默认情况下，ACS连接器的定期复制每15分钟一次。 有关详细信息，请参 [阅数据复制](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)。

## 创建工作流 {#creating-a-workflow}

从活动v7复制的用户档案和服务可供数字营销人员利用Campaign Standard中的丰富数据。 下面的说明演示如何向查询工作流中添加Campaign Standard，然后将其与复制的数据库一起使用。

有关Campaign Standard工作流的更多信息和完整说明，请参阅 [工作流](../../workflow/using/about-workflows.md)。

1. 转到Campaign Standard并单击 **[!UICONTROL Marketing Activities]**。
1. 单击 **[!UICONTROL Create]** 右上角的。
1. 单击 **[!UICONTROL Workflow]**.
1. 单击 **[!UICONTROL New workflow]** 并 **[!UICONTROL Next]**。
1. 在字段中输入工作流的名称， **[!UICONTROL Label]** 并根据需要输入其他信息。 单击 **[!UICONTROL Next]**.
1. 从 **[!UICONTROL Targeting]** 左侧将目标拖 **[!UICONTROL Query]** 动到工作区。

   ![](assets/acs_connect_profile_sync_05.png)

1. 多次单 **[!UICONTROL Query]** 击活动，然后选择可与复制的数据库一起使用的参数。 例如，您可以：

   * 拖动 **[!UICONTROL Profiles]** 到工作区。 使用字段下拉菜单选择 **[!UICONTROL Is external resource]** 查找从活动v7复制的用户档案。
   * 拖动其他查询参数以进一步目标复制的用户档案。

## 创建投放 {#creating-a-delivery}

>[!NOTE]
>
>创建投放的说明继续从创建工作流 [开始的工作流](#creating-a-workflow)。

数字营销人员可以利用活动v7 Web应用程序确保收件人选择取消订阅服务会发送到活动v7数据库。 收件人单击退订链接后，停止接收服务的选项将从活动v7复制到Campaign Standard。 有关其他详细信息，请 [参阅更改退订链接](#changing-the-unsubscription-link)。

按照以下步骤，使用在活动v7中创建的投放服务将电子邮件退订添加到现有工作流。 有关Campaign Standard工作流的更多信息和完整说明，请参阅此 [文档](../../workflow/using/about-workflows.md)。

>[!NOTE]
>
>请咨询顾问为退订服务配置Web应用程序，然后执行以下步骤。

1. 单 **[!UICONTROL Channels]** 击左侧。
1. 拖动 **[!UICONTROL Email delivery]** 到工作区中的现有工作流。

   ![](assets/acs_connect_profile_sync_07.png)

1. 多次单击 **[!UICONTROL Email delivery]** 活动，然后 **[!UICONTROL Single send email]** 选择或 **[!UICONTROL Recurring email]**。 选择您的选项，然后单击 **[!UICONTROL Next]**。
1. 单击 **[!UICONTROL Send via email]** 并单击 **[!UICONTROL Next]**。

   ![](assets/acs_connect_profile_sync_08.png)

1. 在字段中输入投放的名称， **[!UICONTROL Label]** 并根据需要输入其他信息。 单击 **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_09.png)

1. 在字段 **[!UICONTROL Subject]** 中，输入将显示在收件人电子邮件收件箱中的主题。
1. 单 **[!UICONTROL Change content]** 击以添加HTML模板。

   ![](assets/acs_connect_profile_sync_10.png)

1. 选择包含该链接的内容以取消订阅服务。 单击 **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_11.png)

1. 当前退订链接必须替换为使用顾问创建的Web应用程序的新链接。 找到电子邮件内容底部的退订链接，然后单击一次。 单击垃圾桶图标以删除链接。

   ![](assets/acs_connect_profile_sync_12.png)

1. 单击同一内容区域，然后键入 **退订链接**。

   ![](assets/acs_connect_profile_sync_13.png)

1. 用光标高亮显示文本，然后单击链图标。
1. 单击 **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_profile_sync_14.png)

1. 单击文件夹图标以选择登陆页。

   ![](assets/acs_connect_profile_sync_15.png)

1. 选择由顾问创建的Web应用程序，然后单击 **[!UICONTROL Confirm]**。

   ![](assets/acs_connect_profile_sync_16.png)

1. 单击 **[!UICONTROL Create]**.
1. 单击投放名称，返回工作流。

   ![](assets/acs_connect_profile_sync_17.png)

1. 单击 **[!UICONTROL Start]** 以发送投放。 电子邮件投放图标会闪烁，指示正在为投放准备。

   ![](assets/acs_connect_profile_sync_18.png)

1. 多次单击 **[!UICONTROL Email delivery]** 渠道，然 **[!UICONTROL Confirm]** 后选择发送电子邮件。 单击 **[!UICONTROL OK]** 以发送消息。

   ![](assets/acs_connect_profile_sync_19.png)

## 验证退订服务 {#verifying-the-unsubscription-service}

请按照创建工 [作流和](#creating-a-workflow)[创建投放中的说](#creating-a-delivery) 明进行操作，然后转到以下步骤。

1. 收件人单击电子邮件投放中的退订链接。

   ![](assets/acs_connect_profile_sync_20.png)

1. 收件人确认退订。

   ![](assets/acs_connect_profile_sync_21.png)

1. 更新活动v7中的收件人数据，以反映用户已取消订阅。 确认已选中 **[!UICONTROL No longer contact (by any channel)]** 该框以查找收件人。 要了解如何在v7视图中活动收件人，请参 [阅编辑用户档案](../../platform/using/editing-a-profile.md)。

   ![](assets/acs_connect_profile_sync_22.png)

1. 转到Campaign Standard并打开收件人的用户档案详细信息。 确认复选框在旁边出现 **[!UICONTROL No longer contact (by any channel)]**。 要了解在Campaign Standard中查找用户档案的位置，请参阅导 [航基础](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_23.png)

