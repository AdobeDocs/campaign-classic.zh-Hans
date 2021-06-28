---
product: campaign
title: 管理营销资源
description: 了解如何管理营销资源
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: f661e1d1-de2f-4c6a-bbff-e3ffcd1831f0
source-git-commit: 690f7c4e62203127da7a7055afa0ee8ad4a2bce4
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 0%

---

# 管理营销资源{#managing-marketing-resources}

Adobe Campaign允许您管理和跟踪营销活动生命周期中涉及的营销资源。 这些营销资源可以是手册、视觉辅助工具或涉及多个操作员的任何其他通信媒介。

对于通过Adobe Campaign管理的每个营销资源，您可以随时跟踪其状态和历史记录并查看当前版本。

## 添加营销资源 {#adding-a-marketing-resource}

可通过&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡访问营销资源。

要添加资源，请单击&#x200B;**[!UICONTROL Create]**&#x200B;按钮。

![](assets/s_ncs_user_mkg_resource_add.png)

要使资源在Adobe Campaign服务器上可用，必须通过将所需资源拖放到编辑器的中间区域来添加该资源。 您还可以单击&#x200B;**[!UICONTROL Upload file to server...]**&#x200B;链接。

![](assets/s_ncs_user_mkg_resource_file.png)

确认消息允许您启动上传。

上传完成后，资源会添加到可用资源列表。 Adobe Campaign运营商可以访问该功能。 他们可以（通过&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡）查看文件，制作副本以对其进行修改，或在服务器上更新文件（使用&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡）。

![](assets/s_ncs_user_mkg_resource_extract.png)

单击&#x200B;**[!UICONTROL General]**&#x200B;选项卡，选择负责监视、跟踪和批准此资源的操作员或操作员组。 通过&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;链接选择审阅人。

* 为其分配资源的操作员负责跟踪该资源。
* 批准运营商负责批准营销资源。 资源验证过程启动后，系统会通知他们。

   如果未选择审核者，则资源&#x200B;**[!UICONTROL cannot be]**&#x200B;须经批准。

* 如有必要，您还可以指定校对器。

您可以为资源指定（指示性）可用日期。 在此日期之后，将显示&#x200B;**[!UICONTROL Late]**&#x200B;状态。

## 资源协作工作 {#collaborative-work-on-resources}

您可以修改和更新营销资源，并在必要时通知其他Adobe Campaign操作员。 您可以：

* 将资源下载到本地以对其进行修改。
* 更新服务器上的文件，使其可供其他操作员访问。
* 锁定资源，以禁止其他操作员修改资源。

>[!NOTE]
>
>**[!UICONTROL History]**&#x200B;选项卡包含资源的下载和更新日志。 使用&#x200B;**[!UICONTROL Details]**&#x200B;按钮可以查看所选版本：

### 锁定/解锁资源 {#locking-unlocking-a-resource}

创建资源后，即可在营销资源功能板中使用资源，操作员可以编辑和修改这些资源。

当操作员希望处理某个资源时，最好在开始工作之前将其锁定，以防止其他操作员同时修改该资源。 然后保留该资源；它仍然可以访问，但无法由其他运算符在服务器上发布或更新。

系统会显示一条特殊消息，通知尝试访问该页面的所有操作员：

![](assets/s_ncs_user_mkg_resource_locked.png)

**[!UICONTROL Tracking]**&#x200B;选项卡指示锁定资源的操作员的名称和计划的更新日期。

![](assets/s_ncs_user_mkg_resource_locked_date.png)

要锁定资源，必须单击资源，然后单击资源功能板中的&#x200B;**[!UICONTROL Lock]**&#x200B;按钮。

![](assets/s_ncs_user_mkg_resource_lock.png)

您可以在资源的&#x200B;**[!UICONTROL Tracking]**&#x200B;选项卡中指示计划的返回日期。

![](assets/s_ncs_user_mkg_resource_lock_date.png)

利用此信息，可通知其他Adobe Campaign操作员资源将解锁的日期。

资源更新后，将自动解锁并再次供所有操作员使用。

如有必要，您还可以从功能板中手动解锁。

>[!NOTE]
>
>只有锁定资源的操作员和具有管理员权限的操作员才有权解锁资源。

### 论坛 {#discussion-forums}

对于每个资源，**[!UICONTROL Forum]**&#x200B;选项卡允许参与者交换信息。

[讨论](../../mrm/using/discussion-forums.md) 概述论坛在Adobe Campaign的运作方式。

## 营销资源的生命周期 {#life-cycle-of-a-marketing-resource}

创建资源后，将指定Adobe Campaign运算符来设计、校对、批准和发布该资源。 可以确定这些营销活动的持续时间。

**[!UICONTROL Tracking]**&#x200B;选项卡允许您监视对资源执行的任何操作：批准、批准拒绝、相关评论或出版物。

**[!UICONTROL History]**&#x200B;选项卡显示为此资源执行的文件传输。

### 审批流程 {#approval-process}

如果在&#x200B;**[!UICONTROL Tracking]**&#x200B;选项卡中指定了预期可用日期，则该日期会显示在资源详细信息中。 达到此日期后，即可使用资源仪表板中的&#x200B;**[!UICONTROL Submit for approval]**&#x200B;按钮执行批准流程。 然后，资源状态将更改为&#x200B;**[!UICONTROL Approval in progress]**。

