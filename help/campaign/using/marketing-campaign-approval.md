---
product: campaign
title: 建立和管理审批流程
description: 了解如何管理营销活动的批准
feature: Approvals, Campaigns
exl-id: 8cbb2445-f5e4-4a25-ba7e-56e39ca9d3ce
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '2438'
ht-degree: 2%

---

# 建立和管理审批流程 {#approving-marketing-campaigns}

![](../../assets/v7-only.svg)

投放的每个步骤都可以获得批准，以确保完全监控和控制营销活动的各个流程：定位、内容、预算、提取和发送证明。

通知消息将发送给Adobe Campaign操作员，他们作为指定的审阅人，负责通知他们有关批准请求的信息。 检查审阅人是否拥有 **适当的权限** ，并确保正确定义了它们的安全区域。 [了解详情](#selecting-reviewers)。

有关批准程序的详情，请参见 [本节](#checking-and-approving-deliveries).

>[!NOTE]
>
>只有投放所有者可以开始投放。 为了使其他操作员（或操作员组）能够开始投放，您必须将他们作为审阅人添加到 **[!UICONTROL Delivery start:]** 字段。\
>[了解详情](#selecting-reviewers)。

## 操作原则 {#operating-principle-}

例如，预算审批的标准消息如下：

![](assets/s_user_validation_link_in_mail.png)

然后，审核者操作员可以选择是否批准预算。

![](assets/s_user_validation_page_confirm.png)

操作员验证后，作业的批准或拒绝将被转发到投放仪表板。

![](assets/s_user_validation_link_in_op_board.png)

该信息还可在营销策划的批准日志中找到。这些日志可通过 **[!UICONTROL Edit > Tracking > Approvals]** 选项卡。

![](assets/s_user_validation_log_in_op_edit_tab.png)

这些通知将发送给每个启用审批的流程中受影响的操作员。

可以为营销活动模板、单独为每个营销活动或投放启用批准。

在营销活动模板中选择了所有需要审批的作业( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** 选项卡)，负责审批的操作员也会收到通知（除非未启用此选项）。 如需详细信息，请参阅[此部分](#approving-processes)。

可以覆盖使用此模板创建的每个营销策划的这些设置，也可以分别覆盖每个营销策划的投放：单击 **[!UICONTROL Properties]** 按钮，然后 **[!UICONTROL Approvals]** 选项卡。

在以下示例中，投放内容不需要审批：

![](assets/s_user_validation_select_process_from_del.png)

## 选择审阅人 {#selecting-reviewers}

对于每种类型的批准，从投放的下拉列表中选择负责批准的操作员或操作员组。 可以使用添加更多运算符 **[!UICONTROL Edit...]** 链接。 利用此窗口，您还可以编辑审批截止日期。

![](assets/s_user_validation_add_operator.png)

如果未指定审核者，则营销活动经理将负责审批并接收通知。 促销活动管理器指定于 **[!UICONTROL Edit > Properties]** 的选项卡：

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>所有其他Adobe Campaign运算符，具有 **[!UICONTROL Administrator]** 权限也可以批准作业，但不会收到通知。\
>默认情况下，如果定义了审批操作员，营销活动经理将无法执行审批或开始投放。 您可以修改此行为并通过创建 **NmsCampaign_Activate_OwnerConfirmation** 选项和 **1** 作为值。

## 审批模式 {#approval-modes}

### 通过仪表板审批 {#approval-via-the-dashboard}

要通过控制台或Web界面批准作业，请单击营销活动仪表板上的相应链接。 作业也可以通过投放跟踪或投放仪表板进行批准。

![](assets/s_user_validation_from_console.png)

检查要批准的信息，选择是接受还是拒绝批准，并根据需要输入备注。 单击 **[!UICONTROL Ok]** 以保存。

>[!NOTE]
>
>如果某个流程已被其他操作员批准，则批准链接不可用。

### 通过通知报文审批 {#approval-via-notification-messages}

单击通知消息中可用的链接(请参阅 [通知](#notifications))。 您需要登录，如下所示：

![](assets/s_user_validation__log_in.png)

选择 **[!UICONTROL Accept]** 或 **[!UICONTROL Reject]** 并根据需要输入评论。

![](assets/s_user_validation_save_target_validation.png)

单击 **[!UICONTROL Validate]**。

>[!NOTE]
>
>如果在此过程中出现警告，则通知中会显示警告。

### 审批跟踪 {#approval-tracking}

该信息在以下几个位置提供：

* 在营销活动批准日志中， **[!UICONTROL Approvals]** 的子选项卡 **[!UICONTROL Edit > Tracking]** 选项卡：

   ![](assets/s_user_validation_log_from_op.png)

* 在营销活动投放日志中， **[!UICONTROL Deliveries]** 的子选项卡 **[!UICONTROL Edit > Tracking]** 选项卡：

   ![](assets/s_user_validation_log_from_delivery_list.png)

* 通过单击 **[!UICONTROL Hide/show log]** 的选项 **[!UICONTROL Summary]** 选项卡。

   ![](assets/s_user_validation_log_delivery.png)

* 此信息也可通过 **[!UICONTROL Tracking > Approvals]** 选项卡中显示的每个投放：

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>一旦操作员批准或拒绝了任务，其他审核操作员就不能再对批准执行操作。

### 自动和手动批准 {#automatic-and-manual-approval}

在创建定位工作流时，如果批准是自动的（默认模式），Adobe Campaign会显示批准链接，或者在需要批准时立即发送通知。

要选择审批模式（人工或自动），请单击 **[!UICONTROL Edit > Properties]** 选项卡，然后单击 **[!UICONTROL Advanced campaign settings...]** 最后 **[!UICONTROL Approvals]** 选项卡。

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>选定的审批模式将应用于营销活动的所有投放。

在构建定位工作流时，通过手动批准，您可以避免创建批准链接或自动发送通知。 然后，营销活动仪表板提供 **[!UICONTROL Submit targeting for approval]** 链接，以手动启动批准流程。

通过确认消息，可授权审批为此投放选择的作业。

然后，审批按钮会显示在活动仪表板（适用于此投放）、投放仪表板和投放跟踪中。 如果启用了通知，则将并行发送这些通知。

通过启用批准这一方法，您无需向审阅人发送虚假通知，即可确定目标。

## 通知 {#notifications}

通知是发送给审阅人的特定电子邮件，用于通知他们流程正在等待审批。 当操作员单击消息中的链接时，将显示一个身份验证页面，登录后，操作员可以查看该信息并批准或拒绝作业。 您还可以在审批窗口中输入备注。

通知电子邮件的内容可以个性化。 参见 [通知内容](#notification-content).

### 启用/禁用通知 {#enabling-disabling-notification}

默认情况下，如果在活动模板、活动或投放中启用了相关作业的审批，则会发送通知消息。 但是，可以禁用通知，以便仅从控制台中授权审批。

要执行此操作，请编辑活动或活动模板的批准窗口( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** 选项卡)并选择 **[!UICONTROL Do not enable notification sending]**.

![](assets/s_user_validation_notif_desactivate.png)

### 通知内容 {#notification-content}

通知内容是在特定模板中定义的： **[!UICONTROL Notification of validations for the marketing campaign]**. 此模板保存在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** Adobe Campaign树的文件夹。

## 审阅和批准投放 {#checking-and-approving-deliveries}

Adobe Campaign允许您以协作模式为营销活动的主要阶段设置审批流程。

对于直邮投放，Adobe Campaign操作员可以在提取文件发送到路由器之前查看该文件，如有必要，他们可以更改格式并重新提取该文件。 参见 [批准提取文件](#approving-an-extraction-file).

对于每个活动，您可以批准投放目标、内容(请参阅 [批准内容](#approving-content))和成本。 负责审批工作的 Adobe Campaign 操作员收到电子邮件通知后，可通过控制台或 Web 连接批准或拒绝批准相关请求。参见 [批准投放的步骤](#approving-processes).

当这些验证阶段完成后，可以启动投放。 [了解详情](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)。

### 批准投放的步骤 {#approving-processes}

需要批准的阶段将显示在Campaign仪表板上（通过Web界面的控制台）。 它们还会显示在投放跟踪表和投放仪表板中。

此时，营销活动的状态为 **[!UICONTROL To validate]**.

>[!NOTE]
>
>要选择需要批准的流程，请修改活动模板。 有关更多信息，请参阅 [营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>在定向工作流中，如果在消息准备期间发生链接到配置问题的错误，则 **[!UICONTROL Restart message preparation]** 链接将显示在功能板上。 更正错误，单击此链接可在绕过定位阶段时重新开始消息准备。

![](assets/s_user_validation_relaunch_message_preparation.png)

对于营销活动中的每次投放，您可以批准以下流程：

* **定位、内容和预算**

   当 **[!UICONTROL Enable target approval]**， **[!UICONTROL Enable content approval]** 或 **[!UICONTROL Enable budget approval]** 在作业审批设置窗口中选择选项，相关链接将显示在相关投放的营销活动仪表板中。

   >[!NOTE]
   >
   >仅当在审批设置窗口中启用定向审批时，预算审批才可用。 仅当分析目标后，才会显示预算审批链接。 此外，此链接与用于目标审批的链接一起显示。

   如果 **[!UICONTROL Assign content editing]** 或 **[!UICONTROL External content approval]** 在审批设置窗口中选择选项，仪表板将显示 **[!UICONTROL Available content]** 和 **[!UICONTROL External content approval]** 链接。

   通过内容审批，您可以访问发送的校样。

* **提取审批（直邮投放）**

   时间 **[!UICONTROL Enable extraction approval]** 在批准设置窗口中选择，提取的文件必须先获得批准，然后才能通知路由器。

   An **[!UICONTROL Approve content]** campaign功能板上的链接可用，如下所示：

   ![](assets/s_ncs_user_edit_file_valid.png)

   可以通过批准框预览提取文件，然后接受或拒绝提取文件。

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >提取文件预览仅涉及数据示例。 未加载整个输出文件。

* **批准关联的投放**

   此 **[!UICONTROL Enable individual approval of each associated delivery]** 选项用于与二级投放相关的一个主投放。 默认情况下，不会选中此选项，因此可以对主投放执行整体审批。 如果选择此选项，则必须单独批准每个投放。

   ![](assets/s_ncs_user_task_valid_associate.png)

### 选择流程审批 {#choosing-the-processes-to-be-approved}

审批阶段使用与活动关联的模板进行定义。 您必须从模板中选择要审批的元素，并指定负责这些审批的Adobe Campaign操作员。 有关活动模板的更多信息，请参阅 [本节](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>营销活动（或营销活动模板）的批准配置适用于链接到该营销活动的所有未来投放。 任何配置更改都不会应用于以前的投放。

可以为每个营销活动和每个投放覆盖此信息。

对于营销策划，单击 **[!UICONTROL Edit > Properties]** 选项卡，然后 **[!UICONTROL Advanced campaign settings...]** 链接，最后 **[!UICONTROL Approvals]** 用于访问审批配置页面的子选项卡。

您可以选择和取消选择用于批准和指定负责批准工作的Adobe Campaign操作员的流程。 这些可以是单个操作员、一组操作员或操作员列表。

要选择运算符列表，请单击 **[!UICONTROL Edit...]** 链接到指定第一个审阅人的字段的右侧，并根据需要添加任意数量的运算符，如下所示：

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* 如果定义了审阅人列表，则当一个审阅人接受某个作业时，即会批准该作业。 然后，仪表板中不再提供相关审批链接。 启用通知发送后，如果其他审阅人单击通知消息中的批准链接，则会通知他们其他操作员已批准作业。
>* 您可以在审核者编辑窗口的下半部分定义活动的审批计划。 默认情况下，审核者从提交日期起有三天时间来批准流程。 可以配置提醒，该提醒会在批准截止日期之前自动发送给相关操作员。
>* 您可以从此部分添加提醒。
>


![](assets/s_ncs_user_edit_op_valid_calendar.png)

对于每个投放，单击 **[!UICONTROL Audit]** 按钮和 **[!UICONTROL Approvals]** 选项卡以查看和编辑批准日期和自动提醒。

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>一旦启动内容审批流程，此选项卡即可使用。

### 批准内容 {#approving-content}

>[!CAUTION]
>
>要批准内容，验证周期是必需的。 校样允许您批准显示信息和个性化数据，并检查链接是否正常工作。 了解如何在中创建验证 [本节](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).
>
>下面详述的内容审批功能与证明交付相关。

可以配置内容批准周期。 要执行此操作，请选择 **[!UICONTROL Enable content approval]** 选项。 内容审批周期的主要步骤包括：

1. 创建新投放后，营销活动经理单击 **[!UICONTROL Submit content]** 活动仪表板上的链接，以开始内容审批周期。

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Enable the sending of proofs]** 选项（用于电子邮件投放）或 **[!UICONTROL Enable the sending and approval of proofs]** （对于直邮投放）选项已在审批设置窗口中选择，验证将自动发送。

1. 通知电子邮件将发送给负责内容的人员，他们可以选择是否批准该内容：

   * 通过通知电子邮件：

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >通知电子邮件包含指向已发送校样的链接，并且如果 **可投放性** 选项已为此实例启用。

   * 通过控制台或Web界面、投放跟踪、投放仪表板或营销活动仪表板：

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >利用此营销活动信息板，您可以通过单击 **[!UICONTROL Inbox rendering...]** 链接。 要查看其内容，请单击 **[!UICONTROL Detail]** 图标。

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. 将向营销策划负责人发送通知电子邮件，通知他们内容是否已被批准。

   >[!NOTE]
   >
   >营销活动的负责人可以随时重新开始内容审批周期。 要执行此操作，请单击 **[!UICONTROL Content status]** 营销活动仪表板的行（在投放级别），然后单击 **[!UICONTROL Reset content approval to submit it again]**.

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### 分配内容编辑 {#assign-content-editing}

利用此选项，可定义负责内容编辑的人员，如网站管理员。 如果 **[!UICONTROL Assign content editing]** 在审批设置窗口中选择了选项，则在投放创建和将通知电子邮件交付给负责内容的人之间添加了多个审批步骤：

1. 创建新投放后，活动负责人单击 **[!UICONTROL Submit content editing]** campaign仪表板中的链接，以开始内容编辑周期。

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. 负责内容编辑的人员将收到一封电子邮件，告诉他们内容可用。

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. 然后，他们可以登录到控制台，打开投放并使用简化的向导进行编辑，以更改主题、HTML和文本内容，并发送校样。

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Enable the sending of proofs]** 选项（用于电子邮件投放）或 **[!UICONTROL Enable the sending and approval of proofs]** （对于直邮投放）选项已在审批设置窗口中选择，验证将自动发送。

1. 一旦负责内容编辑的人员完成对投放内容的任何更改，他们就可以使内容可用。

   为此，他们可以：

   * 单击 **[!UICONTROL Available content]** 通过Adobe Campaign控制台进行链接。

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * 单击通知消息中的链接，然后审批内容可用性。

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      操作员可在将内容提交到营销策划负责人之前添加评论。

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      通知消息允许审阅人批准或拒绝内容。

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### 外部内容审批 {#external-content-approval}

利用此选项，可定义负责批准投放呈现（如品牌通信一致性、费率等）的外部操作员。 当 **[!UICONTROL External content approval]** 在审批设置窗口中选择选项，则在内容审批和将通知交付给活动负责人之间添加了多个审批步骤：

1. 外部内容经理会收到通知电子邮件，告知他们内容已获批准并请求外部批准。
1. 通知电子邮件包含指向已发送校样的链接（用于查看投放渲染），以及一个用于批准或拒绝投放内容的按钮。

   >[!NOTE]
   >
   >这些链接仅在发送了一个或多个验证后才可用。 否则，只能通过控制台或Web界面进行投放渲染。

   ![](assets/s_user_validation_external_content.png)

### 批准提取文件 {#approving-an-extraction-file}

对于离线投放，Adobe Campaign会生成一个提取文件，并根据其设置方式将其发送到路由器。 其内容取决于所使用的导出模板。

内容、目标和预算获得批准后，交付将更改为 **[!UICONTROL Extraction pending]** 直到启动营销活动的提取工作流为止。

![](assets/s_ncs_user_waiting_file_extraction.png)

在提取请求日期，将创建提取文件并更改投放状态 **[!UICONTROL File to approve]**.

![](assets/s_ncs_user_file_extract_to_valid.png)

您可以查看提取文件的内容（通过单击其名称）、批准该文件，或者在必要时，使用功能板上的链接更改格式并重新启动提取。

文件获得批准后，即可向路由器发送通知电子邮件。 有关更多信息，请参阅 [开始离线投放](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery).
