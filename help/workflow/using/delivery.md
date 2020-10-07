---
title: 投放
seo-title: 投放
description: 投放
seo-description: null
page-status-flag: never-activated
uuid: 3a74fd0b-8598-46a0-bf13-cf35db0987d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9fd7122e-22c7-4f9a-a2a4-5de3daaa3c2e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---


# 投放{#delivery}

投放 **类型**&#x200B;活动允许您创建投放操作。 它可以使用输入元素来构建。

要进行配置，请编辑活动并输入投放选项。

![](assets/edit_diffusion.png)

1. **投放**

   您可以：

   * 对入站投放中指定的过渡执行操作。 为此，请选择窗口部分 **[!UICONTROL Delivery]** 的第一个选项。

      当以前的工作流活动已创建或指定投放时，可以使用此选项。 这可以由生成出站活动的相同类型的过渡执行，如以下示例所示。

      在以下示例中，首次创建投放。 以后将定义人口和内容。 然后，使用入站投放将这三个元素的信息重新输入到新的活动过渡中，以便发送该信息。

      ![](assets/specified_transition_option_exemple.png)

   * 直接选择相关投放。 为此，请选 **[!UICONTROL Explicit]** 择选项，然后从字段的下拉列表中选择投放 **[!UICONTROL Delivery]** 。

      默认情况下，列表显示投放文件夹中 **包含的** 未完成的投放。 要访问其他活动，请单击 **[!UICONTROL Select link]** 图标。

      ![](assets/diffusion_edit_1.png)

      从字段的下拉活动中选 **[!UICONTROL Folder]** 择列表，或 **[!UICONTROL Display sub-levels]** 单击以显示子文件夹中包含的所有投放:

      ![](assets/diffusion_edit_2.png)

      选择投放操作后，可以单击该图标来显示 **[!UICONTROL Edit link]** 内容。

   * 创建一个脚本以计算投放。 为此，请选择选 **[!UICONTROL Computed by a script]** 项并输入脚本。 可通过单击选项打开输入 **[!UICONTROL Edit...]** 窗口。 以下示例恢复投放的标识符：

      ![](assets/diffusion_edit_3.png)

   * 创建新投放。 为此，请选 **[!UICONTROL New, created from a template]** 择选项，并选择投放将基于的投放模板。

      ![](assets/diffusion_edit_4.png)

      单击图 **[!UICONTROL Select link]** 标以浏览文件夹，如果要视图 **[!UICONTROL Edit link]** 选定模板的内容，请单击该图标。

1. **收件人**

   收件人可以由入站事件指定，例如，在文件导入后指定，或在投放操作中指定。 它们也可以存储在一个或多个文件中。

   ![](assets/diffusion_edit_5.png)

1. **内容**

   消息的内容可以在投放或入站事件中定义。

   ![](assets/diffusion_edit_6.png)