资源可通过其仪表板上的&#x200B;**[!UICONTROL Approve resource]**&#x200B;按钮进行批准。

![](assets/s_ncs_user_task_valid_date.png)

然后，授权的运营商可以接受或拒绝批准。 此操作可以：通过发送的电子邮件（通过单击通知消息中的链接）或通过控制台（通过单击&#x200B;**[!UICONTROL Approve]**）按钮。

您可以在审批窗口中输入评论。

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

**[!UICONTROL Tracking]**&#x200B;选项卡允许所有运算符跟踪审批流程的各个阶段。

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>除了为每个营销资源指定的审核者之外，具有管理员权限的操作员和资源管理器也被授权批准营销资源。

### 发布资源 {#publishing-a-resource}

批准后，必须发布营销资源。 出版过程必须按照公司要求具体实施。 这意味着资源可以在外联网或任何其他服务器上发布，特定信息可以发送到外部服务提供商等。

要发布资源，请单击营销资源功能板编辑区域中的&#x200B;**[!UICONTROL Publish]**&#x200B;按钮。

![](assets/s_ncs_user_mkg_resource_available.png)

您还可以通过工作流自动发布资源。

发布资源意味着（例如，由其他任务）使其可供使用。 根据资源的性质，发布内容会有所不同：对于传单，发布可能意味着将文件发送到打印机，对于Web代理，发布可能意味着将其发布到网站等。

要使Adobe Campaign发布，您需要创建一个适当的工作流并将其链接到资源。 要执行此操作，请打开资源的&#x200B;**[!UICONTROL Advanced settings]**&#x200B;框，然后在&#x200B;**[!UICONTROL Post-processing]**&#x200B;字段中选择所需的工作流。

![](assets/mrm_asset_postprocessing_workflow.png)

将执行工作流：

* 当审核人员单击&#x200B;**[!UICONTROL Publish resource]**&#x200B;链接时（或者，如果未定义审核人员，则为资源负责人）。
* 如果资源是通过营销资源创建任务管理的，则在将任务设置为&#x200B;**[!UICONTROL Finished]**&#x200B;时执行该资源，只要在任务中选中&#x200B;**[!UICONTROL Publish the marketing resource]**&#x200B;框（请参阅[营销资源创建任务](../../mrm/using/creating-and-managing-tasks.md#marketing-resource-creation-task)）

如果工作流未立即启动（例如，如果工作流已停止），则资源的状态将更改为&#x200B;**[!UICONTROL Pending publication]**。 启动工作流后，资源的状态将变为&#x200B;**[!UICONTROL Published]**。 此状态未考虑发布过程中可能出现的错误。 检查工作流的状态，确保工作流已正确执行。

## 将资源链接到营销活动 {#linking-a-resource-to-a-campaign}

### 引用营销资源 {#referencing-a-marketing-resource}

营销资源可以与营销活动关联，前提是已在营销活动模板中选择此功能。

>[!NOTE]
>
>有关如何创建和配置营销活动模板的详细信息，请参阅[营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

单击营销活动仪表板中的&#x200B;**[!UICONTROL Documents > Resources]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Add]**&#x200B;以选择相关资源。

![](assets/s_ncs_user_mkg_resource_ref.png)

您可以按状态、自然或类型筛选资源，也可以应用个性化筛选器。

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

单击&#x200B;**[!UICONTROL OK]**&#x200B;将资源添加到此营销活动引用的营销资源列表。

使用&#x200B;**[!UICONTROL Details]**&#x200B;按钮可编辑和查看。

添加的资源将显示在功能板中。 也可在此处编辑它们。

### 向投放大纲添加营销资源 {#adding-a-marketing-resource-to-a-delivery-outline}

营销资源可以通过投放大纲与投放相关联。

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>有关投放大纲的更多信息，请参阅[关联和构建通过投放大纲链接的资源](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

## 库存管理 {#stock-management}

您可以将营销资源与一个或多个库存关联，以便管理您的供应，并在库存不足时在仪表板上显示警告。

>[!NOTE]
>
>有关Adobe Campaign股票管理的更多信息，请参阅[股票管理](../../campaign/using/providers--stocks-and-budgets.md#stock-management)。

要将营销资源与库存关联，请编辑库存图并编辑或创建库存。 添加库存行并选择相应的营销资源。

![](assets/s_ncs_user_task_in_a_stock.png)

如有必要，您可以在选择资源后，通过资源右侧的&#x200B;**[!UICONTROL Edit the link]**&#x200B;图标（放大镜）来编辑选定的资源。

指定初始库存和警报库存，然后保存。

资源详细信息中会指示库存。

![](assets/s_ncs_user_task_with_a_stock.png)

当库存不足时，向相关操作员发送警告。

## 高级功能 {#advanced-functions}

通过“营销资源”功能板，您可以执行常见类型的操作：添加、编辑、锁定/解锁、批准、发布。 您可以创建其他类型的营销资源，并通过Adobe Campaign树访问高级功能。 要执行此操作，请单击Adobe Campaign主页中的&#x200B;**[!UICONTROL Explorer]**。

默认情况下，营销资源存储在树的&#x200B;**[!UICONTROL MRM > Marketing resources]**&#x200B;节点中。

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

您可以从此视图添加以下资源：

* 文件
* HTML
* 文本
* URL
