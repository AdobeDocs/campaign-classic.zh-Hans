---
title: Adobe Analytics Data Connector
seo-title: Adobe Analytics Data Connector
description: Adobe Analytics Data Connector
seo-description: null
page-status-flag: never-activated
uuid: 5a1de443-04de-49a8-9057-5d8381e48630
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: 5ff1577f-0809-46fd-ac1e-11b24637e35c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20174427735b90129cd4cbd9ee1ba5fd705fa302

---


# Adobe Analytics Data Connector{#adobe-analytics-data-connector}

## 关于Data Connector集成 {#about-data-connector-integration}

>[!CAUTION]
>
>Adobe Analytics Data Connector与Transactional Messaging(Message Center)不兼容。

Data Connector（以前称为Adobe Genesis）允许Adobe Campaign和Adobe Analytics通过 **Web Analytics连接器包进行交互** 。 它以区段形式将数据转发到Adobe Campaign，这些区段涉及电子邮件营销活动之后的用户行为。 相反，它会将Adobe Campaign提供的电子邮件营销活动的指标和属性发送到Adobe Analytics - Data connector。

使用数据连接器，Adobe Campaign可以衡量Internet受众（Web分析）。 借助这些集成，Adobe Campaign可以恢复营销活动后一个或多个站点的访客行为数据，并（分析后）运行再营销活动以将其转换为购买者。 相反，Web分析工具使Adobe Campaign能够将指标和营销活动属性转发到其平台。