1. **要执行的操作**

   您可以创建投放、准备目标、开始、评估或发送验证。

   ![](assets/diffusion_edit_7.png)

   选择要执行的操作类型：

   * **[!UICONTROL Save]**:通过此选项，可以创建并保存投放。 它不会分析或提供它。
   * **[!UICONTROL Estimate the target]**:此选项允许您计算投放目标以评估其潜力(第一个分析阶段)。 此操作等效于选择选项 **[!UICONTROL Estimate the population to be targeted]** 并在通过 **[!UICONTROL Analyze]** 投放将投放发送到主目标时单 **击**。
   * **[!UICONTROL Prepare]**:此选项允许您运行完整的分析流程(目标计算和内容准备)。 投放没有发送。 此操作等效于选择选项， **[!UICONTROL Deliver as soon as possible]** 并在将投放 **[!UICONTROL Analyze]** 发送到具有投放的主目标时单 **击它**。
   * **[!UICONTROL Send a proof]**:通过此选项，可发送验证投放。 此操作相当于在具有投放 **[!UICONTROL Send a proof]** 的工具栏中单击按 **钮**
   * **[!UICONTROL Prepare and start]**:此选项启动完整的分析过程(目标计算和内容准备)并发送投放。 此操作等同于在将投放 **[!UICONTROL Deliver as soon as possible]**&#x200B;发 **[!UICONTROL Analyze]**&#x200B;送到 **[!UICONTROL Confirm delivery]** 具有投放的主目标时单击、 **和选项**。

   在工 **[!UICONTROL Act on a delivery]** 作流中进一步使用的活动允许您启动启动投放所需的所有剩余步骤(目标计算、内容准备、投放)。 For more on this, refer to [Delivery control](../../workflow/using/delivery-control.md).

   还提供以下选项：

   * **[!UICONTROL Generate an outbound transition]**

      创建将在执行结束时激活的出站过渡。 您可以选择是否检索出站目标的投放。

   * **[!UICONTROL Do not recover target]**

      不恢复传出投放操作的目标。

   * **[!UICONTROL Processing errors]**

      请参阅 [投放控件](../../workflow/using/delivery-control.md)。
   “脚 **本** ”选项卡允许您修改投放参数。

   ![](assets/edit_diffusion_fil_script.png)

## 示例：投放工作流 {#example--delivery-workflow}

创建新工作流并添加活动，如下图所示：

![](assets/new-workflow-5.png)

打开 **投放** 活动并定义属性，如下所示：

* 在部 **[!UICONTROL Delivery]** 分中，选 **[!UICONTROL New, created from a template]** 择并选择投放模板。
* In the **[!UICONTROL Recipients]** section, select **[!UICONTROL Specified in the delivery]**.
* In the **[!UICONTROL Action to execute]** section, keep the **[!UICONTROL Prepare]** option.

![](assets/new-workflow-param-delivery.png)

单击 **[!UICONTROL OK]** 以关闭属性窗口。 您刚刚配置了一个活动，它包括根据将在其中指定目标的投放模板创建和准备新投放。

打开“ **审批** ”活动，并按如下方式定义属性：

1. 在字 **[!UICONTROL Assignment type]** 段中，选择已注册的组。 如果您使用“admin”帐户连接，请选择“管理”组。
1. 然后，输入标题，并在邮件正文中插入以下文本：

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   这是一条消息，其中包含用JavaScript编写的表达式: **[!UICONTROL vars.recCount]** 表示前一收件人投放所针对的任务数。 有关JavaScript表达式的更多信息，请参 [阅JavaScript脚本和模板](../../workflow/using/javascript-scripts-and-templates.md)。

   ![](assets/new-workflow-param-validation.png)

   批准任务详见 [批准](../../workflow/using/approval.md)。

## 输入参数 {#input-parameters}

投放标识符(如 **[!UICONTROL Specified in the transition]** 果在部分中选择了 **[!UICONTROL Delivery]** 此选项)。

* deliveryId
* tableName
* 模式

每个入站事件必须指定由这些参数定义的目标。

>[!NOTE]
>
>此参数仅在选中节 **[!UICONTROL Specified by inbound event(s)]** 中的选项时才 **[!UICONTROL Recipients]** 显示。

* 文件名

   如果在部分中选择了选项，则 **[!UICONTROL File(s) specified by inbound event(s)]** 生成的文件的完整 **[!UICONTROL Recipients]** 名称。

* contentId

   内容标识符(如 **[!UICONTROL Specified by inbound events]** 果在部分中选择了 **[!UICONTROL Content]** 此选项)。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这三个值集标识由目标产生的投放。 **[!UICONTROL tableName]** 是存储目标标识符的表的名称，是 **[!UICONTROL schema]** 收件人的模式（通常是nms:） **[!UICONTROL recCount]** ，是表中元素的数量。

与补码关联的过渡具有相同的参数。

>[!NOTE]
>
>选中该选项时，不 **[!UICONTROL Do not recover target]** 存在输出参数。

