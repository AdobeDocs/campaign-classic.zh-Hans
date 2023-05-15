---
product: campaign
title: 管理营销资源
description: 了解如何管理营销资源
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: f661e1d1-de2f-4c6a-bbff-e3ffcd1831f0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 1%

---

# 管理营销资源{#managing-marketing-resources}



Adobe Campaign允许您管理和跟踪营销活动生命周期中涉及的营销资源。 这些营销资源可以是手册、视觉辅助工具或涉及多个操作员的任何其他通信媒介。

对于通过Adobe Campaign管理的每个营销资源，您可以随时跟踪其状态和历史记录并查看当前版本。

## 添加营销资源 {#adding-a-marketing-resource}

通过 **[!UICONTROL Campaigns]** 选项卡。

要添加资源，请单击 **[!UICONTROL Create]** 按钮。

![](assets/s_ncs_user_mkg_resource_add.png)

要使资源在Adobe Campaign服务器上可用，必须通过将所需资源拖放到编辑器的中间区域来添加该资源。 您还可以单击 **[!UICONTROL Upload file to server...]** 链接。

![](assets/s_ncs_user_mkg_resource_file.png)

确认消息允许您启动上传。

上传完成后，资源会添加到可用资源列表。 Adobe Campaign运营商可以访问该功能。 他们可以(通过 **[!UICONTROL Preview]** 选项卡)，创建副本以对其进行修改，或在服务器上更新文件(使用 **[!UICONTROL Edit]** 选项卡。

![](assets/s_ncs_user_mkg_resource_extract.png)

单击 **[!UICONTROL General]** 选项卡，选择负责监视、跟踪和批准此资源的操作员或操作员组。 通过 **[!UICONTROL Advanced parameters]** 链接。

* 为其分配资源的操作员负责跟踪该资源。
* 批准运营商负责批准营销资源。 资源验证过程启动后，系统会通知他们。

   如果未选择审核者，则资源 **[!UICONTROL cannot be]** 须经批准。

* 如有必要，您还可以指定校对器。

您可以为资源指定（指示性）可用日期。 在此日期之后，将显示为 **[!UICONTROL Late]** 状态。

## 资源协作工作 {#collaborative-work-on-resources}

您可以修改和更新营销资源，并在必要时通知其他Adobe Campaign操作员。 您可以：

* 将资源下载到本地以对其进行修改。
* 更新服务器上的文件，使其可供其他操作员访问。
* 锁定资源，以禁止其他操作员修改资源。

>[!NOTE]
>
>的 **[!UICONTROL History]** 选项卡包含资源的下载和更新日志。 的 **[!UICONTROL Details]** 按钮可查看所选版本。

### 锁定/解锁资源 {#locking-unlocking-a-resource}

创建资源后，即可在营销资源功能板中使用资源，操作员可以编辑和修改这些资源。

当操作员希望处理某个资源时，最好在开始工作之前将其锁定，以防止其他操作员同时修改该资源。 然后保留该资源；它仍然可以访问，但无法由其他运算符在服务器上发布或更新。

系统会显示一条特殊消息，通知尝试访问该页面的所有操作员：

![](assets/s_ncs_user_mkg_resource_locked.png)

的 **[!UICONTROL Tracking]** 选项卡指示锁定资源的操作员的名称和计划的更新日期。

![](assets/s_ncs_user_mkg_resource_locked_date.png)

要锁定资源，必须单击资源，然后单击 **[!UICONTROL Lock]** 按钮。

![](assets/s_ncs_user_mkg_resource_lock.png)

您可以在 **[!UICONTROL Tracking]** 选项卡。

![](assets/s_ncs_user_mkg_resource_lock_date.png)

利用此信息，可通知其他Adobe Campaign操作员资源将解锁的日期。

资源更新后，将自动解锁并再次供所有操作员使用。

如有必要，您还可以从功能板中手动解锁。

>[!NOTE]
>
>只有锁定资源的操作员和具有管理员权限的操作员才有权解锁资源。

### 论坛 {#discussion-forums}

对于每个资源， **[!UICONTROL Forum]** 选项卡允许参与者交换信息。

[论坛](../../mrm/using/discussion-forums.md) 介绍论坛在Adobe Campaign的运作方式。

## 营销资源的生命周期 {#life-cycle-of-a-marketing-resource}

创建资源后，将指定Adobe Campaign运算符来设计、校对、批准和发布该资源。 可以确定这些营销活动的持续时间。

的 **[!UICONTROL Tracking]** 选项卡，用于监视对资源执行的任何操作：批准、批准拒绝、相关评论或出版物。

的 **[!UICONTROL History]** 选项卡显示为此资源执行的文件传输。

### 审批流程 {#approval-process}

如果在 **[!UICONTROL Tracking]** 选项卡。 到达此日期后，您可以使用 **[!UICONTROL Submit for approval]** 按钮。 然后，资源状态将更改为 **[!UICONTROL Approval in progress]**.

资源可以通过 **[!UICONTROL Approve resource]** 按钮。

![](assets/s_ncs_user_task_valid_date.png)

然后，授权的运营商可以接受或拒绝批准。 此操作可以：（通过单击通知消息中的链接）或通过控制台(通过单击 **[!UICONTROL Approve]** )按钮。

您可以在审批窗口中输入评论。

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

的 **[!UICONTROL Tracking]** 选项卡，所有操作员都可以跟踪审批流程的各个阶段。

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>除了为每个营销资源指定的审核者之外，具有管理员权限的操作员和资源管理器也被授权批准营销资源。

### 发布资源 {#publishing-a-resource}

批准后，必须发布营销资源。 出版过程必须按照公司要求具体实施。 这意味着资源可以在外联网或任何其他服务器上发布，特定信息可以发送到外部服务提供商等。

要发布资源，请单击 **[!UICONTROL Publish]** 按钮。

![](assets/s_ncs_user_mkg_resource_available.png)

您还可以通过工作流自动发布资源。

发布资源意味着（例如，由其他任务）使其可供使用。 根据资源的性质，发布内容会有所不同：对于传单，发布可能意味着将文件发送到打印机，对于Web代理，发布可能意味着将其发布到网站等。

要使Adobe Campaign发布，您需要创建一个适当的工作流并将其链接到资源。 为此，请打开 **[!UICONTROL Advanced settings]** 框中，然后在 **[!UICONTROL Post-processing]** 字段。

![](assets/mrm_asset_postprocessing_workflow.png)

将执行工作流：

* 当审阅人单击 **[!UICONTROL Publish resource]** 链接（或者，如果未定义审核者，则为资源负责人）。
* 如果资源是通过营销资源创建任务来管理的，则在将该任务设置为 **[!UICONTROL Finished]**，只要 **[!UICONTROL Publish the marketing resource]** 框(请参阅 [营销资源创建任务](../../mrm/using/creating-and-managing-tasks.md#marketing-resource-creation-task))

如果工作流未立即启动（例如，如果工作流已停止），则资源的状态将更改为 **[!UICONTROL Pending publication]**. 启动工作流后，资源的状态将更改为 **[!UICONTROL Published]**. 此状态未考虑发布过程中可能出现的错误。 检查工作流的状态，确保工作流已正确执行。

## 将资源链接到营销活动 {#linking-a-resource-to-a-campaign}

### 引用营销资源 {#referencing-a-marketing-resource}

营销资源可以与营销活动关联，前提是已在营销活动模板中选择此功能。

>[!NOTE]
>
>有关如何创建和配置营销活动模板的详细信息，请参阅 [营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

单击 **[!UICONTROL Documents > Resources]** 选项卡，然后单击 **[!UICONTROL Add]** 选择相关资源。

![](assets/s_ncs_user_mkg_resource_ref.png)

您可以按状态、自然或类型筛选资源，也可以应用个性化筛选器。

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

单击 **[!UICONTROL OK]** 将资源添加到此营销活动引用的营销资源列表。

的 **[!UICONTROL Details]** 按钮来编辑和查看。

添加的资源将显示在功能板中。 也可在此处编辑它们。

### 向投放大纲添加营销资源 {#adding-a-marketing-resource-to-a-delivery-outline}

营销资源可以通过投放大纲与投放相关联。

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>有关投放概述的更多信息，请参阅 [通过投放大纲关联和构建链接的资源](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

## 库存管理 {#stock-management}

您可以将营销资源与一个或多个库存关联，以便管理您的供应，并在库存不足时在仪表板上显示警告。

>[!NOTE]
>
>有关Adobe Campaign股票管理的更多信息，请参阅 [库存管理](../../campaign/using/providers--stocks-and-budgets.md#stock-management).

要将营销资源与库存关联，请编辑库存图并编辑或创建库存。 添加库存行并选择相应的营销资源。

![](assets/s_ncs_user_task_in_a_stock.png)

如有必要，您可以通过 **[!UICONTROL Edit the link]** 图标（放大镜）。

指定初始库存和警报库存，然后保存。

资源详细信息中会指示库存。

![](assets/s_ncs_user_task_with_a_stock.png)

当库存不足时，向相关操作员发送警告。

## 高级功能 {#advanced-functions}

通过“营销资源”功能板，您可以执行常见类型的操作：添加、编辑、锁定/解锁、批准、发布。 您可以创建其他类型的营销资源，并通过Adobe Campaign树访问高级功能。 为此，请单击 **[!UICONTROL Explorer]** 在Adobe Campaign主页中。

默认情况下，营销资源存储在 **[!UICONTROL MRM > Marketing resources]** 树的节点。

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

您可以从此视图添加以下资源：

* 文件
* HTML
* 文本
* URL
