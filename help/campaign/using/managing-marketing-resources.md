---
title: 管理营销资源
seo-title: 管理营销资源
description: 管理营销资源
seo-description: null
page-status-flag: never-activated
uuid: 35333bcb-0749-45b1-98ab-d5de6d91861c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 069dbc6b-4019-4d66-85a8-0e4de6b66f18
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e09692e316a92a67632201e5691e8b4df42cc341

---


# 管理营销资源{#managing-marketing-resources}

Adobe Campaign可让您管理和跟踪营销活动生命周期中涉及的营销资源。 这些营销资源可以是小册子、视觉辅助工具或涉及多个运营商的任何其他通信介质。

对于通过Adobe Campaign管理的每个营销资源，您可以随时跟踪其状态和历史记录并查看当前版本。

## 添加营销资源 {#adding-a-marketing-resource}

营销资源可通过营销活动范围访问。

要添加资源，请单击 **[!UICONTROL Create]** 按钮。

![](assets/s_ncs_user_mkg_resource_add.png)

要使某个资源在Adobe Campaign服务器上可用，您必须通过将所需的资源拖放到编辑器的中间区域来添加该资源。 您还可以单击该 **[!UICONTROL Upload file to server...]** 链接。

![](assets/s_ncs_user_mkg_resource_file.png)

通过确认消息可启动上传。

上传完成后，资源将添加到可用资源列表。 Adobe Campaign运营商可以访问它。 他们可以（通过选项卡） **[!UICONTROL Preview]** 查看文件，制作一个副本以修改文件，或者（使用选项卡）更新服务器上的 **[!UICONTROL Edit]** 文件。

![](assets/s_ncs_user_mkg_resource_extract.png)

单击选 **[!UICONTROL General]** 项卡以选择负责监视、跟踪和批准此资源的操作员或操作员组。 通过链接选择审阅者即 **[!UICONTROL Advanced parameters]** 可。

* 为其分配资源的操作员负责跟踪该资源。
* 批准运营商负责批准营销资源。 资源验证过程启动时，会通知这些用户。

   如果未选择审阅人，则资 **[!UICONTROL cannot be]** 源需要批准。

* 如有必要，还可以指定校对器。

您可以为资源指定（指示性）可用日期。 在此日期之后，它将显示为状态 **[!UICONTROL Late]** 。

## 资源协作工作 {#collaborative-work-on-resources}

您可以修改和更新营销资源，并在必要时通知其他Adobe Campaign运营商。 您可以：

* 在本地下载资源以对其进行修改。
* 更新服务器上的文件，使其他操作员能够访问它。
* 锁定资源，以禁止其他运营商修改它。

>[!NOTE]
>
>该选 **[!UICONTROL History]** 项卡包含资源的下载和更新日志。 通过 **[!UICONTROL Details]** 该按钮可以查看所选版本：

### 锁定／解锁资源 {#locking-unlocking-a-resource}

创建资源后，资源便可在营销资源控制板中使用，操作员可以编辑和修改它们。

当操作者希望处理资源时，最好在开始工作之前将其锁定，以防止其他操作者同时修改它。 然后保留资源；它仍然可访问，但无法由其他操作员在服务器上发布或更新。

将显示一条特殊消息，通知任何尝试访问它的操作员：

![](assets/s_ncs_user_mkg_resource_locked.png)

该选 **[!UICONTROL Tracking]** 项卡指示锁定资源的操作员的姓名和计划的更新日期。

![](assets/s_ncs_user_mkg_resource_locked_date.png)

要锁定资源，必须单击资源，然后单击资源功 **[!UICONTROL Lock]** 能板中的按钮。

![](assets/s_ncs_user_mkg_resource_lock.png)

您可以在资源的标签中指明计 **[!UICONTROL Tracking]** 划的退回日期。

![](assets/s_ncs_user_mkg_resource_lock_date.png)

通过此信息，您可以通知其他Adobe Campaign运营商资源将解锁的日期。

更新资源后，该资源将自动解锁并再次向所有操作员提供。

如有必要，您还可以从功能板中手动解锁它。

>[!NOTE]
>
>只有锁定资源的操作员和具有管理员权限的操作员才能解锁资源。

### 论坛 {#discussion-forums}

对于每个资源，该选项卡 **[!UICONTROL Forum]** 允许参加者交换信息。

[论坛介绍](../../campaign/using/discussion-forums.md) ，论坛如何在Adobe Campaign中运行。

## 营销资源的生命周期 {#life-cycle-of-a-marketing-resource}

创建资源后，会指定Adobe Campaign运营商来设计、校对、批准和发布资源。 可以为这些营销活动确定持续时间。

通过 **[!UICONTROL Tracking]** 该选项卡可以监视对资源执行的任何操作：批准、批准拒绝、相关评论或出版物。

该选 **[!UICONTROL History]** 项卡显示为此资源执行的文件传输。

### 批准流程 {#approval-process}

如果在选项卡中指定了预期发布日期，则该日期将显示在资源详细信息 **[!UICONTROL Tracking]** 中。 到达此日期后，您可以使用资源功能板中的按 **[!UICONTROL Submit for approval]** 钮执行批准过程。 然后，资源状态将更改为 **[!UICONTROL Approval in progress]**。

