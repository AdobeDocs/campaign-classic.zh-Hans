---
product: campaign
title: Adobe Analytics Connector
description: 了解有关 Adobe Analytics Connector 的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: User, Admin
level: Beginner
exl-id: 0dc6ce98-dc3e-4242-953e-e7cec55289ff
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 90%

---

# Adobe Analytics Connector{#adobe-analytics-connector}



## 关于 Adobe Analytics Connector 集成 {#about-analytics-connector-integration}

Adobe Analytics Connector 允许 Adobe Campaign 和 Adobe Analytics 通过 **[!UICONTROL Web Analytics connectors]** 包进行交互。它会以区段形式将数据转发到Adobe Campaign，涉及营销活动后的用户行为。 相反，它会将Adobe Campaign提供的促销活动指标和属性发送到Adobe Analytics。

>[!CAUTION]
>
>* Adobe Analytics Connector 与事务性消息传递（消息中心）不兼容。
>
>* 开始前，请确保在 Campaign 中实施 Adobe Identity Management System (IMS) 。 [请参阅此页面](../../integrations/using/about-adobe-id.md)以了解详情。


使用 Adobe Analytics Connector，Adobe Campaign 可以对互联网受众进行评测（网站分析）。借助这些集成，Adobe Campaign 可以在投放营销活动后回收一个或多个网站的访客行为数据，并（在分析之后）开展再营销活动，以期将访客转化为购买者。反过来，网站分析工具让 Adobe Campaign 能够将指标和营销活动属性转发到其平台。

每个工具的操作字段如下所示：

* 网站分析的作用：

   1. 标记通过Adobe Campaign启动的营销活动，
   1. 以区段形式保存收件人在点击营销活动后浏览的网站上的行为。 区段涉及放弃的产品（已浏览但未加入购物车或购买）、购买或购物车放弃。

* Adobe Campaign 的角色：

   1. 将指标和营销活动属性发送到连接器，然后由连接器将它们转发到网站分析工具，
   1. 恢复和分析区段，
   1. 触发再营销活动。

## 设置集成 {#setting-up-the-integration}

>[!IMPORTANT]
>
> 对于混合和内部部署实施，请确保遵循此[页面](../../platform/using/adobe-analytics-provisioning.md)中详述的配置步骤。

要设置 Data Connector，您必须连接到 Adobe Campaign 实例并执行以下操作：

