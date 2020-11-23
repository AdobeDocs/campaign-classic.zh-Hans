---
solution: Campaign Classic
product: campaign
title: 批准营销活动
description: 批准营销活动
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2476'
ht-degree: 1%

---

# 批准营销活动 {#approving-marketing-campaigns}

## 批准流程 {#approval-process}

投放的每个步骤均须经批准，以确保全面监控活动的各个流程：定位、内容、预算、提取和发送验证。

>[!NOTE]
>
>您需要检查审阅者是否具有相应的批准权限。 同时检查其安全区域是否已正确定义。

通知电子邮件会发送给被指定审阅者的Adobe Campaign操作员，以通知他们批准请求。

审批过程显示在 [检查和审批投放](#checking-and-approving-deliveries)。

>[!NOTE]
>
>只有投放所有者才能开始投放。 为了使其他运算符（或运算符组）能够开始投放，您必须在字段中将其添加为审阅 **[!UICONTROL Delivery start:]** 者。\
>另请参阅选 [择审阅者](#selecting-reviewers)。

### 工作原理 {#operating-principle-}

例如，用于预算审批的标准电子邮件将如下所示：

![](assets/s_user_validation_link_in_mail.png)

然后，审阅者操作员可以选择是否批准相关步骤。

![](assets/s_user_validation_page_confirm.png)

一旦运营商批准其选择，就会将作业的批准或拒绝转发给投放仪表板。

![](assets/s_user_validation_link_in_op_board.png)

活动的批准日志中也提供此信息(通过选项卡访 **[!UICONTROL Edit > Tracking > Approvals]** 问):

![](assets/s_user_validation_log_in_op_edit_tab.png)

这些通知将发送给受其启用审批的每个流程影响的操作员。

可以为活动模板、单独为每个活动或投放启用批准。

所有需要批准的作业都在活动模板( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** >选 **[!UICONTROL Approvals]** 项卡)中选择，负责批准的操作员也是如此（除非未启用此选项，否则他们将收到通知）。 For more on this, refer to [Approving processes](#approving-processes).

可以使用此模板创建的每个活动都可以覆盖这些设置，对于每个活动投放也可以分别覆盖这些设置：单击按 **[!UICONTROL Properties]** 钮，然后单击选 **[!UICONTROL Approvals]** 项卡。

在以下示例中，投放内容将不需要批准：

![](assets/s_user_validation_select_process_from_del.png)

### 选择审阅者 {#selecting-reviewers}

对于每种类型的批准，负责批准的操作员或操作员组从投放的下拉列表中进行选择。 可以使用链接添加其他运 **[!UICONTROL Edit...]** 算符。 此窗口还允许您编辑审批截止日期。

![](assets/s_user_validation_add_operator.png)

如果未指定审核者，活动经理将负责审批并接收通知。 活动管理器在活动的 **[!UICONTROL Edit > Properties]** 选项卡中指定：

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>所有其他具有权限的Adobe Campaign **[!UICONTROL Administrator]** 操作员也可以批准作业，但他们不会收到通知。\
>默认情况下，如果已定义审批操作符，活动管理者将无法执行投放批准或开始。 您可以修改此行为并授权活动管理器批准/开始投放，方 **法是创建NmsCampaign_Activate_OwnerConfirmation** 选 **项(值** 为1)。

### 批准模式 {#approval-modes}

#### 通过仪表板批准 {#approval-via-the-dashboard}

要通过控制台或Web界面批准作业，请单击活动仪表板上的相应链接。 还可以通过投放跟踪或投放仪表板批准作业。

![](assets/s_user_validation_from_console.png)

检查要批准的信息，选择是接受还是拒绝批准，并根据需要输入评论。 单击 **[!UICONTROL Ok]** 保存。

>[!NOTE]
>
>如果某个流程已经由其他操作员批准，则该批准链接将不可用。

#### 通过通知消息进行批准 {#approval-via-notification-messages}

单击通知消息中可用的链接(请参 [阅通](#notifications)知)。 系统将要求您识别自己的身份，如下所示：

![](assets/s_user_validation__log_in.png)

选择 **[!UICONTROL Accept]** 或 **[!UICONTROL Reject]** 者根据需要输入评论。

![](assets/s_user_validation_save_target_validation.png)

单击 **[!UICONTROL Validate]**.

>[!NOTE]
>
>如果在该过程中引发警告，则通知中会显示警告。

#### 批准跟踪 {#approval-tracking}

信息可在以下几个位置获取：

* 在活动批准日志 **[!UICONTROL Approvals]** 中，选项卡的子选 **[!UICONTROL Edit > Tracking]** 项卡：

   ![](assets/s_user_validation_log_from_op.png)

* 在活动投放日志 **[!UICONTROL Deliveries]** 中，选项卡的子选 **[!UICONTROL Edit > Tracking]** 项卡：

   ![](assets/s_user_validation_log_from_delivery_list.png)

* 单击选项卡的选项可查看每个投放 **[!UICONTROL Hide/show log]** 的批准 **[!UICONTROL Summary]** 状态。

   ![](assets/s_user_validation_log_delivery.png)

* 此信息还可以通过每个投放 **[!UICONTROL Tracking > Approvals]** 的选项卡访问：

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>一旦操作员批准或拒绝了某个作业，其他审核操作员就不能再对批准采取行动。

#### 自动和手动批准 {#automatic-and-manual-approval}

在创建定位工作流时，如果批准是自动的（默认模式）,Adobe Campaign将显示批准链接或在需要批准时发送通知。

要选择批准模式（手动或自动），请单击活动或 **[!UICONTROL Edit > Properties]** 活动模板的选项卡，然后单 **[!UICONTROL Advanced campaign settings...]** 击，最后单 **[!UICONTROL Approvals]** 击选项卡。

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>选定的批准模式将适用于活动的所有投放。

在构建定位工作流时，手动批准可让您避免创建批准链接或自动发送通知。 然后，活动仪表板将优惠 **[!UICONTROL Submit targeting for approval]** 一个链接，以手动启动批准流程。

系统会显示一条确认消息，允许您对为此投放选择的作业进行批准。

然后，活动仪表板(对于此投放)、投放仪表板和投放跟踪中都会显示批准按钮。 如果通知处于启用状态，则它们将并行发送。

这种启用审批的方法可让您处理定位，而不向审阅者发送虚假通知。

### 通知 {#notifications}

通知是发送给审阅者的特定电子邮件消息，用于通知审阅者某个流程正在等待批准。 当操作员单击消息中的链接时，将显示一个身份验证页，登录后，操作员可以视图信息并批准或拒绝作业。 也可以在审批窗口中输入评论。

通知电子邮件的内容可以个性化。 请参阅 [通知内容](#notification-content)。

#### 启用／禁用通知 {#enabling-disabling-notification}

默认情况下，如果在活动模板、活动或投放中启用了相关作业的批准，则会发送通知消息。 但是，可以禁用通知，以便仅从控制台授权批准。

为此，请编辑活动或活动模板的批准窗口( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** >选 **[!UICONTROL Approvals]** 项卡)并选 **[!UICONTROL Do not enable notification sending]**&#x200B;择。

![](assets/s_user_validation_notif_desactivate.png)

#### 通知内容 {#notification-content}

通知内容在特定模板中定义： **[!UICONTROL Notification of validations for the marketing campaign]**. 此模板将保存在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** Adobe Campaign树的文件夹中。

## 检查和批准投放 {#checking-and-approving-deliveries}

Adobe Campaign允许您以协作模式为营销活动的主要阶段设置审批流程。

对于直邮投放,Adobe Campaign操作员可以在将提取文件发送到路由器之前对其进行视图，如有必要，他们可以更改格式并重新启动提取。 请参 [阅批准提取文件](#approving-an-extraction-file)。

对于每个活动，您可以批准投放目标、内容(请 [参阅批准](#approving-content)内容)和成本。 负责批准工作的 Adobe Campaign 操作员收到电子邮件通知后，可通过控制台或 Web 连接批准或拒绝批准相关请求。请参阅 [批准流程](#approving-processes)。

当这些验证阶段完成时，可以启动投放。 请参 [阅启动投放](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)。

>[!NOTE]
>
>有关批准模式和跟踪的更多信息，请参阅 [批准流程](#approval-process)。

### 批准流程 {#approving-processes}

需要批准的阶段显示在活动仪表板中（通过Web界面的控制台）。 它们还显示在投放跟踪表和投放仪表板中。

此时，活动的状态为 **[!UICONTROL To validate]**。

>[!NOTE]
>
>* 要选择要审批的流程，请修改活动模板。 For more on this, refer to [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).
   >
   >
* 另请参阅“审批”流程 [的一节](#approval-process)。



![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>在定位工作流中，如果在准备消息时出现链接到配置问题的错误，则链 **[!UICONTROL Restart message preparation]** 接会显示在仪表板上。 更正错误并单击此链接，以在绕过定位阶段时重新开始消息准备。

![](assets/s_user_validation_relaunch_message_preparation.png)

对于活动中的每个投放，您可以批准以下流程：

* **定位、内容和预算**

   在任务 **[!UICONTROL Enable target approval]**&#x200B;批准 **[!UICONTROL Enable content approval]** 设置窗 **[!UICONTROL Enable budget approval]** 口中选择或选项后，相关投放的活动仪表板中会显示相关链接。

   >[!NOTE]
   >
   >只有在批准设置窗口中启用了定位批准，预算批准才可用。 仅在分析目标后，才会显示预算审批链接。 此外，此链接会与链接一起显示以供目标批准。

   如果在 **[!UICONTROL Assign content editing]** 批准 **[!UICONTROL External content approval]** 设置窗口中选择了或选项，仪表板将显示 **[!UICONTROL Available content]** 和链 **[!UICONTROL External content approval]** 接。

   内容批准允许您访问发送的验证。

* **提取批准(直邮投放)**

   当在 **[!UICONTROL Enable extraction approval]** 批准设置窗口中选择时，必须先批准提取的文件，然后才能通知路由器。

   活动 **[!UICONTROL Approve content]** 仪表板上有链接，如下所示：

   ![](assets/s_ncs_user_edit_file_valid.png)

   提取文件可通过批准框预览，然后接受或拒绝。

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >提取文件预览仅涉及数据示例。 不加载整个输出文件。

* **批准关联投放**

   该选 **[!UICONTROL Enable individual approval of each associated delivery]** 项用于与辅助投放关联的一个主投放。 默认情况下，不选择此选项，以便能够执行主投放的整体批准。 如果选择此选项，则必须单独批准每个投放。

   ![](assets/s_ncs_user_task_valid_associate.png)

#### 选择要批准的流程 {#choosing-the-processes-to-be-approved}

审批阶段是使用与活动关联的模板定义的。 您必须从模板中选择要批准的元素，并指定负责这些批准的Adobe Campaign操作员。 For more on this, refer to [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>活动或活动模板的批准配置将应用于链接到此活动的所有未来投放。 任何配置更改都不会应用于以前的投放。

此信息可以覆盖每个活动和每个投放。

对于活动，单 **[!UICONTROL Edit > Properties]** 击选项卡、链 **[!UICONTROL Advanced campaign settings...]** 接和子选项 **[!UICONTROL Approvals]** 卡，以访问批准配置页。

您可以选择和取消选择批准和指定负责批准的Adobe Campaign操作员的流程。 这些运算符可以是单个运算符、操作员组或列表运算符。

要选择操作符列表，请单 **[!UICONTROL Edit...]** 击指定第一个审阅者的字段右侧的链接，并根据需要添加任意数量的操作符，如下所示：

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* 如果定义了审阅者列表，则一旦某个审阅者接受了该作业，就会批准该作业。 该仪表板中不再提供相关批准链接。 启用通知发送后，如果其他审阅者单击通知消息中的批准链接，则会通知他们其他操作员已经批准了作业。
>* 您可以在审阅者编辑窗口的下部为活动定义审批计划。 默认情况下，审阅者从提交日期开始有三天时间批准流程。 可以配置提醒，提醒在批准截止日期之前自动发送给相关操作员。
>* 您可以从此部分添加提醒。

>



![](assets/s_ncs_user_edit_op_valid_calendar.png)

对于每个投放，单击按 **[!UICONTROL Audit]** 钮和选 **[!UICONTROL Approvals]** 项卡以视图和编辑批准日期以及自动提醒。

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>内容批准过程启动后，此选项卡即可用。

### 批准内容 {#approving-content}

>[!CAUTION]
>
>要批准内容，必须执行验证周期。 验证允许您批准信息显示、个性化数据并检查链接是否有效。 有关创建验证及其生命周期的详细信息，请参 [阅发送消息](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) 。
>
>下面详述的内容批准功能旨在添加到验证投放。

可以配置内容审批周期。 为此，请在批准设 **[!UICONTROL Enable content approval]** 置窗口中选择选项。 内容审批周期的主要步骤是：

1. 创建新投放后，活动管理器单击 **[!UICONTROL Submit content]** 活动仪表板上的链接以开始内容审批周期。

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >如果在 **[!UICONTROL Enable the sending of proofs]** 批准设置窗口中选 **[!UICONTROL Enable the sending and approval of proofs]** 择了选项(对于电子邮件投放)或(对于直接邮件投放)，则会自动发送验证。

1. 系统会向负责内容的人员发送通知电子邮件，该人员可以选择是否批准该内容：

   * 通过通知电子邮件：

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >通知电子邮件包含指向已发送验证的链接，如果为此实例启用了“可交付性”选项，则可能还包含指向各 **个Web邮件** 消息呈现的链接。

   * 通过控制台或Web界面、投放跟踪、投放仪表板或活动仪表板:

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >此活动仪表板允许您通过单击链接视图已发送的验证的 **[!UICONTROL Inbox rendering...]** 列表。 要视图其内容，请 **[!UICONTROL Detail]** 单击列表右侧的图标。

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. 系统会向负责活动的人员发送通知电子邮件，通知他们内容是否已获得批准。

   >[!NOTE]
   >
   >负责活动的人员可以随时重新开始内容审批周期。 为此，请单击活动仪表板行( **[!UICONTROL Content status]** 在投放级别)上的链接，然后单击 **[!UICONTROL Reset content approval to submit it again]**。

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### 分配内容编辑 {#assign-content-editing}

通过此选项，您可以定义负责内容编辑的人员，如网站管理员。 如果在 **[!UICONTROL Assign content editing]** 批准设置窗口中选择了此选项，则在向负责内容的人员创建通知电子邮件的投放和投放通知电子邮件之间会添加几个批准步骤：

1. 创建新投放后，负责活动的人员单击活动 **[!UICONTROL Submit content editing]** 仪表板中的链接以开始内容编辑周期。

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. 负责内容编辑的人员将收到一封电子邮件，告知他们内容可用。

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. 然后，他们可以登录控制台，打开投放并使用简化的向导对其进行编辑，以更改主题、HTML和文本内容，并发送验证。

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >如果在 **[!UICONTROL Enable the sending of proofs]** 批准设置窗口中选 **[!UICONTROL Enable the sending and approval of proofs]** 择了选项(对于电子邮件投放)或(对于直接邮件投放)，则会自动发送验证。

1. 负责内容编辑的人员完成对投放内容所做的任何更改后，即可使内容可用。

   为此，他们可以：

   * 单击通 **[!UICONTROL Available content]** 过Adobe Campaign控制台的链接。

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * 单击通知消息中的链接，然后批准内容可用性。

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      操作员可以在将内容提交给活动负责人之前添加评论。

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      通知消息允许审阅者批准或拒绝内容。

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### 外部内容批准 {#external-content-approval}

通过此选项，您可以定义负责批准投放呈现的外部运营商，如品牌通信一致性、费率等。 当在 **[!UICONTROL External content approval]** 批准设置窗口中选择该选项时，在内容批准和通知投放之间会向活动负责人添加多个批准步骤：

1. 外部内容管理器收到通知电子邮件，告知其内容已被批准，并请求外部批准。
1. 通知电子邮件包含指向已发送验证的链接，通过该链接，您可以视图投放呈现，以及用于批准或拒绝投放内容的按钮。

   >[!NOTE]
   >
   >这些链接仅在已发送一个或多个验证时才可用。 否则，投放渲染只能通过控制台或Web界面使用。

   ![](assets/s_user_validation_external_content.png)

### 批准提取文件 {#approving-an-extraction-file}

对于脱机投放,Adobe Campaign会生成提取文件，根据设置方式将其发送到路由器。 其内容取决于所使用的导出模板。

在内容、定位和预算获得批准后，投放将变为， **[!UICONTROL Extraction pending]** 直到启动活动的提取工作流。

![](assets/s_ncs_user_waiting_file_extraction.png)

在提取请求日期，将创建提取文件，投放状态将更改为 **[!UICONTROL File to approve]**。

![](assets/s_ncs_user_file_extract_to_valid.png)

您可以视图提取的文件的内容（通过单击其名称）、批准它，或根据需要更改格式并使用仪表板上的链接重新启动提取。

文件获得批准后，您可以向路由器发送通知电子邮件。 有关详细信息，请参阅 [启动脱机投放](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery)。