资源可以通过其功能板上 **[!UICONTROL Approve resource]** 的按钮进行批准。

![](assets/s_ncs_user_task_valid_date.png)

然后，授权运营商可以接受或拒绝批准。 此操作可以：通过发送的电子邮件（通过单击通知消息中的链接）或通过控制台(通过单击 **[!UICONTROL Approve]** )按钮。

在批准窗口中可以输入评论。

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

该选 **[!UICONTROL Tracking]** 项卡使所有运营商都能够跟踪审批过程的各个阶段。

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>除了为每个营销资源指定的审核人之外，具有管理员权限的操作员和资源管理员还被授权批准营销资源。

### 发布资源 {#publishing-a-resource}

批准后，必须发布营销资源。 出版过程必须按照公司要求具体实施。 这意味着资源可以发布到外部网或任何其他服务器上，特定信息可以发送到外部服务提供商等。

要发布资源，请单击 **[!UICONTROL Publish]** 营销资源功能板编辑区域中的按钮。

![](assets/s_ncs_user_mkg_resource_available.png)

您还可以通过工作流自动发布资源。

发布资源意味着（例如，通过其他任务）可以使用资源。 根据您的资源性质，发布内容会有所不同：对于传单，发布可能意味着将文件发送到打印机，对于Web代理，发布可能意味着将其发布到网站等。

要使Adobe Campaign能够发布，您需要创建一个适当的工作流并将其链接到资源。 为此，请打开资 **[!UICONTROL Advanced settings]** 源的框，然后在字段中选择所需的工作流 **[!UICONTROL Post-processing]** 程。

![](assets/mrm_asset_postprocessing_workflow.png)

将执行以下工作流：

* 当审阅人单击链 **[!UICONTROL Publish resource]** 接时（或者，如果未定义审阅人，则单击资源负责人）。
* 如果通过营销资源创建任务管理资源，则只要选中任务中的框(请参阅营销资源创建任务 **[!UICONTROL Finished]****[!UICONTROL Publish the marketing resource]**[](../../campaign/using/creating-and-managing-tasks.md#marketing-resource-creation-task))，该资源将在任务设置为时执行

如果工作流未立即启动（例如，工作流已停止），则资源的状态将更改为 **[!UICONTROL Pending publication]**。 启动工作流后，资源的状态将更改为 **[!UICONTROL Published]**。 此状态未考虑发布过程中可能出现的错误。 检查工作流的状态，以确保其正确执行。

## 将资源关联到营销活动 {#linking-a-resource-to-a-campaign}

### 引用营销资源 {#referencing-a-marketing-resource}

营销资源可以与营销活动关联，前提是该功能已在营销活动模板中选定。

>[!NOTE]
>
>有关如何创建和配置营销活动模板的详细信息，请参阅 [营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

单击营 **[!UICONTROL Documents > Resources]** 销活动功能板中的选项卡，然后单 **[!UICONTROL Add]** 击以选择相关的资源。

![](assets/s_ncs_user_mkg_resource_ref.png)

您可以按状态、性质或类型筛选资源，或应用个性化筛选。

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

单 **[!UICONTROL OK]** 击可将资源添加到此营销活动引用的营销资源列表。

通过 **[!UICONTROL Details]** 该按钮可编辑和查看它。

添加的资源将显示在功能板中。 也可在此处编辑。

### 将营销资源添加到分发大纲 {#adding-a-marketing-resource-to-a-delivery-outline}

营销资源可以通过交付大纲与交付相关联。

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>有关交付大纲的详细信息，请参阅 [关联和构造通过交付大纲链接的资源](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

## 库存管理 {#stock-management}

您可以将营销资源与一个或多个库存关联，以管理您的供应并在库存不足时在仪表板上显示警告。

>[!NOTE]
>
>有关Adobe Campaign中的库存管理的详细信息，请参阅 [库存管理](../../campaign/using/providers--stocks-and-budgets.md#stock-management)。

要将营销资源与库存关联，请编辑库存图并编辑或创建库存。 添加一个库存行，然后选择相应的营销资源。

![](assets/s_ncs_user_task_in_a_stock.png)

如有必要，您可以通过资源右侧的图标(放大镜 **[!UICONTROL Edit the link]** )编辑选定的资源，一旦选定该资源，即可编辑该资源。

指定初始库存和警报库存，然后保存。

资源详细信息中会指示库存。

![](assets/s_ncs_user_task_with_a_stock.png)

当股票不足时，向有关经营者发出警告。

## 高级功能 {#advanced-functions}

通过市场营销资源仪表板，您可以执行常见类型的操作：添加、编辑、锁定／解锁、批准、发布。 您可以创建其他类型的营销资源，并通过Adobe Campaign树访问高级功能。 为此，请单 **[!UICONTROL Explorer]** 击Adobe Campaign主页。

默认情况下，营销资源存储在 **[!UICONTROL MRM > Marketing resources]** 树的节点中。

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

您可以从此视图添加以下资源：

* 文件
* HTML
* 文本
* URL