有关实施Adobe Analytics与Adobe Campaign集成的更多信息，请参阅本 [文档](https://helpx.adobe.com/marketing-cloud/how-to/analytics-ac.html)。

每个工具的操作字段如下所示：

* Web分析的角色：

   1. 标记使用Adobe Campaign启动的电子邮件营销活动，
   1. 以区段的形式保存收件人在单击营销活动电子邮件后浏览的站点上的行为。 区段涉及放弃的产品（已查看但未添加到购物车或购买）、购买或放弃购物车。

* Adobe Campaign的角色：

   1. 将指示器和营销活动属性发送到连接器，连接器将指示器和营销活动属性转发到网络分析工具，
   1. 恢复和分析细分，
   1. 触发再营销活动。

## 设置集成 {#setting-up-the-integration}

要设置数据连接器，必须连接到Adobe Campaign实例并执行以下操作：

* [第1步：在Analytics中配置集成](#step-1--configure-integration-in-analytics)
* [第2步：在Campaign中创建外部帐户](#step-2--create-the-external-account-in-campaign)
* [第3步：同步Adobe Campaign和Adobe Analytics](#step-3--synchronize-adobe-campaign-and-adobe-analytics)

### 第1步：在Analytics中配置集成 {#step-1--configure-integration-in-analytics}

以下步骤使用向导详细说明了数据连接器的配置。

1. 使用Adobe ID或Enterprise ID登录到Adobe Experience Cloud。

   ![](assets/adobe_genesis_install_001.png)

1. 从Experience cloud解决方案列表中，选择 **[!UICONTROL Analytics]**。

   ![](assets/adobe_genesis_install_013.png)

1. 从选项卡 **[!UICONTROL Admin]** 中，选择 **[!UICONTROL Data Connectors]**。

   ![](assets/adobe_genesis_install_002.png)

1. 从合作伙伴列表中，选择 **[!UICONTROL Neolane - Enterprise Marketing Platform]**。

   ![](assets/adobe_genesis_install_014.png)

1. 在对话 **[!UICONTROL Add integration]** 框中，单击 **[!UICONTROL Activate]**。
1. 选中 **[!UICONTROL I accept these terms and conditions]** 并选择与此集 **[!UICONTROL Report suite]** 成相链接的，然后输入连接器标签。

   完成后，单击 **[!UICONTROL Create and configure this integration]**。

   ![](assets/adobe_genesis_install_015.png)

1. 输入将代表连接器接收通知的电子邮件地址，然后复制其在外部Adobe Campaign帐户中显示的状态(有关详细信息，请参阅 **[!UICONTROL Account ID]**[&#x200B;步骤2:在Campaign中创建外部帐户](#step-2--create-the-external-account-in-campaign))。

   ![](assets/adobe_genesis_install_005.png)

1. 指定测量电子邮件营销活动影响所需的标识符，即内部营销活动名称(cid)和iNmsBroadlog(bid)表ID。 您还应指定要收集活动的指示器。

   ![](assets/adobe_genesis_install_006.png)

1. 如有必要，请指定个性化细分。

   ![](assets/adobe_genesis_install_007.png)

1. 在中， **[!UICONTROL Data collection]**&#x200B;选择一种恢复数据的方法，在这种情况下，选择步骤6中指 **[!UICONTROL cid]** 定的 **[!UICONTROL bid]** 标识符和标识符。

   ![](assets/adobe_genesis_install_009.png)

1. 选择要在功能板中显示的信息。

   ![](assets/adobe_genesis_install_0112.png)

1. 检查页面中的配置，该配置总结了以前的步骤。

   ![](assets/adobe_genesis_install_011.png)

1. 单击 **[!UICONTROL Activate Now]** 以批准配置并激活连接器。

   ![](assets/adobe_genesis_install_012.png)

   数据连接器现已配置。

### 第2步：在Campaign中创建外部帐户 {#step-2--create-the-external-account-in-campaign}

将Adobe Campaign集成到Analytics平台中是使用连接器进行的。 要同步应用程序，请应用以下过程：

1. 在Adobe Campaign中 **安装Web Analytics Connectors** 包。
1. 转到Adobe **[!UICONTROL Administration > Platform > External accounts]** Campaign树的文件夹。
1. 右键单击外部帐户列表，在下拉 **[!UICONTROL New]** 菜单中进行选择(或单击外部帐户列 **[!UICONTROL New]** 表上方的按钮)。
1. 使用下拉列表选择类 **[!UICONTROL Web Analytics]** 型。
1. 选择连接器的提供者，即 **[!UICONTROL Adobe Analytics - Data Connector]** 在此例中。

   ![](assets/webanalytics_ext_account_create_001.png)

1. 单击链 **[!UICONTROL Enrich the formula...]** 接以更改URL计算公式，以指定Web分析工具集成信息（系列活动ID）和必须跟踪其活动的站点的域。
1. 指定站点的域名。

   ![](assets/webanalytics_tracking_001.png)

1. 单 **[!UICONTROL Next]** 击并确保域名已保存。

   ![](assets/webanalytics_tracking_002.png)

1. 如有必要，您必须使计算公式过载。 为此，请选中该框并直接在窗口中编辑公式。

   ![](assets/webanalytics_tracking_003.png)

   >[!CAUTION]
   >
   >此配置模式为专家用户保留：此公式中的任何错误都可能导致电子邮件发送停止。

1. 通过 **[!UICONTROL Advanced]** 选项卡可以配置或修改更多技术设置。

   * **[!UICONTROL Lifespan]**:允许您指定延迟（以天数_为单位），之后Adobe Campaign中的Web事件会通过技术工作流恢复。 默认：180天。
   * **[!UICONTROL Persistence]**:允许您将所有Web事件（例如购买）归因到再营销活动的期间，默认值：7天。

>[!NOTE]
>
>如果您使用多个受众评估工具，则可以在创 **[!UICONTROL Other]** 建外部 **[!UICONTROL Partners]** 帐户时在下拉列表中进行选择。 您只能在传送属性中引用一个外部帐户：因此，您需要通过添加Adobe和所有其他使用的测量工具所需的参数来调整跟踪URL的公式。

### 第3步：同步Adobe Campaign和Adobe Analytics {#step-3--synchronize-adobe-campaign-and-adobe-analytics}

创建外部帐户后，您需要同步这两个应用程序。

1. 转到之前创建的外部帐户。
1. 根据需要更 **[!UICONTROL Label]** 改帐户。
1. 更改， **[!UICONTROL Internal name]** 使其与配置数据连接 **[!UICONTROL Name]** 器时选择的匹配。

   ![](assets/webanalytics_ext_account_setting_001.png)

1. 单击链 **[!UICONTROL Approve connection]** 接。

   ![](assets/webanalytics_ext_account_setting_002.png)

   确保与“数据连 **[!UICONTROL Internal name]** 接器”配 **[!UICONTROL Name]** 置向导中指定的匹配。

1. 在数据连 **[!UICONTROL Account ID]** 接器配置向导中输入。

   ![](assets/webanalytics_ext_account_setting_003.png)

1. 按照“数据连接器向导”指南执行步骤，然后返回Adobe Campaign中的外部帐户。
1. 单 **[!UICONTROL Next]** 击以便在Adobe Campaign和Adobe Analytics —— 数据连接器之间进行数据交换。

   同步完成后，将显示区段列表。

   ![](assets/webanalytics_ext_account_setting_004.png)

当Adobe Campaign与Adobe Analytics - Data connector之间的数据同步有效时，Adobe Campaign会恢复在Data Connector向导中定义的三个默认区段，并可在Adobe Campaign外部帐户的选项卡中访问这些区段。 **[!UICONTROL Segments]**

![](assets/webanalytics_segments.png)

如果已在数据连接器向导中配置了其他区段，则可以将其添加到Adobe Campaign。 为此，请单击链接， **[!UICONTROL Update segment list]** 然后按照外部帐户向导中所述的步骤操作。 执行操作后，新区段将显示在列表中。

![](assets/webanalytics_segments_update.png)

### Web分析流程的技术工作流程 {#technical-workflows-of-web-analytics-processes}

Adobe Campaign和Adobe Analytics之间的数据交换——数据连接器由作为后台任务运行的四个技术工作流程处理。

它们位于Adobe Campaign树中的文件夹下 **[!UICONTROL Administration > Production > Technical workflows > Web analytics process]** 。

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**:该工作流每小时会下载有关给定站点上用户行为的区段，并将其包含在Adobe Campaign数据库中，并启动再营销工作流。
* **[!UICONTROL Event purge]**:此工作流允许您根据字段中配置的时间段从数据库中删除所有事 **[!UICONTROL Lifespan]** 件。 有关此方面的详细信息，请参 [阅步骤2:在Campaign中创建外部帐户](#step-2--create-the-external-account-in-campaign)。
* **[!UICONTROL Identification of converted contacts]**:再营销活动后进行购买的访客的目录。 通过此工作流收集的数据可在报告 **[!UICONTROL Re-marketing efficiency]** 中访问，请参阅此 [页](#creating-a-re-marketing-campaign)。* **[!UICONTROL Sending of indicators and campaign attributes]**:允许您使用Adobe Analytics —— 数据连接器通过Adobe Campaign将电子邮件营销活动指示器发送到Adobe Experience Cloud。 此工作流每天凌晨4点触发，并且可能需要24小时才能将数据发送到Analytics。

   请注意，此工作流不应重新启动，否则它将重新发送所有可能歪斜Analytics结果的先前数据。

   相关指标包括：

   * **[!UICONTROL Messages to deliver]** (@toDeliver)
   * **[!UICONTROL Processed]** （@已处理）
   * **[!UICONTROL Success]** (@success)
   * **[!UICONTROL Total count of opens]** (@totalRecipientOpen)
   * **[!UICONTROL Recipients who have opened]** (@recipientOpen)
   * **[!UICONTROL Total number of recipients who clicked]** (@totalRecipientClick)
   * **[!UICONTROL People who clicked]** (@personClick)
   * **[!UICONTROL Number of distinct clicks]** (@recipientClick)
   * **[!UICONTROL Opt-Out]** (@optOut)
   * **[!UICONTROL Errors]** (@error)
   >[!NOTE]
   >
   >发送的数据是基于最后一个快照的增量，该快照可能导致度量数据中的负值。

   发送的属性如下：

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** (operation/@label):仅在安装 **了Campaign** 包时
   * **[!UICONTROL Nature]** (operation/@nature):仅在安装 **了Campaign** 包时
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (scheduling/@contactDate)


* **转换的联系人标识**:再营销活动后进行购买的访客的目录。 通过此工作流收集的数据可在报 **[!UICONTROL Re-marketing efficiency]** 告中访问(请参阅 [此页](../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign))。

## 在Adobe Campaign中跟踪分发 {#tracking-deliveries-in-adobe-campaign}

为了使Adobe Experience cloud能够在Adobe Campaign发送交付后跟踪站点上的活动，您需要在交付属性中引用匹配连接器。 为此，请应用以下步骤：

1. 打开要跟踪的营销活动的交付。

   ![](assets/webanalytics_delivery_properties_003.png)

1. 打开提交属性。
1. 转到选项卡 **[!UICONTROL Web Analytics]** 并选择之前创建的外部帐户。 请参阅 [步骤2:在Campaign中创建外部帐户](#step-2--create-the-external-account-in-campaign))。

   ![](assets/webanalytics_delivery_properties_002.png)

1. 您现在可以在Adobe Analytics中发送交付并访问报告。

## 创建再营销活动 {#creating-a-re-marketing-campaign}

要准备再营销活动，只需创建用于再营销类型营销活动的交付模板。 然后配置再营销活动并将其关联到区段。 每个区段必须有不同的再营销活动。

在Adobe Campaign完成恢复细分后，重新营销活动会自动启动，这些细分分析初始营销活动所针对人群的行为。 如果放弃购物车或查看产品而不购买，则会向相关收件人发送交货，以便其浏览网站以购买结束。

Adobe Campaign提供个性化的投放模板，您可以使用这些模板或将自己的数据库用于准备营销活动。

1. 从中 **[!UICONTROL Explorer]**，转到Adobe Campaign **[!UICONTROL Resources > Templates > Delivery templates]** 树的文件夹。
1. 复制 **[!UICONTROL Email delivery (re-marketing)]** Adobe Campaign提供的模板或再营销模板示例。
1. 个性化模板以满足您的需求并保存它。

   ![](assets/webanalytics_delivery_model.png)

1. 创建新营销活动，然后从 **[!UICONTROL Re-marketing campaign]** 下拉列表中选择模板。

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. 单击链 **[!UICONTROL Configure...]** 接以指定链接到营销活动的区段和分发模板。
1. 选择之前配置的外部帐户。

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. 选择相关的区段。

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. 选择要用于此再营销活动的分发模板，然后单击以 **[!UICONTROL Finish]** 关闭窗口。

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. 单击 **[!UICONTROL OK]** 以关闭营销活动窗口。

通 **[!UICONTROL Re-marketing efficiency]** 过全局报告页面访问报告。 它允许您查看与Adobe Campaign再营销活动后放弃的购物车数量相关的已转换联系人数（即已购买商品）。 转化率是每周、每月或自Adobe Campaign和Web分析工具开始同步以来计算的。

![](assets/webanalytics_reporting.png)

