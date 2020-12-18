---
solution: Campaign Classic
product: campaign
title: 同步用户档案
description: 同步用户档案
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 3%

---


# 同步用户档案{#synchronizing-profiles}

ACS连接器将活动v7复制到Campaign Standard。 从活动v7接收的数据可用于Campaign Standard以创建投放。 您可以通过执行下面列出的操作，了解用户档案的同步方式。

* **添加新收件人**:在活动v7中新建一个收件人，并确认相应用户档案已复制到Campaign Standard。请参阅[创建新收件人](#creating-a-new-recipient)。
* **更新收件人**:在活动v7中编辑新收件人，在Campaign Standard中视图相应用户档案，以确认已复制更新。请参阅[编辑收件人](#editing-a-recipient)。
* **在Campaign Standard中构建工作流**:在Campaign Standard中创建一个工作流，其中包括一个查询，该受众或用户档案从活动v7复制。请参阅[创建工作流](#creating-a-workflow)。
* **在Campaign Standard中创建投放**:按照工作流完成以发送投放。请参阅[创建投放](#creating-a-delivery)。
* **验证退订链接**:使用活动v7 Web应用程序确保收件人选择取消订阅服务会发送到活动v7数据库。停止接收服务的选项被复制到Campaign Standard。 请参阅[更改退订链接](#changing-the-unsubscription-link)。

## 先决条件{#prerequisites}

以下各节介绍ACS连接器如何帮助您在活动v7中添加和编辑收件人，然后在Campaign Standard投放中使用它们。 ACS连接器要求：

* 活动v7中的收件人已复制到Campaign Standard。
* 在活动v7和Campaign Standard中执行工作流的用户权限。
* 用户在Campaign Standard中创建和执行投放的权限。

## 更改退订链接{#changing-the-unsubscription-link}

当收件人单击Campaign Standard发送的电子邮件中的退订链接时，Campaign Standard中的相应用户档案会更新。 要确保复制用户档案包括用户取消订阅服务的选择，必须将该信息发送到活动v7，而不是Campaign Standard。 要执行更改，退订服务链接到活动v7 Web应用程序，而不是Campaign Standard。

>[!NOTE]
>
>请咨询顾问为退订服务配置Web应用程序，然后执行以下步骤。

## 创建新收件人{#creating-a-new-recipient}

1. 在活动v7中创建新收件人，以复制到Campaign Standard。 输入尽可能多的信息，包括收件人的姓、名、电子邮件地址和邮政地址。 但是，不要选择&#x200B;**[!UICONTROL Salutation]**，因为它将添加到下一节[编辑收件人](#editing-a-recipient)中。 有关详细信息，请参阅[添加收件人](../../platform/using/adding-profiles.md)。

   ![](assets/acs_connect_profile_sync_01.png)

1. 确认已将新收件人添加到Campaign Standard。 在查看用户档案时，请确保您在活动v7中输入的数据也在Campaign Standard中可用。 要了解在Campaign Standard中查找用户档案的位置，请参阅[导航基础知识](https://docs.adobe.com/content/help/zh-Hans/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_02.png)

   默认情况下，ACS连接器的定期复制每15分钟一次。 有关详细信息，请参阅[数据复制](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)。

## 编辑收件人{#editing-a-recipient}

以下用于更改单点优惠的步骤是活动v7在使用数据复制时如何成为Campaign Standard的主数据库的一个简单示例。 在活动v7中修改或删除复制的数据对Campaign Standard中的相应数据具有相同的影响。

1. 从[创建新收件人](#creating-a-new-recipient)中选择新创建的收件人，并编辑收件人的名称。 例如，为收件人选择&#x200B;**[!UICONTROL Salutation]**（例如，Mr或Mrs）。 有关详细信息，请参阅[编辑用户档案](../../platform/using/editing-a-profile.md)。

   ![](assets/acs_connect_profile_sync_03.png)

1. 确认收件人的名称已在Campaign Standard中更新。 要了解在Campaign Standard中查找用户档案的位置，请参阅[导航基础知识](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_04.png)

   默认情况下，ACS连接器的定期复制每15分钟一次。 有关详细信息，请参阅[数据复制](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)。

## 创建工作流{#creating-a-workflow}

从活动v7复制的用户档案和服务可供数字营销人员利用Campaign Standard中的丰富数据。 下面的说明演示如何向查询工作流中添加Campaign Standard，然后将其与复制的数据库一起使用。

有关Campaign Standard工作流的详细信息和完整说明，请参见[工作流](../../workflow/using/about-workflows.md)。

1. 转至Campaign Standard并单击&#x200B;**[!UICONTROL Marketing Activities]**。
1. 单击右上角的&#x200B;**[!UICONTROL Create]**。
1. 单击 **[!UICONTROL Workflow]**.
1. 单击&#x200B;**[!UICONTROL New workflow]**&#x200B;和&#x200B;**[!UICONTROL Next]**。
1. 在&#x200B;**[!UICONTROL Label]**&#x200B;字段中输入工作流的名称，并根据需要输入其他信息。 单击 **[!UICONTROL Next]**.
1. 从左侧的&#x200B;**[!UICONTROL Targeting]**&#x200B;将&#x200B;**[!UICONTROL Query]**&#x200B;目标拖动到工作区。

   ![](assets/acs_connect_profile_sync_05.png)

1. 多次单击&#x200B;**[!UICONTROL Query]**&#x200B;活动，然后选择可用于复制数据库的参数。 例如，您可以：

   * 将&#x200B;**[!UICONTROL Profiles]**&#x200B;拖动到工作区。 使用字段下拉菜单选择&#x200B;**[!UICONTROL Is external resource]**&#x200B;以查找从活动v7复制的用户档案。
   * 拖动其他查询参数以进一步目标复制的用户档案。

## 创建投放{#creating-a-delivery}

>[!NOTE]
>
>创建投放的说明继续从[创建工作流](#creating-a-workflow)开始的工作流。

数字营销人员可以利用活动v7 Web应用程序确保收件人选择取消订阅服务会发送到活动v7数据库。 收件人单击退订链接后，停止接收服务的选项将从活动v7复制到Campaign Standard。 有关其他详细信息，请参阅[更改退订链接](#changing-the-unsubscription-link)。

按照以下步骤，使用在活动v7中创建的投放服务将电子邮件退订添加到现有工作流。 有关Campaign Standard工作流的详细信息和完整说明，请参阅此[文档](../../workflow/using/about-workflows.md)。

>[!NOTE]
>
>请咨询顾问为退订服务配置Web应用程序，然后执行以下步骤。

1. 单击左侧的&#x200B;**[!UICONTROL Channels]**。
1. 将&#x200B;**[!UICONTROL Email delivery]**&#x200B;拖动到工作区中的现有工作流。

   ![](assets/acs_connect_profile_sync_07.png)

1. 多次单击&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动并选择&#x200B;**[!UICONTROL Single send email]**&#x200B;或&#x200B;**[!UICONTROL Recurring email]**。 选择您的选项，然后单击&#x200B;**[!UICONTROL Next]**。
1. 单击&#x200B;**[!UICONTROL Send via email]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/acs_connect_profile_sync_08.png)

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;字段中输入投放的名称，并根据需要输入其他信息。 单击 **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_09.png)

1. 在&#x200B;**[!UICONTROL Subject]**&#x200B;字段中，输入将在收件人的电子邮件收件箱中显示的主题。
1. 单击&#x200B;**[!UICONTROL Change content]**&#x200B;添加HTML模板。

   ![](assets/acs_connect_profile_sync_10.png)

1. 选择包含该链接的内容以取消订阅服务。 单击 **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_11.png)

1. 当前退订链接必须替换为使用顾问创建的Web应用程序的新链接。 找到电子邮件内容底部的退订链接，然后单击一次。 单击垃圾桶图标以删除链接。

   ![](assets/acs_connect_profile_sync_12.png)

1. 单击同一内容区域，然后键入&#x200B;**退订链接**。

   ![](assets/acs_connect_profile_sync_13.png)

1. 用光标高亮显示文本，然后单击链图标。
1. 单击 **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_profile_sync_14.png)

1. 单击文件夹图标以选择登陆页。

   ![](assets/acs_connect_profile_sync_15.png)

1. 选择由顾问创建的Web应用程序，然后单击&#x200B;**[!UICONTROL Confirm]**。

   ![](assets/acs_connect_profile_sync_16.png)

1. 单击 **[!UICONTROL Create]**.
1. 单击投放名称，返回工作流。

   ![](assets/acs_connect_profile_sync_17.png)

1. 单击&#x200B;**[!UICONTROL Start]**&#x200B;发送投放。 电子邮件投放图标会闪烁，指示正在为投放准备。

   ![](assets/acs_connect_profile_sync_18.png)

1. 多次单击&#x200B;**[!UICONTROL Email delivery]**&#x200B;渠道，然后选择&#x200B;**[!UICONTROL Confirm]**&#x200B;以发送电子邮件。 单击&#x200B;**[!UICONTROL OK]**&#x200B;发送消息。

   ![](assets/acs_connect_profile_sync_19.png)

## 验证退订服务{#verifying-the-unsubscription-service}

请按照[创建工作流](#creating-a-workflow)和[创建投放](#creating-a-delivery)中的说明操作，然后转到以下步骤。

1. 收件人单击电子邮件投放中的退订链接。

   ![](assets/acs_connect_profile_sync_20.png)

1. 收件人确认退订。

   ![](assets/acs_connect_profile_sync_21.png)

1. 更新活动v7中的收件人数据，以反映用户已取消订阅。 确认已检查框&#x200B;**[!UICONTROL No longer contact (by any channel)]**&#x200B;是否有收件人。 要了解如何在活动v7中视图收件人，请参阅[编辑用户档案](../../platform/using/editing-a-profile.md)。

   ![](assets/acs_connect_profile_sync_22.png)

1. 转到Campaign Standard并打开收件人的用户档案详细信息。 确认在&#x200B;**[!UICONTROL No longer contact (by any channel)]**&#x200B;旁边显示复选框。 要了解在Campaign Standard中查找用户档案的位置，请参阅[导航基础知识](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_23.png)