1. [配置转化变量和成功事件](#configure-conversion-success)
1. [在 Adobe Campaign Classic 中配置外部帐户](#external-account-classic)

<!--
### Create your Report suite in Adobe Analytics {#report-suite-analytics}

To set up the Adobe Analytics/Adobe Campaign Classic integration, you must connect to your [!DNL Adobe Analytics] instance and perform the following operations:

1. From [!DNL Adobe Analytics], select the **[!UICONTROL Admin tab]** then click **[!UICONTROL All admin]**.

   ![](assets/analytics_connnector_1.png)

1. Click **[!UICONTROL Report suites]**.

   ![](assets/analytics_connnector_2.png)

1. From the **[!UICONTROL Report suite manager]** page, click **[!UICONTROL Create new]** then **[!UICONTROL Report suite]**.

   For the detailed procedure on **[!UICONTROL Report suite]** creation, refer to this [section](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=en#prerequisites).

   ![](assets/analytics_connnector_3.png)

1. Select a template. 

1. Configure your new report suite with the following information:

   * **[!UICONTROL Report Suite ID]**
   * **[!UICONTROL Site Title]**
   * **[!UICONTROL Time Zone]**
   * **[!UICONTROL Go Live Date]**
   * **[!UICONTROL Estimated Page Views Per Day]**

   ![](assets/analytics_connnector_4.png)

1. When configured, click **[!UICONTROL Create report suite]**.
-->

### 配置转化变量和成功事件 {#configure-conversion-success}

您需要按如下方式配置 **[!UICONTROL Conversion variables]** 和 **[!UICONTROL Success events]**：

1. 选择要与 Adobe Campaign 关联的 **[!UICONTROL Report suite]**。

1. 在 **[!UICONTROL Edit settings]** 按钮中，选择 **[!UICONTROL Conversion]** > **[!UICONTROL Conversion variables]**。

   ![](assets/analytics_connnector_5.png)

1. 单击 **[!UICONTROL Add new]** 创建测量促销活动影响所需的标识符，即内部促销活动名称(cid)和iNmsBroadlog(bid)表ID。

   如需了解如何编辑 **[!UICONTROL Conversion variables]**，请参阅此[部分](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/t-conversion-variables-admin.html?lang=zh-Hans#admin-tools)。

   ![](assets/analytics_connnector_6.png)

1. 完成后单击 **[!UICONTROL Save]**。

1. 然后，要创建 **[!UICONTROL Success events]**，请在 **[!UICONTROL Edit settings]** 按钮中选择 **[!UICONTROL Conversion]** > **[!UICONTROL Success events]**。

   ![](assets/analytics_connnector_7.png)

1. 单击 **[!UICONTROL Add new]** 以配置以下 **[!UICONTROL Success events]**：

   * **[!UICONTROL Clicked]**
   * **[!UICONTROL Opened]**
   * **[!UICONTROL Person clicks]**
   * **[!UICONTROL Processed]**
   * **[!UICONTROL Scheduled]**
   * **[!UICONTROL Sent]**
   * **[!UICONTROL Total bounces]**
   * **[!UICONTROL Unique Clicks]**
   * **[!UICONTROL Unique Opens]**
   * **[!UICONTROL Unsubscribed]**

   要了解如何配置 **[!UICONTROL Success events]**，请参阅此[部分](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/success-events/t-success-events.html?lang=zh-Hans#admin-tools)。

   >[!NOTE]
   >
   > 仅支持数值类型的 **[!UICONTROL Success events]**。

   ![](assets/analytics_connnector_8.png)

1. 完成后单击 **[!UICONTROL Save]**。

配置 **[!UICONTROL Conversion variables]** 和 **[!UICONTROL Success events]** 后，确保这些变量包含在为 Analytics Connector 创建的 **[!UICONTROL Product Profile]** 中。有关更多信息，请参阅[创建 Adobe Analytics 产品配置文件](../../platform/using/adobe-analytics-provisioning.md#analytics-product-profile)。

然后，您需要在 Adobe Campaign Classic 中配置 **[!UICONTROL External accounts]**。

### 在 Adobe Campaign Classic 中配置外部帐户 {#external-account-classic}

>[!IMPORTANT]
>
> 为使这种集成正常工作，您需要在 Adobe Campaign 中安装 **[!UICONTROL Web Analytics connectors]** 软件包。
>
>有关软件包安装的更多信息，请参阅此[页面](../../installation/using/installing-campaign-standard-packages.md)。

现在，您需要在 Adobe Campaign 中配置 **[!UICONTROL Web Analytics]** 外部帐户，以启用两种解决方案之间的同步。

请注意，如果在配置外部帐户时，您的 **[!UICONTROL Report suite]**、**[!UICONTROL Conversion variables]** 或 **[!UICONTROL Success events]** 不可见，这意味着您在与用户关联的 **[!UICONTROL Product profile]** 中缺少对此新创建组件的权限。

有关此内容的更多信息，请参阅 [Adobe Analytics 的产品配置文件](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/permissions/product-profile.html?lang=zh-Hans#product-profile-admins)页面。

1. 转到 Adobe Campaign 树的 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** 文件夹，然后单击 **[!UICONTROL New]**。

   ![](assets/analytics_connnector_9.png)

1. 使用下拉列表从 **[!UICONTROL Integration]** 下拉列表中选择 **[!UICONTROL Web Analytics]** 类型和 **[!UICONTROL Adobe Analytics]**。

   ![](assets/analytics_connnector_10.png)

1. 单击 **[!UICONTROL Integration]** 下拉列表旁边的 **[!UICONTROL Configure]**。

1. 从 **[!UICONTROL Configure Analytics integration]** 窗口中，将外部帐户映射到您的报表包，并提供以下信息：

   * **[!UICONTROL E-Mail]**
   * **[!UICONTROL IMS Org]**
   * **[!UICONTROL Analytics Company]**
   * **[!UICONTROL Report Suite]**

1. 在 **[!UICONTROL eVars]** 类别中，映射在 [!DNL Adobe Analytics] 中配置的两个 **[!UICONTROL Conversion variables]**。

   ![](assets/analytics_connnector_11.png)

1. 在 **[!UICONTROL Events]** 类别中，映射在 [!DNL Adobe Analytics] 中配置的十个 **[!UICONTROL Success events]**。

1. 完成后单击 **[!UICONTROL Submit]**。Adobe Campaign 将在映射的 Analytics **[!UICONTROL Report Suite]** 中创建 **[!UICONTROL Data source]**、**[!UICONTROL Calculated metrics]**、**[!UICONTROL Remarketing segments]** 和 **[!UICONTROL Classifications]**。

   在 [!DNL Adobe Analytics] 和 Adobe Campaign 之间完成同步后，您可以关闭此窗口。

1. 可以从 **[!UICONTROL Configure Analytics integration]** 窗口的 **[!UICONTROL Data Settings]** 选项卡中查看设置。

   使用 **[!UICONTROL Sync]** 按钮，[!DNL Adobe Campaign] 将会同步在 [!DNL Adobe Analytics] 中完成的名称变更。如果组件在 [!DNL Adobe Analytics] 中被删除，则将在 [!DNL Adobe Campaign] 中删除该组件，或显示&#x200B;**未找到**&#x200B;消息。

   ![](assets/analytics_connnector_12.png)

1. 如果需要，您可以在 **[!UICONTROL Update Segments]** 选项卡中添加或移除区段。

1. 在 **[!UICONTROL External account]** 中，单击 **[!UICONTROL Enrich the formula...]** 链接以更改 URL 计算公式，以指定网站分析工具集成信息（活动 ID）以及必须跟踪其活动的网站域名。

   ![](assets/analytics_connnector_13.png)

1. 指明网站的域名。

   ![](assets/analytics_connnector_14.png)

1. 单击 **[!UICONTROL Next]** 并确保域名已保存。

   ![](assets/analytics_connnector_15.png)

1. 如有必要，您可以让计算公式过载运行。要实现此目的，请勾选方框并直接在窗口中编辑公式。

   >[!IMPORTANT]
   >
   >此配置模式为专家用户保留：此公式中的任何错误都可能导致投放停止。

1. **[!UICONTROL Advanced]** 选项卡可让您配置或修改更多技术设置。

   * **[!UICONTROL Lifespan]**：可让您指定延迟（以天为单位），在此之后技术工作流会在 Adobe Campaign 中恢复网站事件。默认值：180 天。
   * **[!UICONTROL Persistence]**:用于定义所有Web事件（例如购买）可归因到再营销活动的时段，默认：7天。

>[!NOTE]
>
>如果您使用多个受众衡量工具，则在创建外部帐户时，可以在 **[!UICONTROL Partners]** 下拉列表中选择 **[!UICONTROL Other]**。您只能在投放属性中引用一个外部帐户：因此，您需要通过添加 Adobe 以及使用的所有其他衡量工具预期的参数来调整跟踪 URL 的公式。

### 网站分析流程的技术工作流 {#technical-workflows-of-web-analytics-processes}

Adobe Campaign 和 Adobe Analytics 之间的数据交换由作为后台任务运行的四个技术工作流处理。

它们位于 Adobe Campaign 树的 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Web analytics process]** 文件夹下。

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**：每小时一次，此工作流会下载关于用户在特定网站上的行为的区段，将它们纳入 Adobe Campaign 数据库，并启动再营销工作流。
* **[!UICONTROL Event purge]**：使用此工作流，可根据 **[!UICONTROL Lifespan]** 字段中配置的时段，从数据库中删除所有事件。有关此类内容的更多信息，请参阅[在 Adobe Campaign Classic 中配置外部帐户](#external-account-classic)。
* **[!UICONTROL Identification of converted contacts]**：再营销活动后进行购买的访客的目录。通过此工作流收集的数据可在 **[!UICONTROL Re-marketing efficiency]** 报表中访问，请参阅此[页面](#creating-a-re-marketing-campaign)。
* **[!UICONTROL Sending of indicators and campaign attributes]**:允许您使用Adobe Analytics Connector通过Adobe Campaign将促销活动指标发送到Adobe Experience Cloud。 此工作流在每天凌晨 4 点触发，可能需要 24 小时才能将数据发送到 Analytics。

   请注意，切勿重新启动此工作流，否则它将重新发送所有先前数据，可能会影响 Analytics 结果的准确性。

   所涉指标包括：

   * **[!UICONTROL Messages to deliver]** (@toDeliver)
   * **[!UICONTROL Processed]** (@processed)
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
   >发送的数据是基于上次快照的 delta 值，可能会导致量度数据中出现负值。

   发送的属性如下所示：

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** (operation/@label)：仅当安装了 **Campaign** 软件包时
   * **[!UICONTROL Nature]** (operation/@nature)：仅当安装了 **Campaign** 软件包时
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (scheduling/@contactDate)


## 在 Adobe Campaign 中跟踪投放 {#tracking-deliveries-in-adobe-campaign}

为了让 Adobe Experience Cloud 能够在 Adobe Campaign 发送投放后跟踪网站上的活动，您需要在投放属性中引用匹配的连接器。要执行此操作，请应用以下步骤：

1. 打开要跟踪的营销活动的投放。

   ![](assets/webanalytics_delivery_properties_003.png)

1. 打开投放属性。
1. 转到 **[!UICONTROL Web Analytics]** 选项卡，然后选择之前创建的外部帐户。请参阅[在 Adobe Campaign Classic 中配置外部帐户](#external-account-classic)。

   ![](assets/webanalytics_delivery_properties_002.png)

1. 您现在可以发送投放，并在 Adobe Analytics 中访问其报表。

## 创建再营销活动 {#creating-a-re-marketing-campaign}

要准备再营销活动，只需创建用于再营销类型的营销活动的投放模板即可。然后，配置再营销活动并将其链接到区段。每个区段必须具有不同的再营销活动。

在 Adobe Campaign 恢复区段，完成对初始营销活动目标人群的行为分析后，将自动启动再营销活动。对于购物车放弃或查看产品但未购买的情况，会向相关收件人发送投放内容，以便让他们的网站浏览活动以购买结束。

Adobe Campaign 提供个性化投放模板，您可以使用这些模板或建立您自己的数据库以准备营销活动。

1. 在 **[!UICONTROL Explorer]** 中，转到 Adobe Campaign 树的 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]** 文件夹。

1. 复制 **[!UICONTROL Email delivery (re-marketing)]** 模板或 Adobe Campaign 提供的再营销模板示例。

   ![](assets/webanalytics_delivery_model.png)

1. 根据您的需求对模板进行个性化并保存。

1. 创建新营销活动，并从下拉列表中选择 **[!UICONTROL Re-marketing campaign]** 模板。

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. 单击 **[!UICONTROL Configure...]** 链接以指定链接到该营销活动的区段和投放模板。

1. 选择之前配置的外部帐户。

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. 选择相关区段。

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. 选择要用于此再营销活动的投放模板，然后单击 **[!UICONTROL Finish]** 以关闭窗口。

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. 单击 **[!UICONTROL OK]** 以关闭营销活动窗口。

可通过全局报告页面访问 **[!UICONTROL Re-marketing efficiency]** 报告。它可以让您查看在 Adobe Campaign 再营销活动后，已转化联系人数（即已购买商品）与购物车放弃数的关系。转化率在每周、每月或自 Adobe Campaign 与网站分析工具之间开始同步后进行计算。

![](assets/remarketing_reporting.png)
