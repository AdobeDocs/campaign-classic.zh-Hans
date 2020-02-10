---
title: 同步配置文件
seo-title: 同步配置文件
description: 同步配置文件
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
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 同步配置文件{#synchronizing-profiles}

ACS Connector将数据从Campaign v7复制到Campaign Standard。 从Campaign v7接收的数据可在Campaign standard中用于创建分发。 您可以通过执行下面列出的操作来了解配置文件的同步方式。

* **添加新收件人**:在Campaign v7中创建新收件人，并确认相应的配置文件已复制到Campaign Standard。 请参 [阅创建新收件人](#creating-a-new-recipient)。
* **更新收件人**:在Campaign v7中编辑新收件人，并在Campaign standard中查看相应的配置文件，以确认更新已复制。 请参阅 [编辑收件人](#editing-a-recipient)。
* **在Campaign standard中构建工作流**:在Campaign standard中创建一个工作流，该工作流包含一个查询，该查询具有从Campaign v7复制的受众或配置文件。 请参 [阅创建工作流](#creating-a-workflow)。
* **在Campaign standard中创建分发**:按照工作流完成发送交付。 请参 [阅创建分发](#creating-a-delivery)。
* **验证取消订阅链接**:使用Campaign v7 web应用程序确保收件人选择取消订阅服务会发送到Campaign v7数据库。 停止接收服务的选项将复制到Campaign Standard。 请参 [阅更改取消订阅链接](#changing-the-unsubscription-link)。

## 先决条件 {#prerequisites}

以下各节介绍ACS Connector如何帮助您在Campaign v7中添加和编辑收件人，然后在Campaign standard交付中使用收件人。 ACS连接器需要：

* Campaign v7中的收件人已复制到Campaign Standard。
* 在Campaign v7和Campaign standard中执行工作流的用户权限。
* 在Campaign standard中创建和执行分发的用户权限。

## 更改取消订阅链接 {#changing-the-unsubscription-link}

当收件人单击Campaign standard发送的电子邮件中的取消订阅链接时，Campaign standard中的相应配置文件将更新。 要确保复制的配置文件包含用户选择的取消订阅服务，必须将该信息发送到Campaign v7，而不是Campaign Standard。 要执行更改，取消订阅服务将链接到Campaign v7 web应用程序，而不是Campaign Standard。

>[!NOTE]
>
>请咨询顾问为取消订阅服务配置Web应用程序，然后执行以下步骤。

## 创建新收件人 {#creating-a-new-recipient}

1. 在Campaign v7中创建一个新收件人，以便复制到Campaign Standard。 输入尽可能多的信息，包括收件人的姓、名、电子邮件地址和邮政地址。 但是，请勿选择收件人， **[!UICONTROL Salutation]** 因为该收件人将添加到下一节编辑收 [件人中](#editing-a-recipient)。 有关详细信息，请参阅 [添加收件人](../../platform/using/adding-profiles.md)。

   ![](assets/acs_connect_profile_sync_01.png)

1. 确认新收件人已添加到Campaign Standard。 查看配置文件时，请确保您在Campaign v7中输入的数据也在Campaign standard中可用。 要了解在Campaign standard中查找配置文件的位置，请参阅导 [航基础](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_02.png)

   默认情况下，ACS Connector的定期复制每15分钟一次。 有关详细信息，请参阅 [数据复制](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)。

## 编辑收件人 {#editing-a-recipient}

以下更改单点数据的步骤提供了一个简单的示例，说明在使用数据复制时，Campaign v7如何成为Campaign standard的主数据库。 在Campaign v7中修改或删除复制的数据对Campaign standard中的相应数据具有相同的效果。

1. 从创建新收件人中选 [择新创建的收件人](#creating-a-new-recipient) ，然后编辑收件人姓名。 例如，为收件人 **[!UICONTROL Salutation]** 选择一个（例如“mr.”或“mr.”）。 有关详细信息，请参 [阅编辑配置文件](../../platform/using/editing-a-profile.md)。

   ![](assets/acs_connect_profile_sync_03.png)

1. 确认收件人的姓名已在Campaign standard中更新。 要了解在Campaign standard中查找配置文件的位置，请参阅导 [航基础](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_04.png)

   默认情况下，ACS Connector的定期复制每15分钟一次。 有关详细信息，请参阅 [数据复制](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)。

## 创建工作流 {#creating-a-workflow}

数字营销人员可以使用从Campaign v7复制的档案和服务，以利用Campaign standard中的丰富数据。 以下说明演示如何向Campaign standard工作流中添加查询，然后将其与复制的数据库一起使用。

有关Campaign standard工作流程的更多信息和完整说明，请参阅工 [作流](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/about-workflows-and-data-management/workflow-data-and-processes.html)。

1. 转到Campaign Standard并单击 **[!UICONTROL Marketing Activities]**。
1. 单击 **[!UICONTROL Create]** 右上角的。
1. 单击 **[!UICONTROL Workflow]**.
1. 单击 **[!UICONTROL New workflow]** 并 **[!UICONTROL Next]**。
1. 在字段中输入工作流的名称，并 **[!UICONTROL Label]** 根据需要输入其他信息。 单击 **[!UICONTROL Next]**.
1. 从左 **[!UICONTROL Targeting]** 侧，将目标拖动 **[!UICONTROL Query]** 到工作区。

   ![](assets/acs_connect_profile_sync_05.png)

1. 双击活动 **[!UICONTROL Query]** 并选择可与复制的数据库一起使用的参数。 例如，您可以：

   * 拖动 **[!UICONTROL Profiles]** 到工作区。 使用字段下拉菜单选择查 **[!UICONTROL Is external resource]** 找从Campaign v7复制的配置文件。
   * 拖动其他查询参数以进一步定位复制的配置文件。

## 创建分发 {#creating-a-delivery}

>[!NOTE]
>
>创建交付的说明将继续从创建工作流 [开始的工作流](#creating-a-workflow)。

数字营销人员可以利用Campaign v7 web应用程序确保将收件人取消订阅服务的选择发送到Campaign v7数据库。 在收件人单击取消订阅链接后，停止接收服务的选项将从Campaign v7复制到Campaign Standard。 有关其他详细信息，请参 [阅更改取消订阅链接](#changing-the-unsubscription-link)。

按照以下步骤，使用在Campaign v7中创建的取消订阅服务将电子邮件分发添加到现有工作流。 有关Campaign standard工作流程的更多信息和完整说明，请参阅本 [文档](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/about-workflows-and-data-management/workflow-data-and-processes.html)。

>[!NOTE]
>
>请咨询顾问为取消订阅服务配置Web应用程序，然后执行以下步骤。

1. 单 **[!UICONTROL Channels]** 击左侧。
1. 拖动 **[!UICONTROL Email delivery]** 到工作区中的现有工作流。

   ![](assets/acs_connect_profile_sync_07.png)

1. 双击活动 **[!UICONTROL Email delivery]** 并选择 **[!UICONTROL Single send email]** 或 **[!UICONTROL Recurring email]**。 选择您的选项，然后单击 **[!UICONTROL Next]**。
1. 单击 **[!UICONTROL Send via email]** 并单击 **[!UICONTROL Next]**。

   ![](assets/acs_connect_profile_sync_08.png)

1. 在字段中输入传送的名称，并根据需要 **[!UICONTROL Label]** 输入其他信息。 单击 **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_09.png)

1. 在字段 **[!UICONTROL Subject]** 中，输入将显示在收件人电子邮件收件箱中的主题。
1. 单 **[!UICONTROL Change content]** 击以添加HTML模板。

   ![](assets/acs_connect_profile_sync_10.png)

1. 选择包含该链接的内容以取消订阅服务。 单击 **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_11.png)

1. 当前取消订阅链接必须替换为使用顾问创建的Web应用程序的新链接。 找到电子邮件内容底部的取消订阅链接，然后单击它一次。 单击垃圾桶图标以删除链接。

   ![](assets/acs_connect_profile_sync_12.png)

1. 在同一内容区域内单击，然后键入“取消 **订阅”链接**。

   ![](assets/acs_connect_profile_sync_13.png)

1. 用光标高亮显示文本，然后单击链图标。
1. 单击 **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_profile_sync_14.png)

1. 单击文件夹图标以选择登陆页面。

   ![](assets/acs_connect_profile_sync_15.png)

1. 选择由顾问创建的Web应用程序，然后单击 **[!UICONTROL Confirm]**。

   ![](assets/acs_connect_profile_sync_16.png)

1. 单击 **[!UICONTROL Create]**.
1. 单击传送名称以返回至工作流。

   ![](assets/acs_connect_profile_sync_17.png)

1. 单 **[!UICONTROL Start]** 击以发送分发。 电子邮件发送图标会闪烁以指示正在准备发送。

   ![](assets/acs_connect_profile_sync_18.png)

1. 双击渠道 **[!UICONTROL Email delivery]** 并选择发 **[!UICONTROL Confirm]** 送电子邮件。 单击 **[!UICONTROL OK]** 以发送消息。

   ![](assets/acs_connect_profile_sync_19.png)

## 验证取消订阅服务 {#verifying-the-unsubscription-service}

请按照创建工 [作流和创建交付](#creating-a-workflow)[中的说明操作](#creating-a-delivery) ，然后转到以下步骤。

1. 收件人单击电子邮件分发中的取消订阅链接。

   ![](assets/acs_connect_profile_sync_20.png)

1. 收件人确认取消订阅。

   ![](assets/acs_connect_profile_sync_21.png)

1. Campaign v7中的收件人数据将更新，以反映用户已取消订阅。 确认已为收件人 **[!UICONTROL No longer contact (by any channel)]** 选中该框。 要了解如何在Campaign v7中查看收件人，请参阅编 [辑配置文件](../../platform/using/editing-a-profile.md)。

   ![](assets/acs_connect_profile_sync_22.png)

1. 转到Campaign Standard并打开收件人的个人资料详细信息。 确认复选框显示在旁边 **[!UICONTROL No longer contact (by any channel)]**。 要了解在Campaign standard中查找配置文件的位置，请参阅导 [航基础](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_23.png)

