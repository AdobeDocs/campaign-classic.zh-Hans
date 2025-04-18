---
product: campaign
title: 建立和管理审批流程
description: 了解如何管理营销活动的批准
role: User
feature: Approvals, Campaigns
hide: true
hidefromtoc: true
exl-id: 8cbb2445-f5e4-4a25-ba7e-56e39ca9d3ce
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '2437'
ht-degree: 1%

---

# 建立和管理审批流程 {#approving-marketing-campaigns}


投放的每个步骤都可以获得批准，以确保完全监控和控制活动的各个流程：定位、内容、预算、提取和发送证明。

通知消息将发送给Adobe Campaign操作员，这些操作员被指定为审阅者，负责向他们通知批准请求。 检查审阅人是否具有批准所需的&#x200B;**适当权限**，以及是否正确定义了其安全区域。 [了解详情](#selecting-reviewers)。

[本节](#checking-and-approving-deliveries)中介绍了审批程序。

>[!NOTE]
>
>只有投放所有者才能开始投放。 为使另一个操作员（或操作员组）能够开始投放，您必须将其添加为&#x200B;**[!UICONTROL Delivery start:]**&#x200B;字段中的审阅人。\
>[了解详情](#selecting-reviewers)。

## 操作原则 {#operating-principle-}

例如，用于预算审批的标准消息如下：

![](assets/s_user_validation_link_in_mail.png)

之后，审核者操作员可以选择是否批准预算。

![](assets/s_user_validation_page_confirm.png)

操作员验证后，作业的批准或拒绝将被转发到投放仪表板。

![](assets/s_user_validation_link_in_op_board.png)

该信息也可在营销活动的审批日志中找到。这些日志可通过&#x200B;**[!UICONTROL Edit > Tracking > Approvals]**&#x200B;选项卡访问。

![](assets/s_user_validation_log_in_op_edit_tab.png)

这些通知将发送给受影响的操作员，并发送给每个启用了批准的流程。

可以为营销活动模板、单独为每个营销活动或投放启用批准。

所有需要审批的作业都在营销活动模板（**[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]**&#x200B;选项卡）中进行选择，负责审批的操作员也是如此（除非未启用此选项，否则他们将收到通知）。 如需详细信息，请参阅[此小节](#approving-processes)。

可以覆盖使用此模板创建的每个营销活动的这些设置，也可以覆盖每个营销活动投放的这些设置：单击&#x200B;**[!UICONTROL Properties]**&#x200B;按钮，然后单击&#x200B;**[!UICONTROL Approvals]**&#x200B;选项卡。

在以下示例中，投放内容不需要审批：

![](assets/s_user_validation_select_process_from_del.png)

## 选择审阅人 {#selecting-reviewers}

对于每种类型的批准，从投放的下拉列表中选择负责批准的操作员或操作员组。 可以使用&#x200B;**[!UICONTROL Edit...]**&#x200B;链接添加更多运算符。 此窗口还允许您编辑审批截止日期。

![](assets/s_user_validation_add_operator.png)

如果未指定审核者，则活动经理将负责审批并接收通知。 在营销活动的&#x200B;**[!UICONTROL Edit > Properties]**&#x200B;选项卡中指定营销活动管理员：

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>所有其他具有&#x200B;**[!UICONTROL Administrator]**&#x200B;权限的Adobe Campaign操作员也可以批准作业，但他们不会收到通知。\
>默认情况下，如果定义了批准操作员，则活动经理无法执行批准或开始投放。 您可以修改此行为，并通过创建值为&#x200B;**1**&#x200B;的&#x200B;**NmsCampaign_Activate_OwnerConfirmation**&#x200B;选项来授权营销活动经理批准/开始投放。

## 审批模式 {#approval-modes}

### 通过仪表板审批 {#approval-via-the-dashboard}

要通过控制台或Web界面批准作业，请单击活动仪表板上的相应链接。 也可以通过投放跟踪或投放仪表板审批作业。

![](assets/s_user_validation_from_console.png)

检查要批准的信息，选择是接受还是拒绝批准，并根据需要输入备注。 单击&#x200B;**[!UICONTROL Ok]**&#x200B;进行保存。

>[!NOTE]
>
>如果某个流程已被其他操作员批准，则批准链接不可用。

### 通过通知报文审批 {#approval-via-notification-messages}

单击通知消息中可用的链接（请参阅[通知](#notifications)）。 您需要登录，如下所示：

![](assets/s_user_validation__log_in.png)

选择&#x200B;**[!UICONTROL Accept]**&#x200B;或&#x200B;**[!UICONTROL Reject]**，并根据需要输入评论。

![](assets/s_user_validation_save_target_validation.png)

单击 **[!UICONTROL Validate]**。

>[!NOTE]
>
>如果在此过程中出现警告，则通知中会显示警告。

### 审批跟踪 {#approval-tracking}

该信息包括以下几个位置：

* 在营销活动审批日志中，**[!UICONTROL Edit > Tracking]**&#x200B;选项卡的&#x200B;**[!UICONTROL Approvals]**&#x200B;子选项卡：

  ![](assets/s_user_validation_log_from_op.png)

* 在营销活动投放日志中，**[!UICONTROL Edit > Tracking]**&#x200B;选项卡的&#x200B;**[!UICONTROL Deliveries]**&#x200B;子选项卡：

  ![](assets/s_user_validation_log_from_delivery_list.png)

* 单击&#x200B;**[!UICONTROL Summary]**&#x200B;选项卡的&#x200B;**[!UICONTROL Hide/show log]**&#x200B;选项可查看每个投放的批准状态。

  ![](assets/s_user_validation_log_delivery.png)

* 也可以通过每个投放的&#x200B;**[!UICONTROL Tracking > Approvals]**&#x200B;选项卡访问此信息：

  ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>一旦操作员批准或拒绝了任务，其他审核操作员就不能再对批准采取行动。

### 自动和手动审批 {#automatic-and-manual-approval}

在创建定位工作流时，如果批准是自动的（默认模式），Adobe Campaign会显示批准链接，或者在需要批准时立即发送通知。

要选择审批模式（手动或自动），请单击营销活动或营销活动模板的&#x200B;**[!UICONTROL Edit > Properties]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Advanced campaign settings...]**，最后点击&#x200B;**[!UICONTROL Approvals]**&#x200B;选项卡。

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>选定的审批模式将应用于营销活动的所有投放。

在构建定向工作流时，通过手动批准，您可以避免创建批准链接或自动发送通知。 然后，营销活动仪表板提供一个&#x200B;**[!UICONTROL Submit targeting for approval]**&#x200B;链接，以手动启动审批流程。

确认消息允许您授权审批为此投放选择的作业。

然后，审批按钮会显示在活动仪表板（适用于此投放）、投放仪表板和投放跟踪中。 如果启用了通知，则将并行发送这些通知。

这种启用审批的方法允许您在不向审阅人发送虚假通知的情况下进行定位。

## 通知 {#notifications}

通知是发送给审阅人的特定电子邮件，用于通知他们流程正在等待审批。 当操作员单击消息中的链接时，将显示验证页面，登录后，操作员可以查看该信息并批准或拒绝作业。 您还可以在审批窗口中输入备注。

通知电子邮件的内容可以个性化。 查看[通知内容](#notification-content)。

### 启用/禁用通知 {#enabling-disabling-notification}

默认情况下，如果在活动模板、活动或投放中启用了相关作业的审批，则会发送通知消息。 但是，可以禁用通知，以便仅从控制台中授权批准。

为此，请编辑营销活动或营销活动模板的审批窗口（**[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]**&#x200B;选项卡）并选择&#x200B;**[!UICONTROL Do not enable notification sending]**。

![](assets/s_user_validation_notif_desactivate.png)

### 通知内容 {#notification-content}

通知内容是在特定模板中定义的： **[!UICONTROL Notification of validations for the marketing campaign]**。 此模板保存在Adobe Campaign树的&#x200B;**[!UICONTROL Administration > Campaign management > Technical delivery templates]**&#x200B;文件夹中。

## 审阅和批准投放 {#checking-and-approving-deliveries}

Adobe Campaign允许您在协作模式下为营销活动的主要阶段设置审批流程。

对于直邮投放，Adobe Campaign操作员可以在提取文件发送到路由器之前查看该文件，如有必要，他们可以更改格式并重新执行提取。 请参阅[批准提取文件](#approving-an-extraction-file)。

对于每个营销活动，您可以批准投放目标、内容（请参阅[批准内容](#approving-content)）和成本。 负责批准工作的Adobe Campaign操作员收到电子邮件通知后，可通过控制台或Web连接批准或拒绝批准相关请求。 查看批准投放的[步骤](#approving-processes)。

完成这些验证阶段后，可以启动投放。 [了解详情](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)。

### 批准投放的步骤 {#approving-processes}

需要批准的阶段将显示在活动仪表板上（通过Web界面的控制台）。 它们还会显示在投放跟踪表和投放仪表板中。

此时，营销活动的状态为&#x200B;**[!UICONTROL To validate]**。

>[!NOTE]
>
>要选择需要批准的流程，请修改活动模板。 有关详细信息，请参阅[营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。
>

![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>在定向工作流中，如果在消息准备期间发生链接到配置问题的错误，则仪表板上会显示&#x200B;**[!UICONTROL Restart message preparation]**&#x200B;链接。 更正错误，单击此链接在绕过定位阶段时重新启动消息准备。

![](assets/s_user_validation_relaunch_message_preparation.png)

对于活动中的每个投放，您可以批准以下流程：

* **定位、内容和预算**

  在作业审批设置窗口中选择&#x200B;**[!UICONTROL Enable target approval]**、**[!UICONTROL Enable content approval]**&#x200B;或&#x200B;**[!UICONTROL Enable budget approval]**&#x200B;选项后，相关链接将显示在相关投放的活动仪表板中。

  >[!NOTE]
  >
  >仅当在审批设置窗口中启用定向审批时，预算审批才可用。 仅当分析目标后，才会显示预算审批链接。 此外，此链接与用于批准目标的链接一起显示。

  如果在审批设置窗口中选择了&#x200B;**[!UICONTROL Assign content editing]**&#x200B;或&#x200B;**[!UICONTROL External content approval]**&#x200B;选项，则仪表板将显示&#x200B;**[!UICONTROL Available content]**&#x200B;和&#x200B;**[!UICONTROL External content approval]**&#x200B;链接。

  通过内容审批，可访问发送的校样。

* **提取审批（直邮投放）**

  在审批设置窗口中选择&#x200B;**[!UICONTROL Enable extraction approval]**&#x200B;后，必须批准提取的文件，才能通知路由器。

  营销活动信息板上提供了&#x200B;**[!UICONTROL Approve content]**&#x200B;链接，如下所示：

  ![](assets/s_ncs_user_edit_file_valid.png)

  可以通过审批框预览提取文件，然后接受或拒绝。

  ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

  >[!NOTE]
  >
  >提取文件预览仅涉及数据示例。 未加载整个输出文件。

* **批准关联的投放**

  **[!UICONTROL Enable individual approval of each associated delivery]**&#x200B;选项用于与辅助投放相关的一个主投放。 默认情况下，未选中此选项，因此可以对主投放执行整体审批。 如果选择此选项，则必须单独批准每个投放。

  ![](assets/s_ncs_user_task_valid_associate.png)

### 选择审批流程 {#choosing-the-processes-to-be-approved}

使用与活动关联的模板定义审批阶段。 您必须从模板中选择要审批的元素，并指定负责这些审批的Adobe Campaign操作员。 有关营销活动模板的更多信息，请参阅[此章节](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

>[!NOTE]
>
>营销活动（或营销活动模板）的批准配置适用于链接到该营销活动的所有未来投放。 任何配置更改都不会应用于以前的投放。

可以覆盖每个营销活动和每个投放的此类信息。

对于营销活动，依次单击&#x200B;**[!UICONTROL Edit > Properties]**&#x200B;选项卡、**[!UICONTROL Advanced campaign settings...]**&#x200B;链接和&#x200B;**[!UICONTROL Approvals]**&#x200B;子选项卡以访问审批配置页面。

您可以选择和取消选择流程以批准和指定负责批准的Adobe Campaign操作员。 这些可以是单个操作员、一组操作员或操作员列表。

要选择运算符列表，请单击指定第一个审阅人的字段右侧的&#x200B;**[!UICONTROL Edit...]**&#x200B;链接，并根据需要添加任意数量的运算符，如下所示：

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* 如果定义了审阅人列表，则当审阅人接受作业后，即会批准该作业。 然后，仪表板中不再提供相关审批链接。 启用发送通知后，如果其他查看者单击通知消息中的批准链接，则会通知他们其他操作员已批准作业。
>* 您可以在审核者编辑窗口的下半部分中定义活动的审批计划。 默认情况下，审阅人从提交日期起有三天时间来批准流程。 可以配置提醒，该提醒将在批准截止日期前自动发送给相关操作员。
>* 您可以从此分区添加提醒。
>

![](assets/s_ncs_user_edit_op_valid_calendar.png)

对于每个投放，单击&#x200B;**[!UICONTROL Audit]**&#x200B;按钮和&#x200B;**[!UICONTROL Approvals]**&#x200B;选项卡以查看和编辑批准日期及自动提醒。

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>一旦启动内容审批流程，此选项卡即可使用。

### 批准内容 {#approving-content}

>[!CAUTION]
>
>要批准内容，验证周期是必需的。 校样允许您批准显示信息和个性化数据，并检查链接是否正常工作。 在[本节](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)中了解如何创建校对。
>
>下面详述的内容审批功能与验证投放相关。

可以配置内容批准周期。 为此，请在审批设置窗口中选择&#x200B;**[!UICONTROL Enable content approval]**&#x200B;选项。 内容审批周期的主要步骤包括：

1. 创建新投放后，活动经理可单击活动仪表板上的&#x200B;**[!UICONTROL Submit content]**&#x200B;链接以开始内容审批周期。

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >如果在审批设置窗口中选择了&#x200B;**[!UICONTROL Enable the sending of proofs]**&#x200B;选项（用于电子邮件投放）或&#x200B;**[!UICONTROL Enable the sending and approval of proofs]**&#x200B;选项（用于直邮投放），则将自动发送校样。

1. 通知电子邮件将发送给负责内容的人员，他们可以选择是否批准内容：

   * 通过通知电子邮件：

     ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

     >[!NOTE]
     >
     >通知电子邮件包含指向已发送校样的链接，如果为此实例启用了&#x200B;**可投放性**&#x200B;选项，则可能包含指向各种网页邮件的邮件渲染的链接。

   * 通过控制台或web界面、投放跟踪、投放仪表板或活动仪表板：

     ![](assets/s_ncs_user_validation_content_bat_op.png)

     >[!NOTE]
     >
     >此营销活动信息板允许您通过单击&#x200B;**[!UICONTROL Inbox rendering...]**&#x200B;链接查看已发送的验证列表。 要查看其内容，请单击列表右侧的&#x200B;**[!UICONTROL Detail]**&#x200B;图标。

     ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. 将向营销策划负责人发送通知电子邮件，告知他们内容是否已被批准。

   >[!NOTE]
   >
   >活动负责人可以随时重新开始内容审批周期。 为此，请单击Campaign仪表板的&#x200B;**[!UICONTROL Content status]**&#x200B;行（在投放级别）上的链接，然后单击&#x200B;**[!UICONTROL Reset content approval to submit it again]**。

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### 分配内容编辑 {#assign-content-editing}

利用此选项，可定义负责内容编辑的人员，如网站管理员。 如果在审批设置窗口中选择了&#x200B;**[!UICONTROL Assign content editing]**&#x200B;选项，则在投放创建和将通知电子邮件交付给内容负责人之间会添加多个审批步骤：

1. 创建新投放后，营销活动负责人单击营销活动仪表板中的&#x200B;**[!UICONTROL Submit content editing]**&#x200B;链接以开始内容编辑周期。

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. 负责内容编辑的人员将收到一封电子邮件，告知他们内容可用。

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. 然后，他们可以登录到控制台，打开投放并使用简化的助手进行编辑，以更改主题、HTML和文本内容，并发送校样。

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >如果在审批设置窗口中选择了&#x200B;**[!UICONTROL Enable the sending of proofs]**&#x200B;选项（用于电子邮件投放）或&#x200B;**[!UICONTROL Enable the sending and approval of proofs]**&#x200B;选项（用于直邮投放），则将自动发送校样。

1. 一旦负责内容编辑的人员完成对投放内容的任何更改，他们就可以使内容可用。

   为此，他们可以：

   * 通过Adobe Campaign控制台单击&#x200B;**[!UICONTROL Available content]**&#x200B;链接。

     ![](assets/s_ncs_user_validation_submit_content_available.png)

   * 单击通知消息中的链接，然后批准内容可用性。

     ![](assets/s_ncs_user_validation_submit_content_available2.png)

     操作员可在将内容提交到活动负责人之前添加评论。

     ![](assets/s_ncs_user_validation_submit_content_available3.png)

     通知消息允许审阅人批准或拒绝内容。

     ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### 外部内容审批 {#external-content-approval}

利用此选项，可定义负责审批投放呈现的外部操作员，如品牌通信一致性、费率等。 在审批设置窗口中选择&#x200B;**[!UICONTROL External content approval]**&#x200B;选项后，在内容审批和将通知交付给活动负责人之间会添加多个审批步骤：

1. 外部内容经理会收到通知电子邮件，告知他们内容已获批准并请求外部批准。
1. 通知电子邮件包含指向已发送校样的链接（允许您查看投放渲染），以及一个用于批准或拒绝投放内容的按钮。

   >[!NOTE]
   >
   >这些链接仅在发送了一个或多个验证后才可用。 否则，只能通过控制台或Web界面进行投放渲染。

   ![](assets/s_user_validation_external_content.png)

### 批准提取文件 {#approving-an-extraction-file}

对于离线投放，Adobe Campaign会生成一个提取文件，并根据其设置方式将其发送到路由器。 其内容取决于所使用的导出模板。

内容、目标和预算获得批准后，投放将更改为&#x200B;**[!UICONTROL Extraction pending]**，直到启动营销活动的提取工作流为止。

![](assets/s_ncs_user_waiting_file_extraction.png)

在提取请求日期创建提取文件，并且投放状态更改为&#x200B;**[!UICONTROL File to approve]**。

![](assets/s_ncs_user_file_extract_to_valid.png)

您可以查看提取文件的内容（通过单击其名称）、批准该文件，或者在必要时使用功能板上的链接更改格式并重新开始提取。

文件获得批准后，即可向路由器发送通知电子邮件。 有关详细信息，请参阅[开始离线投放](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery)。
